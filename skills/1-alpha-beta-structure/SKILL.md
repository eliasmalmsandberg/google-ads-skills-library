---
name: alpha-beta-structure
id: 1
description: Harvest proven search terms from a broad/phrase "beta" (discovery) campaign into an exact-match "alpha" (managed) campaign with the alpha terms as exact negatives in beta, so the two tiers get different budgets and bids. For established Search accounts with a rich search-terms report and thin exact coverage. Not for new accounts, not a SKAG rebuild, not for Shopping/PMax.
tags: Structure / Search / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: Further loosening or removal of exact match (AI Max replacing keywords); removal of campaign-level negatives; Google giving exact keywords strict cross-campaign priority.
---
## What this is
Two tiers. Alpha holds exact-match keywords built from search terms that have already converted; beta holds broad (and optionally phrase) keywords whose job is discovery, with every alpha keyword added as an exact negative so the query can only serve from alpha. Geddes calls this the discovery/managed model: converting queries move from the discovery campaign into managed campaigns as exact or phrase and go back into discovery as exact negatives (Geddes/Adalysis, 2020). The point is budget and bid separation, not keyword hygiene — under automated bidding the canon splits match types only for budget or a different bid method (Geddes, 2020).

## Where it comes from
Geddes's discovery/managed model (2020) is the method. Optmyzr's 2,637-account match-type study (Hopkins, 2023) is the evidence that exact still earns a separate tier. Rooijmans's 2026 rebuild shows the harvest-into-exact move with a scale gate. Lolk (2025, Optmyzr Town Hall, not canon) supplies the current promotion threshold; Bacchini and Vallaeys (2025) supply the limits.

## When to use it / when not to
Use when: 90-day search terms show converting queries with no exact keyword of their own; the account spends enough that the alpha campaign alone will clear 30 conversions/30 days (Vallaeys/Walker, 2025); you need exact-intent traffic to take the maximum budget while broad is throttled (Geddes, 2020); the account already runs Smart Bidding but exact and broad are sharing one target and the exact terms are being under-bid — the Optmyzr study found exact beat broad on CPA in 70.79% of accounts and on ROAS in 72.52% (Hopkins/Optmyzr, 2023).

Do not use when: the account is new (nothing to harvest); total conversions are under ~30/30 days, where splitting makes both tiers unstable (Vallaeys/Walker, 2025) — run alpha and beta as ad groups inside one campaign or a portfolio instead (Geddes, 2020); the client measures only blended numbers and will not fund a discovery tier; the goal is literal query control — close variants and loose phrase matching make SKAG-style precision "nearly impossible" (Lolk, 2025, not canon; Bacchini, 2025).

## Inputs
- Search-terms report, 90 days (and 12 months for seasonality), with clicks, cost, conversions, conversion value, CPC per term.
- Current keyword list with match types and campaigns.
- Campaign targets (tCPA/tROAS) and budgets; conversions per campaign per 30 days.
- Negative lists currently applied.

