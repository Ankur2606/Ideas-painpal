---
title: "#82 Win-Back Agent"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, eliminated]
up: "[[Idea Index]]"
id: 82
theme: E8
group: "Subscription revenue ops"
desk_score: 65
final_score: 65
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #82 Win-Back Agent

> Re-engages cancelled PayPal subscribers with tailored offers and a one-click resubscribe link.

**Theme:** E8 Failure-path intelligence · **Group:** Subscription revenue ops · **Crowding on Devpost:** none

## Problem statement
Reactivation is cheaper than acquisition.

## Proposed solution
Segment, message, resubscribe link.

## Target users
Subscription SMBs.

## AI contribution
Personalisation.

## PayPal integration
Subscriptions; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `P20` Webhooks (events, retries, verification)
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Churnkey

Category exists; MACH winner SilentWatch did churn reactivation.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
High.

## MVP scope
Cancelled list → offers.

## Risks
Low novelty.

## Credible references


## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **65** | 

_Why (desk):_ Derivative.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
