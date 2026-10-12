---
title: "#24 Support-Ticket Dispute Early Warning"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, eliminated]
up: "[[Idea Index]]"
id: 24
theme: E3
group: "Evidence economy"
desk_score: 71
final_score: 71
status: ELIMINATED
verdict: desk-only
kills: [K2]
---
# #24 Support-Ticket Dispute Early Warning

> Reads incoming customer emails for dispute intent and resolves high-risk cases proactively.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** none

## Problem statement
Many disputes are preceded by frustrated messages the merchant didn't act on.

## Proposed solution
Classifies support messages for dispute risk; proposes refunds/replacements within policy before the buyer files.

## Target users
SMB merchants.

## AI contribution
Intent classification, response drafting.

## PayPal integration
Refunds; Orders lookup; Disputes analytics.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P16` Refunds (full / partial)
- `P18` Transaction Search / Reporting
- `A05` Structured decision / classification (most common)
- `A12` Eligibility reasoning and messaging

## Competitors and prior art
Gorgias, Zendesk AI

Helpdesk AI tools triage sentiment broadly.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Dispute-risk lens.

## Feasibility
High.

## MVP scope
Inbox of 10 messages → triage → refunds.

## Risks
Helpdesk incumbents.

## Credible references
- [Chargebacks911 2026 Field Report — SMBs represent only 60.3%; evidence collection #1 pain](https://chargebacks911.com/chargeback-field-report/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 6 | 
| Innovation | ×2 | 4 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **71** | 

_Why (desk):_ Incumbent-adjacent.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
