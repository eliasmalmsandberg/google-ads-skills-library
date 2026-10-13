# Dossier — 79 Custom experiments — split, duration, valid win

## Sources

1. **Source**: Nils Rooijmans, nilsrooijmans.com daily, "Step, Step, Step, Pause" — https://nilsrooijmans.com/daily/step-step-step-pause · **Tier** 1 · **Date** 2024-12-06 · **Claim**: Bid-strategy tests belong in a campaign experiment, synced with the base campaign, scheduled for at least 6× the median conversion lag AND at least 14 days, then left alone — no mid-test edits. · **Evidence or opinion**: Practitioner method (his standing rule); no account data in the post.

2. **Source**: Aayushi Bhandari (Optmyzr product), optmyzr.com/blog, "Campaign Experiments by Optmyzr" — https://www.optmyzr.com/blog/google-ads-campaign-experiments/ · **Tier** 1 (Optmyzr) · **Date** 2021-10-26, updated 2026-03-02 · **Claim**: Native Google Ads only shows that an experiment exists on a campaign and does not warn when later edits to the base campaign pollute the test; confidence is computed per metric (CTR, CVR, conv/imp, revenue/cost, CPA) by comparing trial vs. base, green = positive, red = negative. Apply options: update original, convert trial to a new campaign (same budget as original), or end. · **Evidence or opinion**: Tool behaviour description; opinion on pollution.

3. **Source**: Mark Meyerson (One Egg Digital), Search Engine Land, "What 54 Google Ads experiments taught me about lead gen" — https://searchengineland.com/google-ads-experiments-lead-gen-446088 · **Tier** added-Tier-2 (passes inclusion for this topic: publishes method, 54 experiments over two years in one account, and contradicts Google's "bids will stabilise" line) · **Date** page undated; ~2024 · **Claim**: Minimum run 30 days, most ran >2 months, many >3 months; evaluate on CVR, conversion volume and CPA (CTR added for copy tests). tCPA beat Maximize Conversions in every head-to-head; MaxConv beat manual; MaxConv pushed bids up and did not come down over 3-month tests despite Google saying they would stabilise; roughly half of tCPA-level tests failed; exact beat phrase on CPA and CVR at similar volume. · **Evidence or opinion**: Single-account series (54 tests) — directional evidence, no significance figures reported.

4. **Source**: Ryan Bowman (Web Eminence), "Broad Match Keyword Experiments in Google Ads: Real 50/50 Test Results Across 6 Accounts" — https://webeminence.com/broad-match-keyword-experiments-in-google-ads-50-50-test/ · **Tier** added-Tier-2 (publishes split, duration, per-account numbers, and overrides Google's significance labels) · **Date** 2026-04-13 · **Claim**: 50/50 split, run ≥30 days; Google labelled 3 of 6 tests "inconclusive" even where cost/conv moved −29% and conversions +42% (~800 clicks, 30 days); author applied the trial anyway on the back of the raw delta and later lead quality. Warns that broad match adds volume and can lower lead quality, so judge on ROAS / sales feedback, not CPL. · **Evidence or opinion**: Six-account results with numbers; small samples.

5. **Source**: Sarah Stemen, Search Engine Journal, "How to test a new bid strategy in Google Ads" — https://www.searchenginejournal.com/how-to-test-a-new-bid-strategy-in-google-ads/571237/ · **Tier** 2 (not in canon; used only for the pitfalls list, which is method not opinion) · **Date** 2026-05-05 · **Claim**: Learning phase 7–14 days; splitting traffic can starve Smart Bidding of data; portfolio strategies and shared budgets don't work in the experiment interface; judge on back-end metrics (MQL/SQL/closed-won) and pull "Conversion value (by time)" in Report Editor, because default columns book value to the click date; trigger a bid-strategy test only at 30–50 conversions / 30 days. · **Evidence or opinion**: Method with one worked SaaS example.

6. **Source**: Frederick Vallaeys, Search Engine Land, "3 pitfalls of PPC experiments" — https://searchengineland.com/3-pitfalls-of-ppc-experiments-326332 · **Tier** 1 · **Date** 2019-12-11 · **Claim**: (1) The control arm is not inert: a tCPA trial bidding aggressively pushed competitors' bids up and the manual-CPC control lost impression share — read the wider auction, not just the two arms. (2) The experiment is not always the cause: a tCPA trial "lost" because broken conversion tracking starved upper-funnel keywords; fix measurement before testing Smart Bidding. (3) Aggregate win/lose hides query-level opportunity; join the query report with the ad report. · **Evidence or opinion**: Client anecdotes, no numbers.