## Method
1. **Qualify the account.** Projected alpha conversions ≥30/30 days (Vallaeys/Walker, 2025). If not, stop at ad-group-level separation (Geddes, 2020) and revisit once 90 days of data exist — the minimum history the Optmyzr study required (Hopkins/Optmyzr, 2024).
2. **Harvest list.** From 90-day search terms, promote a term to alpha when it has ≥1 conversion and its CPC is at or below the 90th–95th percentile of converting-term CPCs (the CPC filter is Rooijmans's outlier screen, 2026); or, with no conversion yet, when it has reached 50–100 clicks/month and the account's CVR implies a conversion is overdue (Lolk's DSA-promotion bar, 2025, not canon — his old bar was 5 clicks; it rose because close variants made small-click terms noisy). Re-run the harvest against the 12-month view before launch so seasonal converters are not missed (Wenner/SEL on keyword harvest, undated — see skill 2).
3. **Build alpha.** One exact keyword per harvested term, grouped into ad groups by landing page and ad relevance — new ad group only when the keyword is not reflected in both ad and landing page (Geddes, 2020). Do not pause the existing keyword that generated the term; "if you remove a keyword, you can't get it back" (Hopkins/Optmyzr, 2023).
4. **Build beta.** Broad match (phrase optional) on the theme keywords. Add every alpha exact keyword as an exact negative in beta (Geddes, 2020). This is mandatory: across campaigns Google prefers the most restrictive match but rotates over time, which is how the same search term ends up served by both campaigns (Geddes, 2020).
5. **Bidding and budget.** Alpha takes the maximum budget; beta's budget is the lever you use to steer the account to target (Geddes, 2020). Alpha on tCPA/tROAS with bid limits via portfolio; beta on tCPA with a tighter target or Max Clicks with a CPC cap while it has fewer than 30 conversions (Rooijmans, 2026; Vallaeys/Walker, 2025). Expect no CPC discount in beta for being broad — the 2023 study killed that assumption (Hopkins/Optmyzr, 2023).
6. **Promotion cadence.** Epiminds operating cadence — no canon source; reason: weekly through the 2–3-week stabilisation window after launch (Hopkins/Optmyzr, 2024), then fortnightly so each pass has enough new clicks to clear the 50–100 click bar (Lolk, 2025, not canon). Apply rule 2 to beta's search terms; add promoted terms to alpha and as exact negatives to beta in the same change set. Terms that pass the upper promotion bar (100 clicks; Lolk, 2025, not canon) with zero conversions get a phrase negative in beta — Epiminds derived rule; reason: a term with more clicks than the promotion bar and no conversion has already had its chance.
7. **Scale gate.** Only raise alpha budgets or loosen bid limits after the tier shows ~30 conversions in a 2-week window; then remove the lower bid limit and cap the upper at 50% of tCPA (Rooijmans, 2026).
8. **Output.** Alpha keyword list with source term, conversions and CPC at promotion; beta negative list (exact) mirroring alpha; budget split; the promotion log.

## What Google will tell you instead, and why we don't
- Google says duplicating a keyword across match types fragments Smart Bidding data and recommends collapsing to broad in one ad group (Google Ads Help, answer 14752782). The 2,637-account study is the reason we keep an exact tier: exact beat broad on CPA in ~71% of accounts and on ROAS in ~73%, with median gaps over 100% (Hopkins/Optmyzr, 2023). The alpha/beta negatives are what stop the "fragmentation" from becoming self-competition.
- Google's UI recommends broad match for its reach and cheaper clicks. Broad only edged impressions (52.89% of accounts) and the CPC discount is gone after the floor rose ~5–10% (Hopkins/Optmyzr, 2023).
- Google's auto-applied recommendations add broad keywords to any campaign, including alpha; turn them off first (Rooijmans, 2026).

## Failure modes
- **Low-volume lead gen** (<30 conv/30 days): both tiers go unstable; use one campaign with alpha/beta ad groups or a portfolio strategy (Vallaeys/Walker, 2025; Geddes, 2020).
- **Accounts where exact is already most of spend**: nothing to harvest; the beta tier becomes a cost centre with no promotion flow.
- **Negative-heavy accounts**: Lolk reports one account where deleting all negatives raised CPC but multiplied revenue ~5.5–6× (Lolk, 2025, not canon) and Vallaeys holds "there's no such thing as a bad keyword, only a bad bid" (2025). If beta's search terms convert fine at their CPC, do not firewall them for tidiness — promote or leave.
- **Close-variant leakage**: alpha exact keywords still serve variants (Bacchini/Lolk, 2025); if the client expects literal control, this structure will disappoint. Budget for ongoing negatives in alpha too.
- **Seasonal retail**: a 90-day harvest misses seasonal winners; use the 12-month view (step 2).
- **Beta budget starvation**: if beta is cut to zero when results dip, the promotion flow stops and alpha stagnates; keep a floor budget as a research line.

## What to measure
- Alpha vs beta: CPA/ROAS, CPC, share of conversions (expect the study pattern — exact better on CPA/ROAS, broad on impressions; Hopkins/Optmyzr, 2023).
- Promotion rate: terms promoted per fortnight; a zero rate across the stabilisation window (2–3 weeks; Hopkins/Optmyzr, 2024) means beta is too narrow or negatives too aggressive.
- Duplicate search terms across alpha and beta (target zero; Geddes, 2020).
- Conversions per campaign per 30 days against the 30 floor (Vallaeys/Walker, 2025).
- Outlier CPCs in beta vs the 90th–95th percentile screen (Rooijmans, 2026).

## Open disagreements in the canon
- **Whether to split at all under Smart Bidding.** Google and Hagakure-style consolidation keep all match types together; Geddes allows the split only for budget/bid method; Optmyzr's study shows exact still outperforms. Epiminds splits when the alpha tier can stand on its own volume, and otherwise splits at ad-group level only.
- **Negatives as routing.** Vallaeys and Lolk (2025) lean "let the bid handle it"; Geddes (2020) requires exact negatives because of cross-campaign rotation. Epiminds uses the negatives — rotation is observed behaviour and the cost of a stray duplicate is paid in the higher-CPC tier.
- **Promotion threshold.** 5 clicks (Lolk's old bar), 50–100 clicks (Lolk, 2025), ≥1 conversion (Rooijmans's practice, 2026). Epiminds uses conversion first, 50–100 clicks second.
