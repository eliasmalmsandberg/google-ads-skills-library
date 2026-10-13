---
name: micro-campaign-consolidation
id: 9
description: Diagnose and fix a low-volume Search account (campaigns under ~25–30 conversions/30 days, stuck in learning) by merging, pooling and capping rather than by "spending more so it can learn". Not for accounts already at 50+ conversions per campaign, and not a Shopping/PMax restructure.
tags: Strategy / Search / Diagnose / New / One-off
last_verified: 2026-10-13
invalidated_by: Bid limits exposed on campaign-level tCPA; Smart Bidding learning changes that stabilise low-volume campaigns; removal of secondary/soft conversion goals.
---
## What this is
Low-volume accounts fail on Smart Bidding for a data reason, and the fix is in three parts: fewer campaigns, pooled bidding with a CPC ceiling, and a scale gate. The thresholds are not Google's 15: in 14,584 accounts, 50+ conversions/30 days is where any strategy becomes predictably successful, going from under 25 to 25–50 does not reliably help, and no account under 25 beat the 50+ group (Hopkins/Optmyzr, 2024). Below that line structure buys stability, not performance, and the skill is written on that distinction.

## Where it comes from
Optmyzr's bidding study (Hopkins, 2024) for the bands; Vallaeys/Walker for the merge rules, the 30-conversion floor and soft-conversion training (Optmyzr Town Hall, 2025); Bacchini for portfolio pooling in lead gen (Optmyzr Town Hall, 2025); Rooijmans for the portfolio-with-CPC-cap repair, the scale gate and the settings that leak small budgets (2026, three posts); Geddes for when a campaign is allowed to exist (Adalysis, 2020).

## When to use it / when not to
Use when: campaigns sit under 25–30 conversions/30 days (Hopkins/Optmyzr, 2024; Vallaeys/Walker, 2025); learning status recurs after every change; CPC has crept up while leads fell with budget still fully spent — Rooijmans's $5–6k/month case went from 20–30 leads to 6 in two weeks after a tCPA cut (Rooijmans, 2026); the account was advised to raise budget "so Smart Bidding can learn" (Rooijmans, 2026).

Do not use when: campaigns already clear 50 conversions/30 days — splitting for different targets is then legitimate (Vallaeys/Walker, 2025); the real problem is tracking (form fills counted instead of SQLs/sales) — fix that first, because "scaling a broken setup… just makes the leak bigger" (Rooijmans, 2026); the campaigns are separated for budget, geo/language or network reasons that cannot be set at ad-group level (Geddes, 2020; Vallaeys/Walker, 2025).

## Inputs
- Conversions, cost, CPA per campaign for the last 30 and 90 days; learning status history.
- Conversion actions: which are primary, what they represent (lead vs SQL vs sale), import lag.
- Search terms with clicks, CPC, conversions for the 10 weeks before the last major change (Rooijmans, 2026).
- Campaign settings: auto-apply recommendations, Search partners, location option, networks (Rooijmans, 2026).
- Targets, budgets, bid strategy type (campaign vs portfolio).

## Method
1. **Stop the leaks before merging.** Disable auto-applied recommendations (they add broad keywords and Display Expansion — "advertise to everyone except your customers"); Search partners off until the campaign is mature; location set to "Presence", not "Presence or interest" (Rooijmans, 2026). Cut budgets to the level you would happily pay for more of the same clicks (Rooijmans, 2026).
2. **Fix the conversion definition.** Primary = the action the business pays for (SQL or sale), not form fills (Rooijmans, 2026). If primary volume is then under 25/30 days, add soft conversions (add-to-cart, engaged visit, product view) with values as *secondary* actions to give the bidder signal, promoting them only while hard conversions lack volume (Vallaeys/Walker, 2025).
3. **Merge by the campaign-existence rule.** A campaign survives only if it needs its own budget, targeting not settable at ad-group level, or performs materially differently; themes become ad groups (Vallaeys/Walker, 2025; Geddes, 2020). Everything else merges into one Search campaign per budget/geo.
4. **Check the band after the merge.** If the merged campaign projects ≥50 conversions/30 days, run campaign-level tCPA/tROAS normally (Hopkins/Optmyzr, 2024). If 25–50, expect stability, not a performance jump (Hopkins/Optmyzr, 2024), and go to step 5. If under 25, go to step 5 and consider manual CPC or Max Clicks with a CPC cap as the starting strategy (Vallaeys/Walker, 2025).
5. **Pool and cap.** Put the surviving campaigns in one tCPA (or tROAS) portfolio strategy so data pools across them (Bacchini, 2025) and set a max CPC limit: take converting search terms (conv ≥1) from the 10 weeks before the problem started, sort by CPC, and set the cap at the 90th–95th percentile (Rooijmans, 2026). Set the target at the CPA the business accepts, not at last month's actual — the lowering from $300 to $220 is what broke the case account (Rooijmans, 2026).
6. **Walk the limits, do not jump.** Raise the lower bid limit every other day for two weeks to win more relevant clicks while junk terms are negated (Rooijmans, 2026). Keep bid changes small and incremental (Vallaeys/Walker, 2025).
7. **Scale gate.** Only when the merged campaign reaches ~20 conversions/month (Rooijmans, 2026) or 30 SQLs in two weeks (Rooijmans, 2026): remove the lower limit, set the upper limit at 50% of tCPA, and then lower tCPA / raise the cap in 10–20% steps (Rooijmans, 2026). Do not raise budget before the gate.
8. **Re-split only at 50+.** Once a theme inside the merged campaign would clear 50 conversions/30 days on its own and needs a different target, give it a campaign (Hopkins/Optmyzr, 2024; Vallaeys/Walker, 2025).
9. **Output**: the surviving campaign list with the rule that justified each; the portfolio with its target and CPC cap and the percentile table behind it; the conversion-action map (primary/secondary); the scale-gate date and numbers.

