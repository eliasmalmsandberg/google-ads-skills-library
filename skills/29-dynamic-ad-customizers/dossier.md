# Dossier — 29 Dynamic ad customizers (countdown, location, business data)

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch. Google Ads Help pages for ad customizers (answer/10587516) and location insertion (answer/9896226) refused to fetch; countdown help (answer/6072565) and the Google Ads API customizer page were read. No canon practitioner page devoted to countdown or location insertion method was reachable; practitioner evidence is on the effect of customised text and location mentions.

## Sources

- **Source:** Brad Geddes, Adalysis — "How to find real insights hiding in your RSA data", https://adalysis.com/blog/how-to-find-real-insights-rsa-data/ · **Tier** 1 · **Date** 2026-09-29 · **Claim:** In a cross-ad-group pattern test, ads *without* store-location mentions performed better than ads with them (test flagged unequal, needs rerun); ads without keyword insertion beat ads with it on CTR and CVR; method is label-based pattern testing judged on conversion value per impression; rerun unequal tests. · **Evidence:** account tests.
- **Source:** Brad Geddes, Adalysis — "How to test RSAs", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** Headline 1 suits location tests, Headline 2 suits price-vs-discount tests; use 1–3 pinned assets per position in up to three RSAs per ad group for theme tests. · **Evidence:** method with examples.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** Countdowns and location insertion are inserted by typing a brace; the example message test is "discount vs free shipping vs price" with the structure held constant. · **Evidence:** method.
- **Source:** Optmyzr (Balakrishnan) — 2022 RSA study, https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 · **Claim:** DKI and ad customizers raised impressions per ad and lowered conversions per ad across 432,343 ads. · **Evidence:** cross-account study.
- **Source:** Navah Hopkins, Optmyzr — "Ad Strength & Creative Study", https://optmyzr.com/blog/google-ad-strength-study · **Tier** 1 · **Date** 2024-09-09 · **Claim:** Headlines benefit from concision; quality beats maxing character count. (Countdown and location strings are long.) · **Evidence:** 1M+ ads.

## Dissenting view
Google's editor and docs present countdowns and location insertion as engagement features; Geddes (2022) lists them as available and suggests H1 for location tests. Geddes' own 2026 account test found location mentions performed worse. The disagreement is whether dynamic specificity (city name, days left) is worth the character cost and the conversion drag seen in customised text generally; the only data point is negative but not yet significant.

## What the platform currently does [Google docs]
- [Google docs] Google Ads API "Customize responsive search ads": `{COUNTDOWN(yyyy-MM-dd HH:mm:ss,daysBefore)}` counts down in the account time zone; `{GLOBAL_COUNTDOWN(...)}` in the user's time zone; `daysBefore` sets when the countdown starts showing. `{LOCATION(Level):Default text}` with Level such as City, State, Country; omitted level uses the most specific available. Custom attributes `{CUSTOMIZER.<name>:<default>}` at account/campaign/ad group/keyword level, most specific wins, 40 attributes per account, headlines and descriptions only, limits include inserted text, default used when the value is too long or invalid provided the default fits. Fallback behaviour for countdown and location tags is not specified on the page.
- [Google docs] Google Ads Help answer/6072565: countdown example `{=COUNTDOWN(Mixers.Sale_ends)}` renders "5 days" five days before the end; VisURL path customisation unsupported for RSA countdowns; ETA customizers could not be created/edited after 2022-06-30 and stopped serving 2024-05-31.
- [Google docs] Google Ads API RSA overview (2026-09-30): an RSA whose customizers lack fallback values can be rejected (NOT_ENOUGH_AVAILABLE_ASSET_LINKS_WITH_FALLBACK_FOR_VALID_COMBINATION).

## Baseline check
Read `google-ads-ad-copy` and `google-ads-ad-extensions` (promotion assets with dates; location assets). Neither covers countdown or location insertion syntax, time-zone choice, daysBefore, fallback, or the evidence that location mentions and customised text can lose. This skill adds those plus the test design.

## Judgment calls
- Practitioner canon on these specific customizers is thin on method but adequate on effect; the skill therefore spends its rules on gating, fallback safety and a labelled test, and labels mechanics as Google docs.
- Chose GLOBAL_COUNTDOWN as the Epiminds default for multi-country Nordic/EU accounts, from the documented time-zone behaviour, and said so.

## Canon strength: Adequate
Two Tier 1 sources with evidence (Optmyzr 2022 study; Geddes 2026 tests), Geddes 2022 method; mechanics from Google docs.

## Invalidated by
Changes to the COUNTDOWN/LOCATION tag syntax or fallback behaviour; removal of business-data customizers; AI Max text customisation overriding advertiser customizer text.
