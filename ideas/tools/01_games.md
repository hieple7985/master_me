# Hack / Cheat / Bot Tool Case Studies (Public)
 
## Scope
This note documents publicly reported case studies about commercial cheating/bot ecosystems in games.
 
It is intentionally non-operational:
- Describes concepts at a high level.
- Avoids instructions, code, bypass methods, or implementation details that enable cheating.
 
## Terminology (quick)
- **Cheat**: software/hardware that provides unfair advantage in competitive gameplay.
- **Botting / automation**: software that plays or assists play automatically.
- **Tooling** (neutral): could be analytics, training, coaching, overlays, replay parsing, etc.
 
## “Công nghệ” của các tool dạng cheat/bot (khái niệm)
The market usually packages cheats like a software product:
- **Client/loader**
  - A desktop app that authenticates subscriptions, updates, and starts the game + module.
- **Update & delivery**
  - Frequent updates because anti-cheat/game patches change.
- **Privilege model (PC games)**
  - Some run in regular user space; others attempt deeper integration (more risk, more detection/legal issues).
- **Data access patterns**
  - Reading game state (memory/telemetry) to surface hidden info.
  - Automating inputs (aim assistance, timing automation) via software/hardware.
- **Evasion & operational security (why it’s a “business”)**
  - Obfuscation, anti-tamper, account binding, HWID policies, support/dispute handling.
 
For botting (automation) specifically, typical components are:
- **Perception**: reading the screen (computer vision) or reading internal game state.
- **Decision**: rules/ML policy.
- **Action**: simulating inputs (mouse/keyboard/controller) or calling exposed APIs.
 
## Bot farming có vi phạm không?
In practice, almost always **yes** when it targets public matchmaking, ranked ladders, economy, or account progression.
Reasons:
- Violates **Terms of Service / rules** (unfair advantage, automation, manipulation).
- Harms ecosystem: matchmaking integrity, boosting, account selling, RMT.
- Even if “just automation”, it can still be treated as cheating.
 
Example (Dota 2): Valve states that **running any application that reads data from the Dota client while playing can lead to a permanent ban**, and described a ban wave of over 40,000 accounts.
 
## Publicly reported numbers (judgments / damages / reported earnings)
These are not always “revenue”, but they indicate the scale of the market and legal risk.
 
- **Activision vs EngineOwning (Call of Duty)**
  - Default judgment: **$14,465,000** + attorneys’ fees reported as **$292,912**.
  - Also included injunction and transfer of the `engineowning.to` domain.
  - Sources:
    - https://www.pcgamer.com/gaming-industry/activision-wins-dollar145-million-in-lawsuit-against-call-of-duty-cheat-maker/
    - https://torrentfreak.com/activision-wins-14-5m-judgment-after-engineowning-cheat-makers-bailed-out-240529/
 
- **Blizzard vs Bossland (Honorbuddy, etc.)**
  - Court awarded statutory copyright damages totaling **$8,563,600** + attorneys’ fees **$174,872**.
  - Source:
    - https://torrentfreak.com/blizzard-beats-cheat-maker-wins-85-million-copyright-damages-170403/
 
- **Epic vs Fortnite tournament cheater (individual case)**
  - Reported court-ordered damages: **$175,000** (Epic said it would donate collected money to charity).
  - Source:
    - https://www.gamesindustry.biz/epic-games-successfully-sues-fortnite-cheat-for-175000
 
- **Take-Two (Rockstar) vs GTA V cheat maker (Menyoo/Absolute)**
  - Reported alleged earnings: **at least $100,000** (settlement amount itself undisclosed/confidential).
  - Source:
    - https://torrentfreak.com/gta-vs-take-two-settles-lawsuit-190407/
 
- **Bungie vs AimJunkies / Phoenix Digital (Destiny 2)**
  - Jury award reported as **$63,210**.
  - Article also references an arbitration award reported as **$4 million** related to DMCA circumvention claims (appeal status noted in reporting).
  - Source:
    - https://www.theverge.com/2024/5/25/24164679/bungie-anti-cheating-lawsuit-jury-trial-aimjunkies-copyright-violation-victory
 
Notes:
- “Doanh thu” is rarely disclosed publicly unless leaked in court filings or reporting.
- These figures still show that successful providers can operate at meaningful scale, but legal exposure can be existential.
 
## Dota 2: có bot chưa? có tool không?
### 1) Bot (hợp lệ) vs bot (vi phạm)
- **Hợp lệ**:
  - Dota 2 has official bot matches / practice modes.
  - Community AI/bot projects exist (e.g., Workshop custom bots / scripts) for playing against bots in appropriate modes.
