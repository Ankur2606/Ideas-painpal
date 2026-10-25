---
title: "#90 Agentic RFQ Desk"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E9, survivor, easy-read]
up: "[[Idea Index]]"
id: 90
theme: E9
group: "Trades & B2B ops"
desk_score: 69
final_score: 69
status: SURVIVOR
verdict: desk-only
kills: []
aliases: [Agentic RFQ Desk]
summary: "Incoming quote request emails for small manufacturers become priced quotes and PayPal deposit invoices, drafted by an agent and approved by a person."
---
# #90 Agentic RFQ Desk

> [!tldr] In one breath
> Incoming quote request emails for small manufacturers become priced quotes and PayPal deposit invoices, drafted by an agent and approved by a person. It survived with 69/120, though it is niche.

> [!example] Picture this
> A small metal shop gets an email: "Need 200 brackets, 3mm steel, by the 20th." It sits for two days. With this desk the agent reads it, applies the shop's pricing rules, drafts the quote, and prepares the deposit invoice. The owner clicks approve.

> [!warning] Crowd check, Oct 23 2026
> Related but not the same: procurement agents (procure-agent, procurepilot, procura-ai, reliefos) sit on the buyer side, and the invoicing cluster is crowded (about 25). No repo for the seller side quote desk showed up, so the exact idea looks thin.

**Where it landed:** ✅ SURVIVOR. Desk score 69/120, final score 69/120, verdict `desk-only`.

**Theme:** E9 Agents as economic actors & B2B ops · **Group:** Trades & B2B ops · **Crowding on Devpost (first pass):** none

## The problem
Small job shops lose deals because quoting is slow.

## The fix
**Email parsing, pricing rules, a quote document, and a deposit invoice.**

## Who it is for
Small manufacturers and wholesalers.

## What the AI does
Extraction and pricing.

## How it uses PayPal
Invoicing.

**Building blocks used** (decoded in [[30 Primitives Legend]]):
* `P08` Invoicing v2 (create, send, partial payment)
* `A01` Document / image extraction (OCR, validation)
* `A03` Intent and rationale reasoning (LLM-as-judge)

## Who else is out there
Paperless Parts. Manufacturing quoting software exists.

> [!warning] How sure are we?
> ⚠️ Desk research only. The competitor names above come from the landscape and Devpost scans, not from a hunt for each idea. Treat "no competitor found" as unproven.

## What makes it different
Aimed at small businesses, with a PayPal deposit.

## Can we build it?
**Feasibility:** High.

## The demo we would show
Email, then quote, then invoice.

## What could go wrong
Niche.

## Evidence and sources
* [KC Fed: B2B payments still ~90% use checks](https://www.kansascityfed.org/research/payments-system-research-briefings/b2b-payments-business-processing-and-challenges-to-achieving-straight-through-processing/) ⚠️

## Scores
Each of the five judging areas is scored 0 to 10 and counts double. Feasibility and low risk count once. The maximum is 120.

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

*Why (desk):* Niche.

**Kill criteria:** none triggered.

## How it would flow
```mermaid
flowchart LR
    A["Quote request email arrives"]
    B["Agent extracts specs and quantity"]
    C["Pricing rules applied"]
    D["Quote drafted for human approval"]
    E["PayPal deposit invoice sent"]
    A --> B --> C --> D --> E
```

> [!info]- Jargon decoder
> **RFQ**: request for quote, the message where a buyer asks "how much for this?".
>
> **Human in the loop**: a person approves before anything is sent, like a manager signing off.
>
> **LLM as judge (A03)**: using one AI to review or score another AI's work.
>
> **Deposit invoice**: an invoice for a part payment up front.

## Where to next
* ⬆️ Up: [[Idea Index]]
* ⬅️ Previous: [[I089 Voice-Note Invoicing]] · ➡️ Next: [[I091 Event Vendor Settlement]]
* 🔗 Theme: [[Theme E9 Agents as economic actors & B2B ops]]
* 🔗 Related: [[41 Brutal Elimination]], [[30 Primitives Legend]], [[00 PayPal AI Hackathon Hub]]
