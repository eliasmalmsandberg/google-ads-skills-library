# Dossier — 71 Budget pacing script

## Sources

1. **Source**: Nils Rooijmans, "Monthly Budget Target Email Alert" script — https://nilsrooijmans.com/google-ads-script-monthly-budget-target-email-alert/ (fetched) · **Tier** 1 · **Date** pub 2022-06-14, mod 2025-05-09, v1.0 · **Claim**: One GAQL query for account cost DURING THIS_MONTH; if month-to-date cost > MONTHLY_BUDGET, email "[GAds Script Alert] Monthly budget depleted" and pause campaigns manually. Built because campaign selectors do not report cost for Local, Discovery, PMax and Demand Gen, so older campaign-iterator budget scripts miss spend. Run hourly. · **Evidence**: Published script. Fetch noted a code issue: the loop overwrites `adSpend` per daily row, so the total may be only the last row — verify against the UI.

2. **Source**: Nils Rooijmans, "Daily Budget Overdelivery Alerts" script — https://nilsrooijmans.com/daily-budget-overdelivery-alerts-script/ (fetched) · **Tier** 1 · **Date** pub 2017-10-10, mod 2025-05-09 · **Claim**: Per enabled campaign (skip label "noBudgetAlert"): yesterday's cost vs daily budget (threshold 20%), last 7 days vs 7× budget on Mondays (10%), last 28 days vs 28× budget on first Monday of month (5%); log to sheet, mark red, email. firstRun flag. · **Evidence**: Published script with thresholds.

3. **Source**: Nils Rooijmans, "Do you want to prevent Google from spending 2x your daily budget?" — https://nilsrooijmans.com/daily/do-you-want-to-prevent-google-from-spending-2x-your-daily-budget (fetched) · **Tier** 1 · **Date** 2022-01-24 (mod 2024-04-29) · **Claim**: Script fetches each active campaign's daily budget and today's cost; if cost > budget × (1 + allowed overdelivery %), label and pause; re-enable needs a separate rule or script; does not work with shared budgets; Shopping and Video need modification. Overdelivery (2× daily) introduced 2017 makes budget control "annoying as hell" for budget-limited clients. · **Evidence**: Published script; opinion on Google.

4. **Source**: Nils Rooijmans, "your daily budget is… not really your daily budget?" — https://nilsrooijmans.com/daily/your-daily-budget-is-not-really-your-daily-budget (fetched) · **Tier** 1 · **Date** 2024-10-14 · **Claim**: Daily limit is 2× average daily budget; monthly limit is 30.4× daily budget; raising the daily budget mid-month raises the monthly cap (example $500→$750 with 17 days left → $17,750 max); ad schedules do not reduce the monthly target — to cap $2,000 over 20 weekdays set daily = 2,000/30.4 = $65.79; automate monitoring with the two scripts above. · **Evidence**: Worked arithmetic from Google's rules.

5. **Source**: Mari Breilin, Optmyzr blog, "Never Blow Your PPC Budget Again" — https://www.optmyzr.com/blog/manage-ppc-budgets/ (fetched) · **Tier** 1 outlet, vendor-authored (cite for thresholds only) · **Date** 2026-09-06 · **Claim**: Example rules: pacing >120% → reduce daily budgets; <80% → notify underpacing; >140% monthly pacing → cut campaign daily budget; Spend Projection uses recent performance, seasonality and day-of-week to give expected/min/max; named scripts "Pause When Things Spend Too Much" (spend caps at several levels) and "Reach Target Monthly Spend" (day-of-week weighting / front-loading); Google's flexibility can put an account over budget within the first five days. · **Evidence**: Illustrative examples; no data.

6. **Source**: Frederick Vallaeys, Optmyzr, "Advertisers Still Make 1 in 10 Google Ads Changes by Hand" — https://www.optmyzr.com/blog/google-ads-manual-work-study/ (fetched) · **Tier** 1 · **Date** 2026-09-16 · **Claim**: 72,358 accounts, Feb–Jul 2026, 578M changes; budgets are 1% of manual volume but the most repeated manual task: 130,800 sessions across 20,141 accounts. · **Evidence**: Cross-account study.

## Dissenting view
Rooijmans's monthly script is a hard threshold (alert when spent > budget) and his overdelivery script measures against Google's own daily budget; Optmyzr's model projects end-of-month spend and alerts at 80/120% of pace. The disagreement is whether pacing alerts should fire on projection (earlier, more false alarms with day-of-week swings) or on actual breach (later, certain). Rooijmans also argues for pausing campaigns by script to defeat 2× overdelivery; Optmyzr's "Reach Target Monthly Spend" instead reshapes daily budgets so overdelivery is absorbed.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] A campaign may spend up to 2× its average daily budget on any day (since Oct 2017), and no more than 30.4× the average daily budget in a calendar month; the monthly cap is recomputed on budget changes (Rooijmans 2024 gives the arithmetic); accelerated delivery was removed in 2019; the Scripts campaign iterator does not expose cost for PMax/Demand Gen/Local (Rooijmans 2022), so GAQL `campaign` resource reports are required.

## Baseline check
Read `google-ads-budget-management` (pacing formula, run-rate projection) and `google-ads-scripts` (a generic pacing script with a 20% threshold, no source). This skill adds: the GAQL-only requirement for PMax/Demand Gen cost, Rooijmans's 20/10/5% daily/weekly/4-weekly thresholds, the 30.4× monthly-cap arithmetic that pacing must respect, the pause-and-label pattern against overdelivery and the Optmyzr 80/120/140% projection bands.

## Judgment calls
- No single "canonical" pacing script exists in the canon; the skill names Rooijmans's three as the free canonical set and Optmyzr's two as the tool alternative.
- Optmyzr's thresholds are vendor examples; used as the projection bands because nothing else in the canon gives projection bands, and flagged as such.
- The bug noted in Rooijmans's monthly script is reported so the operator verifies totals rather than trusting one run.

## Canon strength: Adequate
Rooijmans is the only Tier 1 practitioner with published pacing scripts; Optmyzr supplies thresholds without evidence and one cross-account datum.

## Invalidated by
Google changing the 2×-daily / 30.4×-monthly overdelivery rules or introducing true monthly budgets for all campaign types; Scripts exposing cost for PMax/Demand Gen via the campaign iterator (makes the GAQL note moot); `change_event`/GAQL version sunsets.
