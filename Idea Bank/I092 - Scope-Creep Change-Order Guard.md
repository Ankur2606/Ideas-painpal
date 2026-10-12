---
title: "#92 Scope-Creep Change-Order Guard"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, survivor]
up: "[[Idea Index]]"
id: 92
theme: E9
group: "Trades & B2B ops"
desk_score: 79
final_score: 79
status: SURVIVOR
verdict: desk-only
kills: []
---
# #92 Scope-Creep Change-Order Guard

> Detects out-of-scope requests in client messages and turns them into priced change-order invoices before the work happens.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Trades & B2B ops · **Crowding on Devpost:** Invoice cluster

## Problem statement
Freelancers report "just one more thing" requests and late pay.

## Proposed solution
Message classification against SOW; change-order invoice draft; client approval.

## Target users
Freelancers, agencies.

## AI contribution
Scope comparison, drafting.

## PayPal integration
Invoicing.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P08` Invoicing v2 (create, send, partial payment)
- `A06` Entity matching and narrative drafting
- `A05` Structured decision / classification (most common)

## Competitors and prior art
Bonsai, HoneyBook

Freelancer suites lack automatic scope detection.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Moderate.

## Feasibility
High.

## MVP scope
Chat → change order → paid.

## Risks
Invoice cluster.

## Credible references
- [Remote 2025 — 85% of freelancers paid late sometimes](https://remote.com/blog/contractor-management/reversing-late-payment-culture) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **79** | 

_Why (desk):_ Decent.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
