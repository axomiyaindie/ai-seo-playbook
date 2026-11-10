# 03 — On-Page SEO

> **Part A · Traditional SEO** · [← Back to Traditional SEO](README.md) · Prev: [02 — Keywords and Search Intent](02-keywords-and-intent.md) · Next: [04 — Technical SEO](04-technical-seo.md)

On-page SEO is everything you control **within a page** to help search engines understand it and users want to read it. It's the bridge between the keyword research of the last chapter and the technical infrastructure of the next: you've decided *what* to target, now you build a page that deserves to rank for it.

On-page is not a checklist you perform once. It's a set of decisions about structure, clarity, and usefulness — made for a specific page, for a specific intent.

---

## The two audiences of every page

Every page is read by **two** audiences at once:

1. **Humans** — who want the answer quickly, in a form they can scan and trust.
2. **Machines** — crawlers and indexers that parse structure, extract signals, and decide relevance.

Good on-page SEO satisfies both simultaneously. If a tactic helps one and hurts the other, it's probably wrong. (Example: hiding keyword-stuffed text in white-on-white helps neither — it's invisible to users and a spam signal to engines.)

---

## The page's structural elements

These are the parts of a page that search engines read most deliberately. Get them right and the rest follows.

### Title tag

The single most important on-page element.

```html
<title>Keyword Research: A Practical Guide for 2026</title>
```

**Rules:**
- One per page, unique across the site.
- Include the primary keyword naturally, ideally near the front.
- Aim for ~50–60 characters (longer gets truncated in SERPs).
- Write for clicks *and* relevance — it's both a ranking and a CTR signal.
- No keyword stuffing, no "clickbait", no site name first unless the brand is the draw.

### Meta description

Not a direct ranking factor, but it's your **ad copy in the SERP** — it affects click-through rate, which indirectly affects everything.

```html
<meta name="description" content="Learn how to do keyword research for SEO: find queries, group them by intent, and map them to pages that rank. Free, practical guide.">
```

**Rules:**
- ~150–160 characters.
- Summarise the page's value; include the keyword if natural.
- Unique per page.
- It's a suggestion — engines sometimes rewrite it, especially for AI Overviews. Write it as if it will be used verbatim.

### URL

```html
https://yourdomain.com/guides/keyword-research/
```

**Rules:**
- Short, readable, lowercase, hyphens (not underscores).
- Include the keyword, but don't repeat it.
- Avoid dates, IDs, and parameters in canonical URLs.
- Changing URLs later means 301 redirects — get it right once.

### Headings (H1–H6)

Headings form the **outline** of the page — for readers scanning, and for engines parsing structure.

```html
<h1>Keyword Research: A Practical Guide</h1>
  <h2>What a keyword actually is</h2>
    <h3>The three dimensions</h3>
  <h2>How to do keyword research</h2>
```

**Rules:**
- **Exactly one H1**, matching the page's core topic (usually close to the title).
- Use H2 for major sections, H3 for subsections. Don't skip levels.
- Headings should *describe their section* — not just repeat the keyword.
- Don't use headings purely for styling; use CSS for that.

### Body content

The text itself. This is where relevance is earned — not through density, but through **coverage and clarity**.

**Rules:**
- Lead with the answer (inverted pyramid). Don't bury the point below three paragraphs of preamble.
- Cover the topic thoroughly: the subtopics, the follow-up questions, the edge cases.
- Use the primary keyword and natural variants; no density targets.
- Break up long text with headings, lists, tables, and short paragraphs.
- Cite sources for factual claims (this matters for E-E-A-T and for AI citation).
- Write for a specific reader, not "everyone."

### Internal links

Links from your page to other pages on your site. They do three jobs: help users navigate, distribute authority, and tell engines what each page is about.

```html
<a href="/guides/technical-seo/">technical SEO</a>
```

**Rules:**
- Link to related pages with **descriptive anchor text** (not "click here").
- Link *from* older pages *to* new important pages (so new pages get discovered and authority).
- Use a sensible number — as many as genuinely help the reader, no more.
- Fix broken internal links (they waste crawl budget and frustrate users).

### Images and media

```html
<img src="keyword-research-chart.png" alt="Bar chart showing search volume by intent category" width="800" height="450" loading="lazy">
```

**Rules:**
- Descriptive `alt` text (for accessibility and as an image signal).
- Compress images; specify `width`/`height` to prevent layout shift.
- Use modern formats (WebP/AVIF) where supported.
- `loading="lazy"` for below-the-fold images.
- File names can be descriptive (`keyword-research-chart.png`, not `IMG_2043.png`).

### Structured data

JSON-LD markup that tells engines explicitly what the page is (Article, Product, FAQ, HowTo, etc.). Covered in depth in Part B's [structured data](../modern-ai-seo/03-technical/structured-data.md) page, but worth mentioning here as an on-page element.

