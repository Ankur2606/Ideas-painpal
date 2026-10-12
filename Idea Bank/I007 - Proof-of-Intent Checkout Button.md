---
title: "#7 Proof-of-Intent Checkout Button"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor]
up: "[[Idea Index]]"
id: 7
theme: E1
group: "Agent purchase liability"
desk_score: 78
final_score: 78
status: SURVIVOR
verdict: desk-only
kills: []
---
# #7 Proof-of-Intent Checkout Button

> A JS SDK v6 checkout component that, when the buyer is an agent, captures a signed intent summary into the order — dispute evidence for merchants by default.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** none

## Problem statement
Merchants receiving agent orders have "no signed record of what the shopper authorized" (Worldpay), and issuers side with cardholders.

## Proposed solution
Drop-in wrapper around the v6 PayPal button that detects agent sessions (Web Bot Auth / WebMCP context), asks the agent for a structured intent statement, has the human approve it in the PayPal popup, and stores it with the order.

## Target users
Merchants on any stack.

## AI contribution
Intent summarisation; consistency check between intent and cart.

## PayPal integration
JS SDK v6 sessions; Orders custom_id; Disputes evidence when needed.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P24` JS SDK v6
- `P31` custom_id / invoice_id metadata binding
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `A13` Vision verification / evidence narrative

## Competitors and prior art
Visa Trusted Agent Protocol, Cloudflare Web Bot Auth

Agent identity standards verify who the agent is, not what the human intended.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
Merchant-side, drop-in, PayPal-native.

## Feasibility
Medium; agent-detection in demo can be simulated.

## MVP scope
Demo store + agent + button + stored intent + dispute evidence export.

## Risks
Overlaps ideas 1 and 47; agent detection mostly simulated.

## Credible references
- [Worldpay — 'No liability shift exists yet' for agent disputes (Jul 2026)](https://worldpay.com/insights/articles/agentic-commerce-liability-is-still-being-written) ✅
- [Cloudflare — signed agents, Visa TAP, Web Bot Auth](https://blog.cloudflare.com/secure-agentic-commerce/) ✅
- [PayPal JS SDK v6 announcement](https://developer.paypal.com/community/blog/paypal-js-sdk-v6/) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 7 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 7 | 
| Demo | ×2 | 6 | 
| Feasibility | ×1 | 7 | 
| Risk⁻¹ | ×1 | 7 | 
| **Total /120** | | **78** | 

_Why (desk):_ Good merchant angle; best as a module of idea 1 or 47.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
