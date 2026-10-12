---
title: "#45 Agent Payment Eval Harness"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, eliminated]
up: "[[Idea Index]]"
id: 45
theme: E1
group: "Agent integrity"
desk_score: 76
final_score: 76
status: ELIMINATED
verdict: desk-only
kills: [K6]
---
# #45 Agent Payment Eval Harness

> A benchmark that measures how often payment agents buy the wrong item, double-charge, or fall for injection — run against the PayPal sandbox.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent integrity · **Crowding on Devpost:** none

## Problem statement
Shopping benchmarks exist but none measure wrong-purchase rates with money at stake or downstream dispute cost.

## Proposed solution
Scenario suite + sandbox fixtures (Mock-Response declines, injected listings, ambiguous instructions) + scorecard across models and frameworks.

## Target users
Agent builders, PayPal DevRel.

## AI contribution
LLM agents under test; LLM-as-judge.

## PayPal integration
Agent toolkit; Orders; Mock-Response; Disputes.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P27` Agent Toolkit / MCP
- `P21` PayPal-Mock-Response header (sandbox fault injection)
- `P01` Orders v2 (create / capture / get)
- `A13` Vision verification / evidence narrative

## Competitors and prior art
tau-bench, WebShop, ShoppingBench

Academic benchmarks exist without payment rails.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Money-at-stake metrics.

## Feasibility
High.

## MVP scope
30 scenarios × 3 models leaderboard.

## Risks
Demo is a leaderboard.

## Credible references
- [Magentic Marketplace — 60–100% first-proposal bias (arXiv 2510.25779)](https://arxiv.org/html/2510.25779v1) ✅
- [paypal/agent-toolkit (46 tools, v1.11.0)](https://github.com/paypal/agent-toolkit) ✅
- [paypaldev/getting-started-with-paypal-sandbox (PayPal-Mock-Response)](https://github.com/paypaldev/getting-started-with-paypal-sandbox) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 8 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 8 | 
| Demo | ×2 | 4 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **76** | 

_Why (desk):_ Valuable, not demo-shaped.

**Kill criteria triggered:** `K6` Infrastructure with no watchable demo. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
