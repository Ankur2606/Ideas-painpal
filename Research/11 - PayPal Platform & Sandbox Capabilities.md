---
title: "11 - PayPal Platform & Sandbox Capabilities"
type: research
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [research, paypal-hackathon]
up: "[[00 - PayPal AI Hackathon Hub]]"
description: "PayPal APIs, sandbox behaviour, agent tooling gaps"
confidence_key: "✅ primary / ⚠️ secondary / ❌ unverified"
---
# A. PayPal developer platform: what AI and agent projects can actually use (primary-source intel)

**Prepared for:** PayPal AI Hackathon 2026 team (Devpost, submissions Oct 1 – Nov 12 2026)
**Research date:** 2026-10-11
**Method:** I cloned and read the repos file by file: `paypal/AI-Toolkit`, `paypal/agent-toolkit`, `paypal/ruleshub` and `paypaldev/getting-started-with-paypal-sandbox`. I read the `developer.paypal.com` `.md` doc pages and the `llms.txt` indexes directly, and scraped the GitHub issue and PR lists. Press items were cross-checked against the PayPal newsroom where possible.

**Confidence legend:**
- ✅ I read it directly in a primary source: a PayPal repo, PayPal docs or the PayPal newsroom.
- ⚠️ Secondary source, press coverage or a single source.
- ❌ Could not verify.
- `⚠ inference` marks my own reasoning, not a sourced fact.

---

## 0. TL;DR for the team (read this first)

