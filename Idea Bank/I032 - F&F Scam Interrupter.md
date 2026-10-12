---
title: "#32 F&F Scam Interrupter"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, survivor, deep-dived]
up: "[[Idea Index]]"
id: 32
theme: E5
group: "Moment-of-send scams"
desk_score: 89
final_score: 71
status: SURVIVOR
verdict: demote
kills: []
---
# #32 F&F Scam Interrupter

> Before you send money to a stranger, paste the listing or chat; AI spots purchase-scam patterns and converts the payment into a protected Goods & Services request.

**Theme:** E5 Moment-of-send scams · **Group:** Moment-of-send scams · **Crowding on Devpost:** High: PayPal native F&F AI alerts; Starling/Lloyds listing-screenshot checks; Devpost scam checkers

## Problem statement
US consumers lost $15.9B to fraud in 2025; UK purchase scams hit 175,809 cases, 66% of APP fraud starts online. Friends & Family payments for goods carry no purchase protection and are the scammer's favourite request.

## Proposed solution
A share-sheet / web tool: the buyer pastes the listing, seller handle and chat; AI scores scam signals (price anomaly, urgency, F&F request, reused images, off-platform push) and generates a G&S payment request/invoice from the seller with protections explained, or advises walking away.

## Target users
Marketplace buyers (Facebook Marketplace, forums, social commerce).

## AI contribution
Multimodal scam-pattern detection (text + images), price plausibility, plain-language warnings.

## PayPal integration
Invoicing / Payment Links for G&S requests; Orders; buyer protection framing; Disputes as fallback.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P08` Invoicing v2 (create, send, partial payment)
- `P22` Payment Links
- `P01` Orders v2 (create / capture / get)
- `P32` Seller Protection policy rules
- `A05` Structured decision / classification (most common)
- `A02` Classification with explanation / vision estimation
- `A11` Translation / tone

## Competitors and prior art
Bitdefender Scamio, Norton Genie, F-Secure Scam Protection

Consumer scam checkers analyse messages/links generically; none convert the transaction into a protected PayPal payment.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D032 - F&F Scam Interrupter (Deep Dive)]].

## Differentiation
Detection plus a protected-payment path, at the exact moment of send.

## Feasibility
Medium; PayPal has no public P2P-send API, so the intervention is a pre-send tool rather than an in-app interceptor.

## MVP scope
Paste a scam listing → high risk → protected invoice generated; paste a genuine one → low risk → G&S link.

## Risks
Stage-1 "meaningful PayPal" risk if the PayPal step feels thin; real-world reach depends on PayPal embedding it.

## Credible references
- [FTC — $15.9B reported fraud losses 2025](https://www.ftc.gov/news-events/news/press-releases/2026/03/ftc-testifies-joint-economic-committee-agencys-efforts-combat-fraud) ✅
- [UK Finance Annual Fraud Report 2026 — APP £576.4M; 175,809 purchase scams](https://www.ukfinance.org.uk/system/files/2026-06/UK%20Finance%20Fraud%20Report%202026.pdf) ✅
- [FTC Consumer Sentinel Data Book 2024](https://www.ftc.gov/system/files/ftc_gov/pdf/csn-annual-data-book-2024.pdf) ✅
- [CFPB complaint DB — PayPal 2025: 7,464; #1 'trouble accessing funds' 1,276](https://www.consumerfinance.gov/data-research/consumer-complaints/) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 7 | 5 |
| Design | ×2 | 8 | 7 |
| Impact | ×2 | 9 | 8 |
| Innovation | ×2 | 6 | 3 |
| Demo | ×2 | 8 | 7 |
| Feasibility | ×1 | 7 | 6 |
| Risk⁻¹ | ×1 | 6 | 5 |
| **Total /120** | | **89** | **71** |

_Why (desk):_ Excellent evidence and social impact; PayPal integration depth limited by API surface.

**Kill criteria:** none triggered.

## Deep-dive verdict: demote
Real problem, but PayPal, Starling and Lloyds already ship AI scam checks at the moment of send. Only the 'seller protection handshake' (payee-routed authorize/capture, refusal = verdict) survives; salvage it as a module, not a finalist.

_Score changes:_ Exact-mechanism incumbents found. PayPal's own AI scam alerts on F&F sends: live worldwide on PayPal and US-wide on Venmo since 2025-07-21, risk-scaled, high risk auto-declined. Starling Scam Intelligence (Oct 2025): upload listing/chat images, Gemini risk verdict. Lloyds Scam Check (Jun 2026): screenshots + AI at payment to a new payee. Also Marketplace scam-checker sites, a Chrome extension and Devpost entries (TrustGate, Red Flag). Innovation 6->3. PayPal has no P2P/Request Money API, and Invoicing/Payment Links can't be issued from the seller without partner permissions, so tech is Orders with payee.email_address plus Log in with PayPal (5). Third-party payee for non-partners is unverified; onboard-after-payment needs approved partner (feas 6, risk 5). Impact evidence stays top tier but reach is weaker (8).

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