- **Vi phạm**:
  - Using third-party software in real matchmaking to gain advantage, read hidden client data, automate gameplay, or manipulate outcomes.
 
Valve example enforcement:
- Over **40,000** Dota 2 accounts permanently banned after Valve set a “honeypot” for third-party cheating software that read internal client data.
- Valve warning quoted in reporting: if you run an application that reads data from the Dota client while playing, you can be permanently banned.
- Source:
  - https://www.theverge.com/2023/2/23/23611632/valve-dota-ban-cheating-trap-exploit-patch
 
### 2) “Tool” kiếm tiền trong Dota 2 bằng cách nào? (hướng hợp pháp)
If your goal is to build tools and monetize, these are safer, legitimate directions:
- **Coaching / training products**
  - Replay review tools, drafting helpers that use public match data post-game, coaching dashboards.
- **Analytics & scouting**
  - Stats sites, match history analytics, player performance tracking.
  - Monetization: subscriptions, ads, team services.
- **Tournament / broadcast tooling**
  - Observer overlays, production dashboards, highlight extraction (from replays), scheduling.
- **Community tools**
  - Scrims management, team coordination, hero pool tracking.
- **Workshop / custom game ecosystem**
  - Build custom games or bot experiences that run within supported systems.
 
Practical monetization models (legal)
- **Subscription** for premium insights.
- **B2B** to amateur/pro teams (analysis packages).
- **Sponsorship/ads** for public analytics.
- **Services** (coaching, replay packs, pro support).

## 2026: “đi hướng nào ok” để viết tools/bot (hợp pháp) + ý tưởng nhanh
The safest 2026 directions tend to be:
- **Post-game / replay-based analytics** (no live advantage)
- **Coaching & training workflows**
- **Tournament / broadcast / community operations**
- **UGC ecosystems (custom games / creator tools)**
 
The revenue ranges below are rough estimates (gross revenue per month) once you have traction.

### Tech stack 2026 (để làm game tools “đúng luật”, dễ ship)
Guiding rule: **use public data, replays, VODs, and official APIs**. Avoid anything that reads live client internals or automates gameplay.

- **Frontend (web)**
  - Next.js (React) + TypeScript
  - TailwindCSS + shadcn/ui
  - TanStack Query (data fetching), TanStack Table (analytics tables)
  - Charts: ECharts / Recharts
 
- **Backend API**
  - FastAPI (Python) or NestJS (Node)
  - REST for public endpoints; optional GraphQL for complex dashboards
 
- **Data ingestion & jobs**
  - Queue: Redis + BullMQ (Node) or RQ/Celery (Python)
  - Workers for replay parsing, VOD processing, scheduled data pulls
  - Object storage: S3-compatible (Cloudflare R2 / AWS S3)
 
- **Database**
  - Postgres (primary)
  - Optional: ClickHouse (heavy analytics) or DuckDB (batch analytics offline)
 
- **Auth & billing**
  - Auth: Auth.js (NextAuth) or Clerk
  - Billing: Stripe subscriptions
 
- **Observability & ops**
  - Sentry (errors), OpenTelemetry (tracing), structured logs
  - Hosting: Vercel (frontend) + Fly.io/Render (API/workers) or all-in-one on Fly.io
  - CI: GitHub Actions
 
- **ML / CV (nếu làm VOD/highlight)**
  - PyTorch + ONNX Runtime (inference)
  - ffmpeg pipeline for media processing
  - Keep it offline/post-processing, not in-match assistance

### Idea list (prioritize easiest + fastest monetization)
1) **Tournament ops dashboard (bracket, check-in, assets, penalties)**
   - Game: multi-game
   - Model: per-event license + white-label
   - Revenue: ~$1k–100k+/mo (seasonal)
 
2) **Caster/broadcast overlay toolkit (rosters, lower-thirds, stats)**
   - Game: Dota 2, CS2, Valorant
   - Model: subscription or one-time license + support
   - Revenue: ~$500–50k/mo
 
3) **Scrim manager (Discord + web) (schedule, notes, replay links)**
   - Game: multi-game
   - Model: team subscription
   - Revenue: ~$200–20k/mo
 
4) **Patch/meta tracker + paid newsletter**
   - Game: Dota 2, LoL, Valorant
   - Model: $5–10/mo + sponsorship
   - Revenue: ~$500–25k/mo
 
5) **Discord bot: match summaries + reminders (API-based)**
   - Game: Dota 2/CS2/others (depending on available data)
   - Model: freemium + server subscription
   - Revenue: ~$200–10k/mo
 
6) **Dota 2 draft room for teams (private notes + matchup matrix)**
   - Game: Dota 2
   - Model: B2B teams/academies
   - Revenue: ~$500–20k/mo
 
