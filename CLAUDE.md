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
2. ใช้ subagent ตามลำดับ workflow ด้านล่าง
3. บันทึกผลลัพธ์เป็นไฟล์ใน `content/[keyword-slug]/`
4. รายงานให้เจ้าของโปรเจคตรวจสอบ
5. รอคำสั่ง "อัปเดตขึ้นเว็บ" จึงจะใช้ supabase-publisher agent

---

## มาตรฐานการเขียนภาษาไทย

เนื้อหาทั้งหมดต้องเป็นภาษาไทย และต้องอ่านเหมือนคนเขียนจริงๆ ไม่ใช่ AI ให้ยึดหลักดังนี้:

- **เขียนเหมือนพูดคุย** — ใช้ภาษาที่เป็นธรรมชาติ เข้าใจง่าย ไม่เป็นทางการเกินไป
- **หลีกเลี่ยงภาษา AI** — ห้ามใช้ประโยคสำเร็จรูป เช่น "ในบทความนี้เราจะมาพูดถึง..." หรือ "ดังนั้นจะเห็นได้ว่า..."
- **ย่อหน้าสั้น** — แต่ละย่อหน้าไม่เกิน 3-4 ประโยค อ่านง่ายบนมือถือ
- **ตอบคำถามตรงๆ** — ขึ้นต้นด้วยสิ่งที่ผู้อ่านอยากรู้ ไม่ต้องอารัมภบท
- **ใส่ตัวอย่างจริง** — ถ้าพูดถึงอะไร ให้ยกตัวอย่างที่เป็นรูปธรรม เข้าใจได้ทันที
- **Keyword ต้องกลมกลืน** — ใส่ keyword ให้เป็นธรรมชาติ ไม่ยัดเยียดจนอ่านแปลก

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
- AI Automation คืออะไร? (Cluster: AI & Automation)
- SEO คืออะไร? (Cluster: SEO)
- ยิงแอด Facebook ยังไงให้ได้ผล? (Cluster: Facebook & Google Ads)
- Digital Marketing คืออะไร? (Cluster: Digital Marketing)

---

## Workflow การเขียนบทความ

```
[รับ keyword จากเจ้าของโปรเจค]
        |
        v
1. serp-analyzer
        |
        v
2. content-brief-strategist  <-- ส่ง SEO requirements ให้ writer โดยตรง
        |
        v
3. seo-content-writer  <-- เขียน SEO ให้ถูกตั้งแต่แรกตาม brief
        |
        v
4. internal-linking  <-- ใช้ site-inventory.md ประกอบ
        |
        v
5. cover-image-prompter  <-- สร้าง prompt รูปปก 3 เวอร์ชัน บันทึกใน frontmatter
        |
        v
[บันทึกไฟล์ใน content/[keyword-slug]/draft.md]
[อัปเดต keywords.md สถานะเป็น "รอตรวจ"]
[รายงานให้เจ้าของโปรเจคตรวจ พร้อม prompt รูปปก]
        |
        v (เมื่อได้รับคำสั่ง "อัปเดตขึ้นเว็บ")
6. supabase-publisher
        |
        v
[อัปเดต keywords.md สถานะเป็น "อัปโหลดแล้ว (Draft)"]
```

**ขีดจำกัดความยาว (สำคัญมาก — ประหยัด token):**
- Pillar Page: **2,000–2,500 คำ** (ไม่เกิน)
- Blog Post: **1,000–1,500 คำ**
- Landing Page: **800–1,200 คำ**

---

## Subagent ทั้ง 6 ตัวและวิธีใช้

### 1. serp-analyzer — วิเคราะห์ SERP
ใช้ก่อนเขียนทุกครั้ง วิเคราะห์ว่า Google แสดงผลอะไรสำหรับ keyword นั้น ใครอยู่อันดับต้นๆ มี Featured Snippet หรือ PAA ไหม และมีช่องว่างไหนที่เราเจาะได้

### 2. content-brief-strategist — วางโครงสร้างบทความ
สร้าง brief ครบชุด: meta title, meta description, H1, โครงสร้าง H2/H3, **ระบุ word limit ชัดเจน**, LSI keywords, SEO requirements และ CTA — brief ต้องมีข้อมูล SEO ครบเพื่อให้ writer เขียนถูกตั้งแต่แรก

### 3. seo-content-writer — เขียนบทความพร้อม SEO
เขียนบทความภาษาไทยตาม brief เน้นให้อ่านเหมือนคนเขียน ใส่ keyword อย่างเป็นธรรมชาติ ตอบความต้องการผู้อ่านก่อนเสมอ **ห้ามเกิน word limit ที่ brief กำหนด** — writer รับผิดชอบ SEO ตั้งแต่แรก ไม่ต้องรอ SEO pass แยก

