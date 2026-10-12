---
title: "#64 Refund Policy Compiler"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor]
up: "[[Idea Index]]"
id: 64
theme: E3
group: "After the purchase"
desk_score: 71
final_score: 71
status: SURVIVOR
verdict: desk-only
kills: []
---
# #64 Refund Policy Compiler

> A merchant's plain-English refund policy compiled into deterministic rules that a refund agent executes and explains.

**Theme:** E3 Evidence economy · **Group:** After the purchase · **Crowding on Devpost:** Refund cluster

## Problem statement
Inconsistent refunds create disputes and abuse.

## Proposed solution
NL → rule DSL → agent executes refunds with citations.

## Target users
Merchants.

## AI contribution
Policy compilation.

## PayPal integration
Refunds; Orders.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P16` Refunds (full / partial)
- `A16` Policy / rule reasoning with cited clauses

## Competitors and prior art
Gorgias, Zendesk AI

Helpdesk AI handles refunds with macros.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Deterministic compilation.

## Feasibility
High.

## MVP scope
Policy → 5 refund requests.

## Risks
Refund Desk entries exist.

## Credible references
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **71** | 

_Why (desk):_ Fine, crowded.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
