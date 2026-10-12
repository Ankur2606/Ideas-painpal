---
title: "#60 Sandbox Scenario Studio"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, survivor]
up: "[[Idea Index]]"
id: 60
theme: E8
group: "Failure-path intelligence"
desk_score: 82
final_score: 82
status: SURVIVOR
verdict: desk-only
kills: []
---
# #60 Sandbox Scenario Studio

> Describe a business in a sentence; AI populates a PayPal sandbox with realistic customers, subscriptions, invoices, disputes and payout failures.

**Theme:** E8 Failure-path intelligence · **Group:** Failure-path intelligence · **Crowding on Devpost:** none

## Problem statement
Developers demo and test on empty sandboxes; PayPal's sandbox capabilities (dispute factory, payout test values) are under-known.

## Proposed solution
LLM persona generator + scripted API calls to seed realistic state; scenario library.

## Target users
Developers, DevRel, QA.

## AI contribution
Persona and scenario generation.

## PayPal integration
Orders, Invoicing, Subscriptions, Disputes sandbox factory, Payouts test values.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P15` Disputes sandbox factory (create, adjudicate)
- `P13` Payouts failure handling and test values (UNCLAIMED, cancel, RETURNED, ERRPYO codes)
- `P08` Invoicing v2 (create, send, partial payment)
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Stripe fixtures

Stripe CLI fixtures exist; nothing comparable for PayPal.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Fresh dev tool.

## Feasibility
High.

## MVP scope
"Online bakery with 3 months of history" → seeded sandbox.

## Risks
Developer-only audience.

## Credible references
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅
- [PayPal Payouts sandbox test values (ERRPYO0xx)](https://developer.paypal.com/api/payouts/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 8 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 7 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 9 | 
| **Total /120** | | **82** | 

_Why (desk):_ Useful dev tool; modest impact.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
