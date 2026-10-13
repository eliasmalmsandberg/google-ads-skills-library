---
name: custom-experiments-split-duration-valid-win
id: 79
description: How to set up, size and call a Google Ads custom experiment (bid strategy, structure, match type, landing page) so the result is a decision, not a confidence label. Not for RSA asset tests (see 82) or incrementality/geo lift (see 80, 81).
tags: Technique / Search / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Changes to the 7-day ramp-up exclusion, the 80% default confidence display, budget-vs-traffic split rules per campaign type, or replacement of custom experiments by Google-recommended / multi-campaign experiments only.
---
## What this is
A decision procedure for custom experiments: what to test in one, how to split, how long to pre-commit, what to freeze during the run, and the rule for calling a winner. The core position: the experiment window is set from conversion lag before launch and the readout metric is pre-registered; the UI's "significant" / "inconclusive" label is an input, not the verdict.

## Where it comes from
Rooijmans' duration rule (≥6× median conversion lag and ≥14 days, synced, untouched) (Rooijmans, 2024); Vallaeys' three experiment pitfalls — the control arm reacts to the trial, broken tracking masquerades as a losing strategy, aggregate results hide query-level wins (Vallaeys/SEL, 2019); Optmyzr on base-campaign edits polluting a running trial and how per-metric confidence is computed (Optmyzr, 2021/2026); Meyerson's 54-experiment lead-gen series on run length and bid-strategy outcomes (Meyerson/SEL, c.2024); Bowman's six-account 50/50 broad-match series on Google's "inconclusive" labels (Bowman, 2026); Stemen on back-end readout and interface incompatibilities (Stemen/SEJ, 2026). Platform mechanics from Google Ads Help, labelled.

## When to use it / when not to
Use for any change that alters bidding, targeting breadth, structure or landing page in a Search campaign with ≥30–50 conversions in the last 30 days (Stemen/SEJ, 2026; Google VBB guidance says ≥50 for value tests [Google docs]). Use when the change is reversible and the client needs evidence before rollout.

Do not use for: campaigns on a portfolio bid strategy or shared budget (the experiment interface does not handle them cleanly; move the campaign to its own strategy and budget first) (Stemen/SEJ, 2026); campaigns under ~30 conversions/30 days, where a 50/50 split starves both arms (Stemen/SEJ, 2026); testing more than one variable at a time; anything you would not actually roll out if it won.

## Inputs
- Median conversion lag for the campaign (Report Editor, conversions by days-to-conversion) (Rooijmans, 2024).
- Conversions last 30 days, and conversion value if testing value bidding.
- The single primary metric and the back-end metric that validates it (MQL/SQL/closed-won for lead gen) (Stemen/SEJ, 2026; Meyerson/SEL, c.2024).
- Confirmation that the campaign is on its own budget and its own bid strategy.
- A change log freeze agreement with whoever else touches the account (Optmyzr, 2021).

## Method
0. **Gate on tracking.** Confirm the primary conversion action fired correctly for the previous 30 days and covers upper-funnel keywords; Vallaeys' client "lost" a tCPA test because untracked upper-funnel keywords were starved by Smart Bidding, not because tCPA was worse (Vallaeys/SEL, 2019).
1. **Pre-register.** Write the hypothesis, the one variable changed, the primary metric (CPA or ROAS, plus conversion volume), the back-end validation metric, and the end date. Meyerson evaluated every test on CVR, conversion volume and CPA together, never on one alone (Meyerson/SEL, c.2024).
2. **Set the end date from lag, not from the calendar.** Duration = max(14 days, 6 × median conversion lag) (Rooijmans, 2024). For bid-strategy tests, add the 7–14 day learning phase on top (Stemen/SEJ, 2026). Google excludes the first 7 days from results automatically [Google docs]; for value-based bidding Google's own protocol excludes 14 days of ramp-up and then requires 30 more days [Google docs]. Meyerson's practical floor was 30 days, with most tests running over 2 months (Meyerson/SEL, c.2024). Epiminds floor: 30 days for any Smart Bidding change, regardless of the lag calculation.
3. **Split 50/50, cookie-based for landing-page or audience tests, search-based otherwise.** Cookie-based keeps one user in one arm; search-based is the default and suits low-volume campaigns [Google docs, 2018]. Never use a skewed split to "protect" performance: the split cannot be changed after creation, non-50/50 results are rescaled in reporting, and the smaller arm reaches significance later [Google docs, FAQs]. If the campaign cannot afford a 50/50 split, it cannot afford the experiment.
4. **Know what is actually being split.** Search experiments split *budget*, not traffic; the trial can spend up to 2× its daily budget on a day [Google docs, FAQs]. Pull "Served cost" vs "Billed cost" at the end so overdelivery credit does not flatter the trial CPA [Google docs, FAQs].
5. **Enable sync and freeze the base.** Sync so base-campaign edits carry into the trial (Rooijmans, 2024). Then make no edits to either arm for the whole window; Google does not warn you when a base edit has polluted the test (Optmyzr, 2021). If an unavoidable edit happens, log it and restart the clock.
6. **Turn auto-apply off before launch.** Auto-apply is on by default for some experiment types and applies the trial at the end date on Google's own threshold [Google docs, FAQs]. Our call is made against the pre-registered metric, not Google's.
7. **Do not read mid-window.** The scorecard defaults to an 80% confidence level, not 95% [Google docs]; early green at 80% is close to a coin flip with directionality. Rooijmans' fourth step is literally "wait" (Rooijmans, 2024).
8. **Call the result at the end date, in this order:**
   a. Raise the scorecard confidence to 95% via dynamic confidence reporting [Google docs].
   b. Exclude the last N days where <90% of conversions have reported (N from the lag report) [Google docs, VBB guidance].
   c. Primary metric moved in the right direction AND the 95% interval excludes zero AND conversion volume did not fall → **apply**.
   d. Primary metric moved ≥20% in the right direction, interval includes zero, volume held, and the back-end metric (lead quality, closed-won, conversion value by time) agrees → **apply, flagged as directional**. This is Bowman's call on three of six accounts where Google said "inconclusive" while cost/conversion fell 23–29% (Bowman, 2026). The ≥20% line is an Epiminds operating threshold — no canon source; reason: it sits below the smallest delta Bowman acted on (23%) and above the noise a 50/50 split produces in a 30-day window at our clients' volumes.
   e. Anything else → **do not apply**; extend only if the pre-registered window was shorter than 6× lag. Google's "run 2–3 more weeks" default [Google docs] is open-ended; ours is one extension, maximum.
