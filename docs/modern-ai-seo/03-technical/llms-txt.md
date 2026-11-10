# llms.txt

> **Part B · Modern AI SEO** · [← Back to Technical](README.md) · Prev: [AI Crawlers](ai-usage-preferences.md) · Next: [Sitemaps and robots.txt](sitemap-and-robots.md)

`llms.txt` is a **proposed standard** for giving large language models a curated, markdown-formatted map of a site's most useful content. Think of it as a `sitemap.xml` designed for LLMs rather than crawlers: less about "here are all my URLs" and more about "here are the pages that matter, described in the way an LLM can use."

This page covers the format, the adoption status (honestly), when it's worth publishing, and how to implement it — plus the caveats that most llms.txt advocates skip.

---

## What `llms.txt` is (and isn't)

### It is

- A **plain-text markdown file** at the root of a domain: `https://yourdomain.com/llms.txt`.
- A **curated content map** — human-readable, structured, with short descriptions.
- A **proposal** by Jeremy Howard (Answer.AI) in late 2024, with community adoption since.
- A **low-cost hedge**: if adoption grows, you're ready; if not, you've lost nothing.

### It isn't

- **A Google specification.** Google has not stated that it uses `llms.txt`.
- **A replacement for `robots.txt`.** `robots.txt` controls crawling; `llms.txt` describes content.
- **A replacement for a sitemap.** Sitemaps list URLs for crawlers; `llms.txt` describes content for LLMs.
- **A requirement.** Its absence won't remove you from AI answers.
- **Widely honoured yet.** As of 2026, adoption by major AI providers is inconsistent or undocumented. Treat it as emerging.

> **Honest framing:** publishing `llms.txt` is cheap and harmless. It signals AI-readiness and may help if the standard is adopted. But don't expect it to move the needle today — crawlability, structure, and quality matter far more. See [02 — GEO and AEO](../02-geo-aeo/README.md).

---

## The format

`llms.txt` is markdown, with a specific structure:

```markdown
# Site Name

> One-line summary of what this site is and who it's for.

Optional paragraph of context — what the site covers, what's unique about it,
any conventions the LLM should know.

## Core pages

- [Page title](https://yourdomain.com/page): short description of what this page covers.
- [Another page](https://yourdomain.com/another): short description.

## Documentation

- [Getting started](https://yourdomain.com/docs/getting-started): installation and first steps.
- [API reference](https://yourdomain.com/docs/api): endpoints, auth, examples.

## Optional

- [Changelog](https://yourdomain.com/changelog): release notes.
- [Blog](https://yourdomain.com/blog): articles and updates.

## Optional (not essential for LLM understanding)

- [Legal](https://yourdomain.com/legal): terms and privacy.
```

### Structure rules

- **H1** — the site name.
- **Blockquote** — one-line summary.
- **Paragraph** — optional context.
- **H2 sections** — groupings of related pages (`## Core pages`, `## Documentation`, `## Blog`).
- **List items** — `[Title](URL): description`.
- **`## Optional`** — pages that are useful but not essential. LLMs may skip this section when context is limited.

### What to include

- **Your most important pages** — the ones you'd want an LLM to know about.
- **Descriptions that explain what each page covers** — not marketing copy.
- **Consistent URLs** — canonical, `200`-status, indexable.
- **A manageable number** — 20–100 pages, not thousands. It's a curated map, not a dump.

### What to leave out

