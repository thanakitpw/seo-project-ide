# SEO Patterns — Detailed Notes

## Thai Keyword Density Calculation Method
For Thai/English compound keywords like "ai automation คืออะไร":
- The interrogative suffix "คืออะไร" is part of the page title/H1 framing, not repeated in body
- Count root term "AI Automation" for density (all caps variants count equally)
- Target: 1.9-2.0% for this niche (AI/tech topics tend to repeat the brand term heavily)
- Safe reduction: replace body-paragraph instances (not headings) with pronouns or synonyms

## Heading LSI Audit — Generic Labels to Always Fix
These heading patterns appear in Thai tech articles and always need LSI enrichment:
- "นิยาม..." → add "ระบบอัตโนมัติ" or domain term
- "FAQ" → "คำถามที่พบบ่อยเกี่ยวกับ [keyword]"
- "Comparison Table" → "เปรียบเทียบ [Tool A], [Tool B] และ [Tool C]"
- "ค่าใช้จ่ายจริง" → "ค่าใช้จ่าย [keyword] จริงต่อเดือน"
- "เครื่องมือฟรี..." → "เครื่องมือ [LSI term] ฟรี..."
- "ปัญหาที่เจ้าของธุรกิจเจอ" → "ปัญหางาน Manual ที่... SME เผชิญ"

## Meta Description Trimming Strategy
Priority order for trimming Thai meta descriptions:
1. Remove adverbial phrases: "อย่างไร", "อย่างละเอียด", "ทั้งหมด"
2. Shorten "ขั้นตอนเริ่มต้นใช้งาน" → "ขั้นตอนเริ่มต้น"
3. Remove "และ" conjunctions linking the last two items if space is tight
Always keep: primary keyword, CTA or value hook, SME ไทย reference (brand positioning)

## Article Structure Pattern (bestsolutionscorp.com pillar pages)
Standard structure observed:
1. H1 (keyword + audience + year)
2. Intro paragraph (keyword in first 100 words)
3. H2: Definition section with H3 sub-sections
4. H2: Comparison table (vs alternatives)
5. H2: Why now / business case
6. H2: Use case examples by industry
7. H2: Tools comparison table
8. H2: How to start (step-by-step)
9. H2: FAQ/objection handling
10. H2: Advanced/future topic (Agentic AI, etc.)
11. H2: FAQ (with schema)
12. CTA link

## FAQ Schema Template for This Site
Always use FAQPage type. Questions map 1:1 from FAQ H3 headings.
Wrap in `<script type="application/ld+json">` for CMS compatibility.
Copy answer text verbatim from article — do not paraphrase for schema.
