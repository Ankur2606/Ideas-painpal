---
title: "#8 Final-Price Agent (Overcapture)"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E2, survivor, deep-dived]
up: "[[Idea Index]]"
id: 8
theme: E2
group: "Programmable holds"
desk_score: 90
final_score: 78
status: SURVIVOR
verdict: demote
kills: []
---
# #8 Final-Price Agent (Overcapture)

> For service businesses whose final price isn't known up front, authorise an estimate and let AI compute and justify the final amount within PayPal's overcapture ceiling.

**Theme:** E2 Programmable holds · **Group:** Programmable holds · **Crowding on Devpost:** none

## Problem statement
Trades, salons, repair shops and couriers quote an estimate, then chase a second payment when the job runs over — a late-payment trigger (59% of US SMBs have invoices 30+ days overdue).

## Proposed solution
Customer approves an estimate as an AUTHORIZE order; on completion, the worker dictates notes or uploads photos; AI computes the final amount, explains each delta, and captures up to 115% / +$75 of the authorisation, or issues an invoice for anything beyond.

## Target users
Service SMBs (auto repair, cleaning, handyman, salons, couriers).

## AI contribution
Notes/photo → line items; delta explanation; policy check against the customer's pre-approved ceiling.

## PayPal integration
Orders AUTHORIZE; capture with amount (overcapture); partial capture; Invoicing fallback; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P02` AUTHORIZE intent (hold funds)
- `P04` Overcapture (capture above the authorized amount, within 115% / +$75)
- `P03` Authorization lifecycle: partial capture, void, reauthorize
- `P08` Invoicing v2 (create, send, partial payment)
- `A01` Document / image extraction (OCR, validation)
- `A02` Classification with explanation / vision estimation
- `A08` Speech / voice

## Competitors and prior art
Square tip adjustment, Jobber, Housecall Pro

Field-service suites take deposits and send final invoices; restaurant tip-adjust uses card auth adjustments; nobody uses an AI-justified overcapture inside the consented ceiling.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D008 - Final-Price Agent (Overcapture) (Deep Dive)]].

## Differentiation
Turns PayPal's 115% overcapture rule — almost never used — into a "no second payment request" experience.

## Feasibility
High; overcapture is documented. Must verify sandbox enforces the ceiling (test early).

## MVP scope
Quote → authorise → job notes (voice) → AI final bill → capture; over-ceiling case falls back to invoice.

## Risks
Overcapture availability can depend on account eligibility; customer-trust UX must be explicit.

## Credible references
- [PayPal: authorization 29-day period, 3-day honor, reauth, capture ≤115%/+$75](https://developer.paypal.com/payment-methods/auth-honor.md) ✅
- [QuickBooks 2026 Late Payments Report — 59% have 30+ day overdue; $17.7K owed](https://quickbooks.intuit.com/r/small-business-data/small-business-late-payments-report-2026/) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 8 | 7 |
| Design | ×2 | 8 | 8 |
| Impact | ×2 | 6 | 5 |
| Innovation | ×2 | 8 | 6 |
| Demo | ×2 | 8 | 7 |
| Feasibility | ×1 | 7 | 6 |
| Risk⁻¹ | ×1 | 7 | 6 |
| **Total /120** | | **90** | **78** |

_Why (desk):_ Uses an underused PayPal primitive in a fresh way; evidence of pain is indirect.

**Kill criteria:** none triggered.

## Deep-dive verdict: demote
Keep as a branch inside a holds-based build (consented +15% buffer, over-ceiling -> invoice); not a standalone finalist.

_Score changes:_ Overcapture limit documented (115%/+$75, 'defaults to 115%' in MAX_CAPTURE_AMOUNT_EXCEEDED) but no published eligibility and unknown sandbox enforcement. State auto-repair laws (FL 559.905 disclosure; CA 9884.9) require customer consent to exceed estimates, so AI-set final prices need a pre-consented ceiling - incumbents (Tekmetric/Shopmonkey digital authorization, Housecall Pro/Pepper card-on-file & pre-auth) already cover that workflow. Demo moment is a JSON number.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
