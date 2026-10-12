---
title: "#19 Compelling Evidence Linker"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, eliminated]
up: "[[Idea Index]]"
id: 19
theme: E3
group: "Evidence economy"
desk_score: 73
final_score: 73
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #19 Compelling Evidence Linker

> Defends "unauthorized transaction" claims by linking the disputed payment to the same buyer's prior undisputed purchases.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** Disputes cluster

## Problem statement
Friendly fraud is merchants' largest dispute category (45% of chargebacks judged fraudulent).

## Proposed solution
Searches transaction history for matching payer, address, device/email patterns and builds a CE3.0-style narrative for PayPal evidence.

## Target users
Merchants with repeat customers.

## AI contribution
Entity matching, narrative drafting.

## PayPal integration
Transaction Search; Disputes evidence.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P18` Transaction Search / Reporting
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `A06` Entity matching and narrative drafting

## Competitors and prior art
Visa Compelling Evidence 3.0 tools, Chargeflow

Card-network CE3.0 automation exists via vendors.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal-native port of a known card-network technique.

## Feasibility
High; 3-hour Transaction Search lag is fine.

## MVP scope
Seeded history; dispute; evidence.

## Risks
Low novelty.

## Credible references
- [Mastercard/Datos 2025 State of Chargebacks — 261M→324M by 2028; 45% fraudulent](https://www.mastercard.com/us/en/news-and-trends/Insights/2025/2025-global-chargebacks-outlook.html) ✅
- [PayPal Transaction Search v1 (≤3h lag, 31-day window)](https://developer.paypal.com/docs/api/transaction-search/v1/) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **73** | 

_Why (desk):_ Useful, derivative.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
