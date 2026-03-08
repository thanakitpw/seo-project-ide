สร้าง prompt รูปปกบทความสำหรับ nano-banana-pro (Gemini 2.5 Flash) โดยภาพต้องมีข้อความภาษาไทยบนภาพด้วย

**Brand Guidelines — CI Style**
- Background หลัก: deep navy blue (#0A1628 หรือ #1E3A5F) — ใช้ได้เลยทุกบทความ
- Background ทางเลือก: gradient จาก deep crimson (#8B0000) ซ้าย → deep navy (#0A1628) ขวา — ใช้เมื่อต้องการ energy สูงขึ้น
- Accent: Neon cyan (#00B4D8), white glow, electric blue highlights
- Elements: glowing circuit board patterns, neon tech icons, light rays, digital particles
- Style: Professional, modern, tech-forward — ไม่ cartoon ไม่ stock-photo ทั่วไป
- ขนาด: 1200 x 630px (16:9)

**โครงสร้าง prompt ที่ต้องมี**

```
Deep navy blue (#0A1628) background with glowing neon cyan circuit board pattern overlay,

Large bold Thai text overlay at top/center reading "[ชื่อบทความสั้น 5-7 คำ]" in white bold with subtle neon glow,
Below it smaller text "[English subtitle]" in light cyan (#00B4D8),

[Visual elements ที่เกี่ยวกับหัวข้อ — glowing, neon-lit],
Dramatic neon cyan lighting, digital particles floating,
Color palette: deep navy (#0A1628) background, neon cyan accents (#00B4D8), white text with glow,
Professional corporate digital marketing style, 16:9 ratio, high quality
```

**ถ้าต้องการ gradient style (ทางเลือก)**
เปลี่ยน background เป็น: `Horizontal gradient from deep crimson red (#8B0000) on left to deep navy blue (#0A1628) on right`

**กฎสำหรับ Text Overlay**
- Thai title: ตัวหนา (bold), สีขาว, มี subtle glow เล็กน้อย, วางบน area ที่ไม่มี element รก
- อ่านออกชัดเจน — ไม่ใช้ตัวอักษรที่ซ้อนกับ background ที่ซับซ้อน
- Thai text ต้องสะกดถูกต้อง — คัดลอกจาก title บทความโดยตรง
- English subtitle: ย่อจาก title, สั้น กระชับ ไม่เกิน 7 คำ, สี cyan
- **ชื่อแบรนด์/เครื่องมือ ห้ามแปลงเป็นอักษรไทย** — เช่น "n8n", "Claude", "ChatGPT", "Zapier" ต้องเป็น Latin ตลอด ระบุใน prompt ว่า `keep brand names in Latin characters (n8n, Claude, etc.)`

**Visual Concept per Cluster**
- AI & Automation: Network nodes, glowing AI brain, workflow arrows, data streams, robot elements
- SEO: Ascending growth charts, search bar visualization, ranking arrows, digital graphs
- Ads: Conversion funnel, target/bullseye, performance dashboard, bar charts
- Web Dev: Browser mockup, responsive devices, code snippets glowing, UI wireframe
- Social Media: Content grid, engagement icons (abstract), mobile screen, social feed
- Content Marketing: Content creation workspace, words-to-visuals, pencil/cursor concept
- Digital Marketing: Multi-channel ecosystem, rocket launch, growth metrics, funnel

**Output**

สร้าง prompt สำหรับ nano-banana-pro 1 เวอร์ชัน พร้อม:

```
### Prompt สำหรับ nano-banana-pro

[prompt ตามโครงสร้างข้างต้น]

### Thai Title บนภาพ
"[ข้อความภาษาไทยที่จะใส่]"

### English Subtitle
"[English text]"

### Frontmatter snippet
cover_image_prompt: "[prompt สั้น 50 คำ]"
cover_image_concept: "[อธิบายแนวคิดภาษาไทย 1 ประโยค]"
```

จากนั้น **อัปเดต frontmatter ใน draft.md** ด้วย cover_image_prompt และ cover_image_concept
