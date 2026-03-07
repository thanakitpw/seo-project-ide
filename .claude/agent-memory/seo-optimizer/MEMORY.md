# SEO Optimizer Agent Memory

## Project Context
- Site: bestsolutionscorp.com
- Content type: Thai-language SME-focused tech/AI articles
- Primary content niche: AI Automation, n8n, Make.com, Zapier, Marketing Automation, AI Chatbot
- See `patterns.md` for detailed LSI clusters and recurring patterns

## Thai-Language SEO Rules
- Keyword density: count root English term (e.g., "AI Automation") across full article, not the interrogative Thai phrase ("คืออะไร") alone
- Thai word count: ~1,100 words is typical length for this site's pillar articles
- Character counting for meta tags must include Thai characters as single chars (not bytes)
- "อย่างไร", "คืออะไร", "คือ" are Thai interrogative/copula suffixes — strip when counting root keyword density

## Recurring LSI Keyword Clusters
- "AI automation": ระบบอัตโนมัติ, intelligent automation, ปัญญาประดิษฐ์, workflow, RPA, Make.com, Zapier, n8n, LLM, trigger, action
- "n8n": open-source, self-hosted, workflow automation, LLM integration, AI agent
- "Marketing Automation": Meta Ads, Google Analytics, reporting, CRM, drip campaign

## Common Issues Found in This Content
1. Generic H3 headings without LSI (e.g., "FAQ", "Comparison Table", "นิยามแบบเข้าใจง่าย") — always rename with LSI terms
2. Meta descriptions tend to be 1-5 chars over 155 limit — trim filler adverbs/phrases like "อย่างไร"
3. Keyword density for AI-topic articles with many heading repetitions often runs 2.1-2.3% — trim 2-4 body instances with pronouns (ระบบนี้, มัน) or synonyms (intelligent automation, ระบบ AI อัตโนมัติ)
4. Internal link placeholders are pre-inserted in source content for this site — verify 3 exist before adding new ones

## Internal Link Topic Clusters (Confirmed)
- AI Chatbot คืออะไร
- Marketing Automation คืออะไร
- n8n คืออะไร

## FAQ Schema
- This site's articles consistently have a dedicated FAQ section — always generate FAQPage JSON-LD
- FAQ answers should be copied verbatim from article for schema accuracy
- Wrap in `<script type="application/ld+json">` tags

## Score Calibration
- Well-structured pillar articles on this site typically score 90-95/100 after fixes
- Most points lost from: LSI headings (generic labels), density slightly over 2%, meta description marginally over 155 chars
