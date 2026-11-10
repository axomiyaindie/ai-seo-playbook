# GEO/AEO Implementation Playbook

> **Part B · Modern AI SEO** · [← Back to GEO and AEO](README.md) · Next: [Google's AI Guide (2026)](google-ai-guide-2026.md)

Chapter 02 explained *what* GEO and AEO are and *why* they work. This page is the execution layer: a phased plan for moving from traditional SEO to AI-search readiness, prioritised by impact and sequenced for teams with limited time.

The core premise: **AI visibility is not a single switch you flip. It is a stack of layers, each building on the last.** Technical access comes first. Then structured data. Then content restructuring. Then new content written to standard. Then tracking. Then ongoing freshness.

This playbook follows a six-phase framework adapted from practitioner guidance on transitioning from traditional SEO to AI search [citation:2]. It assumes Part A fundamentals are already in place.

---

## Before you start: the baseline problem

The most common mistake in GEO/AEO implementation is **changing things before measuring anything**. If you restructure content and add schema without a baseline, you cannot tell whether it worked.

**Before Phase 1**, do this:

1. **Pick 20–50 target prompts.** These are the questions your audience asks AI engines. Include brand queries, category queries, comparison queries, and problem queries.
2. **Run each prompt across the engines that matter to you.** At minimum: ChatGPT, Perplexity, Google AI Overviews (if visible), and Gemini.
3. **Record**: Does the answer cite your domain? Does it mention your brand? Which competitors appear?
4. **Save the raw answers.** You will need them to compare after implementation.

This baseline is your only way to know whether the work paid off. Without it, you are optimising blind.

---

## Phase 1 — Technical AI Readiness Audit

**Goal:** Ensure AI retrieval systems can reach, fetch, and render your content.

**Timeline:** 1 week.

### The audit

**1. Check `robots.txt` for AI bot access.**

This is the single most common failure point. Sites often block "AI bots" to protect content and accidentally remove themselves from AI answers.

Verify these are **allowed** (not blocked):
- `OAI-SearchBot` (ChatGPT search retrieval)
- `PerplexityBot` (Perplexity retrieval)
- `Claude-SearchBot` (Claude search retrieval)
- `Googlebot` (covers both Google Search and AI Overviews)

Verify these can be **blocked** (training bots — your choice):
- `GPTBot`, `ClaudeBot`, `Google-Extended`, `CCBot`, `Bytespider`

See [AI Crawlers](../03-technical/ai-usage-preferences.md) for the full breakdown.

**2. Check for WAF or CDN rules blocking unknown bots.**

Cloudflare, Akamai, and similar services sometimes block bots they do not recognise. If `OAI-SearchBot` or `PerplexityBot` is being blocked at the edge, `robots.txt` changes will not help. Check your WAF logs for rejected requests from AI crawler user-agents.

**3. Verify server-rendering.**

Fetch a page as a crawler would (without JavaScript execution). If the main content is missing from the initial HTML, AI retrieval systems may miss it. Use Search Console's URL Inspection → Test Live URL to see what Google renders.

**4. Verify sitemap and indexing.**

Confirm your XML sitemap lists only canonical, indexable, `200`-status URLs. Submit it to Bing Webmaster Tools as well as Search Console — Bing's index feeds some AI retrieval systems [citation:2].

### Output

A checklist of fixes, prioritised by whether they block retrieval entirely (critical) or merely slow it (important).

---

## Phase 2 — Schema Sprint

**Goal:** Add the structured data types that most directly support AI extraction.

**Timeline:** 2–3 weeks.

This phase produces the **fastest visible gains** because structured data removes ambiguity that keeps pages out of AI answers [citation:2]. AI systems parse entities, relationships, and claims; schema hands them those entities directly [citation:4].

### Priority schema types

**Tier 1 (implement first):**

| Schema | Where | Why |
|---|---|---|
| `Organization` | Homepage | Defines your brand entity with `sameAs` links to LinkedIn, Crunchbase, Wikipedia, Wikidata. This is how AI systems connect your site to your entity [citation:4][citation:13]. |
| `Article` / `BlogPosting` | Every content page | Headline, author, publisher, `datePublished`, `dateModified`. Recency matters: 76.4% of ChatGPT's top 1,000 cited pages were updated within the previous 30 days [citation:1]. |
| `FAQPage` | Pages with FAQ sections | Explicit Q&A pairs are easier for AI to extract and cite than prose [citation:4][citation:13]. |
| `Person` | Author bio pages | Credentials, `jobTitle`, `sameAs` links. Supports E-E-A-T and makes authorship machine-readable [citation:4]. |

**Tier 2 (implement next):**

| Schema | Where | Why |
|---|---|---|
| `HowTo` | Step-by-step guides | Ordered steps map cleanly to how-to answers [citation:4]. |
| `Product` / `SoftwareApplication` | Product/pricing pages | Price, availability, reviews — supports comparison and recommendation queries [citation:4]. |
| `BreadcrumbList` | All pages | Hierarchy context, especially useful for large sites [citation:13]. |

### Implementation rules

1. **Use JSON-LD.** Google's preferred format, and the easiest to maintain across templates [citation:4].
2. **Nest entities.** Don't write `"author": "Jane Doe"`. Write `"author": {"@type": "Person", "name": "Jane Doe", "sameAs": [...]}`. Nested entities are more informative [citation:13].
3. **Mark up only visible content.** AI systems cross-check structured data against rendered text. Marking up hidden content is a spam signal [citation:13].
4. **Validate.** Run every page through Google's Rich Results Test and the Schema.org validator before deploying.

### The `sameAs` pattern (critical for entity recognition)

For `Organization` schema, `sameAs` is where entity clarity lives. Include:

```json
"sameAs": [
  "https://www.linkedin.com/company/your-company",
  "https://github.com/your-org",
  "https://crunchbase.com/organization/your-company",
  "https://en.wikipedia.org/wiki/Your_Company",
  "https://www.wikidata.org/wiki/Q..."
]
```

The more authoritative profiles you link, the clearer your entity becomes to AI systems [citation:13].

### Output

All Tier 1 schema live and validated. Tier 2 scheduled for the next sprint.

---

## Phase 3 — Content Restructuring Sprint

**Goal:** Make existing high-value content extractable and citable.

**Timeline:** 4–8 weeks, depending on site size.

Do not rewrite everything. Focus on **top 20–30 pages by organic traffic**, and specifically pages that rank for queries where AI Overviews or Perplexity answers appear [citation:2].

### The restructuring checklist (per page)

**1. Add a direct answer block at the top.**

Each section that answers a question should lead with a **40–60 word direct answer**, followed by supporting detail [citation:2]. This mirrors how AI engines extract: they look for clean, self-contained statements they can lift into a summary.

**Weak:**
> Keyword research is important. Many tools exist. We'll cover the best approaches.

**Strong:**
> Keyword research is the process of finding the queries people use to search for a topic, grouping them by intent, and deciding which ones a site can realistically rank for. It has three dimensions: intent, volume, and difficulty.

The strong version is a complete, quotable definition. An AI system can extract it without surrounding context.

**2. Convert H2 headings to question format.**

Change declarative headings to the questions users actually ask:
- "Keyword research" → "What is keyword research?"
- "Intent types" → "What are the four types of search intent?"
- "Tools" → "What tools do you need for keyword research?"

Question-shaped headings align with how AI systems match queries to passages [citation:2].

**3. Add FAQ sections.**

Pages that don't have one should get a short FAQ (3–5 questions) covering adjacent questions users ask. Mark these up with `FAQPage` schema (from Phase 2) [citation:2].

**4. Add statistics, citations, and quotations.**

Princeton's GEO research (KDD 2024) tested optimisation methods and found the top three by impact were [citation:3][citation:8]:

| Technique | Impact on AI visibility |
|---|---|
| **Cite sources** | +30–40% |
| **Add quotations** (named experts, with credentials) | +30–40% |
| **Add statistics** (specific numbers, dates, percentages) | up to +40% |
| Keyword stuffing | **-10% (negative)** |

The implication inverts traditional SEO: specific, sourced, quotable facts win; keyword repetition loses. Every claim that can have a number should have one. Every statistic should link to its primary source. Every expert claim should be a direct quote with attribution.

**5. Ensure each section is self-contained.**

A paragraph that only makes sense after reading the previous three is hard to retrieve. Each section should be understandable on its own.

### Output

A restructured set of top pages, each with: direct answer blocks, question-shaped headings, FAQ section, statistics with sources, and self-contained passages.

---

## Phase 4 — New Content Integration

**Goal:** Make AI-optimised content the default for everything published going forward.

**Timeline:** Immediate, ongoing.

Once the top pages are restructured, the standard shifts for new content. Writers should be briefed to include, as standard requirements:

- Direct answer block at the top of each section
- Question-shaped H2s where appropriate
- FAQ section
- Statistics with primary-source links
- Named author with credentials and `Person` schema
- Visible publish and update dates

The goal is to stop treating AI optimisation as a retrofit and start treating it as the baseline [citation:2].

---

## Phase 5 — Tracking Infrastructure

**Goal:** Replace rank-only tracking with multi-platform AI visibility measurement.

**Timeline:** 1–2 weeks to set up, then weekly monitoring.

Traditional rank tracking tells you where you appear in Google. It does not tell you whether ChatGPT cites you, whether Perplexity names your brand, or whether you appear in AI Overviews.

### Set up three tracking layers

**1. Prompt audit library.**

Build a spreadsheet (or use a tool) tracking 30–50 target queries across ChatGPT, Gemini, Perplexity, and Claude [citation:2]. Record weekly:
- Is your domain cited?
- Is your brand mentioned (with or without a link)?
- Which competitors appear?
- What is the exact wording of the AI's summary?

**2. GA4 AI referral segment.**

Create a custom channel group in GA4 for AI search traffic. Referral domains to match [citation:10]:

```
chatgpt\.com|chat\.openai\.com|perplexity\.ai|copilot\.microsoft\.com|claude\.ai|gemini\.google\.com
```

**Important caveat:** Google AI Overviews clicks appear as regular organic Google traffic and **cannot be reliably separated** in GA4 [citation:10]. Treat Google organic as blended; do not try to isolate AI Overview clicks with unreliable methods.

**3. Server log monitoring.**

Check logs for requests from AI retrieval bots (`OAI-SearchBot`, `PerplexityBot`, `Claude-SearchBot`). If they are not visiting, they cannot cite you — even if `robots.txt` allows them.

### The KPIs that matter

| KPI | What it measures | Cadence |
|---|---|---|
| **Citation rate** | % of target prompts where your domain is cited | Weekly |
| **AI share of voice** | Your citations vs. competitors for the same prompt set | Biweekly |
| **AI referral traffic** | Sessions from AI engines, segmented in GA4 | Weekly |
| **AI referral conversion rate** | Do AI visitors convert differently? | Monthly |

For benchmark ranges by industry (B2B SaaS, media, e-commerce, etc.), see [Part B → Measurement](../05-measurement/README.md). Treat benchmarks as directional, not absolute [citation:10].

---

## Phase 6 — Ongoing Freshness

**Goal:** Prevent citation decay.

**Timeline:** Quarterly, ongoing.

AI systems treat recency as a trust signal. The data is stark:
- AI-cited content is **25.7% fresher** on average than content cited in traditional organic results [citation:1].
- **76.4%** of ChatGPT's top 1,000 cited pages had been updated within the previous 30 days [citation:1].
- Pages not updated quarterly are **3× more likely** to lose citations entirely [citation:1].

### The freshness checklist (quarterly)

- [ ] Update statistics with the most recent available data.
- [ ] Replace outdated screenshots and examples.
- [ ] Add new sections for emerging subtopics.
- [ ] Update `dateModified` in schema.
- [ ] Add a visible "Last updated" date.
- [ ] Re-run the prompt audit to check citation rates.
- [ ] Identify pages losing citations and prioritise them.

Do not wait for traffic to drop before refreshing. Set a quarterly review schedule for your highest-value content [citation:1].

---

## What *not* to do (Google's guidance)

Google has published explicit guidance on what does **not** help with AI features. The playbook covers this in [Google's AI Guide (2026)](google-ai-guide-2026.md), but the key points bear repeating here:

- **`llms.txt` is not a Google requirement.** Google has not stated it uses it [citation:11].
- **"Chunking" content is not required.** Google's systems understand multiple topics on a page [citation:11].
- **Rewriting content "for AI" is not required.** The same systems understand synonyms and intent [citation:11].
- **Manufactured mentions are not helpful.** Inauthentic brand mentions do not move rankings [citation:11].
- **Schema is not an AI cheat code.** It supports rich results and machine readability, but it does not guarantee AI citation [citation:11].

The tactics in this playbook are grounded in **how retrieval actually works**, not in speculation. If a "GEO hack" promises fast results without evidence, treat it with suspicion.

---

## The 30-day jump start

If you want to start immediately, here is the minimum viable sequence:

| Week | Focus | Key actions |
|---|---|---|
| **Week 1** | Baseline + audit | Run prompt audit across 4 engines. Check `robots.txt` for AI bot access. Verify server-rendering. |
| **Week 2** | Schema sprint (Tier 1) | Add `Organization`, `Article`, `FAQPage`, `Person` schema to top 20 pages. Validate all. |
| **Week 3** | Content restructuring (top 10 pages) | Add direct answer blocks. Convert H2s to questions. Add FAQ sections. |
| **Week 4** | Tracking + iteration | Set up GA4 AI segment. Re-run prompt audit. Compare to baseline. Identify next 10 pages. |

After 30 days, you will have:
- A baseline to measure against
- AI crawler access confirmed
- Core schema live
- 10 pages restructured
- A tracking system in place

From there, repeat the restructuring sprint for the next batch of pages, and move into the ongoing freshness cycle.

---

## Common mistakes

1. **Skipping the baseline.** If you don't measure before changing, you can't tell what worked.
2. **Blocking retrieval bots.** The most common silent failure. See Phase 1.
3. **Adding schema without restructuring content.** Schema on a page with no direct answers still won't be cited [citation:2].
4. **Rewriting everything at once.** Focus on top 20–30 pages first. New content follows the standard from day one.
5. **Tracking only Google.** Perplexity and ChatGPT cite differently. Track multiple engines [citation:2].
6. **Ignoring freshness.** A one-time optimisation decays. Quarterly updates are required [citation:1].
7. **Keyword stuffing.** Princeton's research found it **reduces** AI visibility by 10% [citation:3].
8. **Chasing "AI SEO hacks."** Google has explicitly said no special optimisation is required. Fundamentals win [citation:11].
9. **Not adding statistics and citations.** The top three GEO techniques are sources, quotations, and statistics. Prose alone is not enough [citation:3].
10. **Expecting overnight results.** Technical foundation: 2–4 weeks. Content restructuring: 4–8 weeks. Measurable citation improvements: 6–12 weeks after implementation [citation:2].

---

## Key takeaways

- **Baseline first.** Measure citations before changing anything.
- **Phase 1 (technical access)** and **Phase 2 (schema sprint)** produce the fastest initial gains.
- **Restructure top 20–30 pages** — direct answer blocks, question H2s, FAQ sections.
- **Add statistics, citations, and quotations.** Princeton research shows these are the highest-impact techniques; keyword stuffing hurts.
- **Track multiple engines.** ChatGPT, Perplexity, Gemini, and Google AI Overviews cite differently.
- **Google AI Overview clicks are not separately trackable.** Treat Google organic as blended.
- **Freshness is not optional.** Pages not updated quarterly lose citations.
- **Google's guidance is clear:** no special files or hacks required. Fundamentals plus citability win.

---

**Next:** [Google's AI Guide (2026)](google-ai-guide-2026.md) — a summary of Google's official guidance on AI features and how it maps to the tactics in this playbook.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*