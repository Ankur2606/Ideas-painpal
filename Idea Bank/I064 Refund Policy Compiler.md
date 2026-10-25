---
title: "#64 Refund Policy Compiler"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor, easy-read]
up: "[[Idea Index]]"
id: 64
theme: E3
group: "After the purchase"
desk_score: 71
final_score: 71
status: SURVIVOR
verdict: desk-only
kills: []
aliases: [Refund Policy Compiler]
summary: "A plain English refund policy is turned into fixed rules that a refund agent follows and explains."
---
# #64 Refund Policy Compiler

> [!tldr] In one breath
> A merchant's plain English refund policy is compiled into fixed rules that a refund agent follows and explains with quotes from the policy. **Fine but crowded (71 out of 120).**

> [!example] Picture this
> A shop's policy says "returns within 30 days, unless the item is a gift card". Today two support staff read that sentence two different ways. The compiler turns it into strict rules, so the same request always gets the same answer, and the reply points to the exact clause.

> [!warning] Crowd check, Oct 23 2026
> The scan found dispute and refund tools in a cluster of about 16 repos. Close cousins are returngate and clippay (partial refunds). The note's own Devpost scan lists Refund Desk entries. Helpdesk AI (Gorgias, Zendesk AI) handles refunds outside the hackathon.

**Theme:** [[Theme E3 Evidence economy|E3 Evidence economy]] · **Group:** After the purchase · **Crowding on Devpost:** refund cluster

## The problem
Inconsistent refunds create disputes and abuse.

## The idea
Natural language becomes a rule DSL (a tiny rule language), and the agent runs refunds with citations.

```mermaid
flowchart LR
  A["Merchant with a written refund policy"] --> B["Problem refunds decided inconsistently"]
  B --> C["AI compiles policy into fixed rules"]
  C --> D["PayPal Refunds and Orders executed"]
  D --> E["Consistent refunds with cited clauses"]
```

## Who it is for
Merchants.

## What the AI does
Compiles the policy into rules.

## What PayPal does
Refunds and Orders.

**Building blocks used** (see [[30 Primitives Legend]]):
* `P16` Refunds (full / partial)
* `A16` Policy / rule reasoning with cited clauses

## Who else is doing this
Gorgias, Zendesk AI. **Helpdesk AI handles refunds with macros (saved reply templates).**

⚠️ Verification: desk research only. The competitor names come from the landscape and Devpost scans, not from a hunt for each idea. Treat "no competitor found" as unproven.

## How it stands out
Deterministic compilation, meaning the same input always gives the same result.

## Can we build it?
High.

## Smallest demo
A policy plus 5 refund requests.

## Risks
Refund Desk entries exist.

## Sources
* [Devpost 'Built with PayPal' listing (early entry clustering, about 72 reviewed)](https://devpost.com/software/built-with/paypal) ⚠️

## Scores
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 6 | 
| Impact | ×2 | 5 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 5 | 
| Feasibility | ×1 | 9 | 
| Risk⁻¹ | ×1 | 8 | 
| **Total /120** | | **71** | 

_Why (desk):_ Fine, crowded.

**Kill codes:** none triggered.

> [!info]- Jargon decoder
> **Compiler**: a translator that turns loose human wording into strict machine rules. Like turning a recipe into exact oven settings.
> **DSL**: a tiny special purpose language for one job.
> **Deterministic**: same input, same output, every time. Like a vending machine.
> **Cited clauses**: quoting the exact line of the policy that justifies the answer.
> **Macro**: a canned reply that support staff paste in. More terms in [[Jargon Decoder]].

## Where to next
* ⬆️ Up: [[Idea Index]]
* ⬅️ Previous: [[I063 Price-Protection Autopilot]] · ➡️ Next: [[I065 Net-Landed Quote Engine]]
* 🎯 Theme: [[Theme E3 Evidence economy]]
* 🔗 Related: [[30 Primitives Legend]], [[Jargon Decoder]], [[00 PayPal AI Hackathon Hub]]
