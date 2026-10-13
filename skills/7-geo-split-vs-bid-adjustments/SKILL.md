---
name: geo-split-vs-bid-adjustments
id: 7
description: Decide whether a market/region gets its own campaign or stays inside a shared campaign (with or without location bid adjustments), given that Smart Bidding ignores location adjustments. For Search, Shopping and PMax geo settings. Not a geo-performance analysis guide and not for choosing which countries to enter.
tags: Strategy / All / Setup / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google re-enabling location bid adjustments under Smart Bidding; ad-group-level location targeting; per-geo budget allocation inside one campaign.
---
## What this is
Under Target CPA, Target ROAS, Maximize Conversions and Maximize Conversion Value, location bid adjustments are not used at all — Google's own help page says they "won't be supported"; only Maximize Clicks and manual bidding use them (Google Ads Help, answer 2732132, 2026). So on any Smart Bidding campaign the geo choice is binary: a geo is either in the campaign at the bidder's discretion, or it has its own campaign with its own budget, target and message. This skill is the rule for which.

## Where it comes from
Geddes's two models (campaign per location vs one campaign with ad customizers) and his "new campaign for a different geo or budget control" rule (Adalysis, 2020); Vallaeys/Walker's campaign-split conditions, 30-conversion floor and "target explicitly, don't observe" position (Optmyzr Town Hall, 2025); Optmyzr's 50-conversion finding (Hopkins, 2024); Rooijmans's "Presence" setting (2026).

## When to use it / when not to
Use when: a market needs a guaranteed budget share, a different target, a different language/message or landing page, or a different schedule; the account is on Smart Bidding and someone has proposed location bid adjustments (they will do nothing — answer 2732132); the account is on Max Clicks/manual and the question is modifier vs split.

Do not use when: the geo difference is only a CPA gap that the bidder can see — Smart Bidding already weights location; the canon's objection is about budget and message, not about bid weighting (Vallaeys/Walker, 2025); the split campaign would fall under ~30 conversions/30 days (Vallaeys/Walker, 2025) — no account under 25 beat the 50+ group in 14,584 accounts (Hopkins/Optmyzr, 2024).

## Inputs
- Conversions/30 days by location (country/region/city as relevant) for the last 90 days.
- Business constraints per market: budget commitments, language, pricing, landing pages, service hours.
- Bid strategy per campaign (Smart Bidding vs Max Clicks/manual).
- Current location option (Presence vs Presence or interest) per campaign.

## Method
1. **Set the location option first.** "Presence", not "Presence or interest", on every campaign unless the business sells to people who are not in the market (Rooijmans, 2026). This alone removes a class of out-of-market clicks that no split or modifier addresses.
2. **Classify the bid strategy.** If tCPA/tROAS/Max Conversions/Max Conversion Value: location bid adjustments are off the table (answer 2732132). Skip to step 4. If Max Clicks or manual: adjustments work (−90% to +900%, campaign level, most-specific wins; answer 2732132) — go to step 3.
3. **Max Clicks/manual branch.** Use location adjustments for weighting and exclusions for out-of-footprint areas; move to a split only when step 4's conditions apply. Geddes allows geo ad groups inside one campaign where the only difference is the ad (the plumber rebuild used geo ad groups), accepting that some customizer-driven ads will not show properly (Geddes, 2020).
4. **Split test — a geo gets its own campaign only if at least one holds** (Vallaeys/Walker, 2025; Geddes, 2020):
   a. it needs its own budget (a committed share, or protection from a bigger market draining the shared budget);
   b. it needs a campaign-level setting another geo must not have — language, schedule, location exclusions, a different target CPA/ROAS;
   c. it performs materially differently (the brand/non-brand order of difference, not a few percent).
   If none holds, keep it in the shared campaign and let the bidder weight it.
5. **Volume test.** The split campaign must project ≥30 conversions/30 days (Vallaeys/Walker, 2025), with 50 as the level where results become predictable (Hopkins/Optmyzr, 2024). Below 30: keep it in the shared campaign, or split it but put both in a portfolio strategy so the data pools (Bacchini, 2025 — see skill 9).
6. **Tier the budgets.** Top regions in high-budget campaigns, secondary regions in lower-budget ones; use shared budgets across campaigns that should flex together (Geddes, 2020).
7. **Target explicitly.** For the surviving campaigns, target the known high-performing locations and exclude the known poor ones rather than running broad and observing — Vallaeys/Walker's explicit position against Google's "let the algorithm find customers" (2025).
8. **Review every 90 days** (the minimum data history the Optmyzr study required before judging a strategy; Hopkins/Optmyzr, 2024): a geo that has grown past 50 conversions/30 days and needs its own target moves to its own campaign; a split campaign that has fallen under 30 merges back (Hopkins/Optmyzr, 2024; Vallaeys/Walker, 2025).
9. **Output**: a geo table with conversions/30 days, bid strategy, which of 4a–c applies, and the decision (shared / shared+adjustment / split / split+portfolio); the location option set per campaign.

## What Google will tell you instead, and why we don't
- Google's structure guidance: segment campaigns by business objective only; the bidder factors in device and location (Google Ads Help, answer 14752782). The canon's split reasons are budget, campaign-level settings and materially different performance (Vallaeys/Walker, 2025; Geddes, 2020) — the bidder's weighting does not guarantee a market its budget, and a market with its own language or target is a campaign-level fact.
- Google's UI still shows location bid-adjustment columns on Smart Bidding campaigns; its own help says they are not supported (answer 2732132). We never set them there.
- Google defaults to "Presence or interest"; we set "Presence" (Rooijmans, 2026).
- Google's "let the algorithm find customers" vs explicit location targeting and exclusions (Vallaeys/Walker, 2025).

## Failure modes
- **Many small markets** (e.g. one campaign per Nordic country at 5–10 conversions each): every campaign sits in the under-25 band where nothing works predictably (Hopkins/Optmyzr, 2024). Merge by language or pool in a portfolio.
- **Franchise / local-service accounts** that split per city for message reasons: Geddes's customizer model is the cheaper alternative, with the known cost that some customizer ads will not serve (Geddes, 2020).
- **Accounts on Max Clicks that were given adjustments and then moved to tCPA**: the adjustments silently stop working (answer 2732132); re-run step 4.
- **Markets with different conversion values but one currency/target**: without a split or value rules, the bidder optimises to the blended target; condition 4c applies.
- **"Presence" on travel/relocation businesses**: these need "interest" traffic; step 1's exception.

## What to measure
- Conversions/30 days per geo campaign vs the 30/50 bands (Vallaeys/Walker, 2025; Hopkins/Optmyzr, 2024).
- Budget-limited status on the split geo (the reason for 4a).
- Spend share by geo vs the intended share, monthly.
- Out-of-footprint clicks after switching to "Presence" (Rooijmans, 2026).
- On Max Clicks/manual: CPA by location against the adjustment applied (answer 2732132 ranges).

## Open disagreements in the canon
- **How much to trust the bidder's location weighting.** Google and the consolidation school say fully; Vallaeys/Walker (2025) say target and exclude explicitly. Epiminds targets explicitly, because the canon's evidence base for Smart Bidding (Hopkins, 2024) only covers volume, not geo weighting.
- **Campaign per location vs customizers.** Geddes (2020) presents both as valid trade-offs. Epiminds defaults to customizers/ad groups when only the message differs, and campaigns when budget or settings differ.
- **No canon source gives a geo CPA-ratio threshold.** The baseline's 75%/125%/200% tiers are unsourced; Epiminds does not use them for split decisions.
