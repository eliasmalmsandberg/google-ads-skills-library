---
name: rsa-iteration-loop
id: 22
description: The monthly loop for improving RSA copy in live Search ad groups — what to read, which ad groups have enough data to read, what to change and how to judge it. Not for writing a first RSA (see 23) or for deciding pin structure (see 24).
tags: Technique / Search / Optimise / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Removal of asset-level click and conversion reporting; change to the 15/4 asset limits or the always-shown H1/H2/D1 slots; AI Max text customisation becoming mandatory for Search.
---
## What this is
A monthly, impression-budgeted loop for iterating RSA copy. It replaces "pause Low assets, write new ones" — which depended on the Low/Good/Best labels Google deprecated in 2025 — with three rules: decide whether an ad group has enough data to be read at all, judge on conversions per impression rather than CTR, and learn messaging patterns across many ad groups instead of one.
See also: skill 82 (statistical-significance-ad-tests) — the per-ad minimum-data floors, confidence ladder and stop rule for calling an RSA or landing-page test.

## Where it comes from
Brad Geddes / Adalysis (2022 testing method and combinatorial maths; 2026 cross-ad-group pattern method and the Adalysis testing checklist), Frederick Vallaeys / Optmyzr (2021 conversions-per-impression rule and asset-replacement thresholds; 2026 ~20,000-account creative study), Navah Hopkins / Optmyzr (2024 1M-ad study). Platform facts from Google Ads Help and the API docs, labelled.

## When to use it / when not to
Use monthly on every Search campaign with RSAs. Do not use it as an ad-vs-ad test in ad groups with a few hundred impressions a month — Geddes (Adalysis, 2022) shows weekly metrics there are too inconsistent to act on; those ad groups are iterated only through the cross-ad-group pattern step (rule 6). Do not use it on brand campaigns mixed with non-brand; keep them separate (Geddes, 2026).

## Inputs
- Ads & assets → Assets report with clicks and conversions per asset, date range on or after 5 June 2025 (the only dates with full asset statistics per Google Ads Help; the Performance label column is deprecated).
- Per-ad combinations view (impressions only).
- Per ad group: unpinned headline count, unpinned description count, 30-day impressions, conversions.
- A label scheme for test ads (Geddes, 2026 suggests prefixing with "ad-").

## Method
1. **Compute the data budget per ad group.** Combinations = unpinned headlines taken as served triples, times a description factor of ×6 for three unpinned descriptions and ×12 for four (Geddes/Adalysis, 2022). Fifteen unpinned headlines give up to 2,940 combinations; at the 100-impressions-per-combination floor that is 294,000+ impressions before any combination can be read (Geddes, 2022). Divide the ad group's 30-day impressions by its combination count.
   - ≥100 impressions per combination: eligible for single-ad-group reads (rules 3–5).
   - <100: not eligible. Either reduce combinations by pinning 2–3 assets to H1 and H2 (Adalysis checklist) or feed the ad group only into rule 6. Geddes (2026) worked a 10,000-impressions-a-month ad group with 15/4 assets to "47 years" to significance — do not wait for it.
