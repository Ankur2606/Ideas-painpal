---
title: "#65 Net-Landed Quote Engine"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E10, survivor]
up: "[[Idea Index]]"
id: 65
theme: E10
group: "Cross-border clarity"
desk_score: 79
final_score: 79
status: SURVIVOR
verdict: desk-only
kills: []
---
# #65 Net-Landed Quote Engine

> Freelancers state what they need to receive; AI picks invoice currency and amount so they net exactly that after PayPal fees and FX — and explains every deduction.

**Theme:** E10 Cross-border, giving & inclusion · **Group:** Cross-border clarity · **Crowding on Devpost:** none

## Problem statement
Cross-border, cross-currency PayPal sales can stack to ~8–9% plus fixed fees; Reddit sellers report losing 11.2% without understanding why.

## Proposed solution
Fee/FX calculator using PayPal's published schedule, payer location and currency options; generates the invoice; post-payment, reconciles actual deductions vs expected.

## Target users
Cross-border freelancers and small exporters.

## AI contribution
Fee reasoning, explanations, reconciliation narrative.

## PayPal integration
Invoicing (multi-currency); Transaction Search fee fields.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P08` Invoicing v2 (create, send, partial payment)
- `P18` Transaction Search / Reporting
- `A16` Policy / rule reasoning with cited clauses
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Wise invoices, Payoneer

Alternative rails compete on price; PayPal-specific transparency tools don't exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Transparency framing (not "PayPal is expensive").

## Feasibility
High.

## MVP scope
Target $1,000 net from a UK client → invoice → reconciliation.

## Risks
Anti-sponsor perception if framed poorly; fee schedule changes.

## Credible references
- [PayPal merchant fees (3.49%+$0.49; +1.5% intl; 3–4% FX)](https://www.paypal.com/us/webapps/mpp/merchant-fees) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 6 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **79** | 

_Why (desk):_ Practical; framing risk.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
