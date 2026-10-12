---
title: "#63 Price-Protection Autopilot"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, eliminated]
up: "[[Idea Index]]"
id: 63
theme: E3
group: "After the purchase"
desk_score: 71
final_score: 71
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #63 Price-Protection Autopilot

> Merchants promise 14-day price protection; an agent watches their own prices and auto-issues partial refunds when they drop.

**Theme:** E3 Evidence economy · **Group:** After the purchase · **Crowding on Devpost:** none

## Problem statement
Shoppers delay purchases fearing price drops; manual price-adjustment requests burden support.

## Proposed solution
Watches catalog prices; computes eligible partial refunds; issues via Refunds API; emails buyers.

## Target users
Merchants.

## AI contribution
Eligibility; messaging.

## PayPal integration
Refunds (partial); Catalog.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P16` Refunds (full / partial)
- `P30` Catalog products / billing plans
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Shopify price-protection apps

Some e-commerce apps offer price-drop guarantees.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Moderate.

## Feasibility
High.

## MVP scope
Price drop → partial refunds.

## Risks
Weak evidence.

## Credible references


## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 3 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **71** | 

_Why (desk):_ Weak evidence.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
