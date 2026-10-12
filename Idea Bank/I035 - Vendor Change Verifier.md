---
title: "#35 Vendor Change Verifier"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, survivor]
up: "[[Idea Index]]"
id: 35
theme: E5
group: "Moment-of-send scams"
desk_score: 85
final_score: 85
status: SURVIVOR
verdict: desk-only
kills: []
---
# #35 Vendor Change Verifier

> Before a business pays a vendor whose payment details "changed", AI checks the request for BEC patterns and holds the payout until verified.

**Theme:** E5 Moment-of-send scams · **Group:** Moment-of-send scams · **Crowding on Devpost:** none

## Problem statement
Business email compromise is one of the costliest cybercrime categories reported to the FBI IC3.

## Proposed solution
Vendor master + Payouts; when a vendor's PayPal email changes via email request, AI analyses headers/language, requires out-of-band confirmation, then releases the payout.

## Target users
SMB finance teams paying vendors/contractors via PayPal Payouts.

## AI contribution
BEC language/header analysis, risk explanation.

## PayPal integration
Payouts; Payouts failure handling.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P11` Payouts (batch)
- `P13` Payouts failure handling and test values (UNCLAIMED, cancel, RETURNED, ERRPYO codes)
- `A05` Structured decision / classification (most common)

## Competitors and prior art
Eftsure, Trustpair

Vendor-verification platforms exist for bank payments (mid-market/enterprise).

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
SMB, PayPal Payouts-native.

## Feasibility
High.

## MVP scope
Spoofed change-request email → hold → verification → payout.

## Risks
Incumbents; need fresh IC3 figures verified.

## Credible references
- [FBI IC3 2024 report (BEC losses)](https://www.ic3.gov/AnnualReport/Reports/2024_IC3Report.pdf) ⚠️
- [PayPal Payouts sandbox test values (ERRPYO0xx)](https://developer.paypal.com/api/payouts/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **85** | 

_Why (desk):_ Solid B2B scam angle.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
