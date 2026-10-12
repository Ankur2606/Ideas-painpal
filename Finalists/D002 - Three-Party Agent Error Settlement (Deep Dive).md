---
title: "Deep dive: #2 Three-Party Agent Error Settlement"
type: deep-dive
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [finalist, deep-dive, verdict/demote]
up: "[[50 - Top 10 Overview]]"
idea: "[[I002 - Three-Party Agent Error Settlement]]"
verdict: demote
final_score: 72
---
> Idea note: [[I002 - Three-Party Agent Error Settlement]] · Verdict: **demote** · Final score **72/120** (desk 95). Confidence tags: ✅ primary read directly · ⚠️ secondary / vendor / single source · ❌ unverified. `⚠ inference` marks judgment.

# #2 Three-Party Agent Error Settlement — deep dive (2026-10-12)

## 1. Verdict — DEMOTE as a standalone entry; keep one leg (agent-platform reimbursement via Payouts) as a module

The idea scored highest in the cluster (95) on the claim "No product settles three-way." **That claim is now false.** **Provenant** is a Devpost entry whose tags (ag-grid, render, paypal-payouts, paypal-disputes-api) match this hackathon's sponsors. It is pitched as "when they buy wrong, nobody knows who pays", and it "splits refunds by who actually caused the mistake". It uses "Exact Shapley values" over user, merchant and agent with confidence intervals. Remedies are a void, a merchant refund within signed policy, "a payout of the agent's share from a liability pool", or a dispute evidence pack. That is our mechanism, including Payouts as the agent-platform rail, built with more statistical polish than we planned. Off Devpost, **Amex Agent Purchase Protection** (Apr 14 2026) already commits an issuer to cover "charges related to AI agent error" for registered agents. That doesn't settle three ways, but it takes the "someone guarantees the buyer" story.

What survives: a **simpler, legible two-fork rule driven by a physical fact** rather than counterfactual replay. Item matches the listing but not the instruction → agent fault → the agent platform pays via Payouts and the merchant is kept out of the dispute. Item doesn't match the listing → merchant fault → replacement through Disputes make-offer. This is credible only when it is triggered by #3's delivery check. As a separate product, it's a weaker Provenant.

