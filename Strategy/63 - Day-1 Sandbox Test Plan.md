---
title: "63 - Day-1 Sandbox Test Plan"
type: strategy
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [plan, sandbox, tests]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Day-1 sandbox test plan (gating)

Every Top 3 ranking depends on PayPal sandbox behaviour that the docs leave ambiguous. Run these before writing product code. Deadline: **Nov 12, 2026 12:00pm PT** (about 4.5 weeks from 2026-10-12).

| ID | For | Test | Pass means | If it fails |
|---|---|---|---|---|
| T1 | #23 | Capture a sandbox order with a shipping address; `GET /v2/checkout/orders/{id}`. Check `purchase_units[].payments.captures[].seller_protection`. Vary `shipping_preference: NO_SHIPPING`, pickup shipping type, guest card. Then `POST /v2/checkout/orders/{id}/track` and look at the sandbox UI. | `seller_protection.status` can change, and the tracker is visible | Verdict must come from a policy rules table. Say so honestly in the video. Consider the Wrong Box pivot |
| T2 | Wrong Box | `POST /v1/customer/disputes` with buyer `PayPal-Auth-Assertion` on an Orders v2 capture. Confirm `allowed_response_options.make_offer` contains `REPLACEMENT_WITHOUT_REFUND`, then `accept-offer` resolves the case | Case reaches RESOLVED | Drive from a UI-created dispute. If the replacement offer is unavailable the hero moment collapses to a refund and Wrong Box drops below #55 |
| T3 | Wrong Box | Payout from a second sandbox business app to the buyer's personal sandbox email | Balance visible on the buyer | Show the payout response and webhook only |
| T4 | #55 | `POST /v1/payments/payouts` to an unregistered email. Confirm `UNCLAIMED` with `RECEIVER_UNREGISTERED`, the `PAYMENT.PAYOUTS-ITEM.UNCLAIMED` webhook, then `POST .../payouts-item/{id}/cancel` → RETURNED | Whole loop works for real | Demote #55 below #56 |
| T5 | #28 | Create invoice conditional rules (`EARLY_PAYMENT_DISCOUNT`); see whether the payer view applies the discount | Discount visible and applied | Scope `invoicing/internal` is gated, so #28 loses its demo |
| T6 | #56 | Inject `PayPal-Mock-Response` through a proxy into a merchant SDK call; check whether any sandbox state changes | Fault paths reproducible | Falls back to mock responses only |
| T7 | #42 | Reproduce the counterfactual flip against a v6 checkout with injected product text | Flip and capture block shown | Drop |
| T8 | #8, #9 | Overcapture above 100% on a sandbox authorization; reauthorize once (day 4 to 29) | Enforced as documented | Branch removed |
| T9 | Wrong Box | `GET dispute` → `disputed_transactions[0].custom` equals the order `custom_id` | Equal | Bind through invoice_id or a local table |
| T10 | Wrong Box | `provide-evidence` multipart with a PDF under 10 MB | Success | Avoid `INVALID_EVIDENCE_FILE` by trimming |

Sources for these tests: [PayPal Disputes test & go-live](https://developer.paypal.com/disputes/test-go-live.md) ✅, [Payouts test values](https://developer.paypal.com/api/payouts/test-go-live.md) ✅, [Add Tracking API](https://developer.paypal.com/api/tracking/track-orders/integrate.md) ✅.

## Indicative 4.5-week plan for #23 (⚠ inference)
| Week | Goal |
|---|---|
| 1 (to Oct 19) | T1 to T10; repo, README skeleton, PayPal sandbox apps; decision on #23 vs pivot |
| 2 | Ingest orders and buyer messages; address and policy rules engine with cited clauses |
| 3 | AI layer: intent with quoted span, fuzzy address equivalence, label OCR; tracking upload; evidence pack |
| 4 | AG Grid order queue; unhappy-path tests; webhook handling; polish |
| 4.5 (to Nov 12) | 3-minute video, README "PayPal APIs used" and "Unhappy paths handled", submission buffer |
