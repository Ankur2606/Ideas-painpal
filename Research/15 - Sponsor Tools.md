---
title: "15 - Sponsor Tools"
type: research
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [research, paypal-hackathon]
up: "[[00 - PayPal AI Hackathon Hub]]"
description: "AG Grid, APIMatic, Astropods, Bryntum, Channel3, Elastic, KERNEL, Postman, Render, Zapier"
confidence_key: "✅ primary / ⚠️ secondary / ❌ unverified"
---
# Sponsor tools

_Extract of section 1 of the event report._

## 1. Sponsor tools

### Prize map (who actually pays)

| Sponsor | Prize | Winners | Total | Source |
|---|---|---|---|---|
| AG Grid | $5,000 / $2,000 / $1,000 ×3 | 5 | **$10,000** | ✅ [Rules §8](https://paypalaihackathon.devpost.com/rules) |
| APIMatic | $1,000 + 6 months Business subscription | 3 | $3,000 + subs | ✅ Rules §8 |
| Bryntum | $1,000 | 3 | $3,000 | ✅ Rules §8 |
| Channel3 | $1,500 | 1 | $1,500 | ✅ Rules §8 |
| Render | $1,000 / $750 / $500 in **credits** | 3 | $2,250 credits | ✅ Rules §8 |
| Astropods, Elastic, KERNEL, Postman, Zapier | **No prize.** Free access only | 0 | — | ✅ Rules §8 (not listed) |

⚠ inference: AG Grid offers the deepest sponsor pool. Its 1st place ($5k) equals an Honorable Mention, and it pays out to 5 winners. A project can hold one sponsor prize on top of a Grand Prize or HM (Rules §8; ✅ [FAQ](https://paypalaihackathon.devpost.com/details/faqs)), so the best pairing for sponsor EV is an AG Grid (or Bryntum) prize alongside a main prize. Only the highest single sponsor prize counts, so stacking several sponsor tools adds eligibility but not cash.

---

### 1.1 AG Grid (AG Studio + Studio Agent Framework)
- **What it is:** AG Studio is an "embedded analytics library… dashboards, charts, and grids together in one component." It has a built-in data engine, cross-filtering, and the **Studio Agent Framework**, "so agents can build, query, and edit dashboards for you and alongside you." ✅ [details/aggrid](https://paypalaihackathon.devpost.com/details/aggrid)
- **Access:** Free 45-day trial license, plus an official boilerplate repo, [paypaldev/hackathon-paypal-ag-grid-boilerplate](https://github.com/paypaldev/hackathon-paypal-ag-grid-boilerplate), with AG Studio and PayPal already wired up. ✅ same page
- **Prize criteria (stated):** "covers both what your dashboard looks like and how you build it. Show us polish: custom widgets, theming, and layout tools, not just AG Grid or AG Charts on their own. Take Studio Agent Framework for a spin: a custom agent talking to Studio's built-in agents, or a swapped-in harness." ✅ same page
- **Ideas they suggested (so these will be duplicated):** storefront analytics for fictional TV businesses, an anomaly-alert agent for refund spikes, a nonprofit donation dashboard, an NL finance agent, and an unpaid-invoice "nudge-bot." ✅ same page
- **Framework details:** Published Sep 28, 2026 (Josh Hobson). It is modular: the harness runs in the browser and manages multiple agents. Runners can be local, Vercel AI SDK, or custom. Agent definitions, chat UI and tools are all swappable. It is "disabled until you connect your own LLM." ✅ [AG Grid blog](https://www.ag-grid.com/blog/introducing-the-ag-studio-agent-framework/)
- **Webinar:** Oct 12, 7am PT, "Build a payments dashboard without building a dashboard." ✅ [Overview](https://paypalaihackathon.devpost.com/)
- **Non-obvious PayPal + AI combo** (⚠ inference): Make the **dashboard the agent's control surface, not a report**. For example, a PayPal Disputes "war room" where a custom domain agent (a dispute-evidence specialist) talks to Studio's built-in widget agents. Each dispute row gets a generated evidence-readiness widget, and approving it from the grid calls the PayPal Disputes API. That hits "custom agent talking to Studio's built-in agents" plus custom widgets, and it is a real merchant pain point. Avoid the suggested donation, storefront and nudge ideas verbatim.

### 1.2 APIMatic (Context Plugins for PayPal)
- **What it is:** Turns API specs into SDKs, portals, MCP servers and **Context Plugins**: agent plugins that inject authoritative PayPal API context into Claude Code, Cursor, Codex and Copilot. ✅ [details/apimatic](https://paypalaihackathon.devpost.com/details/apimatic), ✅ [webinar](https://youtu.be/zRWixN68tDg)
- **Coverage:** PayPal Server SDKs in TypeScript, Python, Java, Ruby, PHP and C#, across five APIs: **Orders, Payments, Vault, Subscriptions, Transaction Search**. It installs with one `npx` command, and no APIMatic credentials are needed. ✅ webinar transcript
- **Access:** Anyone who used the plugin gets 1 month of APIMatic Basic. Winners get 6 months of Business. Claim via a [Google Form](https://docs.google.com/forms/d/e/1FAIpQLScc2oCgAFACm7d6H3R4mgzv-O34DdyVnLIBNiwmUNggr_-hhA/viewform). ✅ details page
- **Prize requirement:** "You just have to utilize the context plugin in some way while building your hackathon project. Then answer the plug-in question on the submission form." ✅ webinar transcript (Nathaniel Olson)
- **Claims:** About 50× cheaper context than alternatives on their "production readiness" benchmark. Their argument is that code generated from a bare OpenAPI spec "only works for the happy flows. It doesn't account for errors… retries… server going down." ✅ webinar (vendor claim, unverified)
- **Non-obvious combo** (⚠ inference): The bar to qualify is minimal, so this is a near-free extra prize ticket for any team using a coding agent. To *win* it, show the plugin's effect: resilient retry, idempotency and error paths in the PayPal integration, plus a short README section on how the plugin shaped the integration. That speaks to APIMatic's "production-ready by default" pitch.

### 1.3 Astropods (Postman's agent runtime)
- **What it is:** An "agent operating system for running AI agents in production": models, knowledge stores, tool integrations, observability, runtime and guardrails. Agents are defined in a declarative `astropods.yml` plus an `AGENT.md` Agent Card. The CLI (`ast project create/start`, `ast blueprint push/deploy`) handles the lifecycle. Other pieces are a Remote Sandbox VM, a Messaging SDK (Slack and web chat over gRPC), an AI Gateway, and **evaluators** that run on production traces. ✅ [docs.astropods.com](https://docs.astropods.com/), ✅ [details/astropods](https://paypalaihackathon.devpost.com/details/astropods)
- **Ownership:** **Astropods is a Postman product.** The docs footer reads "© 2026 Postman." The walkthrough, published Oct 7, 2026, was written by **Pooja Mistry** (a Postman judge). It calls Astropods "the agent operating system layer" in the Postman AI stack and lists automated evaluation that flags "unnecessary tool calls, exposed personal data, and negative user sentiment." ✅ [Postman blog](https://blog.postman.com/build-ai-agents-with-astropods/)
- **Access:** Free account. There is no dedicated prize. ✅ details page
- **Non-obvious combo** (⚠ inference): Deploy a PayPal-acting agent on Astropods and **show its evaluator dashboard in the demo**: traces of every PayPal tool call, cost per transaction, and a custom evaluator that flags any money movement made without a matching approval. That turns "trust the agent with money" into something visible. It also hands the Postman judge her own product in a non-trivial role. There is no Astropods prize, but it plausibly lifts Technological Implementation scores.

### 1.4 Bryntum (Gantt / Scheduler / Calendar)
- **What it is:** Commercial JS components for anything time-based. ✅ [details/bryntum](https://paypalaihackathon.devpost.com/details/bryntum)
- **Access:** 45-day trial (`npm install @bryntum/scheduler@npm:@bryntum/scheduler-trial`). ✅ same page. Bryntum also runs an MCP server (mcp.bryntum.com), agent skills and agent-readable docs. ✅ [bryntum.com/agents](https://bryntum.com/agents/)
- **Prize criteria:** "the cleanest timeline, the smartest resource booking, or an agent that drives the schedule itself." ✅ details page
- **Ideas they suggested:** Agency Gantt with payment tranches as dependencies, equipment rental locked on payment, ticketing calendar, subscription revenue radar, a **dispute triage board**, and an agent-driven rescheduler driven by payment webhooks. ✅ details page
- **Corporate link:** AG Grid and Bryntum co-organised the "Beyond the Prompt" conference (London, May 19, 2026). ✅ [agenda JSON](https://ag-grid.com/downloads/beyond-the-prompt/beyond-the-prompt-agenda.json). A law-firm notice describes a "partnership with AG Grid" involving Adelis Equity Partners. ⚠️ [Travers Smith](https://www.traverssmith.com/knowledge/knowledge-container/travers-smith-advises-adelis-equity-partners-and-bryntum-on-partnership-with-ag-grid/). The Bryntum intro session is hosted on AG Grid's Livestorm account. ✅ details page
- **Non-obvious combo** (⚠ inference): **Cash-flow-aware scheduling.** PayPal Pay Later or Subscriptions webhooks drive a Scheduler where an agent re-plans resource allocation (contractors, rooms, shifts) based on *when money actually lands*. Payouts to contractors are released by the Gantt dependency graph. A single project could use both AG Studio and Bryntum (same corporate family), but only one sponsor prize can be won.

### 1.5 Channel3 (product catalog API for agents)
- **What it is:** "One API returns clean, normalized product data – titles, images, prices, variants, availability, and buy links – across 100M+ products from 25,000+ retailers." ✅ [details/channel3](https://paypalaihackathon.devpost.com/details/channel3)
- **Access:** 20,000 free credits with promo **PAYPAL-HACKATHON-2026**. They will top up on Discord: "don't let credits block your demo." ✅ same page
- **Prize requirement:** "Your project may use the Channel3 API or our MCP server as a meaningful part of the product experience — search, product enrichment or recommendations. Projects that only reference Channel3 without calling it will not meet this requirement." ✅ same page
- **Depth from their docs:**
  - Search works by text, **image**, or **URL**, with filters for price, brand, category, dimensions and attributes. It returns offers from multiple retailers. ✅ [docs](https://docs.trychannel3.com/)
  - Access surfaces: REST API, SDK, **MCP** (`https://mcp.trychannel3.com/`, no key for the free tier), CLI, **UCP** profile (`ucp.trychannel3.com`, with tools `search_catalog`, `lookup_catalog`, `get_product`), and **MPP** (pay-per-call, no signup). ✅ [docs](https://docs.trychannel3.com/), [UCP](https://docs.trychannel3.com/use-cases/ucp), [MCP](https://docs.trychannel3.com/mcp-overview)
  - **Monetization:** buy URLs are attributed to the developer, so partner-brand commissions apply. Channel3 does **not** do checkout. Its UCP flow ends at a buy link. ✅ [UCP page](https://docs.trychannel3.com/use-cases/ucp)
  - Company: raised a $6M seed led by Matrix in Dec 2025. Its stated vision is a "neutral, storefront-agnostic catalog of every product sold online." ⚠️ [SiliconANGLE](https://siliconangle.com/2025/12/10/channel3-raises-6m-make-every-single-product-sold-web-discoverable-ai-agents/)
- **The gap PayPal fills** (⚠ inference): Channel3 handles discovery and PayPal handles payment. Every "shopping agent" team will join the two the obvious way (agent searches, then a PayPal checkout button). That is the single most duplicated pattern expected in this hackathon (see §4).
- **Non-obvious combos** (⚠ inference):
  - (a) **Reverse direction / seller side:** use Channel3 image search to price-check an item a seller photographs. Then create a PayPal invoice or Payment Link priced against live market offers, so the agent is a seller's pricing analyst. Duplicates exist (SHELF, Resell.Store on Devpost, see §4), so differentiate hard.
  - (b) **Dispute evidence:** for a PayPal "item not as described" dispute, use Channel3 URL/lookup to pull the canonical product spec and attach it as structured evidence.
  - (c) **Refund-to-replacement:** after a PayPal refund, the agent finds equivalent in-stock items across retailers.
  - (d) **Gift registry / group funding:** many payers fund one Channel3-sourced item through PayPal, with an agent that tracks price and stock until the goal is met.

### 1.6 Elastic (Elasticsearch, Agent Builder, Workflows)
- **What it is:** A search and analytics engine with hybrid and vector search. ✅ [details/elastic](https://paypalaihackathon.devpost.com/details/elastic)
- **Suggested use (sponsor page):** "build a multi-step AI agent that uses Elasticsearch combining a **Jina embedding model**," optionally with "Elastic Agent Builder, Elastic Workflows, Search, ES|QL, Observability, Security, or the A2A/MCP connectivity." ✅ same page
- **Access:** 14-day serverless trial via [ela.st/elastic-paypal-hackathon](https://ela.st/elastic-paypal-hackathon), self-extendable by 30 days ([form](https://www.elastic.co/trialextension)), or run locally for free. ✅ same page. No prize.
- **Agent Builder:** Agents grounded in your indices. Custom tools can be ES|QL, index search, MCP or workflow tools. It **exposes agents over an MCP server and an A2A server**, and agents can trigger Workflows (and the reverse). ✅ [Elastic docs](https://www.elastic.co/docs/explore-analyze/ai-features/elastic-agent-builder). It went GA on Jan 22, 2026. Workflows was in tech preview at that point. ⚠️ [press release via Nasdaq](https://www.nasdaq.com/press-release/elastic-announces-general-availability-agent-builder-expanded-capabilities-2026-01-22)
- **Non-obvious combo** (⚠ inference): Index PayPal **webhook events plus Transaction Search output** into Elasticsearch, and use ES|QL tools in Agent Builder for anomaly and fraud-pattern investigation (refund spikes, dispute clusters by SKU). Expose the agent via A2A so a *separate* PayPal-acting agent (for example, a refund agent) must consult it before moving money. That is agent-to-agent risk checking, which matches Carly Richmond's "context engineering" theme (§2).

### 1.7 KERNEL (browser infrastructure for agents)
- **What it is:** "Cloud infrastructure for AI agents to act on the internet. <30ms browser spin-up, reliable bot anti-detection… 24fps live session view with full replay." Managed auth keeps agents logged in. It runs headful Chromium and works "with every agent harness and cua model." ✅ [details/kernel](https://paypalaihackathon.devpost.com/details/kernel)
- **Access:** **$50 in credits** via [dashboard link with code KERNELDEVPOST2026](https://dashboard.onkernel.com/hackathon?code=KERNELDEVPOST2026). No prize. ✅ same page
- **Depth from docs:**
  - Browser starts in about 30ms (p50) and 105ms (p99), each in an isolated VM. A standby mode stops billing about 5s after disconnect. Each session has a REPL, process exec and SSH. The browser image and VM runtime are open source. ✅ [kernel.sh/docs](https://www.kernel.sh/docs)
  - **Payments primitive:** browser agents complete purchases without handling raw card data. Wallet integrations are **Link (Stripe)**, which issues a single-use card per purchase, and **AgentCard**. A `fill` API injects vault values into fields without them passing through app code *or the model's context*. There is no PayPal wallet integration. ✅ [payments doc](https://www.kernel.sh/docs/browsers/payments)
  - Cookbooks include **"Personal Shopper,"** Claude Computer Use loop, Browser Use, Stagehand + Google CUA, and Mastra. Integrations cover Claude Agent SDK, OpenAI Agents SDK, Vercel AI SDK and 1Password. There is also a page on buying a browser with MPP. ✅ [llms.txt index](https://www.kernel.sh/docs/llms.txt)
- **Non-obvious combo** (⚠ inference): KERNEL's payment wallets are Stripe-centric, so **the obvious "browser agent buys stuff" is both duplicated and competitor-aligned.** Better:
  - (a) **Merchant-side QA agent:** a KERNEL browser walks a merchant's own PayPal sandbox checkout end to end (happy and unhappy paths, as Eddie Jaoude stressed in the kickoff). The replay recording is attached as evidence, and failures are diagnosed with PayPal's `/paypal:explain-error` logic.
  - (b) **Dispute evidence collector:** the agent logs into carrier or tracking portals the merchant uses (managed auth), screenshots proof-of-delivery, and submits it through the PayPal Disputes API. Live view plus replay gives the judges an auditable trail.
  - (c) Use the `fill`-style idea of keeping secrets out of model context as a design principle and *say so*. It speaks to Jo Franchetti's security interests (§2).

### 1.8 Postman
- **What it is:** API lifecycle platform. ✅ [details/postman](https://paypalaihackathon.devpost.com/details/postman) (WebFetch summary)
- **Access:** Free sign-up, the **official PayPal Postman collection** ([postman.com/paypal](https://postman.com/paypal), which includes "examples for agentic commerce" per Marco Podien), and a "Learn API by doing" path focused on AI. No prize. ✅ details page, ✅ kickoff transcript
- **Non-obvious combo** (⚠ inference): Ship a **Postman collection of your project's own API** (for example, the endpoints your agent exposes) with tests that run your PayPal flows, and link it in the README so judges can test in one click. Postman's MCP server also lets agents use the Postman API. ⚠️ [Postman docs](https://learning.postman.com/docs/developer/postman-api/postman-mcp-server/overview). Pairs naturally with Astropods (same company).

### 1.9 Render
- **What it is:** Cloud platform for apps and agents. Web services, Postgres, workers, and **Render Workflows**, where tasks are defined as functions with the SDK and fanned out across "hundreds of concurrent instances." ✅ [details/render](https://paypalaihackathon.devpost.com/details/render) (WebFetch summary)
- **Access:** **$50 in Render credits** via the claim link. ✅ details page
- **Prize:** $1,000 / $750 / $500 in credits for "Eligible Submissions that use any Render tools." No further criteria published. ✅ Rules §8
- **Workflows:** TypeScript and Python SDKs. Each run gets its own instance, runs up to 24 hours, retries automatically, and can chain or await child tasks. Agent orchestration is a headline use case, with a `run_agent` example fanning out to `gather_context`, `execute_skills` and `compose_response`. No native scheduling. ✅ [Render docs](https://www.render.com/docs/workflows)
- **Non-obvious combo** (⚠ inference): Use Workflows as the **durable, retryable backbone for money-moving agent steps**: idempotent capture, webhook-driven continuation, compensation (refund) tasks on failure. A hosted Render URL also satisfies the "functional demo" requirement with no setup friction for judges.

### 1.10 Zapier (Zapier MCP)
- **What it is:** Zapier MCP lets AI tools (Claude, ChatGPT, Cursor) take actions across 9,000+ apps, **including PayPal**, with Zapier handling auth. ✅ [details/zapier](https://paypalaihackathon.devpost.com/details/zapier) (WebFetch summary)
- **Access:** 14-day Professional trial, no card. No prize. ✅ details page
- **Risk** (⚠ inference): A project whose PayPal use runs *only* through Zapier's PayPal actions may look like "PayPal bolted on" (Jo Franchetti: "adding a PayPal button to an unrelated app is not going to be enough," ✅ kickoff). Use Zapier for the *non-PayPal* side effects (CRM, Sheets, Slack), and call PayPal APIs or the PayPal MCP directly.

### 1.11 PayPal's own AI tooling (the core requirement)
- **PayPal AI Toolkit** ([github.com/paypal/AI-Toolkit](https://github.com/paypal/AI-Toolkit), Apache-2.0). It is a Claude Code plugin (Codex via its plugin marketplace per the kickoff) with:
  - the `paypal-best-practices` skill
  - commands `/paypal:setup`, `/paypal:sandbox`, `/paypal:test-accounts`, `/paypal:explain-error`, `/paypal:doctor`
  - a PreToolUse hook that forces SDK-version checks
  - a sandbox MCP server covering Orders/Payments, Invoices (including QR), Subscriptions, Disputes, Catalog, Shipment and Reporting

  ✅ repo README, ✅ kickoff transcript. On Oct 11 the repo had **4 commits, 3 stars, 0 forks.** ✅ repo
- **Agent Toolkit** (distinct from the AI Toolkit) offers framework adapters for LangChain, CrewAI, Mastra and Vercel AI SDK. There is also an MCP server and agent tools reference. ✅ kickoff transcript (Marco), ✅ [Resources](https://paypalaihackathon.devpost.com/resources) → [docs.paypal.ai](https://docs.paypal.ai/)
- **Jo Franchetti invited PRs:** "having I shipped a commit to the PayPal org is a brilliant thing to have on that CV… we absolutely will review them and get them merged." ✅ kickoff transcript. ⚠ inference: the toolkit is young (3 stars), so a team that **upstreams a real fix or new error code to paypal/AI-Toolkit during the hackathon and cites the merged PR** earns unusual goodwill from the three DevRel judges.
- Agentic-commerce context: PayPal launched "Agentic Commerce Services" (**Agent Ready**, **Store Sync**) on Oct 28, 2025, with Perplexity named as a discovery surface. ✅ [PayPal newsroom](https://newsroom.paypal-corp.com/2025-10-28-PayPal-Launches-Agentic-Commerce-Services-to-Power-AI-Driven-Shopping). The same day, a PayPal–OpenAI partnership covered paying inside ChatGPT. ⚠️ [TechCrunch](https://techcrunch.com/2025/10/28/paypal-partners-with-openai-to-let-users-pay-for-their-shopping-within-chatgpt). One Devpost project title mentions "PayPal's Cart API" for agents (AgentBaazar). ⚠️ [Devpost listing](https://devpost.com/software/built-with/paypal?page=3)

---

