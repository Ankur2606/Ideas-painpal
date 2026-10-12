---
title: "#33 Marketplace Safe-Deal Link"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, survivor]
up: "[[Idea Index]]"
id: 33
theme: E5
group: "Moment-of-send scams"
desk_score: 79
final_score: 79
status: SURVIVOR
verdict: desk-only
kills: []
---
# #33 Marketplace Safe-Deal Link

> Honest sellers generate a protected PayPal deal link with an AI-verified listing summary, so buyers stop asking for F&F.

**Theme:** E5 Moment-of-send scams · **Group:** Moment-of-send scams · **Crowding on Devpost:** Escrow adjacent

## Problem statement
G&S fees push people to F&F, which scammers exploit.

## Proposed solution
Seller pastes listing → AI normalises item details and plausibility → protected PayPal payment link with plain-language protection terms; optional authorise-at-meetup for local pickup.

## Target users
Casual sellers.

## AI contribution
Listing normalisation, trust summary.

## PayPal integration
Payment Links API; AUTHORIZE for meet-ups.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P22` Payment Links
- `P02` AUTHORIZE intent (hold funds)
- `A01` Document / image extraction (OCR, validation)
- `A11` Translation / tone

## Competitors and prior art
Trustap, Escrow.com

Marketplace escrow apps exist.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Seller-initiated trust link.

## Feasibility
High.

## MVP scope
Listing → link → buyer pays.

## Risks
Escrow-adjacent; overlaps 32.

## Credible references
- [UK Finance Annual Fraud Report 2026 — APP £576.4M; 175,809 purchase scams](https://www.ukfinance.org.uk/system/files/2026-06/UK%20Finance%20Fraud%20Report%202026.pdf) ✅
- [FTC Consumer Sentinel Data Book 2024](https://www.ftc.gov/system/files/ftc_gov/pdf/csn-annual-data-book-2024.pdf) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 7 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **79** | 

_Why (desk):_ Good complement to 32.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
