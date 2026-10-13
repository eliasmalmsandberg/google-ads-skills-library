# Dossier — 70 N-gram script

## Sources

1. **Source**: Daniel Gilbert, Brainlabs, Search Engine Land, "AdWords Script: Find Your Best And Worst Search Queries Using N-Grams" — https://searchengineland.com/brainlabs-script-find-best-worst-search-queries-using-n-grams-228379 (fetched) · **Tier** 1 · **Date** undated on page; 2015 (script header per Rooijmans's copy: 2015/2016 edits) · **Claim**: Breaks search queries into n-grams of length minNGramLength..maxNGramLength; aggregates clicks, impressions, cost, conversions, value per n-gram with CTR, CPC, CVR, CPA, value/cost and a Query Count column; outputs at ad group, campaign and account level plus a word-count analysis (query length 1..7+). Settings: start/end date, campaignNameContains / DoesNotContain, ignorePausedCampaigns/AdGroups, checkNegatives (skips queries already blocked; set false if timing out), spreadsheetUrl, clearSpreadsheet. Use: good n-grams → new ad groups; poor n-grams → phrase-match negatives; use Query Count to favour common phrases. Timeouts: run per campaign filter with clearSpreadsheet=false and SUMIF totals. No minimum thresholds set. · **Evidence**: Published script and method; no performance data.

2. **Source**: Nils Rooijmans, "Updated Google Ads Script: Brainlabs' Search Query Mining for N-Gram Analysis" — https://nilsrooijmans.com/updated-google-ads-script-brainlabs-search-query-mining-for-n-gram-analysis/ (fetched) · **Tier** 1 · **Date** pub 2022-08-22, mod 2025-05-27; script v2.2 with 2025-03-15 fix by Arjan Schoorl (shared-set access) · **Claim**: Rewrote the AWQL shared-negative query as GAQL after the new scripts runtime broke it. Defaults: n-gram length 1–2, impression threshold 10, query-count / click / cost / conversion thresholds 0, ignore paused campaigns and ad groups, checkNegatives true, clear spreadsheet true. Output tabs: Campaign/Ad Group/Account Word Analysis (n=1) or n-Gram Analysis (n>1) plus Word Count Analysis. · **Evidence**: Published script.

3. **Source**: Nils Rooijmans (crediting Stefan Neefischer), "n-gram analysis pro tip" — https://nilsrooijmans.com/daily/n-gram-analyses-pro-tip (fetched) · **Tier** 1 · **Date** 2023-09-05 (mod 2023-11-23) · **Claim**: Run the n-gram analysis on a soft/micro conversion (e.g., engaged user past a short time window) rather than only hard conversions; it surfaces off-topic patterns from close variants and broad match faster, and reduces wasted spend sooner; watch how Shopping, DSA and broad match map queries. · **Evidence**: Practitioner agreement, confirmed on own accounts; no numbers.

4. **Source**: Mike Rhodes, GitHub `mikerhodesideas/free` — `ngram` and `keyword_v_search` (cloned 2026-10-13; repo last commit 2025-10-22) · **Tier** 1 · **Date** 2024–2025 · **Claim**: Free nGram script runs n-grams over two PMax sources: search-category labels from `campaign_search_term_insight` (LAST_30_DAYS, PMax only, impressions >0) and product titles from `shopping_performance_view` segmented by `segments.product_title`; outputs "sNgrams" and "tNgrams" tabs. `keyword_v_search` pulls keyword, SQR and DSA search-term views for NUMDAYS=90 and computes n-grams for each, plus weekly averages (4×NUMDAYS). · **Evidence**: Published code.

5. **Source**: Nils Rooijmans, "Negative Keyword Suggestions" script — https://nilsrooijmans.com/google-ads-script-negative-keyword-suggestions/ (fetched) · **Tier** 1 · **Date** 2024-10-21 (mod 2025-05-09) · **Claim**: Thresholds for a wasted-spend term: >60 clicks, >5 cost, <0.5 conversions over LAST_90_DAYS; skips terms already blocked by ad group, campaign or shared negatives. Used here as the practitioner click bar for a single term, which an n-gram aggregates across terms. · **Evidence**: Published script.

## Dissenting view
Brainlabs (2015) and Rooijmans's defaults set no click or cost floor on an n-gram (impression threshold 10 only), on the view that Query Count tells you how common a phrase is and you should judge by eye. Rooijmans's own negative-suggestion script (2024) sets 60 clicks / 90 days before a single term is a negative. The disagreement is whether an n-gram with lots of queries but few clicks each deserves a negative — Brainlabs says yes if the aggregate is bad, Rooijmans's single-term rule implies waiting for volume. Vallaeys (2024, dossier 69) adds that PMax term data is sampled and has no cost, so n-grams on PMax categories measure clicks, not money.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial); from prior knowledge, labelled unverified: [Google docs, unverified] The search terms report hides terms below a privacy threshold (since September 2020), so n-grams are computed over the visible subset; AWQL and the legacy report types were removed from the Scripts runtime (the "new scripts experience" migration completed 2023), which is why the original Brainlabs script broke (Rooijmans, 2022 confirms the symptom). `campaign_search_term_insight` has no cost metric (confirmed in Rhodes's code and Vallaeys 2024).

## Baseline check
Read `google-ads-scripts` (regex-pattern negatives, no n-grams) and `google-ads-search-term-mining` (manual mining). Neither names the Brainlabs script, its settings, the GAQL fix, the soft-conversion variant, or the PMax category/product-title n-gram use. This skill does.

## Judgment calls
- Treated the Brainlabs post as 2015 based on the script header history quoted by Rooijmans; the SEL page itself shows no date.
- Combined the three Rooijmans items into one practitioner position on thresholds; the 60-click bar is borrowed from his single-term script and explicitly labelled as such.
- Row says Search; the skill adds the PMax use because the Rhodes code exists and the row's "Use when" (automated n-gram output for search terms) is the same job.

- Review fix: the step-4 build thresholds (CVR above campaign average, at least the campaign median conversions per ad group) and the monthly cadence for the Rhodes PMax script are labelled Epiminds operating rules; Brainlabs supports only "consider creating new ad groups", Rhodes's code supports only the 30-day window.

## Canon strength: Strong
Brainlabs (method), Rooijmans (maintained script + thresholds), Rhodes (PMax variant) — three Tier 1 with published code.

## Invalidated by
Further privacy-thresholding of the search terms report; removal of `search_term_view` or `campaign_search_term_insight` from the Scripts runtime; API-version sunsets breaking the GAQL in the scripts.
