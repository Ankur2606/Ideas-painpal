---
title: "#54 Decline Whisperer"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, eliminated]
up: "[[Idea Index]]"
id: 54
theme: E8
group: "Failure-path intelligence"
desk_score: 79
final_score: 79
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #54 Decline Whisperer

> When a PayPal subscription payment fails, AI picks the retry moment and a personalised rescue message — including switching to a wallet that doesn't expire like a card.

**Theme:** E8 Failure-path intelligence · **Group:** Failure-path intelligence · **Crowding on Devpost:** none on Devpost; mature market

## Problem statement
Involuntary churn runs ~1.25% per month (Recurly), roughly a third of all churn.

## Proposed solution
Webhook-driven dunning agent with retry timing model, message personalisation and payment-method update flow.

## Target users
Subscription SMBs.

## AI contribution
Retry timing, message generation.

## PayPal integration
Subscriptions (BILLING.SUBSCRIPTION.PAYMENT.FAILED), revise; Vault; Mock-Response for demos.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `P20` Webhooks (events, retries, verification)
- `P06` Vault v3 (saved payment tokens, payer-not-present charges)
- `P21` PayPal-Mock-Response header (sandbox fault injection)
- `A04` Forecasting / pricing suggestion
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Churnkey, Butter Payments, Recurly, Stripe Smart Retries

Mature dunning market.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal-wallet rescue angle only.

## Feasibility
High.

## MVP scope
Simulated failure → rescue → recovered.

## Risks
Low novelty.

## Credible references
- [Recurly churn benchmarks — involuntary 1.25%/mo](https://recurly.com/research/churn-rate-benchmarks/) ✅
- [PayPal Webhooks overview (25 retries / 3 days)](https://developer.paypal.com/api/webhooks/overview) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **79** | 

_Why (desk):_ Market is mature.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
