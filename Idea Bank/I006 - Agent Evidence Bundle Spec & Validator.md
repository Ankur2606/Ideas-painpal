---
title: "#6 Agent Evidence Bundle Spec & Validator"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, eliminated]
up: "[[Idea Index]]"
id: 6
theme: E1
group: "Agent purchase liability"
desk_score: 71
final_score: 71
status: ELIMINATED
verdict: desk-only
kills: [K6]
---
# #6 Agent Evidence Bundle Spec & Validator

> An open specification and validator that maps AP2/Verifiable-Intent mandates into PayPal dispute evidence types.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** none

## Problem statement
Verifiable Intent enables selective disclosure "for dispute resolution", but no rule says what evidence wins an agent dispute; formats are per-network.

## Proposed solution
JSON schema + validator + converter producing PROOF_OF_FULFILLMENT/OTHER evidence files from mandates, context hashes and delivery data, with a test suite against sandbox disputes.

## Target users
Developers building agent checkout; payment ops teams.

## AI contribution
Converter uses an LLM to summarise mandates into human-readable evidence narratives; schema-validated output with repair loop.

## PayPal integration
Disputes provide-evidence (multipart); sandbox dispute factory for conformance tests.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P15` Disputes sandbox factory (create, adjudicate)
- `A01` Document / image extraction (OCR, validation)
- `A13` Vision verification / evidence narrative

## Competitors and prior art
Mastercard Verifiable Intent, Google AP2

Standards define the mandate, not the dispute evidence mapping.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
The missing translation layer, open source.

## Feasibility
High, but the product experience is thin.

## MVP scope
Spec, CLI validator, three sandbox dispute conformance runs.

## Risks
Weak "Design" score (no end-user experience); judges may find it dry.

## Credible references
- [Mastercard Verifiable Intent (Mar 2026)](https://www.mastercard.com/au/en/news-and-trends/stories/2026/verifiable-intent.html) ✅
- [Beyond the Mandate — 48 threats vs AP2 v0.2 (arXiv 2608.23858)](https://www.emergentmind.com/papers/2608.23858) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 4 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 7 | 
| Demo | ×2 | 4 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **71** | 

_Why (desk):_ Useful infrastructure, poor video.

**Kill criteria triggered:** `K6` Infrastructure with no watchable demo. See [[41 - Brutal Elimination]].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
