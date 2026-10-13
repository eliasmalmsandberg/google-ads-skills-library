---
name: n-gram-script
id: 70
description: Run the Brainlabs search-query n-gram script (Rooijmans's maintained v2.2) on a Search account, and Rhodes's free nGram script on PMax categories and product titles, then turn the output into phrase negatives and new ad groups by rule. For accounts with enough query volume that single terms are noisy. Not for manual term-by-term mining (skill 76), not for deciding match types.
tags: Script / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Further privacy-thresholding of the search terms report; removal of search_term_view or campaign_search_term_insight from the Scripts runtime; API-version sunsets breaking the GAQL.
---
## What this is
The Brainlabs script splits every search query into n-grams of a chosen length range, aggregates clicks, impressions, cost, conversions and value per n-gram, and writes CTR, CPC, CVR, CPA, value/cost and a Query Count at ad group, campaign and account level, plus a word-count analysis of query length (Gilbert/Brainlabs, 2015). Rooijmans maintains the working copy: the AWQL shared-negative query broke in the new scripts runtime and was rewritten in GAQL (v2.0, 2022), with a shared-set fix in March 2025 (v2.2) (Rooijmans, 2022–2025). Rhodes's free nGram script does the same for PMax, over search-category labels from `campaign_search_term_insight` and over product titles from `shopping_performance_view` (Rhodes, 2025).

## Where it comes from
Method and settings: Gilbert/Brainlabs (2015). Maintained code and defaults: Rooijmans (2022–2025). The soft-conversion variant: Neefischer via Rooijmans (2023). PMax and keyword-vs-query variants: Rhodes's GitHub (2024–2025). The single-term click bar that the n-gram rule is calibrated against: Rooijmans's negative-suggestions script (2024).

## When to use it / when not to
Use when: the search terms report has hundreds of distinct queries so that single terms rarely reach a decision threshold but shared words do; after a match-type loosening or a new broad-match campaign; on PMax when you need to know which words in search categories and product titles carry the conversions (Rhodes, 2025).

Do not use when: the account has a few dozen queries a month — read the terms directly (skill 76); when conversions are so sparse that no n-gram will clear a conversion threshold and you have not set up a soft conversion to analyse against (Rooijmans, 2023); on PMax categories if you need cost — the resource has no cost metric and high-volume terms may be sampled, so PMax n-grams measure clicks only (Vallaeys, 2024).

## Inputs
- A blank Google Sheet URL (required; the script writes tabs into it) (Gilbert/Brainlabs, 2015).
- Date range: start/end dates; default lookback in Rooijmans's copy is a fixed 2022 range you must change (Rooijmans, 2022).
- `minNGramLength` / `maxNGramLength`: 1–1 for single words, 2–4 for phrases; Rooijmans's default is 1–2 (Gilbert/Brainlabs, 2015; Rooijmans, 2022).
- Campaign name include/exclude filters; `ignorePausedCampaigns` and `ignorePausedAdGroups` true by default (Rooijmans, 2022).
- `checkNegatives` true (skips queries already blocked); set false only if the script times out (Gilbert/Brainlabs, 2015).
- Thresholds: impression threshold 10; query-count, click, cost and conversion thresholds 0 by default (Rooijmans, 2022).
- A soft conversion action (engaged visit) imported into Google Ads if hard conversions are sparse (Rooijmans, 2023).

## Method
1. **Install** Rooijmans's v2.2 copy, not the original SEL code — the original's AWQL shared-negative query throws `InputError` in the current runtime (Rooijmans, 2022). Set the sheet URL, dates, currency symbol.
2. **First pass: single words.** n = 1–1, full account, 90 days, `checkNegatives` true. Read the Account Word Analysis tab sorted by cost descending (Gilbert/Brainlabs, 2015).
3. **Negative rule.** A word or phrase becomes a phrase-match negative when, in the window, its aggregate clicks are at or above the single-term bar Rooijmans uses (60 clicks, cost above 5, conversions below 0.5 over 90 days) (Rooijmans, 2024) and its Query Count is at least 2, so the pattern repeats across queries rather than being one bad term (Query Count as the "focus on common phrases" filter: Gilbert/Brainlabs, 2015). Add at the campaign or shared-list level that matches where the pattern appears (Campaign vs Account tabs).
4. **Build rule.** An n-gram with CVR above the campaign average and at least the campaign's median conversions per ad group becomes a candidate ad group or keyword theme. Brainlabs says only "consider creating new ad groups" for good performers (Gilbert/Brainlabs, 2015); the two thresholds are an Epiminds operating rule — no canon source; reason: a new group must carry enough conversions to be bid on its own under Smart Bidding, and the campaign median is the lowest bar that does not create a sub-scale group. Check the Ad Group tab first — if the words already sit in one ad group with a matching ad, no new group.
5. **Second pass: phrases.** n = 2–4 on the campaigns that produced negatives in step 3; longer phrases are more specific but rarer, so again judge by Query Count (Gilbert/Brainlabs, 2015).
6. **Word-count tab.** If 5+-word queries show CPA far above 1–3-word queries, the longer-tail is where broad match is drifting; tighten there before adding more negatives (the tab exists for exactly this comparison: Gilbert/Brainlabs, 2015).
7. **Sparse conversions.** If few n-grams reach 0.5 conversions, add an engaged-visit soft conversion, re-run with it selected and treat soft-CVR outliers as the negative/build signal; this exposes off-topic close-variant patterns sooner (Rooijmans/Neefischer, 2023).
8. **Timeouts.** Run by campaign-name filter, set `clearSpreadsheet` false and SUMIF the campaign tabs into an account view (Gilbert/Brainlabs, 2015); or set `checkNegatives` false as the last resort.
9. **PMax.** Run Rhodes's free nGram script once per 30-day window — its queries are hard-coded to LAST_30_DAYS (Rhodes, 2025); the monthly cadence is an Epiminds operating rule, no canon source: "sNgrams" (search categories, PMax only, last 30 days) tells you which words Google is matching your campaign to; "tNgrams" (product titles) tells you which title words sell (Rhodes, 2025). Words in sNgrams with clicks and no conversions go through step 3's logic as PMax campaign negatives; title words with high value/cost go into feed titles (Rhodes, 2025).
10. **Keyword vs query.** Rhodes's `keyword_v_search` script (90 days, keyword / SQR / DSA views, plus 4×90-day weekly averages) shows whether the n-grams in queries exist as keywords at all (Rhodes, 2024); phrases converting in SQR and absent from the keyword tab go to the build list.

## What Google will tell you instead, and why we don't
Google's search terms report shows terms, and the Recommendations tab proposes negatives one term at a time; it offers no aggregation by word, so a drift of 300 small queries sharing one junk word never clears any single-term threshold. The n-gram is the practitioner answer to that (Gilbert/Brainlabs, 2015). Google also hides terms under a privacy threshold, so a share of spend is invisible to term-level work and only partly recoverable by n-grams [Google docs, unverified]. Rooijmans's reason for running n-grams on soft conversions is Google's loosening of match types and close variants, which "surface many off-topic patterns" (Rooijmans, 2023) — the n-gram is a hygiene tool for Google's matching, not just a mining tool.

## Failure modes
- **Low-volume accounts**: with thresholds at Rooijmans's defaults (impressions 10, everything else 0) the sheet is noise; raise the click and query-count floors as in step 3 or do not run.
- **Brand-heavy accounts**: the brand word dominates every tab; filter brand campaigns out with `campaignNameDoesNotContain` first (Gilbert/Brainlabs, 2015).
- **Large accounts**: 30-minute runtime; the script's own remedy is campaign filtering and append mode (Gilbert/Brainlabs, 2015).
- **PMax**: no cost, sampled terms, one term in several categories — rows repeat (Rhodes, 2025; Vallaeys, 2024). Never compute CPA from the PMax tabs.
- **Shared sets**: versions before v2.2 miss shared negatives, so `checkNegatives` silently fails to exclude blocked queries (Rooijmans, 2025 fix).
- **Pinned API versions**: scripts copied from older posts pin a sunset `apiVersion` and stop with `MutateError.UNSPECIFIED`; remove the version argument (Rooijmans, FAQ, undated).

## What to measure
- Negatives added per run and the 90-day clicks and cost they would have blocked.
- Share of cost in queries of 5+ words vs 1–3 words, per run (Word Count tab).
- CVR of new ad groups built from n-grams vs campaign average after 30 days.
- For PMax: share of sNgram clicks on words with zero conversions.

## Open disagreements in the canon
Brainlabs set no click or cost floor and left judgment to the operator with Query Count; Rooijmans's single-term script uses 60 clicks / 90 days. Epiminds applies the 60-click bar to the n-gram aggregate with a Query Count ≥2 — stricter than Brainlabs, consistent with Rooijmans — because the cost of a wrong phrase negative under Smart Bidding is lost converting traffic, and aggregates reach the bar faster than single terms anyway. On soft conversions, Rooijmans endorses them for n-gram work; nobody in the canon has published numbers showing how often soft-conversion negatives would have blocked hard conversions, so we run soft-conversion n-grams as a review list, not an auto-negative source.
