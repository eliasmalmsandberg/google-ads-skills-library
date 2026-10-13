---
name: ad-strength-not-performance
id: 25
description: The evidence that Ad Strength does not predict RSA performance, and the rules for what to do when a client, a rep or the recommendations tab pushes for "Excellent". Not a writing guide (23) or pin guide (24).
tags: Research / Search / Optimise / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google replacing Ad Strength with a performance-based score, or using it in Ad Rank or serving eligibility.
---
## What this is
Ad Strength scores asset completeness and diversity before an ad serves; it is not an auction factor and, across two independent 20,000-account studies, "Average" ads beat "Excellent" ads on CPA, CVR and conversions per impression. This skill is the evidence and the handling rules for the pressure to chase the label.

## Where it comes from
Navah Hopkins / Optmyzr (2024, 22,000+ accounts, 1M+ ads), Frederick Vallaeys / Optmyzr (2026, ~20,000 accounts; 2022 SMX Advanced experiment reported by Search Engine Land), the Optmyzr 2022 RSA study, Brad Geddes / Adalysis (2022 observations on pinning and strength). Google's own description of the rating from Ginny Marvin (SEJ, 2024), labelled.

## When to use it / when not to
Use when an account review, Google rep call, optimisation score or client request asks for Ad Strength to be raised, or when an audit template scores on it. Not a reason to leave genuinely empty ads alone: an RSA with three near-identical headlines is bad for reasons that have nothing to do with the label (skill 23).

## Inputs
- Per-ad Ad Strength rating and the account's distribution of ratings.
- Per-ad CPA, CVR, conversions per impression and ROAS over a window that clears the combination budget (skill 22).
- The specific suggestion being pushed (add headlines, unpin, accept suggested text, enable AI Max text customisation).

## Method
1. **State what the rating is before arguing about it.** Google's own description: a diagnostic built from headline count, keyword relevance, headline uniqueness and description uniqueness; not used in the auction, bidding, eligibility, Quality Score or Ad Rank (Marvin, SEJ 2024; Marvin on X via Search Engine Land). It drops when you pin (Marvin, 2024) and barely correlates with headline length (0.056; Vallaeys/Optmyzr, 2026).
2. **Put the efficiency evidence on the table.** 2026, ~20,000 accounts: Average ads had the best CPA ($12.43), highest CVR (12.65%) and most conversions per impression (1.40%); Excellent had the worst CPA ($28.68) and lowest CVR (4.97%); Poor had the best ROAS (327.65%) (Vallaeys/Optmyzr, 2026). 2024, 22,000+ accounts: Average RSAs best on CPA, CVR and ROAS; no meaningful CTR difference across labels; ROAS fell sharply from Average to Good (Hopkins/Optmyzr, 2024). 2022: each step ≈3% more clicks, no relation to performance (Optmyzr, 2022).
3. **Reconcile Google's 12–15% claim as a volume effect.** Google reports 12% more conversions (Marvin, 2024) and ~15% more clicks and conversions (Google Ads Help, Aug 2025 internal data) from Poor→Excellent. More assets → more combinations → more auctions → more total clicks and conversions (Marvin, 2024; Optmyzr 2022's 3%-per-step clicks). That is compatible with worse CPA and CVR per the studies above. Decision rule: if the account's constraint is volume at acceptable CPA, adding distinct assets can be worth it — judged on CPA, not the label. If the constraint is efficiency, do not add assets to move the label.
4. **Use the label for exactly one thing.** Hopkins (2024): a filter for creative so weak it may not earn impressions. Geddes (2022) observed fully pinned "Poor" RSAs getting fewer impressions than sibling RSAs in the same ad group. So: a Poor rating on an ad that is also losing impression share to its sibling is a flag to check pins and asset count; a Poor or Average rating on an ad that performs is left alone (Vallaeys, 2026: stop optimising for it if KPIs are fine).
5. **Never accept the suggestion link to move the score.** Typing Google's suggested text by hand did not raise Ad Strength; adding the identical text via the suggestion link did (Vallaeys at SMX Advanced, 2022). The score rewards the path, not the words. If the text is good, type it; if it is only there to move the score, it fails skill 23's line-count rule.
6. **Keep it out of audits and reporting.** Do not build Ad Strength into audit scorecards or client reports (Hopkins, 2024). Report conversions per impression, CPA and the data-budget status of ad groups (skill 22) instead. If a client template scores on it, include the rule-2 numbers in the appendix once and remove the metric.
7. **Decline AI Max text customisation as a strength fix.** The rating accounts for automatically created assets if enabled (Marvin, 2024), so turning it on lifts the label; but those assets are not listed with the ad's own assets and cannot be removed through the normal ad edit (Google Ads API docs, 2026), which breaks skill 22's testing. Strength is not a reason to opt in.

## What Google will tell you instead, and why we don't
Google's RSA page says run at least two RSAs per ad group with Good or Excellent strength and cites ~15% more clicks and conversions from Poor→Excellent; the asset-reporting page says reach Excellent by adding assets to the maximum before replacing any; the recommendations tab scores you on it. We don't manage to the label because the two largest independent studies show Average ads with the best CPA and CVR and Excellent with the worst (Vallaeys, 2026; Hopkins, 2024), because the score moves with how the text was entered rather than what it says (Vallaeys, 2022), and because Google itself says it is not an auction factor (Marvin, 2024).

## Failure modes
- Brand-new accounts or advertisers with no copy process: Vallaeys (2022) says the rating "mostly helps newer advertisers" — for a first ad with three headlines, the diagnostic's prompts to add distinct lines are not wrong. Use skill 23 instead of the score, but don't argue the label with someone who has nothing else.
- Ad groups starved of impressions: a Poor fully pinned ad may be losing serving share to a sibling (Geddes, 2022). Here the label is correlated with a real serving issue; fix the pin map (skill 24), which happens to lift the label.
- Volume-constrained accounts where CPA headroom exists: adding genuinely distinct assets can raise total conversions (Google's 12–15%; Optmyzr 2022's clicks-per-step). The mistake is the metric, not the action.
- Demand Gen and PMax: the rating measures asset breadth across formats (Marvin, 2024); the RSA findings here do not transfer, and the 2024 study's Demand Gen cut shows a different shape (Hopkins, 2024).

## What to measure
CPA, CVR, conversions per impression and ROAS by Ad Strength bucket in your own account (replicate Vallaeys 2026 before quoting it to a client); impression share between sibling RSAs in the same ad group for any ad rated Poor; the count of recommendations accepted solely to move the score (target: zero).

## Open disagreements in the canon
- Is the rating useless or merely misused? Hopkins (2024) and Vallaeys (2026) keep it as a filter for creative so weak it may not serve; Geddes' reader base (2022) treats it as noise. Epiminds keeps the single filter use (rule 4) and nothing else.
- Google's 12–15% vs practitioners' CPA findings: Epiminds reads them as volume vs efficiency and decides per account's constraint (rule 3) rather than declaring either wrong.