### 4. internal-linking — วาง internal links
ดูว่าบทความนี้ควรลิงก์ไปหน้าไหน และหน้าไหนควรลิงก์กลับมา ให้ใช้ `site-inventory.md` ประกอบการทำงาน

### 5. cover-image-prompter — สร้าง prompt รูปปกบทความ
สร้าง prompt สำหรับเจนรูปปกบทความ 3 เวอร์ชัน (Midjourney, DALL-E 3/nano-banana-pro, และแบบสั้น) พร้อม notes ภาษาไทยสำหรับนักออกแบบ ผลลัพธ์จะถูกเพิ่มใน frontmatter ของ draft.md ด้วย

### 6. supabase-publisher — อัปโหลดขึ้น database
ใช้เฉพาะเมื่อเจ้าของโปรเจคสั่ง "อัปเดตขึ้นเว็บ" เท่านั้น อ่านไฟล์ content ที่ผ่านการอนุมัติแล้ว แล้ว upsert ข้อมูลขึ้น Supabase (**หมายเหตุ**: ตาราง `blog_posts` ไม่มี column `status` — ห้ามส่ง field นี้)

---

## โครงสร้างไฟล์

```
bestsolutions-seo/
├── CLAUDE.md                        # ไฟล์นี้
├── keywords.md                      # tracker ทั้ง 75 keyword + สถานะ
├── site-inventory.md                # รายการหน้าทั้งหมด สำหรับ internal-linking
├── best_solutions_content_calendar.csv
├── .env                             # SUPABASE_URL + SUPABASE_SERVICE_ROLE_KEY
├── content/                         # บทความที่เขียนเสร็จแล้ว รอตรวจ
│   └── [keyword-slug]/
│       ├── draft.md                 # บทความฉบับสมบูรณ์ พร้อม metadata
│       ├── brief.md                 # content brief
│       └── seo-report.md           # ผลการ audit
├── published/                       # บทความที่ publish ขึ้น Supabase แล้ว
└── .claude/
    └── agents/                      # subagent configs
```

### รูปแบบ draft.md (ต้องมี frontmatter ครบ)

```markdown
---
title: "ชื่อบทความ"
slug: "keyword-slug"
excerpt: "ย่อเนื้อหา 1-2 ประโยค ใช้แสดงใน listing (ถ้าไม่มีจะใช้ meta_description)"
primary_keyword: "keyword หลัก"
meta_title: "meta title (max 60 chars)"
meta_description: "meta description (max 155 chars)"
cluster: "AI & Automation"
content_type: "Blog"
search_intent: "informational"
priority: "High"
seo_score: 0
tags: ["keyword หลัก", "AI & Automation", "Blog"]
author_name: "Best Solutions Corp"
cover_image_url: null
cover_image_prompt: "prompt สั้นสำหรับเจนรูปปก (จาก cover-image-prompter)"
cover_image_concept: "แนวคิดภาพปกภาษาไทย"
status: "draft"
---

[เนื้อหาบทความ Markdown]
```

**Mapping frontmatter → Supabase `blog_posts`:**
- `meta_title` → `seo_title`
- `meta_description` → `seo_description`
- `cluster` → `category`
- `cover_image_url` → `cover_image`
- อัปโหลดด้วย `status: "draft"` และ `published_at: null` เสมอ

---

## คำถามที่ต้องถามก่อนเริ่มทุกครั้ง

ก่อนเริ่ม workflow ให้ยืนยัน:
1. **Keyword หลักคืออะไร?** — หรือดูจาก `keywords.md` ว่า keyword ไหนยัง pending อยู่
2. **กลุ่มเป้าหมายคือใคร?** — ลูกค้า SME ไทยที่ต้องการบริการดิจิทัลมาร์เก็ตติ้ง
3. **Content Type ไหน?** — ดูจาก `keywords.md` (Blog / Pillar Page / Landing Page / Case Study)
4. **มี Pillar Page ของ Cluster นั้นเขียนแล้วหรือยัง?** — ถ้ายัง ให้เขียน Pillar Page ก่อน

---

## ข้อมูลเว็บไซต์

- **URL:** https://bestsolutionscorp.com/
- **ภาษา:** ไทยทั้งหมด
- **กลุ่มลูกค้า:** SME ไทย ธุรกิจที่ต้องการบริการ AI Automation, SEO, ยิงแอด, ทำเว็บ, โซเชียลมีเดีย, ผลิต Content
- **เป้าหมาย:** ติดอันดับ Google ไทยสำหรับ keyword ที่เกี่ยวกับบริการของบริษัท

เมื่อ agent ถามเรื่อง site URL หรือ domain ให้ใช้ `bestsolutionscorp.com` เสมอ
