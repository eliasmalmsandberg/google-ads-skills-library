---
name: competitor-conquesting
id: 15
description: Whether and how to bid on competitor brand terms — default exclusion from generic campaigns, the conditions for a deliberate conquesting test, and the bidding controls and kill rule for it. Use when a client asks to bid on competitors or when competitor terms are leaking into generic campaigns. Not a brand-defence playbook and not ad-copy guidance beyond the policy-safe rules.
tags: Strategy / Search / Scale / Established / As needed
last_verified: 2026-10-13
invalidated_by: Changes to Google's brand list / brand exclusion features; trademark policy changes on competitor names in ads; removal of bid caps or CPC floors from portfolio strategies; AI Max removing keyword-level control over competitor terms.
---
## What this is
Two decisions. First, competitor intent is excluded from every generic campaign by default, with phrase negatives in a shared list updated from search terms, because competitor clicks show deceptively low CPCs and convert worse, and because they distort the generic campaign's data (Hopkins/SEJ, 2025; Hopkins/SEJ, 2019). Second, conquesting is a deliberate, isolated test with its own budget, goal and kill rule — not a bolt-on ad group. The canon is honest about what it lacks: no Tier 1 source has published account data on conquesting CPA versus generic CPA; the "converts worse" claim is practitioner assertion (Hopkins/SEJ, 2025). The method therefore treats conquesting as an experiment that must prove itself.

## Where it comes from
Navah Hopkins' competitor-term and bid-cap columns (SEJ, 2025, 2022, 2019) and her PMax brand-exclusion note (Optmyzr, 2026); Brad Geddes' Auction Insights method for reading rivals (Adalysis, 2019) and his brand-defence numbers (Adalysis, 2024).

## When to use it / when not to
Use when competitor names appear in generic search terms (exclusion side), and when a client wants to conquest and can isolate budget (test side). Do not conquest from a generic campaign or shared budget (Hopkins/SEJ, 2025). Do not conquest at all when the account lacks conversion values or cannot set a separate ROAS/CPA target for the campaign, because the only controls that keep automation from buying cheap non-converting competitor clicks are values, floors and caps (Hopkins/SEJ, 2025). Do not conquest when the brand's own defence is leaking — fix brand first (Geddes/Adalysis, 2024: brand ran 53% CTR, > 40% CVR, $0.23 CPA while misspellings leaked to PMax).

## Inputs
- Search terms, 90 days, containing competitor names (all campaigns including PMax).
- Auction Insights by campaign over 6–12 months: impression share, overlap rate, position above rate, top-of-page rate (Geddes/Adalysis, 2019).
- Conversion values by action; primary/secondary setup.
- Bid strategy type and whether bid caps / CPC floors are available (portfolio).
- A list of actual competitors (same offering) vs impression competitors (same SERP, different offering) (Geddes/Adalysis, 2019).

## Method
1. **Exclusion default.** Add each competitor name as a phrase negative to a shared "competitor" list applied to all generic campaigns; use exact negatives where a competitor name resembles a valuable generic phrase so only the brand intent is blocked (Hopkins/SEJ, 2025). Add plural/possessive forms manually (Google docs, 2026). Update the list from search terms monthly, including misspellings and new variants (Hopkins/SEJ, 2025). In PMax, use Brand Exclusions for competitor brands, and keep negatives too because close variants can slip past exclusions (Hopkins/Optmyzr, 2026; Hopkins/SEJ, 2025).
2. **Exclusion exception.** Do not block a competitor query family that converts consistently at or near target in a generic campaign; Hopkins' own trade-off is that blocking forfeits comparison shoppers, so exclusion is for consistently underperforming queries (SEJ, 2025). Move converting families into the conquest campaign (step 4) instead.
3. **Choose targets with Auction Insights.** Only "actual competitors" are candidates (Geddes/Adalysis, 2019). Prefer rivals whose coverage trends show budget rhythm — monthly-budget rivals thin out near month end, quarterly-budget rivals fade late in the quarter — and schedule conquest spend into those windows (Geddes/Adalysis, 2019). Limit to a few key rivals (Hopkins/SEJ, 2025).
4. **Build the conquest campaign.** Own campaign, own budget, own goal; one ad group per competitor; competitor names kept out of ad copy; no dynamic keyword insertion (Hopkins/SEJ, 2025). Exact and phrase keywords for the competitor brand and "alternative/vs" forms; the conquest list from step 1 does not apply here.
5. **Bidding controls** (Hopkins/SEJ, 2025, 2022):
   - Give conquest conversions lower values than generic ones, or make low-intent actions secondary, so automation does not chase cheap clicks.
   - Performance goal: tROAS with a high threshold, or tCPA with a bid cap and a CPC floor on a portfolio. Awareness goal: no ROAS target, but a bid cap of at most 10% of daily budget so volume survives (Hopkins/SEJ, 2022).
   - Isolate from brand and generic budgets so a conquest overspend cannot starve them (Hopkins/SEJ, 2019).
