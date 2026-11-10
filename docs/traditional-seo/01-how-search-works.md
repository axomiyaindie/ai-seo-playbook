# 01 — How Search Works

> **Part A · Traditional SEO** · [← Back to Traditional SEO](README.md) · Next: [02 — Keywords and Search Intent](02-keywords-and-intent.md)

Before you optimise anything, you need a working model of what search engines actually do. Every tactic in this playbook — on-page, technical, content, links — is downstream of three processes: **crawling**, **indexing**, and **ranking**. Get the model right and the tactics make sense. Get it wrong and you'll chase myths.

This page explains those three processes, then adds the modern wrinkle: AI Overviews and AI answers sit on top of the same pipeline. That's why **Part A comes first**.

---

## The three-stage pipeline

| Stage | What happens | Who does it | What can go wrong |
|---|---|---|---|
| **1. Crawling** | A bot fetches URLs and follows links | Googlebot, Bingbot, and others | Blocked by `robots.txt`, orphaned pages, server errors, JS-only content |
| **2. Indexing** | The page is parsed, understood, and stored | The search engine's indexer | `noindex`, thin/duplicate content, canonical conflicts, content hidden behind interaction |
| **3. Ranking** | The index is queried and results are ordered | The ranking system | Weak relevance, poor quality signals, no authority, bad UX signals |

A page must survive **all three** to appear in results. Most "my page doesn't rank" problems are actually stage 1 or stage 2 failures, not stage 3. Diagnose in order.

---

## Stage 1 — Crawling

A **crawler** (also called a spider or bot) is a program that discovers URLs and fetches them. Google's primary crawler is **Googlebot**. It discovers URLs from:

- **Links** on pages it already knows about (the classic path)
- **XML sitemaps** you submit
- **Redirects** and canonical hints
- **Manual submission** via Search Console's URL Inspection tool

### What controls crawling

- **`robots.txt`** — a file at your domain root (`https://yourdomain.com/robots.txt`) that tells crawlers which paths they may fetch. It is a *request*, not enforcement, but reputable crawlers honour it.
- **`noindex` meta tag / header** — tells the engine not to *index* the page (this is stage 2, but worth knowing now: `noindex` does **not** stop crawling, only indexing).
- **Server response codes** — `200` (OK), `301`/`302` (redirects, followed), `404` (gone), `5xx` (server error — crawler backs off and retries).
- **Internal linking** — if a page has no inbound internal links and isn't in a sitemap, it's effectively **orphaned** and may never be discovered.

### Practical rules

1. **Keep `robots.txt` minimal and correct.** Don't block CSS/JS — Google needs them to render your page.
2. **Submit an XML sitemap** in Search Console and Bing Webmaster Tools.
3. **Fix 5xx errors fast.** Repeated server errors train the crawler to slow down or back off.
4. **Link your important pages** from somewhere reachable. A sitemap helps; internal links help more.
5. **Don't rely on JS-only navigation** for critical content. If a link only exists after a click handler fires, many crawlers won't follow it.

> **Crawl budget** matters mainly for large sites (thousands+ of URLs). For most sites, the practical concern is simply: *can the crawler reach and fetch your page?*

---

## Stage 2 — Indexing

Once fetched, the page is **parsed** (HTML → content + structure) and **rendered** (JavaScript executed, if needed). The engine then extracts signals and stores the page in its **index** — a massive, queryable database.

### What the indexer extracts

- **Text content** — the visible words, weighted by structure (headings, emphasis, position)
- **Structure** — title, meta description, headings, lists, tables
- **Links** — internal and external, with anchor text
- **Structured data** — JSON-LD, microdata, RDFa (schema.org markup)
- **Media** — images (with alt text), video
- **Metadata** — canonical URL, `hreflang`, language, dates

### What blocks indexing

