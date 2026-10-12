---
title: "65 - Risk Analysis"
type: strategy
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [risk]
up: "[[00 - PayPal AI Hackathon Hub]]"
---
# Risk analysis

| Risk | Likelihood | Impact | Applies to | Mitigation |
|---|---|---|---|---|
| Sandbox `seller_protection` never varies | Medium | High | #23 | T1 on day 1; present the verdict as a policy table and say so |
| Late-found competitor for the seller-protection preflight | Medium | High | #23 | A follow-up hunt (addendum in the #23 deep dive) found DisputeDesk, which overlaps the evidence-pack and AG Grid modules but not the pre-ship gate. Keep the gate as the headline. Re-check Devpost weekly |
| Provenant judged a near-duplicate | High | High | Wrong Box | Lead with the buyer and the photo; position as pre-dispute and fact-driven |
| Dispute create endpoint is limited-release | Medium | High | Wrong Box | Fall back to a UI-created dispute |
| Payout failure branches only mocked | Medium | Medium | #55 | Build the hero loop on real UNCLAIMED state |
| Hosted PayPal sandbox MCP broken (since Oct 8, issue #34) | High | Low | all | Use the REST API or local agent-toolkit |
| Policy variation by region | High | Medium | #23 | State the region; never promise protection |
| AI judged decorative | Medium | High | #23, #28 | Show model-only capabilities on screen |
| Duplicate archetype fatigue (spend gates, escrow, shopping agents, PayPilot) | High | High | any idea in those clusters | Avoid the words "gate", "escrow", "shopper" in the headline |
| Time: 4.5 weeks, 1 to 3 builders | Medium | High | all | Cut to must-haves in [[63 - Day-1 Sandbox Test Plan]] |
| Same-model council bias | High | Medium | recommendation | Seek an outside human review of the shortlist |
