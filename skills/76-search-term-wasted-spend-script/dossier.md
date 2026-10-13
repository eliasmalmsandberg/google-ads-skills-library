# Dossier — 76 Search term wasted-spend script

## Sources

1. **Source**: Nils Rooijmans, "Negative Keyword Suggestions" script — https://nilsrooijmans.com/google-ads-script-negative-keyword-suggestions/ (fetched) · **Tier** 1 · **Date** pub 2024-10-21, mod 2025-05-09 · **Claim**: Weekly (Monday 06:00) list of search terms over PERIOD = LAST_90_DAYS (ending yesterday) with clicks > MIN_CLICKS (60), cost > MIN_COST (5), conversions < MIN_CONVERSIONS (0.5), enabled campaigns and ad groups only, Shopping supported, campaign name include/exclude; skips terms already blocked by ad-group, campaign or active shared negatives using broad/phrase/exact blocking rules; emails a summary with sheet link; suggests only, never adds. Rationale: Google pushes broad match "like a fitness coach demanding 'just one more rep'", match types are "more fuzzy than my memory of high school Greek", matching is imperfect and changes often; manual negative work takes hours weekly. · **Evidence**: Published script with thresholds; opinion on Google.

2. **Source**: Nils Rooijmans, "PMax Non-Converting Search Term Alerts" — https://nilsrooijmans.com/google-ads-script-pmax-non-converting-search-term-alerts/ (fetched) · **Tier** 1 · **Date** 2024-03-06 (mod 2025-05-27), v0.9 · **Claim**: PMax version: LOOKBACK 90 days, MIN_CLICKS 100, CONVERSION_THRESHOLD 0.5, via `campaign_search_term_insight` (categories then terms); weekly; add as negatives; new alerts stack at top of sheet, no auto-clear. · **Evidence**: Published script; fetch flagged a likely de-duplication bug in v0.9.

3. **Source**: Daniel Gilbert/Brainlabs, SEL n-gram script — https://searchengineland.com/brainlabs-script-find-best-worst-search-queries-using-n-grams-228379 (fetched) · **Tier** 1 · **Date** 2015 · **Claim**: Poor-performing n-grams → phrase-match negatives; use Query Count to prefer common phrases; `checkNegatives` skips already-blocked queries. · **Evidence**: Published script.

4. **Source**: Nils Rooijmans / Stefan Neefischer, "n-gram analysis pro tip" — https://nilsrooijmans.com/daily/n-gram-analyses-pro-tip (fetched) · **Tier** 1 · **Date** 2023-09-05 · **Claim**: Judge wasted spend on soft conversions (engaged visit) when hard conversions are sparse; reveals off-topic patterns from close variants and broad match sooner. · **Evidence**: Practitioner agreement.

5. **Source**: Mike Rhodes, GitHub `mikerhodesideas/free` — `keyword_v_search` (cloned 2026-10-13) · **Tier** 1 · **Date** 2024 · **Claim**: Pulls keyword, search-term and DSA search-term views for 90 days plus weekly averages over 4× that window; n-grams per source; purpose is to compare what you bid on with what you got. · **Evidence**: Published code.

6. **Source**: Frederick Vallaeys, SEL, "Automation layering is driving PPC so get onboard in 2020" — https://searchengineland.com/automation-layering-is-driving-ppc-so-get-onboard-in-2020-327123 (fetched) · **Tier** 1 · **Date** 2020-01-03 · **Claim**: Two layers against close-variant drift: a simple alert that flags when Google's matching drifts into poor-fit queries, or a script that detects and adds negatives automatically; the human stays "in charge of the plane". · **Evidence**: Framework; no numbers.

## Dissenting view
Vallaeys (2020) describes a script that adds negatives automatically as the more sophisticated layer; Rooijmans's scripts (2024) deliberately only suggest, because matching "changes often" and a term that is junk under one close-variant regime may be fine under the next. The disagreement is whether zero-conversion terms above a click floor can be auto-negatived. Rooijmans's 60-click bar is also stricter than the baseline's unsourced "impressions >10 and conversions = 0" style regex pauser; the gap is about how much evidence a negative needs under Smart Bidding.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] The search terms report omits terms below a privacy threshold (since September 2020), so a share of spend has no visible term; broad match is the default on new Search campaigns (Cooney/PPC Hero 2024, dossier 78); PMax campaign-level negatives and a UI search terms report with cost arrived during 2025; `search_term_view` is available in the Scripts GAQL runtime; Google's Recommendations tab suggests negatives and offers to auto-apply.

## Baseline check
Read `google-ads-search-term-mining` and `google-ads-scripts` (regex auto-negative script with impressions >10 / conversions = 0 over 7 days, unsourced). This skill replaces the unsourced thresholds with Rooijmans's 60 clicks / cost 5 / <0.5 conversions / 90 days, adds the already-blocked check, the PMax variant at 100 clicks, the soft-conversion fallback and the suggest-vs-auto-apply position.

## Judgment calls
- Position: suggest-only on Search (Rooijmans), with one narrow auto-apply exception for exact-negative of terms that are literally on a client's exclusion list (jobs, free, competitor names) — this exception is ours and is stated as such.
- Cost threshold is in account currency (default 5) and is treated as a floor, not a target; the skill tells the operator to set it to one target CPA.

## Canon strength: Strong
Rooijmans (two scripts with thresholds), Brainlabs (method), Rhodes (code), Vallaeys (framework).

## Invalidated by
Further privacy-thresholding of `search_term_view`; Google applying close variants to negatives; removal of campaign-level PMax negatives; API-version sunsets.
