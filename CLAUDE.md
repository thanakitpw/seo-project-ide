# โปรเจค SEO ภาษาไทย — Best Solutions Corp

เว็บไซต์: https://bestsolutionscorp.com/

โปรเจคนี้ใช้สำหรับเขียนและจัดการเนื้อหา SEO ภาษาไทยทั้งหมดให้กับเว็บไซต์ bestsolutionscorp.com เป้าหมายคือเขียนบทความที่อ่านเข้าใจง่าย เหมือนคนเขียนจริงๆ ไม่ใช่ AI และติดอันดับ Google ได้ดี

---

## การตั้งค่า Environment (ต้องทำก่อน)

ไฟล์ `.env` ถูกสร้างแล้ว มีค่าครบ พร้อมใช้งาน

```
NEXT_PUBLIC_SUPABASE_URL=https://eeqlpvpmjcarqbivzbrr.supabase.co
NEXT_PUBLIC_SUPABASE_ANON_KEY=...
SUPABASE_SERVICE_ROLE_KEY=...
```

**หมายเหตุ**: `.env` อยู่ใน `.gitignore` แล้ว จะไม่ถูก commit ขึ้น git

---

## กฎสำคัญที่ต้องทำทุกครั้ง

**ห้ามอัปเดตเว็บไซต์โดยตรง** — ทุกครั้งที่เขียนเนื้อหาเสร็จ ให้บันทึกเป็นไฟล์ในโปรเจคนี้ก่อน รอให้เจ้าของโปรเจคตรวจและอนุมัติ แล้วจึงสั่งให้อัปเดตขึ้นเว็บได้

ขั้นตอนมาตรฐาน:
1. รับ keyword หรือหัวข้อจากเจ้าของโปรเจค
2. รัน skills ตามลำดับ workflow ด้านล่าง
3. บันทึกผลลัพธ์เป็นไฟล์ใน `content/[keyword-slug]/`
4. รายงานให้เจ้าของโปรเจคตรวจสอบ
5. รอคำสั่ง "อัปเดตขึ้นเว็บ" จึงจะรัน `/publish-article`

---

## มาตรฐานการเขียนภาษาไทย

เนื้อหาทั้งหมดต้องเป็นภาษาไทย และต้องอ่านเหมือนคนเขียนจริงๆ ไม่ใช่ AI ให้ยึดหลักดังนี้:

- **เขียนเหมือนพูดคุย** — ใช้ภาษาที่เป็นธรรมชาติ เข้าใจง่าย ไม่เป็นทางการเกินไป
- **หลีกเลี่ยงภาษา AI** — ห้ามใช้ประโยคสำเร็จรูป เช่น "ในบทความนี้เราจะมาพูดถึง..." หรือ "ดังนั้นจะเห็นได้ว่า..."
- **ย่อหน้าสั้น** — แต่ละย่อหน้าไม่เกิน 3-4 ประโยค อ่านง่ายบนมือถือ
- **ตอบคำถามตรงๆ** — ขึ้นต้นด้วยสิ่งที่ผู้อ่านอยากรู้ ไม่ต้องอารัมภบท
- **ใส่ตัวอย่างจริง** — ถ้าพูดถึงอะไร ให้ยกตัวอย่างที่เป็นรูปธรรม เข้าใจได้ทันที
- **Keyword ต้องกลมกลืน** — ใส่ keyword ให้เป็นธรรมชาติ ไม่ยัดเยียดจนอ่านแปลก
- **ห้ามใช้เครื่องหมาย `:` ในเนื้อหาบทความ** — ใช้ `—` แทนถ้าต้องการแยก เช่น `Step 1 — ทำอะไร` แทน `Step 1: ทำอะไร`, หรือขึ้นบรรทัดใหม่แทน
- **ห้ามใช้ "สำหรับ SME" ใน title หรือ heading** — ฟังดูแข็ง ถ้าต้องการสื่อกลุ่มเป้าหมาย ให้ใช้ "ที่เจ้าของธุรกิจควรรู้" หรือ "ฉบับธุรกิจไทย" หรือตัดออก

---

## Content Calendar

มี 75 บทความที่ต้องเขียน แบ่งเป็น 8 กลุ่ม ดูรายละเอียดทั้งหมดได้ที่ `keywords.md`

| Cluster | จำนวน | Content Type หลัก |
|---|---|---|
| AI & Automation | 12 | Blog, Pillar Page, Landing Page |
| SEO | 12 | Blog, Pillar Page, Landing Page |
| Facebook & Google Ads | 11 | Blog, Pillar Page, Landing Page |
| Web Development | 9 | Blog, Landing Page |
| Social Media | 9 | Blog, Landing Page |
| Content Marketing | 7 | Blog, Landing Page |
| Digital Marketing | 9 | Blog, Pillar Page, Landing Page |
| Case Study | 6 | Case Study, Blog |

**Pillar Pages (เขียนก่อน — เป็น anchor สำหรับ internal linking):**
- AI Automation คืออะไร? (Cluster: AI & Automation) ✅ อัปโหลดแล้ว
- SEO คืออะไร? (Cluster: SEO)
- ยิงแอด Facebook ยังไงให้ได้ผล? (Cluster: Facebook & Google Ads)
- Digital Marketing คืออะไร? (Cluster: Digital Marketing)

---

## Workflow การเขียนบทความ (ใช้ Skills)

