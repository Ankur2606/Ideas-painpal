---
title: "#3 Mismatch-to-Replacement"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor, deep-dived]
up: "[[Idea Index]]"
id: 3
theme: E1
group: "Agent purchase liability"
desk_score: 93
final_score: 87
status: SURVIVOR
verdict: advance-with-changes
kills: []
---
# #3 Mismatch-to-Replacement

> The buyer photographs what the agent bought; AI checks it against the original instruction and triggers a merchant replacement offer before anyone files a dispute.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** Disputes/refunds cluster (~7) adjacent

## Problem statement
58% of US adults fear an AI will buy the wrong item, size or colour (NMI). "Not what I wanted" becomes a chargeback that hurts merchant ratios even though a replacement would have satisfied everyone.

## Proposed solution
A post-delivery check-in. The buyer snaps the item; a vision model compares it with the instruction and the product listing; if mismatched, the system opens a structured resolution with the merchant (replacement or partial refund) and only escalates to a PayPal dispute if the merchant declines.

## Target users
Consumers using shopping agents; merchants who want to keep agent orders out of dispute ratios.

## AI contribution
Vision comparison of delivered item vs listing vs instruction; mismatch explanation; negotiation of resolution options.

## PayPal integration
Orders metadata; Refunds (partial); Disputes make-offer (replacement) and send-message when escalated; tracking API for delivery confirmation; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P16` Refunds (full / partial)
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P17` Shipment Tracking API (add tracking; releases holds)
- `P20` Webhooks (events, retries, verification)
- `A02` Classification with explanation / vision estimation
- `A07` Multi-agent negotiation

## Competitors and prior art
Loop Returns, Narvar, AfterShip Returns

Returns platforms handle merchant-initiated RMA flows; none compare against the agent's instruction or sit before a PayPal dispute.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D003 - Mismatch-to-Replacement (Deep Dive)]].

## Differentiation
Pre-dispute deflection specifically for agent errors, keyed to the instruction rather than the listing alone.

## Feasibility
High; vision models handle colour/size/model mismatch well enough for a demo.

## MVP scope
Upload photo → mismatch verdict → merchant offer flow → partial refund executed in sandbox; escalation path opens a sandbox dispute.

## Risks
Vision false positives; buyer-side app needs merchant cooperation in the real world.

## Credible references
- [NMI Aug 2026 — 76% uncomfortable with AI completing purchases; 58% fear wrong item](https://www.nmi.com/about-us/news/nmi-research-consumers-want-ai-to-help-them-shop-not-control-their-spending/) ✅
- [Worldpay — 'No liability shift exists yet' for agent disputes (Jul 2026)](https://worldpay.com/insights/articles/agentic-commerce-liability-is-still-being-written) ✅
- [Mastercard/Datos 2025 State of Chargebacks — 261M→324M by 2028; 45% fraudulent](https://www.mastercard.com/us/en/news-and-trends/Insights/2025/2025-global-chargebacks-outlook.html) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 7 | 7 |
| Design | ×2 | 8 | 8 |
| Impact | ×2 | 7 | 6 |
| Innovation | ×2 | 7 | 6 |
| Demo | ×2 | 9 | 9 |
| Feasibility | ×1 | 9 | 8 |
| Risk⁻¹ | ×1 | 8 | 7 |
| **Total /120** | | **93** | **87** |

_Why (desk):_ Excellent demo moment; moderate PayPal depth.

**Kill criteria:** none triggered.

## Deep-dive verdict: advance-with-changes
Make this the spine: photo of what arrived vs what the human asked decides merchant-replacement (Disputes) vs agent-platform payout (Payouts), pre-chargeback.

_Score changes:_ Only cluster mechanism not found on Devpost: instruction x listing x delivered-photo comparison feeding PayPal make-offer (REPLACEMENT_WITHOUT_REFUND) before a claim, or a Payouts reimbursement when the agent erred. Innovation docked for Loop AI Image Recognition / PixelProof photo checks, XReceipt 'did the two match', Provenant fault split; impact docked (NMI vendor survey, no agent-dispute volume); feasibility docked for vision reliability and day-1 sandbox dispute-create test. Combined with #1 binding + #2 payout fork: [8,8,6,6,9,7,7].

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
