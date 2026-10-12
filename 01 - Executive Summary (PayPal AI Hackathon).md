---
title: "01 - Executive Summary (PayPal AI Hackathon)"
type: summary
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [summary]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Executive summary

**Goal.** Choose what to build for the PayPal AI Hackathon 2026 (Devpost, online, deadline Nov 12, 2026 12:00pm PT) by researching the event, the PayPal platform, the agentic-payments landscape and real problem evidence, then generating, scoring and stress-testing 100 ideas.

**Answer.**
1. **[[I023 - Seller Protection Preflight|#23 Seller Protection Preflight]]**: a pre-ship gate for PayPal sellers that enforces Seller Protection's own rules, releases holds through tracking and pre-builds the dispute evidence pack. 89/120.
2. **[[Wrong Box - Combined Concept|"Wrong Box"]]**: when an AI agent buys the wrong item, a photo decides who is at fault and PayPal fixes it by replacement offer or payout. 88/120.
3. **[[I055 - Payout Failure Triage|#55 Payout Failure Triage]]**: recoverable payouts with visible compliance refusals. 86/120.

The full Top 10 with tiers is in [[50 - Top 10 Overview]].

**How the answer was reached.** 100 ideas → 44 eliminated on kill criteria → 56 survivors scored on 7 axes → 14 adversarially deep-dived → 8 demoted or merged on evidence (#1 and #2 folded into Wrong Box) → a three-role council converged on the Top 3. See [[40 - Scoring Methodology]].

**What to know before trusting it.**
- Deep dives cut finalist scores by an average of 13.9 points. The other 86 ideas have not been through that, so their scores are likely inflated.
- The council is one model family. Confidence was 3/5 in each role.
- Everything ranks on sandbox behaviours not yet tested: [[63 - Day-1 Sandbox Test Plan]].
- The element-code legend and kill-criterion definitions were reconstructed from usage (⚠).

**Key research findings.**
- Judges score five equal criteria, may not run the code, and may use automated AI analysis of the repo ([[10 - Event, Rules & Judging Intelligence]]).
- PayPal's own agent toolkit has no authorize, vault, payouts, dispute-evidence, idempotency or spend-limit tools, and the hosted sandbox MCP has been broken since Oct 8 ([[11 - PayPal Platform & Sandbox Capabilities]], [[16 - Developer Pain, Gaps & Hidden Insights]]).
- Early Devpost entries cluster heavily in spend gates, AI escrow, shopping agents and "PayPilot" assistants ([[14 - Prior Winners & Duplicated Archetypes]]).
- No liability shift exists for "authorized but wrong" agent purchases ([[12 - Agentic Payments Landscape]]).
