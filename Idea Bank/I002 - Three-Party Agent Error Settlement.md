---
title: "#2 Three-Party Agent Error Settlement"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor, deep-dived]
up: "[[Idea Index]]"
id: 2
theme: E1
group: "Agent purchase liability"
desk_score: 95
final_score: 72
status: SURVIVOR
verdict: demote
kills: []
---
# #2 Three-Party Agent Error Settlement

> When an agent's purchase goes wrong, decide who should pay — merchant, agent platform or buyer — and settle each share on PayPal rails automatically.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** none observed

## Problem statement
Agent mistakes create a three-party liability problem (buyer, merchant, agent provider) that card reason codes and existing dispute flows treat as two-party. Payments Association data shows no answer above 24% among UK merchants; NMI finds consumers would blame the AI provider (62%) before the retailer (34%).

## Proposed solution
A settlement engine that ingests an agent order, the human's instruction and the delivery outcome, applies a published liability matrix (merchant fault → merchant refund/replacement via make-offer; agent fault → agent platform reimburses the buyer via Payouts; ambiguous instruction → split), and executes each leg with an explanation every party can read.

## Target users
Agent platforms that want to offer a "we'll make it right" guarantee; merchants selling to agents; buyers.

## AI contribution
Fault attribution from order + instruction + delivery evidence (vision on delivered-item photo), liability-matrix reasoning with cited rules, plain-language settlement explanations.

## PayPal integration
Disputes (make-offer, accept-claim) for merchant legs; Payouts (incl. Venmo handle) for agent-platform reimbursement; Refunds; webhooks; Orders metadata.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P11` Payouts (batch)
- `P12` Payouts to Venmo handles
- `P16` Refunds (full / partial)
- `P20` Webhooks (events, retries, verification)
- `P31` custom_id / invoice_id metadata binding
- `A02` Classification with explanation / vision estimation
- `A05` Structured decision / classification (most common)
- `A16` Policy / rule reasoning with cited clauses

## Competitors and prior art
Chargeflow, Justt, Rye

Dispute-management vendors fight two-party card chargebacks for merchants; agent-checkout APIs (Rye) don't own liability for wrong orders. No product settles three-way.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D002 - Three-Party Agent Error Settlement (Deep Dive)]].

## Differentiation
First to model the agent provider as a liable, payable party, using Payouts as the reimbursement rail.

## Feasibility
Sandbox supports every leg (disputes factory, payouts test values). The liability matrix is a design artefact, not research.

## MVP scope
Three scripted scenarios (wrong size, merchant shipped wrong item, ambiguous instruction) each producing different settlement legs live in sandbox, plus a settlement ledger UI.

## Risks
Legal framing must be "proposed rulebook", not legal advice; agent platforms may not want liability; forward-looking demand.

## Credible references
- [Worldpay — 'No liability shift exists yet' for agent disputes (Jul 2026)](https://worldpay.com/insights/articles/agentic-commerce-liability-is-still-being-written) ✅
- [The Payments Association — UK merchants: no consensus on agent liability (May 2026)](https://thepaymentsassociation.org/article/agentic-commerce-uk-retail-an-unresolved-liability-question/) ✅
- [NMI Aug 2026 — 76% uncomfortable with AI completing purchases; 58% fear wrong item](https://www.nmi.com/about-us/news/nmi-research-consumers-want-ai-to-help-them-shop-not-control-their-spending/) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅
- [PayPal Payouts sandbox test values (ERRPYO0xx)](https://developer.paypal.com/api/payouts/test-go-live.md) ✅
- [Chargeflow — agent disputes don't fit reason codes; VAMP thresholds](https://www.chargeflow.io/blog/agentic-commerce-regulation-what-merchants-need-to-know) ⚠️

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 9 | 8 |
| Design | ×2 | 7 | 6 |
| Impact | ×2 | 7 | 6 |
| Innovation | ×2 | 9 | 3 |
| Demo | ×2 | 8 | 7 |
| Feasibility | ×1 | 8 | 7 |
| Risk⁻¹ | ×1 | 7 | 5 |
| **Total /120** | | **95** | **72** |

_Why (desk):_ Genuinely new mechanism with multi-API depth; impact is forward-looking.

**Kill criteria:** none triggered.

## Deep-dive verdict: demote
Mechanism already on Devpost (Provenant); survive only as the agent-fault Payouts fork triggered by #3's delivery check.

_Score changes:_ 'No product settles three-way' is false: Provenant (Devpost, same hackathon by sponsor tags) splits fault user/merchant/agent with Shapley values and pays the agent's share via Payouts from a liability pool plus dispute evidence; Amex Agent Purchase Protection (Apr 2026) covers buyers for AI-agent error. No network rule makes agent platforms liable, so demand for the Payouts leg is speculative. Matrix is a lookup table; three personas hurt design/demo.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
