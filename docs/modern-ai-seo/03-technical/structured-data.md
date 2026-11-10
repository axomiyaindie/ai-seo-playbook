# Structured Data for AI Retrieval

> **Part B · Modern AI SEO** · [← Back to Technical](README.md) · Prev: [Sitemaps and robots.txt](sitemap-and-robots.md) · Next: [.well-known, Agents, and MCP](well-known-agents-and-mcp.md)

Structured data (schema.org markup) is the most explicit way to tell search engines and AI systems what your content *is*. Traditional SEO uses it for rich results (stars, FAQ dropdowns, breadcrumbs). AI retrieval uses it for something more fundamental: **entity recognition and semantic clarity**. When an AI system knows exactly what your page is about, who wrote it, and what organisation stands behind it, it can cite it with confidence.

This page covers which schema types matter most for AI retrieval, how to implement them correctly, and the mistakes that make structured data worse than none.

---

## Why structured data matters for AI

AI systems parse unstructured text well, but structured data removes ambiguity:

| What structured data provides | Why it matters for AI |
|---|---|
| **Entity disambiguation** — "Apple" the company vs. the fruit | Clear `Organization` / `Product` markup helps AI systems know which entity you are |
| **Authorship** — who wrote this, with credentials | Supports E-E-A-T and citation trust |
| **Dates** — published, modified | Freshness signals; AI systems weight recency |
| **Relationships** — author → organisation → product | Enables the knowledge graph reasoning AI systems rely on |
| **Explicit type** — Article vs. Product vs. FAQ | Removes ambiguity about what the page *is* |

**The core insight:** AI systems reason over **entities and relationships**, not just text. Structured data makes those entities and relationships explicit.

---

## The high-value schemas for AI

Not all schema types matter equally. These six are the highest-leverage for AI retrieval.

### 1. `Organization` (highest priority)

Tells AI systems who you are, with links to your authoritative profiles.

```json
{
  "@context": "https://schema.org",
  "@type": "Organization",
  "name": "Acme Analytics",
  "url": "https://acme.example",
  "logo": "https://acme.example/logo.png",
  "description": "Privacy-first web analytics for small teams.",
  "sameAs": [
    "https://www.linkedin.com/company/acme-analytics",
    "https://github.com/acme-analytics",
    "https://crunchbase.com/organization/acme-analytics",
    "https://en.wikipedia.org/wiki/Acme_Analytics"
  ],
  "contactPoint": {
    "@type": "ContactPoint",
    "email": "hello@acme.example",
    "contactType": "customer support"
  }
}
```

**Why it matters:** `Organization` schema is how AI systems connect your site to your entity. The `sameAs` links are critical — they tell the AI "this site is the same entity as this LinkedIn page and this GitHub org." Without them, entity recognition is fragmented.

**Place on:** the homepage (and optionally an `/about` page).

### 2. `Person` (for authors)

Tells AI systems who wrote the content, with credentials.

```json
{
  "@context": "https://schema.org",
  "@type": "Person",
  "name": "Jane Doe",
  "jobTitle": "Head of SEO",
  "worksFor": {
    "@type": "Organization",
    "name": "Acme Analytics"
  },
  "url": "https://acme.example/team/jane-doe",
  "sameAs": [
    "https://www.linkedin.com/in/janedoe",
    "https://twitter.com/janedoe"
  ]
}
```

**Why it matters:** authorship is a trust signal. AI systems are more likely to cite content with a clear, credentialed author than anonymous content.

**Place on:** author pages, and reference from `Article` markup.

### 3. `Article` / `BlogPosting`

