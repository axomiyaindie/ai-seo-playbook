# 07 — Measurement

> **Part A · Traditional SEO** · [← Back to Traditional SEO](README.md) · Prev: [06 — Links and Authority](06-links-and-authority.md) · Next: [Part B — Modern AI SEO](../modern-ai-seo/README.md)

Everything in Part A — crawling, indexing, ranking, on-page, technical health, content quality, links — is only useful if you can **measure** whether it's working and **iterate** when it isn't. Measurement is the feedback loop that turns SEO from guesswork into a system.

This final chapter covers what to track, how to track it with free tools (chiefly Google Search Console), and how to interpret the numbers without fooling yourself. It closes Part A and points to Part B, where the measurement surface expands to include AI visibility.

---

## The measurement hierarchy

Track in order of proximity to outcomes. Vanity metrics are easy to game; outcome metrics are what matter.

| Level | What it measures | Examples | Use |
|---|---|---|---|
| **1. Visibility** | Can you be seen? | Impressions, indexed pages, rankings | Diagnose reach |
| **2. Traffic** | Are people clicking? | Clicks, sessions, CTR | Diagnose appeal |
| **3. Engagement** | Do they stay and act? | Dwell time, scroll depth, conversions | Diagnose quality |
| **4. Outcomes** | Does it drive the business? | Revenue, signups, leads, retention | Justify investment |

A page can have high impressions and zero clicks (bad title/intent mismatch), or high clicks and zero conversions (wrong audience or weak offer). **Track all four levels** — each diagnoses a different failure.

---

## Google Search Console: the primary tool

Search Console (GSC) is free, authoritative (it's Google's own data), and the single most important SEO tool. If you use nothing else, use this.

### Key reports

| Report | What it shows | What to look for |
|---|---|---|
| **Performance** | Queries, pages, countries, devices; clicks, impressions, CTR, position | Queries where you rank 5–20 (striking distance); high-impression/low-CTR pages |
| **Pages** (Indexing) | Which URLs are indexed, excluded, or errored | Unexpected exclusions; `noindex`; crawl anomalies |
| **Sitemaps** | Submitted sitemaps, discovered URLs, errors | Errors; URLs discovered but not indexed |
| **Core Web Vitals** | LCP, INP, CLS by URL group | "Poor" or "Needs improvement" groups |
| **Mobile Usability** | Mobile-specific issues | Viewport, tap targets, content width |
| **Links** | Top linked pages, top linking sites, anchor text | New/lost links; anchor distribution |
| **Manual Actions** | Penalties | Any action — fix immediately |
| **Security Issues** | Hacks, malware, phishing | Any issue — fix immediately |
| **URL Inspection** | Per-URL crawl/index/render status | Diagnose individual pages |

### Performance report: the daily driver

The Performance report is where you'll spend most of your time. Key analyses:

**1. Striking-distance queries.** Filter for position 5–20 and impressions > 0. These are queries where you're close to page 1 — small improvements (better title, deeper content, internal links) can move you up. Highest-ROI work in SEO.

**2. High-impression, low-CTR pages.** A page with 10,000 impressions and 1% CTR is being seen but not clicked. Usually a title/meta problem, or intent mismatch. Rewrite the title and meta description; check the SERP.

**3. Query-page mismatches.** Find queries where a page ranks that isn't really about that query. Either the page needs content to match, or a different page should target it.

**4. Declining pages.** Compare date ranges (e.g., last 28 days vs. previous 28). Pages losing clicks/impressions need attention — content refresh, technical check, or competitive analysis.

**5. Branded vs. non-branded.** Filter queries containing your brand name vs. not. Non-branded growth is the real SEO signal; branded growth often reflects marketing, not SEO.

---

## Analytics: behaviour and outcomes

Search Console tells you about *search*. Analytics (Google Analytics 4 or an alternative) tells you about *behaviour after the click*.

