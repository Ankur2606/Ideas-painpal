---
title: "#9 Rental Deposit Inspector"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, survivor, deep-dived]
up: "[[Idea Index]]"
id: 9
theme: E2
group: "Programmable holds"
desk_score: 92
final_score: 81
status: SURVIVOR
verdict: demote
kills: []
---
# #9 Rental Deposit Inspector

> Damage deposits as PayPal authorisations; AI compares check-out and check-in photos and partially captures only what the evidence supports.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** Light (sponsor-suggested rental scheduling)

## Problem statement
Small rental businesses (equipment, cameras, bikes, costumes) either skip deposits or argue about damage, and deposit disputes become PayPal disputes.

## Proposed solution
Deposit = AUTHORIZE hold. Staff photograph the item at hand-over and return; a vision model diff-highlights new damage, estimates cost from a price table, and proposes a partial capture with an annotated evidence page the renter can contest before capture.

## Target users
Rental SMBs; peer-to-peer rental platforms.

## AI contribution
Multimodal before/after damage detection, cost estimation, evidence report generation.

## PayPal integration
Orders AUTHORIZE, partial capture, void, reauthorize for longer rentals; Disputes evidence pre-packaged; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `A02` Classification with explanation / vision estimation
- `A12` Eligibility reasoning and messaging
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)

## Competitors and prior art
Booqable, Rentle, Airbnb AirCover

Rental software handles bookings and deposits; host-protection programmes are platform-specific; AI damage diffing tied to a partial capture is not standard.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D009 - Rental Deposit Inspector (Deep Dive)]].

## Differentiation
Evidence-first deposit capture that is fair to both sides and dispute-ready.

## Feasibility
High for demo (curated photo pairs); production accuracy is harder.

## MVP scope
Two rentals (clean return → void; scratched lens → partial capture with annotated evidence).

## Risks
Bryntum's page suggests "equipment rental locked on payment" (some duplication); vision accuracy.

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅
- [Devpost Bryntum sponsor page (suggested ideas)](https://paypalaihackathon.devpost.com/details/bryntum) ✅
- [Mastercard/Datos 2025 State of Chargebacks — 261M→324M by 2028; 45% fraudulent](https://www.mastercard.com/us/en/news-and-trends/Insights/2025/2025-global-chargebacks-outlook.html) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 8 | 8 |
| Design | ×2 | 8 | 8 |
| Impact | ×2 | 6 | 6 |
| Innovation | ×2 | 7 | 4 |
| Demo | ×2 | 9 | 8 |
| Feasibility | ×1 | 8 | 7 |
| Risk⁻¹ | ×1 | 8 | 6 |
| **Total /120** | | **92** | **81** |

_Why (desk):_ Very strong demo; impact evidence is indirect.

**Kill criteria:** none triggered.

## Deep-dive verdict: demote
PayPal mechanics work for short rentals, but novelty collapses: AI damage diffing + partial hold capture both exist; keep only as a component.

_Score changes:_ AI before/after rental damage detection is a crowded category (Texada, CloudRent, switchlabs Verify, Roboflow, Hertz/UVeye) and public repo RentProof (Claude + Render) does the AI half nearly identically; TWICE/Booqable/ChargeAutomation already do auth-hold deposits with partial capture. Payments v2 reference says reauth allowed only once (day 4-29), contradicting guide's 'multiple'; PayPal partial capture needs account enablement; Hertz AI-billing backlash raises framing risk.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
