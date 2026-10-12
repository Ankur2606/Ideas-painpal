---
title: "#57 Webhook Drift Doctor"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, eliminated]
up: "[[Idea Index]]"
id: 57
theme: E8
group: "Failure-path intelligence"
desk_score: 67
final_score: 67
status: ELIMINATED
verdict: desk-only
kills: [K6]
---
# #57 Webhook Drift Doctor

> Detects missed or unverifiable PayPal webhooks by reconciling against Transaction Search, and explains the root cause.

**Theme:** E8 Failure-path intelligence · **Group:** Failure-path intelligence · **Crowding on Devpost:** none

## Problem statement
Webhook delivery and verification issues are recurring developer pain.

## Proposed solution
Monitor + reconciliation + AI diagnosis.

## Target users
Developers.

## AI contribution
Diagnosis.

## PayPal integration
Webhooks; Transaction Search.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P20` Webhooks (events, retries, verification)
- `P18` Transaction Search / Reporting
- `A14` Diagnosis / code transformation

## Competitors and prior art
Hookdeck, Svix

Webhook infrastructure tools exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal-specific reconciliation.

## Feasibility
High.

## MVP scope
Drop events → detect → explain.

## Risks
Narrow; dashboard demo.

## Credible references
- [PayPal Webhooks overview (25 retries / 3 days)](https://developer.paypal.com/api/webhooks/overview) ✅
- [PayPal Transaction Search v1 (≤3h lag, 31-day window)](https://developer.paypal.com/docs/api/transaction-search/v1/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 4 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **67** | 

_Why (desk):_ Narrow dev utility.

**Kill criteria triggered:** `K6` Infrastructure with no watchable demo. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
