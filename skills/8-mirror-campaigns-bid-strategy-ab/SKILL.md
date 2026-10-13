---
name: mirror-campaigns-bid-strategy-ab
id: 8
description: Choose how to compare two bid strategies on an established Search campaign — custom experiment, mirror (duplicate) campaign, or scoped before/after — and run the chosen one so the result is readable. Not for ad copy tests (see Adalysis ad-testing method) and not for Shopping/PMax structure tests.
tags: Strategy / Search / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Custom experiments extended to Shopping/PMax and shared budgets; experiments syncing base-campaign changes; a Smart Bidding learning change that removes the 2–3-week stabilisation.
---
## What this is
There is no universally best bidding strategy — across 14,584 accounts the winner depended on execution and conversion volume, and 48% of advertisers already run more than one strategy in an account (Hopkins/Optmyzr, 2024). So strategy choice is tested, not assumed. The question is the vehicle. Google's custom experiment is the default; a mirror campaign is the fallback only where the tool cannot run; a scoped before/after inside one campaign is the canon's preferred way to test campaign-level automation when neither fits (Geddes/Adalysis, 2026).

## Where it comes from
Optmyzr's bidding study for the volume floor, stabilisation window and "no best strategy" finding (Hopkins, 2024, reported in Search Engine Land 2024); Geddes's scoped-test design for AI Max and his "combine across units" testing principle (Adalysis, 2026, two posts); Vallaeys/Walker's 30-per-campaign floor (Optmyzr Town Hall, 2025); Google's experiment mechanics (answer 6261395); Lolk's warning on split-campaign data loss (Optmyzr Town Hall, 2025, not canon) and Adchieve's note that structure changes cannot be tested in the tool (2021, vendor).

## When to use it / when not to
Use when: a strategy change is proposed on a campaign with ≥60 conversions/30 days, so each 50% arm clears the 30-per-campaign floor (Vallaeys/Walker, 2025); or the campaign is Shopping / on a shared budget, where the tool is unavailable (answer 6261395) and the only options are mirror or before/after.

Do not use when: the campaign is under ~60 conversions/30 days — both arms land in the band where no strategy is predictably successful (Hopkins/Optmyzr, 2024), and a mirror halves the data again (Lolk, 2025, not canon); the change is a whole-structure rebuild — the tool cannot test it and a before/after on equal periods is the honest method (Adchieve, 2021); tracking is not trustworthy — Geddes's first prerequisite for any automation test (Geddes, 2026).

## Inputs
- Conversions/30 days, cost, CPA/ROAS for the campaign (90 days).
- Budget type (individual vs shared), campaign type (Search vs Shopping), budget-lost impression share.
- Proposed strategy pair and targets; current learning status.
- Planned changes in the test window (promotions, budget moves) — these must be frozen.

## Method
1. **Prerequisites** (Geddes, 2026): accurate conversion tracking; the campaign already on a conversion-based automated strategy if the test is about targets; no significant budget-lost IS (a budget-limited arm is a budget test, not a bidding test).
2. **Pick the vehicle.**
   a. **Custom experiment** if Search, individual budget, and ≥60 conversions/30 days (so 30 per arm; Vallaeys/Walker, 2025). Shopping and shared-budget campaigns are excluded by the tool (answer 6261395).
   b. **Scoped in-campaign test** if the change can be scoped to ad groups (AI Max can be disabled per ad group): enable it on a few high-conversion non-brand ad groups in a campaign with ≥30 conversions/month and compare to the untouched ad groups over the same period (Geddes, 2026).
   c. **Mirror campaign** only if neither a nor b is possible (e.g. Standard Shopping bid strategy comparison). Accept that conversions are not shared and the bidder learns from half the data in each (Lolk, 2025, not canon); mirror everything — products/keywords, negatives, schedule, geo — and use separate equal budgets.
   d. **Before/after** for whole-structure changes: equal-length periods, exclude seasonal windows, same products/keywords (Adchieve, 2021).
