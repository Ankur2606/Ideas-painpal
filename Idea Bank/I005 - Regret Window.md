---
title: "#5 Regret Window"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor]
up: "[[Idea Index]]"
id: 5
theme: E1
group: "Agent purchase liability"
desk_score: 87
final_score: 87
status: SURVIVOR
verdict: desk-only
kills: []
---
# #5 Regret Window

> Agent purchases are authorised, not captured, for a configurable cooling-off window; the human can veto from a push notification and the hold is voided.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** Spend-gate cluster (~13)

## Problem statement
Only 9% of consumers would let an agent pay (Accenture); 35% want approval before completion (RTB House). Pre-approval of every purchase kills the point of delegation.

## Proposed solution
Agents create AUTHORIZE-intent orders; the user receives a digest with an AI-written "why I bought this"; silence captures at window end, veto voids. Reauthorisation handles longer windows inside the 29-day period.

## Target users
Consumers delegating routine purchases; families.

## AI contribution
Rationale summary, risk scoring that shortens/extends the window per purchase.

## PayPal integration
Orders AUTHORIZE; capture/void/reauthorize; webhooks; Vault for payer-not-present.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P06` Vault v3 (saved payment tokens, payer-not-present charges)
- `P20` Webhooks (events, retries, verification)
- `A05` Structured decision / classification (most common)
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Stripe agent guardrails, Ramp Agent Cards, Link agent wallet

Spend-limit and approval layers exist (Stripe preview, Ramp) and ~13 Devpost entries are spend gates. The regret window (post-decision veto on a native hold) is a twist, not a new category.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Uses PayPal's native auth-hold semantics as the consent mechanism instead of a pre-purchase gate.

## Feasibility
High; all sandbox.

## MVP scope
Agent places 3 orders; dashboard with countdowns; veto voids in sandbox; capture on expiry.

## Risks
Crowded cluster; merchants dislike uncaptured auths for perishables.

## Credible references
- [Accenture 2026 — only 9% would let an agent pay](https://www.thediplomat.ro/2026/06/09/accenture-study-74-of-consumers-are-ready-to-let-an-ai-agent-shop-on-their-behalf/) ⚠️
- [RTB House survey — 35% want approval before agent completes](https://www.digitaltransactions.net/consumers-like-ai-for-product-discovery-but-dont-fully-trust-it-for-purchases/) ⚠️
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅
- [Stripe Sessions 2026 announcements (agent guardrails, Issuing for agents)](https://stripe.com/au/blog/everything-we-announced-at-sessions-2026) ✅
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 8 | 
| Design | ×2 | 8 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 8 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **87** | 

_Why (desk):_ Clean, buildable, but lives in the most crowded cluster.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
