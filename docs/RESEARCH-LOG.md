# Research Log

> Every claim in the playbook is sourced here with a date. Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook).

This log tracks the primary sources behind the playbook's claims, especially those that are time-sensitive or contested. Where a claim is practitioner inference rather than a published statement, it is labelled as such.

**Last updated:** 2026-11-10

---

## How to read this log

| Label | Meaning |
|---|---|
| **Primary** | The organisation's own documentation, blog, or public statement |
| **Secondary** | Reporting on a primary source (interview, conference summary) |
| **Practitioner** | Community consensus or inference; not officially confirmed |
| **Proposed** | A specification or proposal that is not yet a standard |

---

## Google AI Overviews and AI Mode

| Claim | Source | Date | Label |
|---|---|---|---|
| AI Overviews and AI Mode use the same index and core ranking systems as traditional Search | Google Search Central Live Deep Dive session (Cherry Prommawin, Gary Illyes) [citation:14] | 2025-07 | Primary (conference) |
| AI features (AI Mode, AI Overviews, Circle to Search, Lens) behave like featured snippets or knowledge panels — same ranking signals, same infrastructure | Same session [citation:14] | 2025-07 | Primary (conference) |
| Google's guidance: "Good SEO is good GEO" — foundational SEO is the strategy for AI features | Think with Google, reported by PPC Land [citation:2] | 2026-06 | Secondary |
| No special schema.org markup is required for AI Overviews or AI Mode | Google guidance, summarised by PPC Guru [citation:6] | 2026-08 | Secondary |
| No new machine-readable files or AI-specific text files are required for Google's AI features | Google AI features documentation, summarised by Safeguard [citation:5] | 2026-10 | Secondary |
| Googlebot covers both Search and AI Overviews; Gemini is a separate system with its own bots | Search Central Live session [citation:14] | 2025-07 | Primary (conference) |
| Only ~38% of AI Overview-cited URLs also rank in the traditional top 10 (down from ~76% in mid-2025) | Ahrefs study (863,000 keywords, ~4M citations), reported by PPC Guru [citation:6] | 2026-08 | Secondary (study) |

---

## AI crawlers and robots.txt

| Claim | Source | Date | Label |
|---|---|---|---|
| `GPTBot` is OpenAI's training crawler; `OAI-SearchBot` is the retrieval crawler for ChatGPT search | OpenAI documentation (referenced in playbook) | 2026 | Primary (documentation) |
| `ClaudeBot` is Anthropic's training crawler; `Claude-SearchBot` is the retrieval crawler | Anthropic documentation (referenced in playbook) | 2026 | Primary (documentation) |
| `Google-Extended` controls Gemini training, not Google Search or AI Overviews visibility | Google documentation (referenced in playbook) | 2026 | Primary (documentation) |
| User-triggered fetchers (`ChatGPT-User`, `Claude-User`) may not fully honour `robots.txt` | Practitioner consensus; individual provider docs vary | 2026 | Practitioner |
| `ai.txt` is a proposed declarative file; not a Google or OpenAI specification | Spawning.ai / IETF aicontrol proposal (referenced in playbook) | 2026 | Proposed |

---

## llms.txt

