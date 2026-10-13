---
name: ad-variations-account-wide-tests
id: 27
description: How to test one copy change (CTA, price, claim, pin rule) across many ads at once — the label-copy method as default, Google's Ad variations tool as the fallback — and how to read the result. Not the monthly loop (22) or single-ad-group testing.
tags: Technique / Search / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google removing or redesigning Ad variations; removal of asset-level statistics; change to the 3-RSA-per-ad-group limit.
---
## What this is
A procedure for a single-variable copy test across many ad groups. Epiminds runs it as a labelled copy test in the account's own data (Geddes' method), and uses Google's Ad variations tool only as a fallback for a mechanical find-and-replace. The reason is control over what gets compared and how it is segmented, not distrust of the tool's maths — which, for the record, none of our sources describe.

## Where it comes from
Brad Geddes / Adalysis (2026 account-wide insight method; 2022 RSA testing strategies; Adalysis testing checklist), Frederick Vallaeys / Optmyzr (2021 conversions-per-impression rule; 2022 recommendation to use Ad variations for creative tests), Optmyzr product guidance (2023). The Ad variations help page could not be read for this skill, so no tool settings are asserted here.

## When to use it / when not to
Use when one change — a CTA phrase, a price or discount claim, a trust line, keyword insertion on/off, a pin rule — needs an answer that holds across the account, and the account has enough ad groups above the data budget to split evenly. Not for low-volume accounts where fewer than two matched sets of ad groups clear 100 impressions per combination (Geddes, 2022), and not for testing two whole ad concepts, which is a per-ad-group test (skill 22 rule 4).

## Inputs
- The single change, stated as a pattern (Geddes, 2026 uses wildcards and "does not include" notation: e.g. headline contains "$" vs does not).
- Candidate campaigns, brand and non-brand listed separately (Geddes, 2026).
- Per ad group: 30-day impressions and combination count (skill 22 rule 1).
- Label namespace (Geddes, 2026: prefix test labels with "ad-").

## Method
1. **Pick the variable and the metric first.** One change. Judge on conversions or conversion value per impression (Vallaeys, 2021; Adalysis checklist; Geddes, 2026), with impressions reported alongside because RSA volume differs between ads under identical conditions (Vallaeys, 2021). Set the minimum data and confidence before launch (Adalysis checklist).
2. **Select ad groups that can pay for the read.** Only ad groups that clear well over 100 impressions per combination (Geddes, 2022). Split them into two sets with the same number of ad groups per version and comparable volume; an unequal split is rerun, not interpreted (Geddes, 2026). Exclude brand from non-brand tests (Geddes, 2026).
3. **Default implementation: label-copy.** Label the control ads; copy them under a second label; apply the change to the copies only — add or remove an asset, change a pin, swap the CTA (Geddes, 2026). Both ads run in the same ad group, so the comparison is within ad group and the aggregate is read by label across ad groups. Max three RSAs per ad group (Geddes, 2022; Optmyzr, 2023), so an ad group already running three needs one paused first.
4. **Fallback implementation: Ad variations.** When the change is a literal find-and-replace across hundreds of ads and labelling by hand is impractical, use Google's Ad variations under Experiments, as Vallaeys (2022) and Optmyzr (2023) suggest for creative and asset-level tests (add, pin, swap). Still apply rules 2 and 5: pre-select eligible campaigns and re-read the outcome in the asset report, not only in the tool's summary, because none of our sources describe how the tool's result is computed and this skill makes no claim about it.
5. **Read by pattern, segmented.** Aggregate by label across ad groups, then segment by campaign type; the account-wide number can hide opposite results in brand vs non-brand or in high- vs low-intent campaigns (Geddes, 2026). Where CTR and CVR disagree, value per impression decides (Geddes, 2026 B2B example: "get a quote" lost CVR, won value per impression).
6. **Decide.** Significant and consistent across segments: roll the change to all eligible ads and retire the losing pattern account-wide. Significant in one segment only: roll out there, keep testing elsewhere. Not significant: do not conclude; extend or rerun with more ad groups (Geddes, 2026). Rerun any test whose sets ended unequal in ad group count or volume.
7. **Clean up.** Pause the losing labelled copies (Geddes, 2022: pause losers even when Google serves the "best" ad most), keep labels for the log, and record the pattern result for skill 22's monthly hypothesis list.

## What Google will tell you instead, and why we don't
Google's UI presents Ad variations as the way to test copy across campaigns, and its asset reporting page says to evaluate at campaign level. We prefer the label-copy method because the results then live in our own asset and ad data, can be segmented by campaign type and aggregated by pattern (Geddes, 2026), and are judged on conversions per impression rather than whatever the tool summarises (Vallaeys, 2021). We also refuse to run any account-wide test over ad groups that cannot clear the per-combination data budget, which Google's tooling does not stop you doing (Geddes, 2022).

## Failure modes
- Small accounts (few ad groups clear the budget): the split is too thin to segment; use a per-ad-group test in the one or two ad groups that qualify (skill 22) and accept that the answer is local.
- Brand campaigns included in a non-brand pattern test: brand's volume swamps the aggregate (Geddes, 2026 keeps them separate).
- Ad groups already at three RSAs: the copy cannot be added (Geddes, 2022; Optmyzr, 2023); pausing a live ad to make room changes the control.
- Tests on H3 or D2 content: those slots are not guaranteed to show (Google Ads Help), so a change there is a change in some impressions only; move the variable to H1/H2/D1 or pin it (skill 24).
- AI Max text customisation on: Google-added assets are invisible in the ad's asset list (Google Ads API docs, 2026) and vary between the two sets; turn it off in test campaigns.
- Reading before the budget is met: weekly metrics in low-volume ad groups are inconsistent (Geddes, 2022); the account-wide total can look significant while every segment is noise.

## What to measure
Conversions and value per impression by label, overall and by campaign type; impressions by label (to catch the serving skew Vallaeys 2021 warns about); ad groups per version and their volume (equality check); impressions per combination reached per ad group at read time.

## Open disagreements in the canon
- Tool vs. labels: Vallaeys (2022) and Optmyzr (2023) point to Ad variations; Geddes (2026) builds the test in labels. Epiminds defaults to labels for the segmentation and metric control, and uses the tool for mechanical replacements only.
- Scope of conclusion: Geddes (2026) argues single-ad-group tests only find the best ad for that targeting; Vallaeys (2021) is comfortable with up-to-three-RSA tests per ad group. Epiminds uses both at their own scope: per-ad-group for "which ad", account-wide for "which message".
