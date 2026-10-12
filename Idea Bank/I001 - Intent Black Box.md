---
title: "#1 Intent Black Box"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor, deep-dived]
up: "[[Idea Index]]"
id: 1
theme: E1
group: "Agent purchase liability"
desk_score: 92
final_score: 71
status: SURVIVOR
verdict: demote
kills: []
---
# #1 Intent Black Box

> A flight recorder for shopping agents that binds "what the agent saw and was told" to the PayPal order, so an agent dispute can be adjudicated instead of argued.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent purchase liability · **Crowding on Devpost:** Adjacent to ~13 spend-gate/receipt entries

## Problem statement
When an AI agent buys the wrong thing, nobody can reconstruct why. Signed mandates (AP2, Verifiable Intent) prove what was signed, not whether the cart matched the human's goal or whether the agent was manipulated before signing. Worldpay says no liability shift exists for "authorized but wrong" agent purchases, and UK merchants show no consensus on who pays.

## Proposed solution
An SDK that wraps any agent's checkout step. It records the instruction, the candidate set, tool outputs, page snippets and the agent's rationale; hashes the transcript (Merkle root) into the PayPal order's custom_id / invoice_id; stores the full record off-chain; and, when a dispute webhook fires, an AI adjudicator replays the record and classifies the case (agent out-of-scope, merchant SNAD, buyer instruction ambiguity, friendly fraud) and drafts the response via the Disputes API.

## Target users
Agent builders who let agents pay; merchants receiving agent-originated orders; (later) PayPal's own Resolution Center.

## AI contribution
Rationale capture, transcript summarisation, scope-vs-instruction comparison (LLM-as-judge with rubric), dispute classification and evidence drafting.

## PayPal integration
Orders v2 with custom_id/invoice_id binding; Disputes API (get, provide-evidence, make-offer) driven end-to-end with the sandbox dispute factory; CUSTOMER.DISPUTE.CREATED webhooks; Refunds.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `P31` custom_id / invoice_id metadata binding
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P15` Disputes sandbox factory (create, adjudicate)
- `P20` Webhooks (events, retries, verification)
- `P16` Refunds (full / partial)
- `A13` Vision verification / evidence narrative
- `A05` Structured decision / classification (most common)
- `A03` Intent and rationale reasoning (LLM-as-judge)

## Competitors and prior art
Mastercard Verifiable Intent, Google AP2, Catena Labs ACK, Skyfire KYAPay

Mandate/intent standards sign the authorisation but stop before the evidence and adjudication step; Devpost already shows "evidence gate" and agent-receipt entries (VELQIRIS Evidence Gate, XReceipt), so the differentiator must be pre-signature context + dispute adjudication, not receipts alone.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D001 - Intent Black Box (Deep Dive)]].

## Differentiation
Captures pre-signature context (the documented hole in AP2 v0.2) and closes the loop into a live PayPal dispute, rather than producing a receipt nobody reads.

## Feasibility
All needed APIs are sandbox-available; sandbox dispute creation lets the demo run a full lifecycle deterministically. Hardest part is a clean, framework-agnostic capture SDK.

## MVP scope
One shopping agent (OpenAI Agents SDK + PayPal agent-toolkit), recorder middleware, order binding, a dispute triggered via sandbox endpoint, adjudicator verdict + evidence posted, and a viewer showing instruction vs purchase diff.

## Risks
Judges may lump it with the crowded "agent receipts/gates" cluster; privacy of recorded context; no agent-dispute volume data yet (forward-looking impact).

## Credible references
- [Worldpay — 'No liability shift exists yet' for agent disputes (Jul 2026)](https://worldpay.com/insights/articles/agentic-commerce-liability-is-still-being-written) ✅
- [Beyond the Mandate — 48 threats vs AP2 v0.2 (arXiv 2608.23858)](https://www.emergentmind.com/papers/2608.23858) ✅
- [Mastercard Verifiable Intent (Mar 2026)](https://www.mastercard.com/au/en/news-and-trends/stories/2026/verifiable-intent.html) ✅
- [The Payments Association — UK merchants: no consensus on agent liability (May 2026)](https://thepaymentsassociation.org/article/agentic-commerce-uk-retail-an-unresolved-liability-question/) ✅
- [NMI Aug 2026 — 76% uncomfortable with AI completing purchases; 58% fear wrong item](https://www.nmi.com/about-us/news/nmi-research-consumers-want-ai-to-help-them-shop-not-control-their-spending/) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅
- [Chargeflow — agent disputes don't fit reason codes; VAMP thresholds](https://www.chargeflow.io/blog/agentic-commerce-regulation-what-merchants-need-to-know) ⚠️

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 9 | 8 |
| Design | ×2 | 7 | 6 |
| Impact | ×2 | 7 | 6 |
| Innovation | ×2 | 7 | 3 |
| Demo | ×2 | 8 | 6 |
| Feasibility | ×1 | 8 | 7 |
| Risk⁻¹ | ×1 | 8 | 6 |
| **Total /120** | | **92** | **71** |

_Why (desk):_ Deep PayPal use and a documented research gap; innovation docked for proximity to the receipt cluster.

**Kill criteria:** none triggered.

## Deep-dive verdict: demote
Mechanism already shipped by Provenant/AgentProof; keep only the normalized-instruction record as the evidence spine for #3.

_Score changes:_ Provenant (Devpost, same hackathon by ag-grid/render tags) already binds custom_id to a hash of the agent decision trace with replay and a dispute evidence pack; AgentProof builds PayPal provide-evidence for agent disputes; Amex ACE (Apr 2026) captures intent + cart context for disputes; Chargebacks911 UDMS records agent consent. Hash binding is invisible on video; sandbox dispute creation is absent from public OpenAPI (day-1 test).

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
