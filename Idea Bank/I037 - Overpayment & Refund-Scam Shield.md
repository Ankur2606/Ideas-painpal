---
title: "#37 Overpayment & Refund-Scam Shield"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, eliminated]
up: "[[Idea Index]]"
id: 37
theme: E5
group: "Moment-of-send scams"
desk_score: 62
final_score: 62
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #37 Overpayment & Refund-Scam Shield

> Flags orders that look like overpayment or "refund to a different account" scams before the merchant ships or refunds.

**Theme:** E5 Moment-of-send scams · **Group:** Moment-of-send scams · **Crowding on Devpost:** none

## Problem statement
Small merchants get targeted with overpayment/refund-redirect scams.

## Proposed solution
Order and message analysis; blocks refunds to non-original methods; explains.

## Target users
SMB merchants.

## AI contribution
Pattern classification.

## PayPal integration
Orders; Refunds (original method only); messages.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `P16` Refunds (full / partial)
- `A05` Structured decision / classification (most common)

## Competitors and prior art
Signifyd, Riskified

Fraud tools cover parts of this.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low-moderate.

## Feasibility
High.

## MVP scope
Scenario-based.

## Risks
Thin evidence; PayPal already refunds to original method.

## Credible references
- [FTC Consumer Sentinel Data Book 2024](https://www.ftc.gov/system/files/ftc_gov/pdf/csn-annual-data-book-2024.pdf) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 5 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **62** | 

_Why (desk):_ Weak evidence.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
