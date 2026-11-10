# 04 — Technical SEO

> **Part A · Traditional SEO** · [← Back to Traditional SEO](README.md) · Prev: [03 — On-Page SEO](03-on-page-seo.md) · Next: [05 — Content Quality and Spam Policies](05-content-and-spam-policies.md)

Technical SEO is the infrastructure layer: everything that determines whether search engines can **crawl, render, index, and serve** your pages correctly and fast. On-page work (chapter 03) makes a page *understandable*; technical work makes it *reachable*. A perfectly written page that can't be crawled is invisible.

This chapter covers the technical floor every site needs. The AI-specific technical layer — AI crawlers, `llms.txt`, structured data for retrieval — lives in Part B ([Modern AI SEO → Technical](../modern-ai-seo/03-technical/README.md)). Master this page first; Part B builds on it.

---

## The technical stack, in order of priority

Work top-down. Fixing the higher layers matters more than micro-optimising the lower ones.

| Priority | Layer | Why it matters |
|---|---|---|
| 1 | **Crawlability** | If bots can't fetch it, nothing else counts |
| 2 | **Indexability** | If it's not indexed, it can't rank |
| 3 | **Rendering** | If JS content isn't rendered, engines see a blank page |
| 4 | **Canonicalisation** | Duplicates dilute signals and waste crawl budget |
| 5 | **Site structure** | Navigation determines discovery and authority flow |
| 6 | **Speed & Core Web Vitals** | Ranking signal + user experience |
| 7 | **Mobile & HTTPS** | Table stakes; non-negotiable |
| 8 | **Structured data** | Explicit semantics; increasingly important for AI retrieval |

---

## 1. Crawlability

**Crawlability** = can a bot reach and fetch your pages? Three things control it: `robots.txt`, server responses, and internal links.

### `robots.txt`

Lives at `https://yourdomain.com/robots.txt`. Rules for all crawlers, or per-bot:

```
User-agent: *
Allow: /
Disallow: /admin/
Disallow: /cart/
Disallow: /*?sessionid=

Sitemap: https://yourdomain.com/sitemap.xml
```

**Rules:**
- Never block CSS/JS — Google needs them to render the page.
- Never block a URL you want indexed. (And remember: a URL blocked in `robots.txt` **cannot be crawled to read its `noindex`** — so if you want a page de-indexed, unblock it first, then use `noindex`.)
- Use `Disallow` sparingly; it's a blunt tool.
- Always declare your sitemap.
- Test changes with Search Console's `robots.txt` tester before deploying.

### Server response codes

| Code | Meaning | SEO impact |
|---|---|---|
| `200` | OK | Indexable |
| `301` | Permanent redirect | Passes most signals; use for URL changes |
| `302` | Temporary redirect | Does not consolidate signals; use sparingly |
| `404` | Not found | Page gone; fine if intentional |
| `410` | Gone | Stronger "permanently gone"; engines de-index faster |
| `5xx` | Server error | **Bad** — crawler backs off, retries; repeated errors reduce crawl rate |

**Rules:**
- Fix `5xx` fast.
- Use `301` for permanent moves; update internal links to point at the new URL.
- Don't chain redirects (`A → B → C`); point directly at the final URL.
- Soft 404s (a "not found" page returning `200`) confuse engines — return the right status.

### Internal linking

If a page has no inbound internal links and isn't in the sitemap, it's **orphaned** — often never discovered.

**Rules:**
- Every important page reachable within a few clicks of the homepage.
- Use descriptive anchor text.
- Keep the link graph shallow (3–4 clicks max for key pages).
- Audit for orphan pages periodically.

---

## 2. Indexability

**Indexability** = will the engine store this page in its index?

### What blocks indexing

| Cause | Fix |
|---|---|
| `<meta name="robots" content="noindex">` | Remove it |
| `X-Robots-Tag: noindex` HTTP header | Remove the header |
| Canonical pointing elsewhere | Self-reference the canonical |
| `robots.txt` block | Unblock (then check for `noindex`) |
| Duplicate content | Consolidate or canonicalise |
| Content hidden behind interaction | Render server-side or in initial HTML |

### Check what's indexed

```
site:yourdomain.com
```

Then compare against your sitemap. Pages that *should* be indexed but aren't → investigate. Pages indexed that *shouldn't* be (admin, search results, tag archives) → `noindex` them or block via `robots.txt` (carefully).

### XML sitemaps

