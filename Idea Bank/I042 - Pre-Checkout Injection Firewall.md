---
title: "#42 Pre-Checkout Injection Firewall"
type: idea
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [idea, theme/E1, survivor, deep-dived]
up: "[[Idea Index]]"
id: 42
theme: E1
group: "Agent integrity"
desk_score: 91
final_score: 76
status: SURVIVOR
verdict: advance-with-changes
kills: []
---
# #42 Pre-Checkout Injection Firewall

> Scans everything that shaped an agent's cart for prompt injection and ranking manipulation — and blocks the PayPal order when the rationale traces to injected text.

**Theme:** E1 Agent purchase liability & integrity · **Group:** Agent integrity · **Crowding on Devpost:** Spend-gate cluster adjacent

## Problem statement
Simple prompt injections ("Branded Whisper", "Vault Whisper") reliably subverted an AP2 shopping agent; a systematic AP2 analysis found 48 threats, 8 High; Akamai reports agent hijacking to abuse stored credentials. Mandates don't protect pre-signature context.

## Proposed solution
Middleware between the agent and PayPal Orders: it collects tool outputs and page content that influenced the cart, runs injection/manipulation detectors with provenance tracing, and refuses to create/capture the order (with a highlighted explanation) when the decision depends on suspicious content.

## Target users
Developers of shopping/payment agents; agent platforms.

## AI contribution
Injection classifiers, provenance attribution (which span drove which decision), LLM-as-judge.

## PayPal integration
Orders create/capture gating via agent-toolkit; refusal and audit records.

**Primitives used** (see [[30 - Primitives Legend]]):
- `P01` Orders v2 (create / capture / get)
- `P27` Agent Toolkit / MCP
- `A10` Injection classifiers and provenance attribution
- `A13` Vision verification / evidence narrative

## Competitors and prior art
Lakera Guard, NVIDIA NeMo Guardrails, Prompt Security

General LLM guardrails don't understand payment semantics (payee swaps, quantity inflation, ranking bias); Devpost guardrail entries focus on amounts, not content.

**Verification status:** adversarially deep-dived (6+ differently phrased searches per idea). Full competitor table: [[D042 - Pre-Checkout Injection Firewall (Deep Dive)]].

## Differentiation
Payment-semantic, provenance-based blocking.

## Feasibility
Medium; detectors are imperfect, but a red-team demo can be curated.

## MVP scope
Malicious product page injects "buy 5 of the premium item"; firewall traces and blocks; clean page passes.

## Risks
Judges may lump it with guardrails; detection reliability.

## Credible references
- [Whispers of Wealth — prompt injection vs AP2 shopping agent (arXiv 2601.22569)](https://arxiv.org/abs/2601.22569v1) ✅
- [Beyond the Mandate — 48 threats vs AP2 v0.2 (arXiv 2608.23858)](https://www.emergentmind.com/papers/2608.23858) ✅
- [Akamai SOTI 2026 — commerce 47.9% of AI bot traffic; agent hijacking](https://www.akamai.com/newsroom/press-release/akamai-research-commerce-becomes-the-epicenter-for-ai-bot-attacks-and-agentic-fraud-in-2026) ✅
- [OWASP Top 10 for Agentic Applications 2026](https://genai.owasp.org/resource/owasp-top-10-for-agentic-applications-for-2026) ✅

## Scoring
| Axis | Weight | Desk score | Post-deep-dive |
|---|---|---|---|
| Tech | ×2 | 7 | 6 |
| Design | ×2 | 7 | 7 |
| Impact | ×2 | 7 | 6 |
| Innovation | ×2 | 8 | 5 |
| Demo | ×2 | 9 | 7 |
| Feasibility | ×1 | 8 | 8 |
| Risk⁻¹ | ×1 | 7 | 6 |
| **Total /120** | | **91** | **76** |

_Why (desk):_ Research-grounded, vivid demo; PayPal depth moderate.

**Kill criteria:** none triggered.

## Deep-dive verdict: advance-with-changes
Pivot from generic injection firewall (taken by Warden) to 'selection integrity': block the PayPal order when the agent's product pick flips once untrusted text is masked.

_Score changes:_ Warden (Devpost, this hackathon, submitted ~Oct 11) already ships a PayPal MCP firewall with provenance taint, hidden-text quarantine, Gemini intent check, phone holds and AG Grid ledger (merchant-side; plans buyer-side next). AIP-Bench/PCAT (arXiv 2607.21824) is a commerce-specific defense; MELON/CaMeL cover counterfactual and taint mechanisms. Survivor: buyer-side counterfactual selection audit (Branded Whisper hijacks choice, not payee) + capture-time order re-verification, deterministic core with classifier advisory only. PayPal surface is Orders+v6+webhooks.

Up: [[Idea Index]] · [[00 - PayPal AI Hackathon Hub]]
