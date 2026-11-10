# 06 — Links and Authority

> **Part A · Traditional SEO** · [← Back to Traditional SEO](README.md) · Prev: [05 — Content Quality and Spam Policies](05-content-and-spam-policies.md) · Next: [07 — Measurement](07-measurement.md)

Links are how the web is stitched together — and how search engines infer authority. A link from page A to page B is, in the simplest terms, a vote: *"this page is worth looking at."* Search engines have refined how they count those votes for twenty-five years, but the core idea hasn't changed. **Pages and sites with more (and better) inbound links tend to rank higher**, all else being equal.

This chapter covers how authority works, how to earn links legitimately, and — crucially — the link-building tactics that violate spam policy and will get you penalised. The line between "earned" and "manipulative" is the most important thing to get right in this chapter.

---

## How links create authority

Search engines model the web as a **graph**: pages are nodes, links are directed edges. From that graph they compute **authority scores** for pages and sites. The exact algorithms are proprietary (PageRank was the first published, and the concept survives in evolved form), but the principles are stable:

| Principle | What it means |
|---|---|
| **Quantity** | More links → more votes (weakly; easily gamed, so engines discount it) |
| **Quality** | Links from authoritative sites count far more than links from obscure ones |
| **Relevance** | Links from topically related sites count more than unrelated ones |
| **Anchor text** | The linked words describe the target page (a signal, but one that's easy to abuse) |
| **Trust** | Links from trusted sites (news, government, academia, established brands) carry extra weight |
| **Placement** | In-content editorial links count more than footer/sidebar links |
| **Reciprocity** | Mutual linking is discounted; one-directional links are the norm |

A single link from a major publication can outweigh hundreds from low-quality directories. **Quality beats quantity, consistently.**

---

## The three categories of links

Every link to your site falls into one of three buckets. Recognising the category tells you how to treat it.

### 1. Earned links (editorial)
Someone linked to you because your content was useful, interesting, or authoritative. **No payment, no request, no exchange.** These are the strongest links and the goal of all legitimate link building.

*Examples:* a journalist cites your original research; a blogger references your guide; a forum user links your tool in a helpful answer.

### 2. Built links (outreach)
You proactively reached out to earn a link — pitching a story, offering a resource, asking for inclusion in a roundup. **Legitimate when the link is earned on merit**, not bought or exchanged.

*Examples:* pitching a data study to journalists; submitting your tool to a relevant directory; guest writing a genuinely useful article for a relevant publication (with editorial oversight).

### 3. Manipulative links (spam)
Links created primarily to manipulate rankings, with no editorial merit. **These violate spam policy** (chapter 05) and risk manual actions.

*Examples:* paid links without `rel="sponsored"`, private blog networks (PBNs), link exchanges ("link to me and I'll link to you"), automated link building, comment/forum spam, link injections.

> **The test:** if the link exists *because someone found the content genuinely useful*, it's earned. If it exists *because someone paid, exchanged, or automated it*, it's manipulative. There's a grey zone (paid placements with proper `rel` attributes, sponsored content) — but the test above resolves most cases.

---

## How to earn links legitimately

Link building is fundamentally **relationship and reputation building**. There's no shortcut that doesn't risk a penalty. The tactics below are durable.

### 1. Create link-worthy assets
The single highest-leverage tactic: **make something people want to link to.**
- **Original research** — surveys, data analyses, benchmarks. Journalists link to data.
- **Tools and calculators** — free utilities that solve a specific problem.
- **Comprehensive guides** — the definitive resource on a topic.
- **Templates and checklists** — practical assets people use and reference.
- **Visual assets** — charts, diagrams, infographics (with proper attribution).

If nothing on your site is worth linking to, no amount of outreach will help.

### 2. Digital PR and outreach
Pitch your assets to people who write about the topic:
- Journalists covering your industry (find them via X/Twitter, industry publications, HARO-style services).
- Bloggers and newsletter authors in your niche.
- Podcasters (links often follow from show notes).

**Rules for outreach:** be specific about why *their* audience would care; don't mass-blast; don't offer payment for editorial links; follow up once, then stop.

### 3. Guest content (with editorial oversight)
Write a genuinely useful article for a relevant publication. **The publication must have editorial control** — you're contributing, not buying placement.

**Avoid:** "guest post" farms that publish anything for a fee; reciprocal guest posting; content that exists only for the link.

### 4. Be a source
Journalists and researchers need expert quotes. Services like Featured, Qwoted, and HARO connect them with sources. Being quoted earns links and brand mentions.

### 5. Build relationships in your community
Answer questions on forums (Reddit, Stack Exchange, industry Slacks). Help people. Links follow naturally when you're consistently useful — and they're among the most durable links you'll get.

### 6. Create linkable reference content
Glossaries, "state of the industry" reports, comparison pages, and definitive explainers attract links passively because people reference them.

### 7. Reclaim unlinked mentions
When someone mentions your brand without linking, politely ask if they'd add a link. This is legitimate — you're not creating the mention, just making it navigable.

### 8. Fix broken links (carefully)
Find broken links on relevant sites and suggest your page as a replacement. **Only when your page genuinely replaces what was there** — otherwise it's just opportunistic.

---

## What *not* to do (spam link tactics)

These violate [spam policies](05-content-and-spam-policies.md#spam-policies-the-specific-behaviours) and risk manual actions. Some still "work" temporarily — that's the trap. The downside (penalty, recovery) outweighs the upside.

| Tactic | Why it's spam | If you've done it |
|---|---|---|
| **Paid links without `rel`** | Buying PageRank | Add `rel="sponsored"` or remove; disavow if you can't |
| **Private Blog Networks (PBNs)** | Networks of sites built purely to link | Disavow; expect penalty risk |
| **Link exchanges / "link to me"** | Reciprocal manipulation | Stop; remove reciprocal schemes |
| **Automated link building** | Tools that create links at scale | Stop; audit and disavow |
| **Comment/forum spam** | Links in comments with no value | Stop; clean up if you control the accounts |
| **Link injections** | Hacked sites adding links | Disavow; secure your site |
| **Exact-match anchor stuffing** | Manipulating anchor text signals | Vary anchors naturally |
| **Directory spam** | Low-quality link directories | Disavow the worst; ignore the rest |
| **Cloaked links** | Links hidden from users | Remove |

**If you've already engaged in these:** stop, audit your backlink profile (Search Console → Links, or a tool like Ahrefs/Semrush), and use the **disavow tool** for links you can't remove. A disavow file tells Google to ignore specific links. Use it sparingly — disavowing good links hurts you.

---

## Anchor text: natural variation, not repetition

Anchor text — the clickable words — tells engines what the target page is about. It's a signal, but one that's easy to over-optimise.

**Natural anchor profile** for a page about "keyword research":
- `keyword research` (exact match) — some
- `keyword research guide` (partial match) — some
- `how to do keyword research` (long-tail) — some
- `this guide` / `here` (generic) — some
- `[brand name]` (branded) — some
- `[URL]` (naked) — some

**Unnatural:** 90% exact-match anchors. That pattern is a footprint of manipulation and is discounted or penalised.

**Rules:**
- Vary anchor text naturally.
- Write links as you'd write them for a reader — descriptive, not keyword-stuffed.
- Don't try to control anchor text on external sites; if you're earning links editorially, the anchor is whatever the linker chose.

---

## Measuring authority

You can't see search engines' internal authority scores, but proxies exist:

| Metric | What it measures | Notes |
|---|---|---|
| **Referring domains** | Number of unique sites linking to you | More meaningful than raw link count |
| **Domain authority (DA/DR)** | Third-party approximation of site strength | Useful for relative comparison; not a Google metric |
| **Page authority (PA/UR)** | Third-party approximation of page strength | Same caveat |
| **Trust flow / citation flow** | Majestic's metrics | Relative only |
| **Search Console → Links** | Your actual backlinks (as Google sees them) | The most authoritative source for *your* site |
| **Brand mentions** | Unlinked mentions across the web | Increasingly important; correlate with authority |

**What to track over time:**
- **Referring domains** growth (quality over quantity).
- **Top linked pages** — which content earns links, so you can make more of it.
- **Anchor text distribution** — watch for over-optimisation.
- **Lost links** — links disappear; investigate why (site removed, page deleted, etc.).
- **Competitor link gaps** — sites linking to competitors but not you are outreach targets.

---

## Internal links: the links you fully control

External links are earned; **internal links are yours to use deliberately.** They matter for:

- **Discovery** — helping crawlers find pages (chapter 04).
- **Authority distribution** — passing authority from strong pages to weaker ones.
- **Context** — anchor text tells engines what the target page is about.
- **User navigation** — helping readers find related content.

**Rules:**
- Link from high-authority pages (homepage, popular guides) to pages you want to rank.
- Use descriptive anchor text (not "click here").
- Keep the link graph shallow — key pages within 3–4 clicks of the homepage.
- Link *contextually* — within the body, where it genuinely helps the reader.
- Audit for broken internal links and orphan pages.

Internal linking is the most underused lever in SEO. You can't control who links to you, but you completely control your own link graph — and improving it is free.

---

## Link building: a realistic cadence

Link building is slow. A realistic view:

- **Months 1–3:** create link-worthy assets; publish them; start building relationships (communities, journalists). Expect few links yet.
- **Months 4–6:** outreach for the assets; guest contributions; begin earning editorial links. Referring domains start to grow.
- **Months 6–12:** compounding — assets attract links passively; relationships yield repeat coverage; authority grows.
- **Year 2+:** links compound. Established assets keep earning; brand recognition drives mentions and links.

**There's no 30-day link-building sprint that works without risk.** If a tactic promises fast links at scale, it's either spam or it'll be discounted. Plan in quarters, not weeks.

---

## Common mistakes

1. **Buying links.** The fastest way to a manual action. Even "high-quality" paid links violate policy without `rel="sponsored"`.
2. **Chasing quantity over quality.** 10 links from reputable sites beat 1,000 from directories.
3. **Over-optimised anchor text.** Exact-match repetition is a manipulation footprint.
4. **Ignoring internal links.** The one link source you fully control — and most sites underuse it.
5. **Building links to thin content.** Links to a weak page waste the link; fix the page first.
6. **No link-worthy assets.** Outreach without something worth linking to is noise.
7. **Mass-blast outreach.** Personalisation matters; generic pitches get ignored (or reported as spam).
8. **Not monitoring backlinks.** You can't disavow what you don't know about; audit regularly.
9. **Disavowing too aggressively.** Disavowing good links hurts you. Use it only for clear spam you can't remove.
10. **Expecting fast results.** Authority compounds over quarters and years, not days.

---

## Key takeaways

- Links are **votes of authority**; quality, relevance, and trust matter far more than quantity.
- **Earned editorial links** are the goal; **built links** are legitimate when earned on merit; **manipulative links** violate policy.
- The test: *does the link exist because someone found the content genuinely useful?*
- **Create link-worthy assets** (research, tools, guides) — outreach without them is noise.
- **Never buy links** without `rel="sponsored"`; never use PBNs, exchanges, or automation.
- **Vary anchor text** naturally; exact-match stuffing is a manipulation footprint.
- **Internal links** are the lever you fully control — use them deliberately.
- **Measure referring domains**, not raw link count; audit regularly; disavow sparingly.
- **Authority compounds over quarters and years.** There are no safe shortcuts.

---

**Next:** [07 — Measurement](07-measurement.md) — how to track rankings, traffic, and the outcomes that matter, and how to use Search Console and analytics to iterate.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../RESEARCH-LOG.md).*