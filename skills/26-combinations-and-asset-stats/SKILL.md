---
name: combinations-and-asset-stats
id: 26
description: How to read the RSA combinations view and the asset-level statistics (and the deprecated Low/Good/Best labels) without being misled, and the decision rule for replacing an asset. Not the test loop itself (22) or the pin design (24).
tags: Diagnostic / Search / Diagnose / Established / Monthly
last_verified: 2026-10-13
invalidated_by: Google exposing per-combination clicks and conversions; removal of asset-level statistics; return of a performance-label column as the only asset signal.
---
## What this is
The three RSA reporting surfaces each hide something: the combinations view shows impressions but not the metric Google optimises on; the asset statistics are per-instance, non-summable and reflect whichever combinations the asset happened to serve in; the old Low/Learning/Good/Best labels (deprecated 2025) had the same problem with less data. This skill is the reading guide and the rule for when an asset-level signal is actually actionable.

## Where it comes from
Brad Geddes / Adalysis (2022 testing method; 2022 creation series; 2026 cross-ad-group insight method), Frederick Vallaeys / Optmyzr (2021 label thresholds and replacement rule; 2022 study framing), the July 2025 platform change reported by Search Engine Land (first spotted by Bob Meijer and Miles McNair, PPC Mastery). Current platform behaviour from Google Ads Help and API docs, labelled.

## When to use it / when not to
Use monthly on established accounts when deciding which assets to rewrite or remove, and whenever someone proposes pausing an asset because it is "Low" or has a bad asset-level CPA. Not useful in ad groups below the combination data budget (skill 22 rule 1); there the views show noise and the only valid read is cross-ad-group (rule 6 below).

## Inputs
- Assets report for a date range on or after 5 June 2025 (the only dates with full asset statistics per Google Ads Help), with clicks, conversions, impressions and the "Added by" column.
- Per-ad combinations view (impressions by served combination).
- Per-ad totals and the ad group's combination count (skill 22).
- Labels on test ads if a cross-ad-group pattern test is running.

## Method
1. **Read the combinations view as a serving log, not a leaderboard.** It shows which combinations served and their impressions, nothing else (Geddes/Adalysis, 2022; Google Ads Help describes the per-ad table as totals across combinations). Serving appears to favour CTR (Geddes, 2022, anecdotal; the API docs say the system favours combinations that "perform well together" without naming the metric). The most-served combination is therefore the best-clicking one in Google's model, not the best-converting one. In Geddes' example the most-served RSA converted at under half the rate of its siblings; pausing it added 200+ conversions in 30 days.
2. **To learn what a combination converts at, pin it into its own ad.** Take the top-impression combination, build a second RSA with those headlines pinned, and read that ad's conversions per impression against the unpinned original (Geddes, 2022, strategy 1). This is the only way to attach conversions to a specific combination; the report will not do it.
3. **Treat asset statistics as directional rankings within one ad.** Asset CTR, CPC, CPA and ROAS are indicators because they reflect the combinations the asset served in, metrics are counted per asset instance and do not sum to ad totals, and clicks mix headline clicks with asset-link clicks unless you segment by click type (Google Ads Help, 2025). Use them to rank assets of the same type inside the same ad; never compare an asset's CPA to the ad group's CPA.
4. **Apply the volume gate before acting on any asset signal.** The old labels only appeared after ~5,000 top-of-page impressions in 30 days (Vallaeys/Optmyzr, 2021), and even accounts spending hundreds of thousands a month saw most assets stuck in "Learning" (reader report on Geddes, 2022). The new statistics have no visible gate, so impose one: the ad must clear well over 100 impressions per combination (Geddes, 2022) before a bottom-ranked asset is treated as real.
5. **Replace on these conditions only.**
   - Zero impressions after 2+ weeks: replace (Vallaeys, 2021; Google Ads Help says "several weeks").
   - Bottom-ranked on conversions per impression within its type and ad, after rule 4, and in an ad group above the budget: rewrite the asset with a different message, keep the slot.
   - Bottom-ranked but in a low-volume ad group: do nothing here; feed it to rule 6.
   - Formerly "Low" label on a pinned asset: not actionable — pinned assets serve regardless and the label reflects the slot, not the line (Geddes, 2022: pins block unpinned assets from the position).
6. **For messaging decisions, aggregate across ad groups.** A single-ad-group read finds the best asset for that targeting only (Geddes/Adalysis, 2026). Label the ads, group assets by pattern (price present/absent, CTA type, keyword insertion on/off), compare on conversion or value per impression, segment by campaign type, and keep brand separate (Geddes, 2026). This is where the asset view becomes a messaging instrument instead of a slot report.
7. **Exclude Google-added text from every read.** Assets with "Google AI" in the Added-by column (Google Ads Help, 2025) are not returned with the ad's own assets in the API (Google Ads API docs, 2026); they contaminate both the combinations view and the asset ranking. Report them separately or keep text customisation off in campaigns you test.
8. **Expect impression discrepancies between identical ads.** Two RSAs under identical conditions can get very different impressions (Vallaeys, 2021); in the 2022 study ad groups allowing multiple texts in pinned positions got 3.9× the impressions. An asset with few impressions may be sitting in an under-served ad, not a rejected line — check the ad's share before judging the asset.

## What Google will tell you instead, and why we don't
Google's asset-reporting page says to evaluate at campaign or asset-group level, aim for Excellent Ad Strength by adding assets to the maximum before replacing any, and consider replacing assets with zero impressions "for several weeks". The first point we share; the second we reject because filling to 15/4 multiplies combinations and pushes the ad group further from a readable data budget (Geddes, 2022; 15/4 at 10,000 impressions a month is "47 years" to significance per Geddes, 2026) and because Ad Strength does not predict performance (skill 25). The old UI advice to act on "Low" labels is also rejected: a label or statistic from one ad group cannot separate the line from the combinations it served in (Geddes, 2022, 2026).

## Failure modes
- Low-volume ad groups (a few hundred impressions a month): every view is noise; weekly metrics there are inconsistent (Geddes, 2022). Only rule 6 applies.
- Heavily pinned ads: asset stats for pinned lines describe the slot, not the line; rule 5's label exception applies and comparisons must be between the 2–3 variants pinned to the same slot.
- Accounts running AI Max text customisation: Google-added assets are invisible in the ad's asset list but present in serving (Google Ads API docs, 2026); any asset ranking that doesn't exclude them is wrong.
- Lead-gen with sparse conversions: conversions per impression per asset is dominated by one or two events; use the pinned-combination test (rule 2) over a longer window, or value per impression with a qualified-lead value.
- Dates before 5 June 2025: full asset statistics do not exist (Google Ads Help); any year-on-year asset comparison across that date is invalid.

## What to measure
Impressions per combination per ad (the gate), conversions per impression per asset ranked within type and ad, share of assets with zero impressions at 14 days, the pinned-combination ad's conversions per impression vs its unpinned parent, and cross-ad-group pattern results by campaign type.

## Open disagreements in the canon
- Vallaeys (2021) says replace "Low" assets as a priority action; Geddes (2022, 2026) says an asset-level signal in one ad group is not evidence about the line. Epiminds follows Geddes for messaging decisions and keeps Vallaeys' rule only for the unambiguous case: zero impressions after two weeks.
- Whether the new asset click/conversion columns change this: the SEL report (2025) presents them as the end of guesswork; Google's own page calls them directional. Epiminds sides with Google's caveat and Geddes' reasoning until per-combination conversions exist.
