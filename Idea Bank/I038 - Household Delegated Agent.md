---
title: "#38 Household Delegated Agent"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E6, eliminated]
up: "[[Idea Index]]"
id: 38
theme: E6
group: "Human delegation"
desk_score: 81
final_score: 81
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #38 Household Delegated Agent

> A family wallet where each member's shopping agent spends from one PayPal account under its own scoped rules — UPI Circle, for PayPal.

**Theme:** E6 Human delegation · **Group:** Human delegation · **Crowding on Devpost:** Spend-gate cluster (~13)

## Problem statement
Western wallets are single-principal; India's UPI Circle lets a primary user delegate to a secondary user or agent. Families share accounts or cards insecurely.

## Proposed solution
Primary vaults PayPal; each delegate (teen-adult child, partner, caregiver, or their agent) gets a scoped mandate (merchants, categories, caps); AI enforces and explains; the primary sees an approvals feed.

## Target users
Households, caregivers.

## AI contribution
Policy compilation from natural language; purchase categorisation; anomaly alerts.

## PayPal integration
Vault payer-not-present; Orders; Log in with PayPal for delegates; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P06` Vault v3 (saved payment tokens, payer-not-present charges)
- `P01` Orders v2 (create / capture / get)
- `P25` Log in with PayPal
- `P20` Webhooks (events, retries, verification)
- `A16` Policy / rule reasoning with cited clauses
- `A05` Structured decision / classification (most common)

## Competitors and prior art
UPI Circle, Greenlight, Ramp Agent Cards

Family cards exist (Greenlight) and agent spend controls exist; the multi-principal PayPal angle is new, but it reads as a spend gate.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Multi-principal delegation rather than single-agent limits.

## Feasibility
High.

## MVP scope
Primary + 2 delegates + agent purchases under different rules.

## Risks
Spend-gate cluster; PayPal requires 18+ account holders (delegates must be adults).

## Credible references
- [Razorpay — agentic payments & NPCI (UPI Reserve Pay)](https://razorpay.com/blog/agentic-payments-and-npci/) ✅
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 8 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **81** | 

_Why (desk):_ Interesting framing inside a crowded cluster.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
