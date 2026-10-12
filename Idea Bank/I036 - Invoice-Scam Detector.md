---
title: "#36 Invoice-Scam Detector"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, eliminated]
up: "[[Idea Index]]"
id: 36
theme: E5
group: "Moment-of-send scams"
desk_score: 60
final_score: 60
status: ELIMINATED
verdict: desk-only
kills: [K3]
---
# #36 Invoice-Scam Detector

> Paste a "PayPal invoice" or payment request you received; AI tells you if it's a known scam pattern and what to do.

**Theme:** E5 Moment-of-send scams · **Group:** Moment-of-send scams · **Crowding on Devpost:** none

## Problem statement
Fake invoices sent from real PayPal accounts are a common phishing vector; commerce phishing more than doubled in early 2026 (Akamai).

## Proposed solution
Analyses text/screenshots for scam patterns and generates a report.

## Target users
Consumers.

## AI contribution
Classification, explanation.

## PayPal integration
Weak — mostly analysis of PayPal-branded content; no API action.

**Primitives used** (see [[30 - Primitives Legend]]):
- `A05` Structured decision / classification (most common)
- `A02` Classification with explanation / vision estimation

## Competitors and prior art
Norton Genie, Bitdefender Scamio

Generic scam checkers already do this.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
High.

## MVP scope
Screenshot analysis.

## Risks
PayPal integration is not meaningful (Stage 1 fail risk).

## Credible references
- [Akamai SOTI 2026 — commerce 47.9% of AI bot traffic; agent hijacking](https://www.akamai.com/newsroom/press-release/akamai-research-commerce-becomes-the-epicenter-for-ai-bot-attacks-and-agentic-fraud-in-2026) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 3 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 3 | 
| **Total /120** | | **60** | 

_Why (desk):_ PayPal not central.

**Kill criteria triggered:** `K3` PayPal is not central to the loop. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
