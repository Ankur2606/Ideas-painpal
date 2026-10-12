---
title: "Council report: judge"
type: council
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [council, judge]
up: "[[62 - Council Reports]]"
---
# Council member: JUDGE (PayPal Developer Advocate on the panel)

**My lens.** I score the five Devpost criteria literally and give each equal weight: Tech, Design, Impact, Innovation, Presentation. Feasibility and risk only count when they would show up in the video or the repo. I've watched hundreds of 3-minute videos, and I reward four things:
- **Problem-first framing.** The first 20 seconds name a person and a loss, not a PayPal product.
- **PayPal used beyond checkout.**
- **Unhappy paths shown on screen.**
- **A real OSS repo.** I want a README that an AI-driven code scan can parse, plus tests.

I'm also tired of what this pile will be full of: agent spend gates (~13), AI escrow (~11), shopping agents (~10) and "PayPilot" chat assistants (~8).

Scores below are my judge view on the five criteria (1–10 each, /50). They are not the 120-point research score.

## 1. Ranking of all 10

| # | Idea | Tech | Design | Impact | Innov. | Present. | /50 | One line |
|---|---|---|---|---|---|---|---|---|
| 1 | **23 Seller Protection Preflight** (+ tracking hold-release + dispute evidence pack) | 8 | 8 | 7 | 8 | 8 | **39** | Problem-first, PayPal-native (it enforces PayPal's own policy text), and nobody in ~144 Devpost entries is near it. It reads as "this team understands how PayPal sellers actually lose money". |
| 2 | **3 Mismatch-to-Replacement as spine ("Wrong Box", with #1 binding + #2 payout fork)** | 8 | 8 | 5 | 6 | 9 | **36** | Best video moment in the set: one photo, two payers, two PayPal APIs. But it lands in the most crowded judging pile (agent liability: Provenant, AgentProof, XReceipt), and the impact is forward-looking. |
| 3 | **55 Payout Failure Triage** | 8 | 8 | 6 | 6 | 7 | **35** | It literally answers "test the unhappy paths", and the compliance refusal is a great judge moment. Every judge has paid hackathon winners, so the persona works. Payouts are crowded, and the failure branches are mostly mocks. |
| 4 | 56 Integration Chaos Monkey | 8 | 6 | 4 | 6 | 7 | 31 | DevRel judges will love it personally. But Impact is "developers, anecdotally", and every PayPal judge knows `/paypal:doctor` and the announced Merchant AI Integration Agent. |
| 5 | 28 Early-Pay Discount Optimizer | 6 | 7 | 6 | 5 | 6 | 30 | Single API family. It looks like invoice entry #5. The wow moment is a percentage on an invoice, and there is gating risk on the payer view. |
| 6 | 42 Selection-Integrity firewall | 6 | 7 | 5 | 5 | 7 | 30 | The counterfactual flip is clever, but Warden is already in this hackathon and I'll have seen "hidden-injection-blocked". The PayPal surface is checkout plus Orders. |
| 7 | 20 Dispute-to-Listing Fixer | 6 | 7 | 5 | 5 | 6 | 29 | The PayPal "fix" is a catalog object no shopper sees, which is exactly the "PayPal bolted on" smell. ReasonWhy already does the loop on returns. |
| 8 | 9 Rental Deposit Inspector | 7 | 8 | 5 | 3 | 7 | 30* | A near-identical public repo exists (RentProof, Claude + Render), and the Hertz AI-billing backlash invites a hostile question. High duplicate risk in the same judge queue. |
| 9 | 84 Accessible Voice Checkout | 4 | 8 | 6 | 5 | 6 | 29 | It can't touch the PayPal approval window, so the tech is checkout plus one API. Jo will spot any a11y defect. Better as a pillar inside another build. |
| 10 | 8 Final-Price Overcapture | 6 | 6 | 4 | 5 | 4 | 25 | The hero moment is "$1,075 captured" as a JSON number. Consent laws undercut the AI-sets-the-price premise. |

(*#9 sits below #20 and #42 despite a similar raw sum. A likely duplicate submission in the same queue is a tie-breaker I would actually apply.)

## 2. Top 3

### #1: Seller Protection Preflight (spine #23, plus tracking hold-release and a pre-built dispute evidence pack)

**Why it wins against ~550–1,100 entries**
- **Scarcity.** It's the only finalist with zero visible Devpost overlap and outside every crowded cluster. In a judging queue, being the only one of its kind is worth a lot.
- **Problem-first by construction.** The hook is a verbatim PayPal policy clause, "you must ship the item to the shipping address on the Transaction Details page… redirected… not eligible", plus a seller who lost $480.
- **Real user voices exist.** Recurring eBay community threads include "Buyer asking to ship to different address", "Zero feedback new buyer paid, asked to ship to different address" and "Scammed out of $400". These are ⚠️ search-result titles only, still to be read and quoted properly (see sources).
- **Deep PayPal usage beyond checkout, aligned with PayPal's own interest.** Orders GET (shipping, `seller_protection`), Transaction Search (`protection_eligibility`, `address_status`, `transaction_note`), Tracking, Disputes webhooks plus evidence. Fewer protection-void losses is a story PayPal people want told.
- **Unhappy paths are the product.** It covers the cousin address, the buyer-arranged courier, pickup or digital goods (NOT_ELIGIBLE), a label OCR mismatch, and a region not supported.

**Prize targets**
- **Grand** (it's balanced across all five criteria).
- **Fallback HM: Most Impactful or Best Use of PayPal + AI.**
- **Sponsor: AG Grid** for the order queue with protection status. APIMatic is the alternative if the server SDK is used.

**Single biggest risk.** The AI looks decorative: "a rules engine with a paste box". If the video doesn't show the model doing things rules can't, Tech and Innovation drop to 6. Those things are multilingual intent with a quoted span, fuzzy address equivalence (forwarder or reshipper detection), and label OCR against the PayPal address. The secondary risk is that buyer messages live off-PayPal, so be upfront about the paste or forward inbox.

**Decisive day-1 test.** Capture a sandbox order with a shipping address, then run `GET /v2/checkout/orders/{id}`.
- Is `purchase_units[].payments.captures[].seller_protection` present?
- Can any input make it not ELIGIBLE? Try `shipping_preference: NO_SHIPPING`, a pickup `shipping.type`, or guest card.
- Then `POST /v2/checkout/orders/{id}/track` and confirm the tracker shows in the sandbox UI.

If `seller_protection` is constant, the eligibility verdict must come from a policy rules table, and the video should say so honestly.

### #2: "Wrong Box" (spine #3 Mismatch-to-Replacement; modules: #1 instruction binding, #2 agent-fault Payouts fork)

**Why it wins**
- **The most legible 3 minutes in the set.** The split screen reads "asked navy/M · listed navy/M · got royal/L". The PayPal dispute then flips to RESOLVED through REPLACEMENT_WITHOUT_REFUND. A second photo produces a Payout instead, and the balance rises in-frame.
- **Five non-checkout capabilities** with a consequential, structured AI decision: the fault class.
- **It wins on presentation even if innovation is docked**, and that is a full fifth of the score.

**Prize targets**
- **HM Best Use of Agentic Commerce** is primary.
- **Best Demo Delivery** is next.
- **Grand** is possible.
- **Sponsor: AG Grid** (keep the grid visually distinct from Provenant's) or Channel3 for the canonical listing.

**Single biggest risk.** Provenant is in the same hackathon and probably the same judge queue. It already does custom_id trace hashing, a fault split, payout of the agent's share and an evidence pack. If the video says "liability" before it shows the photo, I mark it derivative. A second risk: the agent platform as payer is invented, and both consoles belong to the team. Say so.

**Decisive day-1 test.**
1. Run `POST /v1/customer/disputes` (buyer `PayPal-Auth-Assertion`) against an Orders v2 capture.
2. Confirm `allowed_response_options.make_offer` contains `REPLACEMENT_WITHOUT_REFUND`.
3. Confirm `accept-offer` resolves the case.

If API creation fails, drive everything after a UI-created dispute. If the replacement offer is unavailable, the hero moment collapses to a refund, and #2 drops below #55.

### #3: Payout Failure Triage (#55)

**Why it wins**
- It is the purest "unhappy path" entry. The loop is UNCLAIMED → AI contacts the recipient → corrected handle → cancel → RETURNED → re-issue → SUCCESS.
- The guardrail is the beat I'd remember: the agent refuses to reroute around RISK_DECLINE or REGULATORY_BLOCKED. Remediation plus refusal is distinct from HoldWatch, which only explains holds.
- The hackathon/bounty-organiser persona is one every judge on this panel has lived.

**Prize targets**
- **HM Best Use of PayPal + AI** or Most Impactful (creators and gig workers).
- **Sponsor: AG Grid**, with a live cell-flash ledger grouped by failure class. AG Grid is a better fit than Bryntum.

**Single biggest risk.** The demo is mostly simulated JSON. Test values are magic strings, so if the real UNCLAIMED loop doesn't exist in sandbox, I see a lookup table with chat on top: Tech 6 and Innovation 5. Payouts are also used by 10+ entries already.

**Decisive day-1 test.**
1. Send a `POST /v1/payments/payouts` to a non-sandbox email.
2. Confirm the item goes `UNCLAIMED`, with `RECEIVER_UNREGISTERED` on `GET /v1/payments/payouts-item/{id}`, and that the `PAYMENT.PAYOUTS-ITEM.UNCLAIMED` webhook fires.
3. Confirm `POST …/payouts-item/{id}/cancel` returns RETURNED.

If any step fails, demote this idea below #56.

### Judge-side advice for whichever wins
- Open with a person and a loss, not "we built an AI agent with PayPal".
- End with a 10-second unhappy-path montage.
- The README needs a "PayPal APIs used" section with endpoint names, a "Unhappy paths handled" table and runnable tests. The automated AI scan will read these first.
- Show live sandbox state changes or webhook toasts, never a mock.
- Max one Grand/HM plus one sponsor prize, so pick the sponsor tool that does real work in the UI.

## 3. The idea everyone else will overrate: #28 Early-Pay Discount Optimizer (85/120, 4th)

The 120-point table gives it Design 8 and Impact 7. A judge sees something else:
- Another invoicing assistant (~4 already on Devpost, one literally named "Chaser").
- The core loop is one PayPal API family.
- The "AI" is a formula, honestly deterministic, which is correct engineering but not memorable.
- The best visual moment depends on an undocumented payer-view behaviour behind an `invoicing/internal` scope.

The per-client pricing maths is a good idea for a product and a mediocre one for a 3-minute video. Runner-up for overrating: **#56 Chaos Monkey**. It echoes the judges' own kickoff quotes, so it feels tailored. But Impact is a full fifth of the score, and "developers, anecdotally" scores 4. PayPal judges also know `/paypal:doctor` exists.

## 4. Confidence: **3 / 5**

The #1 vs #2 order depends on one thing: whether judges weight scarcity (#23) above presentation ceiling (#3). Both depend on day-1 sandbox results. #23's novelty hunt was cut short by the search budget, so a late-surfacing eBay or Chrome-extension competitor would drop it to #2.

## Sources (new this pass; everything else is from the deep-dive files)
- eBay community: "Buyer asking to ship to different address": https://community.ebay.com/t5/Selling/Help-Buyer-asking-to-ship-to-different-address/m-p/27772008/highlight/true ⚠️ (title only)
- eBay community: "Zero feedback new buyer paid, asked to ship to different address": https://community.ebay.com/t5/Shipping/Zero-feedback-new-buyer-paid-asked-to-ship-to-different-address/m-p/30476177/highlight/true ⚠️ (title only)
- eBay community: "Scammed out of $400": https://community.ebay.com/t5/Selling/Scammed-out-of-400-thanks-to-eBay/m-p/27830012/highlight/true ⚠️ (title only)
- eBay community: "Buyer wants to change name and shipping address after purchase": https://community.ebay.com/t5/Selling/Buyer-wants-to-change-name-and-shipping-address-after-purchase/m-p/31298622/highlight/true ⚠️ (title only)
- Multichannel Merchant: "5 PayPal Chargeback Scams": https://multichannelmerchant.com/blog/5-paypal-chargeback-scams-prevent ⚠️ (title only)
- Search for a Devpost "agent wrong item photo PayPal replacement" competitor: no Devpost hit (3 searches used out of 5)
