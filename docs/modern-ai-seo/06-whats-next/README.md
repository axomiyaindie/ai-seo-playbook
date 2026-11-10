# 06 — What's Next

> **Part B · Modern AI SEO** · [← Back to Modern AI SEO](../README.md) · Prev: [05 — Measurement](../05-measurement/README.md) · Next: [Agentic Commerce and Agents](agentic-commerce-and-agents.md)

The AI search landscape is moving fast. Standards that seemed permanent a year ago are being renegotiated; new surfaces (agents, MCP, A2A) are emerging; and the line between "search" and "transaction" is blurring. This section covers where things are heading — with the honest caveat that anything labelled "next" is speculative.

The goal isn't prediction. It's **preparation**: understanding the direction of travel so you can position your site to benefit from it, without over-investing in things that may not materialise.

---

## The three shifts underway

Three broad shifts define the next phase of AI search. Each is covered in more detail in [Agentic Commerce and Agents](agentic-commerce-and-agents.md).

### 1. From answers to actions

Today, AI systems mostly **answer questions**. Increasingly, they'll **take actions**: book a meeting, place an order, fill a form, call an API. This is the shift from *answer engines* to *action engines*.

**What it means for you:** your site may need to be usable by an AI agent, not just readable by a human. That's what `.well-known` cards ([03 — Technical](../03-technical/well-known-agents-and-mcp.md)) and structured APIs are for.

### 2. From links to transactions

Traditional search sends **traffic**. AI answers increasingly **satisfy the query directly** — no click needed. The next step: AI systems completing transactions on the user's behalf.

**What it means for you:** value may accrue less to "the site that gets the click" and more to "the service that gets invoked." If you sell something an agent could transact, positioning for agent access becomes valuable.

### 3. From pages to knowledge graphs

Traditional SEO optimises **pages**. AI systems increasingly reason over **entities and relationships** — the knowledge graph.

**What it means for you:** entity clarity ([04 — Content](../04-content/README.md)) becomes more important over time. Consistent naming, `sameAs` links, and structured data are long-term investments.

---

## The emerging standards

Several standards are competing to define how AI systems interact with the web and with each other. None is dominant yet.

| Standard | Purpose | Status | Covered in |
|---|---|---|---|
| **MCP** (Model Context Protocol) | Connect AI assistants to tools and data | Growing adoption | [.well-known, Agents, and MCP](../03-technical/well-known-agents-and-mcp.md) |
| **A2A** (Agent2Agent) | Agent-to-agent communication | Emerging | [.well-known, Agents, and MCP](../03-technical/well-known-agents-and-mcp.md) |
| **llms.txt** | Content map for LLMs | Proposed | [llms.txt](../03-technical/llms-txt.md) |
| **ai.txt** | AI preferences | Proposed | [AI Crawlers](../03-technical/ai-usage-preferences.md) |
| **Pay-Per-Crawl** | Monetised content access for AI | Early | [Agentic Commerce and Agents](agentic-commerce-and-agents.md) |

**How to read this table:** "Growing adoption" means tools and platforms are actively using it. "Emerging" means early implementations exist but standards aren't settled. "Proposed" means it exists as a specification but broad adoption is uncertain.

---

## What's likely, what's uncertain, what's hype

A useful filter for AI-search claims:

### Likely
- **More AI answers, fewer clicks.** Already happening; will continue.
- **Entity-based retrieval becomes more important.** Consistent with how AI systems work.
- **Structured data matters more, not less.** Machine readability is the direction of travel.
- **Some agentic layer emerges.** MCP is gaining traction; something like it will become standard.

### Uncertain
- **Which agent standard wins.** MCP vs. A2A vs. something new — unclear.
- **How monetisation works.** Pay-Per-Crawl, licensing, or something else — early.
- **Whether `llms.txt` gets adopted.** Currently a proposal; may or may not become standard.
- **Google's exact AI search roadmap.** AI Overviews are evolving; AI Mode is new; direction unclear.

