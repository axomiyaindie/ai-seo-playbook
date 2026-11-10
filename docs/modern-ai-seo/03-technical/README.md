# 03 — Technical

> **Part B · Modern AI SEO** · [← Back to Modern AI SEO](../README.md) · Prev: [Google's AI Guide (2026)](../02-geo-aeo/google-ai-guide-2026.md) · Next: [04 — Content](../04-content/README.md)

The technical layer of AI SEO is where most sites lose visibility — not because their content is bad, but because AI retrieval systems can't reach it. This section covers the infrastructure decisions that determine whether your content is **available to AI systems in the first place**: which crawlers you allow, how you declare your content, what structured data you publish, and which emerging discovery files you support.

Part A's [Technical SEO](../../traditional-seo/04-technical-seo.md) chapter is the prerequisite. Everything here assumes crawling, indexing, rendering, and canonicals are already healthy. This section adds the **AI-specific** layer on top.

---

## The pages in this section

| Page | What it covers |
|---|---|
| [AI Crawlers](ai-usage-preferences.md) | The bot landscape: training vs. retrieval vs. user-triggered; how to configure `robots.txt` and `ai.txt` for each |
| [llms.txt](llms-txt.md) | The proposed standard for LLM-facing content maps: format, adoption, when to use it |
| [Sitemaps and robots.txt](sitemap-and-robots.md) | Making discovery work for AI systems; sitemap best practices; `robots.txt` for AI bots |
| [Structured Data](structured-data.md) | Schema.org markup for AI retrieval: which types matter and how to implement them |
| [.well-known, Agents, and MCP](well-known-agents-and-mcp.md) | Emerging discovery files: `agent-card.json`, `mcp-server-card.json`, and the agentic layer |

---

## The four technical pillars of AI SEO

AI retrieval depends on four technical conditions being met. Each corresponds to a page in this section.

### 1. Bots must be allowed

The single most common reason sites disappear from AI answers: **retrieval bots are blocked**. Sites often block all AI bots (GPTBot, ClaudeBot, CCBot) to protect content — not realising that this also removes them from **retrieval**, not just **training**.

The distinction matters enormously:
- **Training bots** (GPTBot, ClaudeBot, Google-Extended, CCBot): fetch content to train or improve models. Blocking these opts out of training.
- **Retrieval bots** (OAI-SearchBot, Claude-SearchBot, PerplexityBot): fetch content at query time to ground AI answers. Blocking these removes you from AI visibility.
- **User-triggered fetchers** (ChatGPT-User, Claude-User, Perplexity-User): activate when a user asks the AI to fetch a specific page.

**Block training, allow retrieval** is the balanced configuration for most sites that want AI visibility. See [AI Crawlers](ai-usage-preferences.md) for the full breakdown and configuration.

### 2. Content must be declared

Two declaration files matter:
- **`robots.txt`** — the classic crawl-control file, which AI bots generally respect. Essential; already covered in Part A.
- **`ai.txt`** — a proposed declarative file for AI-specific preferences (use cases, attribution, pricing intent). Less universally honoured than `robots.txt`, but a low-cost hedge.

**`llms.txt`** is a third, different kind of file: not a crawl-control file but a **content map** — a curated markdown index of your most useful pages for LLMs. Emerging standard; low cost; not yet a Google requirement. See [llms.txt](llms-txt.md).

### 3. Content must be machine-readable

AI systems parse structure and semantics. Explicit markup helps:
- **Schema.org JSON-LD** — `Organization`, `Person`, `Article`, `FAQPage`, `HowTo`, `Product`.
- **Semantic HTML** — headings, lists, tables.
- **Clean URLs and canonicals** — the basics from Part A.

See [Structured Data](structured-data.md).

### 4. Discovery must work for agents

Beyond search and citation, AI **agents** (MCP, A2A) are becoming a discovery and transaction surface. Emerging standards:
- **`.well-known/agent-card.json`** — describes an A2A agent: capabilities, endpoints, skills.
- **`.well-known/mcp-server-card.json`** — describes an MCP server: tools, pricing, transport.

These aren't yet widely used, but publishing them is a low-cost hedge for the agentic layer. See [.well-known, Agents, and MCP](well-known-agents-and-mcp.md).

---

## What this section is *not*

To avoid the most common overstatements:

- **Not a replacement for Part A's Technical SEO.** Crawlability, indexability, rendering, and canonicals come first. If those aren't healthy, nothing in this section helps.
- **Not a set of proven Google requirements.** Google has said no special AI optimisation is required. Some files here (`llms.txt`, `ai.txt`, `.well-known` cards) are **emerging standards**, not Google requirements. They're low-cost hedges, not necessities.
- **Not a guarantee of AI visibility.** Being technically available is necessary but not sufficient — content quality, citability, and authority still determine whether you're cited. See [02 — GEO and AEO](../02-geo-aeo/README.md) and [04 — Content](../04-content/README.md).
- **Not static.** The AI bot landscape changes; new bots appear; standards evolve. Re-audit periodically.

---

## The prioritised action list

If you do nothing else, do these in order:

1. **Audit your `robots.txt`.** Are you blocking AI retrieval bots? If you blocked all AI bots to protect content, decide explicitly: block training bots (fine), allow retrieval bots (essential for AI visibility). → [AI Crawlers](ai-usage-preferences.md)
2. **Verify server-rendering.** Is your content in the initial HTML, or does it depend on JS? Retrieval systems fetch the initial response. → Part A, [Technical SEO](../../traditional-seo/04-technical-seo.md)
3. **Add core schema.** `Organization` with `sameAs`, `Person` for authors, `Article`/`BlogPosting` for content. → [Structured Data](structured-data.md)
4. **Keep sitemaps clean.** Only canonical, indexable, `200` URLs. → [Sitemaps and robots.txt](sitemap-and-robots.md)
5. **Consider `llms.txt`** if you have a substantial site and want a low-cost hedge. → [llms.txt](llms-txt.md)
6. **Consider `.well-known` cards** if you operate an API or agent-accessible service. → [.well-known, Agents, and MCP](well-known-agents-and-mcp.md)

---

## A note on timelines

Some of this section is **established** (how `robots.txt` works; how schema.org markup is parsed) and some is **emerging** (`llms.txt`, `ai.txt`, `.well-known` cards). Treat them differently:

| Established | Emerging |
|---|---|
| `robots.txt` semantics | `llms.txt` adoption |
| Schema.org vocabulary | `ai.txt` adoption |
| Sitemap format | `.well-known` card schemas |
| Bot user-agent names (most) | New AI bots and their behaviour |

**For established standards:** implement fully and confidently.
**For emerging standards:** implement cheaply, monitor adoption, don't build dependencies on them.

The playbook will update as standards stabilise. The [research log](../../RESEARCH-LOG.md) tracks sources and dates.

---

## Common mistakes

1. **Blocking all AI bots.** Removes you from retrieval, not just training. Distinguish the two.
2. **Assuming `llms.txt` is a Google requirement.** It isn't. A hedge, not a necessity.
3. **Publishing `.well-known` cards with placeholder data.** Worse than not publishing them — users copying them get junk.
4. **Ignoring Part A's technical basics.** No AI-specific file fixes a site that can't be crawled or rendered.
5. **Over-investing in emerging standards.** Implement cheaply; don't build dependencies on unproven files.
6. **Not re-auditing.** The bot landscape changes; audit quarterly.
7. **Treating all AI bots as one category.** Training, retrieval, and user-triggered fetchers behave differently and have different consequences.
8. **Forgetting to declare `Organization` schema.** It's the single highest-value structured data for entity recognition.

---

## Key takeaways

- **Four technical pillars:** bots must be allowed, content must be declared, content must be machine-readable, discovery must work for agents.
- **Distinguish training bots from retrieval bots.** Blocking training is a choice; blocking retrieval removes you from AI answers.
- **`llms.txt`, `ai.txt`, and `.well-known` cards are emerging standards** — low-cost hedges, not Google requirements.
- **Schema.org markup** is the highest-leverage technical addition for AI retrieval.
- **Part A's technical basics come first.** No AI-specific file fixes a broken crawl/index/render pipeline.
- **Re-audit periodically** — the landscape changes.

---

**Next:** [04 — Content](../04-content/README.md) — citable content, entities, brand mentions, and passage-level optimisation.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*