| Metric | What it tells you | Watch for |
|---|---|---|
| **Sessions / users** | Traffic volume | Segment by source (organic vs. paid vs. direct) |
| **Engagement rate** | Did they interact? | Low = wrong audience or weak page |
| **Average engagement time** | How long did they stay? | Very low = mismatch; very high = possible confusion |
| **Scroll depth** | Did they read past the fold? | Low = above-the-fold problem |
| **Conversion rate** | Did they act? | Segment by landing page |
| **Assisted conversions** | Did SEO contribute to a later conversion? | Often undercounted by last-click |
| **Bounce / exit rate** | Where do they leave? | Not inherently bad — context matters |

### Connecting search to outcomes

The most useful analysis: **landing page → conversion rate**. A page that ranks #1 but converts 0.1% is less valuable than a page at #5 converting 5%. Optimise for *value per visit*, not just traffic.

Set up **conversion events** for whatever matters to your business: signups, purchases, demo requests, downloads, newsletter subscriptions. Without this, you can't tell which SEO work pays off.

---

## Rankings: track them, but don't obsess

Rank tracking tools (Ahrefs, Semrush, SE Ranking, free options like Google Search Console position data) show where you rank for target keywords.

**Caveats:**
- Rankings vary by **location, device, personalisation, and time**. A single rank number is a snapshot, not a truth.
- **Average position** in GSC is an average across queries and users — useful for trends, not absolutes.
- Ranking tools sample from one location/device — they approximate, they don't replicate Google.
- **Rankings are a means, not an end.** A #1 ranking that drives no conversions is worthless; a #8 ranking that drives qualified traffic is valuable.

**Use rankings for:**
- Tracking trends over time for target queries.
- Identifying striking-distance opportunities (position 5–20).
- Competitive benchmarking.
- Validating that content/technical changes had an effect.

**Don't use rankings for:**
- Daily panic. Rankings fluctuate; look at weekly/monthly trends.
- A single "SEO score." No tool replicates Google's ranking.
- Justifying work in isolation from traffic and conversions.

---

## What to measure, by stage

Different stages of a site's life need different metrics.

### New site (0–6 months)
- **Indexed pages** — are pages being discovered and indexed?
- **Impressions** — are you appearing at all?
- **Queries** — what are you being found for (even at low positions)?
- **Crawl errors** — Search Console → Pages.

Traffic and conversions will be low; focus on **getting indexed and appearing**.

### Growing site (6–18 months)
- **Clicks and CTR** — are impressions converting to visits?
- **Striking-distance queries** — where can you move to page 1?
- **Referring domains** — is authority growing?
- **Core Web Vitals** — is the technical floor holding?
- **Conversion rate by landing page** — which pages drive value?

### Mature site (18+ months)
- **Non-branded traffic growth** — real SEO signal.
- **Revenue/leads attributed to organic** — business impact.
- **Content decay** — pages losing traffic need refresh.
- **Competitive share of voice** — are you gaining or losing ground?
- **Retention/return visits** — are you building an audience?

---

## Avoiding measurement traps

SEO measurement is full of ways to fool yourself. The most common:

| Trap | Why it misleads | Fix |
|---|---|---|
| **Attribution confusion** | Last-click credits the final touch, not the discovery | Use multi-touch attribution; understand its limits |
| **Seasonality** | Traffic spikes/dips from calendar, not SEO | Compare year-over-year, not just month-over-month |
| **Algorithm updates** | Rankings shift from updates you didn't cause | Annotate updates; compare before/after carefully |
| **Correlation ≠ causation** | Traffic rose after a change — but something else changed too | Isolate variables; A/B test where possible |
| **Averages hide distribution** | "Average position 8" hides that you're #1 for some queries and #50 for others | Segment; look at distributions |
| **Vanity metrics** | Impressions and rankings feel good but don't pay bills | Pair with clicks, conversions, revenue |
| **Small samples** | 3 clicks last week vs. 5 this week is noise, not signal | Require statistical significance; use trends |
| **Tool discrepancies** | Ahrefs, Semrush, and GSC disagree on traffic/rankings | Trust GSC for your own site; use tools for competitors |
| **Ignoring branded vs. non-branded** | Branded growth masks SEO stagnation | Always segment |

**The core discipline:** when a metric moves, ask *"what else changed?"* before concluding your work caused it.

---

## Reporting: what to show stakeholders

If you report to a team, a client, or yourself, keep it focused on outcomes and trends, not raw metrics.

