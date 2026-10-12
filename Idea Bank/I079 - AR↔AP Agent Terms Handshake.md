---
title: "#79 AR↔AP Agent Terms Handshake"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, survivor]
up: "[[Idea Index]]"
id: 79
theme: E9
group: "Agents as economic actors"
desk_score: 77
final_score: 77
status: SURVIVOR
verdict: desk-only
kills: []
---
# #79 AR↔AP Agent Terms Handshake

> The seller's receivables agent and the buyer's payables agent negotiate payment terms — early discount vs Pay Later — and settle on a PayPal invoice.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Agents as economic actors · **Crowding on Devpost:** Official inspiration (agent-to-agent)

## Problem statement
B2B payments still rely heavily on checks and manual terms negotiation.

## Proposed solution
Two agents with bounded mandates negotiate; result encoded in invoice conditional rules.

## Target users
SMB B2B.

## AI contribution
Negotiation with bounds.

## PayPal integration
Invoicing conditional rules; Pay Later.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P09` Invoicing conditional rules (early-payment discount, auto-cancel)
- `P08` Invoicing v2 (create, send, partial payment)
- `A07` Multi-agent negotiation

## Competitors and prior art
Pactum, C2FO

Enterprise negotiation/discounting exists.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
SMB agent-to-agent.

## Feasibility
Medium.

## MVP scope
Two agents → invoice.

## Risks
Speculative demand.

## Credible references
- [KC Fed — B2B payments still ~90% use checks](https://www.kansascityfed.org/research/payments-system-research-briefings/b2b-payments-business-processing-and-challenges-to-achieving-straight-through-processing/) ⚠️
- [The Automated but Risky Game — agent negotiation imbalance (arXiv 2506.00073)](https://arxiv.org/abs/2506.00073) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 7 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **77** | 

_Why (desk):_ Interesting extension of 28.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
