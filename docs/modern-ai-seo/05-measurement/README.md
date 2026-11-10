# 05 - Measurement

> **Part B · Modern AI SEO** · [Back to Modern AI SEO](../README.md) · Prev: [04 - Content](../04-content/README.md) · Next: [06 - What's next](../06-whats-next/README.md)

Traditional measurement tracks rankings and clicks. AI measurement adds a new surface: **citations, AI impressions, and referral traffic**. Since June 2026, Google provides first-party data on AI feature visibility in Search Console - a significant change from the black-box era. This section covers what to track, how to track it, and how to interpret the data without fooling yourself.

It builds on [Part A - Measurement](../../traditional-seo/07-measurement.md).

---

## The measurement challenge

AI visibility is **harder to measure than traditional search**, for three reasons:

1. **No standard position.** AI answers don't have "rank #3." You're either cited or not.
2. **Personalisation and variability.** Different users get different answers; the same prompt may produce different citations across runs.
3. **No canonical citation list.** Each AI product cites differently (inline links, numbered sources, footnotes) and inconsistently.

**What this means:** you can't measure AI visibility with the precision of traditional rankings. You measure **proxies** - impressions, citations, referral traffic, brand mentions - and combine them into a picture.

Since 2026, one proxy has become much more reliable: **Google's Generative AI performance report in Search Console**.

---

## Google's Generative AI performance report (Search Console)

On June 3, 2026, Google launched dedicated Generative AI performance reports in Search Console, showing **impressions** within AI Overviews, AI Mode, and generative AI features in Discover. The report rolled out globally to all websites by **August 31, 2026**.

This is the first first-party data Google has provided on AI feature visibility. It doesn't solve every measurement problem - but it's a major step forward.

### What the report shows

The report provides **impressions only** - how often links to your site appeared in a generative AI feature on Google Search.

You can segment by:

| Dimension | What it shows |
|---|---|
| **Pages** | Which URLs appeared in AI features (grouped by canonical URL after redirects) |
| **Countries** | Where the AI impressions originated |
| **Devices** | Desktop, tablet, or mobile |
| **Dates** | Hourly, daily, weekly, or monthly granularity |

You can also filter by **search type**: `Web: text-based` (standard search queries) or `Web: multimodal` (image searches via Lens, Circle to Search, etc.).

### What it does *not* show

| Missing | Why it matters |
|---|---|
| **Clicks** | You can't measure CTR or conversion from AI features |
| **Average position** | No ranking context |
| **Query-level data** | You can't see which queries triggered your AI impressions |
| **Historical backfill** | Data starts from May 18, 2026 - no earlier history |

**Google has acknowledged this is inadequate** - the UK's Competition and Markets Authority (CMA) required the reporting, and has mandated that Google add click data and page-level granularity by **March 2027**. Until then, treat impressions as a **visibility signal**, not a traffic metric.

### How to access it

In Search Console: **Performance -> Generative AI** (new tab alongside the standard Search results report).

If you don't see it: your site may not have received enough AI impressions yet, or the report may still be rolling out to your property.

### How impressions are counted

1. **Chart vs. table aggregation.** The chart aggregates by **property** - if two URLs from your site appear in one AI response, that counts as **one** impression. The table aggregates by **page** - each URL may receive its own impression. Chart totals and table totals can differ. Expected, not a bug.

2. **What counts as an impression.** In AI Overviews, a link must be **scrolled or expanded into view** before it counts. In AI Mode, a follow-up question is treated as a new query, and links in the subsequent response generate additional impressions.

### The opt-out toggle (and why you probably shouldn't use it)

Google added a **Search generative AI control** in Search Console Settings. This allows you to exclude your site from AI features entirely.

**Key facts:**
- It has **no ranking penalty** for traditional organic search.
- It **forfeits all AI impressions and traffic** from those features.
- It is **separate from `Google-Extended`** - the toggle controls AI feature display, while `Google-Extended` controls training.

**Recommendation:** for most sites, **do not opt out**. Opting out of AI features is effectively opting out of a growing visibility channel, with no offsetting ranking benefit. Exceptions: publishers with licensing models, paywalled content, or specific legal reasons.

### Using the report to diagnose

The report's real value is not the total impression count. It's the ability to **compare pages across channels**.

**Pattern 1: High organic visibility, low AI visibility.**
A page ranks well and gets organic clicks, but appears rarely in AI features. Review the page: Does it answer questions directly? Are headings descriptive? Can passages stand alone? Is critical content hidden in tabs, images, or JavaScript?

**Pattern 2: Modest organic visibility, high AI visibility.**
A page with modest rankings gets disproportionate AI impressions. These pages are worth studying first - they reveal what Google's systems find easy to extract.

**Pattern 3: Impressions concentrated in a few pages.**
If most AI impressions come from a handful of URLs, group them by topic, template, or content type.

### What to cross-reference

Because the report lacks click data, pair it with the standard Performance report:

- **High AI impressions + high organic clicks** -> your highest-value content.
- **High AI impressions + low organic clicks** -> the AI answer may be satisfying the query without a click.
- **Low AI impressions + high organic clicks** -> the page ranks but isn't being used for AI synthesis.

### Discrepancies to expect

- **Chart vs. table totals differ.** Aggregation is different (property vs. page).
- **Data overlaps with standard Performance.** AI impressions are already included in overall Search totals. Do not add the two figures together.
- **Newest data is preliminary.** Indicated by a dotted line on the chart.

---

## The four measurement layers

| Layer | What it measures | Tools | Reliability |
|---|---|---|---|
| **1. AI impressions (Google)** | Appearances in AI Overviews/AI Mode | Search Console -> Generative AI | **High** for Google AI features |
| **2. AI referral traffic** | Clicks from AI products to your site | Analytics (GA4, Plausible, etc.) | **High** - direct measurement |
| **3. Citations** | Whether your pages are cited in AI answers | Manual checks, prompt trackers | Medium - sample-based |
| **4. Brand mentions in AI outputs** | Whether your brand is named | Prompt trackers, manual checks | Medium - sample-based |

**Start with layers 1 and 2** - they're the most reliable and often the most actionable.

---

## Layer 2: AI referral traffic

### How to track it

In GA4:
- Explore -> Free form
- Dimension: `Session source / medium`
- Filter: source matches regex `chatgpt|openai|perplexity|claude|anthropic|gemini|copilot|bing.*chat|you\.com|phind`

### Common AI referrers

| Source | Referrer domain | Notes |
|---|---|---|
| **ChatGPT** | `chatgpt.com`, `chat.openai.com` | Often includes a query parameter |
| **Perplexity** | `perplexity.ai` | Referrals often include citation context |
| **Claude** | `claude.ai` | Less common; search-enabled |
| **Copilot** | `copilot.microsoft.com` | Bing-backed |
| **You.com** | `you.com` | AI search |
| **Phind** | `phind.com` | Developer-focused |

### The Google AI Overview problem (now partially solved)

Before June 2026, Google AI Overview clicks were **not separately trackable** - they appeared as organic Google traffic. The Generative AI report now provides **impressions**, but **not clicks**.

**What this means:**
- Use **AI impressions** (Search Console) as a visibility signal.
- Use **total Google organic clicks** (Search Console / GA4) as the outcome metric.
- Do not try to isolate AI Overview clicks with unreliable methods.

---

## Layer 3: Citations

### Manual checking

For each AI product, prompt it with queries where you *expect* to be cited. Check:
- **Is your page cited?**
- **Which page?**
- **What context?**
- **Which competitors are also cited?**

**Cadence:** monthly for key queries. Quarterly for broader sets.

### Prompt tracking tools

| Tool | What it does | Notes |
|---|---|---|
| **Profound** | Tracks brand mentions in AI answers | Paid; multiple AI products |
| **AthenaHQ** | AI search visibility tracking | Paid |
| **Otterly.ai** | AI visibility monitoring | Paid |
| **Peec AI** | AI search monitoring | Paid |
| **Manual** | Spreadsheet + monthly checks | Free; labour-intensive |

### What to track

Create a **prompt set** - 20-50 queries:
- **Brand queries** - "What is [Your Brand]?"
- **Category queries** - "Best [category] tools"
- **Comparison queries** - "[Your Brand] vs. [Competitor]"
- **Problem queries** - "How do I [solve problem]?"

---

## Layer 4: Brand mentions in AI outputs

Sometimes an AI answer mentions your brand **without linking**. That's still visibility.

### What to track

- **Mention rate** - in what % of relevant prompts does your brand appear?
- **Sentiment** - positive, neutral, negative.
- **Competitor mentions** - who else appears, and how often?

---

## The AI measurement dashboard

| Metric | Source | Cadence | Target |
|---|---|---|---|
| **AI impressions** (Google) | Search Console -> Generative AI | Weekly | Growing |
| **AI referral sessions** | Analytics (non-Google AI) | Monthly | Growing |
| **AI referral conversion rate** | Analytics | Monthly | Comparable to organic |
| **Citation rate** (for prompt set) | Manual / tool | Monthly | Growing |
| **Brand mention rate** | Manual / tool | Monthly | Growing |
| **Top pages by AI impressions** | Search Console | Monthly | Stable or growing set |

---

## Interpreting the data (caveats)

1. **Impressions are not traffic.** An AI impression means your link was shown, not that anyone clicked.
2. **Sample bias (citations).** A citation rate of 30% on 20 prompts doesn't mean 30% of all AI answers cite you.
3. **Variability.** The same prompt may produce different answers across runs. Track trends.
4. **Google AI Overviews: impressions yes, clicks no.** Click data is mandated by March 2027.
5. **Attribution.** AI referrals often convert differently from organic. Segment them separately.
6. **Correlation is not causation.** A citation increase after a content change could reflect AI system updates.

---

## A practical starting point

### Week 1
- **Check Search Console** for the Generative AI report. Baseline your AI impressions.
- **Set up AI referral segment** in GA4.
- **Create a prompt set** - 20 queries.

### Week 2
- **Baseline citations** - for each prompt, note whether your page is cited.
- **Record competitors.**

### Month 1
- **Review data** - where do you appear? Where don't you?
- **Identify gaps.**
- **Map to tactics.**

### Ongoing
- **Monthly review.**
- **Quarterly re-baseline.**

---

## Common mistakes

1. **Treating AI impressions as traffic.** They're visibility, not visits.
2. **Adding AI impressions to organic impressions.** They're already included in overall Search totals.
3. **Expecting click data from the Generative AI report.** It's impressions only.
4. **Opting out of AI features without a clear reason.** You lose visibility with no ranking benefit.
5. **Trusting a single tool's citation numbers.**
6. **Overreacting to single data points.**
7. **Lumping AI referrals into organic.**
8. **Ignoring high-AI-impression/low-click pages.**
9. **Not cross-referencing AI impressions with organic clicks.**
10. **Confusing impressions with citations.** An impression is a link shown; a citation is a source used in the answer.

---

## Key takeaways

- **Search Console now provides AI impressions** (since August 31, 2026) - the first first-party data on Google AI feature visibility.
- **Impressions only, no clicks.** Click data is mandated by March 2027.
- **Cross-reference AI impressions with organic clicks** to identify high-value content.
- **Do not opt out of AI features** without a specific reason.
- **AI referral traffic** from ChatGPT, Perplexity, etc. is trackable in analytics.
- **Citations and brand mentions** require manual or semi-automated checking.
- **AI measurement is noisy.** Watch trends.
- **Impressions, traffic, and citations are different.** Each measures a different thing.

---

**Next:** [06 - What's next](../06-whats-next/README.md) - agentic commerce, MCP, A2A, and the emerging surface.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*