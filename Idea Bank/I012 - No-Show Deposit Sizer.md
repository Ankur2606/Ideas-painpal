---
title: "#12 No-Show Deposit Sizer"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, survivor]
up: "[[Idea Index]]"
id: 12
theme: E2
group: "Programmable holds"
desk_score: 72
final_score: 72
status: SURVIVOR
verdict: desk-only
kills: []
---
# #12 No-Show Deposit Sizer

> AI predicts no-show risk per booking and sizes the PayPal authorisation accordingly — zero friction for reliable customers, real protection for risky slots.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** Booking cluster (~4)

## Problem statement
Flat deposits deter good customers; no deposit invites no-shows.

## Proposed solution
Risk model on booking signals sets hold size; capture the no-show fee if missed, void on attendance.

## Target users
Salons, clinics (non-medical), restaurants, tutors.

## AI contribution
Risk scoring, explanation of deposit size.

## PayPal integration
AUTHORIZE, partial capture, void; Vault.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P06` Vault v3 (saved payment tokens, payer-not-present charges)
- `A05` Structured decision / classification (most common)

## Competitors and prior art
OpenTable, Booksy, Tock

Booking platforms offer flat no-show fees and card holds.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Dynamic sizing; booking-agent entries already on Devpost (~4).

## Feasibility
High.

## MVP scope
Booking page + risk model + holds.

## Risks
Fairness/discrimination concerns in risk scoring; crowded booking cluster.

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **72** | 

_Why (desk):_ Weak evidence and fairness risk.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