2. **Replace dead assets first.** Any asset with zero impressions after two or more weeks is replaced (Vallaeys/Optmyzr, 2021); Google Ads Help says "several weeks" — use Vallaeys' two. This is hygiene, not a test.
3. **Judge on conversions per impression, never CTR alone.** Google's combination serving appears to favour CTR (Geddes, 2022, anecdotal), so the most-served ad or asset is not the winner by default. Vallaeys (2021) and Geddes (2026) both use conversions (or conversion value) per impression as the tiebreak when CTR and CVR disagree. In Geddes' 2022 example the most-served RSA converted at under half the rate of its siblings and pausing it added 200+ conversions in 30 days.
4. **Pause the losing ad, not the busiest one.** Where an ad group runs two or three RSAs, pause the one with the lowest conversions per impression once rule 1 is met, even if Google is serving it most (Geddes, 2022). Replace it with a new variant that changes one message theme (value prop or CTA), per Vallaeys' "messaging first, positions second" order (2021).
5. **Treat asset-level ratios as directional.** Asset CTR, CPC, CPA and ROAS reflect the combinations an asset served in and are non-summable (Google Ads Help, 2025). Use them to rank assets within the same type and ad, and only act on an asset that is bottom-ranked on conversions per impression and has cleared rule 1.
6. **Run one cross-ad-group pattern test per month.** Following Geddes (Adalysis, 2026): pick the campaigns (brand and non-brand separately), label the ads under test, copy them under a second label, change one thing in one set (a pinning rule, an asset present or absent, a theme such as price vs. quality, keyword insertion on vs. off), use the same number of ad groups per version, and segment results by campaign type. Read on conversion value per impression. Do not conclude from a non-significant or unequal test; rerun it.
7. **Pick next month's hypothesis from the published effect sizes, then test locally.** Candidates with cross-account evidence: headlines under 20 characters (CPA $9.35 vs $18.27, CVR 10.39% vs 8.61%; Vallaeys/Optmyzr, 2026); descriptions of 61–70 characters (best CTR 12.33%, CPA $11.49; Vallaeys, 2026); sentence case in underperforming ads only, never in ads that already perform (Hopkins/Optmyzr, 2024; Vallaeys, 2026, who flags the headline common-account cut at 31 accounts as too small); removing keyword insertion (ads without it won CTR and CVR in Geddes' 2026 example). Each is a hypothesis for rule 6, not a default.
8. **Log and roll forward.** Record the test, the metric, impressions reached and the decision. Winners become the new control for the next cycle; a losing theme is retired account-wide, not just in the tested ad groups.

## What Google will tell you instead, and why we don't
Google's RSA page recommends at least two RSAs per ad group with Good or Excellent Ad Strength, cites ~6.6% more conversions from a second RSA (internal data, Aug 2025), and the asset-reporting page tells you to reach Excellent Ad Strength by filling assets to the maximum before replacing any. We don't fill to 15/4 by default: every unpinned asset multiplies combinations and dilutes the data budget (Geddes, 2022; Adalysis checklist: "don't just add 15 headlines because Google allows it"), and Ad Strength does not predict performance (see skill 25). We also don't take the most-served combination as the winner; it is a CTR artefact until tested on conversions per impression (Geddes, 2022).

## Failure modes
- Low-volume ad groups (a few hundred impressions a month): single-ad-group reads are noise (Geddes, 2022). Only rule 6 applies.
- Lead-gen with sparse conversions: conversions per impression is dominated by a handful of events; use conversion value per impression with a qualified-lead value, or extend the window before judging.
- Brand campaigns: Geddes (2026) keeps single-ad-group testing for brand and very-high-volume ad groups only; cross-ad-group patterns pulled from brand pollute non-brand conclusions.
- Accounts with AI Max text customisation on: automatically created assets are not listed with the ad's own assets (Google Ads API docs, 2026), so a labelled test is no longer a clean comparison. Turn it off in test campaigns or exclude them.
- Applying ETA habits (max length, title case everywhere) to RSAs: Hopkins (2024) found this declined almost every metric.

## What to measure
Per ad group: impressions per combination (rule 1 eligibility), conversions per impression per ad and per asset, assets with zero impressions after 14 days. Per pattern test: conversion value per impression by version, segmented by campaign type, with impressions reached. Account level: share of ad groups eligible for single-ad-group reads, and the monthly log of retired themes.

## Open disagreements in the canon
- Unit of iteration: Geddes and Vallaeys iterate ad-vs-ad under labels and across ad groups; Kristoffersen (SavvyRevenue on Optmyzr, 2025, opinion) iterates assets inside a single RSA. Epiminds follows Geddes/Vallaeys because the single-RSA approach cannot attribute a change to anything but the asset's own directional ratios.
- How much to pin for data density: Adalysis says partially pin H1 and H2 by default; Vallaeys (2021) says unpinned gives the best CTR/CPC/CPA. Epiminds pins to meet the rule-1 budget and leaves high-volume ad groups unpinned (see skill 24).
