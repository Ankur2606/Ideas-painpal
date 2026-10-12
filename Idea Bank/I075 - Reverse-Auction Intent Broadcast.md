---
title: "#75 Reverse-Auction Intent Broadcast"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, survivor]
up: "[[Idea Index]]"
id: 75
theme: E9
group: "Agents as economic actors"
desk_score: 71
final_score: 71
status: SURVIVOR
verdict: desk-only
kills: []
---
# #75 Reverse-Auction Intent Broadcast

> A buyer's agent broadcasts a purchase intent; merchant agents bid; PayPal settles the winner.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Agents as economic actors · **Crowding on Devpost:** Official inspiration

## Problem statement
Agents pick the first offer (Magentic bias); buyers rarely get competitive bids.

## Proposed solution
Intent schema, bidding round, settlement via PayPal Orders.

## Target users
Consumers; merchants.

## AI contribution
Multi-agent negotiation.

## PayPal integration
Orders; AUTHORIZE.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `P02` AUTHORIZE intent (hold funds)
- `A07` Multi-agent negotiation

## Competitors and prior art
Pactum, Fairmarkit

AI procurement negotiation exists for enterprise.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Consumer-side.

## Feasibility
Medium.

## MVP scope
3 merchant agents bid.

## Risks
Needs merchant participation; agent-to-agent is in the official inspiration list.

## Credible references
- [Magentic Marketplace — 60–100% first-proposal bias (arXiv 2510.25779)](https://arxiv.org/html/2510.25779v1) ✅
- [The Automated but Risky Game — agent negotiation imbalance (arXiv 2506.00073)](https://arxiv.org/abs/2506.00073) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **71** | 

_Why (desk):_ Fun, speculative.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
