---
title: "#4 Rogue-Agent Claim Verifier"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor]
up: "[[Idea Index]]"
id: 4
theme: E1
group: "Agent purchase liability"
desk_score: 76
final_score: 76
status: SURVIVOR
verdict: desk-only
kills: []
---
# #4 Rogue-Agent Claim Verifier

> Merchant-side defence against the new friendly-fraud excuse — "my agent went rogue".

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** Disputes cluster

## Problem statement
Worldpay names unverifiable "my agent did it" claims as a new friendly-fraud vector; merchants already lose most disputes (8.1% won outright across all US disputes) and each $1 of fraud costs US retailers $5.13.

## Proposed solution
Checks a claimant's agent-originated order against any captured intent record, prior undisputed agent orders from the same buyer, and agent-identity signals, then produces a reason-specific evidence packet for the PayPal dispute.

## Target users
Merchants with growing agent-referred traffic.

## AI contribution
Evidence retrieval and narrative drafting; pattern detection across buyer history.

## PayPal integration
Disputes provide-evidence; Transaction Search for buyer history; Orders metadata.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P18` Transaction Search / Reporting
- `P31` custom_id / invoice_id metadata binding
- `A06` Entity matching and narrative drafting
- `A05` Structured decision / classification (most common)

## Competitors and prior art
Chargeflow, Justt, Chargebacks911

Fraud/dispute vendors target card chargebacks broadly; none specialise in agent-attribution claims.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Narrow but sharp angle on a newly named fraud vector.

## Feasibility
Needs synthetic agent-order history; otherwise straightforward.

## MVP scope
Seeded history + sandbox dispute + generated evidence packet.

## Risks
Problem is forward-looking with no volume data; overlaps idea 1.

## Credible references
- [Worldpay — 'No liability shift exists yet' for agent disputes (Jul 2026)](https://worldpay.com/insights/articles/agentic-commerce-liability-is-still-being-written) ✅
- [chargeback.io — merchants win 8.1% of all US disputes (Mastercard funnel)](https://www.chargeback.io/blog/chargeback-statistics) ⚠️
- [LexisNexis True Cost of Fraud 2026 — $5.13 per $1 (US retail)](https://risk.lexisnexis.com/about-us/press-room/press-release/20260624-tcof-retail-and-commerce) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **76** | 

_Why (desk):_ Valid but narrow and dependent on idea 1's capture layer.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
