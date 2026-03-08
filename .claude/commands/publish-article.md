อัปโหลดบทความขึ้น Supabase สำหรับ bestsolutionscorp.com

**ขั้นตอน**

1. อ่าน `content/[slug]/draft.md` และ parse frontmatter

2. **ตรวจสอบและ convert รูปปก** — ถ้ามีไฟล์ภาพใน `content/[slug]/` ให้ convert เป็น WebP ก่อน แล้ว upload ขึ้น Supabase Storage:
```python
import subprocess, os
from PIL import Image

# หาไฟล์ภาพ
cover_file = None
for ext in ['jpg', 'jpeg', 'png', 'webp']:
    path = f'content/[slug]/cover.{ext}'
    if os.path.exists(path):
        cover_file = path
        break

cover_url = None
if cover_file:
    # Convert เป็น WebP (quality=85 ดี balance ระหว่างขนาดและคุณภาพ)
    webp_path = '/tmp/cover_[slug].webp'
    img = Image.open(cover_file)
    img.save(webp_path, 'WEBP', quality=85)
    print(f"Converted: {os.path.getsize(cover_file):,} → {os.path.getsize(webp_path):,} bytes")

    # ใช้ชื่อไฟล์ ASCII เสมอ (ไม่ใส่ภาษาไทยใน path)
    ascii_slug = '[ascii-slug]'  # เช่น ai-automation-cover, n8n-cover
    storage_path = f"blog-covers/{ascii_slug}.webp"
    result = subprocess.run([
        'curl', '-s', '-X', 'POST',
        f'{os.environ["NEXT_PUBLIC_SUPABASE_URL"]}/storage/v1/object/images/{storage_path}',
        '-H', f'apikey: {os.environ["SUPABASE_SERVICE_ROLE_KEY"]}',
        '-H', f'Authorization: Bearer {os.environ["SUPABASE_SERVICE_ROLE_KEY"]}',
        '-H', 'Content-Type: image/webp',
        '--data-binary', f'@{webp_path}'
    ], capture_output=True, text=True)
    cover_url = f'{os.environ["NEXT_PUBLIC_SUPABASE_URL"]}/storage/v1/object/public/images/{storage_path}'
    print("Cover URL:", cover_url)
```

3. Convert Markdown body → HTML ด้วย Python + mistune:
```python
import mistune, re
body_md = re.sub(r'```json-ld[\s\S]*?```', '', body_md)
body_md = re.sub(r'\n---\n', '\n\n', body_md)
html = mistune.html(body_md)
html = re.sub(r'^<h1[^>]*>.*?</h1>\s*', '', html, count=1)  # remove H1 (title field handles it)
```

4. Build JSON payload (ห้ามใส่ field `status` — ไม่มีใน schema):
```json
{
  "slug": "...",
  "title": "...",
  "excerpt": "...",
  "content": "[HTML]",
  "category": "AI",
  "tags": [...],
  "author_name": "Best Solutions Corp",
  "cover_image": "[cover_url หรือ null ถ้าไม่มีรูป]",
  "seo_title": "...",
  "seo_description": "...",
  "published_at": "[YYYY-MM-DDT00:00:00+00:00 หรือ null ถ้าเป็น draft]"
}
```

5. บันทึก payload เป็น `/tmp/blog_payload.json` (ใช้ Python json.dump ensure_ascii=False)

6. Upload ด้วย curl — ใช้ POST สำหรับบทความใหม่, PATCH สำหรับอัปเดตที่มีอยู่แล้ว:
```bash
source .env
# บทความใหม่ (POST — single object ไม่ใช่ array)
curl -s -X POST \
  "${NEXT_PUBLIC_SUPABASE_URL}/rest/v1/blog_posts" \
  -H "apikey: ${SUPABASE_SERVICE_ROLE_KEY}" \
  -H "Authorization: Bearer ${SUPABASE_SERVICE_ROLE_KEY}" \
  -H "Content-Type: application/json" \
  -H "Prefer: return=representation" \
  -d @/tmp/blog_payload.json

# อัปเดตบทความเดิม (PATCH — filter ด้วย slug URL-encoded)
SLUG_ENCODED=$(python3 -c "import urllib.parse; print(urllib.parse.quote('[slug]'))")
curl -s -X PATCH \
  "${NEXT_PUBLIC_SUPABASE_URL}/rest/v1/blog_posts?slug=eq.${SLUG_ENCODED}" \
  -H "apikey: ${SUPABASE_SERVICE_ROLE_KEY}" \
  -H "Authorization: Bearer ${SUPABASE_SERVICE_ROLE_KEY}" \
  -H "Content-Type: application/json" \
  -H "Prefer: return=representation" \
  -d @/tmp/blog_payload.json
```

7. หลัง upload สำเร็จ:
   - อัปเดต `status` ใน frontmatter เป็น `"uploaded-draft"`
   - อัปเดต `cover_image_url` ใน frontmatter ถ้ามีการ upload รูป
   - อัปเดต `keywords.md` สถานะเป็น `อัปโหลดแล้ว (Draft)`
   - รายงาน Supabase ID และ cover image URL ที่ได้กลับมา

**หมายเหตุสำคัญ**
- ตาราง: `blog_posts` (ยืนยันแล้ว)
- ไม่มี column `status` ในตาราง — ห้ามส่ง field นี้เด็ดขาด
- category ของ AI cluster ใช้ `"AI"` (ไม่ใช่ `"AI & Automation"`)
- ใช้ Python เพื่อ encode JSON เสมอ ไม่ inline ใน curl
- Supabase Storage bucket: `images` (ยืนยันแล้ว — ไม่ใช่ `public`)
- Upload endpoint: `/storage/v1/object/images/blog-covers/[ascii-slug].webp`
- Public URL pattern: `/storage/v1/object/public/images/blog-covers/[ascii-slug].webp`
- ชื่อไฟล์ใน Storage ต้องเป็น ASCII เสมอ — ห้ามใช้ภาษาไทยใน path เช่น `ai-automation-cover.webp`, `n8n-cover.webp`
- ต้องติดตั้ง Pillow: `pip3 install Pillow` (ถ้ายังไม่มี)
- WebP quality=85 — ลดขนาดได้ ~60-80% จาก JPG/PNG โดยคุณภาพยังดี
