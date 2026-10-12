---
title: "#49 Agent-Buyability Audit"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E7, survivor]
up: "[[Idea Index]]"
id: 49
theme: E7
group: "Agent-ready long tail"
desk_score: 82
final_score: 82
status: SURVIVOR
verdict: desk-only
kills: []
---
# #49 Agent-Buyability Audit

> Lighthouse for agents — a browser agent tries to buy from your store in PayPal sandbox and reports exactly where agents fail, with fixes.

**Theme:** E7 Agent-ready long tail · **Group:** Agent-ready long tail · **Crowding on Devpost:** none

## Problem statement
Merchants can't tell whether agents can complete purchases on their sites.

## Proposed solution
KERNEL browser agent attempts discovery → cart → PayPal checkout; replay video; scorecard; generated fixes (structured data, labels, steps).

## Target users
Merchants and agencies.

## AI contribution
Browser agent, failure diagnosis, fix generation.

## PayPal integration
Checkout in sandbox; JS SDK v6.

**Primitives used** (see [[30 - Primitives Legend]]):
- `S04` Sponsor tool: KERNEL browser infrastructure (⚠ inferred)
- `A09` Browser agents
- `A14` Diagnosis / code transformation
- `P24` JS SDK v6

## Competitors and prior art
Profound, Scrunch AI, Bluefish

"AI visibility" tools track brand mentions in AI answers, not transactional buyability.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Transaction-level audit.

## Feasibility
Medium (browser flakiness).

## MVP scope
Audit two demo stores (good vs broken).

## Risks
PayPal is incidental unless fixes focus on checkout.

## Credible references
- [Mirakl via Beet.TV — <1% of product pages LLM-ready](https://www.beet.tv/2026/08/fewer-than-1-of-product-pages-are-llm-ready-mirakls-meadon.html) ⚠️
- [KERNEL payments doc (Stripe Link, AgentCard; no PayPal)](https://www.kernel.sh/docs/browsers/payments) ✅
- [WebAIM Million 2026 — 95.9% home pages fail WCAG](https://webaim.org/projects/million/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 8 | 
| Demo | ×2 | 8 | 
| Feasibility | ×1 | 6 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **82** | 

_Why (desk):_ Fresh, but PayPal is not the core.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
