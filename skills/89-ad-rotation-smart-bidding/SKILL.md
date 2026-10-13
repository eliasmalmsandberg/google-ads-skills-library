---
name: ad-rotation-under-smart-bidding
id: 89
description: Set or audit the ad rotation setting on Search campaigns and decide how ad tests are run when the campaign is on Smart Bidding. Not for RSA copywriting, Ad Strength, or pinning strategy as such.
tags: Setting / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google honouring "Do not optimize" under Smart Bidding; Optimize being re-tuned to conversions rather than clicks; the rotation setting being removed; Ad variations experiments being withdrawn.
---
## What this is
The rotation setting has two values and, on Smart Bidding, zero effect: Google serves "Optimize" regardless. The skill is the rule for which campaigns the setting still matters on, and what replaces it as the ad-testing instrument on the rest.
See also: skill 82 (statistical-significance-ad-tests) — the per-ad data floors, confidence ladder and winner metric for calling the test.
See also: skill 31 (one-vs-two-rsas) — how many RSAs an ad group runs by default and when a third is allowed as a dated test arm.

## Where it comes from
Brad Geddes / Adalysis: the Optimize misallocation analysis (2018), the position that Optimize shows the worst ads (2019), and the 5,900-account RSA pinning study with its note that Google often serves on CTR (2026). Google Help for what the setting does and the Smart Bidding override.

## When to use it / when not to
Use on every new Search campaign build and on takeover audits where ad testing is planned. Shopping and Display carry the same setting but the testing substitutes below are Search-only. Do not use this skill to decide how many headlines to write or what to pin for performance; it only governs how a test gets fair serving.

## Inputs
- Bid strategy per campaign (Manual CPC / Enhanced CPC vs any Smart Bidding strategy).
- Current rotation value (Optimize / Do not optimize).
- Auto-apply status of "Using optimized ad rotation" (an AAR item — Google Help).
- Number of enabled RSAs per ad group and their enabled dates.
- Whether an ad test is live or planned in the next 30 days.

## Method
1. **Classify each campaign by bid strategy.** Google states that on Smart Bidding it "will automatically use the 'Optimize' ad rotation setting" (Google Help); Geddes observed the same, applied even when Rotate is selected and rarely disclosed (Geddes/Adalysis, 2018). On Smart Bidding, skip to step 4; the setting is cosmetic.
2. **Manual / Enhanced CPC and actively testing → "Do not optimize".** Optimize is tuned for clicks per auction (Google Help), and in Geddes's data it gave an ad that led on CTR, CVR and conversions per impression roughly 20× fewer impressions than a weaker ad, starved new ads (82 impressions in 7 days vs 2,000+ for the incumbent) or over-served them regardless of results, and sided with the CTR leader when CTR and conversions disagreed (Geddes/Adalysis, 2018). A test under Optimize measures Google's preference, not the ads.
3. **Manual / Enhanced CPC and not testing → Optimize is acceptable.** Its occasional good calls beat doing nothing when no one is reading the results (Geddes/Adalysis, 2018). Switch back to "Do not optimize" the week a test starts and keep it there until new ads have accumulated enough data to judge (Geddes/Adalysis, 2018).
4. **Smart Bidding campaigns: move the test out of rotation.** Because serving is Optimize and Google "often falls back on CTR for ad serving" (Geddes/Adalysis, 2026), control the comparison instead of the rotation:
   - Run two enabled RSAs per ad group during a test (a third only as a dated test arm with an end condition, per skill 31) and one or two outside it; with four or five or more ads Geddes found serving looked random rather than performance-driven (Geddes/Adalysis, 2018). The two-ad default is Epiminds' operating rule built on that finding and on Optmyzr's 2022 finding that two RSAs lifted conversion rate where one or three did not.
   - Make the two RSAs differ in one pinned element (headline 1 or the description) so the variable is fixed rather than shuffled; in 5,900+ accounts pinned ads traded CTR for higher conversion rate and higher conversions per 1,000 impressions, with the caveat that heavily pinned ads were also the most actively tested (Geddes/Adalysis, 2026).
   - Judge on conversions per impression, not CTR, because CTR is what the serving already optimises for (Geddes/Adalysis, 2018).
   - Use Ad variations experiments for copy changes that span many ad groups. Epiminds operating rule — no canon source; reason: with rotation overridden on Smart Bidding (Google Help; Geddes/Adalysis, 2018), an experiment's traffic split is the remaining serving control available to the advertiser, but no dossier source tests how well it is honoured.
5. **Turn off the "optimized ad rotation" auto-apply item** with the rest of AAR (see skill 88); otherwise step 2's setting is silently reverted (Google Help lists it as an AAR item).
6. **Takeover audit.** Any Manual/ECPC campaign on Optimize with more than two enabled RSAs per ad group and an open test is a broken test; reset to "Do not optimize", prune to the two contenders, restart the clock.

Output: per campaign, `rotation: n/a (Smart Bidding)` or `Do not optimize — test <name>, started <date>` or `Optimize — no test`; per testing ad group, the two RSAs and the pinned variable.

## What Google will tell you instead, and why we don't
Google does not recommend "Do not optimize" for most advertisers, says ad quality will make serving uneven anyway, and offers optimized rotation as an auto-apply recommendation (Google Help). The uneven-serving warning is true and irrelevant to a test: the test needs *comparable* exposure, not equal exposure, and Optimize removes comparability by picking the click winner (Geddes/Adalysis, 2018). On Smart Bidding the recommendation is moot because Google already overrides the setting (Google Help; Geddes/Adalysis, 2018).

## Failure modes
- **Low-traffic ad groups** (under a few hundred impressions a week — Epiminds operating approximation, no canon threshold): "Do not optimize" cannot reach significance either; Geddes flagged a non-significant CTR gap even in his examples (2018). Consolidate ad groups before testing.
- **Brand campaigns**: CTR and conversion winners usually coincide; Optimize is fine and the pinned-variant method adds nothing.
- **Accounts on Manual CPC solely for rotation control**: do not keep a campaign off Smart Bidding to preserve "Do not optimize". Epiminds judgment — no canon source compares the two; Geddes (2018) only notes advertisers who dropped Smart Bidding because Optimize worsened results.
- **Single-RSA ad groups** with Ad Strength pressure: the two-RSA rule conflicts with reps pushing one "Excellent" RSA; hold the two-ad structure only during a dated test.
- **Shopping and Display**: the setting exists but the substitute instruments (pins, Ad variations) do not apply.

## What to measure
- Impression split between the two test RSAs in the first 7 days (Geddes's starvation symptom was an 82 vs 2,000+ split).
- Conversions per 1,000 impressions per RSA, the metric Geddes uses for the verdict (2018, 2026).
- AAR History: zero "optimized ad rotation" applications.
- Count of Manual/ECPC campaigns on Optimize with a live test (target zero).

## Open disagreements in the canon
Only one Tier 1 practitioner — Geddes — publishes on rotation; the opposing position (optimized rotation is safe to auto-apply) comes from non-canon sources and Google. Within Geddes's own material the tension is between "Optimize is acceptable when not testing" (2018) and "Optimize shows the worst ads" (2019); Epiminds resolves it by the test flag: Optimize only when no test is live. The two-RSA cap and the pinned-variable method extend his findings into an operating rule and should be revisited if Optmyzr's RSA-count study or PPC Mastery's testing material contradicts them.
