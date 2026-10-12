---
title: "14 - Prior Winners & Duplicated Archetypes"
type: research
project: PayPal AI Hackathon 2026
created: 2026-10-12
tags: [research, paypal-hackathon]
up: "[[00 - PayPal AI Hackathon Hub]]"
description: "what won comparable hackathons and which ideas will be duplicated"
confidence_key: "✅ primary / ⚠️ secondary / ❌ unverified"
---
# Prior winners and duplicated archetypes

_Extract of section 4 of the event report._

## 4. Prior winners and the most-duplicated archetypes

### 4.1 Comparable hackathons — what won

**PayPal Dev Days 2025 Hackathon** (San Jose, under 24 hours, article dated May 29, 2025). Tracks were Agentic Integrations (MCP Server / Agent Toolkit), Vibe Coding with Replit, and Upgrade Your Legacy Integration. ✅ [PayPal Dev blog](https://developer.paypal.com/community/blog/winners-dev-days-hackathon)
- 1st **CrawlerPal**: "a paywall AI agent assistant built with PayPal APIs" ($5k + AWS credits).
- 2nd **Codebusters**: migrated Shopware 6's PayPal integration from JS SDK v5 to the beta v6.
- 3rd **Rosen**: upgraded a PYUSD-powered social trading app.
- ⚠ inference: PayPal judges rewarded (a) agents paying for content access (pay-per-crawl), (b) unglamorous **adoption of the newest SDK** in real OSS, and (c) PYUSD.

**SKALE / Coinbase / Google "Agentic Commerce x402" hackathon** (San Francisco plus online, Feb 2026). 324 registered, 86 submissions. Judged on partner integration, **agentic depth, commerce realism, polish/ship-ability**. ✅ [SKALE blog](https://skale.space/blog/san-francisco-agentic-commerce-x402-hackathon-recap-winners)
- Winners: World of Geneva (autonomous agents playing an RPG), Moltbet (prediction market *for agents*), Superpage (agents paying for real e-commerce), Pincer (ad-sponsored 402 paywall fees), Legasi (credit and reputation layer for agents), RequestTap (open-source x402 router, AP2 track), Civiclens (civic rewards).
- ⚠ inference: winners treated **agents as economic actors** (agent-to-agent markets, credit, reputation) rather than as human shopping assistants.

**Agentic Commerce on Arc** (lablab.ai, Circle/Arc plus Google, Jan 9–24, 2026). 1,200+ people, 222 teams. ✅ [lablab.ai](https://lablab.ai/blog/agentic-commerce-on-arc-ai-hackathon)
- Winners: NewsFacts, AisaEscrow, VibeCard rewards, RSoft Agentic Bank, Arcana, AI Merchant Studio & Storefront (Best Design), OmniAgentPay ($20k GCP), Arc Merchant (x402 micropayments), JoyKeep. Common types were agentic banking, **escrow**, storefront and merchant tools, rewards, agent payment infrastructure, stablecoin SDKs and insurance.
- Google raised its prize pool from $10k to $40k because entries looked like "viable businesses."

**Solana x402 Hackathon** (winners Dec 2025). Sentinel Agent (agent monitoring paid via x402), Galaksio (USDC to instant compute), ParallaxPay, Agentx402, x402Resolve and others. Themes were micropayments and paid APIs for agents. ⚠️ [Phemex, citing an X post](https://phemex.com/news/article/solana-x402-hackathon-announces-winners-in-micropayments-and-ai-41757)

**MACH AI Exchange Hackathon** (Bloomreach, article Jul 2026). 900+ registrants, 83 teams. Winner SilentWatch (churn reactivation). The write-up says the best entries "were not just wrapping a language model in a chat box" and that orchestration across systems with human approvals mattered more. ⚠️ [MACH Alliance](https://machalliance.org/insights-hub/from-who-showed-up-to-what-they-built)

**Historical PayPal hackathons:** BattleHack (2014–15; for example WeBzerking Care, "TransferWise for charity donations") and Opportunity Hack. These show PayPal has a long history of rewarding social-impact giving. ⚠️ [Silicon Allee](https://news.siliconallee.com/?p=27286), [PayPal APAC](https://newsroom.apac.paypal-corp.com/PayPal-announces-winners-of-Opportunity-Hack-2016)

### 4.2 Direct evidence of this hackathon's clustering
Devpost's public "Built with PayPal" listing already shows dozens of PayPal + AI sandbox projects. Most are almost certainly this hackathon's in-progress entries: they mention the sandbox, Orders v2 and agents. I reviewed about 72 entries across pages 1–3. ✅ [page 1](https://devpost.com/software/built-with/paypal) · [page 2](https://devpost.com/software/built-with/paypal?page=2) · [page 3](https://devpost.com/software/built-with/paypal?page=3) (WebFetch summaries. ⚠ Hackathon attribution is inferred; the listing doesn't show hackathon names.)

Rough counts of the archetypes I observed (one project can count in more than one):

| Observed cluster | ~Count / 72 | Examples |
|---|---|---|
| **Agent spend governance / human-approval payment gate** (policy engine, budgets, mandates, audit) | ~13 | AGENT GATE, Pulse Safe Commerce Agent, PayGuard, BOLT Control Plane, AgentAllowance, Leash, BoundPay, LexProof, VELQIRIS Evidence Gate, XReceipt, AI PAY, PayPilot (deterministic router) |
| **Escrow / pay-on-verified-work** (AI judge releases funds) | ~11 | JudgePay, EscrowEase, AgentEscrow, PACT, Handovr AI, LOCIM, Accepted Work Settlement, MergePay (GitHub bounties), Nightcall Pays, Timeline Studio, Paceline |
| **Shopping / checkout agent** | ~10 | Agentic Cart, Checkout Agent, acp-sandbox, Dukkan, AgentBaazar, AgentDeal, CarryPay, ShopVoice Pay, MAHI, Babes & Babies |
| **"Talk to PayPal" NL payment assistant** | ~8 | **"PayPilot" appears as the name of 5 separate projects**, plus PayFlow AI, PayBuddy AI, PayAgent AI, SmartPay AI, PayGroq |
| **Disputes / refunds / chargebacks** | ~7 | SubGuard, Fairplay, Rebuttal, Refund Desk, PayGuard AI, PayPilot Resolve, HoldWatch |
| **Reconciliation / bookkeeping / insights** | ~6 | Chaser, Caseproof, Invoice-Sync, Salah, SmartPay AI, Parts Ledger |
| **Group pay / splitting / group buy** | ~6 | Together, Tipping Point, Rally, SarafuPay, PayBuddy, Parts Ledger |
| **Invoice generation / AR chasing** | ~4 | PayPilot (invoices + chase), Clause-to-Cash, Vendora, Paceline |
| **Booking / front-desk agent with deposits** | ~4 | Vidal Booking, paypal-frontdesk, Glow Pilot, TownHubs |
| **Photo → price → list → sell** | ~2 | SHELF, Resell.Store |
| **Subscription cancel / guard** | ~2 | Subscription Killer, SubGuard |

⚠ inference: these ~72 visible entries are early movers about 10 days into a 6-week window, from a pool of 11,274 registrants. They are a leading indicator. Assuming a typical Devpost submit rate of roughly 5–10%, expect **about 550–1,100 final submissions** (estimate, not sourced).

### 4.3 The ~12 most-duplicated archetypes expected (ranked by expected volume)

Evidence key: [D] = seen on Devpost "Built with PayPal" (§4.2) · [S] = suggested on an official sponsor page or webinar · [P] = recurring winner or entry type in prior agentic-commerce hackathons (§4.1).

1. **AI shopping agent that searches products and pays with PayPal** (often with Channel3). [D][S Channel3 "shopping agents, gift finders, AI stylists"][P Superpage, KERNEL "Personal Shopper" cookbook]
2. **Human-in-the-loop "agent wallet" / spend-policy gate / mandate layer.** [D ~13][P Legasi, OmniAgentPay]. Judges' own talking points (Mats, Jo) push people here.
3. **AI escrow / milestone release by an "AI judge"** for freelancers or bounties. [D ~11][P AisaEscrow]
4. **Natural-language PayPal assistant ("PayPilot")** that sends money, creates invoices, checks balances or summarises transactions over the MCP server. [D ~8, name collisions][S the AI Toolkit makes this a 10-minute build]
5. **AI dispute / chargeback / refund assistant** for merchants. [D ~7][S Bryntum "dispute triage board"]
6. **Merchant analytics / anomaly dashboard / "ask your revenue."** [D][S AG Grid storefront, anomaly-alert and NL-finance ideas][P MACH: analytics most common]
7. **Invoice generator plus payment-reminder ("nudge") agent.** [D][S AG Grid "Nudge-bot"]
8. **Bill / receipt splitting and group payments** (OCR receipt → PayPal requests or payouts). [D ~6]
9. **Personal budgeting / spending-insights chatbot** over transaction data. [D SmartPay, Salah, MamaPal]
10. **Subscription manager / forgotten-subscription killer.** [D][S Bryntum "subscription revenue radar"]
11. **Booking or appointment agent with PayPal deposits** (salons, rentals, tickets). [D ~4][S Bryntum "equipment rental," "event ticketing"]
12. **Donation / creator-tipping / nonprofit dashboard.** [S AG Grid "nonprofit donation dashboard"][P BattleHack charity winners]. Honorable mention: the **simple storefront / coffee-shop checkout** cloned from the APIMatic demo prompt [S], and **photo-to-listing resale agents** [D].

⚠ inference — strategic reading: archetypes #2 and #3 look sophisticated, which is exactly why they are crowded. Teams read the same "trust and agents" discourse. A project that *contains* a safety gate is fine. A project whose *pitch* is the safety gate will sit among ~10% of the field.

---

