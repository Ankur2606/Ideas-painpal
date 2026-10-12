---
title: "#13 Pricing-Error Shield"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, survivor]
up: "[[Idea Index]]"
id: 13
theme: E2
group: "Programmable holds"
desk_score: 83
final_score: 83
status: SURVIVOR
verdict: desk-only
kills: []
---
# #13 Pricing-Error Shield

> Authorise first, capture after an AI sanity check — so a $1 typo on a $100 product doesn't ship 400 orders.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** none

## Problem statement
Mispricing incidents can wipe out a small merchant overnight; once captured, cancelling triggers refunds and disputes.

## Proposed solution
Merchant switches to AUTHORIZE; an anomaly agent compares each order against catalog history, competitor prices and margin, holds suspicious orders for one-click review, and voids or captures in bulk.

## Target users
SMB e-commerce merchants.

## AI contribution
Price anomaly detection; order clustering (viral mispricing spikes).

## PayPal integration
AUTHORIZE, capture/void; Catalog products; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P30` Catalog products / billing plans
- `A15` Anomaly detection

## Competitors and prior art
Shopify Flow, Signifyd

Fraud tools score buyers, not merchant-side pricing mistakes.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Merchant-error protection is unusual.

## Feasibility
High.

## MVP scope
Seed catalog, trigger a spike of $1 orders, shield holds them, bulk void.

## Risks
Evidence is anecdotal (no dataset on pricing-error losses).

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 7 | 
| Demo | ×2 | 8 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **83** | 

_Why (desk):_ Fun demo; weak evidence.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
