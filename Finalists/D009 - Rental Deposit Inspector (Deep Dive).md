---
title: "Deep dive: #9 Rental Deposit Inspector"
type: deep-dive
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [finalist, deep-dive, verdict/demote]
up: "[[50 - Top 10 Overview]]"
idea: "[[I009 - Rental Deposit Inspector]]"
verdict: demote
final_score: 81
---
> Idea note: [[I009 - Rental Deposit Inspector]] · Verdict: **demote** · Final score **81/120** (desk 92). Confidence tags: ✅ primary read directly · ⚠️ secondary / vendor / single source · ❌ unverified. `⚠ inference` marks judgment.

# #9 Rental Deposit Inspector — deep dive

Analyst run 2026-10-12. Shared budget with #28 and #8.

## 1. Verdict

**Demote (keep as a component, not a finalist).** The PayPal mechanics work for short rentals: authorize, partial capture, void ✅. The weak points are novelty and risk.

AI before/after damage detection for rental returns is now a crowded product category:

- Texada (equipment-rental software) ships "AI Damage Detection" in its mobile app.
- CloudRent markets AI damage detection.
- switchlabs "Verify" sells AI condition verification for equipment rental and car rental.
- Roboflow has a rental-equipment damage inspection template.
- Hertz/UVeye scanners produce damage bills automatically.
- **RentProof**, a public GitHub repo (fork of BorisKonov/rentproof), does almost exactly this card's AI half: six fixed-angle photos at check-out and return, a vision diff, and damage converted into invoice lines with photo proof, built on Claude and deployed on Render. Render is a hackathon sponsor, so this could be a competing hackathon entry. ⚠ inference
- Rental platforms already partially capture deposit holds manually: TWICE ("Charge part or all of an authorized hold") and Booqable (pre-auth holds).

The only unoccupied slice is "AI evidence → PayPal partial capture with a contest window", which is a thin delta.

Risk is also worse than scored:

- Hertz's AI scanners drew public backlash for auto-charging questionable damage. Judges will ask "isn't this the Hertz problem?"
- Holds are only reliable for 3 days (the honor period).
- The Payments v2 reference says reauthorization is allowed "only once, from day 4 to day 29", which contradicts the guide's "multiple re-authorizations".
- Partial capture of PayPal-wallet authorizations must be enabled on the merchant account.

**Adjusted scores** [tech, design, impact, innovation, demo, feasibility, risk] = **[8, 8, 6, 4, 8, 7, 6]** (was [8,8,6,7,9,8,8]).

| Axis | Change | Reason |
|---|---|---|
| Tech 8 | = | Authorize, partial capture with `final_capture`, void, reauthorize, disputes and webhooks make a real multi-API loop. None of it is in agent-toolkit (`create_order` hardcodes CAPTURE), so it needs raw REST. |
| Design 8 | = | Clear persona and start/end states. |
| Impact 6 | = | Pain is plausible, but there is no primary data on rental deposit disputes. Hertz shows the reverse harm (consumers over-charged by AI). |
| Innovation 7→4 | −3 | Texada, CloudRent, switchlabs, Roboflow, UVeye/Hertz, RentProof (near-identical), and TWICE/Booqable partial holds. |
| Demo 9→8 | −1 | Still visual, but a near-identical public demo exists (rentproof-three.vercel.app). |
| Feasibility 8→7 | −1 | Partial capture needs account enablement. Reauth limits are contradictory. Holds longer than 3 days are not guaranteed. |
| Risk 8→6 | −2 | Hertz backlash framing, possible crowding from a duplicate entry, and buyer disputes of damage captures. |

**If revived**, reframe as a *renter-side fairness* product: the renter gets the AI diff and a 48-hour contest window before any capture, with a mandatory human review for anything above $X. Or fold the hold mechanics into a broader "programmable holds" idea.

## 2. Problem validation

