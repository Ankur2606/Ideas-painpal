---
title: "#66 Duty-Inclusive Cross-Border Checkout"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E10, eliminated]
up: "[[Idea Index]]"
id: 66
theme: E10
group: "Cross-border clarity"
desk_score: 59
final_score: 59
status: ELIMINATED
verdict: desk-only
kills: [K2, K4]
---
# #66 Duty-Inclusive Cross-Border Checkout

> Estimates duties and taxes at checkout and shows the landed cost in the PayPal order breakdown, so parcels aren't refused at the door.

**Theme:** E10 Cross-border, giving & inclusion · **Group:** Cross-border clarity · **Crowding on Devpost:** none

## Problem statement
Surprise duties cause refused deliveries and disputes.

## Proposed solution
HS-code classification + duty estimate + order breakdown.

## Target users
Cross-border SMBs.

## AI contribution
HS classification.

## PayPal integration
Orders breakdown (tax/shipping).

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `A05` Structured decision / classification (most common)

## Competitors and prior art
Zonos, Global-e, Avalara

Mature landed-cost providers.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
Medium.

## MVP scope
Two countries.

## Risks
Incumbents; tax accuracy.

## Credible references


## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 5 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **59** | 

_Why (desk):_ Solved by incumbents.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended; `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
