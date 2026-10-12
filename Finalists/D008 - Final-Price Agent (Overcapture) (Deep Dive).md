---
title: "Deep dive: #8 Final-Price Agent (Overcapture)"
type: deep-dive
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [finalist, deep-dive, verdict/demote]
up: "[[50 - Top 10 Overview]]"
idea: "[[I008 - Final-Price Agent (Overcapture)]]"
verdict: demote
final_score: 78
---
> Idea note: [[I008 - Final-Price Agent (Overcapture)]] · Verdict: **demote** · Final score **78/120** (desk 90). Confidence tags: ✅ primary read directly · ⚠️ secondary / vendor / single source · ❌ unverified. `⚠ inference` marks judgment.

# #8 Final-Price Agent (Overcapture) — reserve deep dive (short)

## 1. Verdict

**Demote to reserve.** PayPal overcapture is documented: "up to 115% or $75 USD more than the original authorized amount, whichever is less" ✅. The Payments v2 error `MAX_CAPTURE_AMOUNT_EXCEEDED` reads "exceeds the overage limit, which defaults to 115% of the order amount across all captures" ✅. The word "defaults" implies the limit is per-account or configurable, and **no eligibility rules (region, account type, funding source) are published** in any of the three auth/capture pages I read. Whether the sandbox enforces the limit is unknown.

The law cuts against the pitch. The flagship vertical, auto repair, has estimate-consent laws:

- **Florida:** the statutory disclosure reads "THE SHOP MAY NOT EXCEED THIS AMOUNT WITHOUT MY WRITTEN OR ORAL APPROVAL" (§559.905) ✅. Overrun tolerance is in §559.909(1), which I didn't read (commonly cited as 10% or $10, max $50) ❌.
- **California:** B&P §9884.9 requires consent for any charge above the written estimate ⚠️ (secondary sources only).

So "AI decides the final price and captures more" is legally a non-starter for auto repair unless the customer pre-consents to a ceiling. That turns the product into "estimate + consented buffer", which Tekmetric and Shopmonkey already digitise with text-to-approve authorizations, and which Housecall Pro and Pepper cover with card-on-file auto-charge and pre-authorized payments.

**Adjusted** [tech, design, impact, innovation, demo, feasibility, risk] = **[7, 8, 5, 6, 7, 6, 6]** (was [8,8,6,8,8,7,7]).

| Axis | Change | Reason |
|---|---|---|
| Tech | −1 | Auth + capture(+over) + invoice fallback is fewer distinct capabilities than #9 |
| Impact | −1 | Only indirect evidence (late payment). Consent laws show regulators treat overruns as a consumer harm. |
| Innovation | −2 | Estimate-approval flows (Tekmetric, Shopmonkey), card-on-file auto-charge (Housecall Pro, Pepper), restaurant tip-adjust. Stripe also offers card overcapture for some industries (❌ not verified this run). |
| Demo | −1 | A capture of $1,075 on a $1,000 auth is a JSON number, not a visual moment |
| Feasibility | −1 | Overcapture eligibility and sandbox enforcement unknown; partial-capture enablement needed |
| Risk | −1 | Legal consent constraints, account eligibility |

## 2. Evidence & competitors

