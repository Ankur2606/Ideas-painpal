---
title: "#17 Digital-Goods Proof Ledger"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor]
up: "[[Idea Index]]"
id: 17
theme: E3
group: "Evidence economy"
desk_score: 79
final_score: 79
status: SURVIVOR
verdict: desk-only
kills: []
---
# #17 Digital-Goods Proof Ledger

> Logs delivery and access events for digital products and turns them into the "compelling evidence" PayPal asks for on intangible goods.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** Disputes cluster

## Problem statement
PayPal's Seller Protection for intangibles needs a system of record showing the item was sent and accessed; small digital sellers rarely have one.

## Proposed solution
Lightweight delivery service (signed download links, license activation, access pings) that, on dispute, auto-builds a timeline and posts it as evidence.

## Target users
Creators selling courses, templates, software licenses.

## AI contribution
Timeline narrative and relevance filtering of logs.

## PayPal integration
Orders; Disputes provide-evidence; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P20` Webhooks (events, retries, verification)
- `A01` Document / image extraction (OCR, validation)

## Competitors and prior art
Gumroad, Lemon Squeezy, Sellfy

Digital storefronts keep logs but lock them inside their platform.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Portable, PayPal-dispute-native.

## Feasibility
High.

## MVP scope
Sell a template, access it, open dispute, evidence posted.

## Risks
Modest novelty; limited AI depth.

## Credible references
- [PayPal Seller Protection Program (ship-to address rule, SNAD excluded, intangibles evidence)](https://www.paypal.com/us/legalhub/paypal/seller-protection) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅
- [Chargebacks911 2026 Field Report — SMBs represent only 60.3%; evidence collection #1 pain](https://chargebacks911.com/chargeback-field-report/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **79** | 

_Why (desk):_ Solid utility, low novelty.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
