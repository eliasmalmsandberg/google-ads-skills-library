# Dossier — 31 One vs. two RSAs per ad group under Smart Bidding

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch.

## Sources

- **Source:** Optmyzr (Ashwin Balakrishnan) — "Optmyzr study: RSA performance", https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 (upd. 2023-04-07) · **Claim:** 13,671 accounts. Ad groups with more RSAs got significantly more impressions; two RSAs per ad group produced a conversion-rate lift that one or three did not — "two the apparent sweet spot"; recommend two as a starting point, adjusting per situation. · **Evidence:** cross-account study.
- **Source:** Vallaeys via Nicole Farley, Search Engine Land — "Creating better ads in a world with only RSAs", https://searchengineland.com/creating-better-ads-in-a-world-with-only-rsas-386377 · **Tier** 1 · **Date** 2022-07-11 · **Claim:** Two RSAs per ad group appear ideal for conversion rates; ad groups with RSAs got 1.6× the conversions of those without; RSA CVR ~11% worse than ETA but far more impressions. · **Evidence:** 1.7M-ad audit.
- **Source:** Frederick Vallaeys, SEJ — "How To A/B Test Responsive Search Ads", https://www.searchenginejournal.com/how-to-test-responsive-search-ads/429270 · **Tier** 1 · **Date** 2021-12-17 · **Claim:** Create up to three RSAs per ad group, each around a different value proposition or CTA; include impression data in every test; impression discrepancies occur between RSAs under identical conditions. · **Evidence:** Optmyzr data (157,000+ ad groups).
- **Source:** Brad Geddes, Adalysis — "How to test RSAs", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** Up to three RSAs per ad group for theme tests; Google often gives one RSA most impressions even when it underperforms (example: 10× impressions at under half the CVR; pausing it added 200+ conversions in 30 days); pause losers; unpinned single-RSA serving suits large data only (50,000+ clicks/month example); a few hundred impressions/month gives inconsistent results. · **Evidence:** account examples.
- **Source:** Nils Rooijmans — "Report ad groups that don't have RSAs" script, https://nilsrooijmans.com/google-ads-script-report-ad-groups-that-dont-have-rsas/ · **Tier** 1 · **Date** 2022-08-31 (mod. 2025-05-09) · **Claim:** Script flags enabled ad groups below a minimum RSA count (default 1) and emails when a flagged ad group has over 1,000 impressions in 7 days; rationale: practitioners report ETAs get fewer impressions than RSAs, so every ad group needs an RSA. · **Evidence:** script with thresholds; the impression claim is reported, not measured.
- **Source:** Morten Kristoffersen (SavvyRevenue), Optmyzr blog — "One RSA per ad group", https://www.optmyzr.com/blog/one-rsa-per-ad-group-google-ads-strategy/ · **Tier** not canon (opinion piece; fails inclusion rule c, no evidence) · **Date** 2025-12-15 · **Claim:** One RSA per ad group with ~5 headlines and 2 descriptions; multiple RSAs "steal impressions from each other and confuse the algorithm"; consolidate learning; easier management; refresh assets rather than add ads. · **Evidence:** none stated.

## Dissenting view
Kristoffersen (2025, opinion) argues for one RSA to concentrate data; Optmyzr's 2022 study found two RSAs produced a CVR lift one did not; Google recommends at least two with internal data (+6.6%). Geddes (2022) adds that with two or three, Google often over-serves the worse one. The disagreement is whether a second RSA is a test instrument (Geddes, Vallaeys) or a data-splitting liability (Kristoffersen); the only measured evidence favours two.

## What the platform currently does [Google docs]
- [Google docs] About RSAs (answer/7684791): recommends at least 2 RSAs per ad group, each with Good/Excellent Ad Strength and a unique final URL; internal data (15–20 Aug 2025): ~6.6% more conversions from 1→2 RSAs and ~3.7% from 2→3 at similar cost per conversion.
- [Google docs] Google Ads API RSA overview (2026-09-30): no API limit on RSAs per ad group is stated on the page; practitioners (Geddes 2022; Optmyzr 2023) state a maximum of three RSAs per ad group.
- [Google docs] Campaign-level asset reporting (answer/9781208): asset statistics from 2025-06-05; asset ratios directional.

## Baseline check
Read `google-ads-ad-copy` (does not address RSA count) and `google-ads-experiments` (campaign experiments; no RSA-count rule). This skill adds the 2022 cross-account finding, the over-serving failure mode, the volume gate, and the decision rule for one vs. two vs. three.

## Judgment calls
- Smart Bidding is in the row title; none of the sources segment by bid strategy. The skill says so and treats the over-serving behaviour as the Smart-Bidding-era default rather than claiming a bid-strategy-specific finding.
- Review fix (rubric 4): the "8 weeks" cap was unsourced; the end condition is now the sourced data-budget test, with the time-box left as a launch-time Epiminds operating threshold and labelled as such.
- Google's +6.6% is cited as a platform claim consistent in direction with Optmyzr's finding, not as the reason.

## Canon strength: Strong
Optmyzr 2022 cross-account study plus Vallaeys 2021/2022 and Geddes 2022 account evidence; Rooijmans' script for the floor.

## Invalidated by
Google changing the per-ad-group RSA limit, removing per-ad reporting, or serving a single auto-generated ad per ad group under AI Max.
