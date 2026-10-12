---
title: "#62 Returns-Abuse Pattern Detector"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, eliminated]
up: "[[Idea Index]]"
id: 62
theme: E3
group: "After the purchase"
desk_score: 67
final_score: 67
status: ELIMINATED
verdict: desk-only
kills: [K6]
---
# #62 Returns-Abuse Pattern Detector

> Flags wardrobing and serial-return patterns across a merchant's PayPal refunds and disputes.

**Theme:** E3 Evidence economy · **Group:** After the purchase · **Crowding on Devpost:** none

## Problem statement
Return fraud and abuse cost US retailers about $100B (Appriss).

## Proposed solution
Pattern detection over refunds/disputes; policy suggestions.

## Target users
Merchants.

## AI contribution
Anomaly detection.

## PayPal integration
Transaction Search; Disputes; Refunds.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P18` Transaction Search / Reporting
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `A15` Anomaly detection

## Competitors and prior art
Appriss Retail, Signifyd Abuse Prevention

Incumbents in enterprise retail.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
SMB PayPal version.

## Feasibility
High.

## MVP scope
Seeded data.

## Risks
Table demo.

## Credible references
- [Appriss 2026 — $100B preventable return fraud/abuse](https://apprissretail.com/2026-total-retail-loss-benchmark-report/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 4 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **67** | 

_Why (desk):_ Incumbent space, table demo.

**Kill criteria triggered:** `K6` Infrastructure with no watchable demo. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
