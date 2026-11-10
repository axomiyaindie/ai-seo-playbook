# 01 — Foundations: How AI Answers Are Produced

> **Part B · Modern AI SEO** · [← Back to Modern AI SEO](../README.md) · Next: [02 — GEO and AEO](../02-geo-aeo/README.md)

Before you can optimise for AI answers, you need a working model of how they're produced. This chapter explains the pipeline behind tools like ChatGPT, Perplexity, Claude, Gemini, and Google AI Overviews: how they retrieve content, how they decide what to cite, and why some pages get quoted while others are invisible.

The core idea: **AI answers are a retrieval-and-citation problem, not a ranking problem — but they sit on top of the same index and ranking systems as traditional search.** Part A got you into that index. This chapter explains what happens next.

---

## The two kinds of AI answer

Not all AI answers work the same way. Distinguish them, because the tactics differ.

### 1. Parametric answers (from training data)
The model answers from what it learned during training. No live retrieval. The answer reflects the model's weights as of its training cutoff.

- **Example:** "What is the capital of France?" — answered from training.
- **Implication:** You cannot influence this directly by publishing content *now*. You influence it only if your content was in the training data — and even then, indirectly.

### 2. Retrieval-augmented answers (RAG)
The model **retrieves** relevant content at query time, then **generates** an answer grounded in what it retrieved, often with **citations**.

- **Example:** "What's the best SEO playbook for AI search?" — the system searches the web, retrieves candidate pages, and synthesises an answer citing them.
- **Implication:** This is where AI SEO lives. You can influence retrieval and citation directly by making your content crawlable, retrievable, and citable.

Most modern AI search products (ChatGPT search, Perplexity, Google AI Overviews, Copilot, Gemini) use **RAG** for factual, current, or sourceable queries. That's the pipeline this chapter focuses on.

---

## The RAG pipeline

A retrieval-augmented answer goes through five stages:

```
Query → Retrieve → Rerank → Generate → Cite
```

Each stage is a filter. A page must survive **all five** to be cited. Understanding each stage tells you what to optimise.

### Stage 1 — Query understanding
The system interprets the user's query: intent, entities, constraints, and whether retrieval is needed at all. Some queries are answered parametrically; others trigger retrieval.

**What you influence:** nothing directly at this stage. But **query intent** (Part A, chapter 02) determines what kind of content gets retrieved.

### Stage 2 — Retrieval
The system searches an index (often a web search API, sometimes a proprietary index) for candidate passages. This is where **crawlability and indexability** (Part A, chapter 04) matter most.

**What you influence:**
- Whether your page is **crawlable** by the retrieval system's bot (see [03 — Technical](../03-technical/README.md)).
- Whether your page is **indexed** and discoverable.
- Whether your content is **clearly about the query topic** (relevance signals).
- Whether your page is **structured** so passages can be extracted (see [04 — Content](../04-content/README.md)).

**What fails here:** pages blocked by `robots.txt`, JS-only content, thin pages, pages that don't clearly match the query intent.

### Stage 3 — Reranking
The system takes the retrieved candidates and **reranks** them by relevance, quality, freshness, authority, and other signals. Only the top few passages make it into the answer.

**What you influence:**
- **Quality signals** (E-E-A-T, sourcing, accuracy) — see Part A, chapter 05.
- **Authority signals** (links, brand mentions) — see Part A, chapter 06.
- **Freshness** (visible dates, updated content).
- **Passage clarity** — self-contained, quotable passages rerank better than meandering prose.

**What fails here:** pages that are technically retrievable but lose the reranking to better-sourced, clearer, more authoritative competitors.

### Stage 4 — Generation
The model generates an answer **grounded in the retrieved passages**. It synthesises, summarises, and quotes. How it uses your content depends on how clearly your claims are stated and how easy they are to extract.

**What you influence:**
- **Citability** — clear, self-contained claims are easier to quote.
- **Structure** — headings, lists, tables, and short paragraphs make extraction easier.
- **Explicit facts** — "X is Y" is easier to cite than a paragraph that implies it.
- **Sourcing** — cited claims are more likely to be trusted and re-cited.

**What fails here:** content that's technically retrieved but hard to quote — buried claims, ambiguous phrasing, claims that require reading the whole page to understand.

### Stage 5 — Citation
The system attributes claims to sources. Not every retrieved page gets cited; the system cites what it actually used.

**What you influence:**
- **Being the clearest source** for a specific claim.
- **Being consistent** — the same fact stated the same way across your site and the web.
- **Being authoritative** — cited sources tend to be ones the system trusts.

**What fails here:** pages that were retrieved but whose claims were superseded by clearer or more authoritative sources.

---

## Why citations happen

A system cites a source when:

