---
name: anomaly-detector-script
id: 72
description: Set up the two-layer anomaly alerting the canon actually runs — Google's Account Anomaly Detector for volume (impressions/clicks/cost, hourly) and Mike Rhodes's Search Term Watchdog for conversions on the top-spending terms (7 days vs a 13-week baseline) — plus Rooijmans's change-history and high-bid guards for the causes. For any account with steady conversion volume. Not a diagnosis playbook (what to do once alerted belongs to the anomaly-diagnosis skill), not for accounts under ~2 conversions a week per monitored unit.
tags: Script / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Deprecation of search_term_view or change_event in Scripts; Scripts frequency or runtime limits changing; Google removing or re-pinning the Account Anomaly Detector solution.
---
## What this is
Two detectors and two guards. The detectors: Google's Account Anomaly Detector (reference; compares today-so-far with the same weekday's history for impressions, clicks, cost) [Google docs, unverified], and Rhodes's Search Term Watchdog, which takes the TOP_N (default 100) search terms by cost, compares conversions in the last 7 full days with the weekly average of the 13 weeks before, and raises YELLOW when current ÷ baseline ≤ 20% and RED when current = 0 — but only for terms whose baseline averages more than 2 conversions a week (Rhodes, 2025). The guards: Rooijmans's change-history alert (any change by a user not on the approved list, daily) and high-CPC-bid alert (manual-CPC keyword bid above a threshold, default 5.00, hourly) (Rooijmans, 2019–2023). Rooijmans's own agency runs KPI anomaly alerts at daily, weekly and monthly cadence on impressions, clicks, cost, conversions, CVR, cost/conv and ROAS, with an account-offline alert by email and SMS (Rooijmans, 2023).
See also: skill 74 (negative-keyword-conflict-script) — the conflict script the watchdog is paired with, so a bad negative list is caught by logic as well as damage.

## Where it comes from
The watchdog thresholds and their revision history are published by Rhodes (2025): his first draft alerted on 50%/80% drops in impressions and conversions and was rewritten because 0→0 and 0→1 on low-volume terms generated noise, hence the 2-conversion floor and conversion-only rules. Rooijmans supplies the cadence model and the guards (2019–2025), including the December 2025 case where a client's tool rewrote tracking templates on a Saturday and the change-history alert caught it before Smart Bidding "went haywire" (Rooijmans, 2025). The API-version trap is from Rooijmans's FAQ (undated).

