---
title: "#41 Shared Subscription Steward"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E6, eliminated]
up: "[[Idea Index]]"
id: 41
theme: E6
group: "Human delegation"
desk_score: 60
final_score: 60
status: ELIMINATED
verdict: desk-only
kills: [K2, K4]
---
# #41 Shared Subscription Steward

> Family-plan members each pay their share through their own PayPal subscription; AI handles joins, leaves and price changes.

**Theme:** E6 Human delegation · **Group:** Human delegation · **Crowding on Devpost:** Group-pay cluster

## Problem statement
Shared plans create awkward reimbursement chasing.

## Proposed solution
Organiser creates plan; members subscribe to share; AI rebalances on member changes.

## Target users
Friend groups, households.

## AI contribution
Rebalancing, comms.

## PayPal integration
Subscriptions (revise quantity/price).

**Primitives used** (see [[30 - Primitives Legend]]):
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Splitwise, Spliiit, Together Price

Subscription-sharing marketplaces exist; ToS issues.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
High.

## MVP scope
Plan + 3 members.

## Risks
Group-pay cluster; streaming ToS.

## Credible references
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 3 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **60** | 

_Why (desk):_ Weak.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended; `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
