# On-Page SEO Optimizer — Agent Memory

## Project Context
- Site: BestSolutions (bestsolutions.co.th)
- Language: Thai (th)
- Primary content type: Pillar Pages + Blog posts targeting Thai SME audience
- Target audience: SME business owners in Thailand — education level mid-high, non-technical
- Content cluster focus: AI Automation, AI Chatbot, n8n, Make.com, Marketing Automation

## Recurring Patterns

### Meta Tags
- Meta Descriptions for this site consistently lack a CTA — always add one (e.g., "อ่านคู่มือฉบับสมบูรณ์", "ดูตัวอย่างได้เลย")
- Meta Title format preferred: "[Keyword]? [Modifier] [Audience] [Year]" e.g., "AI Automation คืออะไร? คู่มือ SME ไทยฉบับสมบูรณ์ [2026]"

### Keyword Placement
- Thai pillar pages tend to have low exact-match keyword density because "คืออะไร" suffix does not repeat naturally — compensate by ensuring head term (e.g., "AI Automation") appears 1-1.5% across the page
- Always verify keyword appears in the first 100 words of body text (not just in H1/H2)

### Heading Structure
- Preferred H3 pattern: descriptive, keyword-containing, not abbreviated (e.g., avoid "Step 1-4 + ข้อผิดพลาด" — use full Thai description)
- H2s on this site are generally well-structured; H3s are the most common weak point

### Schema Strategy
- All Pillar Pages need 3 schemas: Article + BreadcrumbList + FAQPage
- Use separate `<script type="application/ld+json">` tags for each schema type
- FAQPage schema text MUST match visible on-page content exactly
- Article Schema requires image URL — always flag missing hero image as CRITICAL

### Images
- This site currently produces content without images — image SEO is a consistent gap
- Recommended image types per Pillar Page: Hero Infographic, Comparison Diagram, Use Case Screenshot/Mockup, Tools Comparison Visual, Step-by-Step Visual
- File naming convention: lowercase Thai-English hybrid with hyphens, e.g., `ai-automation-คืออะไร-sme-thailand-guide.jpg`
- Hero image dimensions: 1200x630px (dual purpose: Article Schema + OG image)

### Readability
- Target Flesch score: 55-70 for SME Thai audience
- Comparison sections (vs. tables) must be HTML tables with `<thead>/<tbody>` for Featured Snippet eligibility
- Internal links pattern: always link to AI Chatbot, n8n, Marketing Automation articles from AI Automation content

## Detailed Notes
- See `patterns.md` for extended schema templates and image SEO guidelines
