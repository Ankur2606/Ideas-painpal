---
title: "Wrong Box - Combined Concept"
type: deep-dive
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [finalist, combination]
up: "[[50 - Top 10 Overview]]"
spine: "[[I003 - Mismatch-to-Replacement]]"
final_score: 88
---
> Combines [[I001 - Intent Black Box|#1 Intent Black Box]] (instruction record), [[I002 - Three-Party Agent Error Settlement|#2 Three-Party Agent Error Settlement]] (agent-fault payout fork) onto the [[I003 - Mismatch-to-Replacement|#3 Mismatch-to-Replacement]] spine. Reports: [[D001 - Intent Black Box (Deep Dive)]], [[D002 - Three-Party Agent Error Settlement (Deep Dive)]], [[D003 - Mismatch-to-Replacement (Deep Dive)]].

# Agent-liability cluster (#1 + #2 + #3): one product or not? (2026-10-12)

## Bottom line
**Yes, build one product. But invert the original hierarchy.** The spine is **#3 (post-delivery mismatch check)**. **#1** shrinks to a module: an instruction record bound to the order. **#2** shrinks to one fork: the agent-platform reimbursement via Payouts. Shipping #1 or #2 as the headline would put us head-to-head with **Provenant**, a Devpost entry in this hackathon (sponsor tags ag-grid and render). Provenant already binds `custom_id` to a hash of the agent's decision trace and splits fault across user, merchant and agent with Shapley values. It then pays the agent's share through Payouts from a liability pool, or builds a dispute evidence pack ([Devpost](https://devpost.com/software/provenant-safe-checkout-and-recourse-for-ai-agents) ✅). **AgentProof** separately builds PayPal provide-evidence requests for agent disputes ([Devpost](https://devpost.com/software/agentproof-gwkxv6) ✅). Amex's ACE kit and Agent Purchase Protection (Apr 14 2026) take the "intent for disputes" and "someone covers agent error" stories at network level.

What no one shows is the **physical fact**: a photo of what arrived, checked against what the human asked for *and* what the shop listed. That photo answers who pays: if the listing doesn't match, the merchant pays; if the listing matches but the instruction doesn't, the agent pays. It then executes the answer on PayPal before a chargeback exists.

## Working name and single pitch
**"Wrong Box" (working name): when your AI agent buys the wrong thing, snap the box. We work out whether the shop or the agent got it wrong, and fix it on PayPal before anyone files a chargeback.**

Pitch (≈60 words): *Shopping agents will get orders wrong, and today nobody owns those mistakes. Card rules make the merchant eat them, even when the agent misread the instruction. Wrong Box compares the delivered item with the human's original instruction and the listing. If the shop erred, it runs a PayPal replacement offer. If the agent erred, the agent platform's guarantee pays the buyer through PayPal Payouts. Either way, no chargeback.*

## Spine + modules

| Layer | From | What it does | PayPal capability | Build effort |
|---|---|---|---|---|
| Module A: Instruction record | #1 (slimmed) | Normalizes "navy hoodie, M, < $60" into attributes; buyer confirms; `custom_id = "wb:v1:<sha256>"` (≤255 chars ✅) | Orders v2 (custom_id), read back via `disputed_transactions[].custom` (≤2000 ✅) | ~4 days |
| **Spine: Delivery check** | #3 | Photo upload → per-attribute vision verdict vs instruction **and** listing; shows crops; confidence below threshold → human review | Shipment Tracking (delivery and label match) | ~1.5 weeks |
| Fork M: Merchant at fault | #3 + #2 | Pre-dispute partial refund, or a replacement through the dispute: `make-offer REPLACEMENT_WITHOUT_REFUND` → `accept-offer` | Refunds, Disputes (create [sandbox], make-offer, accept-offer, provide-evidence on refusal), webhooks | ~1 week |
| Fork A: Agent at fault | #2 (slimmed) | Agent platform's opt-in "make-it-right" guarantee pays the buyer; merchant never sees a dispute | Payouts (EMAIL / VENMO_HANDLE, `sender_batch_id` = case ID) + payouts webhooks | ~3 days |
| Fork B: Ambiguous instruction (could) | #2 | Split: partial merchant refund + partial payout | Refunds + Payouts | ~2 days |
| Not built | #1/#2 | Full transcript capture SDK, Merkle trees, Shapley splits, rulebook publishing | — | dropped (commodity or duplicate) |

That's 5 non-checkout PayPal capabilities in the core loop (Orders metadata binding, Tracking, Refunds, Disputes, Payouts), plus webhooks. The AI makes the consequential structured decision (the fault class), and deterministic code moves the money. Per the anchors this is Tech 8. It reaches 9 if the unhappy paths are shown: merchant declines → evidence → adjudicate, and payout DENIED via the `ERRPYO` test values.

**Combined scores:** [8,8,6,6,9,7,7] → weighted 88. The originals were #2 95 / #3 93 / #1 92, all inflated by the "no one does this" assumption that Provenant breaks.

## Why one product beats three
- #1 alone has no visible end state (hash + JSON). #2 alone needs three personas and duplicates Provenant. #3 alone (scored 87) is a returns feature that isn't specific to agents.
- Combined, each module fixes another's weakness. #1 supplies the reference that makes #3 *agent-specific*. #3 supplies the *fact* that makes #2's allocation credible without counterfactual replay. #2 supplies the second PayPal money movement, which creates the "same photo, different payer" moment.
- Sponsor/HM fit: **Best Use of Agentic Commerce** (agent-error recourse), **Best Demo Delivery** (photo → split screen → PayPal state flips). AG Grid case queue (sponsor prize; differentiate from Provenant's grid). Render hosting. Channel3 product lookup as the canonical "listing".

## 3-minute demo
| Time | Scene | PayPal state change on screen |
|---|---|---|
| 0:00–0:20 | Hook: 58% fear wrong-item agent buys (NMI); "No liability shift exists yet" (Worldpay); merchants eat it | — |
| 0:20–0:50 | Maya: "navy hoodie, size M, under $60." Instruction card confirmed; agent checks out | Order CREATED → COMPLETED; inset shows `custom_id wb:v1:3f9a…` |
| 0:50–1:30 | **Wow 1:** box arrives; photo; split screen *Asked navy/M · Listed navy/M · Got royal/L* with crops → "Shop shipped the wrong item" | Tracker DELIVERED |
| 1:30–2:05 | Merchant queue (AG Grid) → one click → replacement offer → Maya accepts | Dispute PP-D-… `make-offer REPLACEMENT_WITHOUT_REFUND` → `accept-offer` → **RESOLVED** (webhook toast) |
| 2:05–2:40 | **Wow 2:** second order, listing *was* royal; agent chose it anyway → "Agent error" → agent platform's guarantee pays | **Payout** batch SUCCESS; Maya's sandbox balance +$54 in the same frame; merchant dispute count stays 0 |
| 2:40–3:00 | Unhappy paths montage (merchant declines → evidence PDF → adjudicate; low confidence → human; payout DENIED → retry); API strip; close | — |

Production notes: pre-record the sandbox UI dispute in case API creation is blocked. Make every state change a live API response or webhook toast, not a mock. Keep the hash inset small: it's support, not the story.

## Day-1 test list (gating)
1. `POST /v1/customer/disputes` with buyer `PayPal-Auth-Assertion` on an Orders v2 capture: which transaction ID works? (The public OpenAPI lacks this endpoint, and the reference page calls create "limited-release"; test-go-live documents it ✅.) Fallback: sandbox buyer UI.
2. `allowed_response_options` includes `REPLACEMENT_WITHOUT_REFUND` for a NOT_AS_DESCRIBED inquiry, and `accept-offer` closes it.
3. Payouts from a second sandbox business app to the buyer's personal sandbox email; balance visible.
4. `GET dispute` → `disputed_transactions[0].custom` equals the order custom_id.
5. `provide-evidence` multipart with a PDF (<10 MB) succeeds (avoid `INVALID_EVIDENCE_FILE`).

## Risks
- **Judge comparison with Provenant:** lead with the buyer and the photo, never with "liability engine" or "flight recorder". Explicitly position as "pre-dispute and fact-driven" in the README.
- **Forward-looking impact:** no published agent-dispute volume. Anchor on NMI 58%, Payments Association 24%, chargeback growth (Mastercard/Datos), and the VAMP 1.5% threshold.
- **Agent platforms paying is voluntary:** frame it as an opt-in guarantee, with the Amex precedent that guarantees are competitive.
- **Vision reliability:** OCR size and model labels, use colour checks against the reference image, and set a confidence floor.

## Sources
See 1_intent-black-box.md, 2_three-party-settlement.md, 3_mismatch-to-replacement.md (all claims carry URLs and confidence tags there).
