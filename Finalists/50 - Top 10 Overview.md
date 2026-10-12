---
title: "50 - Top 10 Overview"
type: finalists
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [finalists, top-10]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Top 10 ideas and solutions

**How ranked:** deep-dive verdict first (advance / advance-with-changes ahead of demote), then final score /120. Tier A = build candidates (the Top 3). Tier B = viable alternates. Tier C = best of the *demoted*; each is listed because it scored well on desk research but its own deep dive recommended against building it standalone. Presenting them honestly is the point: **a Top 10 that hid those verdicts would repeat the inflation the deep dives were run to remove.**

⚠️ The finalists were deep-dived from the high-scoring survivor pool. Several more survivors scored 83 to 87 on desk research (e.g. #5, #35, #40, #96, #13) and were not deep-dived (see [[44 - Bench Ideas Not Deep-Dived]]).

| Rank | Idea | Tier | Final /120 | Verdict | Prize target | Day-1 gate |
|---|---|---|---|---|---|---|
| 1 | [[I023 - Seller Protection Preflight\|#23 Seller Protection Preflight]] | Tier A | 89 | advance-with-changes | Grand; fallback Most Impactful / Best Use of PayPal + AI; sponsor AG Grid. | T1 |
| 2 | [[Wrong Box - Combined Concept\|Wrong Box (#3+#1+#2)]] | Tier A | 88 (spine #3 = 87) | advance-with-changes | HM Best Use of Agentic Commerce / Best Demo Delivery; Grand possible; sponsor AG Grid or Channel3. | T2, T3 |
| 3 | [[I055 - Payout Failure Triage\|#55 Payout Failure Triage]] | Tier A | 86 | advance-with-changes | HM Best Use of PayPal + AI or Most Impactful; sponsor AG Grid. | T4 |
| 4 | [[I028 - Early-Pay Discount Optimizer\|#28 Early-Pay Discount Optimizer]] | Tier B | 85 | advance-with-changes | Most Impactful (freelancers / SMBs); sponsor AG Grid. | T5 |
| 5 | [[I056 - Integration Chaos Monkey\|#56 Integration Chaos Monkey]] | Tier B | 80 | advance-with-changes | HM Most Creative / Best Use of PayPal + AI. | T6 |
| 6 | [[I042 - Pre-Checkout Injection Firewall\|#42 Pre-Checkout Injection Firewall]] | Tier B | 76 | advance-with-changes | HM Best Use of Agentic Commerce. | T7 |
| 7 | [[I009 - Rental Deposit Inspector\|#9 Rental Deposit Inspector]] | Tier C | 81 | demote | Not recommended as standalone. | T8 |
| 8 | [[I020 - Dispute-to-Listing Fixer\|#20 Dispute-to-Listing Fixer]] | Tier C | 80 | demote | Not recommended as standalone. | - |
| 9 | [[I008 - Final-Price Agent (Overcapture)\|#8 Final-Price Agent (Overcapture)]] | Tier C | 78 | demote | Branch only. | T8 |
| 10 | [[I084 - Accessible Voice Checkout\|#84 Accessible Voice Checkout]] | Tier C | 75 | demote | Better as a design pillar inside another build. | - |

Day-1 gates are defined in [[63 - Day-1 Sandbox Test Plan]].

## Solution cards

### 1. Seller Protection Preflight (+ tracking release + dispute evidence pack)
**Tier:** Tier A · **Score:** 89/120 · [[D023 - Seller Protection Preflight (Deep Dive)|Deep dive]] · [[I023 - Seller Protection Preflight|Idea note]]

**Solution.** A pre-ship gate for PayPal sellers. For each paid order it checks the ship-to address against Transaction Details, reads buyer messages for address-change and off-platform requests (the "ship it to my cousin" scam), checks proof-of-delivery needs, and quotes the policy clause. On clearance it uploads tracking (the documented fastest way to release held funds) and pre-builds the dispute evidence pack.

**Hero demo moment.** Scam message → red "do not ship" with the quoted PayPal clause → corrected label → tracking uploaded → order flips.

**Prize target.** Grand; fallback Most Impactful / Best Use of PayPal + AI; sponsor AG Grid.

**Biggest risk.** AI looks decorative next to a rules table.

**Day-1 gate.** T1

### 2. "Wrong Box" (#3 spine + #1 binding + #2 payout fork)
**Tier:** Tier A · **Score:** 88/120 · [[Wrong Box - Combined Concept|Combined concept]]

**Solution.** When an agent-bought item arrives, snap the box. A vision check compares the photo with the human's instruction and the listing. If the shop erred, a PayPal replacement offer resolves the dispute; if the agent erred, the agent platform's opt-in guarantee pays the buyer through Payouts.

**Hero demo moment.** Split screen "Asked navy/M · Listed navy/M · Got royal/L", then the dispute flips to RESOLVED; second order pays out and the balance rises in-frame.

**Prize target.** HM Best Use of Agentic Commerce / Best Demo Delivery; Grand possible; sponsor AG Grid or Channel3.

**Biggest risk.** Provenant (same hackathon) overlaps the liability story.

**Day-1 gate.** T2, T3

### 3. Payout Failure Triage
**Tier:** Tier A · **Score:** 86/120 · [[D055 - Payout Failure Triage (Deep Dive)|Deep dive]] · [[I055 - Payout Failure Triage|Idea note]]

**Solution.** A recoverable payout workflow. A payout to an unknown email goes UNCLAIMED; the agent contacts the recipient, gets a corrected handle, cancels (RETURNED) and re-issues. It visibly refuses to reroute around compliance blocks (RISK_DECLINE, REGULATORY_BLOCKED).

**Hero demo moment.** Live ledger cell-flash: UNCLAIMED → RETURNED → SUCCESS, then a refusal on a compliance block.

**Prize target.** HM Best Use of PayPal + AI or Most Impactful; sponsor AG Grid.

**Biggest risk.** Failure branches may be mock-only; Payouts used by 10+ entries.

**Day-1 gate.** T4

### 4. Early-Pay Discount Optimizer
**Tier:** Tier B · **Score:** 85/120 · [[D028 - Early-Pay Discount Optimizer (Deep Dive)|Deep dive]] · [[I028 - Early-Pay Discount Optimizer|Idea note]]

**Solution.** Per-client early-payment discounts priced from cost-of-waiting maths and written into PayPal Invoicing conditional rules.

**Hero demo moment.** An invoice that shows a client-specific discount and its expiry.

**Prize target.** Most Impactful (freelancers / SMBs); sponsor AG Grid.

**Biggest risk.** One API family; payer-view behaviour behind an "invoicing/internal" scope; Chaser overlaps.

**Day-1 gate.** T5

### 5. Integration Chaos Monkey
**Tier:** Tier B · **Score:** 80/120 · [[D056 - Integration Chaos Monkey (Deep Dive)|Deep dive]] · [[I056 - Integration Chaos Monkey|Idea note]]

**Solution.** Dynamic sandbox fault injection with signed webhook replay and a re-run-gated fix PR for developers integrating PayPal.

**Hero demo moment.** A failing checkout turning green after an AI-authored, test-gated PR.

**Prize target.** HM Most Creative / Best Use of PayPal + AI.

**Biggest risk.** Overlaps PayPal's own /paypal:doctor; developer-only impact.

**Day-1 gate.** T6

### 6. Selection-Integrity Firewall (pivot of Injection Firewall)
**Tier:** Tier B · **Score:** 76/120 · [[D042 - Pre-Checkout Injection Firewall (Deep Dive)|Deep dive]] · [[I042 - Pre-Checkout Injection Firewall|Idea note]]

**Solution.** Buyer-side counterfactual audit of what an agent chose (catching hijacked choice, not just payee) plus capture-time order re-verification. Deterministic core, classifier advisory only.

**Hero demo moment.** Same prompt run with and without injected text: the product choice flips and the capture is blocked.

**Prize target.** HM Best Use of Agentic Commerce.

**Biggest risk.** Warden (same hackathon) already ships a merchant-side MCP firewall.

**Day-1 gate.** T7

### 7. Rental Deposit Inspector (demoted)
**Tier:** Tier C · **Score:** 81/120 · [[D009 - Rental Deposit Inspector (Deep Dive)|Deep dive]] · [[I009 - Rental Deposit Inspector|Idea note]]

**Solution.** Hold a deposit, AI-diff before/after photos, capture only the damage. Demoted because RentProof and many rental-AI products exist; keep only as a holds branch.

**Hero demo moment.** Partial capture after a photo diff.

**Prize target.** Not recommended as standalone.

**Biggest risk.** Near-duplicate public repo.

**Day-1 gate.** T8

### 8. Dispute-to-Listing Fixer (demoted)
**Tier:** Tier C · **Score:** 80/120 · [[D020 - Dispute-to-Listing Fixer (Deep Dive)|Deep dive]] · [[I020 - Dispute-to-Listing Fixer|Idea note]]

**Solution.** Cluster "not as described" disputes and fix the listing. The PayPal-side fix is cosmetic and ReasonWhy ships the loop.

**Hero demo moment.** Before/after listing copy.

**Prize target.** Not recommended as standalone.

**Biggest risk.** ReasonWhy; weak PayPal write-back.

**Day-1 gate.** -

### 9. Final-Price Agent / Overcapture (demoted)
**Tier:** Tier C · **Score:** 78/120 · [[D008 - Final-Price Agent (Overcapture) (Deep Dive)|Deep dive]] · [[I008 - Final-Price Agent (Overcapture)|Idea note]]

**Solution.** Capture up to 115% of the authorization when the final job price is higher. Valid as a consented-buffer branch in a holds build.

**Hero demo moment.** A JSON number (weak video).

**Prize target.** Branch only.

**Biggest risk.** Consent laws; sandbox enforcement unknown.

**Day-1 gate.** T8

### 10. Accessible Voice Checkout (demoted)
**Tier:** Tier C · **Score:** 75/120 · [[D084 - Accessible Voice Checkout (Deep Dive)|Deep dive]] · [[I084 - Accessible Voice Checkout|Idea note]]

**Solution.** Voice-first accessible checkout. PayPal's approval popup is cross-origin so the hardest step cannot be made accessible by a third party.

**Hero demo moment.** Voice order through to approval handoff.

**Prize target.** Better as a design pillar inside another build.

**Biggest risk.** PayU and Be My Eyes already ship adjacent products.

**Day-1 gate.** -
