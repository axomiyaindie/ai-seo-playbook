# Google's Official AI Guide (2026): Summary and Mapping

> **Part B · Modern AI SEO** · [← Back to GEO and AEO](README.md) · [Part B hub](../README.md)

Google has published official guidance on how its AI features (AI Overviews, AI Mode) interact with Search, and what site owners should do about it. This page summarises that guidance and maps each point to the tactics in this playbook — so you can see which recommendations come directly from Google and which are practitioner inference.

> **Sourcing note:** this page summarises Google's published documentation as of 2026. Google's guidance evolves; check the linked primary sources for the latest version. Every claim here is dated in the [research log](../../RESEARCH-LOG.md).

---

## What Google actually says

Google's published position, in plain terms:

1. **AI Overviews and AI Mode use the same index and ranking systems as Search.** There is no separate "AI index." Pages that rank well in Search are the pages eligible for AI features.

2. **There are no special optimisations required for AI Overviews.** Google has explicitly said that the SEO fundamentals — crawlability, helpful content, good structure — are what matters. There is no "AI SEO hack."

3. **You cannot pay to appear in AI Overviews.** They are not an ad product. Eligibility is determined by the same systems as organic search.

4. **Google-Extended controls AI training, not AI search visibility.** Blocking `Google-Extended` (via `robots.txt`) opts your content out of Gemini training, but **does not** remove you from AI Overviews or AI Mode — those use the regular Googlebot crawl.

5. **Google respects `robots.txt` for AI features the same way it does for Search.** If you block Googlebot, you're out of both. If you block Google-Extended only, you're out of training but still in AI Overviews.

6. **Helpful, people-first content is the standard.** The same quality guidelines (E-E-A-T, spam policies) apply. AI features don't have a separate quality bar.

7. **Structured data helps.** Google recommends schema.org markup for rich results, and this markup also helps AI features understand content.

8. **Freshness matters for time-sensitive queries.** Google's systems consider freshness where relevant, and this extends to AI answers.

---

## Mapping Google's guidance to this playbook

