---
title: "#14 Delivery-Confirmed Capture"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, eliminated]
up: "[[Idea Index]]"
id: 14
theme: E2
group: "Programmable holds"
desk_score: 72
final_score: 72
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #14 Delivery-Confirmed Capture

> New sellers authorise at order and capture on carrier-confirmed delivery, so buyers trust unknown shops and sellers avoid new-account holds.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** Escrow cluster (~11)

## Problem statement
New sellers face 21-day holds; buyers distrust unknown shops (19% of abandoners don't trust the site with card details).

## Proposed solution
Authorise; upload tracking via Tracking API; AI watches carrier status and captures on delivery; reauthorises if transit runs long.

## Target users
New marketplace and social sellers.

## AI contribution
Carrier event interpretation; exception handling messages.

## PayPal integration
AUTHORIZE/capture/reauth; Tracking API.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P17` Shipment Tracking API (add tracking; releases holds)
- `A01` Document / image extraction (OCR, validation)

## Competitors and prior art
Escrow.com, Trustap

Escrow services exist; AI-judge escrow is the second most crowded Devpost cluster (~11).

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Uses native auth rather than escrow, but reads as escrow.

## Feasibility
Medium (tracking simulation).

## MVP scope
Order → tracking → simulated delivery → capture.

## Risks
Escrow cluster; auth windows shorter than slow shipping.

## Credible references
- [PayPal — funds availability, holds up to 21 days](https://www.paypal.com/us/brc/article/funds-availability) ✅
- [Baymard — 70.22% cart abandonment; reasons](https://baymard.com/lists/cart-abandonment-rate) ✅
- [PayPal Add Tracking API — 'fastest way to access on-hold funds'](https://developer.paypal.com/api/tracking/track-orders/integrate.md) ✅
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **72** | 

_Why (desk):_ Reads as escrow in a crowded field.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