7) **Dota 2 replay coach (post-game)**
   - Game: Dota 2
   - Model: freemium + $5–15/mo; team plan $50–300/mo
   - Revenue: ~$1k–30k/mo
 
8) **CS2 demo analytics (entry/utility/trade efficiency) (post-match)**
   - Game: CS2
   - Model: subscription + coach seats
   - Revenue: ~$2k–50k/mo
 
9) **Valorant VOD tagging + coach report generator**
   - Game: Valorant
   - Model: SaaS subscription; B2B for academies
   - Revenue: ~$1k–40k/mo
 
10) **Apex / Fortnite highlight generator (VOD/replay-based)**
    - Game: Apex, Fortnite
    - Model: creator subscription
    - Revenue: ~$2k–80k/mo
 
11) **Replay pack curation + labeling for academies**
    - Game: Dota 2, CS2
    - Model: subscription or per-pack sale
    - Revenue: ~$500–30k/mo
 
12) **Esports scouting dashboard (team-only)**
    - Game: Dota 2, CS2, Valorant
    - Model: B2B license
    - Revenue: ~$500–50k/mo
 
13) **Coaching marketplace (booking + payments) (take-rate)**
    - Game: multi-game
    - Model: 10–20% take rate + coach SaaS
    - Revenue: ~$1k–200k/mo
 
14) **Steam economy tracker (alerts/portfolio) (policy-dependent)**
    - Game: CS2 items, Steam market
    - Model: premium analytics + affiliate
    - Revenue: ~$1k–100k/mo
 
15) **Personal performance journal + session review (non-invasive)**
    - Game: multi-game
    - Model: mobile/web subscription
    - Revenue: ~$500–20k/mo
 
16) **Custom game / UGC mode with AI bots (in supported modes)**
    - Game: Dota 2 Arcade, Fortnite Creative/UEFN, Roblox
    - Model: creator payouts + cosmetics + sponsors
    - Revenue: ~$0–500k+/mo (hit-driven)
 
17) **QA automation bot for studios (not public matchmaking)**
    - Game: internal (game dev)
    - Model: B2B contract
    - Revenue: ~$3k–100k+/mo
 
## 2026: còn “đất” cho bot farming ARPG không?
If you mean bots that automate gameplay to farm currency/loot/accounts in live servers (Diablo-like ARPGs), there is usually still demand, but it is a **high-risk, high-churn** space.
 
### Why it’s risky (and often not worth building)
- **ToS violations**: automation and RMT/farming typically violate game rules.
- **Ban waves & anti-bot escalation**: detection improves, bot lifetimes shrink.
- **Payment & distribution risk**: chargebacks, platform bans, domain takedowns.
- **Legal exposure**: some publishers actively pursue sellers/providers.
 
### If you want “ARPG automation/tooling” but legal
Consider products that do not automate gameplay and do not provide unfair in-session advantage:
- **Build planner & simulator** (theorycrafting calculator)
- **Loot log + inventory organization helpers** (user-driven, no automation)
- **Post-run analytics** (time-to-clear, death causes, route review)
- **Community economy dashboards** (public price trends if permitted)
- **Coaching content + workflow tools**
 
### Monetization for legal ARPG tools
- Subscription for premium planners/analytics
- One-time pro license
- Sponsorship/ads
- B2B (creator tooling for streamers/communities)

## ARPG Bot Farming Deep-Dive (WoW, PoE) (non-operational)
This section focuses on the *business/economics and risks* around bot farming ecosystems.
It does not cover implementation, evasion, or “how-to”.

### What “bot farming” sells (outputs)
Most bot-farming operations are not selling “the bot”. They sell outcomes:
- **Currency / gold** (RMT)
- **Materials** (crafting, consumables)
- **Service completion** (leveling, reputation, challenges)
- **Accounts** (high-risk; often linked to fraud and bans)

### Demand drivers (why buyers exist)
- **Time vs money tradeoff**: players pay to skip repetitive grind.
- **Seasonality**: league/season launches spike demand for early advantage.
- **Competitive pressure**: group content, market racing, ladder progress.

### Supply chain / lifecycle (high-level)
A typical “farming business” behaves like a pipeline:
1) **Acquisition**: obtain accounts and the ability to run them.
2) **Production**: generate currency/items/services.
3) **Aggregation**: consolidate to “mules” / storage.
4) **Distribution**: deliver to buyers (direct or via resellers).
5) **Loss management**: account bans, chargebacks, payment shutdowns.
6) **Reset**: rebuild inventory of accounts and routes after enforcement.