```xml
<?xml version="1.0" encoding="UTF-8"?>
<urlset xmlns="http://www.sitemaps.org/schemas/sitemap/0.9">
  <url>
    <loc>https://yourdomain.com/guides/technical-seo/</loc>
    <lastmod>2026-11-10</lastmod>
  </url>
</urlset>
```

**Rules:**
- List only **canonical, indexable, `200`-status** URLs.
- Keep it under 50,000 URLs / 50 MB; split if larger.
- Include `<lastmod>` accurately — don't fake it.
- Submit in Search Console and Bing Webmaster Tools.
- Reference the sitemap in `robots.txt`.

---

## 3. Rendering (JavaScript)

Modern sites often render content with JavaScript. Engines *can* render JS, but it's slower and less reliable than server-rendered HTML. The safe rule: **critical content should be in the initial HTML response**, not injected after JS runs.

**Check what Google sees:**
- Search Console → URL Inspection → **Test live URL** → **View tested page** → **Screenshot** / **HTML**.
- Compare the rendered HTML to what a user sees.

**Rules:**
- Server-side render (SSR) or static-generate (SSG) important content.
- Avoid client-only rendering for anything you want indexed.
- Don't block JS/CSS in `robots.txt`.
- Use `history.pushState` for real URLs (not hash routes) if you build a SPA.
- Test with JavaScript disabled — if the page is blank, that's a problem.

---

## 4. Canonicalisation

**Canonicalisation** = telling engines which URL is the "main" version when multiple URLs serve similar content.

```html
<link rel="canonical" href="https://yourdomain.com/guides/technical-seo/">
```

**Rules:**
- Every indexable page should have a **self-referencing** canonical (even if there are no duplicates — it prevents accidental canonicalisation).
- Canonical must point to a `200`-status, indexable URL.
- Don't canonicalise across domains unless you genuinely want to consolidate.
- Pick **one** preferred version: `www` vs non-`www`, `http` vs `https`, trailing slash vs not. Redirect the others with `301`.

### Common duplicate sources

- `www` vs non-`www`
- `http` vs `https`
- Trailing slash vs no slash
- Uppercase vs lowercase URLs
- Query parameters (`?utm_source=…`, `?sort=…`)
- Pagination, filters, faceted navigation
- Print versions, AMP versions
- Session IDs

Fix each with a `301` or a canonical, then consolidate internal links to the preferred URL.

---

## 5. Site structure & navigation

The link graph is how engines discover pages and distribute authority.

**Rules:**
- **Flat is better than deep.** Key pages within 3–4 clicks of the homepage.
- **Breadcrumbs** help users and engines understand hierarchy. Mark them up with `BreadcrumbList` structured data.
- **Category pages** should be indexable and useful, not thin.
- **Pagination**: use `<link rel="next">` / `<link rel="prev">` for clarity (no longer a Google ranking signal, but good practice), or make paginated pages self-canonical.
- **Avoid infinite scroll** for content you want indexed — provide paginated URLs or a "view all" page.
- **HTML sitemap** (optional) helps users and provides another discovery path.

---

## 6. Speed & Core Web Vitals

**Core Web Vitals** are Google's page-experience signals. They're a tiebreaker, not a primary ranking factor — but they matter for UX and conversions.

| Metric | Measures | Good threshold |
|---|---|---|
| **LCP** (Largest Contentful Paint) | Loading performance | ≤ 2.5 s |
| **INP** (Interaction to Next Paint) | Responsiveness (replaced FID in 2024) | ≤ 200 ms |
| **CLS** (Cumulative Layout Shift) | Visual stability | ≤ 0.1 |

**How to improve:**

- **LCP**: optimise the largest element (usually a hero image or heading) — preload it, compress it, serve from a CDN, avoid render-blocking resources.
- **INP**: reduce main-thread work; break up long tasks; defer non-critical JS.
- **CLS**: set explicit `width`/`height` on images and embeds; avoid injecting content above existing content; use `font-display: swap` for fonts.

**Measurement:** PageSpeed Insights, Search Console → Core Web Vitals report, Chrome DevTools → Lighthouse, and field data via CrUX.

---

## 7. Mobile & HTTPS

- **Mobile-first indexing**: Google indexes the mobile version of your site. If mobile is worse than desktop, your ranking reflects the mobile version.
- **Responsive design** (one URL, adapts via CSS) is the recommended approach. Avoid separate `m.` sites.
- **HTTPS** is a confirmed (lightweight) ranking signal and a trust signal. Redirect all `http` → `https` with `301`. Use HSTS.
- **No intrusive interstitials** on mobile (full-screen popups that block content) — a negative signal.

---

## 8. Structured data

