# Dossier — 35 Improve Ad Relevance

## Sources

1. **Source**: Navah Hopkins, Search Engine Land, "What is quality score and how to use it in PPC" — https://searchengineland.com/quality-score-ppc-394513 · **Tier** 1 · **Date** 2023 (undated page; data table from Feb 2023) · **Claim**: ad relevance is "the easiest lever to control"; it examines how well keywords appear in the ad copy and how closely the triggering keyword matches the query. Ad Strength is a creative-quality score and "does not impact quality score". A separate branded campaign sequesters brand traffic and lends equity to new ad groups (new non-brand campaigns start 6–7 rather than 5 when brand runs alongside). Changing match type doesn't erase QS history; editing a keyword in place removes the original. · **Evidence**: practitioner observation; one account table.

2. **Source**: Brad Geddes, Acquisio webinar write-up — https://www.acquisio.com/blog/?p=6300 · **Tier** 1 · **Date** undated, c.2016 · **Claim**: low ad relevance usually signals poor organisation, ads unrelated to their keywords, or a need for different copy; include "supporting keywords" in copy; use Bing's published CTR heat maps (175+ industries) to pick title/description word combinations. · **Evidence**: Geddes's analysis across $100M+ spend; heat-map claim rests on Microsoft data.

3. **Source**: Brad Geddes, Acquisio SMX West interview — https://www.acquisio.com/blog/?p=11166 · **Tier** 1 · **Date** March 2018 · **Claim**: QS "is about how consumers interact with your ads"; step 1 is account organisation, step 2 is ad testing/creative. · **Evidence**: opinion.

4. **Source**: Brad Geddes, Adalysis, "Six ways Adalysis can help you improve quality scores" — https://adalysis.com/blog/six-ways-adalysis-can-help-diagnose-improve-quality-scores/ · **Tier** 1 · **Date** 16 May 2017 · **Claim**: sub-factors are impression-weighted and colour-coded per ad group so the weak component is visible; ad relevance problems are fixed at ad-group level, prioritised by impression-weighted QS × spend; Adalysis's QS docs say for ad relevance "look at ad group organisation". · **Evidence**: product method, hypothetical example.

5. **Source**: Amy Hebdon, Copyhackers, "How to write an AdWords ad" — https://copyhackers.com/write-adwords-ad/ · **Tier** 2 · **Date** 24 Apr 2018 · **Claim**: match the headline to the searched keyword ("it's what works"); SKAGs only with enough traffic because splitting dilutes data; fix the single component flagged below average rather than everything. · **Evidence**: her own tests, no numbers.

6. **Source**: Optmyzr blog (Ronia; quotes Vallaeys, Levy, Gales, Marvin), "Google Ads Quality Score" — https://www.optmyzr.com/blog/google-ads-quality-score/ · **Tier** 1 with vendor caveat · **Date** 2 Mar 2026 · **Claim**: for ad relevance — tighten message match, refine search-term coverage, test new assets; visible QS "mostly based on past exact match performance" (unsourced); Levy: auction-time quality may be fine for best queries and poor for the worst, "which dominate what you can see". · **Evidence**: opinion.

7. **Source**: Adalysis blog Q&A, Brad Geddes with reader "Mark" (webinar follow-up) — https://adalysis.com/?p=1848 · **Tier** 1 · **Date** undated (AdWords era) · **Claim**: Google keeps QS segmented by device and never surfaces it; Geddes doubts single-word hypotheses about relevance ratings and frames relevance signals as broader "supporting words", like organic search. · **Evidence**: opinion plus one reader's informal keyword review.

## Dissenting view
Hopkins calls ad relevance the easiest lever (keyword in copy, SEL 2023); Geddes says the lever is structure first and copy second (Acquisio 2018; Adalysis 2017). The disagreement is whether a below-average rating is normally a copy defect (fix the RSA) or a grouping defect (move the keyword). Hebdon adds the counter-pressure: splitting groups to fix relevance dilutes CTR data (2018).

## What the platform currently does [Google docs]
- [Google docs] answer/6167118 (fetched 2026-10-13): ad relevance = how closely the ad matches the intent behind a search; rated vs advertisers on the exact same keyword over 90 days; match-type changes don't affect QS; a broad keyword with no impressions can show the QS of an exact keyword in the same ad group; assets are not captured.
- [Google docs] answer/6167130 "5 ways": if ad relevance is below/average — align wording with search terms, split ad groups whose keywords can't be served by one ad, group keywords by theme; moving an ad group with the same ads and keywords to another campaign/account does not change ad quality.
- [Google docs] Null QS for low-activity keywords since the week of 12 Sep 2016 (Ads Developers blog, 15 Aug 2016).

## Baseline check
Read `google-ads-quality-score` and `google-ads-ad-copy`. Baseline: "split the ad group, keyword in 2 headlines, DKI, unpin". This skill adds the Geddes order (structure before copy) with an explicit test to tell which defect you have, the Hebdon volume gate against over-splitting, the Hopkins Ad Strength decoupling, the brand-campaign equity effect, and the match-type/edit-in-place rules from Google docs that practitioners rely on.

## Judgment calls
- No source gives a numeric cut-off for "enough traffic" to split; Epiminds sets 100 clicks/90 days as an operating threshold and labels it as ours.
- Geddes's Bing heat-map recommendation is dated; kept in the dossier, not promoted in the skill.
- Hebdon is Tier 2 on ad copy/relevance per canon.

## Canon strength: Adequate
Hopkins, Geddes (three pages), Optmyzr/Levy, Hebdon — 2+ Tier 1/2 sources, but the evidence is practitioner observation rather than cross-account data.

## Invalidated by
Google merging ad relevance into an RSA/asset-level signal, changing the exact-same-keyword comparison set, or removing keyword-level component reporting.
