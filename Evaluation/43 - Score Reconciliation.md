---
title: "43 - Score Reconciliation"
type: evaluation
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [evaluation, deep-dive]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Score reconciliation: desk vs deep-dive

The 14 ideas that received an adversarial deep dive, before and after. Axis order: Tech, Design, Impact, Innovation, Demo, Feasibility, Risk⁻¹.

| # | Idea | Desk axes | Desk | Deep axes | Final | Δ | Verdict |
|---|---|---|---|---|---|---|---|
| 23 | [[I023 - Seller Protection Preflight\|#23 Seller Protection Preflight]] | [8, 8, 8, 8, 8, 9, 8] | 97 | [8, 8, 6, 7, 8, 8, 7] | **89** | -8 | advance-with-changes |
| 3 | [[I003 - Mismatch-to-Replacement\|#3 Mismatch-to-Replacement]] | [7, 8, 7, 7, 9, 9, 8] | 93 | [7, 8, 6, 6, 9, 8, 7] | **87** | -6 | advance-with-changes |
| 55 | [[I055 - Payout Failure Triage\|#55 Payout Failure Triage]] | [9, 8, 7, 7, 8, 9, 8] | 95 | [8, 8, 6, 6, 7, 9, 7] | **86** | -9 | advance-with-changes |
| 28 | [[I028 - Early-Pay Discount Optimizer\|#28 Early-Pay Discount Optimizer]] | [8, 8, 8, 7, 7, 9, 8] | 93 | [7, 8, 7, 6, 7, 8, 7] | **85** | -8 | advance-with-changes |
| 9 | [[I009 - Rental Deposit Inspector\|#9 Rental Deposit Inspector]] | [8, 8, 6, 7, 9, 8, 8] | 92 | [8, 8, 6, 4, 8, 7, 6] | **81** | -11 | demote |
| 20 | [[I020 - Dispute-to-Listing Fixer\|#20 Dispute-to-Listing Fixer]] | [8, 8, 8, 8, 8, 9, 8] | 97 | [7, 7, 6, 6, 7, 7, 7] | **80** | -17 | demote |
| 56 | [[I056 - Integration Chaos Monkey\|#56 Integration Chaos Monkey]] | [8, 7, 6, 8, 8, 8, 8] | 90 | [8, 7, 5, 6, 7, 7, 7] | **80** | -10 | advance-with-changes |
| 8 | [[I008 - Final-Price Agent (Overcapture)\|#8 Final-Price Agent (Overcapture)]] | [8, 8, 6, 8, 8, 7, 7] | 90 | [7, 8, 5, 6, 7, 6, 6] | **78** | -12 | demote |
| 42 | [[I042 - Pre-Checkout Injection Firewall\|#42 Pre-Checkout Injection Firewall]] | [7, 7, 7, 8, 9, 8, 7] | 91 | [6, 7, 6, 5, 7, 8, 6] | **76** | -15 | advance-with-changes |
| 84 | [[I084 - Accessible Voice Checkout\|#84 Accessible Voice Checkout]] | [7, 9, 6, 7, 8, 7, 7] | 88 | [5, 8, 6, 5, 7, 7, 6] | **75** | -13 | demote |
| 47 | [[I047 - WebMCP Storefront Kit\|#47 WebMCP Storefront Kit]] | [8, 8, 7, 9, 9, 7, 6] | 95 | [6, 7, 6, 4, 7, 7, 5] | **72** | -23 | demote |
| 2 | [[I002 - Three-Party Agent Error Settlement\|#2 Three-Party Agent Error Settlement]] | [9, 7, 7, 9, 8, 8, 7] | 95 | [8, 6, 6, 3, 7, 7, 5] | **72** | -23 | demote |
| 1 | [[I001 - Intent Black Box\|#1 Intent Black Box]] | [9, 7, 7, 7, 8, 8, 8] | 92 | [8, 6, 6, 3, 6, 7, 6] | **71** | -21 | demote |
| 32 | [[I032 - F&F Scam Interrupter\|#32 F&F Scam Interrupter]] | [7, 8, 9, 6, 8, 7, 6] | 89 | [5, 7, 8, 3, 7, 6, 5] | **71** | -18 | demote |

## Reasons for the changes

### #23 Seller Protection Preflight → advance-with-changes
Primary-verified: US (Jan 2026) and UK (Jul 2026) terms require shipping to the Transaction Details address, void protection on redirect, recommend against buyer-arranged shipping, and exclude SNAD. There is NO signature/value threshold, so drop it. APIs are confirmed in OpenAPI: Orders v2 purchase_units[].shipping, capture seller_protection.status + dispute_categories, Transaction Search shipping_info, protection_eligibility, address_status and transaction_note, plus Orders track. Impact is lowered: no quantified scam frequency and no verified user voices. Innovation is lowered slightly because the competitor hunt was incomplete (search budget exhausted) and label-from-order printing already enforces the address implicitly. No Devpost overlap in ~144 entries.

_One line:_ A before-shipping PayPal Seller Protection gate: real API signals plus AI that reads 'ship to my cousin' messages and OCRs labels. Advance, paired with tracking-upload hold release; drop the signature claim and fill in scam evidence.

Full report: [[D023 - Seller Protection Preflight (Deep Dive)]]

### #3 Mismatch-to-Replacement → advance-with-changes
Only cluster mechanism not found on Devpost: instruction x listing x delivered-photo comparison feeding PayPal make-offer (REPLACEMENT_WITHOUT_REFUND) before a claim, or a Payouts reimbursement when the agent erred. Innovation docked for Loop AI Image Recognition / PixelProof photo checks, XReceipt 'did the two match', Provenant fault split; impact docked (NMI vendor survey, no agent-dispute volume); feasibility docked for vision reliability and day-1 sandbox dispute-create test. Combined with #1 binding + #2 payout fork: [8,8,6,6,9,7,7].

_One line:_ Make this the spine: photo of what arrived vs what the human asked decides merchant-replacement (Disputes) vs agent-platform payout (Payouts), pre-chargeback.

Full report: [[D003 - Mismatch-to-Replacement (Deep Dive)]]

### #55 Payout Failure Triage → advance-with-changes
Sandbox failure branches are mostly canned mock responses; classification is a lookup table; no primary payout-failure-rate data; payouts used by >=10 Devpost entries and HoldWatch explains ONHOLD events. Survives as a real UNCLAIMED→contact→cancel→RETURNED→re-issue loop with visible compliance refusals.

_One line:_ Recoverable payout workflow with compliance guardrails; build the hero loop on real UNCLAIMED state, not mock codes.

Full report: [[D055 - Payout Failure Triage (Deep Dive)]]

### #28 Early-Pay Discount Optimizer → advance-with-changes
Conditional-rules endpoint verified in public Invoicing v2 docs and agent-toolkit v1.11 (EARLY_PAYMENT_DISCOUNT/AUTO_CANCEL, PERCENT/AMOUNT, expiry enums), but an 'invoicing/internal' scope is listed and payer-view/auto-apply behaviour is undocumented -> day-1 sandbox test. Chaser already applies per-debtor automatic discounts in its portal; Zoho/Upflow/C2FO/Taulia and AP-side AI discount agents exist -> innovation down. Core loop is Invoicing-only -> tech down. Discount-uptake evidence is vendor/snippet only.

_One line:_ Survives as an AI-priced, per-client early-pay discount (cost-of-waiting maths) written natively into PayPal invoice conditional rules; must pass day-1 payer-view test.

Full report: [[D028 - Early-Pay Discount Optimizer (Deep Dive)]]

### #9 Rental Deposit Inspector → demote
AI before/after rental damage detection is a crowded category (Texada, CloudRent, switchlabs Verify, Roboflow, Hertz/UVeye) and public repo RentProof (Claude + Render) does the AI half nearly identically; TWICE/Booqable/ChargeAutomation already do auth-hold deposits with partial capture. Payments v2 reference says reauth allowed only once (day 4-29), contradicting guide's 'multiple'; PayPal partial capture needs account enablement; Hertz AI-billing backlash raises framing risk.

_One line:_ PayPal mechanics work for short rentals, but novelty collapses: AI damage diffing + partial hold capture both exist; keep only as a component.

Full report: [[D009 - Rental Deposit Inspector (Deep Dive)]]

### #20 Dispute-to-Listing Fixer → demote
Dispute data is rich enough to cluster: GET dispute has reason, sub_reasons, buyer product_details.description, purchase_url, items[] and messages[]. But the PayPal 'fix' step is cosmetic: /v1/catalogs/products backs Subscriptions, not storefronts, so the real fix goes to Shopify/Woo. ReasonWhy (Shopify, Jun 2026) already ships the cluster -> page-fix -> before/after loop on returns, and Return Insights AI, Vortex IQ ASIN clusters and Amazon VoC are adjacent. No primary figure found for the SNAD share of disputes. Competitor search was cut short by the shared search budget.

_One line:_ The data is real but the PayPal-side fix is cosmetic and ReasonWhy already does the same loop on returns; better as a prevention tab inside a dispute or ship-safe product.

Full report: [[D020 - Dispute-to-Listing Fixer (Deep Dive)]]

### #56 Integration Chaos Monkey → advance-with-changes
PayPal's own AI-Toolkit /paypal:doctor already statically scans for the same failure taxonomy (INSTRUMENT_DECLINED, webhook verify/idempotency, PayPal-Request-Id, retries) and auto-applies fixes; payfuzz (webhook delivery fuzzing), MockGateway (PayPal mock outcomes), Autonoma (agentic checkout E2E), Stripe audit/fix skills and PayPal's announced Merchant AI Integration Agent crowd the space; pain evidence is anecdotal; mock responses don't change PayPal state; header injection into merchant SDK calls needs a proxy. Dynamic sandbox fault injection + signed webhook replay + re-run-gated PR survives as novel.

_One line:_ Position as the dynamic complement to /paypal:doctor: make PayPal actually fail at the running app (mock codes + real signed webhook replays), show the broken order, open a PR only when the re-run goes green.

Full report: [[D056 - Integration Chaos Monkey (Deep Dive)]]

### #8 Final-Price Agent (Overcapture) → demote
Overcapture limit documented (115%/+$75, 'defaults to 115%' in MAX_CAPTURE_AMOUNT_EXCEEDED) but no published eligibility and unknown sandbox enforcement. State auto-repair laws (FL 559.905 disclosure; CA 9884.9) require customer consent to exceed estimates, so AI-set final prices need a pre-consented ceiling - incumbents (Tekmetric/Shopmonkey digital authorization, Housecall Pro/Pepper card-on-file & pre-auth) already cover that workflow. Demo moment is a JSON number.

_One line:_ Keep as a branch inside a holds-based build (consented +15% buffer, over-ceiling -> invoice); not a standalone finalist.

Full report: [[D008 - Final-Price Agent (Overcapture) (Deep Dive)]]

### #42 Pre-Checkout Injection Firewall → advance-with-changes
Warden (Devpost, this hackathon, submitted ~Oct 11) already ships a PayPal MCP firewall with provenance taint, hidden-text quarantine, Gemini intent check, phone holds and AG Grid ledger (merchant-side; plans buyer-side next). AIP-Bench/PCAT (arXiv 2607.21824) is a commerce-specific defense; MELON/CaMeL cover counterfactual and taint mechanisms. Survivor: buyer-side counterfactual selection audit (Branded Whisper hijacks choice, not payee) + capture-time order re-verification, deterministic core with classifier advisory only. PayPal surface is Orders+v6+webhooks.

_One line:_ Pivot from generic injection firewall (taken by Warden) to 'selection integrity': block the PayPal order when the agent's product pick flips once untrusted text is masked.

Full report: [[D042 - Pre-Checkout Injection Firewall (Deep Dive)]]

### #84 Accessible Voice Checkout → demote
PayPal v6 approval popup/modal is cross-origin and PayPal-owned: a third-party layer cannot make the approval step accessible, only the handoff around it. Core loop is checkout+Orders (tech anchor ~5) unless Vault/Refunds added. Close competitors: PayU accessible checkout w/ voice navigation (Aug 2026), Be My Eyes x InnoSearch AI accessible shopping portal (May 2025), Kalon Devpost (2023), CHI'26 voice-CUA shopping study (payment excluded), agentic browsers as AT (arXiv 2606.24870). Evidence strong on prevalence (WebAIM 95.9%, EAA in force, FTC accessiBe $1M, ~70% of >5,000 2025 suits e-com [vendor]) but payment-specific harm data still missing. Expert a11y judges (Jo Franchetti; Sylwia Vargas only via AG Grid) raise the bar.

_One line:_ Real need, but the PayPal approval window is a hard boundary and accessible/AI shopping already exists; fold 'statement-form confirmation + announced PayPal handoff + vaulted voice reconfirm' into a shopping/agent finalist as its accessibility pillar.

Full report: [[D084 - Accessible Voice Checkout (Deep Dive)]]

### #47 WebMCP Storefront Kit → demote
Shopify turned on 10 WebMCP tools (incl. checkout) by default on all Liquid/Hydrogen stores (Aug 2026); Stripe ships WebMCP tools in its payment UIs; WebMCP Bridge WP plugin (600+ installs) already exposes Woo cart tools; PayPal announced the same concept (Store Sync-gated). Agent demand ~zero (no mainstream agent calls modelContext tools; Gemini in Chrome 'soon'). PayPal loop is checkout-centric. Only narrow survivor: open PayPal v6 WebMCP checkout tools for non-Store-Sync sites.

_One line:_ Merchant-side WebMCP is already shipped by Shopify, Stripe and WP plugins; only an ungated 'PayPal v6 checkout as WebMCP tools' sliver remains — demote, salvage as a component.

Full report: [[D047 - WebMCP Storefront Kit (Deep Dive)]]

### #2 Three-Party Agent Error Settlement → demote
'No product settles three-way' is false: Provenant (Devpost, same hackathon by sponsor tags) splits fault user/merchant/agent with Shapley values and pays the agent's share via Payouts from a liability pool plus dispute evidence; Amex Agent Purchase Protection (Apr 2026) covers buyers for AI-agent error. No network rule makes agent platforms liable, so demand for the Payouts leg is speculative. Matrix is a lookup table; three personas hurt design/demo.

_One line:_ Mechanism already on Devpost (Provenant); survive only as the agent-fault Payouts fork triggered by #3's delivery check.

Full report: [[D002 - Three-Party Agent Error Settlement (Deep Dive)]]

### #1 Intent Black Box → demote
Provenant (Devpost, same hackathon by ag-grid/render tags) already binds custom_id to a hash of the agent decision trace with replay and a dispute evidence pack; AgentProof builds PayPal provide-evidence for agent disputes; Amex ACE (Apr 2026) captures intent + cart context for disputes; Chargebacks911 UDMS records agent consent. Hash binding is invisible on video; sandbox dispute creation is absent from public OpenAPI (day-1 test).

_One line:_ Mechanism already shipped by Provenant/AgentProof; keep only the normalized-instruction record as the evidence spine for #3.

Full report: [[D001 - Intent Black Box (Deep Dive)]]

### #32 F&F Scam Interrupter → demote
Exact-mechanism incumbents found. PayPal's own AI scam alerts on F&F sends: live worldwide on PayPal and US-wide on Venmo since 2025-07-21, risk-scaled, high risk auto-declined. Starling Scam Intelligence (Oct 2025): upload listing/chat images, Gemini risk verdict. Lloyds Scam Check (Jun 2026): screenshots + AI at payment to a new payee. Also Marketplace scam-checker sites, a Chrome extension and Devpost entries (TrustGate, Red Flag). Innovation 6->3. PayPal has no P2P/Request Money API, and Invoicing/Payment Links can't be issued from the seller without partner permissions, so tech is Orders with payee.email_address plus Log in with PayPal (5). Third-party payee for non-partners is unverified; onboard-after-payment needs approved partner (feas 6, risk 5). Impact evidence stays top tier but reach is weaker (8).

_One line:_ Real problem, but PayPal, Starling and Lloyds already ship AI scam checks at the moment of send. Only the 'seller protection handshake' (payee-routed authorize/capture, refusal = verdict) survives; salvage it as a module, not a finalist.

Full report: [[D032 - F&F Scam Interrupter (Deep Dive)]]

## Combined concept
"Wrong Box" combines #3 (spine) with #1 (instruction binding) and #2 (agent-fault Payouts fork). Combined axes [8,8,6,6,9,7,7] = **88/120**. See [[Wrong Box - Combined Concept]].
