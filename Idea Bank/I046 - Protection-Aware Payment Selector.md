---
title: "#46 Protection-Aware Payment Selector"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, eliminated]
up: "[[Idea Index]]"
id: 46
theme: E5
group: "Agent integrity"
desk_score: 66
final_score: 66
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #46 Protection-Aware Payment Selector

> Agents choose a payment method by weighing buyer protection, not just approval rate — and explain the choice to the human.

**Theme:** E5 Moment-of-send scams · **Group:** Agent integrity · **Crowding on Devpost:** none

## Problem statement
Agents optimise for signals like approval and post-purchase handling; Klarna markets exactly those signals to agents. PayPal's protection advantage is invisible to agents.

## Proposed solution
Machine-readable protection profile per method/merchant/category; agent picks method and explains.

## Target users
Agent builders; PayPal (branded checkout).

## AI contribution
Reasoning over protection terms.

## PayPal integration
Orders; Purchase Protection terms.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `A16` Policy / rule reasoning with cited clauses

## Competitors and prior art
Klarna agentic APP

Klarna pitches agent-facing signals.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Strategic for PayPal; weak user pain.

## Feasibility
High.

## MVP scope
Agent choosing among methods.

## Risks
Weak end-user problem.

## Credible references
- [Klarna agentic commerce — 'signals agents rely on to choose a payment provider'](https://www.klarna.com/international/enterprise/agentic-commerce/) ✅
- [Nasdaq/Zacks — PayPal agentic meaningful 'from 2028'; branded checkout +2%](https://www.nasdaq.com/articles/paypal-agentic-payments-can-they-reshape-future-commerce) ⚠️
- [Visa — Earning Consumer Trust in Agentic Commerce (PayPal top-3 trusted)](https://corporate.visa.com/en/products/intelligent-commerce/earning-trust-report.html) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 5 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **66** | 

_Why (desk):_ Strategy deck, not a product.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
