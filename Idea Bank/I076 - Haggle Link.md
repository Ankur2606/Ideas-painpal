---
title: "#76 Haggle Link"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, eliminated]
up: "[[Idea Index]]"
id: 76
theme: E9
group: "Agents as economic actors"
desk_score: 72
final_score: 72
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #76 Haggle Link

> A PayPal payment link with an AI negotiator that haggles within the seller's floor price.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Agents as economic actors · **Crowding on Devpost:** none

## Problem statement
Casual sellers spend time haggling in DMs.

## Proposed solution
Negotiation chat bounded by floor; creates PayPal order at agreed price.

## Target users
Marketplace sellers.

## AI contribution
Negotiation.

## PayPal integration
Orders; Payment Links.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P22` Payment Links
- `P01` Orders v2 (create / capture / get)
- `A07` Multi-agent negotiation

## Competitors and prior art
Nibble

AI negotiation widgets exist for e-commerce.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Seller-link scope.

## Feasibility
High.

## MVP scope
Negotiate → pay.

## Risks
Weak evidence; LLM exploitability.

## Credible references
- [Training LMs for bilateral trade — price discrimination (arXiv 2604.16472)](https://econpapers.repec.org/paper/arxpapers/2604.16472.htm) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 3 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **72** | 

_Why (desk):_ Fun, low impact.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
