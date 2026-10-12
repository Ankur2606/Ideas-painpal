---
title: "#18 Service-Proof Ledger"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor]
up: "[[Idea Index]]"
id: 18
theme: E3
group: "Evidence economy"
desk_score: 79
final_score: 79
status: SURVIVOR
verdict: desk-only
kills: []
---
# #18 Service-Proof Ledger

> Freelancer deliverables, approvals and change requests become dispute-ready evidence — because Seller Protection doesn't cover services.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** Escrow/disputes adjacent

## Problem statement
85% of freelancers are paid late at least sometimes; PayPal Seller Protection covers physical goods, leaving services exposed to SNAD disputes.

## Proposed solution
Invoice-linked workspace where client approvals, file deliveries and messages are timestamped; AI maps them to invoice line items and builds the evidence narrative when disputes arrive.

## Target users
Freelancers and micro-agencies invoicing via PayPal.

## AI contribution
Mapping deliverables to scope, narrative drafting.

## PayPal integration
Invoicing; Disputes evidence; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P08` Invoicing v2 (create, send, partial payment)
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P20` Webhooks (events, retries, verification)
- `A01` Document / image extraction (OCR, validation)
- `A06` Entity matching and narrative drafting

## Competitors and prior art
Bonsai, HoneyBook, Upwork

Freelancer suites manage contracts; marketplaces offer escrow at 10%+ fees.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Evidence-first for off-platform freelancers.

## Feasibility
High.

## MVP scope
Invoice → deliverables → client approval → dispute → evidence.

## Risks
Escrow-adjacent framing; evidence alone may not win service disputes.

## Credible references
- [Remote 2025 — 85% of freelancers paid late sometimes](https://remote.com/blog/contractor-management/reversing-late-payment-culture) ✅
- [PayPal Seller Protection Program (ship-to address rule, SNAD excluded, intangibles evidence)](https://www.paypal.com/us/legalhub/paypal/seller-protection) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **79** | 

_Why (desk):_ Real pain; moderate novelty.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