3. **Split and budget** (experiment): cookie-based split for user-level cleanliness; search-based when you need significance faster and accept that one user may see both arms (answer 6261395). 50% budget split (answer 6261395). Keep any bid cap within ~10% of daily budget so the arm gets enough clicks (Hopkins/Optmyzr, 2024).
4. **Freeze.** No changes to the base campaign during the run — they are not mirrored into the experiment and make results uninterpretable (answer 6261395). No budget or goal changes in either arm (Hopkins/Optmyzr, 2024).
5. **Duration.** Discard the first 2–3 weeks as stabilisation after the strategy switch (Hopkins/Optmyzr, 2024), then run until each arm has ≥30 conversions in the measured window (Vallaeys/Walker, 2025) — in practice 4–6 weeks for a 60/month campaign. One experiment per campaign at a time (answer 6261395).
6. **Read it like an ad test, not a single number.** Compare CPA/ROAS and volume per arm; for scoped tests, combine the treated ad groups and the control ad groups as two labelled sets rather than reading each ad group alone (Geddes, 2026). Do not declare on a target that merely "looks" better — targets more often hurt than helped in the study, so a lower CPA with collapsed volume is a loss (Hopkins/Optmyzr, 2024).
7. **Decide and apply.** Apply the experiment to the original or convert it to a new campaign (answer 6261395). For mirrors, pause the loser and move its budget — never run both on; that is a permanent split with the data cost Lolk describes (2025, not canon).
8. **Output**: the vehicle chosen and why (2a–d); the frozen settings; start date, stabilisation cut-off, planned read date; per-arm conversions, CPA/ROAS, volume; the decision.

## What Google will tell you instead, and why we don't
- Google's UI pushes one-click bid-strategy recommendations and "apply" without a test. The 14,584-account study found no universal winner and that targets more often hurt (Hopkins/Optmyzr, 2024); we test.
- Google's experiment tool reports a winner with its own significance read and no stated threshold (answer 6261395). We hold the volume floor (30 per arm) and the stabilisation discard before reading anything.
- Google's structure guidance discourages splits; for Shopping and shared-budget campaigns Google offers no test vehicle at all (answer 6261395), so a time-boxed mirror is the only honest option there.

## Failure modes
- **Campaigns under 60 conversions/30 days**: both arms in the unpredictable band (Hopkins/Optmyzr, 2024). Test at account level with a portfolio change and before/after instead.
- **Seasonal retail windows**: before/after and even experiments mislead across promo periods; Adchieve excluded seasonal accounts for this reason (2021).
- **Mirrors left running**: become a permanent split that cannot share conversions or budgets (Lolk, 2025, not canon).
- **Search-based splits on long consideration cycles**: one user sees both arms, contaminating conversion attribution (answer 6261395); use cookie-based.
- **Base-campaign edits mid-test**: not mirrored; results unreadable (answer 6261395).
- **Budget-limited arms**: you are testing budgets (Geddes, 2026 prerequisite).

## What to measure
- Per-arm conversions in the measured window vs the 30 floor (Vallaeys/Walker, 2025).
- CPA/ROAS and conversion volume per arm after the 2–3-week discard (Hopkins/Optmyzr, 2024).
- Budget-lost IS per arm (should be ~0; Geddes, 2026).
- For scoped tests: search terms, auto-created assets and URL expansion on the treated ad groups (Geddes, 2026).
- Days since last base-campaign change (must exceed test start).

## Open disagreements in the canon
- **Whether mirrors are ever acceptable.** Lolk (2025) and Google's structure guidance say never split; Adchieve (2021) and the tool's own exclusions force it for Shopping/structure. Epiminds allows time-boxed mirrors only under 2c and pauses the loser.
- **Experiment tool vs scoped in-campaign test.** Google's tool is the default; Geddes (2026) tests AI Max by ad-group scope instead. Epiminds uses the tool for bid-strategy pairs and Geddes's scope for campaign-level automation features.
- **How long.** Google gives no duration; Hopkins gives 2–3 weeks to stabilise; the 30-per-arm floor is derived from Vallaeys/Walker. Epiminds uses discard-then-30-per-arm.