| Google's guidance | Where this playbook covers it |
|---|---|
| "Same index and ranking systems as Search" | [01 — Foundations](../01-foundations/README.md); [Part A → How Search Works](../../traditional-seo/01-how-search-works.md) |
| "No special optimisations required" | [02 — GEO and AEO](README.md) — the tactics here are grounded in retrieval mechanics, not hacks |
| "Cannot pay to appear" | [02 — GEO and AEO](README.md) — organic-only; no paid shortcuts |
| "Google-Extended controls training, not AI search" | [03 — Technical → AI Crawlers](../03-technical/README.md) |
| "Respects robots.txt for AI features" | [03 — Technical → Sitemaps and robots.txt](../03-technical/sitemap-and-robots.md) |
| "Helpful, people-first content" | [Part A → Content Quality and Spam Policies](../../traditional-seo/05-content-and-spam-policies.md); [04 — Content](../04-content/README.md) |
| "Structured data helps" | [03 — Technical → Structured Data](../03-technical/structured-data.md) |
| "Freshness matters" | [02 — GEO and AEO](README.md#6-be-fresh) |

---

## What Google has *not* said

It's as important to know what Google hasn't claimed, because a lot of AI SEO advice overstates the evidence.

| Claim (often made) | Status |
|---|---|
| "AI Overviews use a separate index" | **False.** Google has said they use the same index and ranking systems. |
| "You need to write specifically for AI" | **Not what Google says.** Google recommends helpful, people-first content. |
| "`llms.txt` is required for AI visibility" | **Not claimed by Google.** `llms.txt` is a proposed standard, not a Google requirement. See [03 — Technical → llms.txt](../03-technical/llms-txt.md). |
| "Blocking AI bots improves your rankings" | **False.** Blocking Googlebot removes you from Search and AI features. Blocking training bots is a separate choice. |
| "There's a secret AI SEO trick" | **No evidence.** Google has explicitly said no special optimisation is required. |
| "AI Overviews favour certain content formats" | **Speculative.** Google says the same systems as Search; no format preference has been confirmed. |
| "Keyword density matters for AI" | **False.** Modern systems understand semantics; density is not a factor. |

**The pattern:** Google's guidance consistently points back to **fundamentals** — crawlability, helpful content, structure, E-E-A-T. The speculative tactics (special formats, magic prompts, `llms.txt` as a requirement) are not endorsed by Google and should be treated as low-confidence.

---

## What this means practically

If you follow only Google's official guidance, you should:

1. **Make your site crawlable and indexable** — the same as Part A.
2. **Write helpful, people-first content** — the same as Part A.
3. **Use structured data** — the same as Part A.
4. **Keep content fresh** — the same as Part A.
5. **Don't block Googlebot** — if you want to appear in Search or AI features.
6. **Consider `Google-Extended` separately** — if you want to opt out of Gemini training without leaving AI Overviews.

That's it. Google's guidance is, in effect, **"do good traditional SEO, and you're eligible for AI features."** Everything in Part B beyond this is about **increasing the odds** of being the source that gets cited — quotability, consistency, entity clarity — but it builds on the fundamentals, not around them.

---

## On `Google-Extended` (important distinction)

This is the most commonly misunderstood point. Three different things are often conflated:

| Bot / token | Controls | If you block it |
|---|---|---|
| **Googlebot** | Crawling for Search **and** AI Overviews/AI Mode | You disappear from Search **and** AI features |
| **Google-Extended** | Gemini training and grounding | You opt out of Gemini training; **AI Overviews still work** |
| **Googlebot-Image** | Image crawling | Images don't appear in Search or AI |

**Key point:** blocking `Google-Extended` does **not** remove you from AI Overviews. AI Overviews use the regular Googlebot crawl. If your goal is AI search visibility, **keep Googlebot allowed**. If your goal is to opt out of model training, block `Google-Extended` — and AI Overviews will still include you.

See [03 — Technical → AI Crawlers](../03-technical/README.md) for the full bot breakdown.

---

## On llms.txt (Google's position)

`llms.txt` is a **proposed standard** (not a Google specification) for providing a curated map of a site's content to LLMs. Google has **not** stated that it uses `llms.txt`, and there is no official Google guidance requiring it.

**What this means:**
- Adding `llms.txt` is a **low-cost hedge** — it doesn't hurt, and if adoption grows, you're ready.
- It is **not a requirement** for AI visibility, and its absence won't remove you from AI answers.
- Don't treat it as a substitute for crawlability, structure, and quality.

See [03 — Technical → llms.txt](../03-technical/llms-txt.md) for implementation.

---

## How to verify Google's current guidance

Google's guidance changes. To check the current position:

1. **Google Search Central blog** — official announcements about AI features.
2. **Google Search Central documentation** — the "AI features and your website" documentation (if published).
3. **Google's public statements** — Search Liaison (Danny Sullivan) on X/Twitter and in interviews.
4. **Google's AI features help pages** — for AI Overviews and AI Mode specifics.

**Cross-check anything you read elsewhere against these primary sources.** A lot of AI SEO advice is inference presented as fact; Google's own documentation is the ground truth.

---

## Common mistakes

1. **Believing AI Overviews use a separate index.** They don't — same index, same ranking systems.
2. **Blocking Googlebot to "protect content from AI."** This removes you from Search *and* AI features. Block `Google-Extended` instead if you want to opt out of training.
3. **Thinking `llms.txt` is required.** It's a proposed standard, not a Google requirement.
4. **Chasing "AI SEO hacks."** Google has said no special optimisation is required.
5. **Ignoring fundamentals to focus on AI tactics.** The fundamentals *are* the AI tactics, per Google's guidance.
6. **Treating speculative advice as fact.** Cross-check against primary sources.
7. **Assuming AI Overviews are an ad product.** They're not; you can't pay to appear.
8. **Confusing training bots with retrieval bots.** Different purposes; different consequences of blocking.

---

## Key takeaways

- **AI Overviews and AI Mode use the same index and ranking systems as Search.** No separate AI index.
- **No special optimisation is required** per Google — the SEO fundamentals are what matter.
- **You cannot pay to appear** in AI Overviews.
- **`Google-Extended` controls training, not AI search visibility.** Blocking it doesn't remove you from AI Overviews; blocking Googlebot does.
- **`llms.txt` is not a Google requirement** — a low-cost hedge, not a necessity.
- **Helpful, people-first content** is the standard; the same quality guidelines apply.
- **Structured data and freshness** help, as they do in traditional Search.
- **Cross-check AI SEO advice against Google's primary sources** — a lot of it is speculation.

---

**Next:** [03 — Technical](../03-technical/README.md) — AI crawlers, `llms.txt`, `robots.txt`/sitemaps, structured data for retrieval, and `.well-known` agent cards.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*