**A useful monthly report includes:**
1. **Organic traffic trend** (year-over-year, with context).
2. **Conversions/revenue from organic** (the business outcome).
3. **Top gaining/losing pages** (what's working, what needs attention).
4. **Striking-distance opportunities** (next month's work).
5. **Technical health** (indexing, Core Web Vitals, errors).
6. **Notable changes** (algorithm updates, site changes, competitive moves).
7. **Next actions** (what you'll do, with expected impact).

**What to leave out:** raw impression counts without context, single-day ranking screenshots, "SEO score" from third-party tools.

---

## AI search measurement (preview of Part B)

Traditional measurement tells you about classic search. But increasingly, visibility happens in **AI Overviews, ChatGPT, Perplexity, Claude, Gemini** — often without a click. Part B covers this in depth ([Part B → Measurement](../modern-ai-seo/05-measurement/README.md)), but the key ideas:

- **Citation tracking** — are AI answers citing your pages? (Manual checks, prompt trackers.)
- **Referral traffic from AI** — some AI tools send referrers (ChatGPT, Perplexity); track them in analytics.
- **Share of AI answers** — for target prompts, how often does your brand appear?
- **Brand mentions in AI outputs** — even without a link, being named is visibility.

The measurement surface is expanding. The principles in this chapter — track outcomes, segment, avoid traps — apply equally.

---

## The measurement loop

SEO is iterative. The loop:

1. **Set a hypothesis** — "improving the title on page X will raise its CTR."
2. **Make the change.**
3. **Measure** — GSC and analytics, before vs. after, controlling for seasonality.
4. **Interpret** — did it work? Why or why not?
5. **Iterate** — double down on what works; revert what doesn't.

Without this loop, SEO is just activity. With it, it compounds.

---

## Common mistakes

1. **Tracking rankings only.** Rankings without traffic and conversions are vanity.
2. **Ignoring GSC.** It's free, authoritative, and underused.
3. **Not segmenting branded vs. non-branded.** Masks real SEO performance.
4. **Overreacting to short-term fluctuations.** Rankings and traffic are noisy; look at trends.
5. **No conversion tracking.** You can't measure ROI without it.
6. **Trusting one tool's numbers.** GSC for your site; tools for competitors; understand discrepancies.
7. **Confusing correlation with causation.** Algorithm updates and seasonality confound results.
8. **Reporting raw metrics without context.** Impressions alone don't justify work.
9. **Not annotating changes.** You can't interpret a traffic shift if you don't know what you changed.
10. **Forgetting AI search.** Traditional metrics miss an increasingly large share of visibility.

---

## Key takeaways

- Measure at **four levels**: visibility → traffic → engagement → outcomes.
- **Google Search Console** is the primary tool — master the Performance and Pages reports.
- **Striking-distance queries** (position 5–20) are the highest-ROI work in SEO.
- **Analytics** connects search to behaviour and conversions; segment by landing page.
- **Rankings are a means, not an end** — track trends, not daily snapshots.
- Match metrics to **stage** (new, growing, mature).
- Avoid the **traps**: attribution confusion, seasonality, correlation, vanity metrics, small samples.
- Report **outcomes and trends**, not raw metrics.
- **AI search measurement** is the next frontier — Part B covers it.
- SEO compounds through the **measure → interpret → iterate** loop.

---

## Part A complete

You've now covered the full traditional SEO pipeline:

1. [How search works](01-how-search-works.md) — crawl, index, rank
2. [Keywords and intent](02-keywords-and-intent.md) — what to target and why
3. [On-page SEO](03-on-page-seo.md) — how to structure a page
4. [Technical SEO](04-technical-seo.md) — the infrastructure that makes it reachable
5. [Content quality and spam](05-content-and-spam-policies.md) — what's helpful vs. what's spam
6. [Links and authority](06-links-and-authority.md) — how authority is earned
7. **Measurement** — how to know it's working

**Next:** [Part B — Modern AI SEO](../modern-ai-seo/README.md) — how AI Overviews, ChatGPT, Perplexity, and other LLMs retrieve and cite content, and the tactics that earn visibility in AI answers.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../RESEARCH-LOG.md).*