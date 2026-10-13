---
name: qs-tracker-script
id: 37
description: Specification for a daily Google Ads Script that snapshots keyword QS and its three components, builds an impression-weighted trend, and alerts on real drops. Use when setting up an account's QS history. Not for deciding what to fix (34–36, 38) or whether QS matters (39).
tags: Script / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Removal of quality_info from the Google Ads API/Scripts reports, a change to the Scripts 30-minute execution limit, or Google shipping native impression-weighted QS trend charts.
---
## What this is
A build spec for a daily QS snapshot script. Google keeps end-of-day keyword history in the "(hist.)" columns since 2017, back to 22 January 2016 [Google docs; SEL/Marvin, 2017], so the script's job is not "history Google doesn't keep". Its job is what Google still does not give you: an impression-weighted aggregate you can chart, the distribution of impressions by QS level, a per-component index, retention for removed keywords, and a drop alert that can tell a reporting bug from a real decline (Vallaeys/Optmyzr, 2017; Vallaeys/Optmyzr, 2015).

## Where it comes from
Brainlabs's Low-QS Keyword Alert script and its threshold/pause warnings (Gilbert/SEL, c.2018). Wesley Parker's daily tracker design — component distribution, impression-weighted QS and 1–3 component index (Parker/SEL, c.2019; Tier 2 for this topic). Optmyzr's tracker method — Search-impression weighting, null = 6, component mapping 2/6/10, ad groups QS < 6 with cost > 0 (Optmyzr help, fetched 2026). Vallaeys's ±0.2 normal-movement band and the 2015 reporting bug (Optmyzr, 2015). Rooijmans's review of a QS dashboard script, recommending a daily run (Rooijmans, 2024).

## When to use it / when not to
Use once per Search account at onboarding, before any QS work, so there is a baseline. Also use when an account reports a sudden CPC rise and you need to rule QS in or out (Optmyzr help, use cases).
Do not use on accounts with no keyword-targeted Search campaigns — QS is keyword-level only [Google docs]. Do not let it pause anything: Brainlabs ships a `PAUSE_KEYWORDS` switch and warns the threshold must not be high; we leave it off (Gilbert/SEL, c.2018).

## Inputs
- A Google Sheet URL (one per account; MCC runs write one tab per account).
- Keyword-level pull of: campaign, ad group, keyword, match type, status, `quality_info.quality_score`, `creative_quality_score` (ad relevance), `post_click_quality_score` (LPE), `search_predicted_ctr` (expected CTR), impressions, clicks, cost, conversions — yesterday, Search network only (Google Ads API, AdGroupCriterion.QualityInfo). Scripts' object model exposes only `getQualityScore()`, so use the report/GAQL path for components [Google docs, Scripts reference].
- Config: `MIN_IMPRESSIONS` (default 0 — keep everything; filter at read time), `ALERT_EMAILS`, `LABEL_LOW_QS` (default false).

## Method
1. **Run daily, before 06:00 account time.** Parker's and Rooijmans's cadence is daily (Parker/SEL, c.2019; Rooijmans, 2024); Google's "(hist.)" values are end-of-day, so yesterday's snapshot is the comparable unit [Google docs].
2. **Pull with the GAQL/report path, not keyword iterators.** The Scripts `Keyword` object has `getQualityScore()` only; components are not on it [Google docs, Scripts reference]. Use `ad_group_criterion.quality_info.*` from the keyword view (Google Ads API reference). Stop the loop at 25 minutes and write what you have; the Scripts limit is 30.
3. **Keep nulls, never filter on a numeric QS.** Since 12 Sep 2016 keywords without enough exact-match data return NULL, and any numeric QS filter silently drops them [Google docs, Ads Developers blog 2016]. Store `QS = ""` and `has_qs = FALSE`. For aggregate maths, Optmyzr substitutes a neutral 6 (Optmyzr help); we store the raw null and apply the 6 only in the weighted calculation, flagged as imputed.
4. **Append, never overwrite.** One row per keyword per day to a `data` tab (Parker/SEL, c.2019). Keywords that disappear from the pull are not deleted — their last row is the only history that survives removal; Google's "(hist.)" column cannot show removed keywords.
5. **Compute the daily aggregates on a `summary` tab:**
   - `wQS` = Σ(QS × Search impressions) / Σ(impressions), all devices, over keywords with impressions > 0 (Optmyzr help: weighted by Google Search impressions on all devices). Also store the simple mean for comparison (Parker/SEL, c.2019).
   - Impression share by QS level 1–10 (Rooijmans, 2024, share of impressions and share of keywords per level).
   - Component index per component: map Below = 1, Average = 2, Above = 3, impression-weighted; 3 means every impression came from above-average keywords (Parker/SEL, c.2019). Optmyzr's 2/6/10 mapping is equivalent on a 10-scale (Optmyzr help); use one, document it.
   - Keyword-count distribution of QS 1–10 with the first-run distribution frozen for comparison (Parker/SEL, c.2019).
