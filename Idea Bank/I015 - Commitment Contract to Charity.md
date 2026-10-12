---
title: "#15 Commitment Contract to Charity"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, eliminated]
up: "[[Idea Index]]"
id: 15
theme: E2
group: "Programmable holds"
desk_score: 71
final_score: 71
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #15 Commitment Contract to Charity

> Put money on a goal; if AI-verified evidence says you missed it, the hold is captured as a donation.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** none

## Problem statement
Commitment devices work but require trusting the app with money upfront.

## Proposed solution
AUTHORIZE a stake; AI checks evidence (photos, app exports) against the goal; void on success, capture + donate on failure.

## Target users
Individuals; workplace wellness challenges.

## AI contribution
Evidence verification with rubric.

## PayPal integration
AUTHORIZE/void/capture; Donate SDK or Payouts to charity.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P29` Donate SDK / charity flows
- `A02` Classification with explanation / vision estimation
- `A13` Vision verification / evidence narrative

## Competitors and prior art
Beeminder, stickK, Forfeit

Established commitment apps exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Hold-based stake and charity routing.

## Feasibility
High, but 29-day limit caps goal length.

## MVP scope
One 7-day goal simulated.

## Risks
Low impact evidence; gamification framing.

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 3 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **71** | 

_Why (desk):_ Charming, low impact.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
