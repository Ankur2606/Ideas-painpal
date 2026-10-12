---
title: "Deep dive: #1 Intent Black Box"
type: deep-dive
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [finalist, deep-dive, verdict/demote]
up: "[[50 - Top 10 Overview]]"
idea: "[[I001 - Intent Black Box]]"
verdict: demote
final_score: 71
---
> Idea note: [[I001 - Intent Black Box]] · Verdict: **demote** · Final score **71/120** (desk 92). Confidence tags: ✅ primary read directly · ⚠️ secondary / vendor / single source · ❌ unverified. `⚠ inference` marks judgment.

# #1 Intent Black Box — deep dive (2026-10-12)

## 1. Verdict — DEMOTE as a standalone entry; keep as the thin evidence spine of the combined product

The problem is real and well documented. No card network or protocol says who pays for "authorized but wrong" agent purchases, and AP2 explicitly puts dispute resolution out of scope. But the specific mechanism is already on Devpost **in this hackathon**. **Provenant** (tags ag-grid, render, paypal-payouts, paypal-disputes-api) does exactly what we planned: "The PayPal order's `custom_id` is the hash of the decision trace", a hash-chained flight recorder, case replay "from recorded inputs", and a "dispute evidence pack". **AgentProof** records "what the agent searched for, what it chose, the budget check, and the payment" and builds the PayPal provide-evidence request when a dispute arrives. **XReceipt**, **LexProof** (a hash chain anchored on Sepolia) and **AGENT GATE** ("auditable evidence") fill out the receipt and audit cluster. Off Devpost, **Amex's ACE developer kit** (Apr 14 2026) already captures purchase intent and cart context "to support authentication, authorization, and disputes". **Chargebacks911's UDMS** captures consent and permission records for agent-initiated transactions. A recorder whose only job is "bind the transcript to the order and draft the evidence" would be judged as the fifth or sixth version of the same entry.

What survives is the **instruction capture**: a structured, hashed copy of what the human actually asked for, bound to the order. It is worth keeping only as the reference input that makes #3 (did the delivered item match the instruction?) and #2 (who pays?) decidable.

| Axis | Old | New | Reason |
|---|---|---|---|
| Tech | 9 | 8 | Orders + Disputes + webhooks is solid. The hash binding is trivial, and Provenant already does it. |
| Design | 7 | 6 | It's middleware. The persona (agent builder or merchant) has no satisfying end state unless a dispute happens. |
| Impact | 7 | 6 | Liability evidence is strong (Worldpay, Payments Association), but there's no agent-dispute volume data (❌), and Amex is solving the same thing issuer-side. |
| Innovation | 7 | **3** | Provenant (same hackathon) uses the same custom_id = trace-hash binding plus replay. AgentProof does merchant evidence for agent disputes. Amex ACE does intent + cart context for disputes. |
| Demo | 8 | 6 | Hash-in-custom_id is invisible on video. Evidence posting is a JSON response. |
| Feasibility | 8 | 7 | Sandbox dispute *creation* isn't in the public OpenAPI spec and is called "limited-release" on the reference landing page. The test-go-live page documents it, so it needs a day-1 test. |
| Risk | 8 | 6 | Direct-duplicate risk in judging, plus privacy of recorded page and tool context. |

s_adjusted = [8,6,6,3,6,7,6] → weighted total 71 (was 92).

## 2. Problem validation

