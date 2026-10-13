# Dossier — 80 Geo experiments / conversion lift

## Sources

1. **Source**: Haus (haus.io), "Understanding Google Ads incrementality testing" — https://haus.io/article/google-ads-incrementality-testing · **Tier** added-Tier-2 for this topic, with a vendor caveat (Haus sells geo testing; the page publishes method and worked numbers and contradicts platform-reported ROAS, so it passes the inclusion rule on method and evidence but fails the "not tool-vendor content" clause — use only for method, never as the reason to buy) · **Date** undated, 2026 footer · **Claim**: Two designs — Google Conversion Lift (user- or geo-randomised, Google controls exclusions and maths) vs. third-party geo holdout measuring total sales across channels (synthetic control). Power: ~1,000 weekly conversions detects ~10% lift; ~100 weekly detects only >~25%. Read as incremental ROAS vs. platform ROAS (example: $100k treatment spend, $300k treatment revenue vs. $250k scaled control = $50k incremental, iROAS 0.5× vs. platform 3.0×). "Incrementality factor" = incremental ÷ platform-reported conversions, used to calibrate later reporting. Pitfalls: low volume, opportunity cost of holdout, seasonality, commuting-zone contamination between adjacent geos. Google's typical minimum duration 14 days; monitor ~3 weeks after for lag. · **Evidence or opinion**: Method with worked example; two case results (Caraway: Google overstated PMax-with-brand by ~33%; Jones Road: doubling YouTube spend more than doubled new-customer orders) without test parameters.

2. **Source**: Tyler Horner & Nick Doren (Haus), "PMAX Experiments Revealed: Including vs. Excluding Branded Search Terms" — https://www.haus.io/blog/pmax-experiments-including-excluding-branded-search-terms · **Tier** added-Tier-2 (same caveat) · **Date** 2024-08-20 · **Claim**: 3-cell geo design (no PMax / PMax with brand / PMax without brand). Across an unstated number of brand experiments: excluding brand won on incremental revenue in 50% of tests, +24% incremental revenue on average when it won; excluding brand was more efficient for new customers in 100% of tests (CAC 19–60% lower, ~40% average); high-AOV brands (AOV > $238) saw +27% incremental revenue with brand included. Signal threshold cited: ~300–1,000 monthly conversions. · **Evidence or opinion**: Aggregated test results, sample size not stated.

3. **Source**: Anu Adegbola, Search Engine Land, "Google makes incrementality testing easier, cheaper, and faster" — https://searchengineland.com/google-makes-incrementality-testing-easier-cheaper-and-faster-464575 · **Tier** Reference (news) · **Date** 2025-11-12 · **Claim**: Minimum budget for Google incrementality experiments cut from ~$100,000 to $5,000; new models "up to 50% more conclusive"; custom test size and confidence level selectable in UI. · **Evidence or opinion**: Reports Google's announcement; no practitioner commentary.

4. **Source**: Frederick Vallaeys, Search Engine Land, "How Bayesian testing lets Google measure incrementality with $5,000" — https://searchengineland.com/bayesian-testing-google-measure-incrementality-466374 · **Tier** 1 · **Date** 2025-12-18 · **Claim**: Google's $5k lift tests work by Bayesian inference with informative priors from similar campaigns plus hierarchical pooling ("priors + scale"). Worked example: 50/50, $2 CPC, 1,250 clicks per arm, 25 vs 30 conversions → frequentist two-proportion z ≈ 0.68, two-tailed p ≈ 0.50 (not significant despite +20%); flat-prior Bayesian gives ~75–80% probability lift > 0 with a credible interval spanning zero; a prior of ~10% lift for similar campaigns moves the estimate from +0.7% (54% prob.) to +20.5% (76%). Priors are down-weighted as data accumulates, but advertisers cannot inspect them. Read "probability of lift" as a decision input: ~80% justifies extending, replicating or shifting a small allocation, not a full reallocation. · **Evidence or opinion**: Method with worked arithmetic; the prior-sensitivity table is the evidence that small-budget results are prior-driven.