9. **Check the control was not moved by the trial.** Pull impression share and avg CPC for the control arm across the window; a tCPA trial bidding aggressively can lift competitor bids and starve a manual-CPC control of impression share, which flatters the trial (Vallaeys/SEL, 2019). If control IS fell >10 points with no other cause, discount the relative lift and read absolute trial CPA against the pre-test baseline instead. The 10-point line is an Epiminds operating threshold — no canon source; reason: Google states IS is estimated daily and small moves are noise [Google docs], and 10 points over a 30-day window is beyond that noise in every account we have measured.
10. **Validate with back-end data before the permanent change.** Pull "Conversion value (by time)" rather than default columns, which book value to the click date (Stemen/SEJ, 2026). For lead gen, compare SQL rate per arm (Stemen/SEJ, 2026; Bowman, 2026).
11. **Read below the aggregate.** Join the search-term report to the ad report per arm; aggregate win/lose hides query-level results, and Vallaeys reports a brand query served the wrong ad until this join exposed it (Vallaeys/SEL, 2019).
12. **Log it.** Meyerson's finding that roughly half of tCPA-level tests fail (Meyerson/SEL, c.2024) is the reason a test log exists: the losers are the calibration data.

## What Google will tell you instead, and why we don't
- Google ships a default 80% confidence scorecard and suggests "2–3 more weeks" when there is no clear winner [Google docs]. We pre-commit the window from conversion lag (Rooijmans, 2024) and read at 95%, once.
- Google auto-applies favourable trials by default [Google docs, FAQs]. We switch it off: Google's favourable is not our pre-registered metric, and the trial CPA can be flattered by overdelivery (step 4).
- Google's "bids will stabilise" reassurance on Maximize Conversions: Meyerson ran those tests for three months and the bids did not come down (Meyerson/SEL, c.2024). Treat a MaxConv arm whose CPC is still rising at day 30 as a loss, not as "still learning".
- Google's recommended experiments (preconfigured, one-click) [SEL, 2026] default to Google's hypotheses (final URL expansion, broad match, AI Max). Run them through the same pre-registration; Bowman's series shows the same broad-match test winning in 3 accounts and losing ROAS by 60% in another (Bowman, 2026).

## Failure modes
- **Low-volume campaigns (<30 conv/30 days).** A 50/50 split halves the data each arm's bid strategy sees (Stemen/SEJ, 2026); both arms underperform the pre-test campaign and the comparison is meaningless. Use a before/after with a holdout period instead.
- **Long-cycle B2B (60–90 day lag).** 6× median lag can be a year. Use the lag of the earliest counted stage (e.g. MQL) for the window and validate closed-won later (Stemen/SEJ, 2026).
- **Portfolio strategies / shared budgets.** The experiment interface does not handle them (Stemen/SEJ, 2026); splitting one campaign out of a portfolio changes its bidding before the test starts.
- **Seasonal retail.** A window that straddles a peak measures the peak, not the variable. Do not launch an experiment that will end inside a known demand spike.
- **Value tests with few distinct values.** Google's own VBB protocol requires ≥2 distinct non-zero values and ≥50 conv/30 days [Google docs]; below that the ROAS readout is noise.
- **Broad-match / AI Max expansions in lead gen.** Volume rises while lead quality falls; CPL can improve while SQL rate collapses (Bowman, 2026). The back-end check in step 10 is mandatory for these.

## What to measure
Per arm, over the window minus ramp-up and minus the under-reported tail: conversions, CPA or ROAS, conversion value by time, CPC trend by week (rising CPC on a MaxConv arm is the failure signature; Meyerson/SEL, c.2024), served vs billed cost [Google docs], and the back-end quality metric. Record the 95% interval at the end date and the decision taken.

## Open disagreements in the canon
- **Acting on "inconclusive".** Bowman applies trials on large raw deltas plus business signal (Bowman, 2026); Rooijmans and Google's VBB protocol say wait the full window and do not read early (Rooijmans, 2024; [Google docs]). Epiminds: fixed window from lag (Rooijmans), then step 8d allows a flagged directional apply when volume held and the back-end agrees. Reason: in small accounts the interval will rarely exclude zero and refusing to act leaves known improvements on the table; the flag forces a re-check at 60 days.
- **Minimum run.** Rooijmans: 14 days floor; Meyerson: 30 days, most over 60; Google: 4–6 weeks. Epiminds takes 30 days as the floor for any bid-strategy change because the learning phase alone consumes 7–14 days (Stemen/SEJ, 2026).
