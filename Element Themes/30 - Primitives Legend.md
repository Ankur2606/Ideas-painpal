---
title: "30 - Primitives Legend"
type: reference
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [elements, legend]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Primitives legend (P = PayPal, A = AI, S = sponsor)

> ⚠ The idea records tag each idea with element codes. The original code table was not saved, so these labels are **reconstructed from how each code is used** across the 100 ideas. Treat the exact wording as an inference. Usage counts are exact.

## PayPal primitives

| Code | Meaning | Ideas using it |
|---|---|---|
| P01 | Orders v2 (create / capture / get) | 25 |
| P02 | AUTHORIZE intent (hold funds) | 12 |
| P03 | Authorization lifecycle: partial capture, void, reauthorize | 9 |
| P04 | Overcapture (capture above the authorized amount, within 115% / +$75) | 1 |
| P05 | Orders PATCH (change an order before capture) | 1 |
| P06 | Vault v3 (saved payment tokens, payer-not-present charges) | 6 |
| P07 | Subscriptions (revise, suspend, payment-failed events) | 12 |
| P08 | Invoicing v2 (create, send, partial payment) | 17 |
| P09 | Invoicing conditional rules (early-payment discount, auto-cancel) | 2 |
| P10 | Invoicing recurring series / record payment | 3 |
| P11 | Payouts (batch) | 14 |
| P12 | Payouts to Venmo handles | 4 |
| P13 | Payouts failure handling and test values (UNCLAIMED, cancel, RETURNED, ERRPYO codes) | 3 |
| P14 | Disputes API (get, messages, make-offer, accept-offer, provide-evidence) | 18 |
| P15 | Disputes sandbox factory (create, adjudicate) | 6 |
| P16 | Refunds (full / partial) | 11 |
| P17 | Shipment Tracking API (add tracking; releases holds) | 8 |
| P18 | Transaction Search / Reporting | 20 |
| P19 | Merchant insights / balances | 2 |
| P20 | Webhooks (events, retries, verification) | 23 |
| P21 | PayPal-Mock-Response header (sandbox fault injection) | 3 |
| P22 | Payment Links | 6 |
| P23 | Pay Later messaging | 4 |
| P24 | JS SDK v6 | 6 |
| P25 | Log in with PayPal | 3 |
| P26 | Multiparty / platform (partner-gated) | 1 |
| P27 | Agent Toolkit / MCP | 4 |
| P29 | Donate SDK / charity flows | 3 |
| P30 | Catalog products / billing plans | 5 |
| P31 | custom_id / invoice_id metadata binding | 6 |
| P32 | Seller Protection policy rules | 2 |

## AI primitives

| Code | Meaning | Ideas using it |
|---|---|---|
| A01 | Document / image extraction (OCR, validation) | 22 |
| A02 | Classification with explanation / vision estimation | 11 |
| A03 | Intent and rationale reasoning (LLM-as-judge) | 12 |
| A04 | Forecasting / pricing suggestion | 11 |
| A05 | Structured decision / classification (most common) | 25 |
| A06 | Entity matching and narrative drafting | 12 |
| A07 | Multi-agent negotiation | 5 |
| A08 | Speech / voice | 5 |
| A09 | Browser agents | 3 |
| A10 | Injection classifiers and provenance attribution | 1 |
| A11 | Translation / tone | 6 |
| A12 | Eligibility reasoning and messaging | 20 |
| A13 | Vision verification / evidence narrative | 9 |
| A14 | Diagnosis / code transformation | 4 |
| A15 | Anomaly detection | 6 |
| A16 | Policy / rule reasoning with cited clauses | 8 |

## Sponsor tooling

| Code | Meaning | Ideas using it |
|---|---|---|
| S01 | Sponsor tool: AG Grid / AG Studio (⚠ inferred) | 1 |
| S02 | Sponsor tool: APIMatic (⚠ inferred) | 0 |
| S03 | Sponsor tool: Channel3 (⚠ inferred) | 2 |
| S04 | Sponsor tool: KERNEL browser infrastructure (⚠ inferred) | 3 |
| S05 | Sponsor tool: Elastic / Render (⚠ inferred) | 1 |

## Observations
- Most-used PayPal primitives: Orders (P01), Webhooks (P20), Transaction Search (P18), Invoicing (P08), Disputes (P14). That is the "checkout-adjacent" centre of gravity, which is why the finalists below favour Tracking (P17), Payouts failure handling (P13), Disputes sandbox factory (P15) and conditional invoicing (P09).
- Least-used: Orders PATCH (P05), Overcapture (P04), Multiparty (P26). The first two are effectively only #8; the last is partner-gated.
- AI is dominated by classification / structured decisions (A05) and document extraction (A01). The highest-scoring ideas pair a *consequential* structured decision with a PayPal money-state change.
