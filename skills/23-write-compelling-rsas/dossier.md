# Dossier — 23 Write compelling RSAs

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch of known practitioner URLs. Google Ads Help pages for ad customizers and ad variations could not be fetched.

## Sources

- **Source:** Frederick Vallaeys, Optmyzr — "We analyzed ~20,000 Google Ads accounts" (RSA performance study), https://www.optmyzr.com/blog/google-rsa-performance-study/ · **Tier** 1 · **Date** 2026-04-06 · **Claim:** Headlines under 20 characters: CPA $9.35 vs $18.27 for longer, CTR 11.77% vs 10.52%, CVR 10.39% vs 8.61%, conversions/impression 1.22% vs 0.91%. Correlation between headline length and Ad Strength 0.056. Descriptions 61–70 chars best overall (CTR 12.33%, ROAS 307.58%, CVR 9.21%, CPA $11.49); 0–50 chars lowest CPA ($9.61) but lowest CTR (8.90%); 81–90 chars highest CPC ($1.71) and CPA $20.11. Sentence-case headlines CPA $7.46 vs $27.47 title case (all-accounts cut; common-account cut only 31 accounts, author says too small); description sentence/mixed case ~$17.50 vs title $19.97. "Natural, direct copy outperformed polished, maximised ad-like copy." Test in your own account first. · **Evidence:** ~20,000 accounts; author notes sample skews to experienced practitioners.
- **Source:** Navah Hopkins, Optmyzr — "Ad Strength & Creative Study: Data & Learnings From 1M+ Ads", https://optmyzr.com/blog/google-ad-strength-study · **Tier** 1 · **Date** 2024-09-09 · **Claim:** RSAs performed better in sentence case (ETAs in title case); headlines benefit from concision, descriptions from some length but not max; applying ETA tactics to RSAs declined almost all metrics; quality beats maxing character count; test sentence case only in underperforming ads. Amy Hebdon (Tier 2, quoted): filling every character can keep H3 from serving. · **Evidence:** 22,000+ accounts, 1M+ ads.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** Ads need lines tied to the ad group and the query; without pins, keep roughly equal numbers of ad-group-related headlines, CTAs, and USP/authority lines (about three of each); one- or two-word lines are not distinct; too many unrelated lines with one relevant line weakens the ad. · **Evidence:** method with worked examples; no cross-account numbers.
- **Source:** Adalysis docs — "Ad testing checklist", https://docs.adalysis.com/product/inside-adalysis/ad-testing-checklist · **Tier** 1 · **Date** undated · **Claim:** Balanced mix of relevance headlines, benefits, authority statements, CTAs; "don't just add 15 headlines because Google allows it"; researchers and buyers need different messages. · **Evidence:** method.
- **Source:** Brad Geddes, Adalysis — "How to find real insights hiding in your RSA data", https://adalysis.com/blog/how-to-find-real-insights-rsa-data/ · **Tier** 1 · **Date** 2026-09-29 · **Claim:** In account tests, ads without keyword insertion had better CTR and CVR than ads with it; prices in headlines trended worse (unequal test); "get a quote" beat "affordable" on conversion value per impression for B2B despite lower CVR. · **Evidence:** account tests, some not yet significant.
- **Source:** Optmyzr (Ashwin Balakrishnan) — "Optmyzr study: RSA performance", https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 (upd. 2023-04-07) · **Claim:** Across 432,343 ads, DKI and ad customizers increased impressions per ad but decreased conversions per ad. More headline variants → more impressions per RSA (no figure). · **Evidence:** 13,671-account study.
- **Source:** Frederick Vallaeys, SEJ — "How To A/B Test Responsive Search Ads", https://www.searchenginejournal.com/how-to-test-responsive-search-ads/429270 · **Tier** 1 · **Date** 2021-12-17 · **Claim:** Build up to three RSAs per ad group each around a different value proposition or CTA; more headline variations associated with more conversions per ad (no figure). · **Evidence:** Optmyzr data, 157,000+ ad groups.

## Dissenting view
Optmyzr's own product post (Chatterjee, 2023, vendor content) and Google's RSA page tell you to use both the asset counts and the character limits fully. The practitioners above (Geddes; Hopkins; Vallaeys 2026) disagree: fewer, shorter, distinct lines beat maxed-out ones. The disagreement is whether volume of combinations (impressions) or quality of each combination (conversions per impression) is the objective.

## What the platform currently does [Google docs]
- [Google docs] About RSAs (answer/7684791): 3–15 headlines, 2–4 descriptions; 30/90/15 character limits (double-width characters count as 2); H1, H2 and D1 always shown, H3 and D2 not guaranteed; keyword over 30 chars should go in a description; Google reports ~15% more clicks and conversions from Poor→Excellent Ad Strength (internal data, Aug 2025).
- [Google docs] Google Ads API RSA overview (updated 2026-09-30): the system collects statistics on combinations and favours combinations that perform well together; AI Max text customisation is opt-in for Search and generated assets are not listed with the advertiser's assets; `Campaign.text_guidelines` can set term exclusions and messaging restrictions for generated text.

## Baseline check
Read `google-ads-ad-copy`. It gives headline frameworks by slot category and a 15-headline checklist, with no evidence behind any length, case or mix rule, and it tells you to fill 15/4. This skill adds the measured length and case effects (Vallaeys 2026, Hopkins 2024), the balanced-thirds mix with a cap on line count (Geddes 2022; Adalysis), and the evidence against keyword insertion as a default (Geddes 2026; Optmyzr 2022).

## Judgment calls
- Treated the 2026 sentence-case headline finding as a hypothesis to test (its common-account sample was 31 accounts, which the author calls too small), not a rule; the length findings are stronger and are written as defaults.
- "Compelling" is defined as conversions per impression, per Vallaeys (2021) and Geddes (2026), not CTR.
- Review fix (rubric 4): the opening line count is now derived from Geddes' 100-impressions-per-combination rule; the fallback "9 headlines / 3 descriptions" is labelled an Epiminds operating threshold (3 per third from Geddes' 2022 example; 2–3 per slot from the pinning sources), not a canon figure.
- Google's ~15% Poor→Excellent claim is recorded as a platform claim and contradicted via skill 25.

## Canon strength: Strong
Three Tier 1 practitioners with cross-account studies (Optmyzr 2022, 2024, 2026) and account-level tests (Adalysis 2026), plus Adalysis method docs.

## Invalidated by
A change to the 30/90 limits or to which slots are always shown; Google switching to serve more than three headlines routinely; mandatory AI Max text assets in Search.
