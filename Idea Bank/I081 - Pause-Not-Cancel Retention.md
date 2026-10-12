---
title: "#81 Pause-Not-Cancel Retention"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, eliminated]
up: "[[Idea Index]]"
id: 81
theme: E8
group: "Subscription revenue ops"
desk_score: 65
final_score: 65
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #81 Pause-Not-Cancel Retention

> When a subscriber tries to cancel, an AI offers pause or downgrade and executes it through PayPal subscription suspend/revise.

**Theme:** E8 Failure-path intelligence · **Group:** Subscription revenue ops · **Crowding on Devpost:** none

## Problem statement
Voluntary churn ~2.34%/month (Recurly).

## Proposed solution
Cancellation flow with AI offers.

## Target users
Subscription SMBs.

## AI contribution
Offer selection.

## PayPal integration
Subscriptions suspend/revise/cancel.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `A05` Structured decision / classification (most common)

## Competitors and prior art
Churnkey, ProsperStack

Mature category.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
High.

## MVP scope
Cancel → pause.

## Risks
Dark-pattern optics.

## Credible references
- [Recurly churn benchmarks — involuntary 1.25%/mo](https://recurly.com/research/churn-rate-benchmarks/) ✅
- [FTC $2.5B Amazon settlement (subscription dark patterns)](https://www.ftc.gov/news-events/news/press-releases/2025/09/ftc-secures-historic-25-billion-settlement-against-amazon) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **65** | 

_Why (desk):_ Solved; dark-pattern risk.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
