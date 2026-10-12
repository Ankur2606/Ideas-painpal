---
title: "#20 Dispute-to-Listing Fixer"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E3, survivor, deep-dived]
up: "[[Idea Index]]"
id: 20
theme: E3
group: "Evidence economy"
desk_score: 97
final_score: 80
status: SURVIVOR
verdict: demote
kills: []
---
# #20 Dispute-to-Listing Fixer

> Mines "not as described" disputes and buyer messages to find the listings that cause them — then rewrites those listings before the next dispute.

**Theme:** E3 Evidence economy · **Group:** Evidence economy · **Crowding on Devpost:** Disputes cluster adjacent, but a different mechanism

## Problem statement
Disputes are treated one at a time; the root cause (a misleading photo, a missing dimension) keeps generating new ones. SNAD claims aren't covered by Seller Protection at all.

## Proposed solution
Clusters dispute reasons and messages by product, identifies the misleading attribute, proposes listing edits (and image annotations), updates the catalog, and tracks the dispute rate before vs after.

## Target users
SMB merchants and marketplace sellers.

## AI contribution
Clustering and root-cause extraction from dispute text; listing rewrite; vision check of photos vs claims.

## PayPal integration
Disputes list/get (messages, reasons); Catalog Products API update; Transaction Search for rates; webhooks.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P14` Disputes API (get, messages, make-offer, accept-offer, provide-evidence)
- `P15` Disputes sandbox factory (create, adjudicate)
- `P30` Catalog products / billing plans
- `P18` Transaction Search / Reporting
- `P20` Webhooks (events, retries, verification)
- `A06` Entity matching and narrative drafting
- `A05` Structured decision / classification (most common)
- `A02` Classification with explanation / vision estimation

## Competitors and prior art
Chargeflow, Yotpo, Amazon Voice of the Customer

Marketplaces show listing-quality dashboards internally (Amazon's Voice of the Customer); dispute vendors fight cases rather than prevent the next one. No PayPal-native closed loop found.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D020 - Dispute-to-Listing Fixer (Deep Dive)]].

## Differentiation
Moves disputes from "defend" to "prevent", using the dispute API as a product-feedback channel.

## Feasibility
High; the sandbox dispute factory can seed realistic SNAD clusters.

## MVP scope
Seed 20 sandbox disputes over 4 products; fixer finds "sizing runs small" on one; rewrites listing; projected dispute reduction.

## Risks
Before/after impact can only be simulated within the hackathon.

## Credible references
- [PayPal Seller Protection Program (ship-to address rule, SNAD excluded, intangibles evidence)](https://www.paypal.com/us/legalhub/paypal/seller-protection) ✅
- [PayPal Disputes test & go-live — sandbox create/chargeback/adjudicate endpoints](https://developer.paypal.com/disputes/test-go-live.md) ✅
- [Mastercard/Datos 2025 State of Chargebacks — 261M→324M by 2028; 45% fraudulent](https://www.mastercard.com/us/en/news-and-trends/Insights/2025/2025-global-chargebacks-outlook.html) ✅
- [Chargebacks911 2026 Field Report — SMBs represent only 60.3%; evidence collection #1 pain](https://chargebacks911.com/chargeback-field-report/) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 8 | 7 |
| Design | ×2 | 8 | 7 |
| Impact | ×2 | 8 | 6 |
| Innovation | ×2 | 8 | 6 |
| Demo | ×2 | 8 | 7 |
| Feasibility | ×1 | 9 | 7 |
| Risk⁻¹ | ×1 | 8 | 7 |
| **Total /120** | | **97** | **80** |

_Why (desk):_ Prevention loop is fresh and deeply PayPal-native.

**Kill criteria:** none triggered.

## Deep-dive verdict: demote
The data is real but the PayPal-side fix is cosmetic and ReasonWhy already does the same loop on returns; better as a prevention tab inside a dispute or ship-safe product.

_Score changes:_ Dispute data is rich enough to cluster: GET dispute has reason, sub_reasons, buyer product_details.description, purchase_url, items[] and messages[]. But the PayPal 'fix' step is cosmetic: /v1/catalogs/products backs Subscriptions, not storefronts, so the real fix goes to Shopify/Woo. ReasonWhy (Shopify, Jun 2026) already ships the cluster -> page-fix -> before/after loop on returns, and Return Insights AI, Vortex IQ ASIN clusters and Amazon VoC are adjacent. No primary figure found for the SNAD share of disputes. Competitor search was cut short by the shared search budget.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