```
[รับ keyword จากเจ้าของโปรเจค]
        |
        v
/serp-analyze    ← วิเคราะห์ SERP, featured snippet, PAA, content gap
        |
        v
/content-brief   ← brief ครบ: meta, H2/H3, word limit, LSI, CTA, cover image text
        |
        v
/write-article   ← เขียนตาม brief, SEO ถูกตั้งแต่แรก, ห้ามเกิน word limit
        |
        v
/link-article    ← internal links จาก site-inventory.md, แก้ draft.md โดยตรง
        |
        v
/cover-image     ← prompt สำหรับ nano-banana-pro พร้อม Thai text overlay
        |
        v
[บันทึก draft.md ใน content/[keyword-slug]/]
[อัปเดต keywords.md → "รอตรวจ"]
[รายงานให้เจ้าของตรวจ พร้อม prompt รูปปก]
        |
        v (เมื่อได้รับคำสั่ง "อัปเดตขึ้นเว็บ")
/publish-article ← convert MD→HTML (mistune), upload Supabase, update keywords.md
        |
        v
[keywords.md → "อัปโหลดแล้ว (Draft)"]
```

**ขีดจำกัดความยาว (สำคัญมาก — ประหยัด token):**
- Pillar Page: **2,000–2,500 คำ** (ไม่เกิน)
- Blog Post: **1,000–1,500 คำ**
- Landing Page: **800–1,200 คำ**

---

## Skills ทั้ง 5 ตัวและวิธีใช้

Skills อยู่ใน `.claude/commands/` — รันใน main conversation ประหยัด token กว่า subagents

### `/serp-analyze` — วิเคราะห์ SERP
WebSearch หา top results, featured snippet, PAA boxes, search intent และ content gap สรุป 200-300 คำ

### `/content-brief` — วางโครงสร้างบทความ
สร้าง brief ครบชุด: meta title/description, H1, H2/H3, **word limit ชัดเจน**, LSI keywords, internal link targets, CTA และ Thai text สำหรับภาพปก

### `/write-article` — เขียนบทความพร้อม SEO
เขียนภาษาไทยตาม brief, SEO ถูกตั้งแต่แรก, **ห้ามเกิน word limit**, มี Featured Snippet paragraph, FAQ + JSON-LD, output เป็น Markdown พร้อม frontmatter ครบ

### `/link-article` — วาง internal links
อ่าน site-inventory.md, หาจุดที่ควรลิงก์ 3-5 จุด, แก้ draft.md โดยตรง

### `/cover-image` — สร้าง prompt รูปปก
Prompt สำหรับ nano-banana-pro พร้อม **Thai text overlay บนภาพ** (ชื่อบทความภาษาไทย bold + English subtitle), อัปเดต frontmatter ใน draft.md
**CI Style:** deep navy `#0A1628` + neon cyan `#00B4D8` (gradient แดง→น้ำเงินเป็น optional สำหรับ high-energy topics) — ชื่อแบรนด์ต้องเป็น Latin เสมอ (n8n, Claude, Zapier ห้ามแปลงเป็นไทย)

### `/publish-article` — อัปโหลดขึ้น Supabase
Convert MD→HTML ด้วย mistune, upload ผ่าน Supabase REST API (**ห้ามส่ง field `status`** — ไม่มีใน schema), อัปเดต keywords.md
- ถ้ามีไฟล์ `cover.jpg/png/webp` ในโฟลเดอร์ → upload รูปไป Supabase Storage ก่อน แล้วใส่ URL ใน `cover_image`
- บทความใหม่ใช้ POST, บทความที่มีอยู่แล้วใช้ PATCH (filter `?slug=eq.[slug]`)

---

## โครงสร้างไฟล์

```
bestsolutions-seo/
├── CLAUDE.md
├── keywords.md                      # tracker 75 keyword + สถานะ
├── site-inventory.md                # รายการหน้าทั้งหมด สำหรับ /link-article
├── .env                             # SUPABASE credentials
├── content/
│   └── [keyword-slug]/
│       └── draft.md                 # บทความ + frontmatter ครบ
├── published/                       # บทความที่อัปโหลดแล้ว
└── .claude/
    ├── commands/                    # Skills (slash commands)
    │   ├── serp-analyze.md
    │   ├── content-brief.md
    │   ├── write-article.md
    │   ├── link-article.md
    │   ├── cover-image.md
    │   └── publish-article.md
    └── agents/                      # Legacy (ยังใช้ได้ถ้าต้องการ isolated context)
```

### รูปแบบ draft.md (frontmatter ครบ)

```markdown
---
title: "ชื่อบทความ"
slug: "keyword-slug"
excerpt: "ย่อเนื้อหา 1-2 ประโยค"
primary_keyword: "keyword หลัก"
meta_title: "meta title (max 60 chars)"
meta_description: "meta description (max 155 chars)"
cluster: "AI & Automation"
content_type: "Blog"
search_intent: "informational"
priority: "High"
seo_score: 0
tags: ["keyword หลัก", "cluster", "content_type"]
author_name: "Best Solutions Corp"
cover_image_url: null
cover_image_prompt: "prompt สำหรับ nano-banana-pro"
cover_image_concept: "แนวคิดภาพปกภาษาไทย"
status: "draft"
---
```

**Mapping frontmatter → Supabase `blog_posts`:**
- `meta_title` → `seo_title`
- `meta_description` → `seo_description`
- `cluster` → `category` (ใช้ชื่อสั้น เช่น "AI", "SEO", "Ads")
- `cover_image_url` → `cover_image`
- ห้ามส่ง field `status` — ไม่มีใน DB schema

---

## ข้อมูลเว็บไซต์

- **URL:** https://bestsolutionscorp.com/
- **ภาษา:** ไทยทั้งหมด
- **กลุ่มลูกค้า:** SME ไทย ต้องการบริการ AI Automation, SEO, ยิงแอด, ทำเว็บ, โซเชียลมีเดีย, ผลิต Content
- **เป้าหมาย:** ติดอันดับ Google ไทยสำหรับ keyword ที่เกี่ยวกับบริการของบริษัท
- **Domain:** `bestsolutionscorp.com` เสมอ
