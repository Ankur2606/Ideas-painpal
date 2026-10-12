---
title: "_Method & Assumptions"
type: meta
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [meta, method]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Method and assumptions

## Pipeline
1. Inspected the existing `Agentic-Payments-Hackathon` vault for structure, frontmatter and methodology (read-only).
2. Four parallel research reports: PayPal platform and sandbox; event, sponsors and judges; agentic-payments landscape; problem evidence (~29k words, in `Research/`).
3. 100 ideas written to one schema (problem, solution, users, AI, PayPal, competitors, differentiation, feasibility, MVP, risks, references).
4. Kill criteria, then 7-axis scoring.
5. Fourteen adversarial deep dives (competitor, novelty, feasibility, problem validation).
6. Three-role local council → Top 3.

## Evidence conventions
✅ primary source read directly · ⚠️ secondary, vendor or single source · ❌ unverified · `⚠ inference` marks judgment.

## Known limitations (read these)
1. **Competitor verification is complete only for the 14 deep-dived ideas.** For the other 86, competitor names are from landscape scans; "no competitor found" is not evidence of novelty. A dedicated verification pass was started and cut off by a usage limit, and was not re-run.
2. **Several deep-dive agents exceeded their search budgets,** and a few (e.g. #20, #23) say their competitor searches were cut short.
3. **The council is a single model family** (claude-council `--local` equivalent). The suggested external multi-model council was not run because no external API keys were available.
4. **Element codes (P/A/S) and kill codes (K) were reconstructed** from usage because the original legend was not saved.
5. **Sponsor-tool codes S01 to S05 are inferred.**
6. **Sandbox behaviour is untested.** All ranking depends on [[63 - Day-1 Sandbox Test Plan]].
7. **Devpost entry counts are early (about 72 to 144 entries reviewed)** against an expected 550 to 1,100 submissions. Duplication risk will rise.
8. **User voices:** several quoted threads are search-snippet titles only and are labelled as such.
9. Knowledge date: 2026-10-12.

## What differs from the old vault
- 4.5-week online frame instead of a 7-hour build.
- Scoring tied to the five Devpost criteria.
- Every finalist was adversarially attacked before ranking; demoted ideas stay visible with reasons.
