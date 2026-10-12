---
title: "#58 Exactly-Once Agent Payment Proxy"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, eliminated]
up: "[[Idea Index]]"
id: 58
theme: E8
group: "Failure-path intelligence"
desk_score: 73
final_score: 73
status: ELIMINATED
verdict: desk-only
kills: [K6]
---
# #58 Exactly-Once Agent Payment Proxy

> An MCP proxy that gives every PayPal agent tool call a deterministic idempotency key so a retrying LLM can never double-charge.

**Theme:** E8 Failure-path intelligence · **Group:** Failure-path intelligence · **Crowding on Devpost:** Policy-proxy cluster adjacent

## Problem statement
The agent toolkit never sets PayPal-Request-Id per call (#98); LLM retries can duplicate orders/refunds.

## Proposed solution
Proxy derives keys from intent hashes, caches outcomes, resolves unknown-outcome errors; upstream PR.

## Target users
Agent developers.

## AI contribution
Intent hashing; retry reasoning.

## PayPal integration
Agent toolkit/MCP; PayPal-Request-Id.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P27` Agent Toolkit / MCP
- `A03` Intent and rationale reasoning (LLM-as-judge)

## Competitors and prior art
HN 'pays once' projects

Builders hand-roll idempotency.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Correctness for PayPal agents.

## Feasibility
High.

## MVP scope
Chaos retry demo: double charge without proxy, single with.

## Risks
Infra-only; weak design score.

## Credible references
- [agent-toolkit #98 — PayPal-Request-Id never set per call (no idempotency)](https://github.com/paypal/agent-toolkit/issues/98) ✅
- [HN Algolia — 2026 'agent payments' Show HN threads](https://hn.algolia.com/api/v1/search?query=agent%20payments&tags=story&numericFilters=created_at_i>1767225600) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 8 | 
| Design | ×2 | 4 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **73** | 

_Why (desk):_ Great PR, thin product.

**Kill criteria triggered:** `K6` Infrastructure with no watchable demo. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
