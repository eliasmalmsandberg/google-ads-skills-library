---
name: statistical-significance-ad-tests
id: 82
description: Rules for calling a winner in RSA and landing-page tests — minimum data per ad, the confidence ladder, the winner metric, the stop rule, and why unpinned-vs-unpinned RSA tests usually cannot be called. Not for campaign-level experiments (see 79) or incrementality (80/81).
tags: Research / All / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google removing "Do not optimize" rotation entirely; changes to RSA asset limits (15/4) or pinning rules; a documented significance method in ad variations; mandatory final URL expansion or AI Max text customisation breaking ad-vs-ad comparability.
---
## What this is
The decision rules Epiminds uses to declare an ad or landing-page test won, lost, or abandoned. Position: conversions per impression (CPI) is the winner metric, CPA/ROAS are filters, per-ad minimum data must be met before confidence is even read, and no test is called below 90%. An RSA test is a test between pinned designs; "let Google pick" is not a test that can be called in a normal ad group.

## Where it comes from
Adalysis' Ad Testing Guide (minimum data per ad by traffic tier, confidence ladder by keyword type, 10×/3-month stop rule, CPI over CTR) (Adalysis, 2026); Geddes on RSA combination arithmetic and the five RSA test designs (Geddes/Adalysis, 2022); Geddes' evidence that Optimize rotation starves the best-CPI ad (Geddes/Adalysis, 2018); Geddes' 5,900-account pinning study (Geddes/Adalysis, 2026); Hopkins' 22k-account Ad Strength study (Hopkins/Optmyzr, 2024).

## When to use it / when not to
Use whenever two or more RSAs, or two landing pages behind identical ads, are live in the same ad group and someone wants to pause one. Use before any "Ad Strength says…" conversation with a client.

Do not use to compare ads that were not live in the same window (serving and auction conditions differ; Geddes/Adalysis, 2018). Do not use on ad groups with fewer than ~350 impressions per ad per week; they will never clear the floor (Adalysis, 2026) — consolidate first. Do not use to judge Google's unpinned asset serving unless the ad group sees hundreds of thousands of impressions a month (Adalysis, 2026).

## Inputs
- Per-ad impressions, clicks, conversions, conversion value for the same date range, ads active for the whole range.
- Traffic tier of the ad group (low / mid / high / own-brand) and the keyword type (long-tail / mid / top / third-party brand / own brand) (Adalysis, 2026).
- Rotation setting and bid strategy (Optimize is forced under Smart Bidding; Adalysis, 2026).
- Pinning state of each RSA and asset counts.
- The client's binding constraint: CPA ceiling or ROAS floor.

## Method
1. **Design the test so it can be called.**
   - Two to three RSAs per ad group, never five or more (serving becomes effectively random; Adalysis, 2026; Geddes/Adalysis, 2018).
   - Pin. An unpinned 15-headline RSA has 2,940 headline pairs, ×12 with four descriptions; at even 100 impressions per combination — "not enough most of the time" — that is >294,000 impressions before one ad is readable (Geddes/Adalysis, 2022). Epiminds default: all three headline positions pinned with 1–2 assets each, so the test is between pinned designs. Pinning all three raises data density and, in the 5,900-account study, the 3-pin group had a markedly higher conversion rate (Geddes/Adalysis, 2026).
   - Landing-page tests: identical ads, different final URLs; metric is conversion rate (Adalysis, 2026).
2. **Set rotation.** Manual CPC / Maximize Clicks / script-managed bids → "Do not optimize" (Adalysis, 2026). Under Smart Bidding, Optimize is forced; expect the highest-CTR ad to be served ~3× as often as the best-converting ad and a worse ad to collect up to ~20× the impressions of the best-CPI ad (Geddes/Adalysis, 2018). Compensate by (a) running only two ads and (b) reading per-ad minimums, not test totals.
3. **Do not read until every ad clears the floor** (impressions / clicks / conversions, per ad):
   - low-traffic ad group: 350 / 300 / 7
   - mid: 750 / 500 / 13
   - high: 1,000 / 1,000 / 20
   - own well-known brand terms: 100,000 / 10,000 / 100–1,000
   and at least one full week has elapsed (Adalysis, 2026). The floor is per ad; a test where one ad has 2,000 impressions and the other 82 is not readable (Geddes/Adalysis, 2018). Confidence shown before the floor is noise: 97 impressions can display 97% (Adalysis, 2026).