6. **Kill rule.** Review at 30 days and at the campaign's first 50 conversions, whichever comes first. If conquest CPA/ROAS is outside the account's generic target by more than the tolerance the client set in advance (Epiminds default: worse than the generic campaign's CPA after segmenting by device, location and audience; Hopkins/SEJ, 2025), pause the campaign and return the terms to the exclusion list. No published evidence says conquesting pays; the test is the evidence.
7. **Ongoing.** Monthly search-term audit for new competitor variants and misspellings (Hopkins/SEJ, 2025); quarterly Auction Insights refresh for new rivals and coverage shifts (Geddes/Adalysis, 2019).

## What Google will tell you instead, and why we don't
Google's AI-driven formats offer Brand Exclusions as the way to keep competitor brands out and present brand lists as sufficient control (Hopkins/SEJ, 2025 describing Google's guidance). Hopkins notes close variants can still get through exclusions, that brand controls require conversion thresholds many accounts don't meet, and that conventional negatives therefore remain necessary (SEJ, 2025). Google's keyword recommendations will also surface competitor terms as "new keywords" for generic campaigns; we route them through step 1 or step 4, never into a generic ad group.

## Failure modes
- **No conversion values / no bid caps.** Automation buys cheap competitor clicks that don't convert and the campaign looks efficient on CPC (Hopkins/SEJ, 2025).
- **Shared budgets.** Conquest spend starves brand and generic (Hopkins/SEJ, 2019).
- **Ad copy with competitor names or DKI.** Policy risk and low relevance (Hopkins/SEJ, 2025).
- **Small accounts.** The conquest campaign will not reach the conversion count needed to judge it or to run Smart Bidding; run it on manual CPC with a hard cap or not at all.
- **Markets where comparison is the buying behaviour** (B2B software, insurance): default exclusion may forfeit the best buyers; Hopkins' exception in step 2 applies and the test in step 4 should run earlier.
- **Impression competitors mistaken for actual competitors.** Conquesting a brand that sells something else buys irrelevant clicks (Geddes/Adalysis, 2019).
- **Evidence gap.** The canon contains no published conquesting results; any expectation of ROI is unsupported until the account's own test reports.

## What to measure
- Competitor-term spend inside generic campaigns (target: zero after step 1).
- Conquest campaign CPA/ROAS vs generic campaign CPA/ROAS, segmented by device, location, audience (Hopkins/SEJ, 2025).
- Conquest CPC vs generic CPC (a low CPC with poor CVR is the warning sign; Hopkins/SEJ, 2025).
- Rival impression share and overlap rate over time, per campaign (Geddes/Adalysis, 2019).
- New competitor variants found per monthly audit.

## Open disagreements in the canon
- **Default exclude vs default test.** Hopkins (2025) excludes by default and acknowledges the forfeited comparison shoppers; no canon source argues for conquesting by default. Epiminds: exclude by default, test only in isolation with the kill rule, and state to the client that the canon has no published returns for conquesting.
- **Brand exclusions vs negatives.** Google positions brand controls as the tool; Hopkins (2025, 2026) uses both. Epiminds uses both.