1. **The claim needs attribution** — factual, specific, or contestable claims are more likely to be cited than common knowledge.
2. **The source is retrievable and relevant** — it survived stages 1–3.
3. **The source is quotable** — the claim is clearly stated and easy to extract.
4. **The source is trustworthy** — it has authority signals the system recognises.

You can't force a citation. You can make your content **more likely to be cited** by optimising each of the four conditions.

---

## Passage-level retrieval (the key shift)

Traditional SEO optimises **pages**. AI retrieval optimises **passages** — specific chunks of a page that answer a specific query.

This is the most important conceptual shift in Part B:

| Traditional SEO | AI retrieval |
|---|---|
| One page ranks for a query | One passage is retrieved for a query |
| Optimise the whole page | Optimise individual passages |
| Think in pages | Think in claims, sections, and self-contained answers |
| Page-level authority | Passage-level relevance + page-level authority |

**What this means in practice:**
- Each **section** of a page should be understandable on its own.
- Each **claim** should be stated clearly enough to be quoted without surrounding context.
- **Headings** should describe what the section answers.
- **Short paragraphs** are easier to extract than long ones.
- **Tables and lists** are highly extractable — use them for comparisons and structured facts.

---

## The different AI search products

Each product retrieves and cites differently. The principles above apply to all, but the specifics vary.

| Product | Retrieval | Citation style | Notes |
|---|---|---|---|
| **Google AI Overviews** | Google's index + ranking systems | Links to sources in the overview | Uses the same index as classic search — Part A fundamentals are critical |
| **ChatGPT (search mode)** | Bing-backed web search + OpenAI's own | Inline citations with links | Referral traffic is trackable; user-triggered fetches (`ChatGPT-User`) |
| **Perplexity** | Own index + web search | Numbered citations, prominent source list | Heavily citation-focused; referral traffic trackable |
| **Claude (web search)** | Web search when enabled | Inline citations | `Claude-SearchBot` for retrieval, `Claude-User` for user-triggered |
| **Gemini** | Google's index | Links in answers | Same index as Google Search |
| **Copilot** | Bing's index | Inline citations | Bing Webmaster Tools matters here |

**Common thread:** all of them retrieve from a web index and cite sources. Optimising for retrieval and citability helps across all of them. The [03 — Technical](../03-technical/README.md) chapter covers bot-specific details.

---

## What this means for your site

The foundations chapter leads to five practical conclusions, each expanded in later chapters:

1. **Crawlability and indexability come first.** If AI retrieval bots can't fetch your pages, nothing else matters. See [03 — Technical](../03-technical/README.md).
2. **Structure content at the passage level.** Self-contained sections, clear claims, scannable structure. See [04 — Content](../04-content/README.md).
3. **Be citable.** State facts clearly, cite your own sources, use explicit language. See [04 — Content](../04-content/README.md).
4. **Clarify entities.** AI systems reason over entities (people, organisations, products). Consistent naming, `sameAs` links, and organisation schema help. See [04 — Content](../04-content/README.md).
5. **Measure AI visibility.** Citations and AI referral traffic are trackable. See [05 — Measurement](../05-measurement/README.md).

---

## Common misconceptions

| Misconception | Reality |
|---|---|
| "AI answers use a separate index." | Google AI Overviews use the same index and ranking systems as classic search. Other products use web search APIs. |
| "If I'm in ChatGPT's training data, I'll be cited." | Retrieval is query-time; training data is fixed at cutoff. RAG uses live retrieval, not just training. |
| "Citations are random." | Citations follow from retrieval, reranking, quotability, and trust — all influenceable. |
| "I just need to rank #1." | Ranking helps retrieval, but citation depends on passage-level clarity and quotability. |
| "AI SEO is separate from traditional SEO." | It builds on it. Same index, same fundamentals, plus retrieval and citability. |
| "If I'm cited, I get traffic." | Not always — AI answers often satisfy the query without a click. Citation is visibility even without traffic. |

---

## Key takeaways

- AI answers come in **two kinds**: parametric (from training) and **retrieval-augmented (RAG)**. AI SEO focuses on RAG.
- RAG has **five stages**: query → retrieve → rerank → generate → cite. A page must survive all five.
- **Retrieval** depends on crawlability, indexability, and topic clarity (Part A fundamentals).
- **Reranking** depends on quality, authority, freshness, and passage clarity.
- **Citation** depends on being the clearest, most trustworthy source for a specific claim.
- **Passage-level retrieval** is the key shift: optimise sections and claims, not just pages.
- Different AI products retrieve differently, but the **principles are shared**.
- **Part A is the foundation** — AI SEO builds on crawlability, quality, and structure.

---

**Next:** [02 — GEO and AEO](../02-geo-aeo/README.md) — the practical tactics for earning AI visibility: Generative Engine Optimization and Answer Engine Optimization.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*