- Every URL on your site (that's what sitemaps are for).
- Thin or low-value pages.
- Pages that shouldn't be indexed.
- Marketing language; descriptions should be factual.

---

## A complete example

```markdown
# Acme Analytics

> Privacy-first web analytics for small teams. No cookies, GDPR-compliant, self-hostable.

Acme Analytics helps small teams understand their website traffic without invasive tracking.
The product is available as a hosted service and a self-hosted open-source edition.

## Core pages

- [Product overview](https://acme.example/product): what Acme Analytics does, who it's for, and how it differs from cookie-based analytics.
- [Pricing](https://acme.example/pricing): plans, limits, and what's included at each tier.
- [Documentation](https://acme.example/docs): setup, configuration, and API reference.
- [Comparison](https://acme.example/vs/google-analytics): feature-by-feature comparison with Google Analytics 4.

## Documentation

- [Getting started](https://acme.example/docs/getting-started): install the tracking script and verify it's working.
- [Self-hosting guide](https://acme.example/docs/self-hosting): deploy on your own infrastructure with Docker.
- [API reference](https://acme.example/docs/api): endpoints, authentication, and rate limits.

## Research and updates

- [Blog](https://acme.example/blog): product updates and analytics research.
- [Benchmarks](https://acme.example/benchmarks): performance benchmarks vs. other analytics tools.

## Optional

- [About](https://acme.example/about): team, company, and mission.
- [Contact](https://acme.example/contact): support and sales contact.
- [Changelog](https://acme.example/changelog): release notes.
```

This file tells an LLM: *here's what this site is, here are the pages that matter, and here's what each one covers.* If an LLM chooses to read `llms.txt`, it gets a fast, structured overview without crawling the entire site.

---

## Adoption status (honest assessment)

As of 2026:

| Provider | Uses `llms.txt`? | Notes |
|---|---|---|
| **OpenAI** | No public statement | No documented support |
| **Anthropic** | No public statement | No documented support |
| **Google** | No public statement | No documented support |
| **Perplexity** | No public statement | No documented support |
| **Mistral** | No public statement | No documented support |
| **Community tooling** | Growing | Several crawlers and tools support it |

**What this means:** `llms.txt` is a **proposed standard**, not a widely adopted one. It's used by some community tools and may be picked up by providers, but there's no public evidence that the major AI companies use it to determine what to retrieve or cite.

**The honest position:** publish it if it's cheap for you to do so. Don't expect it to change your AI visibility today. It's a hedge, not a lever.

---

## When it's worth publishing

**Worth publishing if:**
- You have a substantial site (50+ pages) where a curated map would genuinely help.
- You want to signal AI-readiness.
- It's cheap to maintain (you can generate it from your sitemap or CMS).
- You want to be ready if adoption grows.

**Skip it if:**
- Your site is small (a 10-page site doesn't need a map).
- You don't have the capacity to maintain it (stale `llms.txt` is worse than none).
- You're spending time on it that would be better spent on crawlability, structure, or content quality.

**The prioritisation:** `robots.txt` > sitemap > schema.org markup > `llms.txt`. Get the first three right before worrying about the fourth.

---

## Implementing `llms.txt`

### 1. Choose your most important pages

Aim for 20–100 URLs. Prioritise:
- Product/service pages
- Documentation
- Key articles or guides
- Comparison pages
- About/company info

### 2. Write short descriptions

For each page, one sentence explaining what it covers. Factual, not marketing.

**Weak:** "Our amazing product that everyone loves."

**Strong:** "Privacy-first web analytics for small teams, with cookie-free tracking and a self-hosted option."

### 3. Group into sections

Common groupings: Core pages, Documentation, Blog/Research, Optional.

### 4. Serve at `/llms.txt`

```
https://yourdomain.com/llms.txt
```

Content-Type: `text/plain; charset=utf-8` (or `text/markdown`).

### 5. Link from `robots.txt` (optional)

Some implementations reference it:

```
# Sitemap for crawlers
Sitemap: https://yourdomain.com/sitemap.xml

# Content map for LLMs
# llms.txt: https://yourdomain.com/llms.txt
```

(There's no standard directive for this; a comment is harmless.)

### 6. Maintain it

When you add or remove important pages, update `llms.txt`. Stale maps erode trust — and if adoption grows, a stale map will mislead.

---

## Beyond `llms.txt`: `llms-full.txt` and per-page `.md`

Some implementations extend the proposal:

- **`llms-full.txt`** — the full text of your key pages, concatenated. Useful for LLMs that want the content, not just links. Large and rarely used.
- **Per-page `.md` versions** — e.g., `/docs/getting-started.md` alongside `/docs/getting-started/`. Some sites serve markdown versions for LLM consumption.

**Status:** these are extensions of an unadopted standard. Low-cost to add; don't build dependencies on them.

---

## Common mistakes

1. **Treating `llms.txt` as a requirement.** It isn't. It's a proposal.
2. **Publishing it instead of fixing crawlability.** `llms.txt` can't help if bots can't fetch your site.
3. **Including every URL.** It's a curated map, not a sitemap. Keep it focused.
4. **Writing marketing copy in descriptions.** Be factual; LLMs are reading for content, not persuasion.
5. **Not maintaining it.** Stale maps are worse than none.
6. **Expecting immediate AI visibility gains.** Adoption is uncertain; don't measure success by it yet.
7. **Confusing `llms.txt` with `robots.txt`.** Different purposes: content map vs. crawl control.
8. **Over-investing in extensions** (`llms-full.txt`, per-page `.md`) before the basics are right.
9. **Including pages you don't want indexed.** `llms.txt` should reflect what you want LLMs to know.
10. **Forgetting canonical URLs.** Links should point to the canonical version of each page.

---

## Key takeaways

- `llms.txt` is a **proposed standard** (not a Google requirement) for giving LLMs a curated content map.
- **Format:** markdown, with H1 site name, blockquote summary, H2 sections of `[Title](URL): description` lists.
- **Include 20–100 of your most important pages**, with factual descriptions.
- **Adoption is uncertain** as of 2026 — no major AI provider has documented using it.
- **Worth publishing as a low-cost hedge** if you have a substantial site.
- **Prioritise `robots.txt` > sitemap > schema.org > `llms.txt`.**
- **Maintain it** if you publish it — stale maps are worse than none.
- **Don't expect immediate gains.** It's a hedge, not a lever.

---

**Next:** [Sitemaps and robots.txt](sitemap-and-robots.md) — making discovery work for AI systems.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*