---
title: "#82 Win-Back Agent"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E8, eliminated, easy-read]
up: "[[Idea Index]]"
id: 82
theme: E8
group: "Subscription revenue ops"
desk_score: 65
final_score: 65
status: ELIMINATED
verdict: desk-only
kills: [K2]
aliases: [Win-Back Agent]
summary: "Reaches out to people who cancelled a PayPal subscription with a tailored offer and a one click resubscribe link."
---
# #82 Win-Back Agent

> [!tldr] In one breath
> Reaches out to people who cancelled a PayPal subscription with a tailored offer and a one click resubscribe link. Cut as derivative (K2): Churnkey exists and a MACH winner, SilentWatch, did churn reactivation.

> [!example] Picture this
> Ana cancelled a language app in March. In June she gets a note: "We added Portuguese. Come back for half price?" One tap and she is subscribed again.

> [!success] Crowd check, Oct 23 2026
> Nothing matching in the 266 repo scan (partial coverage). Subscriptions looked thin. Outside the hackathon, retention tools are mature.

**Where it landed:** ❌ ELIMINATED. Desk score 65/120, final score 65/120, verdict `desk-only`. Kill codes: K2.

**Theme:** E8 Failure-path intelligence · **Group:** Subscription revenue ops · **Crowding on Devpost (first pass):** none

## The problem
Winning back a customer is cheaper than finding a new one.

## The fix
**Sort cancelled customers into groups, message them, and send a resubscribe link.**

## Who it is for
Small subscription businesses.

## What the AI does
Personalisation.

## How it uses PayPal
Subscriptions and webhooks.

**Building blocks used** (decoded in [[30 Primitives Legend]]):
* `P07` Subscriptions (revise, suspend, payment-failed events)
* `P20` Webhooks (events, retries, verification)
* `A12` Eligibility reasoning and messaging

## Who else is out there
Churnkey. The category exists, and MACH winner SilentWatch did churn reactivation.

> [!warning] How sure are we?
> ⚠️ Desk research only. The competitor names above come from the landscape and Devpost scans, not from a hunt for each idea. Treat "no competitor found" as unproven.

## What makes it different
Low.

## Can we build it?
**Feasibility:** High.

## The demo we would show
A list of cancelled customers turns into offers.

## What could go wrong
Low novelty.

## Scores
Each of the five judging areas is scored 0 to 10 and counts double. Feasibility and low risk count once. The maximum is 120.

| Axis | Weight | Desk score |
|---|---|---|
| Tech | ×2 | 6 |
| Design | ×2 | 6 |
| Impact | ×2 | 4 |
| Innovation | ×2 | 3 |
| Demo | ×2 | 5 |
| Feasibility | ×1 | 9 |
| Risk⁻¹ | ×1 | 8 |
| **Total /120** | | **65** |

*Why (desk):* Derivative.

**Kill criteria triggered:** `K2` Crowded cluster or derivative headline; innovation cannot be defended (too many teams will build the same thing). See [[41 Brutal Elimination]].

## How it would flow
```mermaid
flowchart LR
    A["Subscriber cancels"]
    B["Webhook records it"]
    C["AI picks a tailored offer"]
    D["Message with resubscribe link"]
    E["Customer returns"]
    A --> B --> C --> D --> E
```

> [!info]- Jargon decoder
> **Reactivation**: getting a lapsed customer to come back, like a shop calling a regular who stopped visiting.
>
> **Webhook**: an automatic ping from PayPal when an event happens, like a doorbell.
>
> **Personalisation**: adjusting a message to one person instead of sending the same text to all.

## Where to next
* ⬆️ Up: [[Idea Index]]
* ⬅️ Previous: [[I081 Pause-Not-Cancel Retention]] · ➡️ Next: [[I083 Spec-to-Plan Billing Compiler]]
* 🔗 Theme: [[Theme E8 Failure-path intelligence]]
* 🔗 Related: [[41 Brutal Elimination]], [[30 Primitives Legend]], [[00 PayPal AI Hackathon Hub]]