| Claim | Number | Source | Conf |
|---|---|---|---|
| Hertz AI scanners catch more damage and bill customers automatically; customer outrage | Reported 5× more damage caught | [The Autopian](https://www.theautopian.com/customers-outraged-with-hertz-ai-scanners-they-say-automatically-charge-for-questionable-damages/), [CO/AI](https://getcoai.com/news/hertzs-ai-scanners-catch-5x-more-car-damage-surprising-customers-with-bills/), [Fox 26](https://www.fox26houston.com/news/rental-cars-using-ai-damage-hertz-billing), [Forbes/Elliott](https://www.forbes.com/sites/christopherelliott/2025/11/01/ai-vs-the-iphone-the-battle-for-your-rental-car-damage-bill/) | ⚠️ (snippets; consistent across 4 outlets) |
| Rental SMBs want holds instead of charge-and-refund | qualitative | [HivePress community](https://community.hivepress.io/t/hold-security-deposits-instead-of-charging-refunding/2481), [Shopify community "authorization hold"](https://community.shopify.com/t/option-to-do-a-credit-card-authorization-hold/18703) | ⚠️ titles/snippets |
| Shopify rental merchants struggle to charge damage/late fees | qualitative | [Shopify community](https://community.shopify.com/t/charging-late-damage-non-returns-fee-for-rental-business/85197) | ⚠️ snippet |
| Stripe uncaptured holds last ~7 days, so rental tools auto-expire them | ~7 days | [TWICE docs](https://www.twicecommerce.com/docs/concepts/orders/deposits.md) | ✅ |

No regulator or network data quantifies deposit disputes for SMB equipment rental. Impact stays at 6.

## 3. Competitor & novelty research

Queries: "PayPal security deposit policy merchant authorization hold rental"; "Hertz UVeye AI damage scanner automatic charge"; "Booqable security deposit authorization hold Stripe partial capture"; "AI before after photo damage detection equipment rental return app deposit automatic deduction" (extended); "CloudRent AI damage detection rental deposit"; "devpost PayPal rental deposit damage AI authorization capture". Plus raw/B, where Bryntum suggests "equipment rental locked on payment".

| Name | Type | What it does | Overlap | URL | Conf |
|---|---|---|---|---|---|
| RentProof (maistor1, fork of BorisKonov) | OSS / likely hackathon project | Six-angle check-out/return photos, vision diff lists new damage, confirmed damage becomes invoice lines with photo proof. Next.js + Claude, Render/Vercel demo. No payment capture. | **High** | [github.com/maistor1/rentproof](https://github.com/maistor1/rentproof) | ✅ |
| Texada Service & Rental Mobile: AI Damage Detection | product | AI damage detection at check-in/out for equipment rental yards | High (AI half) | [help.texadasoftware.com](https://help.texadasoftware.com/en/knowledge/3276/service-rental-mobile-ai-damage-detection), [blog](https://texadasoftware.com/blog/ai-damage-detection/) | ⚠️ |
| CloudRent AI Damage Detection | product | AI damage detection for rental | High (AI half) | [cloudrent.me](https://www.cloudrent.me/ai-damage-detection/) | ⚠️ |
| switchlabs Verify | product | AI condition verification for equipment rental and car rental returns | High (AI half) | [verify.switchlabs.dev](https://verify.switchlabs.dev/use-cases/equipment-rental-condition) | ⚠️ |
| Roboflow rental damage inspection | platform template | CV model template for rental equipment damage | Med | [roboflow.com](https://roboflow.com/ai/rental-equipment-damage-inspection) | ⚠️ |
| Hertz × UVeye (also ProovStation, Ravin, Tchek, DeGould) | product | Drive-through AI scans that trigger damage bills | High (AI → charge) | see §2 | ⚠️ |
| Levy Electric fleets | product | Car-sharing condition reports and damage claims | Med | [levyelectric](https://fleets.levyelectric.com/help/car-sharing/damage-claims) | ⚠️ |
| TWICE | product | Card deposit as an auth hold. Partial charge with reason, release remainder. Stripe/Adyen only, **not PayPal**. Manual decision. | High (payment half) | [twicecommerce.com](https://www.twicecommerce.com/docs/concepts/orders/deposits.md) | ✅ |
| Booqable | product | Credit-card pre-authorization holds for rental deposits | High (payment half) | [booqable.com](https://booqable.com/blog/authorize-credit-card-holds/) | ⚠️ |
| ChargeAutomation | product | Security/damage deposit holds and capture for short-term rentals | Med-High | [help.chargeautomation.com](https://help.chargeautomation.com/en/articles/3443570-how-to-capture-security-damage-deposits) | ⚠️ |
| Rentle, Checkfront, Goodshuffle, Fat Llama | product | Rental booking with deposits / damage protection | Med | not individually verified | ❌ |
| Airbnb AirCover, Turo damage claims | platform feature | Photo-evidence damage claims inside the platform | Med | not fetched | ❌ |
| Bryntum sponsor idea "equipment rental locked on payment" | sponsor prompt | Rental scheduling with a payment lock | Med (crowding) | raw/B | ✅ |

**Does anyone tie AI damage assessment to a partial capture?** Hertz/UVeye effectively ties AI to a charge, though not to a pre-auth hold. Nobody I found ties it to a *PayPal* authorization partial capture. That is the only gap, and it is a narrow one.

## 4. Novelty verdict

- **Not new:** AI before/after diffing (at least 5 products plus RentProof), auth-hold deposits with partial capture (TWICE, Booqable, ChargeAutomation).
- **New:** joining the two on PayPal rails, plus a renter-facing contest window before capture.
- **Sharpest differentiator (weak):** "The AI drafts the deduction; the renter sees the evidence and can contest before PayPal captures a cent."

## 5. Technical feasibility in PayPal sandbox

**Verified mechanics**

- 29-day authorization period with a 3-day honor period ✅ ([auth-honor](https://developer.paypal.com/payment-methods/auth-honor.md)).
- "Each reauthorization generates a new authorization ID and restarts the honor period" ✅.
- "Partial captures are supported during a single authorization period." "For PayPal payment authorizations, you must enable partial capture on your PayPal account." ✅
- Capture body: `amount`, `final_capture` (default false: "Indicates whether you can make additional captures"), `invoice_id`, `note_to_payer`, `soft_descriptor` ✅ ([Payments v2 ref](https://developer.paypal.com/docs/api/payments/v2/)).
- Void: `POST /v2/payments/authorizations/{id}/void`, no body ✅. `CANNOT_BE_VOIDED`: a reauthorization can't be voided; void the parent instead ✅.

**Contradiction (flag):** the guide says "multiple re-authorizations" within 29 days, but the API error `REAUTHORIZATION_TOO_SOON` says "Reauthorization is allowed only once, from day 4 to day 29", and `REAUTHORIZATION_NOT_SUPPORTED` says you can't reauthorize a reauthorization ✅ (both from docs). **Assume one reauth.** That caps a reliable hold at about day 4 + 3 days of honor, with a 29-day hard limit.

**Buyer view:** the PayPal help article (Pay in 4 context) says an authorization "will show as a pending authorization within your PayPal Account Activity and also at your financial institution" ✅ ([help465](https://www.paypal.com/us/cshelp/article/help465)). For standard wallet auths this is ⚠ inference; verify in the sandbox buyer account.

**PayPal policy on security deposits:** I found no explicit PayPal policy. The User Agreement's holds/reserves sections cover seller-side holds, not merchant deposits ❌. Day-1: check the AUP. Also note that a captured damage charge can be disputed by the buyer, and Seller Protection covers unauthorized/INR claims, not "I didn't damage it".

**API sequence**

1. `POST /v2/checkout/orders` with `intent:AUTHORIZE`.
2. Buyer approves.
3. `POST /v2/checkout/orders/{id}/authorize` returns the `authorization_id`.
4. On return: AI diff, then a renter contest window.
5. Then one of:
   - (a) clean: `POST /v2/payments/authorizations/{id}/void`
   - (b) damage: `POST …/capture {amount: X, final_capture: true, note_to_payer, invoice_id}`
   - (c) rental >3 days: `POST …/reauthorize` on day 4+
6. Webhooks: `PAYMENT.AUTHORIZATION.VOIDED`, `PAYMENT.CAPTURE.COMPLETED`.

**Day-1 tests**

- T1: does partial capture work on a fresh sandbox business account, or does it return a permission error until enabled?
- T2: reauthorize on day 0 (expect REAUTHORIZATION_TOO_SOON). Sandbox may not let you time-travel, so a long-rental demo is narrated only.
- T3: a second reauth (expect REAUTHORIZATION_NOT_SUPPORTED).
- T4: capture with `final_capture:true`, then void the remainder (expect AUTHORIZATION_ALREADY_CAPTURED or an implicit release).
- T5: buyer sandbox activity shows "pending"?

## 6. AI contribution

A vision model compares paired photos and outputs `[{region, damage_type, severity, new_vs_preexisting, confidence, bbox}]`. A price table maps these to costs (deterministic). The LLM writes an evidence page. Guardrails: confidence threshold, human approval, and a cap of capture ≤ authorized amount (no overcapture for damage).

## 7. MVP (if revived)

Two scripted rentals (clean → void; scratched lens → partial capture), a renter contest page, and an evidence PDF linked in `note_to_payer`. Weeks 1–4 as in the original card.

## 8. Demo storyboard (if revived)

- 0:00–0:20 Hertz headline: "AI damage bills are making renters furious."
- 0:20–1:00 Check-out photos, then a $300 PayPal hold appears.
- 1:00–1:40 Return. The AI diff highlights a lens scratch. The renter sees the evidence and accepts.
- 1:40–2:10 **Wow moment:** the PayPal sandbox shows a $300 auth, $85 captured, the remainder released.
- 2:10–2:40 Clean return, then void.
- 2:40–3:00 Close.

## 9. Risks & mitigations

| Risk | Mitigation |
|---|---|
| Hertz-style backlash framing | Renter-first contest window, human approval |
| Duplicate (RentProof, Bryntum prompt) | Differentiate on payment + fairness, or demote |
| Holds expire for multi-day rentals | One reauth only; restrict to rentals under ~7 days; otherwise use a vaulted payment method |
| Partial capture not enabled | Day-1 T1 |

## 10. Sources

Linked inline. Primary: PayPal auth-honor, auth-capture guide, Payments v2 reference, help465, TWICE docs, RentProof GitHub page ✅. Others ⚠️.
