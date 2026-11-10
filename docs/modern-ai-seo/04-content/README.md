# 04 — Content

> **Part B · Modern AI SEO** · [← Back to Modern AI SEO](../README.md) · Prev: [.well-known, Agents, and MCP](../03-technical/well-known-agents-and-mcp.md) · Next: [05 — Measurement](../05-measurement/README.md)

Technical work gets you retrieved. Content work gets you **cited**. This section covers the content decisions that determine whether AI systems choose your passage as the source for an answer: how to structure content so it's easy to quote, how to make your entities clear, and how to earn the brand mentions that AI systems use as trust signals.

The principles here build on [Part A → On-Page SEO](../../traditional-seo/03-on-page-seo.md) and [Part A → Content Quality](../../traditional-seo/05-content-and-spam-policies.md). What's new is the **passage-level** focus: AI systems retrieve and quote passages, not pages.

---

## The core shift: pages → passages

Traditional SEO optimises **pages**. AI retrieval optimises **passages** — specific chunks that answer a specific query.

This means:

| Traditional view | AI-retrieval view |
|---|---|
| "This page is about keyword research" | "This passage defines keyword research" |
| Optimise the whole page | Optimise individual claims and sections |
| Authority accrues to the page | Citability accrues to the passage |
| One ranking per query | Many possible citations per answer |

**The practical implication:** every section of every page should be able to stand alone as a quotable answer. If a paragraph only makes sense in context, it's harder to retrieve and cite.

---

## What makes content citable

AI systems cite content that is **clear, specific, and attributable**. Five properties drive citability:

### 1. Self-contained passages

Each section should make sense on its own.

**Weak:** "As we mentioned earlier, this approach has several benefits, which we'll cover below."

**Strong:** "Server-side rendering improves AI retrieval because it ensures content is present in the initial HTML response, which is what most retrieval systems fetch."

The strong version can be quoted without any surrounding context. It's a complete, attributable claim.

