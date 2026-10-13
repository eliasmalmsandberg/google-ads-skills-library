# Dossier — 38 Impression-weighted QS as the account metric

## Sources

1. **Source**: Brad Geddes, Adalysis, "Six ways Adalysis can help you improve quality scores" — https://adalysis.com/blog/six-ways-adalysis-can-help-diagnose-improve-quality-scores/ · **Tier** 1 · **Date** 16 May 2017 · **Claim**: QS is weighted by impressions at account, campaign and ad group level so averages aren't skewed by low-volume keywords; example — a QS 1 keyword with 1 impression and a QS 10 keyword with 10,000 impressions: simple average 5.5, weighted score "quite high" (≈9.999); an algorithm combines impression-weighted QS with spend to rank ad groups by how much help they need; sub-factors are impression-weighted and colour-coded per ad group. · **Evidence**: method with worked example.

2. **Source**: Fred Vallaeys, Optmyzr, "Here's why your Quality Score suddenly plummeted" — https://www.optmyzr.com/blog/why-did-my-quality-score-plummet · **Tier** 1 · **Date** 30 Mar 2015 · **Claim**: account-level QS normally moves ~±0.2; a ~2-point drop was a reporting bug; CPCs a "mixed bag" across accounts despite it; method — rank ad groups by spend × low QS; compare QS distribution start vs end; weight by impressions "to see which QS levels actually receive traffic, since low-QS keywords with few impressions matter less". · **Evidence**: multi-account observation.

3. **Source**: Optmyzr help, "Quality Score Tracker – FAQs" — https://help.optmyzr.com/en/articles/3075127-quality-score-tracker-faqs · **Tier** 1 · **Date** current (fetched 2026-10-13) · **Claim**: account/campaign/ad group QS = weighted average by Google Search impressions on all devices; keyword "—" treated as 6; components mapped 2/6/10; "ad groups to be optimized" = QS < 6 and cost > 0 sorted by cost. · **Evidence**: vendor method.

4. **Source**: Geetanjali Tyagi, Optmyzr, "Have you tried the new Quality Score tracker for AdWords" — https://www.optmyzr.com/blog/have-you-tried-the-new-quality-score-tracker-for-adwords · **Tier** 1 · **Date** undated (AdWords era) · **Claim**: account/campaign/ad group QS use a "weighted impression share"; switching from desktop-only to all-device impressions changed account QS values for mobile-heavy accounts — i.e., the weighting basis materially changes the number. · **Evidence**: vendor observation.

5. **Source**: Fred Vallaeys, Optmyzr, "Five ways Optmyzr tracks Quality Score that AdWords can't" — https://www.optmyzr.com/blog/five-ways-optmyzr-tracks-quality-score-that-adwords-cant · **Tier** 1 · **Date** 16 May 2017 · **Claim**: a keyword with 18 impressions may not justify attention; aggregate at ad group level for more data; ad groups recommended by weighted sort on cost and low QS; the 1–10 score is position-normalised. · **Evidence**: vendor description.

6. **Source**: Wesley Parker (Clicteq), Search Engine Land, daily tracker script — https://searchengineland.com/track-quality-score-daily-with-this-advanced-adwords-script-315545 · **Tier** added-Tier-2 (topic 37/38) · **Date** c.2019 · **Claim**: plots impression-weighted account QS daily alongside keyword-count-weighted average; components as a 1–3 impression-weighted index. · **Evidence**: published script.

7. **Source**: Optmyzr blog (quotes Aaron Levy) — https://www.optmyzr.com/blog/google-ads-quality-score/ · **Tier** 1, vendor caveat · **Date** 2 Mar 2026 · **Claim**: Levy — treat a sustained downward trend across themes as the signal, not a single snapshot; don't change solely for QS at the expense of ROAS; auction-time quality may be fine for the best queries and poor for the worst "which dominate what you can see". · **Evidence**: opinion.

8. **Source**: Navah Hopkins, Search Engine Land — https://searchengineland.com/quality-score-ppc-394513 · **Tier** 1 · **Date** 2023 · **Claim**: QS is a health indicator, not a KPI; 1–2 point drops normal, 5→2 a problem; keywords with data settle 7–9, many drift to 5–6. · **Evidence**: observation.

## Dissenting view
Google: QS "should not be optimised or aggregated with the rest of your data" [Google docs]. Hopkins (SEL 2023; PPC Town Hall 2020) is the in-canon sceptic — a health indicator, not a reported KPI. The disagreement is whether an account-level number is useful at all; the canon's answer (Geddes, Vallaeys, Optmyzr) is yes, but only if impression-weighted and read as a trend.

## What the platform currently does [Google docs]
- [Google docs] answer/6167118 (fetched 2026-10-13): QS is keyword-level 1–10, a diagnostic, not an auction input, "not a key performance indicator and should not be optimised or aggregated". No account-level QS exists in the UI or API; the keyword report offers no weighted column.
- [Google docs] "—" for keywords without enough exact-match data (since Sep 2016); numeric filters exclude nulls (Ads Developers blog, 2016).
- [Google docs] Historical columns with day segmentation since May 2017 (SEL/Marvin, 2017).

## Baseline check
Read `google-ads-quality-score`. The baseline mentions "account-level weighted average QS (weighted by impressions)" as one line in a tracking list, with no formula, no null rule, no noise band, no reporting rule. This skill adds the formula and weighting basis, the null/imputation rule, Vallaeys's ±0.2 noise band and 2-point bug signature, the Optmyzr QS < 6 & cost > 0 work queue, and the explicit decision to report wQS against Google's instruction not to aggregate.

## Judgment calls
- Weighting basis: Optmyzr uses Search impressions on all devices; Geddes's example uses impressions generally. We specify Search-network impressions, all devices, and note Tyagi's observation that the basis changes the number.
- The ±0.2 band is from one Vallaeys observation in 2015, across his accounts; it is the only published noise band and is labelled as such.
- Cost-weighting as an alternative appears in Vallaeys 2015 (spend × low QS for ad groups) — adopted for the work queue, not for the headline metric.

## Canon strength: Strong
Geddes (worked method), Vallaeys (two posts, one with multi-account data), Optmyzr help (formula), Parker (script), Levy, Hopkins.

## Invalidated by
Google publishing a native weighted account-level quality metric, removing keyword-level QS, or changing the null-QS rule.