Tells AI systems this is editorial content, with author, dates, and publisher.

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "Technical SEO: The Complete Guide",
  "author": {
    "@type": "Person",
    "name": "Jane Doe",
    "url": "https://acme.example/team/jane-doe"
  },
  "publisher": {
    "@type": "Organization",
    "name": "Acme Analytics",
    "logo": "https://acme.example/logo.png"
  },
  "datePublished": "2026-11-10",
  "dateModified": "2026-11-10",
  "image": "https://acme.example/images/technical-seo.jpg"
}
```

**Why it matters:** explicit type + author + dates are exactly what AI systems use for freshness and trust signals.

**Place on:** every article or blog post page.

### 4. `FAQPage`

Question-answer pairs in explicit structure — the most quotable format for AI.

```json
{
  "@context": "https://schema.org",
  "@type": "FAQPage",
  "mainEntity": [
    {
      "@type": "Question",
      "name": "What is llms.txt?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "llms.txt is a proposed standard file placed at a site's root that provides a curated, markdown-formatted map of the site's most useful content for large language models."
      }
    },
    {
      "@type": "Question",
      "name": "Is llms.txt required for AI visibility?",
      "acceptedAnswer": {
        "@type": "Answer",
        "text": "No. llms.txt is a proposed standard, not a Google or OpenAI requirement. Its absence won't remove you from AI answers."
      }
    }
  ]
}
```

**Why it matters:** FAQ markup is directly extractable. An AI system can quote your answer verbatim, with attribution.

**Place on:** pages with genuine FAQ sections. **Only mark up questions that are actually visible on the page** — hidden FAQ markup is a spam signal.

### 5. `Product` / `SoftwareApplication`

Tells AI systems what you offer, with pricing and features.

```json
{
  "@context": "https://schema.org",
  "@type": "SoftwareApplication",
  "name": "Acme Analytics",
  "applicationCategory": "BusinessApplication",
  "operatingSystem": "Web",
  "offers": {
    "@type": "Offer",
    "price": "0",
    "priceCurrency": "USD",
    "description": "Free tier for up to 10,000 monthly events"
  },
  "aggregateRating": {
    "@type": "AggregateRating",
    "ratingValue": "4.7",
    "reviewCount": "312"
  }
}
```

**Why it matters:** when an AI answer recommends a tool, it needs structured information about what the tool is, who it's for, and what it costs.

**Place on:** product/pricing pages.

### 6. `BreadcrumbList`

Tells AI systems the page's hierarchy.

```json
{
  "@context": "https://schema.org",
  "@type": "BreadcrumbList",
  "itemListElement": [
    { "@type": "ListItem", "position": 1, "name": "Home", "item": "https://acme.example/" },
    { "@type": "ListItem", "position": 2, "name": "Docs", "item": "https://acme.example/docs/" },
    { "@type": "ListItem", "position": 3, "name": "API Reference", "item": "https://acme.example/docs/api/" }
  ]
}
```

**Why it matters:** hierarchy context. Helps AI systems understand where a page sits in your site's structure.

**Place on:** all pages with breadcrumb navigation.

---

## Additional schemas worth knowing

| Schema | When to use | AI relevance |
|---|---|---|
| `HowTo` | Step-by-step instructions | High — directly extractable steps |
| `QAPage` | Q&A forums, community discussions | High — quotable exchanges |
| `Review` / `AggregateRating` | Products, services, content | Medium — trust signals |
| `Event` | Conferences, webinars | Medium — time-sensitive retrieval |
| `LocalBusiness` | Physical locations | Medium — local AI answers |
| `Course` / `LearningResource` | Educational content | Medium — structured learning |
| `Dataset` | Published data | High for research queries |
| `SoftwareSourceCode` | Code repositories | Medium for developer queries |

---

## Implementation rules

### Use JSON-LD

Google's preferred format, and the easiest to maintain.

```html
<script type="application/ld+json">
{
  "@context": "https://schema.org",
  "@type": "Article",
  "headline": "..."
}
</script>
```

Place it in `<head>` or at the end of `<body>`. It doesn't affect rendering.

### One script per entity type

You can have multiple JSON-LD blocks on a page — one for `Organization`, one for `Article`, one for `BreadcrumbList`. That's fine and often cleaner than nesting.

### Reference other entities

Use `@id` to link entities across blocks:

```json
{
  "@context": "https://schema.org",
  "@type": "Article",
  "author": { "@id": "https://acme.example/team/jane-doe#person" }
}
```

### Validate everything

- **[Schema Markup Validator](https://validator.schema.org/)** — general validation.
- **[Google Rich Results Test](https://search.google.com/test/rich-results)** — checks for Google-eligible markup.
- **Search Console → Enhancements** — reports on detected structured data.

### Mark up only what's visible

If a claim or FAQ isn't visible on the page, don't mark it up. Hidden structured data is a spam signal and won't be trusted.

---

## The `sameAs` pattern (important)

`sameAs` is how you tell AI systems "this entity is the same as that entity elsewhere." It's the single most important property for **entity clarity**.

### For `Organization`

```json
"sameAs": [
  "https://www.linkedin.com/company/acme-analytics",
  "https://github.com/acme-analytics",
  "https://crunchbase.com/organization/acme-analytics",
  "https://en.wikipedia.org/wiki/Acme_Analytics",
  "https://twitter.com/acme_analytics"
]
```

### For `Person`

```json
"sameAs": [
  "https://www.linkedin.com/in/janedoe",
  "https://twitter.com/janedoe",
  "https://scholar.google.com/citations?user=..."
]
```

**Rules:**
- Only link to profiles that **genuinely belong to you**.
- Only link to profiles you **control** (or that are authoritative about you).
- Don't link to unrelated profiles — it confuses entity recognition.
- Include Wikipedia if you have a page; it's a strong authority signal.

---

## What structured data does *not* do

- **Doesn't guarantee rich results.** Eligibility ≠ display. Google decides.
- **Doesn't guarantee AI citation.** Structured data helps recognition; it doesn't guarantee retrieval or citation.
- **Doesn't replace content quality.** Marking up thin content doesn't make it helpful.
- **Doesn't fix crawlability.** If the page can't be fetched, schema markup is invisible.
- **Doesn't work if hidden.** Only mark up visible content.

---

## A structured data checklist

For each page:

**Every page**
- [ ] `BreadcrumbList` if breadcrumbs are visible
- [ ] Valid JSON-LD (no syntax errors)

**Homepage**
- [ ] `Organization` with `sameAs` links
- [ ] `WebSite` with `potentialAction: SearchAction` (optional, for sitelinks search box)

**Content pages**
- [ ] `Article` / `BlogPosting` with author, publisher, dates
- [ ] `Person` for the author (if not already referenced)
- [ ] `FAQPage` if FAQ section exists

**Product pages**
- [ ] `Product` / `SoftwareApplication` with `offers`, `aggregateRating` (if genuine)
- [ ] `Review` for individual reviews (if genuine)

**Documentation/guides**
- [ ] `HowTo` for step-by-step content
- [ ] `TechArticle` for technical docs

**Validation**
- [ ] Passes Schema Markup Validator
- [ ] Passes Rich Results Test (for eligible types)
- [ ] No warnings in Search Console Enhancements
- [ ] All marked-up content is visible on the page

---

## Common mistakes

1. **Marking up hidden content.** Spam signal; won't be trusted.
2. **No `Organization` schema.** The highest-value markup for entity recognition — most sites skip it.
3. **No `sameAs` links.** Fragments your entity across the web.
4. **Fake reviews/ratings.** Violates spam policies; detectable.
5. **Broken JSON.** Syntax errors make the whole block invisible.
6. **Marking up every page with every schema.** Noise dilutes signal.
7. **Not validating.** Deploy → invisible failure.
8. **Using microdata instead of JSON-LD.** Valid, but harder to maintain. Prefer JSON-LD.
9. **Duplicating schema.** Multiple conflicting blocks for the same entity confuse parsers.
10. **Expecting rich results from thin markup.** Markup describes; it doesn't promote.

---

## Key takeaways

- Structured data makes **entities and relationships explicit** — crucial for AI retrieval.
- **Six high-value schemas:** `Organization`, `Person`, `Article`/`BlogPosting`, `FAQPage`, `Product`/`SoftwareApplication`, `BreadcrumbList`.
- **`Organization` + `sameAs` is the highest-leverage addition** for entity clarity.
- **Use JSON-LD.** Validate with Schema Markup Validator and Rich Results Test.
- **Mark up only visible content.** Hidden markup is a spam signal.
- **Reference entities with `@id`** to link related schema blocks.
- **Structured data helps recognition; it doesn't guarantee citation.** Quality and crawlability still matter.
- **Audit periodically.** Broken markup silently stops helping.

---

**Next:** [.well-known, Agents, and MCP](well-known-agents-and-mcp.md) — the emerging discovery layer for AI agents.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*