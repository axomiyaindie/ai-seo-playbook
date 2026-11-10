# 02 — GEO and AEO

> **Part B · Modern AI SEO** · [← Back to Modern AI SEO](../README.md) · Prev: [01 — Foundations](../01-foundations/README.md) · Next: [Google's AI Guide (2026)](google-ai-guide-2026.md)

Chapter 01 explained *how* AI answers are produced. This chapter covers *what to do about it*: the practical tactics for earning retrieval, citation, and recommendation in AI answers. Two related disciplines have emerged for this:

- **GEO** — Generative Engine Optimization: being used and cited in generative AI answers (AI Overviews, ChatGPT, Perplexity, Claude, Gemini).
- **AEO** — Answer Engine Optimization: being the direct answer — in featured snippets, voice results, and AI answers.

They overlap heavily. GEO is the broader term (any generative engine); AEO emphasises being *the answer* rather than merely a cited source. In practice, the tactics are largely the same. This chapter treats them together.

---

## Why GEO/AEO differs from traditional SEO

Traditional SEO optimises for **ranking a page**. GEO/AEO optimises for **being retrieved, quoted, and cited as a source** in a generated answer. The differences:

| | Traditional SEO | GEO / AEO |
|---|---|---|
| **Unit of optimisation** | The page | The passage / claim |
| **Goal** | Rank in the top 10 | Be retrieved and cited in the answer |
| **Success** | Clicks | Citations, mentions, referrals |
| **Key signal** | Relevance + authority | Retrievability + quotability + trust |
| **Audience** | Human reading links | Human reading a synthesised answer |
| **Competition** | Other pages | Other sources in the retrieval set |

The fundamentals from Part A still apply — crawlability, quality, authority — but GEO/AEO adds **citability** as a first-class concern.

---

## The core GEO/AEO principles

Six principles drive most GEO/AEO work. Each is expanded below.

1. **Be retrievable** — crawlable, indexed, clearly about the topic.
2. **Be quotable** — state claims clearly, in self-contained passages.
3. **Be authoritative** — earn trust signals the systems recognise.
4. **Be consistent** — same facts, same names, across your site and the web.
5. **Be structured** — headings, lists, tables, schema.
6. **Be fresh** — dated, updated, current.

---

## 1. Be retrievable

If the retrieval system can't find or fetch your page, nothing else matters.

**Tactics:**
- **Allow AI retrieval bots** in `robots.txt` (see [03 — Technical](../03-technical/README.md)). Distinguish training bots (blockable) from retrieval bots (must be allowed for AI visibility).
- **Server-render critical content.** JS-only content may not be retrieved.
- **Keep canonical URLs clean.** Duplicates dilute retrieval signals.
- **Submit sitemaps** (Search Console, Bing Webmaster Tools) — some AI systems use them.
- **Focus each page on a clear topic.** A page that's "about everything" is retrieved for nothing.

---

## 2. Be quotable

AI systems retrieve **passages** and quote **claims**. Content that's easy to extract and attribute gets cited more.

### Write self-contained passages

Each section should make sense on its own. A paragraph that only works when read in the context of the whole page is hard to retrieve.

**Weak:** "As we mentioned above, this approach has several benefits, which we'll explore in the next section."

**Strong:** "Server-side rendering improves AI retrieval because it ensures content is present in the initial HTML response, which is what most retrieval systems fetch."

The strong version can be quoted alone. The weak version can't.

### State claims explicitly

Vague claims are hard to cite. Explicit claims are easy.

**Weak:** "Our tool is quite fast compared to alternatives."

**Strong:** "Our tool processes 10,000 pages per minute, compared to a 1,000-page-per-minute median across the alternatives we benchmarked in 2026."

The strong version gives an AI something specific to attribute.

### Use structure AI can parse

- **Headings** that describe what the section answers.
- **Lists** for enumerable facts.
- **Tables** for comparisons — highly extractable.
- **Short paragraphs** — easier to extract than long ones.
- **Definitions** in a clear "X is Y" format.

### Front-load the answer

Put the answer in the first sentence or two of a section. AI systems often extract the opening of a passage. Don't bury the point.

**Weak:** Three paragraphs of context before the answer.

**Strong:** One-sentence answer, then context.

---

## 3. Be authoritative

AI systems cite sources they trust. Trust comes from the same signals as traditional E-E-A-T (Part A, chapter 05) — plus AI-specific considerations.

**Tactics:**
- **Named authors with credentials** — an AI system is more likely to cite content with a clear author.
- **Cited sources** — link to primary sources; don't assert facts without attribution.
- **Visible dates** — publish and update dates signal freshness and reliability.
- **Consistent brand identity** — same name, same description, across the web.
- **Third-party validation** — reviews, mentions, citations from reputable sites.
- **Organisation schema** — explicitly declare your organisation with `sameAs` links to authoritative profiles.

---

## 4. Be consistent

AI systems reason over **entities** (people, organisations, products, concepts). Inconsistent naming fragments your entity and dilutes recognition.

**Tactics:**
- **One canonical name.** Pick "Acme Corp" or "Acme Corporation" — not both. Use it everywhere.
- **Consistent descriptions.** The same one-sentence description across your site, LinkedIn, GitHub, Crunchbase, directories.
- **`sameAs` links** in `Organization` schema pointing to your authoritative profiles (Wikipedia, LinkedIn, Crunchbase, GitHub, X, etc.).
- **Consistent facts.** If your pricing, founding date, or key claims differ across sources, AI systems can't confidently cite any of them.
- **Entity pages.** A clear About page, a Team page, a Product page — each with consistent information.

---

## 5. Be structured

Structured data (schema.org JSON-LD) helps AI systems understand your content explicitly.

**High-value schemas for AI retrieval:**
- `Organization` — who you are, with `sameAs` links.
- `Person` — authors and team members, with credentials.
- `Article` / `BlogPosting` — content with author, dates, publisher.
- `FAQPage` — question-answer pairs, highly extractable.
- `HowTo` — step-by-step instructions.
- `Product` / `SoftwareApplication` — what you offer, with pricing.
- `BreadcrumbList` — hierarchy.

See [03 — Technical → Structured Data](../03-technical/structured-data.md) for implementation details.

**Beyond schema:**
- **Clear headings** (H2/H3) that describe sections.
- **Tables** for comparisons.
- **Lists** for enumerated facts.
- **FAQ sections** on key pages — these are directly extractable.

---

## 6. Be fresh

AI systems weight freshness for time-sensitive queries. Stale content loses citations to newer sources.

**Tactics:**
- **Visible "last updated" dates** — in the page, not just metadata.
- **Update content when facts change** — pricing, features, statistics, regulations.
- **Re-validate links** periodically.
- **Add new data** — refreshed statistics, new examples.
- **Don't fake freshness.** Changing the date without changing the content erodes trust.

---

## AEO specifics: being *the answer*

GEO is about being cited. AEO is about being **the direct answer** — the passage that the system extracts as the core response.

**AEO tactics:**
- **Question-shaped headings.** "What is X?" as an H2, followed by a direct answer.
- **Definitional openings.** "X is…" at the start of the relevant section.
- **FAQ sections.** Explicit question-answer pairs.
- **Step-by-step lists.** For "how to" queries.
- **Comparison tables.** For "X vs Y" queries.
- **Concise, direct answers** in the first sentence of each section.

**Example structure for a page targeting "what is llms.txt":**

```markdown
## What is llms.txt?

llms.txt is a proposed standard file placed at a site's root that provides
a curated, markdown-formatted map of the site's most useful content for
large language models.

## Why llms.txt matters

...
```

The first sentence is a complete, quotable definition. An AI system can extract it directly.

---

## What GEO/AEO does *not* mean

Some claims about AI SEO are speculative or overstated. Be sceptical of:

- **"AI SEO replaces traditional SEO."** No — it builds on it. Same index, same fundamentals.
- **"You need to write for AI, not humans."** No — AI systems are trained on human-quality content and prefer it. Write for humans; structure for retrieval.
- **"Keyword density matters for AI."** No — AI systems understand semantics; density is irrelevant (and harmful).
- **"There's a magic prompt or trick."** No — the tactics are grounded in how retrieval actually works: crawlability, clarity, structure, trust.
- **"AI content ranks better because AI wrote it."** No — quality and originality matter; the tool doesn't.

The legitimate tactics are the ones grounded in retrieval mechanics: be retrievable, quotable, authoritative, consistent, structured, and fresh.

---

## A GEO/AEO checklist

Use this per page that should earn AI visibility:

**Retrievability**
- [ ] Page is crawlable by AI retrieval bots
- [ ] Content is server-rendered (not JS-only)
- [ ] Canonical URL is clean
- [ ] Page has a clear topical focus
- [ ] Included in the XML sitemap

**Quotability**
- [ ] Each section is self-contained
- [ ] Claims are stated explicitly (not implied)
- [ ] Answer is front-loaded (first 1–2 sentences)
- [ ] Short paragraphs; lists and tables where useful
- [ ] Headings describe what the section answers

**Authority**
- [ ] Named author with credentials
- [ ] Sources cited for factual claims
- [ ] Visible publish and update dates
- [ ] Organisation and Person schema present
- [ ] Third-party validation (mentions, reviews, citations)

**Consistency**
- [ ] One canonical brand name
- [ ] Consistent one-sentence description across the web
- [ ] `sameAs` links in Organisation schema
- [ ] Consistent facts (pricing, dates, claims)

**Structure**
- [ ] Question-shaped headings where appropriate
- [ ] FAQ section on key pages
- [ ] Tables for comparisons
- [ ] Lists for enumerated facts
- [ ] Applicable schema (Article, FAQPage, HowTo, Product)

**Freshness**
- [ ] Visible last-updated date
- [ ] Content current (no stale facts)
- [ ] Links valid
- [ ] Date reflects real updates

---

## Common mistakes

1. **Blocking AI retrieval bots.** Removes you from AI answers entirely. Distinguish training from retrieval.
2. **Writing vague marketing copy.** Hard to quote; AI systems prefer specific claims.
3. **Burying the answer.** Three paragraphs before the point = missed citation.
4. **No author or dates.** Reduces trust and citability.
5. **Inconsistent brand naming.** Fragments your entity.
6. **No structured data.** Misses explicit machine-readable signals.
7. **Wall-of-text pages.** Hard to extract passages from.
8. **Stale content.** Newer sources win for time-sensitive queries.
9. **Chasing tricks.** No magic prompt; the tactics are grounded in retrieval mechanics.
10. **Ignoring traditional SEO.** AI visibility requires crawlability and quality first.

---

## Key takeaways

- **GEO** = being used and cited in generative AI answers; **AEO** = being the direct answer. Tactics overlap.
- Six principles: **retrievable, quotable, authoritative, consistent, structured, fresh**.
- **Quotability** is the key shift from traditional SEO — self-contained passages and explicit claims.
- **Front-load answers**; use question-shaped headings and FAQ sections.
- **Consistency** across the web strengthens your entity.
- **Structured data** (schema.org) helps AI systems understand you explicitly.
- **Freshness** matters for time-sensitive queries; date real updates honestly.
- AI SEO **builds on** traditional SEO; it doesn't replace it.

---

**Next:** [Google's AI Guide (2026)](google-ai-guide-2026.md) — a summary of Google's official guidance on AI features and how it maps to the tactics in this chapter.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*