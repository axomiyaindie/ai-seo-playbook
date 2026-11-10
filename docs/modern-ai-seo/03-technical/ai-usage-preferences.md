# AI Crawlers and Usage Preferences

> **Part B · Modern AI SEO** · [← Back to Technical](README.md) · Next: [llms.txt](llms-txt.md)

The single most consequential technical decision in AI SEO is **which AI bots you allow to fetch your content**. Sites routinely block "AI bots" to protect their content — and accidentally remove themselves from AI search results in the process. This page explains the bot landscape, the distinction that matters most (training vs. retrieval), and how to configure `robots.txt` and `ai.txt` accordingly.

---

## The three categories of AI bots

AI bots are not one thing. They fall into three categories with **different purposes and different consequences of blocking**.

### 1. Training crawlers

Fetch content to train or improve AI models. Blocking these opts your content out of training data. It does **not** remove you from AI search answers — those use retrieval, not training.

| Bot | Owner | Purpose |
|---|---|---|
| `GPTBot` | OpenAI | Training data for GPT models |
| `ClaudeBot` | Anthropic | Training data for Claude models |
| `Google-Extended` | Google | Training for Gemini (does **not** affect Google Search or AI Overviews) |
| `CCBot` | Common Crawl | Public training dataset used by many models |
| `Bytespider` | ByteDance | Training data |
| `Amazonbot` | Amazon | Training and indexing |
| `meta-externalagent` | Meta | Training data |
| `Applebot-Extended` | Apple | Training for Apple Intelligence |
| `cohere-ai` | Cohere | Training data |

**Blocking these is a legitimate choice** if you don't want your content used for model training. It has no direct effect on AI search visibility.

### 2. Search & retrieval crawlers

Fetch content at **query time** to ground AI answers — and typically cite sources back. Blocking these **removes you from AI answers**.

| Bot | Owner | Purpose |
|---|---|---|
| `OAI-SearchBot` | OpenAI | Retrieval for ChatGPT search |
| `ChatGPT-User` | OpenAI | User-triggered fetch (when a user asks ChatGPT to read a page) |
| `Claude-SearchBot` | Anthropic | Retrieval for Claude search |
| `Claude-User` | Anthropic | User-triggered fetch |
| `PerplexityBot` | Perplexity | Retrieval for Perplexity answers |
| `Perplexity-User` | Perplexity | User-triggered fetch |
| `Googlebot` | Google | Search **and** AI Overviews / AI Mode |
| `Bingbot` | Microsoft | Search **and** Copilot |
| `MistralAI-User` | Mistral | User-triggered fetch |

**Blocking these removes you from AI visibility.** For most sites that want to appear in AI answers, these must be **allowed**.

> **Critical distinction:** `Googlebot` covers both traditional Search and AI Overviews. There is no separate Google AI search bot. Blocking `Googlebot` removes you from both. `Google-Extended` is a *different* token — it controls Gemini training only, and blocking it does **not** affect AI Overviews.

### 3. User-triggered fetchers

Activate when a **user explicitly asks** an AI to fetch a specific page (e.g., "summarise this URL"). Often these are partial-compliance — they may not honour `robots.txt` fully. Treat them as part of the retrieval category for visibility purposes.

---

## Why this distinction matters

The most common AI SEO mistake is this:

```
User-agent: GPTBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: CCBot
Disallow: /
```

This blocks **training** — a defensible choice. But it's often accompanied by:

```
User-agent: *
Disallow: /
```

…or by blocking all "AI" user-agents indiscriminately, which also blocks `OAI-SearchBot`, `Claude-SearchBot`, `PerplexityBot` — **removing the site from AI search entirely**.

The correct approach: **decide separately** whether you want to be in training data and whether you want to be in AI search results. They are different questions.

| Goal | Block training bots | Block retrieval bots |
|---|---|---|
| Protect content from training, stay in AI search | ✅ | ❌ |
| Opt out entirely (training + search) | ✅ | ✅ |
| Maximise AI visibility | ❌ | ❌ |
| Stay out of AI features entirely | ✅ | ✅ (and block Googlebot/Bingbot for full opt-out) |

For most businesses, the first row is the right answer: **block training, allow retrieval**.

---

## Configuring `robots.txt`

`robots.txt` lives at `https://yourdomain.com/robots.txt` and is the primary crawl-control file. AI bots generally respect it (with the user-triggered caveat above).

### Template: block training, allow retrieval

```
# ── Default ──────────────────────────────────────────────
User-agent: *
Allow: /
Disallow: /private/
Disallow: /admin/

# ── Training crawlers (blocked) ──────────────────────────
User-agent: GPTBot
Disallow: /

User-agent: ClaudeBot
Disallow: /

User-agent: Google-Extended
Disallow: /

User-agent: CCBot
Disallow: /

User-agent: Bytespider
Disallow: /

User-agent: Amazonbot
Disallow: /

User-agent: meta-externalagent
Disallow: /

User-agent: Applebot-Extended
Disallow: /

# ── Retrieval crawlers (allowed) ─────────────────────────
User-agent: OAI-SearchBot
Allow: /

User-agent: ChatGPT-User
Allow: /

User-agent: Claude-SearchBot
Allow: /

User-agent: Claude-User
Allow: /

User-agent: PerplexityBot
Allow: /

User-agent: Perplexity-User
Allow: /

User-agent: MistralAI-User
Allow: /

# ── Sitemap ──────────────────────────────────────────────
Sitemap: https://yourdomain.com/sitemap.xml
```