| Claim | Source | Date | Label |
|---|---|---|---|
| `llms.txt` was proposed by Jeremy Howard (Answer.AI) in September 2024 | AnswerDotAI proposal [citation:1][citation:13] | 2024-09 | Primary (proposal) |
| Format: H1 (required), blockquote summary, optional detail, H2 sections of `[name](url)` links, `## Optional` section | AnswerDotAI proposal [citation:1][citation:13] | 2024-09 | Primary (proposal) |
| File lives at `/llms.txt` or at a subpath (e.g., `/docs/llms.txt`); agents should use the most specific file | AnswerDotAI proposal [citation:1] | 2024-09 | Primary (proposal) |
| Thousands of sites publish `llms.txt`; documentation platforms generate it automatically; Chrome Lighthouse audits for it as part of agentic browsing checks | AnswerDotAI proposal (v2, updated) [citation:1] | 2026 | Primary (proposal) |
| OpenAI, Anthropic, and Gemini publish `llms.txt` files for their own developer docs | AnswerDotAI proposal [citation:1] | 2026 | Primary (proposal) |
| `llms.txt` is **not** a Google requirement; Google's AI features do not need AI-specific text files | Google documentation, summarised by Safeguard [citation:5] | 2026-10 | Secondary |
| Adoption does not equal effect on citations; treat as a low-cost experiment | Safeguard analysis [citation:5] | 2026-10 | Practitioner |
| `llms-full.txt` and per-page `.md` versions are extensions of the proposal; low-cost, not required | AnswerDotAI proposal [citation:1] | 2026 | Primary (proposal) |

---

## A2A and agent-card.json

| Claim | Source | Date | Label |
|---|---|---|---|
| A2A Agent Card is served at `/.well-known/agent-card.json` | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |
| A2A v1.0 is recommended; v0.3 is also supported | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |
| v1.0 requires `supportedInterfaces` (array of `{url, protocolBinding, protocolVersion}`) | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |
| `skills` array is indexed for keyword search in Agent Registries | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |
| Card size limit: 10 KB | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |
| A2A protocol bindings: `HTTP+JSON`, `JSONRPC`, `GRPC` | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |
| Skills fields: `id`, `name`, `description`, `tags`, `examples` | Google Cloud Agent Registry docs [citation:7] | 2026 | Primary (documentation) |

---

## MCP and mcp-server-card.json

| Claim | Source | Date | Label |
|---|---|---|---|
| MCP Server Cards describe capabilities at `/.well-known/mcp-server-card.json` | PyPI `agent-server-card-mcp` [citation:4] | 2026-03 | Proposed (community) |
| Required fields: `name`, `description`, `version`, `tools` (array of `{name, description}`) | PyPI `agent-server-card-mcp` [citation:4] | 2026-03 | Proposed (community) |
| Optional fields: `author`, `repository`, `categories`, `pricing`, `auth_required`, `transport` | PyPI `agent-server-card-mcp` [citation:4] | 2026-03 | Proposed (community) |
| Transport options: `stdio`, `http`, `both`; pricing: `free`, `freemium`, `paid`, `open-source` | PyPI `agent-server-card-mcp` [citation:4] | 2026-03 | Proposed (community) |
| Alternative path in some implementations: `/.well-known/mcp/server-card.json` (SEP-1649) | MCP World (SEP-1649) [citation:8] | 2026-03 | Proposed (community) |
| Redocly implementation uses `/.well-known/mcp/server-card.json` with `$schema` and `protocolVersion` | Redocly documentation [citation:12] | 2026-08 | Primary (implementation) |

> **Note:** The MCP server card schema is **less standardised** than A2A's. Different implementations use different paths (`/.well-known/mcp-server-card.json` vs. `/.well-known/mcp/server-card.json`) and slightly different field names. The playbook's template uses the more common flat path and the field set from `agent-server-card-mcp` [citation:4].

---

## Structured data

| Claim | Source | Date | Label |
|---|---|---|---|
| JSON-LD is Google's preferred structured data format | Google Search Central documentation (referenced in playbook) | 2026 | Primary (documentation) |
| `sameAs` links help entity disambiguation | Schema.org specification (referenced in playbook) | 2026 | Primary (specification) |
| `Organization` + `sameAs` is high-value for entity recognition | Practitioner consensus; supported by schema.org semantics | 2026 | Practitioner |
| Marking up hidden content is a spam signal | Google spam policies (referenced in playbook) | 2026 | Primary (documentation) |

---

## AI measurement

