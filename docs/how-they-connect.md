# How Traditional SEO and Modern AI SEO Connect

> Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). [Part A — Traditional SEO](traditional-seo/README.md) · [Part B — Modern AI SEO](modern-ai-seo/README.md)

The playbook is split into two parts for a reason: **Traditional SEO (Part A)** and **Modern AI SEO (Part B)** are different disciplines, but they are not separate systems. Part B sits *on top of* Part A. This page explains how, so you know why Part A comes first and what Part B adds.

---

## The short version

**AI Overviews, ChatGPT, Perplexity, Claude, Gemini and Copilot do not use a separate index or a separate ranking system.** Google has stated that AI Overviews and AI Mode draw on the **same index and the same core ranking systems** as traditional Search. AI answers are a **presentation layer** on top of the classic crawl → index → rank pipeline.

That means:

1. **If your page can't be crawled, indexed, and ranked well in traditional search, it won't be retrieved for AI answers either.**
2. **Part A is the prerequisite, not the alternative.** Fixing the fundamentals is what makes AI visibility possible.
3. **Part B adds tactics** that improve the odds of being *retrieved, cited, and quoted* — but those tactics assume the pipeline described in Part A is healthy.

---

## The two-part model

| | **Part A · Traditional SEO** | **Part B · Modern AI SEO** |
|---|---|---|
| **Goal** | Crawled, indexed, ranked in classic search | Cited, recommended, acted on by AI |
| **Audience** | Human searchers clicking blue links | Humans reading AI answers (with or without clicks) |
| **Core unit** | The page | The passage / claim / entity |
| **Primary signals** | Relevance, quality, authority, technical health | Retrieval, structure, citability, entity clarity |
| **Success metric** | Rankings, organic traffic, conversions | AI citations, brand mentions, AI referral traffic |
| **When to do it** | First | After Part A fundamentals are in place |

Both parts matter. Neither replaces the other. A site with strong Part A and no Part B is invisible in AI answers. A site chasing Part B without Part A has nothing to retrieve.

---

## What carries over from Part A

These Part A fundamentals **directly determine** AI visibility:

| Part A concept | How it affects AI visibility |
|---|---|
| **Crawlability** (04) | AI retrieval bots must be able to fetch your pages. Blocking them means disappearing from AI answers. |
| **Indexability** (04) | If a page isn't in the index, it can't be retrieved to ground an AI answer. |
| **Rendering** (04) | If content is JS-only, retrieval systems may miss it. |
| **Canonicalisation** (04) | Duplicates dilute signals; AI systems prefer clear, canonical sources. |
| **Intent match** (02, 03) | AI systems retrieve pages that clearly answer the query's intent. |
| **Content quality** (05) | AI systems are trained to prefer helpful, accurate, sourced content. |
| **E-E-A-T** (05) | Trust signals matter for citation — AI systems favour sources they can vouch for. |
| **Authority / links** (06) | Backlinks and brand mentions correlate with which sources AI systems cite. |
| **Measurement discipline** (07) | The same iteration loop applies — you just add AI-specific metrics. |

**Nothing in Part A becomes obsolete.** AI search raises the bar on some of it (quality, citability, entity clarity) and adds new surface area, but the foundation is the same.

---

## What Part B adds

Part B introduces tactics that **don't exist in traditional SEO**:

### 1. AI crawler management
Traditional SEO manages Googlebot and Bingbot. AI SEO also manages **training crawlers** (GPTBot, ClaudeBot, Google-Extended, CCBot) vs. **retrieval crawlers** (OAI-SearchBot, Claude-SearchBot, PerplexityBot) vs. **user-triggered fetchers** (ChatGPT-User, Claude-User). These are different bots with different purposes — blocking one doesn't block the others. Part B covers the distinction and how to configure `robots.txt` and `ai.txt` accordingly.

### 2. `llms.txt`
A proposed standard (still emerging) for giving LLMs a curated map of your site's most useful content. Not yet widely honoured, but a low-cost hedge and a signal of AI-readiness. Part B covers the format and when it's worth adding.

### 3. Structured data for retrieval
Traditional SEO uses schema.org markup for rich results. AI SEO uses it to make content **machine-readable and quotable** — `Article`, `FAQPage`, `HowTo`, `Organization`, `Person`, `Product`, plus emerging `.well-known` files for agent discovery. Part B covers which schemas matter for AI retrieval.

### 4. Citability and passage-level optimisation
AI systems retrieve **passages**, not whole pages. Part B covers how to structure content so specific claims are easy to extract, attribute, and quote — clear headings, self-contained paragraphs, sourced facts, scannable structure.

### 5. Entity and brand clarity
AI systems reason over **entities** (people, organisations, products, concepts), not just keywords. Part B covers entity clarity: consistent naming, `sameAs` links, `Organization` schema, knowledge-panel alignment, and brand mentions across the web.