| Cause | Fix |
|---|---|
| `<meta name="robots" content="noindex">` | Remove it if the page should be indexed |
| `X-Robots-Tag: noindex` HTTP header | Remove the header |
| `robots.txt` blocking the URL | Unblock it (but note: a blocked URL can't be crawled to see its `noindex` — so unblock first) |
| Canonical pointing elsewhere | Fix the canonical to self-reference |
| Duplicate content | Consolidate or canonicalise |
| Content hidden behind interaction (tabs, accordions loaded on click, infinite scroll) | Render it server-side or in initial HTML |

### Practical rules

1. **Every indexable page should have a self-referencing canonical** (`<link rel="canonical" href="...">`).
2. **One page, one intent.** Don't split the same topic across near-duplicate URLs — consolidate.
3. **Test rendering.** Use Search Console's URL Inspection → "Test live URL" to see what Google actually renders.
4. **Check `site:yourdomain.com`** to see what's indexed — and spot pages that shouldn't be.
5. **`noindex` is a stage-2 tool.** It does not save crawl budget (the page is still fetched). To save crawl budget, use `robots.txt`; to remove from results, use `noindex`.

---

## Stage 3 — Ranking

When a user searches, the engine queries its index and **orders** the results. Ranking is not a single score — it's a system of many signals combined by learned models. The broad categories are stable:

| Signal family | What it captures | You influence it by |
|---|---|---|
| **Relevance** | Does the page match the query intent? | Keyword use, headings, content depth, entity coverage |
| **Quality** | Is the content trustworthy and useful? | Expertise, sourcing, originality, accuracy, E-E-A-T signals |
| **Authority** | Do others vouch for this page/site? | Inbound links, brand mentions, citations |
| **Technical health** | Can it be crawled, indexed, and served fast? | Core Web Vitals, mobile-friendliness, HTTPS, clean structure |
| **User signals** | How do users behave when they see it? | Click-through rate, dwell time, pogo-sticking (indirect) |
| **Context** | Location, language, device, freshness | Localisation, `hreflang`, publication dates |

### What ranking is *not*

- **Not a single "SEO score."** Third-party tools approximate; they don't replicate the engine.
- **Not purely keyword matching.** Modern ranking understands entities, intent, and semantics.
- **Not static.** Rankings fluctuate as the index updates, competitors publish, and models retrain.

### Practical rules

1. **Match intent first.** A page optimised for "buy" won't rank for "what is" — and vice versa.
2. **Cover the topic, not just the keyword.** Answer the follow-up questions a user will have.
3. **Earn links and mentions.** They remain the strongest off-page signal.
4. **Keep the technical floor clean.** Speed, mobile, HTTPS — table stakes, not differentiators.
5. **Measure, don't guess.** Use Search Console (queries, impressions, CTR, position) and iterate.

---

## The modern wrinkle: AI Overviews and AI answers

Here's the part most SEO guides still get wrong. **AI Overviews and AI Mode do not use a separate index or a separate ranking system.** Google has stated that they draw on the **same index and the same core ranking systems** as traditional Search. AI answers are a *presentation layer* on top of the classic pipeline.

That has three consequences:

1. **Part A is not optional.** If your page can't be crawled, indexed, and ranked well in traditional search, it won't be retrieved for AI answers either. Fixing the fundamentals is the prerequisite for AI visibility.
2. **Retrieval is the new battleground.** AI systems retrieve a subset of indexed pages to ground their answers. Being *retrievable* (crawlable, well-structured, clearly about a topic) matters more than ever.
3. **Citation is the new click.** When an AI answer cites you, that's visibility even without a click. Structuring content so it's easy to quote — clear claims, sourced facts, scannable structure — pays off.

Part B of this playbook covers the AI-specific tactics (GEO, AEO, `llms.txt`, structured data for retrieval, AI crawler management). But every one of them assumes the pipeline described on this page is healthy.

> See [How Traditional SEO and Modern AI SEO Connect](../how-they-connect.md) for the full picture.

---

## Diagnose in order

When a page underperforms, work through the pipeline **in sequence** — don't jump to "ranking" before confirming the earlier stages:

1. **Is it crawlable?** Check `robots.txt`, server response, internal links, sitemap.
2. **Is it indexed?** Check `site:` search, Search Console URL Inspection, `noindex` tags.
3. **Is it relevant?** Check query-intent match, content depth, heading structure.
4. **Is it authoritative?** Check inbound links, brand mentions, citations.
5. **Is it technically healthy?** Check Core Web Vitals, mobile rendering, HTTPS.
6. **Is it competitive?** Check what currently ranks — and whether you can genuinely do better.

Most problems are found at steps 1–2. Fix those before touching content or links.

---

## Key takeaways

- Search is a **three-stage pipeline**: crawl → index → rank. A page must pass all three.
- **Crawling** is controlled by `robots.txt`, links, sitemaps, and server responses.
- **Indexing** is controlled by `noindex`, canonicals, content rendering, and duplication.
- **Ranking** combines relevance, quality, authority, technical health, user signals, and context.
- **AI Overviews use the same index and ranking systems** — so traditional SEO fundamentals come first.
- **Diagnose in order.** Crawl and index failures masquerade as ranking problems.

---

**Next:** [02 — Keywords and Search Intent](02-keywords-and-intent.md) — how to find what people actually search for, and match your content to the intent behind the query.

---
*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../RESEARCH-LOG.md).*