| Item | Finding | URL | Conf |
|---|---|---|---|
| PayPal auth-honor | 29-day auth, 3-day honor, reauth gives a new ID and restarts honor; up to 115%/+$75; partial captures; must enable partial capture for PayPal auths | [auth-honor.md](https://developer.paypal.com/payment-methods/auth-honor.md) | ✅ |
| Auth-capture guide (platforms) | Same 115%/$75; "multiple re-authorizations"; nothing on eligibility | [auth-capture.md](https://developer.paypal.com/platforms/checkout/standard/customize/auth-capture.md) | ✅ |
| Limited-release commerce platform v3 | Same limit, "whichever is less"; no eligibility | [authorize-capture.md](https://developer.paypal.com/limited-release/commerce-platform/v3/payment/authorize-capture.md) | ✅ |
| Payments v2 errors | MAX_CAPTURE_AMOUNT_EXCEEDED (defaults to 115%), MAX_CAPTURE_COUNT_EXCEEDED, AUTHORIZATION_ALREADY_CAPTURED (after final_capture), REAUTHORIZATION_TOO_SOON ("only once, day 4–29") | [payments v2](https://developer.paypal.com/docs/api/payments/v2/) | ✅ |
| FL §559.905 | Disclosure: shop "may not exceed this amount without my written or oral approval" | [flsenate.gov](https://flsenate.gov/Laws/Statutes/2015/0559.905) | ✅ |
| FL §559.909 | Overrun limits (not read) | [flsenate.gov](https://flsenate.gov/Laws/Statutes/2015/559.909) | ❌ |
| CA B&P §9884.9 | Consent required to exceed the estimate | [terms.law](https://terms.law/Demand-Letters/Automotive/california-auto-repair-overcharge-demand.html) | ⚠️ |
| Tekmetric | Digital signature authorization of estimates and additional work | [support.tekmetric.com](https://support.tekmetric.com/hc/en-us/articles/4421125978391-Digital-Signature-Authorization-Process) | ⚠️ |
| Shopmonkey | "Request Customer Authorization" for services | [support.shopmonkey.io](https://support.shopmonkey.io/hc/en-us/articles/38743372579988-Request-Customer-Authorization) | ⚠️ |
| Housecall Pro | Card on file, auto-charge on invoice | [help.housecallpro.com](https://help.housecallpro.com/en/articles/9944421-auto-charge-card-on-file-feature) | ⚠️ |
| Pepper | "Pre-authorized payments" | [help.usepepper.com](https://help.usepepper.com/en/articles/14501631-pre-authorized-payments) | ⚠️ title only |
| ServiceTitan | Financing; card-on-file features | [help.servicetitan.com](https://help.servicetitan.com/residential-s-r/docs/offer-financing-to-close-bigger-jobs-1) | ⚠️ |
| Jobber, Toast tip-adjust, Square tip-adjust | Deposits / tip adjustment on card auths | not verified this run | ❌ |

Queries run: "PayPal capture more than authorized 115% $75 eligibility"; "auto repair estimate exceed 10 percent consent Florida 559.905 California 9884.9"; "Housecall Pro OR Jobber OR ServiceTitan card on file authorization hold"; "Tekmetric OR Shopmonkey digital estimate approval". Square/Toast/Jobber were not searched separately because of the budget.

## 3. Novelty verdict

The new part is narrow: an AI that turns job notes and photos into an itemised final bill, checks it against a *customer-pre-consented ceiling*, and captures within PayPal's overage limit. Anything over the ceiling goes to an invoice. The "consented ceiling" maps neatly onto Florida-style tolerance rules, which is the one interesting angle. Everything else is incumbent workflow.

## 4. Feasibility & day-1 tests

Sequence:

1. `POST /v2/checkout/orders` with `intent:AUTHORIZE` for the estimate.
2. `/authorize`.
3. On job completion: `POST /v2/payments/authorizations/{id}/capture {amount: final, final_capture:true}` where final ≤ min(1.15×, +$75).
4. If over: capture 100%, then `POST /v2/invoicing/invoices` + `/send` for the remainder.

Day-1 tests:

- T1: capture 110% of a $100 sandbox auth.
- T2: capture 120% (expect MAX_CAPTURE_AMOUNT_EXCEEDED).
- T3: capture $1,080 on a $1,000 auth (tests whether the $75 cap is enforced).
- T4: is partial or over-capture refused with a permission error on a default sandbox business account?

If T1 fails, the idea is dead.

## 5. Recommendation

Don't build standalone. If #9 or a "programmable holds" idea is built, include overcapture as one branch: an estimate with a consented +15% buffer. Its unhappy path (over the ceiling → invoice) is a good "test the unhappy paths" moment.