### Hype (treat sceptically)
- **"AI SEO replaces traditional SEO."** No — it builds on it.
- **"You need a magic file / prompt / trick."** No — fundamentals matter most.
- **"Rankings don't matter anymore."** They still determine retrieval.
- **"AI will read your mind."** No — retrieval is still query-driven.
- **"Everyone needs an agent strategy now."** Only if you operate services agents could use.

---

## How to prepare (without over-investing)

The practical position: **do the fundamentals, hedge on the emerging standards, don't build dependencies on unproven ones.**

### 1. Get Part A right
Crawlability, indexability, quality, structure, authority — these are durable. AI search builds on them. If you haven't done [Part A](../../traditional-seo/README.md), that's the priority.

### 2. Get Part B retrieval right
AI crawlers allowed, `llms.txt` published (cheaply), structured data in place, content citable. These are the current levers. See [03 — Technical](../03-technical/README.md) and [04 — Content](../04-content/README.md).

### 3. Hedge on the emerging layer
- **`llms.txt`** — cheap to add; useful if adopted.
- **`ai.txt`** — cheap to add; declarative preferences.
- **`.well-known` cards** — only if you operate an agent or MCP server.
- **Structured APIs** — if agent access to your service is plausible.

### 4. Monitor, don't panic
- **Follow the standards bodies** (Anthropic, Google, OpenAI) for announcements.
- **Watch your AI referral traffic** ([05 — Measurement](../05-measurement/README.md)).
- **Re-audit quarterly** — the landscape changes fast.
- **Don't chase every new proposal** — most won't survive.

### 5. Keep the fundamentals clean
The sites that win in AI search aren't the ones that chase every trend. They're the ones that:
- Are crawlable and indexable.
- Have high-quality, citable content.
- Have clear entities and consistent branding.
- Measure what's happening and iterate.

That's not new. It's just applied to a new surface.

---

## What this section covers

Two pages:

| Page | What it covers |
|---|---|
| **This page** | The three shifts, emerging standards, how to prepare |
| [Agentic Commerce and Agents](agentic-commerce-and-agents.md) | The agentic layer in depth: MCP, A2A, agentic commerce, what it means for e-commerce and services |

---

## Common mistakes

1. **Over-investing in hype.** Most proposed standards don't survive. Hedge cheaply.
2. **Ignoring the fundamentals.** AI search builds on Part A; skipping it leaves nothing to retrieve.
3. **Building dependencies on unproven standards.** Implement cheaply; don't bet the site on them.
4. **Assuming the future is knowable.** It isn't. Prepare for multiple scenarios.
5. **Ignoring the agentic layer entirely.** If you operate a service, it may matter sooner than you think.
6. **Chasing every new proposal.** Most won't survive; focus on the fundamentals plus cheap hedges.
7. **Not measuring.** Without data ([05 — Measurement](../05-measurement/README.md)), you're guessing.
8. **Assuming AI replaces search.** It's additive; traditional search still drives most traffic for most sites.

---

## Key takeaways

- **Three shifts:** answers → actions, links → transactions, pages → knowledge graphs.
- **Emerging standards** (MCP, A2A, `llms.txt`, `ai.txt`, Pay-Per-Crawl) are competing; none is dominant.
- **Likely:** more AI answers, entity-based retrieval, structured data importance, some agentic layer.
- **Uncertain:** which standard wins, how monetisation works, whether `llms.txt` gets adopted.
- **Hype:** "AI replaces SEO," "magic tricks," "rankings don't matter."
- **How to prepare:** fundamentals + cheap hedges + monitoring + iteration.
- **The winners** aren't chasing trends; they're doing the fundamentals well and applying them to new surfaces.

---

**Next:** [Agentic Commerce and Agents](agentic-commerce-and-agents.md) — the agentic layer in depth: MCP, A2A, agentic commerce, and what it means for e-commerce and services.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*