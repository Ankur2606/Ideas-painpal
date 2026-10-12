---
title: "#23 Seller Protection Preflight"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor, deep-dived]
up: "[[Idea Index]]"
id: 23
theme: E3
group: "Evidence economy"
desk_score: 97
final_score: 89
status: SURVIVOR
verdict: advance-with-changes
kills: []
---
# #23 Seller Protection Preflight

> Before a seller ships, AI checks every PayPal Seller Protection condition — and catches the "please ship to my cousin's address" scam.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** none

## Problem statement
Seller Protection is voided if the seller ships anywhere other than the address on the Transaction Details page, or if a buyer-arranged shipment is redirected; scammers exploit this by messaging new addresses. Sellers often learn the rules only after losing.

## Proposed solution
For each paid order, pulls the transaction address, reads buyer messages for address-change or off-platform requests, checks proof-of-delivery requirements for the carrier and value, flags violations, and uploads tracking when the label is created.

## Target users
Small sellers on PayPal (marketplace, social commerce).

## AI contribution
Message intent detection (address change, urgency, off-platform pay), rule reasoning with cited policy clauses, label OCR.

## PayPal integration
Orders/transaction details (shipping address); Tracking API; Disputes evidence later; Seller Protection policy.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P32` Seller Protection policy rules
- `P17` Shipment Tracking API (add tracking; releases holds)
- `P18` Transaction Search / Reporting
- `P01` Orders v2 (create / capture / get)
- `A05` Structured decision / classification (most common)
- `A01` Document / image extraction (OCR, validation)
- `A16` Policy / rule reasoning with cited clauses

## Competitors and prior art
ShipStation, Shippo

Shipping tools validate addresses for deliverability, not for PayPal Seller Protection eligibility or scam patterns. No direct competitor found.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D023 - Seller Protection Preflight (Deep Dive)]].

## Differentiation
Turns a dense PayPal policy into an automatic preflight — prevention, not representment.

## Feasibility
High; rules are public, messages can be simulated.

## MVP scope
Three orders (clean; address-change scam; high-value without adequate proof) with preflight verdicts and fixes.

## Risks
Policy varies by region (US version used); must not give legal guarantees.

## Credible references
- [PayPal Seller Protection Program (ship-to address rule, SNAD excluded, intangibles evidence)](https://www.paypal.com/us/legalhub/paypal/seller-protection) ✅
- [PayPal Add Tracking API — 'fastest way to access on-hold funds'](https://developer.paypal.com/api/tracking/track-orders/integrate.md) ✅
- [UK Finance Annual Fraud Report 2026 — APP £576.4M; 175,809 purchase scams](https://www.ukfinance.org.uk/system/files/2026-06/UK%20Finance%20Fraud%20Report%202026.pdf) ✅
- [FTC Consumer Sentinel Data Book 2024](https://www.ftc.gov/system/files/ftc_gov/pdf/csn-annual-data-book-2024.pdf) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 8 | 8 |
| Design | ×2 | 8 | 8 |
| Impact | ×2 | 8 | 6 |
| Innovation | ×2 | 8 | 7 |
| Demo | ×2 | 8 | 8 |
| Feasibility | ×1 | 9 | 8 |
| Risk⁻¹ | ×1 | 8 | 7 |
| **Total /120** | | **97** | **89** |

_Why (desk):_ Concrete PayPal-specific prevention with scam relevance; no competitor found.

**Kill criteria:** none triggered.

## Deep-dive verdict: advance-with-changes
A before-shipping PayPal Seller Protection gate: real API signals plus AI that reads 'ship to my cousin' messages and OCRs labels. Advance, paired with tracking-upload hold release; drop the signature claim and fill in scam evidence.

_Score changes:_ Primary-verified: US (Jan 2026) and UK (Jul 2026) terms require shipping to the Transaction Details address, void protection on redirect, recommend against buyer-arranged shipping, and exclude SNAD. There is NO signature/value threshold, so drop it. APIs are confirmed in OpenAPI: Orders v2 purchase_units[].shipping, capture seller_protection.status + dispute_categories, Transaction Search shipping_info, protection_eligibility, address_status and transaction_note, plus Orders track. Impact is lowered: no quantified scam frequency and no verified user voices. Innovation is lowered slightly because the competitor hunt was incomplete (search budget exhausted) and label-from-order printing already enforces the address implicitly. No Devpost overlap in ~144 entries.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
