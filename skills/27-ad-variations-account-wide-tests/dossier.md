# Dossier — 27 Ad variations tool for account-wide copy tests

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch. The Google Ads Help page for Ad variations (answer/9177946, and the en-GB / co= variants) refused to fetch, so this dossier has no Google-docs description of the tool's settings (split, duration, reporting). The skill therefore does not state any tool mechanics beyond what the practitioner sources say, and says so.

## Sources

- **Source:** Vallaeys via Nicole Farley, Search Engine Land — "Creating better ads in a world with only RSAs", https://searchengineland.com/creating-better-ads-in-a-world-with-only-rsas-386377 · **Tier** 1 · **Date** 2022-07-11 · **Claim:** Test RSAs against RSAs (not against ETAs); "use ad variations under the campaign Experiments section to test creative." · **Evidence:** opinion from a 1.7M-ad audit context.
- **Source:** Sukanya Chatterjee, Optmyzr — "How to Create, Optimize, and Manage Google RSAs", https://www.optmyzr.com/blog/create-optimize-manage-google-responsive-search-ads/ · **Tier** 1 outlet, vendor/product content (cite with care) · **Date** 2023-05-01 · **Claim:** Use Google Ads Ad Variations for asset-level tests of adding, pinning, or swapping assets; only 3 RSAs can be created per ad group. · **Evidence:** opinion.
- **Source:** Brad Geddes, Adalysis — "How to find real insights hiding in your RSA data", https://adalysis.com/blog/how-to-find-real-insights-rsa-data/ · **Tier** 1 · **Date** 2026-09-29 · **Claim:** The alternative account-wide method: pick campaigns (brand/non-brand separate), label test ads ("ad-" prefix), copy under a second label, change one thing in one set (pinning, an asset, deleted assets), equal ad group counts per version, segment by campaign type, judge on conversion value per impression; rerun unequal tests; don't conclude from non-significant results. Example pattern results (keyword insertion off > on; price in headline trending worse; quote > affordable on value per impression). · **Evidence:** account tests.
- **Source:** Brad Geddes, Adalysis — "How to test RSAs", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** For theme tests use a maximum of three RSAs per ad group, pinning 1–3 assets to the same headline position in each; need well over 100 impressions per combination; low-volume ad groups give inconsistent weekly metrics; pause losers. · **Evidence:** method with examples.
- **Source:** Adalysis docs — "Ad testing checklist", https://docs.adalysis.com/product/inside-adalysis/ad-testing-checklist · **Tier** 1 · **Date** undated · **Claim:** Theme-based tests across multiple ad groups (pricing vs quality, reviews vs offers, CTA vs authority); define minimum data and confidence before choosing a winner; conversion per impression over CTR. · **Evidence:** method.
- **Source:** Frederick Vallaeys, SEJ — "How To A/B Test Responsive Search Ads", https://www.searchenginejournal.com/how-to-test-responsive-search-ads/429270 · **Tier** 1 · **Date** 2021-12-17 · **Claim:** Any RSA test must include impression data; measure conversions per impression; messaging first, positions second. · **Evidence:** Optmyzr data.

## Dissenting view
Vallaeys (2022) and Optmyzr's product content (2023) point to the Ad variations tool for creative tests; Geddes (2026) runs account-wide tests through labels and ad copies instead, so that results can be segmented by campaign type and patterns can be aggregated. The disagreement is about where the test lives: in Google's experiment reporting (which the practitioners do not describe in detail) or in the advertiser's own labelled data.

## What the platform currently does [Google docs]
- [Google docs] Ad variations help page: could not be fetched; no platform claims about the tool are made in the skill.
- [Google docs] About RSAs (answer/7684791): H1/H2/D1 always shown; pinning one asset blocks the slot.
- [Google docs] Campaign-level asset reporting (answer/9781208): asset statistics for dates on or after 2025-06-05; asset-level ratios are directional and non-summable.
- [Google docs] Google Ads API RSA overview (2026-09-30): automatically created assets are not returned with the ad's own assets.

## Baseline check
Read `google-ads-experiments` (describes Ad variations as find/replace/swap across campaigns; a sample-size formula) and `google-ads-ad-copy`. The baseline's description of the tool is unsourced and its sample-size rule is generic. This skill adds the practitioner alternative (label-copy method), the equal-ad-group and segmentation rules, the per-combination data gate, and the decision rule for choosing between the tool and the label method.

## Judgment calls
- Canon on the *tool* is thin (two opinions, no evidence, no Google doc read); canon on the *job* (one change across many ads) is adequate with Geddes' 2026 evidence. The skill is written for the job and names the tool only where the sources do.
- Position taken: the label-copy method is the Epiminds default; the tool is the fallback for a single find-and-replace where labelling is impractical, with results re-read through the asset report.

## Canon strength: Adequate
Two-plus Tier 1 sources; evidence from Geddes' 2026 account tests; the tool itself is referenced only in opinion.

## Invalidated by
Google removing or redesigning Ad variations; removal of asset-level statistics; changes to the 3-RSA-per-ad-group limit.
