---
title: "#10 Backorder Reauth Manager"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, survivor]
up: "[[Idea Index]]"
id: 10
theme: E2
group: "Programmable holds"
desk_score: 70
final_score: 70
status: SURVIVOR
verdict: desk-only
kills: []
---
# #10 Backorder Reauth Manager

> AI manages authorisation, reauthorisation and capture timing for pre-orders and backorders so merchants never ship without funds or charge too early.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** none

## Problem statement
Merchants selling long-lead items either capture early (refund headaches, disputes) or authorise and lose the hold after the honour period.

## Proposed solution
Predicts ship dates from supplier messages, schedules reauthorisations inside the 29-day window, communicates with buyers, and voids if the item will miss the window.

## Target users
Makers, pre-order merchants.

## AI contribution
ETA extraction from supplier emails; scheduling decisions; buyer comms.

## PayPal integration
AUTHORIZE, reauthorize, capture, void; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `A01` Document / image extraction (OCR, validation)
- `A04` Forecasting / pricing suggestion
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
PreProduct, Shopify pre-order apps

Pre-order apps exist but typically capture upfront or use deposits.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Auth-window intelligence; niche.

## Feasibility
Reauth timing is hard to show in a 3-minute video without time travel; simulate.

## MVP scope
Simulated timeline with three orders and decisions.

## Risks
Niche; demo requires simulated time.

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **70** | 

_Why (desk):_ Clever but narrow.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
