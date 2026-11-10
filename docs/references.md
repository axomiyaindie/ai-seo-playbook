# References and Official Links

> Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Official specifications, documentation, and monitoring sources for every standard covered in the playbook.

This page collects the **primary sources** â€” the official specs, documentation, and blogs â€” so you can verify claims and monitor updates. Where a standard is emerging or proposed, that's noted.

**Last updated:** 2026-11-10

---

## Model Context Protocol (MCP)

| Resource | URL | Status |
|---|---|---|
| **Official specification** | https://modelcontextprotocol.io/specification/2026-07-28/ | âœ… Current |
| **Architecture** | https://modelcontextprotocol.io/specification/2026-07-28/architecture | âœ… |
| **Base protocol** | https://modelcontextprotocol.io/specification/2026-07-28/basic | âœ… |
| **Server features** | https://modelcontextprotocol.io/specification/2026-07-28/server | âœ… |
| **GitHub (spec source)** | https://github.com/modelcontextprotocol/specification | âœ… |
| **Main site** | https://modelcontextprotocol.io | âœ… |

**What it is:** An open protocol from Anthropic for connecting LLM applications to external data sources and tools. Uses JSON-RPC 2.0. Hosts â†’ Clients â†’ Servers architecture.

**MCP Server Cards:** Described at `/.well-known/mcp-server-card.json`. Note: the card schema is **less standardised** than A2A's â€” different implementations may use `/.well-known/mcp/server-card.json`. The playbook's template uses the more common flat path.

---

## Agent2Agent (A2A) Protocol

| Resource | URL | Status |
|---|---|---|
| **Official specification** | https://a2a-protocol.org/latest/specification/ | âœ… v1.0.0 |
| **Documentation home** | https://a2a-protocol.org/latest/ | âœ… |
| **Normative Protobuf** | https://github.com/a2aproject/A2A/blob/main/specification/a2a.proto | âœ… Source of truth |
| **JSON Schema (non-normative)** | https://a2a-protocol.org/latest/spec/a2a.json | âœ… Generated |
| **GitHub org** | https://github.com/a2aproject | âœ… |
| **Quickstart (Python)** | https://a2a-protocol.org/latest/tutorials/python/1-introduction/ | âœ… |
| **A2A and MCP** | https://a2a-protocol.org/latest/topics/a2a-and-mcp/ | âœ… |

**What it is:** An open protocol originated by Google, donated to the Linux Foundation, for agent-to-agent communication. Agents discover capabilities via `/.well-known/agent-card.json`. v1.0 uses `supportedInterfaces` (required), `skills`, `capabilities`.

**Agent Card path:** `/.well-known/agent-card.json` (standard).

---

## llms.txt

