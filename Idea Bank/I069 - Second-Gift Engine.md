---
title: "#69 Second-Gift Engine"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E10, survivor]
up: "[[Idea Index]]"
id: 69
theme: E10
group: "Giving & community"
desk_score: 81
final_score: 81
status: SURVIVOR
verdict: desk-only
kills: []
---
# #69 Second-Gift Engine

> Turns a first PayPal donation into a second one with an AI-personalised impact update, timed to the donor's behaviour.

**Theme:** E10 Cross-border, giving & inclusion · **Group:** Giving & community · **Crowding on Devpost:** Donation cluster (sponsor-suggested)

## Problem statement
Overall donor retention is 43.3%; donor counts fell 3.6% in 2025; FEP calls first-to-second gift conversion "the most consequential unsolved problem".

## Proposed solution
Donation webhooks trigger an impact story drafted from the nonprofit's field updates, a recurring-gift ask at the right moment, and one-click PayPal recurring donation.

## Target users
Small nonprofits.

## AI contribution
Personalised impact writing, timing model.

## PayPal integration
Donate SDK; Subscriptions (recurring gifts); webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P29` Donate SDK / charity flows
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `P20` Webhooks (events, retries, verification)
- `A12` Eligibility reasoning and messaging
- `A04` Forecasting / pricing suggestion

## Competitors and prior art
Fundraise Up, Givebutter, Bloomerang

Donor CRMs and AI fundraising tools exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Moderate; focus on first→second gift.

## Feasibility
High.

## MVP scope
Donation → impact email → recurring gift.

## Risks
AG Grid suggests a donation dashboard; donor CRMs.

## Credible references
- [Fundraising Effectiveness Project — 43.3% retention; donors −3.6%](https://afpglobal.org/news/fundraising-effectiveness-project-reports-strongest-revenue-growth-five-years-even-fewer) ✅
- [Devpost AG Grid sponsor page (criteria, suggested ideas)](https://paypalaihackathon.devpost.com/details/aggrid) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **81** | 

_Why (desk):_ Strong evidence; moderate novelty.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
