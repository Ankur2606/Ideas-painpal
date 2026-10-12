---
title: "#44 Agent Price-Parity Checker"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, eliminated]
up: "[[Idea Index]]"
id: 44
theme: E1
group: "Agent integrity"
desk_score: 72
final_score: 72
status: ELIMINATED
verdict: desk-only
kills: [K4]
---
# #44 Agent Price-Parity Checker

> Compares the price a merchant quotes a signed agent with what a human session sees, before payment.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent integrity · **Crowding on Devpost:** none

## Problem statement
Signed agent identity makes agents easy to price-discriminate; no consumer tool audits it.

## Proposed solution
Parallel KERNEL browser sessions (agent vs human profile) capture quotes; differences flagged before PayPal capture.

## Target users
Consumers, regulators, researchers.

## AI contribution
Browser agents; price extraction.

## PayPal integration
Hold payment until parity check.

**Primitives used** (see [[30 - Primitives Legend]]):
- `S04` Sponsor tool: KERNEL browser infrastructure (⚠ inferred)
- `A09` Browser agents
- `P02` AUTHORIZE intent (hold funds)

## Competitors and prior art
academic audits

No product found.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Novel.

## Feasibility
Low-medium (bot detection, flaky sites).

## MVP scope
Two demo merchants with differential pricing.

## Risks
Thin PayPal integration; problem is hypothetical today.

## Credible references
- [Cloudflare — signed agents, Visa TAP, Web Bot Auth](https://blog.cloudflare.com/secure-agentic-commerce/) ✅
- [Training LMs for bilateral trade — price discrimination (arXiv 2604.16472)](https://econpapers.repec.org/paper/arxpapers/2604.16472.htm) ✅
- [KERNEL payments doc (Stripe Link, AgentCard; no PayPal)](https://www.kernel.sh/docs/browsers/payments) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 5 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 9 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 5 | 
| Risk⁻¹ | ×1 | 5 | 
| **Total /120** | | **72** | 

_Why (desk):_ Novel but speculative and thin on PayPal.

**Kill criteria triggered:** `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
