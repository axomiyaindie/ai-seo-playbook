# Agentic Commerce and Agents

> **Part B · Modern AI SEO** · [← Back to What's Next](README.md) · [Part B hub](../README.md)

The final page of the playbook covers the frontier: **AI agents that don't just answer questions but take actions** — booking, buying, calling APIs, completing transactions on a user's behalf. This is the least mature area of AI search, and the most speculative. But it's where the trajectory points, and preparing early is cheap.

This page covers what agentic commerce is, the standards behind it (MCP, A2A), what it means for different kinds of businesses, and how to prepare — with the honest caveat that most of this is **early**.

---

## What is an AI agent?

An **AI agent** is a system that can:
- **Perceive** — read web pages, call APIs, query databases.
- **Reason** — decide what to do based on a goal.
- **Act** — take actions: fill forms, place orders, send messages, execute code.
- **Iterate** — adjust based on results.

Traditional AI search: *"What's the best CRM for small teams?"* → answer.
Agentic AI: *"Find me the best CRM for small teams, sign up for a trial, and import my contacts."* → actions.

**The shift:** from **answer engines** to **action engines**. This is what the "agentic layer" means for SEO.

---

## Why it matters for SEO

If agents increasingly act on users' behalf, then:

1. **Your site may need to be machine-actionable**, not just machine-readable.
2. **Discovery shifts** — agents need to know what services exist and how to use them.
3. **Transaction value may accrue to accessible services**, not just clickable pages.

This is speculative. Agents are early. But the direction is clear enough to prepare for cheaply.

---

## The standards behind it

Two standards dominate the emerging agentic layer, plus a third for content.

### MCP (Model Context Protocol)

**What it is:** an open protocol from Anthropic for connecting AI assistants to tools and data. An **MCP server** exposes tools that AI assistants can call.

**Why it matters:** MCP is the most widely adopted agent-tool protocol as of 2026. Tools, platforms, and assistants are adopting it. If your service has an MCP server, agents can use it.

**How to discover an MCP server:** via `.well-known/mcp-server-card.json` — see [03 — Technical → .well-known, Agents, and MCP](../03-technical/well-known-agents-and-mcp.md).

**When to build one:** if you operate an API or tool that agents could use to accomplish tasks (search, fetch data, take an action). Not for content sites.

### A2A (Agent2Agent)

**What it is:** an open protocol for **agent-to-agent communication**. Agents describe their capabilities in an **agent card**; other agents discover and communicate with them.

**Why it matters:** A2A is the emerging standard for agents to cooperate — one agent delegating to another. As agent ecosystems grow, A2A enables composition.

**How to discover an A2A agent:** via `.well-known/agent-card.json` — see [03 — Technical → .well-known, Agents, and MCP](../03-technical/well-known-agents-and-mcp.md).

**When to build one:** if you operate an agent-like service (search, booking, analysis) that other agents might call. Not for content sites.

### Pay-Per-Crawl

**What it is:** an emerging model where AI systems pay content owners for access to their content at crawl time — either directly or via a settlement layer.

**Why it matters:** if AI answers reduce click traffic, content owners need alternative monetisation. Pay-Per-Crawl is one proposed answer.

**Status:** early. Some implementations exist; standards aren't settled. Declarative pricing intent can be included in `ai.txt` (see [03 — Technical → AI Crawlers](../03-technical/ai-usage-preferences.md)).

**When to care:** if you have premium, valuable, or paywalled content. Not a priority for most sites yet.

---

## What agentic commerce looks like (in practice)

Here are concrete examples of what agents can do today or will soon be able to do. The pattern: **goal → action → result**, with agents handling the mechanics.

### Product discovery and purchase
**User:** "Find me a privacy-first analytics tool under $50/month and start a trial."
**Agent:** searches, compares options, selects one, fills the signup form, starts the trial.
**Your role:** your product must be discoverable (structured data, MCP/A2A cards if relevant) and signup must be machine-accessible.

### Booking and reservations
**User:** "Book me a table for four at a good Italian place near my hotel on Friday."
**Agent:** searches, checks availability, books, confirms.
**Your role:** booking APIs accessible to agents; structured data on availability and pricing.

### Research and analysis
**User:** "Compare the top five SEO tools for AI-search readiness."
**Agent:** retrieves information, runs comparisons, returns a structured answer.
**Your role:** citable content (chapters [04](../04-content/README.md)), structured comparisons, original data.

### Workflow execution
**User:** "Generate a technical SEO audit for my site and send it to my team."
**Agent:** runs the audit, formats the report, sends it.
**Your role:** if you offer an audit tool, expose it as an MCP server or API.

### Procurement and transactions
**User:** "Order 100 units from my usual supplier."
**Agent:** negotiates, places order, pays.
**Your role:** B2B commerce platforms need machine-actionable interfaces.

**What's real today:** some agent-driven purchasing (early). **What's coming:** more of the above, at scale. **What's still speculative:** autonomous negotiation, complex multi-party transactions.

---

## What it means for different businesses

Not every business needs an agent strategy. Here's a filter:

| Business type | Agent relevance | What to do |
|---|---|---|
| **E-commerce (products)** | High | Structured data (Product), checkout APIs, agent-friendly purchasing |
| **SaaS / tools** | High if API-accessible | MCP server, API docs, structured data on pricing/features |
| **Services (booking, reservations)** | High | Booking API, A2A card if you operate an agent, availability data |
| **Publishers / content** | Medium | Citable content ([04](../04-content/README.md)), `llms.txt`, Pay-Per-Crawl monitoring |
| **Local businesses** | Medium | LocalBusiness schema, booking APIs (if applicable) |
| **B2B platforms** | High if transactional | APIs, MCP server, structured procurement data |
| **Personal blogs** | Low | Fundamentals, citable content, `llms.txt` (optional) |

**The test:** *does an AI agent need to call your service to accomplish a task?* If yes, agent access matters. If no, focus on content and citation.

---

## How to prepare (without over-investing)

The practical position: **build for the current reality, hedge on the frontier.**

### Now (high priority)
1. **Structured data for products/services.** `Product`, `SoftwareApplication`, `LocalBusiness` — machine-readable info on what you offer.
2. **Clear pricing and feature information.** Agents need to compare; structured facts help.
3. **APIs and documentation** (if you offer a service). Make your service accessible to systems, not just humans.

### Next 1–2 years (medium priority)
4. **MCP server** — if you operate a tool or API agents could use. The most likely-to-matter agent standard.
5. **A2A agent card** — if you operate an agent-like service.
6. **Agent-friendly checkout/booking** — if you sell or take bookings.

### Longer term (low priority, monitor)
7. **Pay-Per-Crawl readiness** — if you have premium content.
8. **Agentic commerce integrations** — as standards mature.
9. **Autonomous negotiation / multi-agent workflows** — speculative; watch.

**The trap:** building for a future that doesn't arrive. Implement cheaply; don't bet the site on agentic commerce being mainstream next year. The fundamentals — crawlability, content, structure — remain the priority.

---

## What's likely vs. hype (again)

Repeating from the hub page, because it's important here:

### Likely
- **Agents become part of search.** Already happening in limited forms.
- **MCP becomes a standard.** Growing adoption.
- **Structured data matters more.** Consistent with everything else in AI search.
- **Product/service APIs become machine-accessible.** Natural extension of the trend.

### Uncertain
- **Timeline.** 2 years? 5 years? 10 years? Unclear.
- **Which agent standard dominates.** MCP vs. A2A vs. something new.
- **How transactions are monetised.** Pay-Per-Crawl, licensing, or something else.
- **Whether "agentic commerce" becomes mainstream** or stays niche.

### Hype
- **"AI will replace shopping entirely."** No — people still buy.
- **"You need an agent strategy now."** Only if it fits your business.
- **"Agents will bypass sites entirely."** No — agents need content and services to act on.
- **"Agentic commerce is tomorrow."** It's early; most businesses have time.

---

## The honest bottom line

Agentic commerce is **real but early**. The standards exist; adoption is growing; the actual use of agents for complex transactions is still limited. For most businesses, the priority remains:

1. **Part A fundamentals** — crawlable, indexable, high-quality.
2. **Part B retrieval** — allowed AI crawlers, structured data, citable content.
3. **Cheap agent hedges** — `llms.txt`, `ai.txt`, structured data.
4. **Agent layer only if relevant** — MCP server, A2A card, if your business is transactional.

**The pattern across this whole playbook:** the fundamentals matter most. AI search builds on them; agentic commerce will too. Don't chase the frontier at the expense of the foundation.

---

## Common mistakes

1. **Building for a future that doesn't arrive.** Agents are early; don't bet the business on agentic commerce.
2. **Ignoring the fundamentals.** Crawlability, content, structure — these come first.
3. **Publishing agent cards for services that don't exist.** Worse than not publishing.
4. **Over-investing in `llms.txt`.** Cheap hedge; not a priority.
5. **Assuming agents replace search.** They'll add to it, not replace it.
6. **Not preparing for machine-readable data.** Structured data is the foundation for everything agentic.
7. **Ignoring Pay-Per-Crawl entirely.** If you have premium content, monitor it.
8. **Chasing every new agent standard.** Most will not survive; focus on likely winners.
9. **Forgetting that agents need content to act on.** Your content is the fuel; don't neglect it.
10. **Not measuring.** As always — you can't improve what you don't measure ([05 — Measurement](../05-measurement/README.md)).

---

## Key takeaways

- **Agentic commerce** = AI agents taking actions, not just answering questions. From *answer engines* to *action engines*.
- **MCP** (tool protocol) and **A2A** (agent-to-agent) are the emerging standards. Both use `.well-known` cards for discovery.
- **Pay-Per-Crawl** is an emerging monetisation model for AI content access.
- **Most relevant if you operate a transactional service** — not for content sites.
- **Prepare cheaply:** structured data, `llms.txt`, `ai.txt`, agent cards only if relevant.
- **The fundamentals matter most** — crawlability, content, structure. Agentic commerce builds on them.
- **Most of this is early.** Don't bet the site on agentic commerce being mainstream next year.
- **The pattern of this playbook:** do the fundamentals, hedge cheaply, monitor, iterate.

---

*This page completes the AI SEO Playbook. For the full playbook, see [Part A — Traditional SEO](../../traditional-seo/README.md) and [Part B — Modern AI SEO](../README.md). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook).*