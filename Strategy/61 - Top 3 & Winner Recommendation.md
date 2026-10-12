---
title: "61 - Top 3 & Winner Recommendation"
type: strategy
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [top-3, recommendation]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Top 3 and winner recommendation

## The Top 3
| Rank | Idea | Final | Why it wins | Biggest risk | Decisive day-1 test |
|---|---|---|---|---|---|
| 1 | [[D023 - Seller Protection Preflight (Deep Dive)\|#23 Seller Protection Preflight]] (+ tracking release + evidence pack) | 89 | No Devpost entry found doing the pre-ship gate (DisputeDesk overlaps only the evidence module); starts from a verbatim PayPal policy clause; uses Orders, Transaction Search, Tracking and Disputes beyond checkout | AI reads as decorative next to a rules engine | T1 |
| 2 | [[Wrong Box - Combined Concept\|"Wrong Box"]] (#3 + #1 + #2) | 88 | Best 3-minute visual: one photo, two payers, two PayPal money movements | Provenant overlaps the liability angle | T2, T3 |
| 3 | [[D055 - Payout Failure Triage (Deep Dive)\|#55 Payout Failure Triage]] | 86 | Literally "test the unhappy paths"; compliance refusal is memorable | Failure branches may be mocks | T4 |

## Recommendation
**Build #23 first, and keep Wrong Box as the pre-agreed pivot.** Reasons:
1. Two of three council roles ranked #23 first, and the third ranked it third, so it never falls out of the set.
2. Innovation is a full fifth of the score. #23 is the only Top 3 member whose core mechanism has no same-hackathon near-duplicate (Wrong Box has Provenant; #55 has HoldWatch and ≥10 Payouts entries). Its evidence-pack module does overlap DisputeDesk, hence the advice to keep the gate as the headline.
3. Its PayPal usage is aligned with PayPal's own interest (fewer lost Seller Protection claims), which is the story DevRel judges say they want.

**Why not just pick the highest-scoring by the builder?** The builder's pick (Wrong Box) has the stronger video but the weaker novelty position, and its impact is forward-looking (no published agent-dispute volume). That is a closer call than the headline suggests: the scores are 89 vs 88.

## Decision tree after day 1 (⚠ inference)
- **T1 passes** (a sandbox capture exposes a `seller_protection` status that can change, and `/track` appears) → commit to #23.
- **T1 fails but T2 and T3 pass** → pivot to Wrong Box. #23's Tracking and Disputes-evidence modules are reusable, so little work is wasted.
- **T1 and T2 fail, T4 passes** → #55.
- **All three fail** → deep-dive the bench ([[44 - Bench Ideas Not Deep-Dived]]).

## What would change this recommendation
- A published competitor for #23 found late. A follow-up hunt found **DisputeDesk** (same hackathon, post-dispute evidence copilot with an AG Grid queue) but nothing doing the pre-ship preflight. See the addendum in [[D023 - Seller Protection Preflight (Deep Dive)]].
- Evidence that Seller Protection status is constant in sandbox (then the verdict must come from a rules table and the video must say so).
- PayPal shipping an equivalent seller-side pre-ship warning.

## Prize mapping
Max one Grand/HM plus one sponsor prize per team. #23 → Grand or Most Impactful, plus AG Grid. Wrong Box → Best Use of Agentic Commerce or Best Demo Delivery, plus AG Grid or Channel3. #55 → Best Use of PayPal + AI, plus AG Grid.
