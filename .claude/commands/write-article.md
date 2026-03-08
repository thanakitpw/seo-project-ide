เขียนบทความภาษาไทยตาม content brief ที่กำหนด โดยยึดกฎเหล่านี้อย่างเคร่งครัด:

**กฎการเขียน**
- เขียนเหมือนคนพูดคุย ไม่เป็นทางการเกินไป อ่านง่าย
- ห้ามใช้ประโยค AI สำเร็จรูป เช่น "ในบทความนี้เราจะ..." "ดังนั้นจะเห็นได้ว่า..."
- ย่อหน้าสั้น 3-4 ประโยค อ่านง่ายบนมือถือ
- ตอบคำถามตรงๆ ตั้งแต่ต้น ไม่อารัมภบท
- ใส่ตัวอย่างที่เป็นรูปธรรม โดยเฉพาะตัวอย่างจาก SME ไทย
- **ห้ามเกิน word limit ที่ brief กำหนด**
- **ห้ามใช้เครื่องหมาย `:` ในเนื้อหา** — ใช้ `—` แทน เช่น `Step 1 — ทำอะไร` หรือขึ้นบรรทัดใหม่แทน (ยกเว้นใน JSON-LD, URL, frontmatter)

**โครงสร้างที่ต้องมี**
1. Featured Snippet paragraph — นิยามสั้น 40-60 คำ ตอบ keyword โดยตรง (H2 แรก)
2. เนื้อหาหลักตาม H2/H3 ใน brief
3. ตัวอย่างหรือ case study อย่างน้อย 1 ชิ้น
4. FAQ 3-5 ข้อ พร้อม JSON-LD schema ที่ท้ายบทความ
5. CTA ปิดท้าย link ไป /services/[relevant]/

**SEO ที่ต้องทำใน content**
- ใส่ primary keyword ใน 100 คำแรก, H1, H2 แรก, และ conclusion
- กระจาย LSI keywords ตาม brief
- ใส่ internal links ตามที่ brief ระบุ (format: `[anchor text](/blog/slug)`)

**Output**
เขียนเป็น Markdown พร้อม frontmatter ครบ:
```
---
title:
slug:
excerpt:
primary_keyword:
meta_title:
meta_description:
cluster:
content_type:
search_intent:
priority:
seo_score: 0
tags: []
author_name: "Best Solutions Corp"
cover_image_url: null
cover_image_prompt: ""
cover_image_concept: ""
status: "draft"
---
```
