---
title: "#80 Price-Change Rollout Agent"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, survivor]
up: "[[Idea Index]]"
id: 80
theme: E8
group: "Subscription revenue ops"
desk_score: 73
final_score: 73
status: SURVIVOR
verdict: desk-only
kills: []
---
# #80 Price-Change Rollout Agent

> Raising prices? AI segments subscribers, predicts churn, drafts notices, and offers downgrades via PayPal plan revisions.

**Theme:** E8 Failure-path intelligence · **Group:** Subscription revenue ops · **Crowding on Devpost:** none

## Problem statement
Price changes are a top churn trigger; FTC's $2.5B Amazon settlement raised the stakes on subscription transparency.

## Proposed solution
Segment by usage/tenure, notice generation, downgrade/annual offers via subscription revise, monitor acceptances.

## Target users
Subscription SMBs.

## AI contribution
Churn prediction, copy.

## PayPal integration
Subscriptions plan price change, revise.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `P20` Webhooks (events, retries, verification)
- `A05` Structured decision / classification (most common)
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Paddle Retain, ProfitWell

Retention analytics exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal plan-change workflow.

## Feasibility
High.

## MVP scope
50 synthetic subscribers.

## Risks
Moderate novelty.

## Credible references
- [FTC $2.5B Amazon settlement (subscription dark patterns)](https://www.ftc.gov/news-events/news/press-releases/2025/09/ftc-secures-historic-25-billion-settlement-against-amazon) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **73** | 

_Why (desk):_ Useful, modest.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
