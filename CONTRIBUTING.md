# Contributing

Thanks for helping build the open AI SEO playbook.

This project grows through community contributions — typo fixes, new sources, updated bot lists, case studies, and new pages. This guide explains how to contribute so that the playbook stays **accurate, honest, and useful**.

---

## Ways to contribute

| Contribution | Examples |
|---|---|
| **Fix a typo or broken link** | Spelling, grammar, dead URLs |
| **Add or update a source** | New official documentation, updated bot user-agents, new studies |
| **Improve an existing page** | Clarify a section, add an example, fix an inaccuracy |
| **Add a new page** | A section that's missing, a new standard, a case study |
| **Add a template** | A new `robots.txt` example, schema snippet, agent card |
| **Report an issue** | Factual error, outdated claim, unclear section |

Small PRs are welcome and encouraged. A one-line typo fix is a valid contribution.

---

## Rules for every tactic

Every tactic, recommendation, or claim in the playbook must answer four questions:

1. **What it is** — a one-sentence definition.
2. **Why it works** — the mechanism. Not "it's best practice" — *why*.
3. **How to do it** — concrete steps or example.
4. **How to verify** — how a reader can check it works on their own site.

If a section can't answer all four, it isn't ready.

### Label the evidence

Every non-obvious claim must be labelled with its evidence level:

| Label | Meaning | Example |
|---|---|---|
| **Proven** | Documented by the platform (Google, OpenAI, Anthropic, etc.) or a published specification | "Google says AI Overviews use the same index as Search" |
| **Likely** | Strong, consistent evidence from multiple independent studies or wide practitioner consensus — but not officially confirmed | "AI referral traffic converts differently from organic" |
| **Experimental** | Unverified or early. Worth trying, but not established | "`llms.txt` may improve citation rates" |

**Do not present Experimental claims as Proven.** The playbook's credibility depends on honest labelling.

### Cite primary sources

- **Link the primary source** — official docs, specifications, published studies. Not a blog that cites the source.
- **Include the date** — `(Google, 2026-07)` or `(Ahrefs study, 2026-02)`.
- **If you can't find a primary source**, say so — or mark the claim Experimental.

### No spam, fake reviews, or manipulation

The playbook documents legitimate tactics only. Do not contribute:

- Link schemes, PBNs, or paid-link advice without `rel="sponsored"`
- Fake reviews or ratings
- Cloaking, hidden text, or deceptive structured data
- "AI SEO hacks" that violate platform policies

If a tactic is grey-area, explain the risk and cite the relevant policy. Don't present it as safe.

---

## Content standards

### Structure

Every page should follow this pattern:

```markdown
# Page Title

> **Part X · Section** · [← Back](README.md) · Prev: [Previous](prev.md) · Next: [Next](next.md)

Opening paragraph — what this page covers and why it matters.

---

## Section 1

Content...

## Key takeaways

- One-line summary
- One-line summary

---

**Next:** [Next page](next.md)

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](RESEARCH-LOG.md).*
```

### Writing style

- **Plain English.** Short sentences. No jargon without definition.
- **Answer first.** Lead with the answer, then context (inverted pyramid).
- **Self-contained sections.** Each section should make sense on its own — this also helps AI retrieval (see [Part B → Content](docs/modern-ai-seo/04-content/README.md)).
- **Tables for comparisons.** Lists for enumerated facts. Short paragraphs.
- **No marketing copy.** This is a playbook, not a brochure.

### Length

There is no target word count. A page should be **as long as it needs to be** to cover its topic completely, and no longer. Padding hurts.

---

## Process

### 1. Fork and branch

```bash
git clone https://github.com/<your-username>/ai-seo-playbook.git
cd ai-seo-playbook
git remote add upstream https://github.com/rakibuli10/ai-seo-playbook.git
git checkout -b fix/describe-your-change
```

### 2. Make your change

- **Editing an existing page** — keep the structure; update the content.
- **Adding a page** — follow the structure above; add it to the relevant `README.md` hub.
- **Adding a template** — put it in `templates/`; add it to the "Ready to use" section of the root `README.md`.
- **Updating sources** — link the primary source and add the date.

### 3. Verify links

Before submitting, check that every link in your change resolves:

```powershell
# PowerShell — check a single file's links
$file = "docs/your-page.md"
(Get-Content $file -Raw) -match '\]\(([^)]+)\)' | Out-Null
[regex]::Matches((Get-Content $file -Raw), '\]\(([^)]+)\)') | ForEach-Object { $_.Groups[1].Value } |
  Where-Object { $_ -notmatch '^https?://' -and $_ -notmatch '^#' } |
  ForEach-Object { [pscustomobject]@{ Link = $_.Split('#')[0]; Exists = (Test-Path $_.Split('#')[0]) } } |
  Sort-Object Exists, Link | Format-Table -AutoSize
```

Every row should say `True`.

### 4. Commit

Use a clear commit message:

```
docs: fix broken link in AI crawlers page
docs(traditional-seo): add source for Core Web Vitals thresholds
templates: update robots.txt with new AI bots
```

### 5. Pull request

Open a PR with:

- **What changed** — one or two sentences.
- **Why** — the problem it solves or the gap it fills.
- **Sources** — links to primary sources for any new claims.
- **Evidence labels** — which claims are Proven / Likely / Experimental.

The PR template below asks for these.

---

## Review checklist

Before a PR is merged, it must pass:

**Content**
- [ ] Answers the four questions (what, why, how, verify)
- [ ] Every non-obvious claim is labelled (Proven / Likely / Experimental)
- [ ] Every factual claim has a source with a date
- [ ] No spam, fake reviews, or manipulation tactics
- [ ] Structure matches the playbook format (nav header, key takeaways, footer)

**Links**
- [ ] All internal links resolve
- [ ] All external links point to primary sources
- [ ] No links to your own fork (`axomiyaindie`) — canonical links point to `rakibuli10`

**Writing**
- [ ] Plain English; no undefined jargon
- [ ] Answer-first (inverted pyramid)
- [ ] Sections are self-contained
- [ ] No marketing copy

**Files**
- [ ] New page added to the relevant `README.md` hub
- [ ] New template added to the root `README.md` "Ready to use" section
- [ ] File naming follows the existing convention (`NN-topic.md` for chapters, `README.md` for hubs)

---

## PR template

When you open a PR, use this template:

```markdown
## What changed

<!-- One or two sentences -->

## Why

<!-- The problem this solves or gap this fills -->

## Sources

<!-- Links to primary sources for any new claims -->

- Source 1 (date)
- Source 2 (date)

## Evidence labels

<!-- Which claims are Proven / Likely / Experimental -->

- Proven: ...
- Likely: ...
- Experimental: ...

## Checklist

- [ ] Every non-obvious claim is labelled
- [ ] Every factual claim has a source with a date
- [ ] All internal links resolve
- [ ] New page added to the relevant hub (if applicable)
- [ ] No spam, fake reviews, or manipulation tactics
```

---

## File structure

```
ai-seo-playbook/
├── README.md                          # Root README — navigation
├── CONTRIBUTING.md                    # This file
├── LICENSE                            # CC BY 4.0 (content), MIT (code)
├── docs/
│   ├── RESEARCH-LOG.md                # Claim-by-claim sourcing
│   ├── references.md                  # Official links for every standard
│   ├── how-they-connect.md            # Bridge page
│   ├── traditional-seo/               # Part A
│   │   ├── README.md                  # Hub
│   │   ├── 01-how-search-works.md
│   │   └── ... 07-measurement.md
│   └── modern-ai-seo/                 # Part B
│       ├── README.md                  # Hub
│       ├── 01-foundations/
│       ├── 02-geo-aeo/
│       ├── 03-technical/
│       ├── 04-content/
│       ├── 05-measurement/
│       └── 06-whats-next/
├── templates/
│   ├── ai.txt
│   ├── llms.txt
│   ├── robots.txt
│   ├── product-schema.json
│   ├── prompt-tracker.csv
│   └── well-known/
│       ├── agent-card.json
│       └── mcp-server-card.json
├── checklists/
│   └── ai-seo-launch-checklist.md
├── assets/
│   └── logo.svg
└── .github/
    └── (issue and PR templates)
```

**Naming conventions:**
- Chapter files: `NN-topic-name.md` (e.g. `01-how-search-works.md`)
- Hub files: `README.md`
- Templates: descriptive names (`ai.txt`, `agent-card.json`)
- Use hyphens, not underscores, in file names

---

## Updating sources and bot lists

Two categories of contribution are especially valuable and time-sensitive:

### AI bot user-agents

The AI bot landscape changes. When a new bot appears or an existing one changes:

1. **Check the provider's official documentation** for the user-agent string.
2. **Update** [`docs/modern-ai-seo/03-technical/ai-usage-preferences.md`](docs/modern-ai-seo/03-technical/ai-usage-preferences.md) and the relevant `robots.txt` template.
3. **Add the source** to [`docs/references.md`](docs/references.md) and [`docs/RESEARCH-LOG.md`](docs/RESEARCH-LOG.md).
4. **Label** new bots as Proven (official docs) or Likely (practitioner consensus).

### Standards (MCP, A2A, llms.txt, ai.txt)

When a standard updates:

1. **Check the official specification** (links in [`docs/references.md`](docs/references.md)).
2. **Update the relevant page** with the new version or specification.
3. **Update `docs/references.md`** with the new version URL.
4. **Add an entry** to the research log with the date.

---

## Questions?

- **Open an issue** for questions, suggestions, or bug reports.
- **Check the [research log](docs/RESEARCH-LOG.md)** to see whether a claim is already sourced.
- **Check the [references](docs/references.md)** to find the primary source for a standard.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook).*