6. **Alert rule, account level.** Vallaeys's observed normal movement in account-level QS is about ±0.2; a ~2-point move was a Google reporting bug (Optmyzr, 2015). Therefore: |ΔwQS| day-over-day ≥ 0.5 → email; ≥ 1.0 → email with "verify against Google Ads UI before acting" (0.5 and 1.0 are Epiminds operating thresholds — no canon source; reason: 2.5× and 5× Vallaeys's observed ±0.2 band, chosen to sit well outside normal movement and below the 2-point bug signature). Do not act on day one: in 2015 CPCs were "a mixed bag" across accounts despite a uniform 2-point drop, which is the signature of a reporting change rather than an auction change (Optmyzr, 2015). Wait for three consecutive days below the prior 30-day mean before opening a ticket (the 3-day / 30-day rule is an Epiminds operating threshold — no canon source; reason: long enough to exclude a one-day reporting glitch of the 2015 kind).
7. **Alert rule, ad-group level.** List ad groups with wQS < 6 and cost > 0, sorted by cost descending (Optmyzr help, "Ad groups to be optimized"); this is the work queue for skills 34–36 and the prioritisation Geddes uses (impression-weighted QS × spend) (Adalysis, 2017).
8. **Optional labelling.** Brainlabs's script labels keywords at or below a threshold (Gilbert/SEL, c.2018). If `LABEL_LOW_QS` is on, label keywords with QS ≤ 4 **and** impressions ≥ 100 in the trailing 7 days (both numbers are Epiminds operating thresholds — no canon source; reason: Brainlabs leaves `QS_THRESHOLD` to the user and gives no impression floor; 4 is the bottom of Hopkins's "drifted" band and 100 impressions is the floor the baseline tracker and PPC.io also use), so new keywords are not labelled before they have data — Brainlabs: new keywords need time to earn impressions before the score means anything (Gilbert/SEL, c.2018).
9. **Charts.** Four: wQS vs simple mean over time; impression share by QS level; three component indices over time; keyword-count distribution today vs first run (Parker/SEL, c.2019; Rooijmans, 2024). Vallaeys adds max CPC charted against QS (Optmyzr, 2017); include if bids are manual.

## What Google will tell you instead, and why we don't
Google says QS "is not a key performance indicator and should not be optimised or aggregated with the rest of your data" [Google docs]. We aggregate anyway, for three documented reasons: an unweighted view misleads — a QS 1 keyword with 1 impression beside a QS 10 keyword with 10,000 averages 5.5 but weighs 10 (Adalysis, 2017); you cannot see a reporting bug without a series (Optmyzr, 2015); and the day segment on the "(hist.)" columns is hard to read for patterns and cannot be charted or grouped by label (Vallaeys/Optmyzr, 2017). Google's QS filter also silently excludes nulls [Google docs]; the script keeps them.

## Failure modes
- **Small accounts** (roughly under 100 keywords or a few hundred daily impressions — Epiminds operating threshold, no canon source; reason: at that size one keyword can dominate the weighting): wQS swings on one keyword; use weekly rather than daily reads (Vallaeys/Optmyzr, 2017, on low-impression keywords not justifying attention).
- **Large MCCs**: a keyword-by-day sheet grows past Sheets limits in months; roll keyword rows to weekly after 90 days and keep daily only for the summary tab (PPC.io's script uses a 90-day rolling window for the same reason; not canon, noted for the pattern).
- **Broad-match-heavy accounts**: a broad keyword can carry the QS of an exact keyword in the same ad group [Google docs]; its impressions inflate the weighted score with borrowed quality.
- **Google reporting incidents**: a uniform step change across every account is a reporting change until proven otherwise (Optmyzr, 2015).
- **Scripts that pause on threshold**: Brainlabs warns against a high pause threshold; under Smart Bidding pausing on QS alone removes converting keywords (Gilbert/SEL, c.2018; Levy/Optmyzr, 2026 on not changing solely for QS).
- **Time zone drift**: run after the account day closes or yesterday's impressions are partial and wQS jumps.

## What to measure
- wQS (impression-weighted), daily; 7-day and 30-day means (Optmyzr help; Parker, c.2019).
- Share of impressions at QS ≤ 4 and ≥ 7 (Rooijmans, 2024).
- Component indices (1–3) for Exp. CTR, Ad Relevance, LPE (Parker, c.2019).
- Number and cost of ad groups with wQS < 6 (Optmyzr help).
- Count of null-QS keywords and their share of cost [Google docs, 2016 change].
- Average CPC and impression share plotted beside wQS, to test whether a CPC move has a QS cause (Optmyzr help, use cases).

## Open disagreements in the canon
- **Is a QS series worth maintaining?** Hopkins would rather watch quality, impression share, CTR and conversion rate than the score (Optmyzr PPC Town Hall, 2020); Vallaeys and Tyagi keep it as a gauge (same episode). Epiminds keeps the series because it is cheap and it is the only way to catch reporting incidents (Optmyzr, 2015).
- **Impression-weighted or keyword-weighted?** Parker plots both (c.2019); Optmyzr weights by Search impressions (help). Epiminds reports wQS and keeps the simple mean as a diagnostic only (see skill 38).
- **Null handling.** Optmyzr imputes 6 (help); nothing in the canon argues for excluding nulls from aggregates, but Google's 2016 change makes them common in new accounts. We impute 6 in wQS and report the null share beside it.
