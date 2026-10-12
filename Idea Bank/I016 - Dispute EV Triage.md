---
title: "#16 Dispute EV Triage"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, eliminated]
up: "[[Idea Index]]"
id: 16
theme: E3
group: "Evidence economy"
desk_score: 91
final_score: 91
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #16 Dispute EV Triage

> For every PayPal dispute, estimate the expected value of fighting vs offering vs accepting — then execute the best move with reason-specific evidence.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** Disputes cluster (~7)

## Problem statement
Small merchants fight only 60.3% of friendly-fraud chargebacks; evidence collection is the

## Proposed solution
Pulls every open dispute, scores win probability from reason, amount and available evidence, recommends fight / partial-refund offer / accept, and executes via the Disputes API with assembled evidence.

## Target users
SMB merchants on PayPal.

## AI contribution
Win-probability scoring, evidence assembly, offer sizing.

## PayPal integration
Full Disputes API (list, get, make-offer, provide-evidence, accept-claim, escalate); sandbox factory; tracking; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P15` Disputes sandbox factory (create, adjudicate)
- `P17` Shipment Tracking API (add tracking; releases holds)
- `P20` Webhooks (events, retries, verification)
- `A05` Structured decision / classification (most common)
- `A01` Document / image extraction (OCR, validation)
- `A03` Intent and rationale reasoning (LLM-as-judge)

## Competitors and prior art
Chargeflow, Justt, Chargebacks911, Disputifier

Mature vendors (contingency fees ~20–30%) already automate representment; ~7 Devpost entries target disputes.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
EV framing and offer-making are the twist; otherwise a known category.

## Feasibility
High; sandbox dispute lifecycle is rich.

## MVP scope
5 sandbox disputes across reasons with different recommended moves executed live.

## Risks
Crowded; must avoid auto-accepting (PayPal's own skill warns).

## Credible references
- [Chargebacks911 2026 Field Report — SMBs represent only 60.3%; evidence collection #1 pain](https://chargebacks911.com/chargeback-field-report/) ✅
- [Mastercard/Datos 2025 State of Chargebacks — 261M→324M by 2028; 45% fraudulent](https://www.mastercard.com/us/en/news-and-trends/Insights/2025/2025-global-chargebacks-outlook.html) ✅
- [LexisNexis True Cost of Fraud 2026 — $5.13 per $1 (US retail)](https://risk.lexisnexis.com/about-us/press-room/press-release/20260624-tcof-retail-and-commerce) ✅
- [PayPal merchant fees (3.49%+$0.49; +1.5% intl; 3–4% FX)](https://www.paypal.com/us/webapps/mpp/merchant-fees) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅
- [Devpost 'Built with PayPal' listing (early-entry clustering, ~72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 9 | 
| Design | ×2 | 8 | 
| Impact | ×2 | 9 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **91** | 

_Why (desk):_ Best-evidenced problem, but a crowded headline.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