5. **Source**: Google Ads Help, "Strengthen media measurement… incrementality testing improvements" (John Chen, 2025-11-11) — https://support.google.com/google-ads/answer/16719772 ; "Conversion Lift study settings (user-based)" — https://support.google.com/google-ads/answer/12005564 · **Tier** Reference only · **Date** 2025-11 / 2026-04 · see below.

Not found: no Tier 1 canon page on self-run geo/holdout *design* (geo selection, pre-period, synthetic control). The web-search budget for this build was exhausted before this skill; guessed URLs for Optmyzr, Tinuiti/Aaron Levy and 8020agent on incrementality did not resolve. Mike Rhodes' site blocks fetch. Nothing from Vallaeys, Geddes, Williams, Rooijmans, McNair/Meijer, Brainlabs, Cruz or Hopkins specifically on geo-lift design was reachable.

## Dissenting view
Haus (2026) argues platform-run Conversion Lift studies carry selection bias because Google controls exclusions and the calculation; Vallaeys (2025) accepts Google's Bayesian method as "math, not magic" but shows the small-budget estimate is largely the prior, which advertisers cannot inspect; Google positions its studies as the calibration source for MMM [Google docs]. The disagreement is about who holds the control group and the maths — the platform being measured, or a third party — and whether a prior-driven lift estimate is evidence.

## What the platform currently does [Google docs]
- Conversion Lift (user-based): minimum $5,000 campaign budget; ≥1,000 observed conversions; holdout 1–50%; "certainty" selector 50–95% in 5% steps, ≥90% recommended, 50–90% labelled directional; 7-day minimum, ≥14 days recommended; studies shorter than that can lose up to 17% of absolute lift; one study per campaign at a time; Search, Display, Video, Demand Gen, App, PMax eligible; results as incremental conversions/iCPA or incremental value/iROAS, with projected "cooldown" conversions included by default (Demand Gen studies from 2 Mar / 14 Apr 2026) [Google docs, answer 12005564].
- Geo-based Conversion Lift is set up via a separate guide (not fetched).
- Nov 2025: minimum budget lowered from ~$100k to $5k; custom confidence; results in UI [Google docs, answer 16719772; SEL 2025-11-12].
- Jan 2026: Lift studies consolidated with Experiments in the Experiment Center [Google docs, answer 16856494].

## Baseline check
Read `google-ads-experiments` (PMax vs Search experiment section) and `google-ads-attribution`. Neither covers holdout design, power vs. conversion volume, or iROAS vs. platform ROAS; this topic would add those, but the canon does not yet support writing them.

## Judgment calls
- Haus admitted as added Tier 2 for *method and data* only, with the vendor caveat recorded. Its evidence is aggregated and unparameterised.
- Vallaeys' piece was found after the first pass (via his SEL author page) and lifts the topic from Thin to Adequate; the skill is written around Google Conversion Lift read with Vallaeys' prior-awareness, and the self-run geo design is kept to the power rules Haus publishes.
- The skill positions Google Conversion Lift as the default for Epiminds clients under ~1,000 weekly conversions (self-run geo tests lack power there per Haus), with explicit discounting of results where the prior does the work.

- Review fix (2026-10-13): the ~5,000 monthly-conversion ceiling and the 50%-spend / 6-month re-test cadence are labelled Epiminds operating thresholds; no canon source. Haus should be recorded in canon.md under "Dossier-added Tier 2" (geo/incrementality testing, method and data only, vendor caveat).

## Canon strength: Adequate
One Tier 1 (Vallaeys, method with arithmetic) and one added Tier 2 (Haus, vendor, aggregated data), plus Google docs.

## Invalidated by
Changes to Conversion Lift minimums ($5k, 1,000 conversions, 14 days), the certainty selector, or geo-based study availability; Google changing how projected cooldown conversions are included.
