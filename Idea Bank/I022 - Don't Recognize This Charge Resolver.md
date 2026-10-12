---
title: "#22 'Don't Recognize This Charge' Resolver"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor]
up: "[[Idea Index]]"
id: 22
theme: E3
group: "Evidence economy"
desk_score: 81
final_score: 81
status: SURVIVOR
verdict: desk-only
kills: []
---
# #22 "Don't Recognize This Charge" Resolver

> A buyer-facing lookup reachable from the soft descriptor that identifies the purchase and offers refund/cancel before the buyer calls their bank.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** Disputes cluster

## Problem statement
Unrecognised descriptors drive friendly-fraud disputes; Reddit merchants report buyers dispute before contacting them.

## Proposed solution
Short URL in the soft descriptor → conversational lookup by email/amount/date → shows receipt and offers cancel/refund via the merchant's rules.

## Target users
Subscription and digital merchants.

## AI contribution
Fuzzy order matching; conversational resolution within policy.

## PayPal integration
Orders soft_descriptor; Transaction Search; Refunds; Subscriptions cancel.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P31` custom_id / invoice_id metadata binding
- `P18` Transaction Search / Reporting
- `P16` Refunds (full / partial)
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `A06` Entity matching and narrative drafting
- `A16` Policy / rule reasoning with cited clauses

## Competitors and prior art
Ethoca Consumer Clarity, Verifi Order Insight

Card networks run issuer-side order-insight programmes; not for PayPal SMBs' own descriptors.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Merchant-owned deflection page.

## Feasibility
High.

## MVP scope
Lookup page + refund in sandbox.

## Risks
Moderate novelty.

## Credible references
- [Chargebacks911 2026 Field Report — SMBs represent only 60.3%; evidence collection #1 pain](https://chargebacks911.com/chargeback-field-report/) ✅
- [Mastercard/Datos 2025 State of Chargebacks — 261M→324M by 2028; 45% fraudulent](https://www.mastercard.com/us/en/news-and-trends/Insights/2025/2025-global-chargebacks-outlook.html) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **81** | 

_Why (desk):_ Practical, moderate novelty.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
