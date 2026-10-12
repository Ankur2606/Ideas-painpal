---
title: "#83 Spec-to-Plan Billing Compiler"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, survivor]
up: "[[Idea Index]]"
id: 83
theme: E8
group: "Subscription revenue ops"
desk_score: 71
final_score: 71
status: SURVIVOR
verdict: desk-only
kills: []
---
# #83 Spec-to-Plan Billing Compiler

> Paste a pricing page or contract; AI compiles it into PayPal products and billing plans (tiered, volume, trials, setup fees).

**Theme:** E8 Failure-path intelligence · **Group:** Subscription revenue ops · **Crowding on Devpost:** none

## Problem statement
Translating contracts into billing configs is error-prone.

## Proposed solution
Extraction → plan configs → validation against PayPal plan constraints.

## Target users
SaaS founders, finance ops.

## AI contribution
Structured extraction with validation.

## PayPal integration
Catalog products; billing plans.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P30` Catalog products / billing plans
- `P07` Subscriptions (revise, suspend, payment-failed events)
- `A01` Document / image extraction (OCR, validation)

## Competitors and prior art
Tabs, Maxio

AI contract-to-billing startups exist (Tabs).

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal-native.

## Feasibility
High.

## MVP scope
Pricing page → plans created.

## Risks
Feature-sized.

## Credible references
- [paypal/agent-toolkit (46 tools, v1.11.0)](https://github.com/paypal/agent-toolkit) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **71** | 

_Why (desk):_ Neat utility.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
