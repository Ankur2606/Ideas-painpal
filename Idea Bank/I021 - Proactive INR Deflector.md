---
title: "#21 Proactive INR Deflector"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, eliminated]
up: "[[Idea Index]]"
id: 21
theme: E3
group: "Evidence economy"
desk_score: 67
final_score: 67
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #21 Proactive INR Deflector

> Watches tracking events and messages buyers before "item not received" anxiety turns into a dispute.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** none on Devpost; mature market

## Problem statement
INR disputes cost fees and hurt ratios even when the parcel is simply late.

## Proposed solution
Tracking-aware agent sends proactive updates, offers small goodwill credits when delays exceed thresholds, and uploads proof of delivery when it lands.

## Target users
E-commerce SMBs.

## AI contribution
Delay prediction and message personalisation.

## PayPal integration
Tracking API; Refunds (goodwill); Disputes send-message.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P17` Shipment Tracking API (add tracking; releases holds)
- `P16` Refunds (full / partial)
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `A04` Forecasting / pricing suggestion
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
AfterShip, Route, Narvar, parcelLab

Post-purchase tracking-comms is a mature category.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal-dispute-aware, but mostly known.

## Feasibility
High.

## MVP scope
Simulated delays and messages.

## Risks
Low novelty.

## Credible references
- [PayPal Add Tracking API — 'fastest way to access on-hold funds'](https://developer.paypal.com/api/tracking/track-orders/integrate.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **67** | 

_Why (desk):_ Market already solved this.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