**Rules:**
- Never block CSS/JS for any bot you want to render your page.
- Never block `Googlebot` unless you want to disappear from Google entirely.
- Test with Google Search Console's `robots.txt` tester before deploying.
- Keep a copy of your `robots.txt` in version control so you can roll back.

### Checking what a bot sees

For a specific URL, some AI companies provide verification tools or documentation:
- OpenAI publishes IP ranges and user-agent documentation for `GPTBot` and `OAI-SearchBot`.
- Anthropic publishes `ClaudeBot` / `Claude-SearchBot` documentation.
- Google documents `Googlebot` and `Google-Extended` separately.

Verify against the **official documentation** for each bot — user-agent strings can be spoofed, and the authoritative source is the owner's docs.

---

## `ai.txt` (emerging)

`ai.txt` is a **proposed** declarative file (not yet widely honoured) that signals AI-specific preferences beyond crawl control: use cases, attribution requirements, pricing intent, dataset opt-outs.

It complements `robots.txt` — it doesn't replace it.

**Template** (see [`templates/ai.txt`](../../../templates/ai.txt) for the full version):

```
# ai.txt — AI Crawl Preferences
User-agent: *
Allow: /
Disallow: /private/

# Training: blocked
User-agent: GPTBot
Disallow: /

# Retrieval: allowed
User-agent: OAI-SearchBot
Allow: /

# Attribution requirement: cite as
# "Source: Your Site (https://yourdomain.com)"
```

**Status:** `ai.txt` is not a Google or OpenAI specification. Adoption is uncertain. Add it as a **low-cost hedge** — it doesn't hurt, and if it becomes standard, you're ready.

---

## The decision framework

Ask three questions to decide your configuration:

### 1. Do you want your content used to train AI models?

- **Yes** (e.g., open-source, public interest, or want brand in training data) → allow training bots.
- **No** (e.g., proprietary content, paid content, competitive edge) → block training bots.
- **Undecided** → block by default; you can reverse later.

### 2. Do you want to appear in AI search answers?

- **Yes** (nearly always, for businesses) → allow retrieval bots.
- **No** (e.g., you want to force users to your site directly, which rarely works) → block retrieval bots — but understand this removes you from AI answers.

### 3. Do you operate an API or agent-accessible service?

- **Yes** → consider `.well-known` cards (see [.well-known, Agents, and MCP](well-known-agents-and-mcp.md)).
- **No** → skip.

The most common configuration for a business site: **block training, allow retrieval, publish `.well-known` cards if relevant**.

---

## Monitoring and re-auditing

The AI bot landscape changes fast. Bots appear, user-agents change, and policies shift. Re-audit quarterly.

**What to monitor:**
- **Server logs** — which AI bots are actually fetching your pages. Most CDNs and log tools surface user-agents.
- **Bot documentation** — check each AI company's pages for changes (new bots, deprecated ones, updated IP ranges).
- **Search Console / Bing Webmaster Tools** — for Google and Bing bot behaviour.
- **Your `robots.txt`** — is it still doing what you intended? Blocking a bot you meant to allow is a silent visibility killer.

**Warning signs you've blocked a retrieval bot by mistake:**
- Your site never appears in AI answers, even for queries where you should be a top result.
- Competitors appear in AI answers for your brand queries.
- Your server logs show zero requests from known retrieval bots.

---

## Common mistakes

1. **Blocking all AI bots.** Removes you from retrieval, not just training. Distinguish the two.
2. **Blocking `Googlebot` to "opt out of AI."** Removes you from Google Search entirely. Use `Google-Extended` instead.
3. **Confusing `Google-Extended` with AI Overviews.** They're separate; blocking one doesn't affect the other the way you might think.
4. **Blocking `OAI-SearchBot` but allowing `GPTBot`.** Backwards for AI visibility: you've allowed training but blocked the retrieval that would cite you.
5. **Forgetting `ChatGPT-User` and `Claude-User`.** User-triggered fetchers matter for pages users share with AI.
6. **Not testing changes.** Deploy `robots.txt` changes carefully; a typo can block everything.
7. **Not monitoring server logs.** You can't manage what you don't see.
8. **Treating `ai.txt` as a requirement.** It's a hedge, not a necessity.
9. **Blocking CSS/JS for allowed bots.** Breaks rendering; page looks blank.
10. **Not re-auditing.** Bots change; last year's config may be wrong now.

---

## Key takeaways

- **Three bot categories:** training (blockable), retrieval (must be allowed for AI visibility), user-triggered (part of retrieval).
- **Blocking training does not affect AI search visibility.** Blocking retrieval does.
- **`Googlebot` covers both Search and AI Overviews** — don't block it if you want either.
- **`Google-Extended` controls Gemini training only** — separate from Googlebot.
- **`robots.txt` is the primary control.** `ai.txt` is an emerging complement, not a replacement.
- **The common configuration:** block training, allow retrieval, publish `.well-known` cards where relevant.
- **Monitor server logs and re-audit quarterly.** Bot landscapes change.

---

**Next:** [llms.txt](llms-txt.md) — the proposed standard for LLM-facing content maps: format, adoption, and when it's worth using.

---

*Part of the [AI SEO Playbook](https://github.com/rakibuli10/ai-seo-playbook). Every claim is sourced in the [research log](../../RESEARCH-LOG.md).*