| Claim | Number | Source | Conf |
|---|---|---|---|
| No liability shift for non-fraud agent disputes (misread instruction, wrong item) | qualitative | [Worldpay, Jul 2026](https://worldpay.com/insights/articles/agentic-commerce-liability-is-still-being-written) | ✅ (via raw/C) |
| UK merchants have no consensus on who pays for an agent purchase | top answer "depends" 24% | [Payments Association, May 14 2026](https://thepaymentsassociation.org/article/agentic-commerce-uk-retail-an-unresolved-liability-question/) | ✅ (raw/D) |
| US adults fear an AI buys the wrong item, size or colour | 58% | [NMI, Aug 26 2026](https://www.nmi.com/about-us/news/nmi-research-consumers-want-ai-to-help-them-shop-not-control-their-spending/) | ✅ vendor |
| AP2 v0.2: "dispute resolution, retention, and retrieval requirements are outside the scope of this specification"; task-scope determination also out of scope | — | [AP2 spec](https://ap2-protocol.org/ap2/specification/) | ✅ read |
| Mandates don't protect pre-signature context (48 threats, 8 High) | 48/8 | [arXiv 2608.23858](https://www.emergentmind.com/papers/2608.23858) | ✅ (raw/C) |
| "No rule makes the agent platform liable: the merchant stays merchant of record." Visa's rules (Apr 2026) address agentic txns; Mastercard's public rules are silent; EMVCo draft framework (Sep 1 2026) publishes no dispute-liability allocation | — | [Chargeflow, upd. Oct 7 2026](https://www.chargeflow.io/blog/ai-agent-chargeback-liability) | ⚠️ vendor blog |
| Merchants "cannot prove what the agent was authorized to do" | — | [Chargebacks911 via Business Money, May 14 2026](https://www.business-money.com/announcements/ai-agents-are-starting-to-buy-things-but-who-handles-the-dispute-when-they-get-it-wrong/) | ⚠️ vendor |
| Agent-dispute volume | **no published data** | raw/D §6 | ❌ |

User and industry voices (all exist; I read the pages):
- Monica Eaton, Chargebacks911: "In an agentic world, that question doesn't have a clean answer" ([Business Money](https://www.business-money.com/announcements/ai-agents-are-starting-to-buy-things-but-who-handles-the-dispute-when-they-get-it-wrong/)) ✅
- Rivero: "Agentic commerce is already here, but the back-office isn't fully ready", and on fixing that back-office gap, "no one has a credible answer" ([Rivero, Mar 6 2026](https://rivero.tech/blog/agentic-commerce-needs-new-dispute-framework)) ✅
- Worldpay: "the murky cases are everything short of outright fraud, such as an agent that misread an instruction" (quoted in [Chargeflow](https://www.chargeflow.io/blog/ai-agent-chargeback-liability)) ⚠️ secondary
- No first-person consumer complaint was found about a *wrong agent purchase* being disputed. That gap is itself a signal that the problem is still forward-looking. ⚠ inference

## 3. Competitor & novelty research

Queries run: "Catena Labs Agent Commerce Kit ACK receipt verifiable credential dispute"; "AP2 … payment receipt mandate dispute"; "Mastercard Verifiable Intent reference implementation github"; "agentic commerce chargeback reason code Visa Mastercard 2026"; "2026 launch agentic chargeback dispute product Justt/Chargebacks911/Forter/Sift"; "American Express Agent Purchase Protection"; "github flight recorder audit trail AI shopping agent purchase hash"; "Natural agentic payments disputes"; Devpost searches "xreceipt", "velqiris", "lexproof", "\"agent gate\" paypal", "agent dispute paypal" (38 results, both pages read).

| Name | Type | What it does | Overlap | URL | Conf |
|---|---|---|---|---|---|
| **Provenant** | Devpost entry (this hackathon, by tags) | Lineage-labelled mandate, hash-chained flight recorder, **custom_id = hash of decision trace**, replay-based case ruling, Shapley fault split, refund / void / **Payouts from liability pool** / dispute evidence pack | **High (near-identical)** | https://devpost.com/software/provenant-safe-checkout-and-recourse-for-ai-agents | ✅ read |
| **AgentProof** | Devpost entry | Records agent search, choice, budget check and payment; on dispute rebuilds facts; AI writes evidence; builds PayPal provide-evidence request | High | https://devpost.com/software/agentproof-gwkxv6 | ✅ read |
| XReceipt | Devpost entry | Signed portable receipt per PayPal payment: "what was requested… what was delivered… did the two match?" (x402/PYUSD) | Med-High | https://devpost.com/software/xreceipt | ✅ read |
| LexProof | Devpost entry | Contract-gated invoices and refunds via agent-toolkit; "Every step is a hashed receipt… anchored on Ethereum Sepolia" | Med | https://devpost.com/software/lexproof-contract-governed-agentic-payments-on-paypal | ✅ read |
| VELQIRIS Evidence Gate | Devpost entry | Pre-execution "cryptographic order verification" gate (Orders + Webhooks); no disputes | Low-Med | https://devpost.com/software/velqiris-paypal-ai-evidence-gate | ✅ read |
| AGENT GATE | Devpost entry | Policy + human approval, "auditable evidence", duplicate-charge recovery | Low-Med | https://devpost.com/software/agent-gate-human-controlled-ai-payments | ✅ read (thin page) |
| Squid; AgentVerify; PayLeash | Devpost entries (earlier hackathons) | "trust and liability layer… cryptographic audit trails"; "dispute resolution layer for agent commerce"; signed mandates + dispute replies | Med | devpost.com/software/squid-2fwad5, /agentverify-3zrcgh, /payleash-a-trust-layer-for-paypal-ai-agents | ⚠️ tagline only |
| Amex ACE dev kit + Agent Purchase Protection | Platform feature (Apr 14 2026) | Captures purchase intent + cart context for disputes; protects card members from "charges related to AI agent error" (registered agents) | High (issuer-side) | [press release](https://www.eagletribune.com/region/american-express-debuts-agentic-commerce-experiences-ace-developer-kit-and-announces-industry-first-protection-for/article_0aed4835-c886-5dee-867d-976a006c806a.html) | ✅ read |
| Chargebacks911 UDMS | Product | Captures consent and permission records for agent-initiated transactions | Med | [Business Money](https://www.business-money.com/announcements/ai-agents-are-starting-to-buy-things-but-who-handles-the-dispute-when-they-get-it-wrong/) | ⚠️ |
| Chargeflow Automation | Product | Same chargeback workflow for agent disputes, "different evidence attached" | Med | [Chargeflow](https://www.chargeflow.io/blog/ai-agent-chargeback-liability) | ⚠️ |
| Rivero Amiko | Product (issuer) | Agentic dispute management; argues for intent, agent-behaviour and presentation logs | Med | [Rivero](https://rivero.tech/blog/agentic-commerce-needs-new-dispute-framework) | ✅ |
| ATXP | Product | "transaction-level receipts for every agent action", agent-ID tagging for dispute evidence | Med | [ATXP blog, Mar 31 2026](https://atxp.ai/blog/agent-payment-dispute-resolution) | ⚠️ |
| AP2 v0.2 | Protocol | Signed Payment Receipt must match hash of closed Payment Mandate; mandates give evidence of "what the user, and each role saw"; disputes out of scope | Med | https://ap2-protocol.org/ap2/specification/ | ✅ |
| Mastercard Verifiable Intent | Protocol + ref impl | Selectively disclosed intent record "for fraud mitigation or dispute resolution" | Med | [Mastercard](https://www.mastercard.com/au/en/news-and-trends/stories/2026/verifiable-intent.html) | ✅ (raw/C) |
| Catena ACK | OSS kit | Identity, payments, receipts (W3C VC) | Med | [catena.com ACK v2](https://catena.com/blog/ack-v2-smaller-identity-core-x402-payment-profile) | ⚠️ |
| Skyfire KYAPay / Kite Agent Passport / Prove Verified Agent | Identity | Agent identity + principal binding; no adjudication | Low | raw/C §2 | ✅/⚠️ |
| LangSmith / Langfuse | Observability | Store full agent traces, but not bound to a payment and not dispute-shaped | Low-Med (the *capture* part is commodity) | ⚠ inference | ⚠️ |
| airblackbox/gateway, flightbox, "Agent Flight Recorder" HF space | OSS | Generic agent flight recorders / audit gateways | Low-Med | pkg.go.dev/github.com/airblackbox/gateway; pypi.org/project/flightbox | ⚠️ search snippet |

## 4. Novelty verdict
- **Not new:** hashing the agent trace into the order (Provenant), merchant evidence for agent disputes (AgentProof, Chargeflow, C911), signed receipts (XReceipt, AP2, ACK, ATXP), and intent capture for disputes (Amex ACE, Verifiable Intent). The capture SDK itself is commodity observability.
- **Still thin-but-open:** a *normalized instruction record* (structured attributes such as colour, size, model, budget and substitutes allowed) that is later checked against **physical delivery evidence**. That's what #3 needs, and no competitor found combines it with post-delivery vision.
- **Sharpest surviving differentiator:** "We don't just prove what the agent was allowed to buy. We check what actually arrived against what the human asked for." That sentence belongs to #3, not #1.

## 5. Technical feasibility (PayPal sandbox)
Verified facts:
- `purchase_units[].custom_id` is **1–255 chars** (not 127) and is not shown to the payer. `invoice_id` is **1–127**, shown to the payer, and unique per merchant by default ([purchase_unit_request](https://developer.paypal.com/api/orders/v2/definitions/purchase_unit_request) ✅). A SHA-256 hex string (64 chars) plus a prefix such as `ibb:v1:` fits in custom_id.
- The dispute object exposes `disputed_transactions[].custom` (≤2000) and `invoice_number` (≤127, pattern `^[A-Za-z0-9:\-|]+$`) (PayPal REST OpenAPI `customer_disputes_v1.json` ✅). The binding can therefore be read straight back from a dispute.
- Evidence files must be .jpg/.jpeg/.gif/.png/.pdf, **<10 MB per file and ≤50 MB per call** ([supported file types](https://developer.paypal.com/platforms/disputes/reference/supported-file-types-sizes.md) ✅). Notes are ≤2000 chars and evidence_list holds ≤100 items. **JSON transcripts must be rendered to PDF.**
- Evidence types include `ORDER_DETAILS`, `ITEM_DETAILS`, `LISTING_URL`, `PHOTOS_OF_SHIPPED_ITEM`, `PROOF_OF_EMPTY_PACKAGE_OR_DIFFERENT_ITEM`, `DECLARATION` and `OTHER` (spec ✅). There is no agent-specific type.
- Sandbox dispute creation: `POST /v1/customer/disputes`, multipart field `input`, header `PayPal-Auth-Assertion` (buyer JWT), body `disputed_transactions[].buyer_transaction_id`, `reason`, `dispute_amount`. The prerequisite in the docs is a personal account sending money to the business account. Duplicate disputes on a transaction are never allowed, and actions appear "a few minutes" after creation ([test-go-live](https://developer.paypal.com/disputes/test-go-live.md) ✅). **This endpoint is absent from the public OpenAPI**, and the reference landing page says create is "limited-release".

Day-1 tests:
1. Create an order with `custom_id="ibb:v1:<sha256>"`, capture it as the sandbox buyer, then `POST /v1/customer/disputes` with an unsigned JWT assertion (`{"alg":"none"}`, `iss=<client_id>`, `payer_id=<buyer payer id>`). Find out whether a capture ID or the buyer-side transaction ID is required. **Fallback:** open the dispute in the sandbox buyer UI (sandbox.paypal.com Resolution Center), pre-recorded.
2. `GET /v1/customer/disputes/{id}`: confirm `disputed_transactions[0].custom` echoes the custom_id.
3. `provide-evidence` with a 1-page PDF: confirm the multipart part naming avoids `INVALID_EVIDENCE_FILE` ([SO 78902643](https://stackoverflow.com/questions/78902643/paypal-disputes-api-returns-invalid-evidence-file-when-posting-file) ⚠️).

## 6. AI contribution
LLM-as-judge comparing the normalized instruction against the cart and against delivery evidence, with output in a strict JSON schema: `{fault: merchant|agent|buyer_ambiguity|friendly_fraud|undetermined, rule_id, confidence, cited_evidence[]}`. Deterministic code does the hashing, the money movement and the threshold rules, and a human confirms anything below the confidence threshold. Model: a multimodal frontier model (Gemini 2.5/3 class, which matches the team's Gemini experience) with temperature 0 and schema-constrained output.

## 7. MVP scope (only as a module of the combined product)
- **Must:** an instruction normalizer (NL → attributes JSON), order creation with custom_id hash binding, a stored record, and a viewer that shows instruction vs cart vs delivered.
- **Should:** an evidence PDF generator for the provide-evidence call.
- **Could:** AP2- or VI-shaped export of the intent record.
- Effort: about 1 week of the 4.5.

## 8. Demo storyboard (standalone, for completeness — not recommended)
0:00 agent buys → 0:40 show custom_id hash in PayPal order → 1:20 buyer disputes → 2:00 AI classifies and posts evidence → 2:40 dispute shows evidence. The weakness is that the "wow" is a hash and a JSON response.

## 9. Risks & mitigations
- **Duplicate of Provenant / AgentProof:** don't ship #1 standalone. Fold it into #3 as the instruction reference.
- **Privacy:** store only the normalized instruction plus hashes of page snippets, not raw pages.
- **Sandbox dispute creation access:** day-1 test, with the UI fallback above.

## 10. Sources
See inline links. Local: raw/A §3.6, raw/C §1–3, raw/D §6, PayPal REST OpenAPI `customer_disputes_v1.json` (scratchpad clone of paypal-rest-api-specifications).