| Resource | URL | Status |
|---|---|---|
| **Official proposal site** | https://llmstxt.org/ | âš ï¸ Proposed |
| **GitHub (Answer.AI)** | https://github.com/AnswerDotAI/llms-txt | âš ï¸ Proposed |
| **PyPI package** | https://pypi.org/project/llms-txt/ | âš ï¸ Proposed |
| **Full consolidated docs (A2A's own llms.txt)** | https://a2a-protocol.org/llms.txt | ðŸ“„ Example |

**What it is:** A proposed standard (Jeremy Howard, Answer.AI, late 2024) for a markdown file at `/llms.txt` that gives LLMs a curated content map.

**Format:** H1 (required), blockquote summary (recommended), optional detail, H2 sections of `[name](url)` links, `## Optional` for skippable links.

**Status:** **Proposed, not a Google/OpenAI requirement.** No major AI provider has documented using it to determine retrieval or citation. Low-cost hedge, not a lever.

---

## ai.txt

| Resource | URL | Status |
|---|---|---|
| **Official spec (aitxt.ing)** | https://aitxt.ing/ai.txt | âš ï¸ Proposed |
| **GitHub (markc/aitxt)** | https://github.com/markc/aitxt | âš ï¸ Proposed |
| **GitHub (kaylacar/ai-txt)** | https://github.com/kaylacar/ai-txt | âš ï¸ Proposed |
| **IETF draft** | `draft-car-ai-txt-wellknown-00` (Datatracker) | âš ï¸ Under review |

**What it is:** A proposed standard for declaring a website's AI policy â€” training permissions, licensing, attribution, per-agent rules.

**Status:** **Proposed, not adopted.** Two competing proposals exist (`markc/aitxt` and `kaylacar/ai-txt`). IANA #76/#77 filed; IETF draft under review. Treat as emerging.

---

## Schema.org

| Resource | URL | Status |
|---|---|---|
| **Official site** | https://schema.org/ | âœ… Standard |
| **Developer documentation** | https://schema.org/docs/developers.html | âœ… |
| **Releases** | https://schema.org/docs/releases.html | âœ… |
| **GitHub** | https://github.com/schemaorg/schemaorg | âœ… |
| **Blog** | https://blog.schema.org/ | âœ… |
| **JSON-LD context** | https://schema.org/docs/jsonldcontext.json | âœ… |

**What it is:** The shared vocabulary for structured data on the web. Used for rich results and AI retrieval.

**Key schemas for AI:** `Organization`, `Person`, `Article`, `FAQPage`, `Product`, `SoftwareApplication`, `BreadcrumbList`, `HowTo`, `QAPage`.

---

## Google AI Search

| Resource | URL | What it covers |
|---|---|---|
| **Google Search Central Blog** | https://developers.google.com/search/blog | AI Overviews, AI Mode, Search updates |
| **Google Search Central Docs** | https://developers.google.com/search/docs | Official SEO guidance |
| **Search Quality Rater Guidelines** | https://guidelines.raterhub.com/searchqualityevaluatorguidelines.pdf | E-E-A-T, quality standards |
| **Spam Policies** | https://developers.google.com/search/docs/essentials/spam-policies | Spam definitions |
| **Search Console** | https://search.google.com/search-console | Your site's data |
| **Rich Results Test** | https://search.google.com/test/rich-results | Schema validation |

**Key Google position:** AI Overviews and AI Mode use the **same index and core ranking systems** as traditional Search. No special optimisation required.

---

## Microsoft Bing / Copilot

| Resource | URL | What it covers |
|---|---|---|
| **Bing Webmaster Blog** | https://blogs.bing.com/webmaster | AI grounding, index updates |
| **Bing Webmaster Tools** | https://www.bing.com/webmasters | Your site's data |
| **Bing Webmaster Guidelines** | https://www.bing.com/webmasters/help/webmasters-guidelines-30fba23a | Official guidelines |

**Key Microsoft position (May 2026):** AI grounding is **not the same as search indexing**. Grounded answers require accurate, fresh, attributable, consistent evidence. "Abstention" â€” the AI declining to answer when evidence is missing/stale/contradictory â€” is legitimate behaviour.

---

## AI Crawler Documentation

| Provider | Resource | URL |
|---|---|---|
| **OpenAI** | GPTBot / OAI-SearchBot docs | https://platform.openai.com/docs/gptbot |
| **Anthropic** | ClaudeBot / Claude-SearchBot docs | https://support.anthropic.com/en/articles/8896518 |
| **Google** | Googlebot / Google-Extended | https://developers.google.com/search/docs/crawling-indexing/google-common-crawlers |
| **Common Crawl** | CCBot | https://commoncrawl.org/ccbot |

**Key distinction:** Training bots (blockable) â‰  retrieval bots (must be allowed for AI visibility). See [AI Crawlers](modern-ai-seo/03-technical/ai-usage-preferences.md).

---

## Research and Studies

| Study | What it found | URL |
|---|---|---|
| **Ahrefs AI Overviews study (Feb 2026)** | ~58% CTR reduction for top-ranking pages when AI Overviews present | https://ahrefs.com/blog/ |
| **Ahrefs citation overlap study (Aug 2026)** | Only ~38% of AI Overview-cited URLs also rank top 10 (down from ~76% in mid-2025) | https://ahrefs.com/blog/ |
| **Volpini et al. (2026)** | Materialised entity pages improved retrieval accuracy by 29.6% vs. JSON-LD-only | Zenodo (referenced in ) |

**Note:** Studies are point-in-time. AI search changes fast. Treat findings as directional, not permanent.

---

## Monitoring checklist

Check these **quarterly** for updates:

- [ ] **MCP specification** â€” new version? (modelcontextprotocol.io)
- [ ] **A2A specification** â€” new version? (a2a-protocol.org)
- [ ] **llms.txt** â€” adoption news? (llmstxt.org)
- [ ] **ai.txt** â€” IETF status? (Datatracker)
- [ ] **Schema.org** â€” new releases? (schema.org/docs/releases)
- [ ] **Google Search Central Blog** â€” AI feature changes?
- [ ] **Bing Webmaster Blog** â€” AI grounding changes?
- [ ] **Crawler docs** â€” new bots or user-agent changes?

---

## Status legend

| Symbol | Meaning |
|---|---|
| âœ… **Standard** | Widely adopted, stable |
| âš ï¸ **Proposed** | Specification exists; adoption uncertain |
| ðŸ“„ **Example** | Real-world implementation |

---

## Related playbook pages

- [AI Crawlers](modern-ai-seo/03-technical/ai-usage-preferences.md) â€” bot landscape
- [llms.txt](modern-ai-seo/03-technical/llms-txt.md) â€” proposal details
- [Structured Data](modern-ai-seo/03-technical/structured-data.md) â€” schema.org implementation
- [.well-known, Agents, and MCP](modern-ai-seo/03-technical/well-known-agents-and-mcp.md) â€” agent cards
- [Research Log](RESEARCH-LOG.md) â€” claim-by-claim sourcing

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook).*