**How to write self-contained passages:**
- Lead with the claim, then explain.
- Avoid backward references ("as mentioned above").
- Name entities explicitly (don't rely on "it" or "this").
- Include the context needed to understand the passage.

### 2. Explicit claims

Vague claims are hard to cite. Specific claims are easy.

**Weak:** "Our tool is quite fast compared to alternatives."

**Strong:** "Our tool processes 10,000 pages per minute, compared to a 1,000-page-per-minute median across the alternatives we benchmarked in 2026."

The strong version has:
- A **specific number** (10,000)
- A **comparison** (vs. 1,000 median)
- A **scope** (benchmarked alternatives)
- A **date** (2026)

Each of those makes it more quotable.

**How to write explicit claims:**
- Replace adjectives with numbers where possible.
- Name the source or method.
- Include the date.
- Specify the scope (who, what, when).

### 3. Front-loaded answers

Put the answer in the first sentence or two of a section. AI systems often extract the opening of a passage.

**Weak:** Three paragraphs of context before the answer.

**Strong:** "The answer is X. Here's why: …"

**How to front-load:**
- Use **inverted pyramid** structure: answer first, then context.
- **Question-shaped headings** followed immediately by a direct answer.
- **Definitional openings**: "X is …" at the start of the relevant section.

### 4. Structure AI can parse

AI systems parse structure. Explicit structure helps.

| Structure | When to use |
|---|---|
| **Headings** | Every section; descriptive, not keyword-stuffed |
| **Lists** | Enumerated facts, steps, options |
| **Tables** | Comparisons, structured data, feature matrices |
| **Short paragraphs** | Default; easier to extract than long ones |
| **Definition lists** | Term → meaning pairs (great for glossaries) |
| **Code blocks** | Technical instructions, configurations |

**Tables are especially valuable.** A comparison table is one of the most extractable formats — an AI system can lift the entire table or a specific row and cite it directly.

### 5. Sourced, dated facts

Cited claims are more likely to be trusted and re-cited.

**Rules:**
- **Link to primary sources** — not a blog that cites the source.
- **Date every claim** that could go stale.
- **Name the method** — "based on a survey of 500 SEOs in 2026" beats "research shows."
- **Use consistent facts** across your site (see entity clarity, below).

---

## Entities: the other half of content

AI systems reason over **entities** (people, organisations, products, concepts), not just keywords. Content that clearly establishes and reinforces entities is more retrievable and citable.

### What entity clarity looks like

- **One canonical name** for each entity, used consistently.
- **`sameAs` links** in structured data (see [03 — Structured Data](../03-technical/structured-data.md)).
- **Explicit definitions** of key entities.
- **Consistent facts** across your site and the web.
- **Entity pages** — About, Team, Product, with clear information.

### Entity SEO in practice

**For an organisation:**
- Homepage `Organization` schema with `sameAs` links to LinkedIn, GitHub, Crunchbase, Wikipedia.
- An About page with consistent history, mission, team.
- A Team page with `Person` schema for each person.
- Consistent naming everywhere (pick "Acme Analytics" or "Acme", not both).

**For people (authors):**
- Author pages with `Person` schema, `sameAs` links to LinkedIn, Twitter, Scholar.
- Byline on every article with a link to the author page.
- Credentials visible (job title, expertise).

**For products:**
- Product pages with `Product` / `SoftwareApplication` schema.
- Consistent naming, versioning, pricing.
- Reviews and ratings (genuine).

**For concepts:**
- A glossary page defining key terms.
- Internal links from articles to the glossary.
- Consistent definitions across your content.

---

## Brand mentions: the AI-era backlink

Backlinks still matter (Part A, chapter 06). But for AI visibility, **brand mentions** — with or without links — are increasingly important. AI systems use mentions as trust signals: a brand mentioned across many sources is more likely to be cited.

### How to earn brand mentions

- **Original research** — journalists cite data and name the source.
- **Expert commentary** — being quoted (Featured, Qwoted, HARO) earns mentions.
- **Community participation** — genuine helpfulness in forums, Slack communities, Reddit.
- **Podcasts and interviews** — show notes mention guests.
- **Open source** — contributions to projects (README mentions, contributor lists).
- **Speaking** — conference bios, session pages.

### Unlinked mentions are valuable

Traditional SEO focused on **links**. AI systems also value **mentions** — even unlinked. If a reputable source says "Acme Analytics reported X," that's a trust signal even without a hyperlink.

**What this means:**
- Don't obsess over turning every mention into a link (though asking politely is fine).
- Focus on **earning the mention** through value.
- **Monitor mentions** (Google Alerts, brand monitoring tools) and respond where appropriate.

---

## Passage-level optimisation in practice

Here's how to apply the principles above to a real page.

### Before: page-level structure

```markdown
# Keyword Research: A Complete Guide

Keyword research is really important for SEO. There are many tools you can use.
We'll cover everything you need to know.

## Introduction

As we mentioned, keyword research is important. Many people think it's just about
finding keywords, but it's really about understanding intent...

## Tools

There are many tools. Some are free, some are paid. They all have pros and cons...

## Conclusion

Keyword research is important. Do it well.
```

**Why this fails AI retrieval:**
- Vague, front-loaded with filler.
- No explicit claims.
- Sections don't stand alone.
- No specific facts, dates, or sources.

### After: passage-level structure

```markdown
# Keyword Research: A Complete Guide

Keyword research is the process of finding the queries people use to search
for a topic, grouping them by intent, and deciding which ones a site can
realistically rank for. It has three dimensions: intent, volume, and difficulty.

## What are the four types of search intent?

Search intent falls into four categories:

| Intent | User wants | Query shape |
|---|---|---|
| Informational | To learn | "what is", "how to" |
| Navigational | To reach a specific site | brand names |
| Commercial | To compare before buying | "best", "vs", "review" |
| Transactional | To do/buy now | "buy", "price" |

The same topic can appear in all four intents — each needs a different page.

## How do you identify search intent?

Read the query literally and check what already ranks. If page 1 is all
how-to guides, a product page won't win — no matter how well optimised.

## Key takeaways

- Keyword research is demand research, not string matching.
- The four intents — informational, navigational, commercial, transactional
  — each need a different page format.
- Cluster related keywords into one strong page; don't split them.
```

**Why this works:**
- Answers are **front-loaded** under question-shaped headings.
- Claims are **explicit** (specific categories, specific tests).
- **Tables** are highly extractable.
- Each section **stands alone**.
- **Key takeaways** are quotable summaries.

---

## Content types that get cited

Some content formats are especially citable. Prioritise these if AI visibility is a goal:

| Format | Why it gets cited |
|---|---|
| **Definitions** | "X is Y" — directly quotable |
| **Comparisons** | Tables and structured trade-offs |
| **How-to steps** | Numbered, extractable instructions |
| **FAQ sections** | Q&A pairs — the most quotable format |
| **Original data** | Numbers journalists and AI systems cite |
| **Glossaries** | Term → definition pairs |
| **Benchmarks** | Performance comparisons with methodology |
| **Case studies** | Specific outcomes with context |

**What's less citable:**
- Opinion pieces without specific claims
- Vague marketing copy
- Long-form pieces with buried answers
- Content that copies other sources

---

## The citability checklist

Per page:

**Structure**
- [ ] Question-shaped headings where appropriate
- [ ] Answers front-loaded (first 1–2 sentences)
- [ ] Short paragraphs
- [ ] Lists and tables for structured facts
- [ ] Each section self-contained

**Claims**
- [ ] Explicit, specific claims (not vague)
- [ ] Numbers where possible
- [ ] Sources linked (primary sources)
- [ ] Dates on time-sensitive claims
- [ ] Methods named ("based on X")

**Entities**
- [ ] Key entities defined explicitly
- [ ] Consistent naming
- [ ] `Organization` / `Person` / `Product` schema (see [03 — Structured Data](../03-technical/structured-data.md))
- [ ] `sameAs` links in schema
- [ ] Author byline with credentials

**Authority**
- [ ] Named author
- [ ] Author page with `Person` schema
- [ ] Visible publish and update dates
- [ ] Third-party mentions (where earned)
- [ ] No unsupported claims

**AI-specific**
- [ ] Passage-level self-containment
- [ ] FAQ section (if appropriate)
- [ ] Definitional openings
- [ ] Key takeaways section (optional but valuable)

---

## Common mistakes

1. **Writing for "SEO" rather than readers.** AI systems prefer human-quality content; the same standards apply.
2. **Burying the answer.** Lead with the answer; context comes after.
3. **Vague claims.** Specificity makes content quotable.
4. **No sources or dates.** Erodes trust and citability.
5. **Long paragraphs.** Hard to extract; break them up.
6. **Inconsistent brand naming.** Fragments your entity across the web.
7. **No author attribution.** Hurts E-E-A-T and citation trust.
8. **Ignoring entity clarity.** AI systems reason over entities, not just keywords.
9. **No FAQ sections.** Misses an obvious opportunity for direct Q&A extraction.
10. **Copying competitors.** Duplicates don't get cited — originality does.

---

## Key takeaways

- **Pages → passages.** AI systems retrieve and quote passages, not pages.
- **Five properties drive citability:** self-contained, explicit, front-loaded, structured, sourced.
- **Entity clarity** is the other half of content — AI systems reason over entities.
- **Brand mentions** (linked or not) are the AI-era trust signal.
- **Question-shaped headings** and **FAQ sections** are the most extractable formats.
- **Tables, lists, and definitions** are highly quotable.
- **Specific claims** (numbers, dates, sources) beat vague marketing copy.
- **Original content** gets cited; duplicates don't.

---

**Next:** [05 — Measurement](../05-measurement/README.md) — tracking AI visibility, citations, and AI referral traffic.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*