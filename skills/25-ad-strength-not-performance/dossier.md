# Dossier — 25 Ad Strength doesn't predict performance

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch.

## Sources

- **Source:** Navah Hopkins, Optmyzr — "Ad Strength & Creative Study: Data & Learnings From 1M+ Ads", https://optmyzr.com/blog/google-ad-strength-study · **Tier** 1 · **Date** 2024-09-09 · **Claim:** 22,000+ accounts (90+ days active, $1,500+/month), 1M+ ads. RSAs rated "Average" had the best CPA, CVR and ROAS; CTR showed no meaningful difference across labels; ROAS dropped sharply from Average to Good; Demand Gen "Average" best on everything except ROAS. Most "Poor"/"Average" ads performed well on typical KPIs; "Good"/"Excellent" were mixed. Recommendation: don't build Ad Strength into audits or sales tools; use it only as a filter for creative so weak it may not earn impressions. Sample skews to advanced marketers. · **Evidence:** cross-account study (exact tables in images, not extracted).
- **Source:** Frederick Vallaeys, Optmyzr — "We analyzed ~20,000 Google Ads accounts", https://www.optmyzr.com/blog/google-rsa-performance-study/ · **Tier** 1 · **Date** 2026-04-06 · **Claim:** "Average" ads: best CPA ($12.43), highest CVR (12.65%), most conversions per impression (1.40%). "Excellent": worst CPA ($28.68), lowest CVR (4.97%). "Poor": best ROAS (327.65%). Headline-length vs Ad Strength correlation 0.056. Ad Strength measures asset completeness, not performance; low-rated but well-performing ads may get fewer impressions. Stop optimising for it if KPIs are fine. · **Evidence:** ~20,000-account study.
- **Source:** Optmyzr (Balakrishnan) — 2022 RSA study, https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 · **Claim:** Each Ad Strength step ≈3% click uplift (Google's figure) but no relation to performance; distinguish Ad Strength (pre-serving best-practice score) from asset labels (performance-based). · **Evidence:** 13,671 accounts.
- **Source:** Vallaeys via Nicole Farley, Search Engine Land — "Creating better ads in a world with only RSAs", https://searchengineland.com/creating-better-ads-in-a-world-with-only-rsas-386377 · **Tier** 1 · **Date** 2022-07-11 · **Claim:** Manually typing the exact text Google suggested did not raise Ad Strength, but adding the same text via Google's suggestion link did; Ad Strength mostly helps newer advertisers and does not reflect performance; a "Poor" rating doesn't predict serving. · **Evidence:** reproducible experiment.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** Ad Strength appears tied to how many options and how much control Google has; heavy pinning lowers it; can be misleading when pinning performs well. Commenters: pinning dropped strength with no change in impression share; strength did not improve CTR or ROAS. · **Evidence:** practitioner observation plus reader reports.
- **Source:** Brad Geddes, Adalysis — "How to test RSAs", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** Fully pinned RSAs usually get "Poor" and can get fewer impressions than sibling RSAs in the same ad group — i.e. the rating may influence serving share between ads, not performance. · **Evidence:** account observation.

## Dissenting view
Google (Marvin, SEJ 2024-04-22): advertisers moving RSAs from Poor to Excellent see 12% more conversions on average; Google Ads Help (Aug 2025 internal data) says ~15% more clicks and conversions. The disagreement is about what is being measured: Google's figures are from holdback experiments on the same ad gaining assets (more combinations, more impressions, more total conversions); the practitioner studies compare efficiency (CPA, CVR, ROAS) across ads at each label and find Average best. Both can be true; only one is a reason to chase the label.

## What the platform currently does [Google docs]
- [Google docs] Ginny Marvin, SEJ (2024-04-22): Ad Strength is a diagnostic rating (Poor/Average/Good/Excellent) from regression analyses on headline count, keyword relevance, headline uniqueness, description uniqueness; it is not an auction factor, has no effect on bidding or eligibility, is unrelated to Quality Score and Ad Rank; pinning lowers it; it accounts for automatically created assets if enabled; Google says not to treat it as a KPI.
- [Google docs] Search Engine Land (Adegbola, undated page) quoting Marvin on X: Ad Strength "is not used in Ad Rank" and does not block a keyword from auction.
- [Google docs] About RSAs (answer/7684791): recommends ≥2 RSAs per ad group with Good/Excellent strength; ~15% more clicks and conversions Poor→Excellent (internal data 15–20 Aug 2025).
- [Google docs] Campaign-level asset reporting (answer/9781208): tells advertisers to aim for Excellent by adding assets to the maximum before replacing any.

## Baseline check
Read `google-ads-ad-copy` (uses Low/Good/Best asset ratings as the audit input; does not discuss Ad Strength as a target) and `google-ads-experiments`. Neither contains the cross-account finding that Average outperforms Excellent on CPA/CVR, the 3%-clicks-per-step framing, or the suggestion-link quirk. This skill is the evidence file for refusing the Ad Strength KPI.

## Judgment calls
- Positioned the skill as "what to optimise instead" with a short rule set, since it is a Research-type row; the operator rules are about handling the pressure (client, Google rep, recommendation score) rather than about editing ads.
- Took Google's 12–15% figures at face value as a volume effect and contrasted them with efficiency metrics rather than calling them wrong.

## Canon strength: Strong
Two independent cross-account Optmyzr studies (2024, 2026) plus the 2022 study and Adalysis observations; a reproducible experiment on the suggestion link.

## Invalidated by
Google replacing Ad Strength with a performance-based score, or using it in Ad Rank/eligibility (Google currently states it does not).