## What Google will tell you instead, and why we don't
- Google's guidance is 15 conversions in 30 days and "give it budget to learn" (as cited by Vallaeys/Walker, 2025; Rooijmans, 2026). The 14,584-account study shows nothing reliable happens until 50 and nothing at all under 25 (Hopkins/Optmyzr, 2024); the Rooijmans case lost 70% of its leads doing what the recommendation said (Rooijmans, 2026).
- Google's recommendation to set tCPA at the recent actual CPA is what pushed the case account into high-CPC clicks; we set the target at the acceptable CPA and cap CPC instead (Rooijmans, 2026).
- Google's UI defaults (auto-apply, Search partners on, "Presence or interest") are the first things removed in a small account (Rooijmans, 2026).
- Google frames targets and bid caps as helpful; in the study, setting them more often hurt than helped (Hopkins/Optmyzr, 2024). We use the cap only as a repair in the under-30 band and remove it at the gate.

## Failure modes
- **Accounts whose "low volume" is a tracking artefact** (import lag, form-fill-only tracking): merging pools bad data faster (Rooijmans, 2026). Step 2 first.
- **Multi-geo or multi-language accounts**: merging across geos removes targeting you need; Geddes's campaign-existence rule keeps those apart (Geddes, 2020).
- **Accounts that need materially different targets** (e.g. two product lines at 500% vs 300% ROAS): merging forces one target; keep separate and pool only the bidding (Bacchini, 2025).
- **Expecting a performance lift from 12 + 12 = 24**: the study says 25–50 is not reliably better than <25 (Hopkins/Optmyzr, 2024); promise stability, not CPA.
- **Over-tight CPC cap**: a cap below the 90th percentile starves impressions; the percentile rule is deliberate (Rooijmans, 2026).
- **PMax-heavy small accounts**: Lolk's bar is ~30 conversions/month for PMax to work at all (Lolk, 2025, not canon); Rooijmans moved spend from PMax to exact Search in his rebuild (Rooijmans, 2026).

## What to measure
- Conversions/30 days per campaign against the 25/30/50 bands (Hopkins/Optmyzr, 2024; Vallaeys/Walker, 2025).
- CPC distribution of converting terms vs the cap percentile, weekly (Rooijmans, 2026).
- Learning-status re-triggers per month (target: none after the merge).
- Share of spend on Search partners / Display Expansion (target: zero until mature; Rooijmans, 2026).
- Scale-gate metric: SQLs per two weeks (Rooijmans, 2026).

## Open disagreements in the canon
- **Does consolidation under 50 help?** Hopkins's data (2024) says not measurably; Vallaeys/Walker (2025) and Bacchini (2025) still consolidate/pool. Epiminds consolidates for stability and says so to the client.
- **Manual start vs Smart Bidding with caps.** Vallaeys/Walker (2025) often start new low-data campaigns on manual; Rooijmans (2026) keeps tCPA but caps it. Epiminds caps tCPA in a portfolio where there is any conversion history, and starts manual only when there is none.
- **Bid caps.** The study says caps more often hurt (Hopkins/Optmyzr, 2024); Rooijmans uses them as a repair (2026). Epiminds treats the cap as temporary and removes it at the gate.
