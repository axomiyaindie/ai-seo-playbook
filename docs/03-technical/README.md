# 03 · Technical

## 1. Let the right bots in
Decide per bot: **search/citation bots** (usually allow) vs **training bots** (your choice). See [templates/robots.txt](../../templates/robots.txt).

| Bot | Owner | Purpose |
|---|---|---|
| Googlebot | Google | Search + AI Overviews |
| Google-Extended | Google | Control use for Gemini training/grounding (not a ranking signal) |
| Bingbot | Microsoft | Bing + Copilot |
| OAI-SearchBot | OpenAI | ChatGPT search results |
| GPTBot | OpenAI | Training |
| ChatGPT-User | OpenAI | User-triggered fetch |
| ClaudeBot | Anthropic | Training |
| Claude-SearchBot | Anthropic | Search quality |
| Claude-User | Anthropic | User-triggered fetch |
| PerplexityBot | Perplexity | Search index |
| Applebot-Extended | Apple | Opt out of AI training |
| CCBot | Common Crawl | Open dataset used by many models |

## 2. Render and speed
- Serve key content in HTML, not only via client-side JavaScript. Many AI crawlers do not run JS.
- Good Core Web Vitals, HTTPS, clean canonicals, XML sitemap with accurate `lastmod`.

## 3. Structured data
Use JSON-LD: `Organization`, `Product`, `SoftwareApplication`, `FAQPage`, `Article`, `Review`, `BreadcrumbList`. Must match visible content. See [templates/product-schema.json](../../templates/product-schema.json).

## 4. llms.txt
A proposed convention (llmstxt.org): a Markdown file at `/llms.txt` that points LLMs to your best pages. **Adoption by major AI search engines is unconfirmed**, so treat it as low-cost and experimental. See [templates/llms.txt](../../templates/llms.txt).

## 5. Clean structure
Descriptive headings, short paragraphs, tables, lists, one topic per URL, and obvious About / Pricing / Docs / Contact pages.
