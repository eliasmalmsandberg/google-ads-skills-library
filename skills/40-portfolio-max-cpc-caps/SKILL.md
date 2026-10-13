---
name: portfolio-max-cpc-caps
id: 40
description: Use when a Smart Bidding Search campaign is paying CPCs far above its historical range and you need a ceiling without leaving Smart Bidding. Not for Display/PMax/Demand Gen (caps don't apply there), not a substitute for fixing a wrong target, and not a reflex response to the Aug 2026 budget-limited bidding change.
tags: Technique / Search / Optimise / Established / One-off
last_verified: 2026-10-13
invalidated_by: Google adding bid limits to standard (non-portfolio) strategies, removing them from portfolios, extending them beyond Search auctions, or reversing the 17 Aug 2026 budget-limited bidding change.
---
## What this is
A max CPC bid limit only exists on a *portfolio* bid strategy, not on campaign-level tCPA/tROAS (Google Ads Help, 2026), so practitioners wrap a single campaign in a one-campaign portfolio purely to unlock the ceiling (Bharadwaj/Optmyzr, 2025; Carroll/KlientBoost, 2023). The cap matters in one situation: when ROAS is above target and budget is unspent, tROAS keeps raising max CPC by design (Rooijmans, 2021/2024). Since 17 Aug 2026, budget-limited tCPA/tROAS campaigns are no longer bid-suppressed to ration budget — they bid to the stated target — and median CPCs on budget-limited tROAS campaigns rose 15.8% in the first weeks (Ryan/Smarter Ecommerce, 2026). That is now the most common reason this skill gets pulled.
See also: skill 9 (micro-campaign-consolidation) — the same percentile cap used as part of the low-volume merge-pool-cap repair and its scale gate.
See also: skill 46 (bid-simulator-target-too-aggressive) — diagnosing whether a volume drop is a target problem at all, the gap taxonomy and the IS signature.

## Where it comes from
Hopkins' 14,584-account study (2024) is the only cross-account evidence on caps. Rooijmans (2021/2024; 2026 AMA) gives the mechanism, the single-campaign-portfolio trick and the percentile cap rule; Bharadwaj (2025) portfolio hygiene; Carroll/KlientBoost (2023, added Tier 2) the 25%-over-CPC fallback with five uncontrolled before/afters; Vallaeys (2026) and Ryan (2026) the Aug 2026 change.

## When to use it / when not to
Use when all three hold: (1) a Search campaign on tCPA or tROAS; (2) 14-day average CPC is well above the 90-day median *and* the campaign is at or better than target — spending headroom on expensive clicks, not failing to convert; (3) 50+ conversions in 30 days, Hopkins' floor for predictable Smart Bidding (Hopkins/Optmyzr, 2024).

Not when the campaign is *under* target — that's a target or structure problem and a cap just cuts volume (Carroll/KlientBoost, 2023). Not on Display, PMax or Demand Gen: limits apply to Search auctions only (Google Ads Help, 2026). Not *solely because* of the Aug 2026 change; wait one to two conversion cycles and diagnose first (Vallaeys/Optmyzr, 2026).

## Inputs
- 90-day daily CPC series and 14-day average CPC for the campaign
- Daily budget; actual CPA/ROAS vs target, matured (exclude the conversion-lag window)
- Conversions in last 30 days
- Search top impression share and IS lost to rank/budget, before and after any change
- Whether the campaign is or was "limited by budget" (relevant post-Aug 2026)

## Method
1. **Confirm the symptom is CPC inflation, not target failure.** Condition: 14-day avg CPC ≥ 1.5× the 90-day median AND matured CPA/ROAS is at or better than target. If the campaign is worse than target, stop — go to target diagnosis (skill 46), not a cap.
2. **Check the budget-limited flag.** If the campaign became "limited by budget" after 17 Aug 2026, expect IS lost to budget to have jumped (median went from 4% to 33% in Ryan's data) and CPCs to have risen (Ryan/Smarter Ecommerce, 2026). Do *not* reflexively cut the tCPA to the old actual CPA: in Rooijmans' reader case that took a $5–6K/month account from 20–30 leads to 6 in two weeks at full spend (Rooijmans, 2026). Keep the target at the business-acceptable number, wait 1–2 conversion cycles (Vallaeys/Optmyzr, 2026), and proceed to a cap if CPC inflation persists.
3. **Size the cap from the converting-click distribution, then sanity-check against budget.** Pull 10 weeks of search-term data from before the CPC rise, keep only terms with ≥1 conversion, sort by CPC, and set the cap at the 90th–95th percentile — that removes only the expensive tail that has never converted (Rooijmans, 2026). Then check it against Rule A: ≤10% of daily budget, so the campaign can always afford roughly 10 clicks a day; up to 15% only where click quality is the concern (Hopkins/Optmyzr, 2024). If the percentile cap is above 10–15% of daily budget, the budget is the problem, not the cap. KlientBoost's 25% above average CPC (Carroll, 2023) is a fallback when there's no converting-term history; Bharadwaj's 50–100% above average CPC (Optmyzr, 2025) is the upper bound you relax toward, not a start.
4. **Build the portfolio.** Create a new portfolio with the same strategy type and target the campaign already has, set the max CPC under Advanced options, attach the one campaign. One campaign per portfolio unless the campaigns' targets are within ~15% of each other and their average CPCs are within ~2× — a $30 shared tCPA starves a $50-CPA campaign, and a $3 cap kills a $7-CPC group (Carroll/KlientBoost, 2023). Don't mix objectives in one portfolio (Bharadwaj/Optmyzr, 2025). For Max Conversion Value you must create a *new* portfolio and set a tROAS before the limit field appears (PPC News Feed, 2025).
5. **Hold for 2–3 weeks** — Hopkins' settle window for Smart Bidding changes (Hopkins/Optmyzr, 2024). Do not touch target or budget in that window.
6. **Read the result on three numbers**: avg CPC, search top IS, matured conversions. If top IS fell more than ~10 points and conversions fell while CPC fell, the cap is binding on good auctions — raise it 10–20% (Rooijmans, 2026; Carroll/KlientBoost, 2023). Once conversions are back to the pre-change run rate (~20/month in Rooijmans' case), tighten the target and loosen the cap in alternating 10–20% steps — at that volume the bidder predicts well enough that higher bids can still give lower actual CPA (Rooijmans, 2026).
7. **Expected outcome by strategy.** Caps help tROAS and tIS most, are mixed on tCPA (Hopkins/Optmyzr, 2024). On tCPA, treat a cap as a short-lived diagnostic, not a standing setting; revisit quarterly (Bharadwaj/Optmyzr, 2025).

## What Google will tell you instead, and why we don't
Google's tCPA documentation says setting bid limits "isn't recommended" because it restricts automatic bid optimisation (Google Ads Help, 2026), and after the Aug 2026 change it advised against adding new bid limits for that reason (Vallaeys/Optmyzr, 2026). We disagree on the narrow case: when ROAS is above target with budget unspent, the algorithm is *designed* to raise CPC without limit (Rooijmans, 2021/2024), and Ryan's post-change data shows that budget-limited campaigns now pay 15.8% more per click for the privilege of hitting a target they were already beating (Ryan/Smarter Ecommerce, 2026). A sized cap is the only ceiling Google leaves you. Where we agree with Google: not as a default — Hopkins found cap impact inconsistent and constraints hurting more often than helping (Hopkins/Optmyzr, 2024).

## Failure modes
- **Under-target campaigns.** A cap here lowers auction participation and volume with no efficiency gain (Carroll/KlientBoost, 2023).
- **Low-volume accounts** (<50 conversions/30 days). Smart Bidding is unpredictable below this anyway; a cap adds a second constraint on top of noise (Hopkins/Optmyzr, 2024).
- **Mixed-CPC portfolios** — legal or insurance keyword sets with $5 and $80 CPCs in one campaign: any single cap is wrong for half the traffic (Carroll/KlientBoost, 2023). Split first.
- **Non-Search inventory.** Caps do nothing on Display, PMax, Demand Gen (Google Ads Help, 2026).
- **Volume-first clients.** Caps reduce auction entry; if the brief is growth, the cap works against it (Carroll/KlientBoost, 2023).
- **Existing Max Conversion Value portfolios** — limits only appear on newly created ones (PPC News Feed, 2025).
- **The first fortnight after Aug 17 2026** — forecasts were unreliable in the transition window; a cap set on that data was set on noise (Vallaeys/Optmyzr, 2026).

## What to measure
Avg CPC vs 90-day median; search top IS and IS lost to rank/budget (expect lost-to-rank to rise when a cap binds); matured conversions and CPA/ROAS vs date-matched target, excluding the lag window (Vallaeys/Optmyzr, 2026); share of days where avg CPC equals the cap (a binding-cap signal). Review the cap quarterly (Bharadwaj/Optmyzr, 2025).

## Open disagreements in the canon
- **Standing control vs exception.** KlientBoost runs caps as a standing "hybrid" layer and reports CPC −18% to −34% across five accounts without controls (Carroll, 2023); Hopkins' cross-account data says the effect is inconsistent and strategy-dependent (2024). Epiminds goes with Hopkins: a cap is a diagnosed exception for tROAS/tIS, a short diagnostic on tCPA.
- **Cap sizing.** 25% above CPC (KlientBoost) vs ≤10% of daily budget (Hopkins) vs 50–100% above CPC (Bharadwaj). We take the lower of the first two; evidence beats practice.
- **Timing after Aug 2026.** Vallaeys says wait and diagnose; Ryan's data says CPCs on budget-limited campaigns rose immediately. We wait one cycle, then cap only if the target move did not fix it.