The fragility comes from two facts:
- The more you scale, the more your behavior becomes statistically visible.
- Enforcement is often *batched* (ban waves), which can wipe inventory overnight.

### How publishers typically detect / disrupt (conceptual)
- **Behavioral signals**: repetitive play patterns, 24/7 uptime, abnormal reaction distribution.
- **Economic graph analysis**: trade networks, mule hubs, laundering patterns.
- **Platform controls**: account trust, trade restrictions, verification, payment scrutiny.

### Why “high-churn” matters financially
Botting economics reduces to:
- **Expected lifetime (days)** of an account before it becomes unusable.
- **Net yield per day** while alive.
- **Replacement cost** (account + time + overhead).
If lifetime drops faster than yield improves, profit collapses.

## Scenario-based revenue estimates (illustrative)
These are *order-of-magnitude* estimates to reason about the business. They vary widely by game, season, enforcement, and your ability to acquire/retain customers.
 
Assumptions used below:
- **Take rate**: gross revenue (before costs).
- **Costs** include: accounts/subscriptions, infrastructure, moderation/CS, fraud/chargebacks, and losses from bans.
- **No evasion assumptions** are provided.

### Scenario A — Solo “small farm” (low scale)
Profile:
- 1–5 running accounts
- Sells currency/services to a tiny network (friends/community)
 
Revenue (gross): ~$100–$1,000/mo
- Upside happens at season launch spikes.
- Downside: single ban wave or a few chargebacks wipe the month.
 
Costs & risks:
- Accounts/subscriptions (MMO) can dominate.
- High personal time cost doing “delivery” and dispute handling.

### Scenario B — Micro-farm (small operation)
Profile:
- 10–50 accounts, basic reseller relationships
- Some process discipline (inventory tracking, delivery windows)
 
Revenue (gross): ~$1,000–$20,000/mo
- Requires consistent demand + low churn.
- Often volatile: feast/famine around enforcement.
 
Cost structure (typical drivers):
- Account/subscription pool (especially for WoW-like MMOs)
- “Loss rate” from bans (inventory turns into write-offs)
- Customer support + fraud overhead (chargebacks, disputes)
 
Reality check:
- Profit margin can swing from positive to negative depending on ban intensity.

### Scenario C — Provider / reseller network (higher scale)
Profile:
- 50–500+ accounts or a network of suppliers
- Dedicated sales channels, support, and resellers
 
Revenue (gross): ~$20,000–$200,000+/mo
- The upper end typically correlates with higher legal and platform risk.
- Scaling increases visibility to enforcement and increases operational complexity.
 
Key risks:
- Payment processors and marketplaces shutting you down.
- Civil litigation exposure depending on jurisdiction and publisher posture.
- Reputation risk (scams, doxxing, harassment between sellers).

## Game-specific notes
### World of Warcraft (WoW)
Why people bot/farm:
- Persistent MMO economy and long-running demand for gold/materials.
- Services (leveling, reputation) are recurring.
 
What makes it risky:
- Subscription/account cost adds fixed overhead.
- High enforcement posture historically; public lawsuits show willingness to pursue large providers.
- Trade graph analysis tends to be effective in persistent economies.

Practical outcome:
- Often profitable only if churn is low and distribution is stable.
- Legal exposure can become the dominating risk at scale.

### Path of Exile (PoE)
Why people bot/farm:
- League resets create intense early demand for currency and crafting materials.
- Player-driven economy and high grind variance.
 
What makes it volatile:
- The best profit window is often early league, when scrutiny is also high.
- Currency prices swing, so unit economics can flip quickly.
 
Practical outcome:
- Many operations behave like “seasonal hit-and-run” rather than stable SaaS.

## Issues around bot-farming businesses (the “problems around it”)
- **ToS & bans**: customers can lose accounts too; refunds/disputes follow.
- **Legal risk**: lawsuits, injunctions, domain seizures (especially for sellers/providers).
- **Payments**: high chargeback risk; processor shutdown; fraud losses.
- **Security risk**: cheat/bot ecosystems frequently distribute malware/stealers; reputational and real harm.
- **Ethics & community harm**: ruins economy, undermines fair play, increases toxicity and scam activity.
- **Operational stress**: 24/7 incident handling, constant resets, adversarial environment.

## If you want “ARPG money” but sustainable: legal product angles
Better long-term product strategies inspired by the same player pain points:
- **Build planners / simulators** with monetized premium features.
- **Crafting workflow tools** (checklists, budgeting, probability calculators).
- **Post-run analytics** (session review, route review, time-to-clear tracking).
- **Community economy dashboards** (where allowed) + alerts + newsletters.
- **Coaching tooling**: VOD/replay review workflows + structured improvement plans.