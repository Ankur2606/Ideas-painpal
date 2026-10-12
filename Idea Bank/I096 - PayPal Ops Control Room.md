---
title: "#96 PayPal Ops Control Room"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor]
up: "[[Idea Index]]"
id: 96
theme: E3
group: "Merchant risk intelligence"
desk_score: 84
final_score: 84
status: SURVIVOR
verdict: desk-only
kills: []
---
# #96 PayPal Ops Control Room

> An AG Studio dashboard where a dispute-specialist agent works alongside Studio's built-in agents — approve evidence, offers and refunds straight from the grid.

**Theme:** E3 Evidence economy · **Group:** Merchant risk intelligence · **Crowding on Devpost:** Analytics cluster

## Problem statement
Merchants juggle disputes, refunds and payouts across screens.

## Proposed solution
AG Studio with custom widgets + custom domain agent driving PayPal APIs from grid actions.

## Target users
SMB ops.

## AI contribution
Domain agent + Studio agents.

## PayPal integration
Disputes, Refunds, Payouts, Transaction Search.

**Primitives used** (see [[30 - Primitives Legend]]):
- `S01` Sponsor tool: AG Grid / AG Studio (⚠ inferred)
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P16` Refunds (full / partial)
- `P11` Payouts (batch)
- `P18` Transaction Search / Reporting
- `A03` Intent and rationale reasoning (LLM-as-judge)

## Competitors and prior art
PayPal dashboard

Analytics dashboards are crowded; control-surface twist matches AG Grid criteria.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Control surface rather than report.

## Feasibility
High (boilerplate exists).

## MVP scope
Grid of disputes with agent-generated evidence widgets.

## Risks
Dashboard cluster; best as a shell for another idea.

## Credible references
- [Devpost AG Grid sponsor page (criteria, suggested ideas)](https://paypalaihackathon.devpost.com/details/aggrid) ✅
- [AG Studio Agent Framework (Sep 2026)](https://www.ag-grid.com/blog/introducing-the-ag-studio-agent-framework/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 8 | 
| Design | ×2 | 8 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 8 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **84** | 

_Why (desk):_ Great sponsor-prize shell for idea 16/20/23.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
