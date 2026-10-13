# Dossier — 82 Statistical significance for ad tests

## Sources

1. **Source**: Adalysis (Brad Geddes' firm), "The Ad Testing Guide" — https://adalysis.com/scientific-ad-testing/ · **Tier** 1 · **Date** undated; last modified 2026-07-28 · **Claim**: Minimum data *per ad* before reading (impressions / clicks / conversions): low-traffic 350 / 300 / 7; mid 750 / 500 / 13; high 1,000 / 1,000 / 20; well-known brand terms 100,000 / 10,000 / 100–1,000. Every ad in the test must hit the minimum, not the test combined. Always ≥1 week; 1–3 months is good. Confidence: never below 90%; long-tail 90%, mid-data 90–95%, top keywords 95–99%, own brand 95–99%. Stop rule: 10× minimum data or 3 months without reaching confidence → end the test, move on. Metric: impression-based (CPI = conversions per impression) for most advertisers; CTR for traffic/QS and tie-break; CVR only for landing-page tests with identical ads; CPA and ROAS as filters, not winner metrics. Example: 97 impressions showed 97% confidence — not actionable; ~1,000 impressions per ad gave 99.96%. Rotation: "Do not optimize" for manual bidding or scripts; Optimize is forced with Smart Bidding; ≥5 ads per ad group confuses serving. Testing Google's own serving with 2–3 unpinned RSAs needs hundreds of thousands of impressions per ad group per month. Ad Strength is unrelated to metrics or QS. · **Evidence or opinion**: Method with worked examples; the firm's testing engine implements it.

2. **Source**: Brad Geddes, Adalysis, "How to test responsive search ads (RSA)" — https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 (mod. 2026-07-23) · **Claim**: Five RSA test designs (fully pinned vs unpinned; unpinned vs partially pinned; pinned vs pinned themes, max 3 per ad group; RSA vs ETA; unpinned left to Google — not recommended under a few hundred impressions/month). Combination maths: 5 unpinned headlines → 20 pairs; 15 → 2,940; ×6 with 3 descriptions, ×12 with 4; at a floor of 100 impressions per combination (itself "not enough most of the time"), 15 headlines need >294,000 impressions. Google appears to favour CTR when serving combinations (anecdotal); pausing the worst-converting RSA in one ad group added >200 conversions in 30 days. · **Evidence or opinion**: Method with arithmetic and one account example.

3. **Source**: Brad Geddes, Adalysis, "Why Google Ads 'Optimize' often misses your best ad" — https://adalysis.com/blog/google-ads-optimize-ad-serving-often-fails/ · **Tier** 1 · **Date** 2018-09-18 (mod. 2026-04-28) · **Claim**: Under Optimize, the ad with the best CPI received ~29.9k impressions while a worse ad received ~617.7k (~20×); the highest-CTR ad was shown ~3× as often as the best-converting ad; new ads got 82 impressions in 7 days vs >2,000 for the incumbent. Rule: rotate for serious testing; rotate new ads until they have data; Optimize is applied with any Smart Bidding and cannot be overridden (2019 reply). · **Evidence or opinion**: Single-advertiser examples with numbers.

4. **Source**: Brad Geddes, Adalysis, "Data study: What 5,900 accounts reveal about RSA pinning" — https://adalysis.com/blog/data-study-5900-accounts-rsa-pinning/ · **Tier** 1 · **Date** 2026-10-13 · **Claim**: >5,900 accounts; ads ≥30 days old, ≥250 impressions, ≥1 conversion, non-brand, FUE campaigns excluded. Weighted: CTR falls as pinning rises; CVR differs <2% between 0 and 2 pins; 3 pins has a "vastly superior" CVR. Unweighted (≥250 impr; and ≥100 clicks): CTR flat, CVR and CPI rise with pinning. Pin-3 advertisers are also the most active testers (confound acknowledged). 15 headlines × 4 descriptions = 50,235 combinations; pinning raises data density. "The metric most advertisers should care about is conversions per impression." Recommendation: pin all three headlines if you will analyse and act on tests. · **Evidence or opinion**: Cross-account study, charts not extractable.

5. **Source**: Navah Hopkins, Optmyzr, "Ad Strength & Creative Study: Data & Learnings From 1M+ Ads" — https://www.optmyzr.com/blog/google-ad-strength-study/ · **Tier** 1 · **Date** 2024-09-09 (updated 2026-03-02) · **Claim**: >22k accounts (≥90 days, ≥$1,500/month), >1M ads. RSAs with "Average" Ad Strength had the best CPA, CVR and ROAS; ROAS fell sharply from Average to Good; no meaningful CTR difference by label; "it doesn't make sense to build Ad Strength into audits." Pinning: some pinning best for CPA/ROAS/CPC, none a close second; CVR suffered with pinning in this dataset; full pinning had the highest CTR by a small margin. · **Evidence or opinion**: Cross-account study; tables as images (figures not extractable).

6. **Source**: Google Ads Help, "About ad variations" — https://support.google.com/google-ads/answer/7438541 · **Tier** Reference only · **Date** current · Ad variations test one text change across campaigns/account on RSAs with an end date and traffic %; results show modified vs original; no confidence, minimum-data or significance method documented on the page.

Not found: a PPC Mastery or Brainlabs page on significance specifically (site search unavailable / blocked). Vallaeys' SEL "3 pitfalls" (2019) is cited in dossier 79 and not repeated here.

## Dissenting view
Geddes (2026 study) finds 3-pin RSAs have a markedly higher CVR and recommends pinning all three headlines for testers; Hopkins (2024 study) finds CVR suffered with pinning and advises leaving room for Google to place creative. The disagreement is about whether the pinning effect is causal or a proxy for "advertisers who test" (Geddes concedes the confound). Both agree Ad Strength is not a performance metric.

## What the platform currently does [Google docs]
- Ad variations: RSA-only, one change across many campaigns, traffic % and end date, results reported as modified vs original; no documented significance method [Google docs].
- Ad rotation: Optimize is the only rotation with Smart Bidding (Adalysis guide, consistent with Geddes' 2019 note); "Do not optimize" survives for manual CPC / Maximize Clicks (Adalysis, 2026 — practitioner statement; Google's rotation page could not be fetched).
- Experiment scorecards default to 80% confidence (see dossier 79) [Google docs].

## Baseline check
Read `google-ads-experiments` (sample-size formula, "95% = act") and `google-ads-ad-copy`. This skill adds Adalysis' per-ad minimum-data table by traffic tier, the confidence ladder by keyword type, the 10×/3-month stop rule, CPI as the winner metric with CPA/ROAS as filters, the RSA combination arithmetic that makes unpinned-vs-unpinned tests infeasible below hundreds of thousands of impressions, the evidence that Optimize starves the best-CPI ad, and the two cross-account studies on pinning and Ad Strength.

## Judgment calls
- Treated the undated Adalysis Ad Testing Guide as 2026 (last modified 2026-07-28) and as Geddes' method.
- Took Geddes' 3-pin recommendation over Hopkins' "leave room" on the strength of the stated test-design rationale (data density), while recording the confound.

## Canon strength: Strong
Four Tier 1 Adalysis sources (method + two data studies) and one Tier 1 Optmyzr cross-account study.

## Invalidated by
Google removing "Do not optimize" rotation entirely, changing RSA asset limits (15/4) or pinning rules, exposing a documented significance method in ad variations, or making final URL expansion / AI Max text customisation mandatory (which breaks ad-vs-ad comparability).