### 6. GEO / AEO tactics
**Generative Engine Optimization** and **Answer Engine Optimization** are the AI-era counterparts to on-page SEO. Part B covers the practical tactics — direct answers, question-shaped headings, cited sources, comparison tables, structured summaries — and Google's own published AI guidance.

### 7. AI measurement
Traditional measurement tracks rankings and clicks. AI measurement adds: **citation tracking** (is your page cited in AI answers?), **AI referral traffic** (ChatGPT, Perplexity send referrers), **share of AI answers** for target prompts, and **brand mentions in AI outputs**. Part B covers the tools and methods.

### 8. The agentic layer
Beyond search and citation, AI agents (MCP, A2A) are becoming a discovery and transaction surface. `.well-known/agent-card.json` and `.well-known/mcp-server-card.json` let agents find and use your services. Part B covers the emerging standards.

---

## The mental model

Think of it as three layers:

```
┌─────────────────────────────────────────────┐
│  Layer 3: Agentic & transactional           │  ← Part B (what's next)
│  MCP, A2A, agentic commerce                 │
├─────────────────────────────────────────────┤
│  Layer 2: AI retrieval & citation           │  ← Part B (core AI SEO)
│  GEO, AEO, llms.txt, structured data,       │
│  citability, entity clarity, AI crawlers    │
├─────────────────────────────────────────────┤
│  Layer 1: Classic search pipeline           │  ← Part A (foundation)
│  Crawl → index → rank                       │
│  On-page, technical, content, links,        │
│  measurement                                │
└─────────────────────────────────────────────┘
```

**Layer 1 is the foundation.** Layer 2 retrieves from it. Layer 3 acts on it. You cannot skip Layer 1 — there is nothing for Layers 2 and 3 to work with.

---

## A practical sequencing

If you're starting from scratch or auditing an existing site, do it in this order:

1. **Fix Part A fundamentals first.**
   - Can your key pages be crawled and indexed? (Ch. 04)
   - Do they match query intent? (Ch. 02, 03)
   - Is the content genuinely helpful and trustworthy? (Ch. 05)
   - Do you have some authority? (Ch. 06)
   - Can you measure it? (Ch. 07)

2. **Then add Part B's retrieval layer.**
   - Unblock AI retrieval bots (but consider training bots separately). (Part B → Technical)
   - Structure content for citability — clear claims, sourced facts, scannable passages. (Part B → Content)
   - Add `llms.txt` and structured data where they help. (Part B → Technical)
   - Clarify entities (organisation schema, consistent naming). (Part B → Content)

3. **Then track AI visibility.**
   - Monitor AI referral traffic. (Part B → Measurement)
   - Track citations for target prompts. (Part B → Measurement)
   - Iterate based on what gets cited. (Part B → Measurement)

4. **Explore the agentic layer when relevant.**
   - If you have a service agents could use, publish `.well-known` cards. (Part B → What's next)
   - If you sell products, monitor agentic commerce developments. (Part B → What's next)

---

## Common misconceptions

| Misconception | Reality |
|---|---|
| "AI SEO replaces traditional SEO." | AI SEO **builds on** traditional SEO. The index and ranking systems are shared. |
| "I should block all AI bots to protect my content." | Blocking training bots is a choice. Blocking **retrieval** bots removes you from AI answers. Distinguish them. |
| "AI Overviews use a different index." | Google has stated they use the **same index and ranking systems**. |
| "Rankings don't matter anymore." | They still determine what gets retrieved for AI answers. They matter *more*, not less. |
| "I just need `llms.txt`." | `llms.txt` is a low-cost hedge, not a substitute for crawlable, well-structured, citable content. |
| "AI SEO is all speculation." | Some tactics are emerging, but the core (crawlability, quality, structure, citability) is grounded in how retrieval actually works. |
| "If I'm cited, I don't need clicks." | Citation without a click is still visibility and brand value. But you still want the click where possible — structure pages to earn both. |

---

## Key takeaways

- **AI answers sit on the same crawl → index → rank pipeline** as traditional search.
- **Part A is the prerequisite.** Fix crawlability, indexability, quality, and intent match before anything in Part B.
- **Part B adds**: AI crawler management, `llms.txt`, structured data for retrieval, citability, entity clarity, GEO/AEO tactics, AI measurement, and the agentic layer.
- **Nothing in Part A becomes obsolete.** AI search raises the bar on quality and citability; it doesn't replace fundamentals.
- **Sequence matters.** Layer 1 → Layer 2 → Layer 3. Skipping Layer 1 leaves nothing to retrieve.
- **Distinguish training bots from retrieval bots.** They have different purposes; blocking one doesn't block the other.

---

**Next:** [Part A — Traditional SEO](traditional-seo/README.md) (if you haven't done it) or [Part B — Modern AI SEO](modern-ai-seo/README.md) (if you have).

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](RESEARCH-LOG.md).*