---

## Writing for intent (the part that actually ranks)

Structure is necessary; **intent match** is what wins. The page must *be* what the searcher wanted.

| Intent | The page should… | Common failure |
|---|---|---|
| **Informational** | Answer the question directly, then go deeper | Burying the answer under marketing copy |
| **Navigational** | Be the destination (or a clear path to it) | Redirecting to an unrelated page |
| **Commercial** | Compare options honestly, with criteria | One-sided sales pitch with no comparison |
| **Transactional** | Make the action easy and obvious | Hiding the buy/signup action below the fold |

**Test:** read the query, then read your page's first screen. Does the page immediately look like what the searcher hoped for? If not, intent is mismatched — no amount of on-page optimisation fixes that.

---

## Content quality signals (E-E-A-T)

On-page SEO increasingly means **demonstrating quality**. The framework Google publishes is **E-E-A-T**: Experience, Expertise, Authoritativeness, Trustworthiness.

| Signal | How to show it on-page |
|---|---|
| **Experience** | First-hand examples, screenshots, "we tested this", case data |
| **Expertise** | Author bylines with credentials, accurate terminology, depth |
| **Authoritativeness** | Citations to primary sources, links to/from reputable sites |
| **Trustworthiness** | Contact info, clear ownership, no misleading claims, HTTPS, transparency |

Practical on-page moves:
- **Author bio** with real credentials (linked to an author page).
- **Published and updated dates** (visible, not just in metadata).
- **Sources** for factual claims (link to the primary source, not a blog that cites it).
- **About / Contact** pages that establish who runs the site.
- **No deceptive patterns** — no fake urgency, no hidden fees, no misleading titles.

---

## On-page checklist

Use this per page. Not every item applies to every page type, but the defaults are sound.

**Structure**
- [ ] One unique `<title>`, ~50–60 chars, keyword front-loaded
- [ ] One unique meta description, ~150–160 chars
- [ ] One `<h1>` matching the page topic
- [ ] Logical H2/H3 hierarchy, no skipped levels
- [ ] Clean, readable URL

**Content**
- [ ] Answers the query intent in the first screen
- [ ] Covers subtopics and follow-up questions
- [ ] Natural keyword use; no stuffing
- [ ] Short paragraphs, lists, tables where helpful
- [ ] Sources cited for factual claims
- [ ] Author byline + credentials (where appropriate)
- [ ] Published/updated dates visible

**Links & media**
- [ ] Descriptive internal links to related pages
- [ ] External links to primary sources
- [ ] No broken links
- [ ] Images: descriptive `alt`, compressed, sized, lazy-loaded
- [ ] Descriptive image file names

**Technical (on-page scope)**
- [ ] Self-referencing canonical
- [ ] `noindex` absent (if the page should rank)
- [ ] Structured data where applicable (JSON-LD)
- [ ] Mobile-friendly layout
- [ ] Fast load (see [04 — Technical SEO](04-technical-seo.md))

---

## Common mistakes

1. **Keyword stuffing.** Repeating the keyword in every sentence. Hurts readability, signals spam, helps nothing.
2. **Multiple H1s, or H1 used for styling.** Confuses structure; use CSS for size.
3. **Burying the answer.** Three paragraphs of preamble before the point. Lead with the answer.
4. **Thin content.** A page that says less than the top result — or says it worse — won't rank.
5. **Intent mismatch.** Optimising a product page for an informational query (or vice versa).
6. **"Click here" anchors.** Wastes the internal-link signal; use descriptive text.
7. **No internal links.** Orphan pages don't get discovered or ranked well.
8. **Ignoring the SERP.** If you don't look at what ranks, you don't know what intent to match.
9. **Duplicate titles/descriptions across pages.** Cannibalises and confuses.
10. **Treating on-page as a one-time task.** It's iterative — update pages as intent and competition shift.

---

## Key takeaways

- On-page SEO serves **two audiences**: humans who scan and machines that parse. Optimise for both.
- **Title, meta description, URL, headings, body, internal links, images, structured data** — these are the elements engines read most deliberately.
- **Intent match** is what actually ranks; structure is necessary but not sufficient.
- **E-E-A-T** is demonstrated on-page through bylines, sources, dates, and transparency.
- Write for the reader; use keywords where natural; **no density targets**.
- **Internal links** with descriptive anchors distribute authority and aid discovery.
- Use the **checklist** per page, and revisit pages as competition and intent evolve.

---

**Next:** [04 — Technical SEO](04-technical-seo.md) — crawling, indexing, speed, mobile, HTTPS, structured data, and the infrastructure that lets on-page work reach its audience.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../RESEARCH-LOG.md).*