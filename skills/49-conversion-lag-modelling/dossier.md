# Dossier — 49 Conversion lag modelling

## Sources

1. **Source**: Frederick Vallaeys, Optmyzr — "Google is making Smart Bidding more obedient", https://www.optmyzr.com/blog/smart-bidding-budget-caps-guide/ · **Tier** 1 · **Date** 2026-08-11 · **Claim**: Judge Smart Bidding on *matured* performance against date-matched targets, excluding the conversion-delay window; wait one to two full conversion cycles before judging any change; Google itself warned forecasts were unreliable during the 17–31 Aug 2026 transition. · **Evidence**: method; Google docs.

2. **Source**: Frederick Vallaeys, Optmyzr — "Value-based bidding guide", https://optmyzr.com/blog/value-based-bidding-guide · **Tier** 1 · **Date** 2026-07-16 · **Claim**: Conversion lag misattributes results to the wrong day; judging during the 1–2 week learning period and on unmatured data are the two most common VBB mistakes; experiments need ≥3 conversion cycles or 4 weeks before reading. · **Evidence**: support-ticket patterns.

3. **Source**: Frederick Vallaeys, Search Engine Land — "Why PPC measurement feels broken", https://searchengineland.com/ppc-measurement-broken-468574 · **Tier** 1 · **Date** 2026-02-10 · **Claim**: Bidding systems account for lag and validate new signals over time; imported or modelled conversions appear in reporting before they are fully weighted in optimisation; "conversions arriving later than expected" is a normal symptom. · **Evidence**: experience.

4. **Source**: Nils Rooijmans — "Data exclusions", https://nilsrooijmans.com/daily/data-exclusions · **Tier** 1 · **Date** 2025-10-16 · **Claim**: Operational lag rule: if more than 30% of conversions take more than a day from last interaction, with a ~2-day typical delay, widen any click-based window by two days; i.e. use the lag distribution, not the calendar. · **Evidence**: worked example on Google's help text.

5. **Source**: Will Gray, WebMechanix (on Optmyzr) — https://www.optmyzr.com/blog/make-value-based-bidding-work-for-you/ · **Tier** added-Tier-2 (dossier 43) · **Date** 2024-12-10 · **Claim**: Which stage you can optimise to depends on how long it takes to convert; 90-day maximum click window. · **Evidence**: practice.

6. **Source**: Fred Vallaeys & David Newson, Optmyzr Town Hall — https://www.optmyzr.com/ppctownhall/optimize-ppc-long-sales-cycles · **Tier** 1 host · **Date** 2026-08-12 · **Claim**: Signals returned within ~2 weeks steer bidding; at 90 days it's largely wasted; 24-month cycles can't be closed-loop measured in-platform. · **Evidence**: anecdote.

7. **Source**: Lakshmi Padmanaban, Optmyzr — "Google Ads for BFCM 2026", https://www.optmyzr.com/blog/google-ads-bfcm-2026/ · **Tier** 1 outlet · **Date** 2026-09-22 · **Claim**: The week after Cyber Monday, Standard Shopping CVR was 7.3% below pre-BFCM and CPC 10.2% higher — a real post-peak dip that lag analysis must not "correct away". · **Evidence**: 4,211 accounts.

8. **Source**: Google Ads Help — data exclusions (answer/10370710) and bid simulators (answer/2470105), fetched 2026-10-13 · **Tier** Reference only · **Claim**: Exclusions must "account for conversion delay"; if a week or more of clicks is affected expect 1–2 conversion cycles of fluctuation. Search, PMax and App simulators "include expected late conversions"; other types count only conversions recorded in the simulation period. Google's lag-bucket and days-to-conversion segments exist in the API (reference pages fetched but definitions truncated).

## Dissenting view
No canon source disputes that lag must be modelled; the disagreement is about who does it. Vallaeys (SEL 2026) says the bidder already accounts for lag and validates late signals — i.e. don't over-correct. Rooijmans treats lag as something the operator must explicitly build into every window. Brainlabs (Cecere 2026, not canon-cited) pushes the other way: the "lag" that matters is weeks of upper-funnel influence that in-platform lag reports never see. The practical disagreement is whether a lag-adjusted dashboard is enough (Rooijmans/Vallaeys) or a distraction from incrementality (Brainlabs).

## What the platform currently does [Google docs]
- [Google docs] Reporting attributes conversions to the click/interaction date by default; "by conversion time" columns and days-to-conversion / conversion-lag-bucket segments exist to split by when the conversion happened (API reference fetched 2026-10-13; definitions truncated in fetch — labelled from field names).
- [Google docs] Search/PMax/App simulators include expected late conversions; others don't (answer/2470105).
- [Google docs] Data exclusions must account for conversion delay; 1–2 cycles of fluctuation after a week-long exclusion (answer/10370710).
- [Google docs via Gray 2024] 90-day maximum click-through conversion window.

## Baseline check
Read `google-ads-attribution` (Time Lag report: "if 20% of conversions happen after day 30 your window is losing them"; "set client expectations") and `google-ads-bidding` (learning period). Baseline knows the time-lag report exists and uses it to pick a window. This skill adds: the maturity-curve construction from the lag buckets, the rule that recent-period verdicts are forbidden inside the p90 lag window, the ×(1/maturity) expected-conversion read for the open window, the lag-share rule for widening any click-based window, the "imported conversions are reported before weighted" caveat, and the post-peak-dip guard.

## Judgment calls
- Canon strength is Adequate: three Tier 1 authors with explicit rules (exclude the delay window; widen by lag share; 1–2 cycles) but no published maturity-curve method. The curve construction in the skill is Epiminds' own, built on Google's by-conversion-time reporting, and is labelled as such.
- Position: never issue a performance verdict on the last p90-lag days; report two numbers (matured and expected) for the open window; monthly cadence re-derives the curve.

## Canon strength: Adequate
Three Tier 1 sources with rules, Google docs for primitives; no cross-account evidence on lag modelling specifically.

## Invalidated by
Google changing conversion-time reporting, the lag-bucket segments, the 90-day click window, or (for the bidding caveat) how late conversions are weighted in Smart Bidding.
