---
title: "#90 Agentic RFQ Desk"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, survivor]
up: "[[Idea Index]]"
id: 90
theme: E9
group: "Trades & B2B ops"
desk_score: 69
final_score: 69
status: SURVIVOR
verdict: desk-only
kills: []
---
# #90 Agentic RFQ Desk

> Inbound quote-request emails for small manufacturers become priced quotes and PayPal deposit invoices, drafted by an agent and approved by a human.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Trades & B2B ops · **Crowding on Devpost:** none

## Problem statement
Small job shops lose deals to slow quoting.

## Proposed solution
Email parsing, pricing rules, quote doc, deposit invoice.

## Target users
Small manufacturers/wholesalers.

## AI contribution
Extraction, pricing.

## PayPal integration
Invoicing.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P08` Invoicing v2 (create, send, partial payment)
- `A01` Document / image extraction (OCR, validation)
- `A03` Intent and rationale reasoning (LLM-as-judge)

## Competitors and prior art
Paperless Parts

Manufacturing quoting software exists.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
SMB, PayPal deposit.

## Feasibility
High.

## MVP scope
Email → quote → invoice.

## Risks
Niche.

## Credible references
- [KC Fed — B2B payments still ~90% use checks](https://www.kansascityfed.org/research/payments-system-research-briefings/b2b-payments-business-processing-and-challenges-to-achieving-straight-through-processing/) ⚠️

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 4 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **69** | 

_Why (desk):_ Niche.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