4. **Pick the metric before reading.**
   - Default winner metric: CPI (conversions per impression) (Adalysis, 2026; Geddes/Adalysis, 2026).
   - CPA (or ROAS) is a filter: discard any ad above the CPA ceiling / below the ROAS floor, then pick the highest CPI (or RPI) among survivors (Adalysis, 2026).
   - CTR only when the goal is traffic or Quality Score, or as tie-break (Adalysis, 2026).
   - CVR only for landing-page tests with identical ads (Adalysis, 2026).
5. **Apply the confidence ladder** on the chosen metric (two-proportion test on the counts; the Adalysis engine or an equivalent calculator):
   - long-tail keywords: 90%
   - mid-volume: 90–95%
   - top keywords: 95–99%
   - own brand: 95% (unknown brand) to 99% (well-known)
   - third-party brands: 90–95%
   Never below 90% (Adalysis, 2026).
6. **Stop rule.** If an ad reaches 10× the minimum data or the test passes 3 months without reaching the ladder's confidence, end it with no winner and replace the variant with a different hypothesis (Adalysis, 2026). Do not "run a bit longer".
7. **Call and act.** Winner → pause loser, launch the next challenger against the winner. In Geddes' example, pausing the worst-converting RSA added >200 conversions in 30 days to the ad group (Geddes/Adalysis, 2022). No winner at stop → keep both, change the hypothesis.
8. **Ignore Ad Strength when calling.** "Average" Ad Strength RSAs had the best CPA, CVR and ROAS across 22k accounts, with no meaningful CTR difference by label (Hopkins/Optmyzr, 2024); Ad Strength is unrelated to the metrics or QS (Adalysis, 2026). A winning pinned RSA will often show "Poor" (Geddes/Adalysis, 2022).

## What Google will tell you instead, and why we don't
- Google pushes unpinned 15-headline RSAs and "Excellent" Ad Strength. The combination count makes such an ad untestable below hundreds of thousands of impressions (Geddes/Adalysis, 2022; Adalysis, 2026), and Ad Strength does not predict performance (Hopkins/Optmyzr, 2024). We test pinned designs and do not report Ad Strength.
- Google's Optimize rotation claims to find the best ad. Its serving skews to CTR and can give a worse ad ~20× the impressions of the best-CPI ad (Geddes/Adalysis, 2018). We rotate where we can and read per-ad floors where we cannot.
- Google's ad variations report shows modified vs original without a documented significance method [Google docs]. We run ad variations only as the delivery mechanism and apply steps 3–6 to the output.
- Google's experiment scorecard defaults to 80% (see 79); for ads we never go below 90% (Adalysis, 2026).

## Failure modes
- **Low-volume ad groups (<350 impressions/ad/week).** The floor is never met; consolidate ad groups or test at campaign level instead (Adalysis, 2026).
- **Smart Bidding + many ads.** Optimize plus ≥4–5 ads makes serving random and the comparison invalid (Geddes/Adalysis, 2018; Adalysis, 2026).
- **Brand ad groups.** Minimums are two orders of magnitude higher and the ladder is 95–99% (Adalysis, 2026); most brand "tests" never close.
- **Final URL expansion / AI Max text customisation on.** Google rewrites assets and landing pages per ad; ad-vs-ad comparability is gone (Geddes' pinning study excluded FUE campaigns for this reason; Geddes/Adalysis, 2026).
- **Ads added at different times.** New ads are either starved or over-served (Geddes/Adalysis, 2018); compare only the overlapping window.
- **Seasonal CVR swings.** A 3-month test window straddling a peak measures the peak; read both ads over the same days, never cumulative since launch.
- **E-commerce with ROAS goal.** CPI picks volume; use ROAS as the filter and RPI (revenue per impression) as the winner metric (Adalysis, 2026).

## What to measure
Per ad in the test window: impressions, clicks, conversions, value, CPI, CPA, CTR, the tier floor status, the confidence on the chosen metric, days running, and whether the 10×/3-month stop has been hit (Adalysis, 2026). Across the account: number of tests called per month and the CPI lift realised after pausing losers (Geddes/Adalysis, 2022).

## Open disagreements in the canon
- **Pinning and conversion rate.** Geddes' 5,900-account study: CVR and CPI rise with pinning; pin all three headlines if you will act on the data (Geddes/Adalysis, 2026). Hopkins' 22k-account study: CVR suffered with pinning; some pinning best on CPA/ROAS, leave room for Google (Hopkins/Optmyzr, 2024). Epiminds: pin all three positions for *tests*; Geddes concedes the 3-pin group are also the most active testers, so the causal claim is weak, but the data-density argument is enough — an unpinned ad cannot be called at our clients' volumes.
- **Minimum confidence.** Adalysis floors at 90% and climbs by keyword type (Adalysis, 2026); Google's experiment tooling shows 80% by default [Google docs]. Epiminds takes the Adalysis ladder.
