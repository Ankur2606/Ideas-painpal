---
title: "#91 Event Vendor Settlement"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, eliminated]
up: "[[Idea Index]]"
id: 91
theme: E9
group: "Trades & B2B ops"
desk_score: 59
final_score: 59
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #91 Event Vendor Settlement

> Markets and festivals collect stall fees and settle revenue shares with vendors automatically.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Trades & B2B ops · **Crowding on Devpost:** none

## Problem statement
Organisers reconcile vendor shares manually.

## Proposed solution
Multiparty checkout or Payouts after AI reconciliation.

## Target users
Event organisers.

## AI contribution
Reconciliation.

## PayPal integration
Multiparty (partner gated) or Payouts.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P26` Multiparty / platform (partner-gated)
- `P11` Payouts (batch)
- `A06` Entity matching and narrative drafting

## Competitors and prior art
Eventeny

Vendor management tools exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
Low-medium (multiparty needs partner enablement).

## MVP scope
Payout-based variant.

## Risks
Gated multiparty.

## Credible references
- [PayPal multiseller payments (10 purchase units, platform_fees)](https://developer.paypal.com/platforms/checkout/standard/customize/multiseller-payments.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 3 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 6 | 
| Risk⁻¹ | ×1 | 5 | 
| **Total /120** | | **59** | 

_Why (desk):_ Weak evidence; gated APIs.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