1. **"PayPal AI-Toolkit" is not an agent SDK any more. It is a coding-assistant plugin.** `github.com/paypal/AI-Toolkit` was created on 2026-07-08 and is at v1.2.0. It bundles skills, slash commands, a hook and a pointer to PayPal's hosted **sandbox MCP server** (`https://mcp.sandbox.paypal.com/sse`) for Claude Code, Codex and Cursor. It has no runtime code and nothing for your app to import. ✅ [repo README](https://github.com/paypal/AI-Toolkit), [.mcp.json](https://github.com/paypal/AI-Toolkit/blob/main/.mcp.json)
2. **The agent SDK you embed in an app is `github.com/paypal/agent-toolkit`.** Packages: `@paypal/agent-toolkit` (npm) and `paypal-agent-toolkit` (PyPI), both v1.11.0. They support OpenAI Agents SDK, Vercel AI SDK, LangChain, CrewAI, Amazon Bedrock and MCP. The toolkit exposes about 46 tools across invoices, orders, refunds, disputes, tracking, catalog, subscriptions, transactions and insights. ✅ [agent-toolkit README](https://github.com/paypal/agent-toolkit)
3. **The hosted sandbox MCP server was broken on 2026-10-08.** Every tool call returned `PAYPAL_API_SETUP_ERROR "Unsupported cache mode: default"`. As of 2026-10-11 the issue is still open, with no assignee and no fix. A second developer confirmed it. ✅ [AI-Toolkit #34](https://github.com/paypal/AI-Toolkit/issues/34) **Build a fallback: the local `@paypal/mcp`, agent-toolkit in-process, or direct REST.**
4. **The agent tooling leaves big gaps.** It has no Payouts, Vault/payment-method tokens, authorize/void/reauthorize, webhooks, Payment Links, dispute evidence/offer/escalate, spend limits or human approval. `create_order` hardcodes `intent: 'CAPTURE'`. Idempotency headers are effectively never set. ✅ (code read, details in §1.3 and §6)
5. **Agentic commerce products (Agent Ready, Store Sync, WebMCP) are gated or enterprise.** Store Sync and the agentic commerce services need an access-request form. Agent Ready runs through **Braintree** (ACP for ChatGPT, UCP for Google). In the ACP docs the PayPal wallet and Venmo wallet are still listed as "coming soon". ✅ [ACP doc](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md)
6. **The sandbox is much richer than most teams know.** It has sandbox-only Disputes endpoints to *create* disputes and chargebacks, change reasons, adjudicate and force evidence states. It also has the `PayPal-Mock-Response` negative-testing header, a large set of Payouts test values and amount-based dispute escalation simulation. ✅ [disputes test-go-live](https://developer.paypal.com/disputes/test-go-live.md), [sandbox repo](https://github.com/paypaldev/getting-started-with-paypal-sandbox)

---

## 1. PayPal AI and agent tooling

### 1.1 `paypal/AI-Toolkit`: a coding-agent plugin (cloned at commit `5dce83d`)

| Attribute | Value | Src |
|---|---|---|
| What it is | "A plugin that integrates PayPal's APIs and MCP server across multiple AI coding agents (Claude Code, Cursor and more) into your development workflow." | ✅ [repo](https://github.com/paypal/AI-Toolkit) |
| Version | `1.2.0` in package.json and in all 3 plugin manifests; GitHub's latest tag is `v1.1.0` | ✅ `package.json`, `.claude-plugin/plugin.json`; tag from repo page |
| First commit | 2026-07-08 ("Initial commit", "Adding mcp json") | ✅ `git log` |
| Last commit | 2026-10-07, `fix: correct Venmo eligibility check API in docs and doctor guidance (#33)` | ✅ `git log` |
| Other notable commits | 2026-10-06 Cursor plugin support (#32); 2026-09-21 "remove paypal.ai references and add security policy" (#30); 2026-09-18 Codex plugin support, v1.1.0 (#29) | ✅ `git log` |
| Stars / forks / watchers | 27 / 9 / 2 (scraped 2026-10-11) | ✅ [repo page](https://github.com/paypal/AI-Toolkit) |
| Issues | 22 in total; #34 is the only open bug | ✅ [issues](https://github.com/paypal/AI-Toolkit/issues?q=is%3Aissue) |
| License | Apache-2.0 | ✅ `LICENSE` |
| Total files | 46 (Markdown, JSON and one SVG; **no executable code**) | ✅ `find` |

**Supported hosts:** Claude Code (`/plugin install paypal@claude-plugins-official`), OpenAI Codex (`codex plugin marketplace add paypal/AI-Toolkit`) and Cursor (`cursor-agent plugin marketplace add …`). ✅ README

**Components:**
- **MCP config** (`.mcp.json`): `"paypal-sandbox": {"type":"sse","url":"https://mcp.sandbox.paypal.com/sse","headers":{"Authorization":"Bearer ${PAYPAL_SANDBOX_ACCESS_TOKEN}"}}`. Sandbox only. ✅
- **Skills:**
  - `paypal-best-practices`: 17 reference files. They cover checkout, v6 SDK, expanded checkout, Venmo, BNPL, subscriptions, disputes-refunds, payouts, invoicing, auth, webhooks, Fastlane (PayPal v5, v6 and Braintree variants), 3DS, agentic-commerce and mcp-tools.
  - `paypal-routing`: an intent router. It also tells the agent to WebFetch `raw.githubusercontent.com/paypal/ruleshub/...` snippets as "authoritative". ✅
- **Commands:** `/paypal:doctor`, `/paypal:explain-error`, `/paypal:sandbox`, `/paypal:setup`, `/paypal:test-accounts`. ✅
- **Hook:** a `PreToolUse` prompt hook on Write and Edit that reminds the agent which SDK version is in use (v5 or v6). It is "informational only, never blocks". ✅ `hooks/hooks.json`

**Developer pain visible in the files:**
- **Static token.** You paste an access token by hand. "Tokens expire in up to 8 hours", and you run `/paypal:setup refresh` when you get a 401. ✅ README. Feature request #28 asked for `headersHelper` so tokens refresh without a restart; it is closed as of 2026-09-29. ✅ [#28](https://github.com/paypal/AI-Toolkit/issues/28)
- **Documented failure modes:** "`SSE error: Header has invalid value`" (newline in the token) and the hosted gateway rate-limiting reconnects with "`HTTP 429` … wait 1–2 minutes". ✅ `commands/setup.md`
- **Tool count.** `setup.md` gives "`[✓] Sandbox MCP — connected (31 tools)`" as its example output. ✅ (example string; ⚠ inference: the hosted sandbox exposes roughly 31 tools, fewer than the agent-toolkit's 46)
- **The reference docs disagree with each other.** `mcp-tools.md` lists Orders as only `create_order, pay_order` and says "7 invoice tools", which is vaguer than the agent-toolkit. It also documents the remote-only commerce tools `search_product`, `create_cart`, `checkout_cart`, which need the header `x-feature-flags: commerce:true`. ✅ `skills/.../mcp-tools.md`
- **Disputes guidance.** The skill tells the agent to "Never automatically accept a dispute claim without review", while the agent-toolkit ships `accept_dispute_claim`. ✅ `disputes-refunds.md`

**Issues list (developer pain).** Most are repo housekeeping filed by a DevRel contributor: templates, Husky, labels, releases. ✅ [issues](https://github.com/paypal/AI-Toolkit/issues?q=is%3Aissue) The meaningful ones:
- #34 "Sandbox MCP: every tool returns PAYPAL_API_SETUP_ERROR 'Unsupported cache mode: default'". **Open since 2026-10-08.** It started around 07:15 UTC. `list_invoices`, `list_transactions`, `list_disputes`, `list_subscription_plans` and `list_products` all fail, while the same token returns 200 from `api-m.sandbox.paypal.com`. The reporter is a hackathon entrant ("Stood") who switched to a REST "witness" script. ✅ [#34](https://github.com/paypal/AI-Toolkit/issues/34)
- #28 "[FEATURE] Replace the static PAYPAL_SANDBOX_ACCESS_TOKEN header with headersHelper so tokens refresh without a restart" (closed). ✅
- #10 "README: 9 hour token expiration" (closed). ✅
- #25 "[BUG] Installation update?" (closed). ✅

### 1.2 `paypal/agent-toolkit`: the embeddable SDK (cloned at `a3aa963`)

| Attribute | Value | Src |
|---|---|---|
| Packages | `@paypal/agent-toolkit` (npm) and `paypal-agent-toolkit` (PyPI); both `1.11.0` | ✅ `typescript/package.json`, `python/pyproject.toml` |
| Last commit | 2026-09-01, `chore: version bump to v1.11.0`. On 2026-08-28 the auto-send was removed from `create_invoice`. On 2026-08-20 invoicing tools were added: search, recurring, update, conditional, record. | ✅ `git log` |
| Version churn | v1.12.0 was published on 2026-08-07, then "Bumping down the version due to failed builds (#90)" to 1.9.0 on 2026-08-10 | ✅ `git log` |
| Stars / forks / watchers | 196 / 118 / 14 | ✅ [repo](https://github.com/paypal/agent-toolkit) |
| PRs | 17 open, 67 closed | ✅ [pulls](https://github.com/paypal/agent-toolkit/pulls) |
| TS subpath exports | `./ai-sdk`, `./mcp`, `./langchain`, `./openai`, `./bedrock` | ✅ package.json |
| Python modules | `openai`, `langchain`, `crewai`, `bedrock` | ✅ tree |
| Key deps | TS: `ai ^4.0.23` (the code uses `LanguageModelV1`, the AI SDK v4 type), `openai 4.86.1`, `@langchain/core 0.3.6`, `@modelcontextprotocol/sdk ^1.6.1`, `@paypal/paypal-server-sdk ^1.0.0`. Python: `openai-agents==0.0.2`, `langchain==0.3.23`, `crewai==0.76.2`, `crewai-tools==0.13.2`, `boto3==1.39.11`. | ✅ package.json, requirements.txt |
| Local MCP | `npx -y @paypal/mcp --tools=all` with `PAYPAL_ACCESS_TOKEN` and `PAYPAL_ENVIRONMENT=SANDBOX` | ✅ [MCP quickstart](https://developer.paypal.com/ai-tools/mcp-server.md) |

**Full tool list.** These are the exact `method` names from `typescript/src/shared/tools.ts` (46 in TS). ✅
- **Invoices (20):** `create_invoice`, `create_recurring_series`, `activate_recurring_series`, `get_recurring_series`, `cancel_recurring_series`, `delete_recurring_series`, `list_invoices`, `get_invoice`, `send_invoice`, `send_invoice_reminder`, `cancel_sent_invoice`, `delete_invoice`, `setup_invoice_auto_reminders`, `update_invoice_auto_reminder`, `search_invoicing`, `update_invoicing`, `cancel_invoice_auto_reminder`, `generate_invoice_qr_code`, `generate_invoice_number`, `record_payment_for_invoice`, `record_refund_for_invoice`, `create_conditional_rules_for_invoice`. Despite the "(20)" label, that list has 22 names, so the 46 total counts every name.
- **Catalog:** `create_product`, `list_products`, `update_product`, `show_product_details`
- **Subscriptions:** `create_subscription_plan`, `list_subscription_plans`, `show_subscription_plan_details`, `update_plan`, `create_subscription`, `show_subscription_details`, `update_subscription`, `cancel_subscription`
- **Shipment:** `create_shipment_tracking`, `get_shipment_tracking`, `update_shipment_tracking`
- **Orders and payments:** `create_order`, `get_order`, `pay_order`, `create_refund`, `get_refund`
- **Disputes:** `list_disputes`, `get_dispute`, `accept_dispute_claim`
- **Reporting:** `list_transactions`, `get_merchant_insights`

The Python `tools.py` has 43 methods. It uses `get_order_details` where TS uses `get_order`, and it lacks `update_product`, `update_plan`, `create_refund` and `get_refund`. ✅

**REST endpoints the tools hit** (from `functions.ts`): ✅
- Invoicing: `/v2/invoicing/invoices` (plus `/send`, `/remind`, `/cancel`, `/payments`, `/refunds`, `/generate-qr-code`, `/conditional-rules`, `/cancel-reminders`), `/v2/invoicing/recurring-invoices`, `/v2/invoicing/search-invoices`, `/v2/invoicing/setup-reminders`
- Catalog and billing: `/v1/catalogs/products`, `/v1/billing/plans`, `/v1/billing/subscriptions`
- Orders and payments: `/v2/checkout/orders` (plus `/capture`), `/v2/payments/captures/{id}/refund`, `/v2/payments/refunds/{id}`
- Tracking: `/v1/shipping/trackers-batch`, `/v1/shipping/trackers`
- Disputes and reporting: `/v1/customer/disputes` (plus `/accept-claim`), `/v1/reporting/transactions`
- **`/v1/merchant/insights`**: an insights endpoint that I found no public REST reference for (⚠ inference: undocumented or internal surface).

**Configuration** (`configuration.ts`):
- `actions: {product: {action: bool}}` gates which tools are exposed.
- `context: { merchant_id, sandbox, access_token, request_id, tenant_context, debug }`.
- `request_id` is sent as `PayPal-Request-Id`, and `tenant_context` as the `PayPal-Tenant-Context` header.
- `merchant_id` is only **logged**. It is never sent as `PayPal-Auth-Assertion`. ✅ `client.ts` lines 113–127, `functions.ts:356`

**Bugs, smells and TODO-level gaps I confirmed by reading the code:** ✅
- `create_order` always sends `intent: 'CAPTURE'` (`payloadUtils.ts:197`). There is no AUTHORIZE path.
- `pay_order` is described as "Process payment for an authorized order", but it POSTs to `/v2/checkout/orders/{id}/capture` with an empty body.
- The sandbox base URL is `https://api.sandbox.paypal.com`, not `api-m` (`client.ts:50`). This is tracked in issue #43 (opened 2025-06-04) and PR #99 (open).
- `PayPal-Request-Id` comes from the client context, so it is the same value for every call, or absent. Issue #98: "nothing ever sets it, so create_order and capture_order have no idempotency". The fix is in PR #108 (open).
- `PayPalWorkflows` (ai-sdk) only offers `generateOrder`, `getDisputeDetails` and similar multi-step demos, built on the AI SDK v4 `generateText`/`generateObject` API.
- The Python OpenAI example uses `client.beta.assistants.create` (the Assistants API). Issue #93 says that API was "retired Aug 26".
- The TypeScript and Python changelogs stop at 2025-04 and 2025-07. ✅ `CHANGELOG.md`

**Open issues (developer pain, quoted titles):** ✅ [issues](https://github.com/paypal/agent-toolkit/issues?q=is%3Aissue)
- #105 "Host spend policy before orders/invoices tools (agenticPay pattern)?" (2026-09-18)
- #104 "Optional host-side ACTION attestation for mutating pay tools" (2026-09-18)
- #98 "PayPal-Request-Id is set per client, not per call — and nothing ever sets it, so create_order and capture_order have no idempotency (client.ts:122)" (2026-09-04)
- #96 "@paypal/mcp declares '@paypal/agent-toolkit': 'latest', so the tool set and security behavior users get changes without notice" (2026-08-29)
- #95 "paypal-agent-toolkit ships no human gate or spend bound for order capture, and the official LangChain and CrewAI examples enable capture" (2026-08-29)
- #93 "python examples use the Assistants API, retired Aug 26" (2026-08-16)
- #82 "pay_order calls PayPal's capture API directly — no confirmation step, no post-execution record" (2026-07-17)
- #44 "Model tried to call unavailable tool 'list_orders' when using Sandbox environment" (closed)
- #43 "The API domain should be api-m.(sandbox.)paypal.com instead of api.(sandbox.)paypal.com"
- #40 "create_invoice tool issues, mcp"
- Several spam issues ("Cash", "Fraud", "TDANINJA04") suggest light triage. ⚠ inference

**Open PRs, which show demand for missing tools:** ✅ [pulls](https://github.com/paypal/agent-toolkit/pulls)
- #107 "Add Payouts tools (Python and TypeScript)" (2026-10-04)
- #78 "Feature/paymentlinks" (2025-12-02)
- #51 "Add agentic tools for Usage Based Billing" (2025-06-21)
- #110 "Fix create_order totals to match serialized amounts and unit taxes"
- #109 "Fix accept_dispute_claim validating note with the dispute ID pattern"
- #101 "bump langchain and crewai-tools to patch disclosed CVEs"
- #54 "Add Zero-Trust Handshake …"

### 1.3 Official docs: agent toolkit, MCP and tools reference

**docs.paypal.ai no longer exists as a separate site.** `docs.paypal.ai/llms.txt` redirects to `developer.paypal.com/docsai/llms.txt`, which returns 404. Both AI-Toolkit (#30, 2026-09-21) and ruleshub (2026-09-22) replaced their `docs.paypal.ai` links with `developer.paypal.com`. ✅ (redirect observed; [ruleshub commit](https://github.com/paypal/ruleshub) log) The AI docs now live under `developer.paypal.com/ai-tools/*`. ✅ [developer-resources llms.txt](https://developer.paypal.com/developer-resources/llms.txt)

**Agent toolkit quickstart** ([/ai-tools/toolkit](https://developer.paypal.com/ai-tools/toolkit.md)): ✅
- Frameworks: Amazon Bedrock, CrewAI, LangChain, MCP, OpenAI Agents SDK and Vercel AI SDK. Python 3.11+ or Node 18+.
- Sandbox is enabled with `context: { sandbox: true }`.
- The page's env var names are inconsistent (`PAYPAL_SECRET` vs `PAYPAL_CLIENT_SECRET`).

**MCP server quickstart** ([/ai-tools/mcp-server](https://developer.paypal.com/ai-tools/mcp-server.md)): ✅
- **Local:** `npx -y @paypal/mcp --tools=all`, env `PAYPAL_ACCESS_TOKEN` and `PAYPAL_ENVIRONMENT` (or `--access-token`).
- **Remote endpoints:**

  | Environment | Base URL | SSE | Streamable HTTP |
  |---|---|---|---|
  | Sandbox | `https://mcp.sandbox.paypal.com` | `/sse` | `/http` |
  | Production | `https://mcp.paypal.com` | `/sse` | `/http` |

  The older "limited release" page lists production streamable HTTP as `/mcp`, so the docs are inconsistent. ✅ [/limited-release/agents](https://developer.paypal.com/limited-release/agents.md)
- **Auth, two modes:** (a) a bearer token header, `--header "Authorization: Bearer <auth_header>"`, built from client credentials; or (b) `mcp-remote` with no header, which redirects you to a **PayPal login and consent** page. Credentials are cached in `~/.mcp-auth`.
- The docs say the full tool catalog "is available in both local and remote". The limited-release page said, by contrast, "Remote MCP server currently offers the following 2 tools with more coming soon". ✅

**Agent tools reference** ([/ai-tools/agent-tools](https://developer.paypal.com/ai-tools/agent-tools.md)): ✅
- **Catalog:** `create_product`, `list_product`, `show_product_details`
- **Disputes:** `list_disputes`, `get_dispute`, `accept_dispute_claim`
- **Invoices:** `create_invoice`, `list_invoices`, `get_invoice`, `send_invoice`, `send_invoice_reminder`, `cancel_sent_invoice`, `generate_invoice_qr_code`
- **Payments:** `create_order`, `create_refund`, `get_order`, `get_refund`, `pay_order`
- **Reporting:** `get_merchant_insights` (`insight_type` ORDERS or SALES; interval DAILY to YEARLY), `list_transaction`
- **Shipment:** `create_shipment_tracking`, `get_shipment_tracking`, `update_shipment_tracking`
- **Subscriptions:** `cancel_subscription`, `create_subscription`, `create_subscription_plan`, `list_subscription_plans`, `show_subscription_details`, `show_subscription_plan_details`, `update_subscription`
- **Remote-only commerce tools:** `search_product`, `create_cart`, `checkout_cart`. These are "for gift cards only for now". They need `x-feature-flags: commerce:true`, and the doc example uses **production** `https://mcp.paypal.com/sse`.

The reference **lags the code**. It does not list the 15 newer invoicing and recurring tools added in v1.10 to v1.11. ⚠ inference from the diff against tools.ts

**LLM integration guide** ([/ai-tools/build-with-llm](https://developer.paypal.com/ai-tools/build-with-llm.md)): ✅
- Anthropic Messages API `mcp_servers` with `authorization_token` (beta header `mcp-client-2025-04-04`, model `claude-sonnet-4-20250514`).
- OpenAI Responses API `tools: [{type:"mcp", server_url:"https://mcp.paypal.com/sse", require_approval:"never", headers:{Authorization:…}}]`.
- **Every example points at production `api-m.paypal.com` and `mcp.paypal.com`.** For the hackathon, substitute the sandbox URLs.

**Is there a separate MCP server repo?** The MCP server ships as the npm package `@paypal/mcp`, which depends on `@paypal/agent-toolkit` at `"latest"` (✅ issue [#96](https://github.com/paypal/agent-toolkit/issues/96)). The MCP implementation itself is in `typescript/src/modelcontextprotocol/` of agent-toolkit. It subclasses `McpServer`, registers the filtered tools and returns `String(result)` as text, with no `structuredContent`. ✅ code. I did not find a standalone `paypal/paypal-mcp-server` repo; gh API access was blocked, so I could not check it directly. ❌

---

## 2. Agentic commerce products and announcements, 2025–2026

| Date | Item | What it is | Hackathon availability | Src |
|---|---|---|---|---|
| 2025-04 | Agent toolkit 1.0 (Python), then MCP | `paypal-agent-toolkit` 1.0.0 on 2025-04-18 | ✅ open, sandbox | ✅ [python CHANGELOG](https://github.com/paypal/agent-toolkit/blob/main/python/CHANGELOG.md) |
| 2025-05-14 | Perplexity × PayPal | In-chat shopping checkout | Consumer surface only | ⚠️ [CNBC via NBC](https://www.nbcmiami.com/news/business/money-report/perplexity-partners-with-paypal-for-in-chat-shopping-as-ai-race-heats-up/3614235/) |
| 2025-09-17 | Google × PayPal multiyear partnership | Agentic commerce plus Google Cloud | Enterprise | ⚠️ [Google Cloud press](https://www.googlecloudpresscorner.com/2025-09-17-Google-and-PayPal-Forge-Multiyear-Partnership-to-Revolutionize-Commerce) |
| 2025-09-27 | JS SDK v6 "available now" | Modular, iframe isolation, PCI DSS v4 | ✅ open, sandbox | ✅ [blog](https://developer.paypal.com/community/blog/paypal-js-sdk-v6/) |
| 2025-10-27 | Mastercard × PayPal | Mastercard **Agent Pay** built into the PayPal wallet; PayPal pilots the "Mastercard Agent Pay Acceptance Framework"; no dates given | Announced only | ✅ [newsroom](https://newsroom.paypal-corp.com/2025-10-27-Mastercard-and-PayPal-Join-Forces-To-Accelerate-Secure-Global-Agentic-Commerce) |
| 2025-10-28 | **Agentic Commerce Services** | **Agent Ready** ("early 2026"), **Store Sync** (sign-up open, enrollment "soon"), catalog and order management. Partners: Wix, Cymbio, Commerce (BigCommerce/Feedonomics), Shopware. Surfaces: Perplexity, PayPal app shopping agent. Merchant stays merchant of record. | Access form | ✅ [newsroom](https://newsroom.paypal-corp.com/2025-10-28-PayPal-Launches-Agentic-Commerce-Services-to-Power-AI-Driven-Shopping) |
| 2025-10-28 | **OpenAI × PayPal** | PayPal adopts **ACP**; PayPal wallet in Instant Checkout; merchant catalogs in ChatGPT "in 2026" through PayPal's ACP server; "delegated payments API" for card processing | Merchant sign-up | ✅ [newsroom](https://newsroom.paypal-corp.com/2025-10-28-OpenAI-and-PayPal-Team-Up-to-Power-Instant-Checkout-and-Agentic-Commerce-in-ChatGPT) |
| 2026-01-11 | **Google UCP** | PayPal endorses the Universal Commerce Protocol; PayPal "will soon be available" in Google's UCP checkout. **AP2 is not named.** | Announced | ✅ [newsroom PDF](https://s205.q4cdn.com/875401827/files/doc_news/From-Search-to-Checkout-PayPal-Supports-Trusted-AI-Checkout-with-Google-2026.pdf) |
| 2026 (docs live) | **Agent Ready docs** | ACP for ChatGPT via Braintree delegated tokens; UCP for Google AI Mode and Gemini via the Google Pay handler on Braintree | Braintree sandbox (see §2.1) | ✅ [overview](https://developer.paypal.com/agent-ready/overview.md) |
| 2026-05 | Anthropic × PayPal | "AI Fluency for Small Business"; "Claude for Small Business" plugin for invoicing and refunds, "always requiring human approval for financial actions" | Consumer/SMB | ⚠️ [CrowdfundInsider](https://www.crowdfundinsider.com/2026/05/279847-paypal-partners-with-anthropic-to-leverage-ai-capabilities-after-announcing-layoffs/) |
| 2026-06-02 | Hey Savi × PayPal (UK) | "UK's first agentic commerce experience"; Debenhams Group is the first adopter | Enterprise | ⚠️ (newsroom title via [AgentLedger](https://useagentledger.xyz/blog/agentic-commerce-news/)) |
| 2026-07 | AI-Toolkit plugin | Claude Code plugin; Codex added 2026-09-18, Cursor 2026-10-06 | ✅ open | ✅ git log |
| 2026-08-10 | Ai4 2026 keynote | "Merchant AI Integration Agent" (upgrades and certifies integrations, runs on merchant infrastructure); "one-tap purchasing" agentic checkout launched earlier in 2026; **Know Your Agent (KYA)** concept | Announced | ✅ [newsroom](https://newsroom.paypal-corp.com/2026-08-10-PayPal-Takes-Center-Stage-at-Ai4-2026) |
| 2026-09-16 | **WebMCP** | Support for WebMCP through the **JS SDK**, for Store Sync merchants only ("limited to Store Sync customers today"). The agent searches, builds the cart and starts checkout; the buyer approves inside PayPal. Benchmark: about 4.6× less inference cost, about 2× faster, and 3 tool calls instead of 30+ UI steps. | **Not available**; ask your account manager | ✅ [blog](https://developer.paypal.com/community/blog/WebMCP_PayPal_Agent_Ready) |
| 2026-09-24 | Meta Muse × PayPal | PayPal checkout inside Meta's Muse agent (launched 2026-09-08) | Consumer | ⚠️ [The Paypers](https://thepaypers.com/payments/news/paypal-partners-with-meta-to-bring-checkout-to-muse-ai-agent) |
| 2026-09-30 | Hackathon announced | No tracks; requirement: "meaningfully use both PayPal and AI"; there is an honorable mention for **"Best Use of Agentic Commerce"** | n/a | ✅ [blog](https://developer.paypal.com/community/blog/PayPal_AI_Hackathon) |

**Not verified:**
- A PayPal × Visa Intelligent Commerce program. ❌
- PYUSD-specific agent-payment APIs. ❌ The only claim I found is a secondary blog with no primary citations ([blockeden](https://blockeden.xyz/blog/2026/04/11/paypal-openai-agent-checkout-protocol-pyusd-agentic-commerce/)) ⚠️.
- PayPal World and Venmo agent features. ❌
- Whether "PayPal checkout in ChatGPT" is live today. Press from 2025-10 says "launch targeted for 2026" ⚠️ [Retail Systems](https://retail-systems.com/rs/ChatGPT_Adds_PayPal_Checkout_As_AI_Shopping_Expands.php). The ACP integration doc still lists `paypal_wallet` and `venmo_wallet` as "coming soon" ✅ [ACP doc](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md).

### 2.1 What the Agent Ready docs actually specify

**ACP for ChatGPT** ✅ [doc](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md):
- You build a ChatGPT App (Apps SDK) and an MCP server that exposes `complete_checkout`.
- The widget calls `window.openai.requestCheckout()` with `payment_provider: {provider:"braintree", merchant_id, supported_payment_methods:["card","applepay","googlepay"]}`, plus `payment_mode: "test"|"live"`.
- `payment_data.token` is a Braintree single-use nonce (e.g. `tokencc_bf_…`). You charge it with `transaction.sale` or GraphQL `chargePaymentMethod`.
- **Allowance validation:** `merchant_id`, `max_amount`, `currency` and `expires_at`, each with a specific error code (e.g. `915266` when the amount exceeds the maximum).
- **AI-initiated transactions are tagged** with `facilitator_details.oauth_application_name = "ChatGPT"` and are searchable through GraphQL `facilitatorOAuthApplicationClientId`.
- You test it in ChatGPT developer mode, with the MCP server on a public URL.

**UCP for Google** ✅ [doc](https://developer.paypal.com/agent-ready/universal-commerce-protocol.md):
- Google tokenizes server-side; your `/checkout-session/{id}/complete` receives `credential.token`, a JSON string containing `androidPayCards[0].nonce`.
- **Needs UCP merchant registration with Google.** Single-use credentials expire after 3 hours.

**Store Sync** ✅ [overview](https://developer.paypal.com/store-sync/overview.md), [integrate](https://developer.paypal.com/store-sync/integrate.md):
- Scope: **US, USD, physical goods only**; no digital goods or subscriptions.
- You implement `POST /merchant-cart`, `PUT /merchant-cart/{id}` and `POST /merchant-cart/{id}/checkout`.
- PayPal calls them with JWTs, which you verify against `https://www.paypal.ai/.well-known/jwks.json`.
- The PayPal-side paths shown are `/commerce/carts`, `/commerce/carts/{id}/complete_payment` and `/api/agentic-commerce/v1/createcart|completecheckout`.
- No sandbox is mentioned, and access goes through the access form.

**Conflicting surface.** ruleshub's enterprise-checkout snippet instead documents a "Cart API" at `POST/GET/PATCH /v2/cart` on `api-m.sandbox.paypal.com` ✅ [ruleshub snippet](https://github.com/paypal/ruleshub/blob/main/paypal-checkout/enterprise-checkout/snippets/python/agentic-commerce.md). I could not find `/v2/cart` in the developer docs, and whether it works for regular sandbox apps is ❌ unverified. (⚠ inference: it is worth one curl to check.)

**Availability matrix for a hackathon team** (⚠ inference, based on the sources above):

| Capability | Usable by a hackathon team in sandbox? |
|---|---|
| Agent toolkit (all frameworks) and local `@paypal/mcp` | **Yes** |
| Hosted sandbox MCP (`mcp.sandbox.paypal.com`) | **Yes, but broken since Oct 8** (#34) |
| Remote commerce tools (`search_product`/`create_cart`/`checkout_cart`) | Gift cards only; documented against production; sandbox unknown ❌ |
| Agent Ready ACP | **Partly.** You can build a ChatGPT App plus Braintree sandbox with `payment_mode:"test"`, but real delegated tokens need OpenAI's ACP onboarding; the PayPal wallet is "coming soon" |
| Agent Ready UCP | No (needs Google UCP merchant registration) |
| Store Sync, WebMCP checkout | No (access form; WebMCP limited to Store Sync merchants) |
| Mastercard Agent Pay, KYA, Merchant AI Integration Agent | No (announced only) |

---

## 3. Core REST APIs: what works in sandbox

Base URL `https://api-m.sandbox.paypal.com`; OAuth `POST /v1/oauth2/token` (client_credentials). ✅ [sandbox repo](https://github.com/paypaldev/getting-started-with-paypal-sandbox)

### 3.1 Orders v2 and Payments v2
- **Intents and flow:** `intent` is CAPTURE or AUTHORIZE. Create with `POST /v2/checkout/orders`, then capture with `/v2/checkout/orders/{id}/capture` or authorize with `/authorize`. A later capture goes through `POST /v2/payments/authorizations/{id}/capture`. ✅ [AI-Toolkit checkout.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/checkout.md)
- **Auth windows:** a **29-day authorization period** with a **3-day honor period**.
  - **Reauthorization** is allowed after the honor period, within 29 days. Each one gives a new auth ID and restarts the honor period; you can reauthorize multiple times.
  - You can capture **up to 115% or +$75 USD** of the authorized amount, whichever is less.
  - Partial captures are supported; for PayPal-wallet auths they must be enabled on the account.
  - "Buyers and merchants cannot close accounts that have authorized but uncaptured payments."
  ✅ [auth-honor](https://developer.paypal.com/payment-methods/auth-honor.md)
- **Related guides:** void an authorization, extend an authorization, refund. ✅ [payments llms.txt](https://developer.paypal.com/payments/llms.txt) (`/checkout/void-authorized-payment`, `/checkout/extend-authorization`, `/checkout/refund-payment`)
- **Update before capture:** "Update order details: … amounts and details before capture". "Capture new totals without payer re-approval". ✅ (same index, `/expanded/update-order-details`, `/v5/checkout/show-order-updates`)
- **Negative testing:** send `PayPal-Mock-Response: {"mock_application_codes":"INSTRUMENT_DECLINED"}` on any sandbox call, or e.g. `DUPLICATE_INVOICE_ID`, which returns 422 with a `debug_id`. There is also an account-level **Negative Testing** toggle. ✅ [sandbox repo](https://github.com/paypaldev/getting-started-with-paypal-sandbox)

### 3.2 Vault: Payment Method Tokens v3
- **Endpoints:** `POST /v3/vault/setup-tokens` → buyer approves → `POST /v3/vault/payment-tokens` → `GET /v3/vault/payment-tokens?customer_id=…`.
- **Charging:** pass `payment_source.paypal.vault_id` in Orders v2. You can also charge "when [the payer] isn't present".
- **Setup:** sandbox is supported. Enable Vault under App Settings → Accept payments → Advanced options.
- **Live eligibility:** you need billing-agreement / reference-transaction approval.
- **Countries:** US, CA, EU/EEA, UK, AU, JP, SG, HK, CN.
✅ [save-without-purchase/paypal](https://developer.paypal.com/api/payment-tokens/save-without-purchase/paypal.md)

Docs exist for saving cards, PayPal and Venmo, both with purchase and without purchase (Venmo only with purchase in JS), across the JS SDK, iOS, Android and Orders API. ✅ [payments llms.txt](https://developer.paypal.com/payments/llms.txt) In JS SDK v6, vaulting needs a `clientToken`, not a `clientId`, and the save sessions are `createPayPalSavePaymentSession()` and `createCardFieldsSavePaymentSession()`. ✅ [AI-Toolkit js-sdk-v6.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/js-sdk-v6.md)

### 3.3 Subscriptions and billing plans
- **Flow:** product (`/v1/catalogs/products`) → plan (`/v1/billing/plans`, must be ACTIVE) → `/v1/billing/subscriptions`.
- **Lifecycle:** revise (upgrade or downgrade), suspend, cancel, up to 2 trial cycles. ✅ [subscriptions.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/subscriptions.md)
- **Doc topics:** delayed start, setup fee, pause/resume, quantity change, plan price change and payment-failure retry ("retries payments up to twice per billing cycle"). Pricing models: fixed, quantity, volume and tiered. ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)
- **Sandbox:** "auto-processes renewal cycles". Use the Webhooks Simulator for `BILLING.SUBSCRIPTION.PAYMENT.FAILED`. ✅ [test-accounts.md](https://github.com/paypal/AI-Toolkit/blob/main/commands/test-accounts.md)

### 3.4 Invoicing v2
- **Lifecycle:** draft → send → remind → cancel. Also record payment, record refund, QR code, next invoice number, search, recurring series, auto-reminders and **conditional rules** (early-payment discount, auto-cancel date). All are implemented in the agent-toolkit. ✅ `functions.ts`
- **Doc topics:** **templates**, a custom email domain for invoice emails, webhooks and test-and-go-live. ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)
- **Payment options:** partial payments, tips and custom charges are configurable. Payers can use PayPal, card, Venmo or ACH. ✅ [invoicing.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/invoicing.md)

### 3.5 Payouts
- **Create:** `POST /v1/payments/payouts` with `recipient_type` EMAIL, PHONE, PAYPAL_ID or **VENMO_HANDLE** (US/USD only).
- **Limits:** $20k per item; 400 POST requests per minute. "Access requires approval via the PayPal Developer Dashboard." ✅ [payouts.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/payouts.md)
- **Sandbox test values (✅ [payouts test-go-live](https://developer.paypal.com/api/payouts/test-go-live.md)):**
  - Put `items[0].note` = `ERRPYO005` to get INSUFFICIENT_FUNDS, `ERRPYO002` for SENDER_EMAIL_UNCONFIRMED, `ERRPYO040` for CIP_NOT_VERIFIED, and so on.
  - `GET /v1/payments/payouts/ERRPYOB002|003|004` returns PENDING, PROCESSING or DENIED batch states.
  - `POSPYO003` gives a 201 for a Venmo receiver.
  - Item-level failures include RECEIVER_UNREGISTERED, RISK_DECLINE and others.
  - "Webhook resources don't contain error objects", so you must GET the object to learn the failure reason.
- Unclaimed payouts return after 30 days. ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)

### 3.6 Disputes API: very simulatable in sandbox ✅ [disputes/test-go-live](https://developer.paypal.com/disputes/test-go-live.md)

**Sandbox-only "buyer and PayPal" endpoints** (each marked "You cannot use it … in the live environment"):

| Endpoint | What it does | Notes |
|---|---|---|
| `POST /v1/customer/disputes` | **Create** a dispute as the buyer | multipart; `PayPal-Auth-Assertion` JWT for the buyer |
| `POST /v2/customer-support/process-chargeback` | **Create** a chargeback | |
| `POST /v1/customer/disputes/{id}/change-reason` | Change the dispute reason | |
| `POST /v1/customer/disputes/{id}/accept-offer` | Buyer accepts a merchant offer | |
| `POST /v1/customer/disputes/{id}/deny-offer` | Buyer denies a merchant offer | |
| `POST /v1/customer/disputes/{id}/adjudicate` | PayPal settles in `BUYER_FAVOR` or seller favor | requires status `UNDER_REVIEW` |
| `POST /v1/customer/disputes/{id}/require-evidence` | Move `UNDER_REVIEW` to `WAITING_FOR_BUYER_RESPONSE` or `WAITING_FOR_SELLER_RESPONSE` | |

**Merchant actions:** `send-message`, `make-offer` (refund, refund with return, replacement), `provide-evidence` (multipart; `PROOF_OF_FULFILLMENT`, `PROOF_OF_REFUND`, `OTHER`), `accept-claim` (including partial or with return), `escalate`, `appeal` and `acknowledge-return-item`. Check the HATEOAS `links` and `allowed_response_options` first. ✅ [disputes-refunds.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/disputes-refunds.md)

**Simulation tricks:**
- **Appeals:** a buyer email containing `allowappeal` enables the appeal workflows; `noappeal` disables them.
- **Accelerated Response:** put `notes: "ACCELERATED_RESPONSE_ENABLED"` in `evidences`.
- **Escalation day by amount:** $5.00–5.99 escalates on day 5, $9.00–9.99 on day 9, and ≥ $11 on day 11.
- **Error simulation:** test values in the path or query (e.g. `/v1/customer/disputes/ERRDIS015`).
- **Duplicates:** a buyer cannot open a second dispute on the same transaction.

**Webhooks:** `CUSTOMER.DISPUTE.CREATED`, `.UPDATED` and `.RESOLVED` can all be triggered. "Wait a few minutes after creating the dispute for the actions to become available."

**Pain:** "Paypal Disputes API returns INVALID_EVIDENCE_FILE when posting file" ⚠️ [SO 78902643](https://stackoverflow.com/questions/78902643/paypal-disputes-api-returns-invalid-evidence-file-when-posting-file). Supported file types and sizes have their own page. ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)

### 3.7 Transaction Search / Reporting
`GET /v1/reporting/transactions`:
- "It takes a maximum of three hours for executed transactions to appear".
- Maximum range is 31 days; it covers the previous 3 years.
- Scope `…/services/reporting/search/read`; `page_size` up to 500.
✅ [Transaction Search v1 reference](https://developer.paypal.com/docs/api/transaction-search/v1/)

SFTP reports (settlement, disputes, fees and others) exist but are merchant-portal flows. ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)

### 3.8 Webhooks
- **Retries:** non-2xx responses are retried "up to 25 times over 3 days", then marked Failed, with manual resend from the dashboard. "Up to 10 webhook URLs … per app."
- **Verification:** either a local CRC32 and signature check, or the verify-signature endpoint. ✅ [webhooks overview](https://developer.paypal.com/api/webhooks/overview)
- **Simulator:** the Webhooks Simulator exists. Simulated events can't be signature-verified; "You can only verify recent webhooks your particular client-id has received". ⚠️ [SO 66856761](https://stackoverflow.com/questions/66856761/verifying-simulated-paypal-webhooks-signature-always-returns-failure)
- **Notable events:** `PAYMENT.CAPTURE.COMPLETED|DENIED|REFUNDED`, `BILLING.SUBSCRIPTION.ACTIVATED|PAYMENT.FAILED|CANCELLED|SUSPENDED`, `PAYMENT.SALE.COMPLETED` (renewals), `CUSTOMER.DISPUTE.CREATED|RESOLVED`. ✅ [webhooks.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/webhooks.md)

### 3.9 Payment Links and Buttons; Pay Later
- **Payment Links:** no-code from the dashboard, or programmatic `POST /v1/checkout/payment-resources` (`type:"BUY_NOW"`, `integration_mode:"LINK"`). ✅ [checkout.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/checkout.md) The API supports inventory, variants and taxes, plus QR sharing. ✅ [payments llms.txt](https://developer.paypal.com/payments/llms.txt)
- **Pay Later:** a v6 `<paypal-message>` component. Sandbox amounts: $30–1,500 for Pay in 4 and $199–10,000 for Pay Monthly. "Sandbox does not simulate installment billing." ✅ [test-accounts.md](https://github.com/paypal/AI-Toolkit/blob/main/commands/test-accounts.md)

### 3.10 Multiparty / platforms
- Up to **10 `purchase_units`** (sellers) per order, with `payment_instruction.platform_fees` and `disbursement_mode` INSTANT or DELAYED. Calls carry the `PayPal-Auth-Assertion` header and a BN code. ✅ [multiseller payments](https://developer.paypal.com/platforms/checkout/standard/customize/multiseller-payments.md)
- Guides exist for delayed disbursement and partner seller onboarding. ✅ [platforms llms.txt](https://developer.paypal.com/platforms/payments/llms.txt)
- The best-practices skill marks "PayPal Commerce Platform (multi-party marketplaces)" as **out of scope**. ✅ [SKILL.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/SKILL.md)
- Whether sandbox partner onboarding works without PayPal approval is ❌ unverified (⚠ inference: platform-fee features usually need partner enablement).

### 3.11 Shipment tracking, Log in with PayPal, Fastlane, Venmo, Braintree
- **Tracking:** `POST /v1/shipping/trackers-batch`, `GET /v1/shipping/trackers?transaction_id=`, and `/v1/shipping/trackers/{id}`. ✅ agent-toolkit `functions.ts` There is also tracking through Orders v2 (`/api/orders-v2/track-orders`). ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)
- **Log in with PayPal:** an Identity API on OpenID Connect, with doc pages for building the button, scopes and best practices. ✅ [revenue llms.txt](https://developer.paypal.com/revenue/llms.txt)
- **Fastlane:** sandbox buyer emails must contain `whitelistallblock`, and test cards are listed (e.g. Visa 4005 5192 0000 0004). There are three variants: v5, v6 and Braintree. ✅ [test-accounts.md](https://github.com/paypal/AI-Toolkit/blob/main/commands/test-accounts.md)
- **Venmo in sandbox:** "Sandbox testing of the desktop QR code is currently unavailable". US only; add `buyer-country=US`. ✅ [venmo/test](https://developer.paypal.com/venmo/test.md) "Venmo sandbox does not invoke the real Venmo app." ✅ [test-accounts.md](https://github.com/paypal/AI-Toolkit/blob/main/commands/test-accounts.md)
- **Braintree:** the GraphQL `chargePaymentMethod` and transaction search with `facilitatorOAuthApplicationClientId` are the agentic hooks. ✅ [ACP doc](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md)

### 3.12 JS SDK v6 (on the hackathon resource list)
- **Loading:** `https://www.sandbox.paypal.com/web-sdk/v6/core`, then `createInstance({clientId | clientToken, components:[…]})`.
- **Components:** `paypal-payments`, `venmo-payments`, `paypal-guest-payments`, `paypal-messages`, `card-fields`, `fastlane`, `googlepay-payments`, `applepay-payments`, `paypal-subscriptions`.
- **Eligibility:** explicit, via `findEligibleMethods()`.
- **Session types:** about 13, including `createPayPalSavePaymentSession` and `createPayPalSubscriptionPaymentSession`.
- **Presentation modes:** `auto`, `popup`, `modal`, `redirect`, `payment-handler` (experimental), `direct-app-switch`.
- **Known bug:** `session.start()` must get a **Promise, not a function** ("SdkInitError: .start() expects a Promise. Received 'function'").
✅ [js-sdk-v6.md](https://github.com/paypal/AI-Toolkit/blob/main/skills/paypal-best-practices/references/js-sdk-v6.md)

The Sept 2026 WebMCP support ships through the JS SDK, but it is limited to Store Sync merchants. ✅ [WebMCP blog](https://developer.paypal.com/community/blog/WebMCP_PayPal_Agent_Ready)

---

## 4. Developer pain signals (2025–2026)

| Theme | Evidence (title, URL) | Conf |
|---|---|---|
| Hosted MCP reliability | "Sandbox MCP: every tool returns PAYPAL_API_SETUP_ERROR 'Unsupported cache mode: default'" ([AI-Toolkit #34](https://github.com/paypal/AI-Toolkit/issues/34)) | ✅ |
| Token lifecycle | "Replace the static PAYPAL_SANDBOX_ACCESS_TOKEN header with headersHelper…" ([#28](https://github.com/paypal/AI-Toolkit/issues/28)); "README: 9 hour token expiration" ([#10](https://github.com/paypal/AI-Toolkit/issues/10)) | ✅ |
| Agent safety and guardrails | #95 no human gate or spend bound; #82 `pay_order` without confirmation; #104 action attestation; #105 host spend policy ([agent-toolkit issues](https://github.com/paypal/agent-toolkit/issues?q=is%3Aissue)) | ✅ |
| Idempotency | #98 `PayPal-Request-Id` never set per call ([link](https://github.com/paypal/agent-toolkit/issues/98)) | ✅ |
| Supply chain | #96 `@paypal/mcp` pins agent-toolkit to `latest`; PR #101 CVE bumps | ✅ |
| Stale examples | #93 Assistants API retired; AI SDK v4 types; `openai-agents==0.0.2` pin | ✅ |
| Wrong domain | #43 `api.` vs `api-m.` | ✅ |
| v6 SDK bugs | paypal-js: "[Bug] Web SDK v6 Card Fields have incorrect Tab order in Safari" (#1028); "[Doc/Bug?] Card Fields testing" (#1033); "[Bug] Inconsistency in the subscription flow depending on the user's login state" (#975); "[Bug] Error on submit credit card payment not logged by callbacks" (#596, 34 comments) ([paypal-js issues](https://github.com/paypal/paypal-js/issues)) | ✅ |
| v6 sandbox onApprove | SO unanswered: "integrating the PayPal JavaScript SDK v6 … critical issue in the Sandbox environment: the onApprove callback…" ([SO tag](https://stackoverflow.com/questions/tagged/paypal-sandbox?tab=Unanswered)) | ⚠️ |
| Webhooks | "PayPal Webhooks Not Received on Production Server (but working via ngrok…)" ([SO 79572615](https://stackoverflow.com/questions/79572615/paypal-webhooks-not-received-on-production-server-but-working-via-ngrok-and-web)); "PayPal sandbox webhook signature verification fails for an event but succeeds for another" ([SO tag](https://stackoverflow.com/questions/tagged/paypal-rest-sdk?tab=Newest)); "PayPal webhook listener gets an HTTP 302 and gets retries" ([SO tag](https://stackoverflow.com/questions/tagged/paypal-webhooks?tab=Newest)) | ⚠️ |
| Vault | "PayPal Vaulting: billingToken is null in onApprove response" ([SO 79538649](https://stackoverflow.com/questions/79538649/paypal-vaulting-billingtoken-is-null-in-onapprove-response)) | ⚠️ |
| Disputes evidence | "Paypal Disputes API returns INVALID_EVIDENCE_FILE when posting file" ([SO 78902643](https://stackoverflow.com/questions/78902643/paypal-disputes-api-returns-invalid-evidence-file-when-posting-file)) | ⚠️ |
| Server SDK feedback channel | `paypal/PayPal-TypeScript-Server-SDK` shows **0 issues**, so the tracker is likely disabled ([issues](https://github.com/paypal/PayPal-TypeScript-Server-SDK/issues?q=is%3Aissue)) | ✅ (observed) |
| Sandbox webhook delay | "Webhook events in sandbox may be delayed; use the Webhooks Simulator" ([test-accounts.md](https://github.com/paypal/AI-Toolkit/blob/main/commands/test-accounts.md)) | ✅ |

---

## 5. Hackathon resource: `paypaldev/getting-started-with-paypal-sandbox`

- Created 2026-09-28; last merge 2026-10-01. It is one README plus one image. ✅ git log
- **What it covers:** the default Business and Personal accounts, which can't be deleted; Create Custom Account for custom balances and cards; multi-currency balances; the three URLs (`developer.paypal.com`, `www.sandbox.paypal.com`, `api-m.sandbox.paypal.com`).
- **Recommendations:** it recommends `@paypal/paypal-server-sdk` for automatic OAuth.
- **Negative testing:** a `PayPal-Mock-Response` example with `INSTRUMENT_DECLINED` and `DUPLICATE_INVOICE_ID`, and the account-level Negative Testing toggle, with the warning: "Turn **Negative Testing** back off … it's easy to forget and later looks like a broken integration."
- **What it does not cover:** disputes, payouts, vault, webhooks or AI.
✅ [repo](https://github.com/paypaldev/getting-started-with-paypal-sandbox)

---

## 6. Gaps: what PayPal's agent tooling does NOT do yet (the most valuable section)

Each gap is grounded in the code or docs above. "Toolkit" means agent-toolkit v1.11.0 plus `@paypal/mcp`. "Hosted" means `mcp.sandbox.paypal.com`.

1. **No authorize-then-capture for agents.** `create_order` hardcodes `intent:'CAPTURE'`, and there are no `authorize_order`, `capture_authorization`, `reauthorize` or `void` tools. Agents can't place a *hold* and settle only after a condition is met, even though Payments v2 supports 29-day auths, reauthorization and over-capture up to 115%. ✅ `payloadUtils.ts:197`, [auth-honor](https://developer.paypal.com/payment-methods/auth-honor.md)
2. **No spend policy, budget, approval gate or audit record.** There is no `max_amount`, allow-list or human-in-the-loop hook in the toolkit (issues #95, #82, #104 and #105 are all open). The only "allowance" concept PayPal ships is Braintree's ACP delegated token (`max_amount`, `expires_at`), and that is ChatGPT-only and Braintree-only. ✅
3. **No idempotency per tool call.** `PayPal-Request-Id` is a client-wide constant or absent (#98, with PR #108 open). An LLM that retries can double-create orders or refunds. ✅
4. **No Payouts tools** (PR #107 open), even though Payouts, including Venmo handles, is fully testable with sandbox test values. ✅
5. **No Vault / payment-method-token tools.** Agents can't save a PayPal, Venmo or card method and later charge it with the payer absent (`vault_id`), even though `/v3/vault/*` works in sandbox. ✅
6. **Disputes only support read and accept.** There is no `provide_evidence`, `make_offer`, `send_message`, `escalate`, `appeal` or `acknowledge_return_item`, and nothing exposes the sandbox simulators (`create dispute`, `adjudicate`, `require-evidence`). The only mutating dispute tool, `accept_dispute_claim`, is the one PayPal's own skill warns against automating. ✅
7. **No webhooks tools or event ingestion.** Nothing registers or verifies webhooks or turns events into agent triggers. Agents are pull-only; ⚠ inference: they have to poll Transaction Search, which lags up to 3 hours.
8. **No Payment Links, buttons or QR tools** (PR #78 open since 2025-12). Only invoice QR codes exist. ✅
9. **No multiparty or platform context.** `merchant_id` in the context is never sent as `PayPal-Auth-Assertion`, so a platform agent can't act on behalf of sellers or set `platform_fees`. ✅ `client.ts`
10. **No Pay Later, Fastlane, Apple Pay or Google Pay, and no buyer-side tools.** The toolkit is merchant-back-office only. Buyer-side agent checkout exists only as gift-card-only remote commerce tools behind a feature flag, plus gated ACP, UCP and Store Sync. ✅
11. **Broken or legacy plumbing.** It uses the `api.sandbox.paypal.com` domain (#43), AI SDK v4 types, `openai-agents==0.0.2` and Assistants API examples (#93), and MCP results come back as `String(result)` text with no `structuredContent` or output schemas. ✅
12. **Hosted MCP is fragile.** It uses static bearer tokens that expire after about 8 hours, a gateway 429 on reconnect, and the open #34 outage. The remote OAuth consent flow is documented with production `mcp.paypal.com` examples. ✅
13. **Agent identity (KYA) is a concept only.** There is no API, token format or "agent" field on Orders. The only machine-readable agent attribution is Braintree's `facilitator_details.oauth_application_name`. ✅ [Ai4](https://newsroom.paypal-corp.com/2026-08-10-PayPal-Takes-Center-Stage-at-Ai4-2026), [ACP doc](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md)
14. **The PayPal wallet in ACP is not shipped.** `paypal_wallet` and `venmo_wallet` are "coming soon"; ACP via Braintree supports only card, Apple Pay and Google Pay. ✅
15. **Docs and code disagree.** The tools reference lists about 30 tools while the code has 46. The local, remote and "2 tools" claims conflict. Store Sync cart paths contradict the ruleshub `/v2/cart`. AI docs moved from docs.paypal.ai to developer.paypal.com in Sept 2026. ✅

---

## 7. Hidden insights and underused capabilities a hackathon team could exploit

Each item is grounded in a source above. The idea attached to each one is ⚠ inference.

1. **Sandbox dispute *factory*.** `POST /v1/customer/disputes` with the buyer's `PayPal-Auth-Assertion`, plus `/process-chargeback`, `/change-reason`, `/require-evidence` and `/adjudicate`, lets you script an entire dispute lifecycle, buyer side included, then drive it with an AI "dispute defense agent" that compiles evidence (tracking, refund proof, chat logs) and calls `provide-evidence`. Escalation can be compressed with $5, $9 or $11 amounts, and `allowappeal` accounts unlock the appeal flow. It makes a live, deterministic demo, and no agent tool covers it today. ✅ [disputes test-go-live](https://developer.paypal.com/disputes/test-go-live.md)
2. **Authorization holds as an agent spending primitive.** Authorize with a 29-day hold, reauthorize on schedule, capture up to 115% or +$75 and partially capture. Together these make a native escrow and budget envelope an agent can operate under ("hold $X, release only on verified delivery"). It also fills gaps 1 and 2. ✅ [auth-honor](https://developer.paypal.com/payment-methods/auth-honor.md)
3. **`PayPal-Mock-Response` for chaos-testing agents.** Inject `INSTRUMENT_DECLINED`, `DUPLICATE_INVOICE_ID` and similar on any sandbox call to show the agent recovering: it switches funding, avoids double charges and explains to the user. Judges rarely see failure-path demos. ✅ [sandbox repo](https://github.com/paypaldev/getting-started-with-paypal-sandbox)
4. **Payouts test values for a deterministic payout agent.** `ERRPYO0xx` notes and `ERRPYOB0xx` batch IDs reproduce about 50 failure modes (RECEIVER_UNREGISTERED, RISK_DECLINE, CIP_NOT_VERIFIED…). Combined with `VENMO_HANDLE`, a contractor-payout or bounty-payout agent can show triage of every failure branch. ✅ [payouts test-go-live](https://developer.paypal.com/api/payouts/test-go-live.md)
5. **The vault is the missing agent primitive.** `/v3/vault/setup-tokens` → `payment-tokens` → Orders with `vault_id` when the payer isn't present. Pair it with your own policy layer (caps, merchant allow-list, approvals) to build a real delegated-spend agent in sandbox, without waiting for ACP's PayPal wallet. ✅ [vault doc](https://developer.paypal.com/api/payment-tokens/save-without-purchase/paypal.md)
6. **Build the guardrail layer PayPal's own issue tracker is asking for.** Issues #95, #98, #104 and #105 describe the exact spec: per-call `PayPal-Request-Id`, a spend bound, action attestation and a post-execution record. A "policy-wrapped PayPal MCP" proxy maps directly onto the "Best Use of PayPal + AI" story. ✅
7. **Invoicing is the deepest agent surface.** It has 22 tools, including recurring series, conditional rules (early-payment discount, auto-cancel), auto-reminders, record payment/refund and search. An AR/collections agent can use far more of PayPal than a checkout bot can. ✅ `tools.ts`
8. **`get_merchant_insights`** (`/v1/merchant/insights`, ORDERS or SALES, DAILY to YEARLY) is a little-known analytics endpoint already wrapped as a tool. Use it for an AI CFO or forecasting feature. ✅ [agent-tools](https://developer.paypal.com/ai-tools/agent-tools.md)
9. **Braintree sandbox plus ChatGPT developer mode** reproduces the ACP Instant Checkout flow end to end (`requestCheckout` → `complete_checkout` → `transaction.sale` with `payment_mode:"test"`). It is the most "agentic commerce" thing a team can actually demo, and it carries `facilitator_details` attribution. Confirm token issuance in test mode early, because it's ❌ unverified. ✅ [ACP doc](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md)
10. **WebMCP is announced but closed.** PayPal published only a benchmark (4.6× cheaper, 2× faster, 3 vs 30+ steps) and a video. A team can build its *own* WebMCP-style storefront tools (`search`, `cart`, `start_checkout`) on JS SDK v6 that hand off to PayPal approval. That is a credible preview of where PayPal is going, and nobody can get the official version yet. ✅ [WebMCP blog](https://developer.paypal.com/community/blog/WebMCP_PayPal_Agent_Ready)
11. **Webhooks as agent triggers.** You get up to 10 URLs per app, 25 retries over 3 days, and dispute, subscription and capture events. An event-driven agent (e.g. on `BILLING.SUBSCRIPTION.PAYMENT.FAILED`, run a dunning conversation, then `send_invoice`) fills gap 7. Use real sandbox events, not the simulator, if you need signature verification. ✅ [webhooks overview](https://developer.paypal.com/api/webhooks/overview)
12. **Shipment tracking feeds dispute defense and fund release.** The tracking tools already exist (`create_shipment_tracking`), and the disputes docs use tracking as `PROOF_OF_FULFILLMENT`. ✅
13. **Multi-seller orders with `platform_fees`** (up to 10 purchase units, INSTANT or DELAYED disbursement) allow an AI marketplace or concierge that splits a cart across sellers. It is unsupported by any agent tool and out of scope for PayPal's own skill, so it's differentiated territory. Verify sandbox partner enablement first. ✅ [multiseller](https://developer.paypal.com/platforms/checkout/standard/customize/multiseller-payments.md)
14. **The remote "commerce" MCP tools** (`search_product`, `create_cart`, `checkout_cart` with `x-feature-flags: commerce:true`) are a hidden buyer-side agent path. They are gift cards only and documented against production, so probe the sandbox early. ✅ [agent-tools](https://developer.paypal.com/ai-tools/agent-tools.md)
15. **Be resilient to the MCP outage.** Ship a "dual path" (hosted MCP, then local `@paypal/mcp`, then direct REST) and show it in the demo. The #34 reporter's REST "witness" pattern is a good template. ✅ [#34](https://github.com/paypal/AI-Toolkit/issues/34)

---

## 8. Source index (primary)

**Repos:**
- [paypal/AI-Toolkit](https://github.com/paypal/AI-Toolkit), cloned at `5dce83d`, 2026-10-07
- [paypal/agent-toolkit](https://github.com/paypal/agent-toolkit), cloned at `a3aa963`, 2026-09-01
- [paypal/ruleshub](https://github.com/paypal/ruleshub), at `524b790`, 2026-09-28
- [paypaldev/getting-started-with-paypal-sandbox](https://github.com/paypaldev/getting-started-with-paypal-sandbox), at `e29cb63`, 2026-10-01
- Local clones are in `/home/claude/research/repos/`.

**Docs:**
- [llms.txt root](https://developer.paypal.com/llms.txt)
- AI tools: [/ai-tools/get-started](https://developer.paypal.com/ai-tools/get-started.md), [/ai-tools/toolkit](https://developer.paypal.com/ai-tools/toolkit.md), [/ai-tools/mcp-server](https://developer.paypal.com/ai-tools/mcp-server.md), [/ai-tools/agent-tools](https://developer.paypal.com/ai-tools/agent-tools.md), [/ai-tools/build-with-llm](https://developer.paypal.com/ai-tools/build-with-llm.md), [/limited-release/agents](https://developer.paypal.com/limited-release/agents.md)
- Agentic commerce: [/agentic-commerce-services/about](https://developer.paypal.com/agentic-commerce-services/about.md), [/agent-ready/overview](https://developer.paypal.com/agent-ready/overview.md), [ACP](https://developer.paypal.com/agent-ready/agentic-commerce-protocol.md), [UCP](https://developer.paypal.com/agent-ready/universal-commerce-protocol.md), [Store Sync overview](https://developer.paypal.com/store-sync/overview.md), [Store Sync integrate](https://developer.paypal.com/store-sync/integrate.md)
- Payments and revenue: [disputes test](https://developer.paypal.com/disputes/test-go-live.md), [auth-honor](https://developer.paypal.com/payment-methods/auth-honor.md), [vault](https://developer.paypal.com/api/payment-tokens/save-without-purchase/paypal.md), [payouts test](https://developer.paypal.com/api/payouts/test-go-live.md), [multiseller](https://developer.paypal.com/platforms/checkout/standard/customize/multiseller-payments.md), [transaction search](https://developer.paypal.com/docs/api/transaction-search/v1/), [webhooks](https://developer.paypal.com/api/webhooks/overview), [venmo test](https://developer.paypal.com/venmo/test.md)
- Blogs: [WebMCP blog](https://developer.paypal.com/community/blog/WebMCP_PayPal_Agent_Ready), [hackathon blog](https://developer.paypal.com/community/blog/PayPal_AI_Hackathon)

**Newsroom:**
- [2025-10-27 Mastercard](https://newsroom.paypal-corp.com/2025-10-27-Mastercard-and-PayPal-Join-Forces-To-Accelerate-Secure-Global-Agentic-Commerce)
- [2025-10-28 Agentic Commerce Services](https://newsroom.paypal-corp.com/2025-10-28-PayPal-Launches-Agentic-Commerce-Services-to-Power-AI-Driven-Shopping)
- [2025-10-28 OpenAI](https://newsroom.paypal-corp.com/2025-10-28-OpenAI-and-PayPal-Team-Up-to-Power-Instant-Checkout-and-Agentic-Commerce-in-ChatGPT)
- [2026-01-11 Google UCP](https://s205.q4cdn.com/875401827/files/doc_news/From-Search-to-Checkout-PayPal-Supports-Trusted-AI-Checkout-with-Google-2026.pdf)
- [2026-08-10 Ai4](https://newsroom.paypal-corp.com/2026-08-10-PayPal-Takes-Center-Stage-at-Ai4-2026)

**Could not access:** the GitHub REST API (gh blocked in this session), and direct curl to developer.paypal.com (proxy-blocked). Content was read through a scraper. Star and issue counts are page-scrape snapshots from 2026-10-11.
