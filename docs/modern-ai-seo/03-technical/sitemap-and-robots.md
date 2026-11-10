# Sitemaps and robots.txt for AI Discovery

> **Part B · Modern AI SEO** · [← Back to Technical](README.md) · Prev: [llms.txt](llms-txt.md) · Next: [Structured Data](structured-data.md)

`robots.txt` and sitemaps are the oldest discovery mechanisms on the web, and they remain the foundation for AI discovery too. This page covers how to configure both so that AI retrieval systems can find, fetch, and prefer your content — without making the common mistakes that quietly remove sites from AI answers.

Part A's [Technical SEO](../../traditional-seo/04-technical-seo.md) covers the fundamentals. This page adds the AI-specific considerations.

---

## Two files, two jobs

| File | Job | Format | Location |
|---|---|---|---|
| **`robots.txt`** | Control **what bots may fetch** | Plain text directives | `https://yourdomain.com/robots.txt` |
| **Sitemap** | Declare **what URLs exist** and **when they changed** | XML (or plain text / RSS) | `https://yourdomain.com/sitemap.xml` |

They complement each other. `robots.txt` says "here's what you can fetch"; the sitemap says "here's what exists." A bot needs both: permission to fetch, and a list of what to fetch.

**AI-specific additions** (covered elsewhere in this section):
- **[AI crawlers](ai-usage-preferences.md)** — which bots you allow, and the training/retrieval distinction.
- **[`llms.txt`](llms-txt.md)** — a content map for LLMs (emerging standard).
- **[`.well-known` cards](well-known-agents-and-mcp.md)** — agent discovery (emerging standard).

---

## `robots.txt`: what matters for AI

### The one rule that matters most

**Do not block retrieval bots.** This is the most common AI SEO failure. See [AI Crawlers](ai-usage-preferences.md) for the full breakdown — but the short version:

- **Training bots** (`GPTBot`, `ClaudeBot`, `Google-Extended`, `CCBot`, etc.) — blockable; no effect on AI search visibility.
- **Retrieval bots** (`OAI-SearchBot`, `Claude-SearchBot`, `PerplexityBot`) — must be allowed for AI search visibility.
- **`Googlebot`** — covers both Search and AI Overviews; blocking removes you from both.
- **`Bingbot`** — covers both Bing Search and Copilot.

### `robots.txt` template for AI visibility

```
# ── Default ──────────────────────────────────────────────
User-agent: *
Allow: /
Disallow: /private/
Disallow: /admin/
Disallow: /account/

# ── Training crawlers (blocked — your choice) ────────────
User-agent: GPTBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: Google-Extended
Disallow: /

User-agent: CCBot
Disallow: /

User-agent: Bytespider
Disallow: /

User-agent: Amazonbot
Disallow: /

User-agent: meta-externalagent
Disallow: /

User-agent: Applebot-Extended
Disallow: /

# ── Retrieval crawlers (allowed — essential for AI visibility)
User-agent: OAI-SearchBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: Claude-SearchBot
Allow: /

User-agent: Claude-User
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: Perplexity-User
Allow: /

User-agent: MistralAI-User
Allow: /

# ── Sitemap ──────────────────────────────────────────────
Sitemap: https://yourdomain.com/sitemap.xml
```

### Rules for `robots.txt` that AI systems care about

1. **Never block CSS/JS for bots you want to render your pages.** AI retrieval systems fetch the page as a browser would; blocked assets break rendering.
2. **Keep it minimal.** The more you block, the more you risk blocking something important.
3. **Test before deploying.** A typo can block everything. Use Google Search Console's `robots.txt` tester and inspect server logs after deployment.
4. **Version-control it.** Keep `robots.txt` in your repo so you can roll back a mistake.
5. **Declare your sitemap.** `Sitemap:` directive at the bottom.

### What `robots.txt` does *not* do