| Claim | Source | Date | Label |
|---|---|---|---|
| Google Search Console AI visibility reports went live (June 2026), giving impression data for AI Overviews and AI Mode separately | PPC Land [citation:2] | 2026-06 | Secondary |
| Google Merchant Center AI performance insights launched (May 2026) | PPC Land [citation:2] | 2026-05 | Secondary |
| AI Overviews reach 2.5 billion monthly active users | PPC Land [citation:2] | 2026-06 | Secondary |
| AI Overviews correlate with ~58% CTR reduction for top-ranking pages (Ahrefs Feb 2026) | PPC Land [citation:2] | 2026-02 | Secondary (study) |
| Position-one CTR drops from ~27% to ~11% when AI Overviews are present | PPC Land [citation:2] | 2026-02 | Secondary (study) |
| AI referral traffic is trackable via referrer domains (chatgpt.com, perplexity.ai, claude.ai, etc.) | Practitioner consensus; analytics implementation | 2026 | Practitioner |
| Google AI Overview clicks are **not** separately trackable in GA4 (appear as organic) | Practitioner consensus; Google has not provided a separate dimension | 2026 | Practitioner |

---

## Agentic commerce

| Claim | Source | Date | Label |
|---|---|---|---|
| MCP is an open protocol from Anthropic for connecting AI assistants to tools and data | Anthropic MCP specification (referenced in playbook) | 2026 | Primary (specification) |
| A2A is an open protocol for agent-to-agent communication | Google A2A specification (referenced in playbook) | 2026 | Primary (specification) |
| Pay-Per-Crawl is an emerging monetisation model for AI content access | Practitioner monitoring; no single authoritative spec | 2026 | Practitioner |
| Agentic commerce is early; mainstream adoption timelines are uncertain | Multiple industry reports; no consensus | 2026 | Practitioner |

---

## Traditional SEO (Part A) sources

| Claim | Source | Label |
|---|---|---|
| Three-stage pipeline (crawl → index → rank) | Google Search Central documentation | Primary |
| Four search intents (informational, navigational, commercial, transactional) | Industry consensus; Google Search Quality Rater Guidelines | Primary (guidelines) |
| E-E-A-T framework (Experience, Expertise, Authoritativeness, Trustworthiness) | Google Search Quality Rater Guidelines | Primary (guidelines) |
| Spam policy categories (scaled content abuse, site reputation abuse, cloaking, etc.) | Google Search Spam Policies documentation | Primary |
| Core Web Vitals thresholds (LCP ≤ 2.5s, INP ≤ 200ms, CLS ≤ 0.1) | Google Web Vitals documentation | Primary |
| Mobile-first indexing | Google Search Central documentation | Primary |

---

## Claims labelled "practitioner" or "proposed"

These are **not** official statements from Google, OpenAI, Anthropic, or other providers. They reflect community consensus, emerging standards, or reasoned inference. Treat them accordingly:

- `ai.txt` adoption and semantics
- `llms.txt` effect on citations (adoption is documented; effect is not)
- MCP server card path and field standardisation
- AI referral tracking methodology
- Pay-Per-Crawl model details
- Agentic commerce timelines

The playbook flags these as emerging or speculative where they appear.

---

## Primary sources to monitor

For the latest positions, check these directly:

| Source | What it covers |
|---|---|
| **Google Search Central Blog** | AI Overviews, AI Mode, Search updates |
| **Google Search Quality Rater Guidelines** | E-E-A-T, quality standards |
| **Google Spam Policies** | Spam definitions and penalties |
| **OpenAI documentation** (GPTBot, OAI-SearchBot) | OpenAI crawler behaviour |
| **Anthropic documentation** (ClaudeBot, Claude-SearchBot) | Anthropic crawler behaviour |
| **Answer.AI / llms-txt GitHub**  | `llms.txt` proposal updates |
| **Google Cloud Agent Registry docs** [citation:7] | A2A agent card schema |
| **Schema.org** | Structured data vocabulary |

---

## Changelog

| Date | Change |
|---|---|
| 2026-11-10 | Initial research log created; sources compiled for Part A and Part B |

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook).*