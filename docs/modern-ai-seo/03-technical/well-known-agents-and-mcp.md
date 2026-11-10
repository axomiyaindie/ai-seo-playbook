# .well-known, Agents, and MCP

> **Part B · Modern AI SEO** · [← Back to Technical](README.md) · Prev: [Structured Data](structured-data.md) · Next: [04 — Content](../04-content/README.md)

Beyond search and citation, a new discovery surface is emerging: **AI agents**. Instead of (or in addition to) a human asking a search engine a question, an AI agent may autonomously look for services it can use — fetch data, book a meeting, place an order, call an API. To do that, it needs a way to discover what you offer and how to interact with it.

The emerging standards for this are `agent-card.json` (for A2A — Agent2Agent) and `mcp-server-card.json` (for MCP — Model Context Protocol), both served from `/.well-known/`. This page explains what they are, when to publish them, and what to include — with the honest caveat that this is the **least mature** area of AI SEO.

---

## What is `.well-known`?

`.well-known` is a **standard URI path** (RFC 8615) for discovering site metadata. Files served from `https://yourdomain.com/.well-known/` are understood to be site-wide metadata, not content.

Common `.well-known` files you may already know:
- `.well-known/security.txt` — security contact
- `.well-known/change-password` — password change URL
- `.well-known/apple-app-site-association` — iOS app linking

The AI-agent additions:

| File | Purpose | Standard |
|---|---|---|
| `.well-known/agent-card.json` | Describe an A2A agent | A2A (Agent2Agent) |
| `.well-known/mcp-server-card.json` | Describe an MCP server | MCP (Model Context Protocol) |

Both are **emerging**. Neither is a Google or OpenAI requirement. Publishing them is a low-cost hedge for the agentic layer — not a substitute for anything in this playbook.

---

## A2A: agent-card.json

**A2A (Agent2Agent)** is an open protocol for AI agents to communicate with each other. An **agent card** describes an agent: what it does, what skills it has, where its endpoints are, and how to talk to it.

### Where it lives

```
https://yourdomain.com/.well-known/agent-card.json
```

### What it contains

Per Google Cloud's Agent Registry documentation, v1.0 is the recommended schema. A minimal card:

```json
{
  "name": "Example SEO Agent",
  "description": "An A2A-compliant agent that analyses web pages for SEO and AI-search readiness.",
  "version": "1.0.0",
  "supportedInterfaces": [
    {
      "url": "https://yourdomain.com/a2a/v1",
      "protocolBinding": "HTTP+JSON",
      "protocolVersion": "1.0.0"
    }
  ],
  "capabilities": {
    "streaming": true,
    "pushNotifications": false,
    "extendedAgentCard": false
  },
  "defaultInputModes": ["text/plain", "application/json"],
  "defaultOutputModes": ["application/json"],
  "skills": [
    {
      "id": "analyse-page-seo",
      "name": "Analyse Page SEO",
      "description": "Fetches a URL and returns a structured report covering title, meta description, headings, internal links, and structured data presence.",
      "tags": ["seo", "audit", "technical"],
      "examples": ["Analyse https://example.com for SEO issues"]
    }
  ]
}
```

### Key fields

| Field | Purpose |
|---|---|
| `name` | Human-readable agent name |
| `description` | What the agent does |
| `version` | Agent version (semver) |
| `supportedInterfaces` | Endpoint URLs and protocol bindings (**required in v1.0**) |
| `capabilities` | What the agent supports (streaming, push, etc.) |
| `defaultInputModes` / `defaultOutputModes` | MIME types |
| `skills` | What the agent can do — indexed by Agent Registries for discoverability |

### When to publish

**Only if you actually operate an A2A agent.** Publishing an `agent-card.json` for an agent that doesn't exist is worse than not publishing — an agent that tries to use it will fail.

A full template lives at [`templates/well-known/agent-card.json`](../../../templates/well-known/agent-card.json).

---

## MCP: mcp-server-card.json

**MCP (Model Context Protocol)** is an open protocol from Anthropic for connecting AI assistants to data sources and tools. An **MCP server** exposes tools that AI assistants can call. An **MCP server card** describes the server: what tools it offers, how to connect, and what it costs.

### Where it lives

```
https://yourdomain.com/.well-known/mcp-server-card.json
```

### What it contains

The schema is less rigidly standardised than A2A's, but the core fields are widely recognised:

```json
{
  "name": "example-seo-mcp",
  "description": "An MCP server exposing SEO analysis tools.",
  "version": "1.0.0",
  "author": "Acme Analytics",
  "repository": "https://github.com/acme/example-seo-mcp",
  "homepage": "https://acme.example/mcp",
  "license": "MIT",
  "tools": [
    {
      "name": "audit_page",
      "description": "Fetch a URL and return a JSON report of on-page SEO signals: title, meta description, H1-H6 structure, canonical, and internal link count."
    },
    {
      "name": "check_ai_readiness",
      "description": "Return a JSON report on AI-search discoverability: robots.txt access for retrieval bots, presence of llms.txt, and structured data validity."
    }
  ],
  "categories": ["seo", "ai-search", "developer-tools"],
  "pricing": "free",
  "auth_required": false,
  "transport": "stdio",
  "documentation_url": "https://acme.example/mcp/docs"
}
```

### Key fields

| Field | Purpose |
|---|---|
| `name` | Server identifier |
| `description` | What the server does |
| `version` | Server version |
| `tools` | Array of `{name, description}` — what the server can do |
| `pricing` | `free` / `freemium` / `paid` / `open-source` |
| `auth_required` | Boolean; if true, document auth in `documentation_url` |
| `transport` | `stdio` / `http` / `both` |

### When to publish

**Only if you actually operate an MCP server.** Same caveat as A2A: don't publish a card for a server that doesn't exist.

A full template lives at [`templates/well-known/mcp-server-card.json`](../../../templates/well-known/mcp-server-card.json).

---

## Adoption status (honest assessment)

This is the least mature area of AI SEO. As of 2026:

| Standard | Adoption | Notes |
|---|---|---|
| **A2A / agent-card.json** | Emerging | Google Cloud published the v1.0 spec; adoption is early |
| **MCP / mcp-server-card.json** | Emerging | Anthropic's MCP is gaining traction; the server card schema is not formally standardised |
| **Agent Registries** | Early | Some registries index agent cards; not universally used |
| **AI agent consumer usage** | Limited | Few AI assistants autonomously use `.well-known` cards today |

**What this means:** publish cards **only if you actually operate an agent or MCP server** that you want discovered. Don't publish placeholders. Don't expect immediate traffic from them. This is a hedge for the next 1–2 years.

**The honest position:** this is speculative compared to the rest of the playbook. The fundamentals — crawlability, structure, quality — matter far more today. Treat agent discovery as a "if relevant, do it cheaply" item, not a priority.

---

## When it's worth publishing

**Publish if:**
- You operate an **A2A agent** or **MCP server** that you want AI assistants to discover.
- You're a developer tool, API service, or platform where agent access is valuable.
- You want to be ready for the agentic layer as it matures.

**Skip if:**
- You don't operate an agent or MCP server.
- Your product isn't something an AI agent would autonomously use.
- You'd be publishing placeholder content.

**The priority test:** does an AI agent need to *know about your service* and *call it autonomously*? If yes, publish cards. If no, skip.

---

## The path from here

The agentic layer is likely to evolve in three stages:

### Stage 1: Discovery (now)
Agents find services by reading `.well-known` cards and Agent Registries. Early adoption.

### Stage 2: Interaction (next 1–2 years)
Agents call APIs, MCP servers, and A2A agents directly — booking, ordering, fetching data. Standards stabilise; more tools appear.

### Stage 3: Transaction (next 2–5 years)
Agents complete transactions — purchasing, negotiating, executing tasks on behalf of users. See [06 — What's next → Agentic commerce](../06-whats-next/agentic-commerce-and-agents.md).

Where you should sit depends on your product. If you sell products or services an agent could transact, the agentic layer will matter. If you publish content for humans, it matters less.

---

## Common mistakes

1. **Publishing cards for services that don't exist.** Worse than not publishing — agents fail trying to use them.
2. **Publishing placeholder content.** Users who copy templates get junk. See the templates section for real examples.
3. **Expecting immediate traffic.** These standards are early; agents aren't yet broadly using them.
4. **Confusing `agent-card.json` with `mcp-server-card.json`.** Different protocols, different purposes.
5. **Not documenting auth.** If `auth_required: true`, the `documentation_url` must explain the auth scheme.
6. **Linking to non-existent endpoints.** Cards reference URLs; broken URLs kill trust.
7. **Over-investing in agent SEO** before Part A fundamentals and Part B retrieval fundamentals are in place.
8. **Assuming Google uses these cards.** Google has not stated that it does. These are for AI agents, not for Google Search.

---

## Key takeaways

- **`.well-known`** is a standard URI path for site metadata (RFC 8615).
- **`agent-card.json`** describes an A2A agent; **`mcp-server-card.json`** describes an MCP server.
- **Both are emerging standards** — the least mature area of AI SEO.
- **Publish only if you actually operate** an agent or MCP server.
- **Don't publish placeholders.** Real templates are in `templates/well-known/`.
- **This is a low-cost hedge, not a priority.** Part A fundamentals and Part B retrieval matter far more today.
- **Monitor developments** as the agentic layer matures.

---

**Next:** [04 — Content](../04-content/README.md) — citable content, entities, brand mentions, and passage-level optimisation.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*