| Axis | Old | New | Reason |
|---|---|---|---|
| Tech | 9 | 8 | Disputes (make-offer / accept-offer) + Payouts + Refunds + webhooks is still deep. Docked because the "liability matrix" is a lookup table and Provenant already shows the same API set. |
| Design | 7 | 6 | Three personas and three dashboards is hard to make coherent in 3 minutes. Agent platforms paying is an assumption, not an observed behaviour. |
| Impact | 7 | 6 | Payments Association (24% max answer) and NMI (62% would blame the AI provider) are good. Still no agent-dispute volume (❌), and "No rule makes the agent platform liable" ([Chargeflow](https://www.chargeflow.io/blog/ai-agent-chargeback-liability) ⚠️) means no one is obliged to pay this leg. |
| Innovation | 9 | **3** | Provenant does three-party fault split + Payouts liability pool + disputes in the same hackathon. Amex covers agent error for buyers. |
| Demo | 8 | 7 | Three different money movements from three scenarios is visual, but slower than one fork. |
| Feasibility | 8 | 7 | Needs 3 sandbox accounts with 2 REST apps. The sandbox dispute-create path needs a day-1 test (see #1 §5). |
| Risk | 7 | 5 | Legal framing ("proposed rulebook"); head-on comparison with Provenant by the same judges. |

s_adjusted = [8,6,6,3,7,7,5] → weighted total 72 (was 95).

## 2. Problem validation

| Claim | Number | Source | Conf |
|---|---|---|---|
| UK merchants: who pays for an agent purchase made when the agent was only asked to research | "Depends" 24%; shared 21%; AI vendor 18%; PSP 15%; consumer 13%; merchant 9% | [Payments Association, May 14 2026](https://thepaymentsassociation.org/article/agentic-commerce-uk-retail-an-unresolved-liability-question/) | ✅ (raw/D) |
| Who consumers would blame for a premature AI purchase | AI provider 62%, retailer 34%, payments provider 24% | [NMI, Aug 2026](https://www.nmi.com/about-us/news/nmi-research-consumers-want-ai-to-help-them-shop-not-control-their-spending/) | ✅ vendor |
| By default the merchant carries the loss unless it wins; "No rule makes the agent platform liable" | — | [Chargeflow, upd. Oct 7 2026](https://www.chargeflow.io/blog/ai-agent-chargeback-liability) | ⚠️ |
| Card scheme view: "the cardholder is responsible for what their agent did on their behalf"; Mastercard "reportedly planning … scheme-carried liability for certified agents" | — | [Rivero, Mar 6 2026](https://rivero.tech/blog/agentic-commerce-needs-new-dispute-framework) | ⚠️ "reportedly" |
| Amex commits to protect eligible card members from charges from AI agent error (registered agents, authenticated intent) | — | [Amex press release, Apr 14 2026](https://www.eagletribune.com/region/american-express-debuts-agentic-commerce-experiences-ace-developer-kit-and-announces-industry-first-protection-for/article_0aed4835-c886-5dee-867d-976a006c806a.html) | ✅ |
| Network rule for agent dispute reason codes | **None found.** Visa's rules (Apr 2026) "expressly address agentic transactions" (identity/token requirements) but reuse 10.4 / 13.3; MC rules silent (4837 / 4853); EMVCo Agentic Payments draft (Sep 1 2026) has no liability allocation | [Chargeflow](https://www.chargeflow.io/blog/ai-agent-chargeback-liability) citing FBT Gibbons | ⚠️ secondary |
| Agent disputes count toward Visa VAMP (1.5% excessive) and MC ECM | — | same | ⚠️ |

Voices: Monica Eaton (Chargebacks911): "The ones who haven't will lose the revenue, pay the fee, and have no way to fight it." ([Business Money](https://www.business-money.com/announcements/ai-agents-are-starting-to-buy-things-but-who-handles-the-dispute-when-they-get-it-wrong/) ✅). Also the Rivero line on scheme liability above ✅. I found no buyer or agent-platform voice asking for a three-way settlement product (⚠ inference: demand is speculative).

## 3. Competitor & novelty research

Queries: as in #1, plus "insurance for AI agent errors purchases 2026 AIUC Armilla", "Natural agentic payments disputes", "ATXP agent payment dispute resolution", and Devpost "agent dispute paypal" (pp. 1–2).

| Name | Type | What it does | Overlap | URL | Conf |
|---|---|---|---|---|---|
| **Provenant** | Devpost entry (this hackathon by tags) | Shapley fault split user/merchant/agent; void, refund, **Payouts from liability pool**, dispute evidence; custom_id = trace hash; AG Grid; Render | **High (same mechanism + same APIs)** | https://devpost.com/software/provenant-safe-checkout-and-recourse-for-ai-agents | ✅ read |
| Amex Agent Purchase Protection | Network/issuer feature | Covers card members for AI-agent-error charges (registered agents) | Med-High (buyer-guarantee story) | press release above | ✅ |
| Armilla / AI-error insurance (Lloyd's market) | Insurance | Covers companies' losses from AI chatbot/agent errors | Med (the "agent platform pays" leg could be insured, not settled) | [Armilla](https://www.armilla.ai/resources/insurers-launch-cover-for-losses-caused-by-ai-chatbot-errors) | ⚠️ snippet |
| Fairplay; Rebuttal; Dispute Copilot; Dispute Defender ×2; SubGuard; Refund Desk | Devpost entries | Two-party dispute mediation / defence on PayPal | Low-Med (two-party) | devpost.com/software/fairplay-gx6ipj etc. | ⚠️ tagline |
| AgentVerify; Squid | Devpost entries (earlier) | "dispute resolution layer for agent commerce"; "trust and liability layer" | Med | devpost.com/software/agentverify-3zrcgh, /squid-2fwad5 | ⚠️ tagline |
| Chargeflow / Justt / Chargebacks911 | Products | Two-party merchant chargeback fighting; C911 UDMS adds agent consent records | Low-Med | as #1 | ⚠️ |
| Rye; Natural; ATXP | Agent payment rails | No fault allocation or reimbursement feature found. ATXP: "doesn't say who bears losses" | Low | [ATXP](https://atxp.ai/blog/agent-payment-dispute-resolution) | ⚠️ |

## 4. Novelty verdict
- **Not new:** three-party fault split, Payouts as the agent-share rail, dispute evidence from the same engine (all in Provenant), and buyer guarantees for agent error (Amex).
- **Still differentiable (small):** (a) **fact-first, vision-driven fault**. The delivered item is compared with the listing *and* the instruction, so the split is a two-question decision tree a judge can follow, not a Shapley distribution. (b) **Pre-dispute resolution**: the merchant leg is a make-offer replacement in the INQUIRY stage, and the agent leg pays the buyer before any claim or chargeback hits the merchant's ratio.
- **Sharpest differentiator sentence:** "Same photo, two different payers: if the shop shipped what it listed, the agent platform makes it right, and the merchant never sees a dispute."

## 5. Technical feasibility (PayPal sandbox)
Accounts: **merchant** (business, REST app A), **agent platform** (business, REST app B, funds the reimbursement pool), and **buyer** (personal).

API sequence (verified shapes, from the PayPal REST OpenAPI specs ✅):
1. Orders v2 create/capture (merchant app), with custom_id carrying the instruction hash (≤255 chars).
2. **Merchant-fault leg:** buyer opens a dispute (sandbox `POST /v1/customer/disputes`, reason `MERCHANDISE_OR_SERVICE_NOT_AS_DESCRIBED`). The merchant calls `POST /v1/customer/disputes/{id}/make-offer` with `offer_type` ∈ {REFUND, REFUND_WITH_RETURN, **REFUND_WITH_REPLACEMENT, REPLACEMENT_WITHOUT_REFUND**} (note ≤2000). The buyer accepts via sandbox `accept-offer`. Webhook `CUSTOMER.DISPUTE.RESOLVED`. Or, with no dispute: partial refund via `POST /v2/payments/captures/{id}/refund` plus a replacement tracker via `/v2/shipping/trackers`.
3. **Agent-fault leg:** `POST /v1/payments/payouts` from app B, `recipient_type: EMAIL` (sandbox buyer email) or `VENMO_HANDLE`, `sender_batch_id` = case ID (duplicate-safe for 30 days ✅ spec). Poll `GET /v1/payments/payouts/{batch}` or use the webhook `PAYMENT.PAYOUTSBATCH.SUCCESS`.
4. **Ambiguous-instruction leg:** a split. Partial merchant refund plus a partial payout.

Unknowns / day-1 tests:
- Payouts enabled for sandbox app B. Live access "requires approval via the PayPal Developer Dashboard" (raw/A §3.5 ✅). Test: a $5 payout to the buyer email, then check the buyer's sandbox balance.
- Is `make-offer` with `REPLACEMENT_WITHOUT_REFUND` listed in `allowed_response_options` for a NOT_AS_DESCRIBED inquiry? Test via GET dispute after the "few minutes" delay.
- Dispute-create assertion details (#1 §5).

## 6. AI contribution
Fault attribution as a structured decision. Vision answers two booleans with confidence: `matches_listing` and `matches_instruction`, per attribute (colour, size, model, quantity). An LLM maps instruction ambiguity ("a blue hoodie" with navy delivered and both listed as "blue") to `buyer_ambiguity`. A **deterministic matrix** turns those outputs into settlement legs. The LLM never chooses amounts. Every party gets a plain-language explanation that cites rule IDs. Below the confidence threshold, the case goes to human review.

## 7. MVP scope (as a module)
- **Must:** the two-fork matrix (merchant vs agent) and the Payouts leg from the agent-platform account.
- **Should:** the split leg and a settlement ledger.
- **Could:** a published "Agent Error Rulebook v0" page.
- About 1 week.

## 8. Demo storyboard (standalone — not recommended)
Three scripted cases, each producing a different PayPal money movement. It's too slow for 3 minutes. Use one fork in the combined demo instead.

## 9. Risks & mitigations
- **Head-on duplicate of Provenant:** reframe as delivery-fact-driven, pre-dispute, and buyer-first. Don't claim "first three-party settlement".
- **Agent platforms may refuse liability:** pitch it as an opt-in "make-it-right guarantee" that the platform funds as a growth or trust feature (the Amex precedent shows guarantees are a competitive lever).
- **Legal:** label it "proposed rulebook, not legal advice".

## 10. Sources
Inline. Local: raw/A §3.5–3.6, raw/C §3.1, raw/D §6; OpenAPI `customer_disputes_v1.json`, `payments_payouts_batch_v1.json`.
