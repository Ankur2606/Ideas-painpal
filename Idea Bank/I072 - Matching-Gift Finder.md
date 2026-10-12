---
title: "#72 Matching-Gift Finder"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E10, eliminated]
up: "[[Idea Index]]"
id: 72
theme: E10
group: "Giving & community"
desk_score: 56
final_score: 56
status: ELIMINATED
verdict: desk-only
kills: [K2, K4]
---
# #72 Matching-Gift Finder

> After a PayPal donation, AI identifies the donor's employer matching programme and files the match request.

**Theme:** E10 Cross-border, giving & inclusion · **Group:** Giving & community · **Crowding on Devpost:** none

## Problem statement
Many eligible matching gifts go unclaimed (vendor claims).

## Proposed solution
Employer detection + program database + request drafting.

## Target users
Nonprofits.

## AI contribution
Matching, drafting.

## PayPal integration
Donate SDK; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P29` Donate SDK / charity flows
- `P20` Webhooks (events, retries, verification)
- `A06` Entity matching and narrative drafting

## Competitors and prior art
Double the Donation

Dominant incumbent.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Low.

## Feasibility
Medium.

## MVP scope
Donation → match request.

## Risks
Incumbent; data access.

## Credible references


## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 5 | 
| Design | ×2 | 5 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 3 | 
| Demo | ×2 | 4 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **56** | 

_Why (desk):_ Solved.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended; `K4` Weak evidence or low impact. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
