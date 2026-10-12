---
title: "#11 Tipping-Point Group Buy"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, survivor]
up: "[[Idea Index]]"
id: 11
theme: E2
group: "Programmable holds"
desk_score: 74
final_score: 74
status: SURVIVOR
verdict: desk-only
kills: []
---
# #11 Tipping-Point Group Buy

> Many buyers authorise; capture fires only if the group hits the supplier's minimum order by the deadline — an AI negotiates the bulk price.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** Group-pay cluster (~6)

## Problem statement
Small buyers can't reach wholesale minimums; crowdfunding captures early and refunds messily.

## Proposed solution
Each participant authorises; an AI agent negotiates tiers with the supplier; at the deadline, all captures run or all holds void.

## Target users
Community buying groups, makers validating demand.

## AI contribution
Supplier negotiation, demand forecasting, group comms.

## PayPal integration
AUTHORIZE holds; batch capture/void; Payouts to supplier; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P11` Payouts (batch)
- `A07` Multi-agent negotiation
- `A04` Forecasting / pricing suggestion

## Competitors and prior art
Kickstarter, BackerKit, Pinduoduo

Crowdfunding and social commerce exist; auth-until-threshold is a known pattern.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Mostly the auth-hold mechanism; group-pay is crowded.

## Feasibility
Medium.

## MVP scope
5 sandbox buyers; threshold met → captures; missed → voids.

## Risks
Group-pay cluster (~6) on Devpost.

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **74** | 

_Why (desk):_ Fine, unremarkable.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
