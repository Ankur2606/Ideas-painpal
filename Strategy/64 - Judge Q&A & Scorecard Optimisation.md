---
title: "64 - Judge Q&A & Scorecard Optimisation"
type: strategy
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [judging, scorecard]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Judge Q&A and scorecard optimisation

Rules facts (✅ [Official Rules](https://paypalaihackathon.devpost.com/rules)): Stage 1 is pass/fail on theme and API use. Stage 2 scores five equal criteria. Judges may not run your code and may use automated AI analysis of the repo. The kickoff said "adding a PayPal button to an unrelated app is not going to be enough", "test the unhappy paths" and "start from the problem, not a PayPal product" (✅ [kickoff transcript](https://www.youtube.com/watch?v=FFJfCW9z3Do)).

## What to show for each criterion (for #23)
| Criterion | Make visible |
|---|---|
| Technological Implementation (first tie-break) | Orders, Transaction Search, Tracking, Disputes and webhooks in one loop; tests; a README "PayPal APIs used" section naming endpoints. The AI repo scan reads this first |
| Design | One persona (a small seller), one start and end state, an AG Grid queue with protection status |
| Potential Impact | Quote the PayPal clause; show a real loss story; cite the figures actually verified. Do not claim a scam frequency that has not been measured |
| Innovation | State once what existing tools (ShipStation, Shippo) do not do: validate for Seller Protection eligibility, not deliverability |
| Presentation | Open with a person and a loss, not "we built an AI agent". End with a 10-second unhappy-path montage. Real sandbox state changes, never a mock |

## Likely judge questions and honest answers
| Question | Answer |
|---|---|
| Isn't this a rules engine? | Partly. The verdict on policy is rule-based on purpose. The model does what rules cannot: multilingual intent with a quoted span, fuzzy address equivalence (forwarders, reshippers), label OCR |
| Where do buyer messages come from? | They live off-PayPal. The MVP takes a pasted or forwarded message. Say so |
| Does PayPal already warn sellers before shipping? | Not verified either way. The follow-up hunt found no such tool, but check PayPal's seller dashboard before the video |
| Is the protection verdict reliable? | It is advisory, with cited clauses. Never promise protection. Policy varies by region; the US Jan 2026 and UK Jul 2026 terms were read |
| Why would a seller trust AI with tracking uploads? | Human confirms; the AI only drafts |
| What if the buyer never sent a message? | The address and proof-of-delivery checks still run |
