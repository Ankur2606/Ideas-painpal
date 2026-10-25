---
title: "#95 Agent Spend Reconciler"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E4, eliminated, easy-read]
up: "[[Idea Index]]"
id: 95
theme: E4
group: "Merchant risk intelligence"
desk_score: 64
final_score: 64
status: ELIMINATED
verdict: desk-only
kills: [K6]
aliases: [Agent Spend Reconciler]
summary: "Checks what a business's AI agents actually spent across PayPal, virtual cards and wallets against what they were told to buy."
---
# #95 Agent Spend Reconciler

> [!tldr] In one breath
> Checks what a business's AI agents actually spent across PayPal, virtual cards and wallets against what they were told to buy. Cut because it is infrastructure with no watchable demo (K6).

> [!example] Picture this
> A small company lets three AI agents buy supplies. At month end the boss asks: "Did they buy only what I asked?" Each payment tool shows only its own spending. This tool puts all of them in one list and flags the odd ones.

> [!warning] Crowd check, Oct 23 2026
> Reconciliation is a smaller cluster in the scan (settlesight, settleproof, cleared-settle, creatorsettle), and agent spending guardrails are the most saturated area (about 30).

**Where it landed:** ❌ ELIMINATED. Desk score 64/120, final score 64/120, verdict `desk-only`. Kill codes: K6.

**Theme:** E4 Locked money & cash-flow · **Group:** Merchant risk intelligence · **Crowding on Devpost (first pass):** Reconciliation cluster

## The problem
Closed loop spend tools only reconcile their own payment methods.

## The fix
**Pull in the ledgers, match them with the instructions given, and list the exceptions.**

## Who it is for
Small businesses that use agents.

## What the AI does
Matching and explaining exceptions.

## How it uses PayPal
Transaction Search and Orders metadata.

**Building blocks used** (decoded in [[30 Primitives Legend]]):
* `P18` Transaction Search / Reporting
* `P31` custom_id / invoice_id metadata binding
* `A06` Entity matching and narrative drafting

## Who else is out there
Ramp, Brex. Closed loop spend platforms.

> [!warning] How sure are we?
> ⚠️ Desk research only. The competitor names above come from the landscape and Devpost scans, not from a hunt for each idea. Treat "no competitor found" as unproven.

## What makes it different
Works across payment rails.

## Can we build it?
**Feasibility:** Medium. The other rails would be mocked.

## The demo we would show
A mixed ledger reconciliation.

## What could go wrong
A table demo, and the demand is speculative.

## Evidence and sources
* [Ramp: Agent Cards, Policy Agent](https://ramp.com/blog/ai-agents-finance) ✅

## Scores
Each of the five judging areas is scored 0 to 10 and counts double. Feasibility and low risk count once. The maximum is 120.

| Axis | Weight | Desk score |
|---|---|---|
| Tech | ×2 | 6 |
| Design | ×2 | 5 |
| Impact | ×2 | 4 |
| Innovation | ×2 | 6 |
| Demo | ×2 | 4 |
| Feasibility | ×1 | 7 |
| Risk⁻¹ | ×1 | 7 |
| **Total /120** | | **64** |

*Why (desk):* Speculative, and the demo is just a table.

**Kill criteria triggered:** `K6` Infrastructure with no watchable demo (it is plumbing that is hard to show in a 3 minute video). See [[41 Brutal Elimination]].

## How it would flow
```mermaid
flowchart LR
    A["Agents spend on several rails"]
    B["Ledgers pulled into one list"]
    C["AI matches spend to instructions"]
    D["Mismatches flagged"]
    E["Owner reviews exceptions"]
    A --> B --> C --> D --> E
```

> [!info]- Jargon decoder
> **Reconciliation**: matching two lists until they agree, like checking your till against your receipts.
>
> **Closed loop**: a system that only sees its own transactions, like a store gift card that works only in that store.
>
> **Payment rails**: the different roads money travels on, such as card, PayPal or wallet.
>
> **Metadata binding (P31)**: tagging each PayPal order with a custom ID so it can be matched later.

## Where to next
* ⬆️ Up: [[Idea Index]]
* ⬅️ Previous: [[I094 Fraud Ring Graph]] · ➡️ Next: [[I096 PayPal Ops Control Room]]
* 🔗 Theme: [[Theme E4 Locked money & cash-flow]]
* 🔗 Related: [[41 Brutal Elimination]], [[30 Primitives Legend]], [[00 PayPal AI Hackathon Hub]]
