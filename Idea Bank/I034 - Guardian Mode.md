---
title: "#34 Guardian Mode"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E5, survivor]
up: "[[Idea Index]]"
id: 34
theme: E5
group: "Moment-of-send scams"
desk_score: 78
final_score: 78
status: SURVIVOR
verdict: desk-only
kills: []
---
# #34 Guardian Mode

> Consent-based co-pilot for older adults: cooling-off for first-time high-value payees and a trusted contact who sees anomalies, not everything.

**Theme:** E5 Moment-of-send scams · **Group:** Moment-of-send scams · **Crowding on Devpost:** none

## Problem statement
Older adults reported $2.4B in fraud losses in 2024 (FTC; up to $81.5B adjusted for under-reporting); losses over $100K rose 351% since 2020.

## Proposed solution
Payments run through an app-level wallet (vaulted PayPal) with AI anomaly scoring; new payee + large amount + unusual pattern triggers delay and trusted-contact approval.

## Target users
Older adults and family caregivers.

## AI contribution
Anomaly detection, scam-script detection in pasted messages, explanation.

## PayPal integration
Vault (payer-not-present payments via app), Orders, Log in with PayPal.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P06` Vault v3 (saved payment tokens, payer-not-present charges)
- `P01` Orders v2 (create / capture / get)
- `P25` Log in with PayPal
- `A15` Anomaly detection
- `A05` Structured decision / classification (most common)

## Competitors and prior art
EverSafe, Carefull, True Link

Bank-feed monitoring services exist for older adults.

**Verification status:** ⚠️ desk research only. The competitor names above come from the landscape and Devpost scans, not from a per-idea novelty hunt. Treat "no competitor found" as unproven.

## Differentiation
PayPal-wallet-native, consent-scoped.

## Feasibility
Medium; PayPal doesn't expose consumer P2P activity to third parties, so the app must be the payment path.

## MVP scope
Senior's app sends payments; scam pattern triggers hold and caregiver approval.

## Risks
Adoption requires routing payments through the app; competitors established.

## Credible references
- [FTC Protecting Older Consumers 2024–2025 — $2.4B reported; $10.1–81.5B adjusted](https://www.ftc.gov/system/files/ftc_gov/pdf/P144400-OlderAdultsReportDec2025.pdf) ✅
- [FinCEN elder financial exploitation analysis](https://www.fincen.gov/news/news-releases/fincen-issues-analysis-elder-financial-exploitation) ✅

## Scoring
| Axis | Weight | Desk score | 
|---|---|---|
| Tech | ×2 | 6 | 
| Design | ×2 | 7 | 
| Impact | ×2 | 8 | 
| Innovation | ×2 | 5 | 
| Demo | ×2 | 7 | 
| Feasibility | ×1 | 6 | 
| Risk⁻¹ | ×1 | 6 | 
| **Total /120** | | **78** | 

_Why (desk):_ Strong evidence, constrained integration.

**Kill criteria:** none triggered.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
