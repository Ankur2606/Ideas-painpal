---
title: "40 - Scoring Methodology"
type: method
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [evaluation, scoring]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Scoring methodology

## Why this scale
The old vault used a 7-hour-build frame. This event is online, ~4.5 weeks, and judged on **five equally weighted Devpost criteria** (Technological Implementation, Design, Potential Impact, Innovation/Idea, Presentation), with Technological Implementation as the first tie-break. The 7-axis score keeps those five at double weight and adds feasibility and risk as single-weight guards.

| Axis | Weight | Maps to Devpost criterion |
|---|---|---|
| Tech | ×2 | Technological Implementation |
| Design | ×2 | Design (complete product experience) |
| Impact | ×2 | Potential Impact |
| Innovation | ×2 | Innovation / Idea |
| Demo | ×2 | Presentation (≤3-min video) |
| Feasibility | ×1 | not a criterion, but decides whether the others are real |
| Risk⁻¹ | ×1 | 10 = no gating, legal or dependency risk |

Max = 120. Each axis is 1 to 10.

## Anchors
- **Tech 10:** ≥4 non-checkout PayPal capabilities in the core loop plus AI making consequential, structured decisions. 5 = checkout + one API with AI writing text. 2 = PayPal peripheral.
- **Design 10:** coherent end-to-end experience with a clear persona and a start and end state demonstrable in sandbox.
- **Impact 10:** top-tier primary evidence (regulator, network, independent) of a severe problem for a named audience. 5 = plausible, vendor-only data. 2 = no data.
- **Innovation 10:** no product, OSS project, paper prototype or visible Devpost entry does this mechanism. Subtract for each close competitor found.
- **Demo 10:** one unmistakable visual moment showing a PayPal sandbox state change, legible in 3 minutes.
- **Feasibility 10:** all required APIs verified in sandbox, buildable by 1 to 3 people in 4 weeks.

## Two scoring passes
1. **Desk score (all 100 ideas).** Scored from the four research reports. Competitor and novelty claims are from landscape scans, not per-idea hunts.
2. **Post-deep-dive score (14 ideas).** An adversarial analyst tried to prove each idea was *not* novel, *not* feasible or *not* valuable, with ≥6 differently phrased searches. Scores were revised with reasons. See [[43 - Score Reconciliation]].

⚠️ **Important bias to know about:** desk scores for deep-dived ideas dropped by an average of 13.9 points, almost entirely on Innovation. The 86 non-deep-dived ideas have not had that treatment, so their desk scores are *probably inflated by a similar margin*. Compare them to each other, not to the deep-dived finalists.

## Control group
Ideas #97 to #100 are deliberately obvious (NL assistant, shopping agent, receipt splitter, budget chatbot). They scored 50 to 60, well below the field, which is a sanity check on the scale.

## Ranking rule for the Top 10
Rank by **deep-dive verdict first** (advance / advance-with-changes before demote), then by final score. See [[50 - Top 10 Overview]].

## Kill criteria
See [[41 - Brutal Elimination]].