JSON-LD markup that explicitly tells engines what a page is: `Article`, `Product`, `FAQPage`, `HowTo`, `Organization`, `BreadcrumbList`, `LocalBusiness`, and so on.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Technical SEO: The Complete Guide",
  "author": { "@type": "Person", "name": "Jane Doe" },
  "datePublished": "2026-11-10",
  "dateModified": "2026-11-10"
}
</script>
```

**Rules:**
- Use JSON-LD (Google's preferred format).
- Mark up only what's **visible** on the page.
- Validate with the [Rich Results Test](https://search.google.com/test/rich-results) and Schema Markup Validator.
- Don't mark up content deceptively — that's a spam signal.
- AI-search implications are covered in [Part B → Structured Data](../modern-ai-seo/03-technical/structured-data.md).

---

## Technical audit: the checklist

Run this periodically (monthly for active sites, quarterly for stable ones).

**Crawl & index**
- [ ] `robots.txt` valid; doesn't block CSS/JS; sitemap declared
- [ ] XML sitemap: only canonical, indexable, `200` URLs; submitted
- [ ] No unintended `noindex` tags or `X-Robots-Tag` headers
- [ ] No `5xx` errors in Search Console
- [ ] No orphan pages (key pages reachable within 4 clicks)
- [ ] `site:` search results roughly match expectations

**Rendering**
- [ ] Critical content in initial HTML (not JS-only)
- [ ] URL Inspection → rendered HTML shows expected content
- [ ] No JS/CSS blocked in `robots.txt`

**Canonicalisation**
- [ ] Self-referencing canonicals on indexable pages
- [ ] One preferred version (`www`/non-`www`, `http`/`https`, trailing slash)
- [ ] `301`s for duplicates; no redirect chains
- [ ] Query parameters handled (canonical or `noindex`)

**Structure**
- [ ] Breadcrumbs (with `BreadcrumbList` markup)
- [ ] Pagination handled cleanly
- [ ] Category pages useful, not thin
- [ ] Internal links descriptive; no broken links

**Performance**
- [ ] Core Web Vitals in "Good" range (Search Console report)
- [ ] Images compressed, sized, lazy-loaded
- [ ] CDN for static assets
- [ ] Caching headers set
- [ ] Fonts optimised (`font-display: swap`)

**Mobile & security**
- [ ] Responsive design; mobile parity with desktop
- [ ] HTTPS everywhere; `http` → `https` `301`
- [ ] HSTS enabled
- [ ] No intrusive interstitials

**Structured data**
- [ ] Applicable schema on key page types
- [ ] Valid per Rich Results Test
- [ ] Only visible content marked up

---

## Common mistakes

1. **Blocking CSS/JS in `robots.txt`.** Breaks rendering; page looks blank to engines.
2. **`noindex` + `robots.txt` block on the same URL.** The block prevents the engine from seeing the `noindex` — de-indexing never happens.
3. **Canonical pointing to a `404` or `noindex` page.** Wastes the signal; page may drop from the index.
4. **Redirect chains.** `A → B → C` loses signal and slows crawling; point `A → C` directly.
5. **JS-only content.** If it's not in the initial HTML, engines may miss it.
6. **Fake or stale `<lastmod>`.** Erodes trust in the sitemap.
7. **Ignoring mobile parity.** Mobile-first indexing means the mobile version *is* your site.
8. **Micro-optimising speed before fixing crawl/index.** Wrong order — fix the top of the stack first.
9. **Forgetting `www`/`http` consolidation.** Splits signals across duplicates.
10. **Treating technical SEO as one-and-done.** Sites change; audit regularly.

---

## Key takeaways

- Technical SEO determines whether on-page work is **reachable**. Fix crawlability and indexability first.
- **`robots.txt`** controls fetching — never block CSS/JS; never block URLs you want indexed.
- **`noindex`** removes from index; **`robots.txt`** saves crawl budget. Don't confuse the two.
- **Render critical content server-side**; test with URL Inspection.
- **Self-referencing canonicals** + one preferred URL version prevent duplicate dilution.
- **Core Web Vitals** (LCP, INP, CLS) are tiebreakers, not primary ranking factors — but they matter for UX.
- **Mobile-first indexing** means your mobile version is your site.
- **Structured data** (JSON-LD) adds explicit semantics and feeds AI retrieval.
- **Audit regularly** — technical debt accumulates.

---

**Next:** [05 — Content Quality and Spam Policies](05-content-and-spam-policies.md) — what separates helpful content from spam, and how to stay on the right side of search engine guidelines.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../RESEARCH-LOG.md).*