## When to use it / when not to
Use when: the account has terms or campaigns averaging more than 2 conversions a week (the watchdog's floor — Rhodes, 2025); several people or tools can change the account; Smart Bidding depends on imported conversions (Rooijmans, 2025).

Do not use the watchdog when: no monitored unit clears 2 conversions a week — every term is "OK" by design (Rhodes, 2025); run only the volume detector and the guards. Do not run the high-bid alert on Smart Bidding campaigns; it only reads manual-CPC campaigns (Rooijmans, 2019).

## Inputs
- Email address (required; the watchdog refuses to run without one) and optional sheet URL — it auto-creates a sheet (Rhodes, 2025).
- `TOP_N` 100, `CAMP_TYPE` SEARCH / SHOPPING / BOTH, `AGGREGATION` ACCOUNT or CAMPAIGN, `MIN_AVG_CONV_FOR_ALERT` 2, `PERCENT_THRESHOLD` 20, `EMAIL_ALERT_TRIGGER` RED_ONLY, `TESTING_MODE` true until verified (Rhodes, 2025).
- Approved-user email list and sheet for the change-history script; `PERIOD` YESTERDAY (Rooijmans, 2023).
- `CPC_THRESHOLD` and optional campaign label for the bid alert (Rooijmans, 2019).
- For the Account Anomaly Detector: remove or comment out the pinned `'apiVersion'` line before first run (Rooijmans, FAQ).

## Method
1. **Volume layer, hourly.** Install Google's Account Anomaly Detector as the "account went dark / spend doubled" alarm. First edit: comment out `'apiVersion': 'v10'` (or whatever is pinned) so it uses the current version; otherwise it dies with `MutateError.UNSPECIFIED` at the next sunset (Rooijmans, FAQ). Treat its alerts as volume signals only.
2. **Conversion layer, daily.** Install the Search Term Watchdog with defaults; leave `TESTING_MODE` true for the first week so you see the full table, then set false and `RED_ONLY` (Rhodes, 2025). Rules it applies: baseline avg ≤2 conv/week → OK; current 0 with baseline >2 → RED; current ÷ baseline ≤0.20 → YELLOW (Rhodes, 2025). Use `AGGREGATION = 'CAMPAIGN'` when the same term converts in brand and non-brand, so a brand-campaign collapse is not masked by non-brand (Rhodes, 2025 revision log).
3. **Read a RED.** A RED on a term that was converting weekly means a block or a break, not a market move: in order, check negatives added in the last 7 days (the script's origin case was a too-broad negative list blocking brand and converting terms — Rhodes, 2025), ads disapproved (skill 75), landing page or tracking changes (step 4), then budget.
4. **Cause guard: change history, daily.** Rooijmans's script lists every `change_event` by a user not in IGNORE_USERS, including Google's system users and third-party tools (Rooijmans, 2023). Any tracking-template, conversion-action or negative-list change by an unlisted user is escalated the same day; the 2025 case shows the stake: broken OCI and Smart Bidding on bad data (Rooijmans, 2025).
5. **Cause guard: bids, hourly.** On manual-CPC campaigns, alert on any keyword bid above the account's ceiling (Rooijmans's default 5.00; his trigger case was 1.90 typed as 19) (Rooijmans, 2019).
6. **Cadence stack.** Mirror Rooijmans's three cadences for the KPI set (impressions, clicks, cost, conversions, CVR, cost/conv, ROAS): daily for cost and conversions, weekly for CVR and cost/conv, monthly for ROAS (Rooijmans, 2023 names the cadences and KPIs; the mapping of KPI to cadence is ours, chosen so that ratio metrics get enough volume).
7. **Offline alert.** Add an account-offline check (declined card, depleted budget) with SMS, since a dark account is the one anomaly the conversion layer cannot see until the next day (Rooijmans, 2023).
8. **Maintenance.** Quarterly: run each script in Preview; any `apiVersion` error → remove the pin (Rooijmans, FAQ). Re-check `TOP_N` after structural changes so the watchdog follows the new top spenders.

## What Google will tell you instead, and why we don't
Google's built-in route is automated-rule notifications per campaign and the Account Anomaly Detector solution, both volume-based (impressions, clicks, cost) [Google docs, unverified]. Volume alerts miss the expensive failures: a too-broad negative list leaves impressions and cost roughly intact while conversions on the terms that mattered go to zero (Rhodes, 2025 origin case), and a tracking-template rewrite shows no volume change at all until Smart Bidding has already re-optimised (Rooijmans, 2025). Google's solution script also ships with a pinned API version that eventually breaks it (Rooijmans, FAQ). We keep Google's detector as the first layer and put conversion and change-history monitoring on top.

## Failure modes
- **Low-volume accounts** (no unit above 2 conv/week): the watchdog is silent by design (Rhodes, 2025); rely on the volume layer and guards, and extend the window rather than lowering the floor.
- **Seasonal businesses**: a 13-week baseline straddling the season end produces REDs in the off-season (Rhodes's baseline window, 2025); pause the watchdog or set `TOP_N` to the off-season term set.
- **Shopping-heavy accounts**: `CAMP_TYPE = 'BOTH'` mixes product queries that churn weekly; monitor Shopping terms at campaign aggregation only.
- **Agencies running many Automated Rules**: change-history alerts are flooded by "Bulk Actions"; whitelist it only after reviewing the rules (Rooijmans, 2023).
- **Accounts with 10k+ daily changes**: the change-history query caps at 9,999 rows and truncates (Rooijmans, 2023).
- **Copied scripts**: pinned API versions sunset (Rooijmans, FAQ).

## What to measure
- Alerts per week by layer (volume / conversion / change-history / bid) and the share that led to a revert or fix.
- Time from change to alert, for change-history alerts (target: next-day, the script's window).
- RED alerts that were true positives vs seasonal or structural (feeds the baseline-window decision).
- Script failures per quarter (API pins, sheet access).

## Open disagreements in the canon
Rhodes monitors conversions on top spenders and ignores volume metrics on low-volume units; Google's detector and Rooijmans's agency stack monitor volume metrics too. Epiminds runs both layers but routes decisions from the conversion layer: a volume alert without a conversion alert is checked once and closed; a conversion RED is worked through steps 3–5. Neither practitioner has published false-positive rates for their thresholds, so the 20% / 2-conversion settings are Rhodes's tested defaults, not measured optima — log true/false positives for a quarter before changing them.
