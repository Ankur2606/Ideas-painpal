---
title: "10 - Event, Rules & Judging Intelligence"
type: research
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [research, paypal-hackathon]
up: "[[00 - PayPal AI Hackathon Hub]]"
description: "event, rules, judges, webinars, judging mechanics"
confidence_key: "✅ primary / ⚠️ secondary / ❌ unverified"
---
# B — PayPal AI Hackathon 2026: Event Mechanics, Sponsors, Judges, Prior Winners, Duplicate Archetypes

Researched 2026-10-11. Confidence tags: ✅ primary source (official page, the person's own talk or post, the actual transcript) · ⚠️ secondary source (press, aggregator, third-party profile) · ❌ unverified or not found. `⚠ inference` marks my own judgment.

---

## 0. Key facts at a glance

| Item | Value | Source |
|---|---|---|
| Submission window | Oct 1, 2026 9:15am PT → **Nov 12, 2026 12:00pm PT** (= 3:00pm EST) | ✅ [Rules §1](https://paypalaihackathon.devpost.com/rules), ✅ [Dates](https://paypalaihackathon.devpost.com/details/dates) |
| Judging | Dec 1 (2pm PT) → Dec 15 (8am PT) 2026 | ✅ [Rules §1](https://paypalaihackathon.devpost.com/rules) |
| Winners announced | ~Dec 21, 2026, 12:00pm EST | ✅ [Dates](https://paypalaihackathon.devpost.com/details/dates) |
| Registered participants | **11,274** (on Oct 11) | ✅ [Overview](https://paypalaihackathon.devpost.com/) |
| Cash | $67,500 headline. The "Why Join" copy says "$69,750 in total prizes" (likely counting Render credits and APIMatic subscriptions) | ✅ [Overview](https://paypalaihackathon.devpost.com/) |
| Tracks | **None.** "No prescribed problem statements and no set of tracks." The one hard requirement is to "meaningfully use both PayPal and AI" | ✅ [Overview](https://paypalaihackathon.devpost.com/) |
| PayPal scope | Any PayPal-family service counts: "Venmo, Braintree, Xoom, Honey, Zettle, Paidy, Hyperwallet, Simility, Swift Financial, and others", used in the free sandbox | ✅ [Rules §4](https://paypalaihackathon.devpost.com/rules) |
| Gallery | Not yet published | ✅ [Gallery](https://paypalaihackathon.devpost.com/project-gallery) |

⚠ **Deadline discrepancy:** in the kickoff webinar Jo Franchetti said submissions close at "2:00 p.m. Pacific time" ([video](https://www.youtube.com/watch?v=FFJfCW9z3Do), ✅ transcript). The Rules say 12:00pm PT, and the Rules prevail in any conflict (Rules §11.4). **Plan for 12:00pm PT / 3:00pm EST, Nov 12.**

---


## 2. Judges — public signals and what they likely reward

General caveat: Rules §6 says judges "may or may not be listed individually," "may change," and judging "may utilize… **automated AI-driven analysis**." ✅ [Rules](https://paypalaihackathon.devpost.com/rules)

### PayPal DevRel (they hosted the kickoff, and they are the most likely Stage-1 and HM gatekeepers)

**Jo Franchetti — Developer Advocate, PayPal (UK)**
- Profile: "Software Engineer and Developer Advocate at PayPal (UK)," focused on DX, TypeScript and "teaching good use of the web." She mentors and promotes mental health, diversity and inclusion. ✅ [GitNation](https://gitnation.com/person/jo_franchetti). Previously DevRel at Deno. ⚠️ [WeAreDevelopers](https://www.wearedevelopers.com/@jo-franchetti) (stale profile)
- 2026 talks:
  - *"Personalisation Without the Price Tag: Local LLMs for JavaScript Developers"* (JSNation and React Summit 2026). Covers schema-structured prompts, "validating and repairing unpredictable output," and running models locally to control cost and environmental impact.
  - *"npm install && pray"* (Node Congress 2026). Covers supply-chain attacks, risks of AI-generated code, and sandboxing untrusted code.

  ✅ [GitNation](https://gitnation.com/person/jo_franchetti)
- Kickoff quotes: PayPal must be "central to what your project does… not something that's just bolted on." "Presentation is a full fifth of your score." "Don't leave the demo video until the last minute." ✅ [kickoff](https://www.youtube.com/watch?v=FFJfCW9z3Do)
- ⚠ inference — likely rewards: schema-validated LLM output with repair loops; deliberate cost and model choices (a local or small model where it fits); security hygiene (secrets server-side, sandboxing, dependency care); accessibility and good web practice; PayPal in the core loop; a polished, clear video.

**Eddie Jaoude — Developer Advocate, PayPal (UK)**
- He is a long-time open-source advocate: "Open Source is about people, community and collaboration." He founded the EddieHub community and BioDrop (an open-source Linktree alternative built with Next.js, Tailwind, Playwright, GitHub Actions and Kubernetes). He makes YouTube and live content including "GitHub Profiles that Stand Out," where he reviews repos live. ✅ [GitHub Stars profile](https://stars.github.com/profiles/eddiejaoude)
- Kickoff (sandbox segment): he stressed separate business and personal sandbox accounts, webhooks with signature verification, retries, debugging via event logs, and **"test the unhappy paths, not just the happy path… negative testing."** He also said "chat in public… this is a collaboration." ✅ [kickoff](https://www.youtube.com/watch?v=FFJfCW9z3Do)
- ⚠ inference — likely rewards: a **repo that looks like a real OSS project**, with a clear README, LICENSE in the About panel, CONTRIBUTING, issues, CI (GitHub Actions), tests (Playwright) and a one-command run. He wants webhook verification and visible handling of failure paths (declines, cancels, refunds). Public Discord participation probably helps too.

**Marco Podien — Developer Advocate, PayPal (Germany)**
- Previously a developer advocate at the Algorand Foundation. His talks cover **end-to-end TypeScript / type safety** and "Real-World Problems That Blockchain Actually Solves." ⚠️ [WeAreDevelopers](https://www.wearedevelopers.com/@marco-podien) (profile predates his PayPal role). PayPal DevRel job postings for Germany and the UK appeared in 2026. ⚠️ [AnitaB jobs](https://jobs.anitab.org/companies/paypal/jobs/68717394-developer-advocate-devrel-germany)
- Kickoff: "Approach your whole idea **from the idea first**. Don't look for a PayPal product… and then try to push something into it… think about a problem… then map this to the PayPal capabilities." He toured the beyond-checkout capabilities (Invoicing, Subscriptions, Payouts, Disputes, Login with PayPal, Order Tracking, Fastlane, Vault, Pay Later) and pointed to the Postman collection's agentic-commerce examples. ✅ [kickoff](https://www.youtube.com/watch?v=FFJfCW9z3Do)
- ⚠ inference — likely rewards: problem-first framing; non-checkout PayPal capabilities used appropriately (Payouts, Disputes, Tracking, Vault); typed end-to-end code (TypeScript, Zod schemas shared between front end and back end). He may respond well to PYUSD or stablecoin use if it is genuinely problem-driven (his Algorand background; PYUSD appeared in a 2025 PayPal hackathon winner, §4). Not verified.

**Nathaniel Olson — Senior Product Manager, PayPal**
- Co-presented the APIMatic webinar. He described his frustration with vibe-coding agents installing "SDKs that were two, three, sometimes even five years old." He championed Context Plugins internally, saying they turned "demos into somewhat of a magic trick," and he values **live-demo reliability**: "I've never had a single concern while running with the context plugin." He also evaluated Context7 as an alternative. ✅ [APIMatic webinar](https://youtu.be/zRWixN68tDg)
- ⚠ inference: He appears to own AI developer tooling (Context Plugins, possibly the AI Toolkit). Likely rewards: current SDK versions (JS SDK v6, Server SDKs), production-ready error handling, and demos that work reliably end to end. A PM lens means a clear user and problem framing.

**Karthik Ravi — Software Engineer, PayPal** · **Himraj Singh — Engineering Manager, PayPal**
- ❌ No attributable public talks or posts found. Searches returned only unrelated profiles or job listings.
- ⚠ inference: Engineering judges probably weight Technological Implementation, which is also the first tie-breaker. Expect them to look at real API depth (more than Orders create/capture), correct webhook handling, idempotency, and whether the AI does real work rather than producing text.

### Sponsor judges (likely judge their sponsor prize; may also sit on main panels)

**Sylwia Vargas — Senior Technical Community Manager, AG Grid**
- She was DevRel Lead at StackBlitz. Her topics are React, DX, **web accessibility**, linguistics, curriculum design and **realtime collaboration (CRDTs)**. She co-organises React Robins (a community for women and non-binary React developers). ⚠️ [Sessionize](https://sessionize.com/sylwia) (pre-AG Grid). She is listed as contact for AG Grid's "Beyond the Prompt" conference. ✅ [agenda](https://ag-grid.com/downloads/beyond-the-prompt/beyond-the-prompt-agenda.json)
- The AG Grid prize page tone ("Bring your curiosity, creativity, and personality!", Friends and The Office storefront jokes) suggests she wrote it or influenced it. ⚠ inference
- ⚠ inference — likely rewards: personality and polish, custom widgets and theming (explicitly asked for), accessible UI, a multi-user or collaborative dashboard, and use of the Agent Framework beyond the defaults.

**Ameer Hassan — Co-Founder (listed), APIMatic**
- His Nordic APIs bio describes him as "VP Strategy & Business Development," a self-described "non-developer who enjoys helping developers." He came from banking and telecom product and strategy, and his talk was "Developing a Business Case for SDKs Driven API Adoption." ⚠️ [Nordic APIs](https://nordicapis.com/speakers/ameer-hassan/) (old)
- ⚠ inference — likely rewards: a clear business case and measurable DX improvement from the plugin (for example, "integration built in X minutes, Y error paths handled").

**Mats Bryntse — CEO, Bryntum**
- He keynoted Beyond the Prompt 2026 and gave the talk "One-click agentic SDLC." ✅ [agenda](https://ag-grid.com/downloads/beyond-the-prompt/beyond-the-prompt-agenda.json). A Bryntum DevRel recap credits him with five rules: **"Automate what you understand." "Force evidence. Especially tests." "If the agent can't explain it, don't ship it." "Keep humans in the loop where risk is high"** (citing *payments* explicitly), and prioritise value over perfection. ✅ [Bryntum blog, May 22 2026](https://bryntum.com/blog/reflections-on-the-beyond-the-prompt-2026-conference/)
- ⚠ inference — likely rewards: agent-driven scheduling with explicit human approval at payment-risk points; tests in the repo; an agent that explains its scheduling decisions.

**Ignacio Valdez Bicard — Founding Engineer, Channel3**
- ❌ No attributable public content found.
- Company context: Channel3 is building a neutral catalog for agentic commerce and earns money through affiliate attribution on buy links. ✅ [UCP docs](https://docs.trychannel3.com/use-cases/ucp), ⚠️ [SiliconANGLE](https://siliconangle.com/2025/12/10/channel3-raises-6m-make-every-single-product-sold-web-discoverable-ai-agents/)
- ⚠ inference — likely rewards: heavy, non-trivial API use (image or URL search, filters, multi-retailer offers, enrichment) beyond a single keyword search, and a flow that ends in a real purchase. A founding engineer will notice whether the integration is deep or decorative.

**Carly Richmond — Senior Manager, Developer Advocacy, Elastic**
- Search Labs posts: **"What is context engineering?"** (Sep 4, 2025), covering prompts, RAG, memory, tools and structured outputs, warning about "context confusion" and "context poisoning," and recommending keeping tool sets small (the RAG-MCP pattern). Also "Building AI agents with AI SDK and Elastic" (Mar 2025). ✅ [author page](https://www.elastic.co/search-labs/author/carly-richmond), ✅ [article](https://www.elastic.co/search-labs/blog/context-engineering-overview). Her Devoxx UK talk "Retrieval in an AI Era" covered naive RAG through agentic RAG with reranking. ✅ [Devoxx](https://devoxx.co.uk/talk%3Fid=35454.html). She has also written on Kibana dashboard design and RUM. ✅ [Elastic blog](https://www.elastic.co/blog/author/carly-richmond)
- ⚠ inference — likely rewards: deliberate retrieval (hybrid BM25 plus vector, reranking), small curated tool sets, structured outputs, and agent evaluation, with the reasoning explained in the README.

**Pooja Mistry — Sr. Developer Advocate, Postman**
- She authored the Astropods walkthrough (Oct 7, 2026). ✅ [Postman blog](https://blog.postman.com/build-ai-agents-with-astropods/). She ran "AI-Powered API & MCP Bootcamp" (PlatformCon, June 26, 2026). ✅ [PlatformCon](https://2026.platformcon.com/speakers/pooja-mistry). Earlier she led IBM's partnership advocacy and gave an API testing workshop. ✅ [GitNation](https://gitnation.com/person/pooja_mistry)
- ⚠ inference — likely rewards: Astropods or Postman used meaningfully (traces, evaluators, collections with tests), and an API-first design where the agent's tools are well-specified APIs.

**Shifra Williams — Founding DevRel Engineer, Render**
- Interview (Oct 2, 2026). Her guiding question is "How does this make my developer's day better?" She rejected AI-generated video: "They want to hear from real people… a real human developer experience." She regrets not emphasising throughput in her Workflows demo. ✅ [HackerNoon](https://hackernoon.com/how-does-this-make-my-developers-day-better-asks-render-founding-devrel-engineer-shifra-williams)
- Talks: "Building for Agent Experience" (Render's MCP server, CLI and agent skills, designed for humans *and* agents), "Ship a Production Voice Agent" (LiveKit on Render). ✅ [GitNation](https://gitnation.com/person/shifra_williams)
- ⚠ inference — likely rewards: a real deployed service (not localhost), Workflows used for real concurrency, scale shown in the demo, and **a real human voice in the video** (avoid fully AI-generated narration and avatars).

### Cross-judge synthesis (⚠ inference)
1. **Trust and safety around money** comes up again and again: Mats (humans in the loop for payments), Jo (sandboxing, validation), Eddie (unhappy paths, webhook verification), Carly (structured outputs), Pooja (evaluators flagging PII). It is valued, but **it is also the single most-duplicated idea on Devpost already** (§4). Treat it as table stakes, not the pitch.
2. **Production realism over vibe code**: Nathaniel, Mats, APIMatic and Shifra all talk about "production-ready" code.
3. **Problem-first, beyond-checkout PayPal use**: Marco.
4. **OSS repo quality**: Eddie, and Jo's invitation to contribute.
5. **A human, clear, 3-minute video**: Jo, Shifra, and the "Best Demo Delivery" prize.

---


## 3. Webinars

### 3.1 "Start building with PayPal" kickoff (Oct 6, 2026)
- Actual YouTube title: **"Set Up PayPal's Sandbox and AI Toolkit From Scratch (Live Walkthrough)"**. Uploaded by Devpost on 2026-10-06, 44:35 long, about 1,315 views on Oct 11. Speakers were Jo Franchetti, Marco Podien and Eddie Jaoude, hosted by Darlyze Calixte (Devpost). **The full transcript was retrieved.** ✅ [YouTube](https://www.youtube.com/watch?v=FFJfCW9z3Do) (via Firecrawl's YouTube post-processor)
- Chapters: 0:10 hackathon overview · 8:35 what PayPal offers · 14:20 Postman collection · 15:33 AI Toolkit · 17:38 toolkit commands · 19:08 sandbox MCP server · 23:58 docs and agent frameworks · 25:35 sandbox walkthrough · 31:20 credentials · 34:10 webhooks · 39:08 debugging · 40:35 demo project and unhappy paths. ✅
- Key takeaways (all ✅ transcript):
  - "Adding a PayPal button to an unrelated app is not going to be enough."
  - Elevator pitch is framed as "what you'd say to a friend at the pub or to an investor." Existing projects are allowed if meaningfully extended. Multiple substantially different entries are allowed.
  - **"Best demo delivery is also a real $5,000 prize. So that three-minute video could get you $5,000."**
  - Prize stacking is encouraged: "you could be prize stacking."
  - Practical gotchas: sandbox MCP tokens expire roughly every 9 hours (run `/paypal:setup refresh`). App feature toggles take up to 10 minutes to apply. Enable Transaction Search. Webhooks retry up to 25 times over 3 days. Verify webhook signatures. Use ngrok or Cloudflare tunnels locally. Keep sandbox personal and business accounts in the same country.
  - Example MCP prompt: "create a subscription plan at $9 a month with a two-week trial, then subscribe this test buyer."
  - PayPal example code: [paypal-examples/docs-examples](https://github.com/paypal-examples/docs-examples).

### 3.2 APIMatic webinar (Oct 7 live, uploaded Oct 9)
- Title: **"Power Your PayPal Hackathon Project with APIMatic Context Plugins"**. PayPal Developer channel, 24:56, about 78 views. **The full transcript was retrieved.** ✅ [YouTube](https://youtu.be/zRWixN68tDg)
- Speakers: Nathaniel Olson (PayPal PM) and an APIMatic engineer (name transcribed as "Sohabe"; ❌ spelling unverified).
- Content: vibe-coding failures with stale SDKs, the benchmark claim (Context Plugin beats docs-MCP, OpenAPI-only and no-context approaches across models from "GLM 5.3 flash" to "Opus 4.8"), the five covered APIs, a live demo building a coffee-shop checkout ("Little Bean Coffees") in 5–7 minutes, and the prize rules (§1.2).
- The demo prompt is in the video description. ⚠ inference: expect *many* coffee-shop and simple-storefront clones built from this exact prompt. Do not resemble it.

### 3.3 Remaining
- Oct 12, 7am PT: "Build a payments dashboard without building a dashboard" (Teams; likely AG Grid). ❌ not yet held.
- Oct 13, 1am PT: an APAC repeat of "Start building with PayPal." ✅ [Overview](https://paypalaihackathon.devpost.com/)
- Other updates: "Live Build Session Oct 6," "FAQs," and "The PayPal build session recording is up." ✅ [Updates](https://paypalaihackathon.devpost.com/updates)

---


## 5. Devpost judging mechanics and strategic implications

### 5.1 Mechanics (all ✅ [Rules](https://paypalaihackathon.devpost.com/rules) unless noted)
- **Stage One, pass/fail:** "whether the ideas meet a baseline level of viability… reasonably fits the theme and reasonably applies the required APIs/SDKs."
- **Stage Two:** five **equally weighted** criteria (Technological Implementation, Design, Potential Impact, Innovation/Idea, Presentation), each worth 20%.
- **Tie-break order:** criteria in listed order. **Technological Implementation first**, then Design, Impact, Innovation, Presentation. If still tied, the judges vote.
- **Judges are not required to test:** they "may choose to judge based solely on the text description, images, and video." The project must still be "available free of charge… until the Judging Period ends," with test credentials or sandbox logins in the README.
- **Video:** under 3 minutes; "judges aren't required to watch past that." It must be public on YouTube, show the project running on its target device, and contain no unlicensed music or third-party trademarks. ✅ [Overview](https://paypalaihackathon.devpost.com/)
- **Functional demo required:** repo setup instructions *or* a hosted URL. "A design mockup, static prototype, or non-functional demo does not meet this requirement."
- **Repo:** must be public on GitHub, GitLab or Bitbucket, with an OSS license "detectable and visible at the top of the repository page (in the About section)."
- **Judging may use "automated AI-driven analysis."** (§6)
- **Prize stacking:** at most one Grand Prize + one Sponsor Prize, *or* one Honorable Mention + one Sponsor Prize. You cannot win a Grand Prize and an HM together, or two sponsor prizes. ✅ Rules §8, ✅ [FAQ](https://paypalaihackathon.devpost.com/details/faqs)
- **Existing projects** must be "significantly updated" during the window, and entrants should explain how. **Multiple submissions** must be "substantially different."
- **Eligibility:** age of majority. Excludes Brazil, Quebec, Russia, Crimea, Cuba, Iran, North Korea and OFAC-sanctioned countries; the exclusion applies to every team member. India is not excluded. ✅ Rules §3, FAQ. No team-size cap. ✅ FAQ

### 5.2 Strategic implications (⚠ inference throughout)
1. **Design for a judge who never runs the code.** The video and the Devpost text are the real product. Spend real effort on a tight 2:45 video: problem in 15s, live end-to-end flow showing PayPal sandbox state changing (both buyer and merchant views, as Eddie demoed), and the architecture in 20s. Presentation is 20% and also unlocks the $5k Best Demo Delivery prize.
2. **Clear Stage One unambiguously.** Name the exact PayPal APIs in the first lines of the description (for example "Orders v2 + Payouts + Disputes + Webhooks via the PayPal MCP server / Server SDK"). Show PayPal in the core loop within the first 30s of the video. Given possible AI-driven screening, use explicit, machine-legible headings: "PayPal integration," "AI integration," "How to run," "Sandbox test accounts."
3. **Win the tie-break: depth on Technological Implementation.** It is both a 20% criterion and the first tie-breaker. Use **at least 3 PayPal capabilities beyond basic checkout** (Payouts, Disputes, Subscriptions, Invoicing, Vault, Transaction Search, Shipment tracking), with **verified webhooks** and visible unhappy-path handling (decline, cancel, refund, retry). Make the AI do consequential work (planning, tool calls, structured decisions), not just generate text.
4. **Avoid the 12 archetypes as the *headline*.** If you build in one, the differentiator must be visible in the first 20 seconds. The Innovation criterion literally asks "does the project differ from existing concepts?" Judges will have seen five PayPilots.
5. **Treat "Design" as product completeness**, not visuals ("complete, coherent product experience — not just a technical proof of concept"). That means onboarding, empty states, error states and a real end state.
6. **Potential Impact needs a named audience and evidence** ("a credible, specific case… for a real audience"). Use a specific persona and numbers, ideally a real user quote or pilot.
7. **Prize-portfolio play:** aim for one main or HM prize plus one sponsor prize. AG Grid has the best sponsor EV ($10k across 5 slots, with polish and agent-framework criteria a strong team can hit). APIMatic is near-free eligibility (use the plugin, answer the form question), but it can't stack with another sponsor prize, so pick the sponsor you can win most convincingly. HM categories are mutually exclusive with Grand Prizes, so a project wins at most one of those.
8. **Hosted demo plus one-command repo.** Deploy on Render (possible Render prize, satisfies "functional demo"). Add a seeded sandbox and test-account credentials in the README. Include CI, tests and a LICENSE in the About panel (Eddie's lens).
9. **Signal PayPal-insider fluency:** current SDKs (JS SDK v6, Server SDKs), the AI Toolkit's `/paypal:doctor` passing, and ideally a merged PR to paypal/AI-Toolkit cited in the submission.
10. **Use a real human voice in the video**, not an AI avatar (Shifra's explicit stance; Jo and Eddie are human-centric DevRel). Use royalty-free music or none (a rules requirement).
11. **Timing:** submit drafts early. The Devpost submission is locked after Nov 12 12:00pm PT, but the repo can keep improving (judges review during Dec 1–15). ⚠ The Rules say judging relies on the submitted materials, so don't count on post-deadline changes.

---


## 6. Gaps / not verified
- Karthik Ravi, Himraj Singh, Ignacio Valdez Bicard: ❌ no public professional content found.
- Nathaniel Olson: known only from the APIMatic webinar. No other public footprint found.
- Marco Podien and Sylwia Vargas profiles predate their current roles. Their current-role statements come from Devpost and the kickoff.
- Postman, Render and Zapier detail pages were read via a WebFetch summary because of a Firecrawl rate limit. Core facts (credits, trial) are consistent but not verbatim.
- Devpost "Built with PayPal" project-to-hackathon attribution is inferred.
- Total final submission count is an estimate.