- **Does not remove pages from the index.** If a page is already indexed and you block it in `robots.txt`, it stays indexed (and can't be re-crawled to see a `noindex`). To remove from the index, use `noindex` — and **do not** block it in `robots.txt`.
- **Does not affect training data already collected.** Blocking `GPTBot` prevents future fetches; it doesn't retract data already used.
- **Is not enforced by all bots.** User-triggered fetchers (`ChatGPT-User`, `Claude-User`) may not fully honour `robots.txt`. Reputable bots generally do; treat it as a request, not a guarantee.

---

## Sitemaps: what AI systems use them for

Sitemaps serve three purposes for AI discovery:

1. **Discovery** — new URLs are found faster than by crawling links alone.
2. **Change signals** — `lastmod` tells bots when a page changed, which can prompt re-fetching.
3. **Coverage** — some AI systems use sitemaps to know what exists on a site.

**A sitemap won't guarantee indexing or citation** — but a missing sitemap can delay discovery, and a malformed sitemap can mislead.

### Sitemap format

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://yourdomain.com/guides/technical-seo/</loc>
    <lastmod>2026-11-10</lastmod>
  </url>
  <url>
    <loc>https://yourdomain.com/guides/on-page-seo/</loc>
    <lastmod>2026-11-08</lastmod>
  </url>
</urlset>
```

### Sitemap rules

1. **Only canonical, indexable, `200`-status URLs.** No redirects, no `404`s, no `noindex` pages.
2. **Accurate `lastmod`.** Real dates, not faked freshness. Faking `lastmod` erodes trust.
3. **Under 50,000 URLs / 50 MB per sitemap.** Split into a sitemap index if larger.
4. **Submit to Search Console and Bing Webmaster Tools.** This is how Google and Bing discover it.
5. **Reference it in `robots.txt`.** `Sitemap: https://yourdomain.com/sitemap.xml`.
6. **Keep it current.** Regenerate on publish; remove old URLs.

### What NOT to include

- **`noindex` pages.** Contradictory; don't list pages you don't want indexed.
- **Redirected URLs.** List the destination, not the redirect.
- **Error pages** (`4xx`, `5xx`).
- **Duplicate URLs** (`www` vs. non-`www`; both versions of a canonical pair).
- **Non-canonical URLs.** Only the preferred version.
- **Pages hidden behind auth or paywalls** that you don't want public.

### Sitemap index (for large sites)

```xml
<?xml version="1.0" encoding="UTF-8"?>
<sitemapindex xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <sitemap>
    <loc>https://yourdomain.com/sitemap-pages.xml</loc>
    <lastmod>2026-11-10</lastmod>
  </sitemap>
  <sitemap>
    <loc>https://yourdomain.com/sitemap-posts.xml</loc>
    <lastmod>2026-11-10</lastmod>
  </sitemap>
</sitemapindex>
```

Submit the index; search engines follow the children.

---

## The interaction between `robots.txt` and sitemaps

There's a subtle but important interaction: **`robots.txt` can block a sitemap from being fetched.**

- If you block `sitemap.xml` in `robots.txt`, some crawlers can't read it.
- If you block the entire site (`Disallow: /`), sitemaps may not be fetched either.

**Rule:** keep sitemaps outside any `Disallow` pattern. Most sites leave sitemaps at the root, unblocked, and reference them in `robots.txt`.

```
# Good
User-agent: *
Disallow: /admin/
Disallow: /private/

Sitemap: https://yourdomain.com/sitemap.xml
```

---

## AI-specific discovery extensions

Beyond the two core files, three emerging mechanisms matter for AI discovery. They're covered in detail elsewhere:

| Mechanism | Purpose | Status | Where |
|---|---|---|---|
| **`llms.txt`** | Curated content map for LLMs | Emerging proposal | [llms-txt.md](llms-txt.md) |
| **`ai.txt`** | Declarative AI preferences | Emerging proposal | [ai-usage-preferences.md](ai-usage-preferences.md) |
| **`.well-known` cards** | Agent discovery (A2A, MCP) | Emerging standards | [well-known-agents-and-mcp.md](well-known-agents-and-mcp.md) |

None of these replaces `robots.txt` or sitemaps. They **complement** them. Get the core two right before adding the rest.

---

## Monitoring and auditing

### `robots.txt` audit (quarterly)

- [ ] Does `robots.txt` still match intent? (Have bots been added/removed?)
- [ ] Are any important bots accidentally blocked?
- [ ] Is the sitemap declared and reachable?
- [ ] Are CSS/JS unblocked for bots you want to render?
- [ ] Has Google Search Console flagged any `robots.txt` issues?
- [ ] Have server logs shown unexpected bot behaviour?

### Sitemap audit (monthly)

- [ ] Do all URLs return `200`?
- [ ] Are any `noindex` pages listed? (Remove them.)
- [ ] Are any redirected URLs listed? (Replace with destinations.)
- [ ] Is `lastmod` accurate?
- [ ] Is the sitemap under the 50,000 URL / 50 MB limit?
- [ ] Is the sitemap submitted and processing without errors in Search Console / Bing WMT?
- [ ] Are new pages being discovered promptly? (Check Search Console coverage.)

### What to watch for in Search Console

- **Sitemaps report** — errors, warnings, discovered vs. indexed.
- **Pages report** — pages excluded from indexing (unexpected exclusions may indicate sitemap issues).
- **`robots.txt` report** — any warnings or errors.
- **Crawl stats** — is Googlebot fetching as expected?

---

## Common mistakes

1. **Blocking retrieval bots in `robots.txt`.** Removes you from AI answers. See [AI Crawlers](ai-usage-preferences.md).
2. **Blocking `Googlebot` to "opt out of AI."** Removes you from Google Search entirely. Use `Google-Extended` instead.
3. **`robots.txt` blocking the sitemap.** Some crawlers can't fetch it; discovery breaks.
4. **Listing `noindex` pages in the sitemap.** Contradictory signals; the page won't be indexed regardless.
5. **Listing redirected URLs in the sitemap.** Wastes crawl budget; the destination is what matters.
6. **Fake or stale `lastmod`.** Erodes trust; re-crawl priority drops.
7. **Sitemap over 50,000 URLs.** Use a sitemap index.
8. **Never updating the sitemap.** New pages go undiscovered; old ones linger.
9. **Not submitting to Search Console / Bing WMT.** You're relying on chance discovery.
10. **Blocking CSS/JS.** Breaks rendering for bots that would otherwise fetch your page.

---

## Key takeaways

- **`robots.txt` controls fetching; sitemaps declare URLs.** They work together.
- **Do not block retrieval bots.** Blocking training bots is fine; blocking retrieval removes you from AI answers.
- **`Googlebot` covers both Search and AI Overviews.** Don't block it if you want either.
- **Only list canonical, indexable, `200` URLs in sitemaps.** No `noindex`, no redirects, no errors.
- **Accurate `lastmod` matters.** Faking it erodes trust.
- **Keep sitemaps outside `Disallow` patterns.** And reference them in `robots.txt`.
- **Submit to Search Console and Bing WMT.** Monitor for errors.
- **AI-specific additions (`llms.txt`, `ai.txt`, `.well-known`) complement these files** — they don't replace them.
- **Audit quarterly.** Bots change; a working config can silently break.

---

**Next:** [Structured Data](structured-data.md) — schema.org markup for AI retrieval: which types matter and how to implement them.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*