7. **Source**: Google Ads Help, "Experiments FAQs" — https://support.google.com/google-ads/answer/13826584 ; "Monitor your experiments" — https://support.google.com/google-ads/answer/6318747 ; "Value-based bidding using campaign experiments" — https://support.google.com/google-ads/answer/14147337 ; "Experiment Center" — https://support.google.com/google-ads/answer/16856494 · **Tier** Reference only · **Date** 2025–2026 · see "What the platform currently does".

Pages searched for and not found: no Adalysis, PPC Mastery, Brainlabs or Mike Rhodes page specifically on custom-experiment design surfaced via search on 2026-10-13. Google's "statistical methodology behind experiments" page could not be located by URL; not cited.

## Dissenting view
Bowman (2026) acts on "inconclusive" results when the raw delta is large and the business signal agrees; Rooijmans (2024) and Google's VBB guidance both say wait the full scheduled window and do not read early. The disagreement is about whether the experiment UI's confidence label is the decision, or one input into it. We side with Rooijmans on duration (fixed window, pre-committed) and with Bowman on the label (the 80% default label is not the decision; the pre-registered metric at the pre-registered end date is).

## What the platform currently does [Google docs]
- Experiment Center launched Jan 2026, combining Experiments and Lift studies under Campaigns > Experiments [Google docs; SEL 2026-01-26].
- Search/App/some Display experiments split *budget*; PMax/Demand Gen/Video split *traffic*. Split cannot be changed after creation. Non-50/50 splits are scaled in reporting. [Google docs, FAQs]
- Trial campaigns may spend up to 2× daily budget in a day, capped at 30.4× monthly; compare "Served cost" vs "Billed cost" for overdelivery credit. [Google docs, FAQs]
- Google recommends 4–6 weeks, longer with conversion delay, 1–2 conversion cycles; first 7 days are excluded from results. For VBB experiments: 14-day ramp-up excluded, then ≥30 more days, 50/50, ≥50 conv/30 days, ≥2 distinct conversion values; exclude days where <90% of conversions have reported. [Google docs]
- Default confidence level shown is 80%; user can change via dynamic confidence reporting; blue asterisk = significant. "No clear winner" → Google suggests running 2–3 more weeks or raising budget. [Google docs, Monitor your experiments]
- Auto-apply is on by default for some experiment types; experiments ended manually are not applied; only those that reach their end date are. [Google docs, FAQs]
- Split option: search-based (default) vs cookie-based; cookie-based recommended for landing-page/audience tests. [Google docs 2018, answer 9051618]
- Multi-campaign Search experiments (budget and ROI target changes across several campaigns) rolling out Sept 2026 [SEJ 2026-08-24]. Recommended experiments (Google-suggested, preconfigured) added to the Experiments page, 2026 [SEL].

## Baseline check
Read `google-ads-experiments` (baseline). It gives generic MDE/sample-size maths, a 2-week minimum / 8-week maximum and "95% = act". This skill adds: the conversion-lag-based duration rule (6× median lag), the budget-split vs traffic-split distinction and the 2× overdelivery issue, the 80%-default-confidence trap, the "pollution by base-campaign edits" problem and sync rule, the back-end-metric and conversion-value-by-time readout, portfolio/shared-budget incompatibility, and documented practitioner outcomes (tCPA > MaxConv, MaxConv bids not stabilising).

## Judgment calls
- Added Meyerson and Bowman as dossier Tier 2 for this topic only; both publish method and numbers and both contradict Google (bid stabilisation; significance labels). Stemen is cited only for operational pitfalls.
- Canon lacks a Tier 1 page devoted to experiment design; the skill therefore leans on Rooijmans' duration rule and Optmyzr's pollution point as the Tier 1 spine.

## Canon strength: Adequate
Three Tier 1 sources (method, no cross-account data) plus two added Tier 2 sources with account numbers.

## Invalidated by
Changes to the experiment ramp-up exclusion (currently 7 days), the default confidence level (80%), the budget-vs-traffic split rules per campaign type, or removal of custom experiments in favour of Google-recommended/multi-campaign experiments only.
