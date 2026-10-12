---
title: "#94 Fraud Ring Graph"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor]
up: "[[Idea Index]]"
id: 94
theme: E3
group: "Merchant risk intelligence"
desk_score: 76
final_score: 76
status: SURVIVOR
verdict: desk-only
kills: []
---
# #94 Fraud Ring Graph

> Indexes PayPal disputes, refunds and webhooks into Elastic; a risk agent must be consulted (A2A) before any refund agent moves money.

**Theme:** E3 Evidence economy · **Group:** Merchant risk intelligence · **Crowding on Devpost:** Analytics cluster

## Problem statement
Refund and dispute abuse clusters go unseen in per-case handling.

## Proposed solution
Elastic index + ES|QL anomaly tools + A2A risk check gating the refund agent.

## Target users
SMB merchants.

## AI contribution
Anomaly detection, agent-to-agent risk consult.

## PayPal integration
Webhooks; Transaction Search; Refunds; Disputes.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P20` Webhooks (events, retries, verification)
- `P18` Transaction Search / Reporting
- `P16` Refunds (full / partial)
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `S05` Sponsor tool: Elastic / Render (⚠ inferred)
- `A15` Anomaly detection

## Competitors and prior art
Signifyd, Sardine

Fraud vendors serve mid-market+.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
A2A gating pattern.

## Feasibility
Medium.

## MVP scope
Seeded ring detected; refund blocked.

## Risks
Analytics-ish demo.

## Credible references
- [Elastic Agent Builder (MCP + A2A servers)](https://www.elastic.co/docs/explore-analyze/ai-features/elastic-agent-builder) ✅
- [Appriss 2026 — $100B preventable return fraud/abuse](https://apprissretail.com/2026-total-retail-loss-benchmark-report/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **76** | 

_Why (desk):_ Solid sponsor play; moderate.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
