# Dossier — 28 Keyword-level ad customizers

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch. Google Ads Help "Ad customizers for RSAs" (answer/10587516) refused to fetch in three variants; platform facts come from the Google Ads API developer page, which was read in full. No canon practitioner page specifically on keyword-level customizer method was reachable; the practitioner evidence is on the effect of DKI/customizers in aggregate.

## Sources

- **Source:** Optmyzr (Ashwin Balakrishnan) — "Optmyzr study: RSA performance", https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 (upd. 2023-04-07) · **Claim:** Across 432,343 ads, dynamic keyword insertion and ad customizers increased impressions per ad but decreased conversions per ad; ETAs with 31+ character headlines (likely DKI/customizers) were treated as outliers. · **Evidence:** 13,671-account study.
- **Source:** Vallaeys via Nicole Farley, Search Engine Land — "Creating better ads in a world with only RSAs", https://searchengineland.com/creating-better-ads-in-a-world-with-only-rsas-386377 · **Tier** 1 · **Date** 2022-07-11 · **Claim:** DKI and ad customizers may raise impressions but likely lower conversion rates; test RSAs against RSAs. · **Evidence:** Optmyzr audit of 1.7M ads.
- **Source:** Brad Geddes, Adalysis — "How to find real insights hiding in your RSA data", https://adalysis.com/blog/how-to-find-real-insights-rsa-data/ · **Tier** 1 · **Date** 2026-09-29 · **Claim:** In a cross-ad-group pattern test, ads without keyword insertion had better CTR and conversion rate than ads with it; prices in headlines (the $-sign pattern) trended worse but the test was unequal and needs a rerun. Method: label-based pattern tests across ad groups judged on conversion value per impression. · **Evidence:** account tests.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** Keyword insertion, countdowns and location insertion are available by typing a brace; relevance should come from written lines tied to the ad group and query. · **Evidence:** method.
- **Source:** Frederick Vallaeys, Optmyzr — "We analyzed ~20,000 accounts", https://www.optmyzr.com/blog/google-rsa-performance-study/ · **Tier** 1 · **Date** 2026-04-06 · **Claim:** Headlines under 20 characters had CPA $9.35 vs $18.27 — relevant because inserted values plus default text count toward the 30-character cap and push customised headlines long. · **Evidence:** ~20,000-account study.

## Dissenting view
Google's editor surfaces keyword insertion and customizers as relevance tools, and Geddes (2022) lists them neutrally as available helpers. The practitioners with data (Optmyzr 2022; Geddes 2026) find they buy impressions at the cost of conversions. The disagreement is whether "relevance" in the headline (matching the query string) is the same as relevance to the searcher; the data says it is not by default.

## What the platform currently does [Google docs]
- [Google docs] Google Ads API, "Customize responsive search ads": CustomizerAttribute has a unique case-insensitive name and type text/number/price/percent; up to 40 enabled attributes per account; linked at customer, campaign, ad group and ad group criterion (keywords only) level; one link per level; the most specific link wins (ad group over campaign; keyword over ad group); syntax `{CUSTOMIZER.<name>:<default>}`; headlines and descriptions only (no URLs); price values take currency code/symbol before or after the number with no space; 30/90 limits include the inserted value and default; if the inserted value is too long or invalid the default is used, but only if the default itself fits; an RSA with customizers lacking fallback values can be rejected (NOT_ENOUGH_AVAILABLE_ASSET_LINKS_WITH_FALLBACK_FOR_VALID_COMBINATION, per the RSA overview page). Keyword insertion `{Keyword:Default text}`.
- [Google docs] Google Ads Help answer/6072565: customizers work for RSAs and text ads; VisURL path customisation not supported for RSA countdowns; ETA customizers could not be created/edited after 2022-06-30 and stopped serving 2024-05-31.
- [Google docs] About RSAs (answer/7684791): a keyword longer than 30 characters should go in a description.

## Baseline check
Read `google-ads-ad-copy` (character-count table notes "dynamic insertion adds chars"; nothing on customizers) and `google-ads-ad-extensions` (nothing). This skill adds the precedence model (keyword > ad group > campaign > account), the fallback failure modes, and the evidence-based rule for when 1:1 copy is worth its conversion cost.

## Judgment calls
- Practitioner canon on the *method* of keyword-level customizers is thin; the canon is adequate on the *effect*. The skill therefore spends its rules on gating (when 1:1 copy earns its cost) and on the test design, and labels the mechanics as Google docs.
- Review fix (rubric 4): replaced the unsourced "≥20 keywords" gate with the sourced data-budget condition plus a labelled Epiminds operating threshold; the "≤12 characters" template cap is now shown as arithmetic (20-character finding minus a 6–8-character price value).
- Chose to treat customized headlines as a hypothesis under skill 22 rule 6 with Geddes' price-pattern test as the template.

## Canon strength: Adequate
Two Tier 1 sources with evidence on the effect (Optmyzr 2022 study; Geddes 2026 tests), one Tier 1 opinion (Vallaeys 2022), mechanics from Google docs.

## Invalidated by
Google changing customizer precedence or the 40-attribute cap, dropping keyword-level customizers, or AI Max text customisation overriding advertiser customizer text.
