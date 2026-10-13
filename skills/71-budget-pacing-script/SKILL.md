---
name: budget-pacing-script
id: 71
description: Install and tune the pacing scripts (Rooijmans's monthly-target alert, daily-overdelivery alert and pause-on-overspend script; Optmyzr's projection alerts as the tool alternative) so monthly budgets are policed hourly against Google's 2x-daily / 30.4x-monthly overdelivery rules. For any account with a fixed monthly budget. Not for budget allocation between campaigns, not for bid-strategy tuning.
tags: Script / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google changing the 2x-daily / 30.4x-monthly overdelivery rules or adding true monthly budgets to all campaign types; Scripts exposing cost for PMax/Demand Gen in the campaign iterator; GAQL version sunsets.
---
## What this is
Three scripts and one piece of arithmetic. (1) Monthly target alert: one GAQL query for account cost `DURING THIS_MONTH`; if cost exceeds `MONTHLY_BUDGET`, email "budget depleted" (Rooijmans, 2022). (2) Daily overdelivery alert: per campaign, yesterday's cost vs daily budget (20% tolerance), last 7 days vs 7× budget on Mondays (10%), last 28 days vs 28× budget on the first Monday (5%), logged to a sheet and emailed (Rooijmans, 2017). (3) Pause-on-overspend: if today's campaign cost exceeds daily budget × (1 + allowed overdelivery), label and pause; a separate rule re-enables (Rooijmans, 2022). The arithmetic: Google may spend 2× the daily budget on any day and up to 30.4× in the month; raising the daily budget mid-month raises the monthly cap; ad schedules do not lower it (Rooijmans, 2024).

## Where it comes from
Rooijmans's scripts (2017–2022, maintained 2025) and his overdelivery arithmetic (2024). Optmyzr's projection bands (80% / 120% / 140%) come from a vendor-authored how-to (Breilin/Optmyzr, 2026) and are the only projection thresholds in the canon. Vallaeys's 72,358-account study shows why this is scripted: budgets are the single most repeated manual task, 130,800 sessions across 20,141 accounts in six months (Vallaeys/Optmyzr, 2026).

## When to use it / when not to
Use when: the client has a monthly cap that must not be breached (budget-limited lead-gen, agencies on retainers, any account where the spend "belongs to a client" — Rooijmans, 2022); the account contains PMax, Demand Gen or Local campaigns, whose cost the Scripts campaign iterator does not return, so legacy pacing scripts silently under-count (Rooijmans, 2022).

Do not use pause-on-overspend when: campaigns share a budget (the script cannot handle shared budgets) or are Shopping/Video without modification (Rooijmans, 2022); when the client prefers hitting the monthly target over daily smoothness — use the budget-reshaping approach instead (Breilin/Optmyzr's "Reach Target Monthly Spend", 2026).

## Inputs
- Monthly budget per account (and per campaign group if the client has sub-budgets).
- Blank Google Sheet URL and alert emails (Rooijmans, 2017–2022).
- Label `noBudgetAlert` on campaigns to exclude from the overdelivery check (Rooijmans, 2017).
- Allowed overdelivery percentage for the pause script (no default published; set it from the client's tolerance) (Rooijmans, 2022).
- Day-of-week spend pattern if projecting (Breilin/Optmyzr, 2026).

## Method
1. **Set daily budgets from the monthly cap, not the reverse.** Daily = monthly ÷ 30.4; if ads run only on 20 weekdays, still divide by 30.4 — a $2,000 month on weekdays is $65.79/day, because the schedule does not lower Google's monthly target (Rooijmans, 2024).
2. **Install the monthly alert, hourly.** Use the GAQL `campaign`-resource cost query, not `AdsApp.campaigns()`, so PMax/Demand Gen spend is counted (Rooijmans, 2022). On first run, compare the script's month-to-date total with the UI: the published v1.0 loop overwrites the running total per daily row, so confirm the summation before trusting alerts (noted on fetch of Rooijmans, 2022).
3. **Install the overdelivery alert, daily.** Keep Rooijmans's tolerances: 20% daily, 10% weekly, 5% four-weekly (Rooijmans, 2017). A daily breach alone is Google's normal 2× behaviour; a weekly breach above 10% means the campaign is running above budget on average and the monthly cap will bind early; a four-weekly breach above 5% is Google exceeding its own 30.4× rule and goes to support.
4. **Add projection bands.** Pacing = month-to-date spend ÷ (monthly budget × days elapsed ÷ days in month). Below 80% → notify under-pacing; above 120% → reduce daily budgets; above 140% on a campaign → cut that campaign's daily budget (Breilin/Optmyzr, 2026). Weight by day-of-week where weekends differ (Breilin/Optmyzr, 2026). These are vendor example bands; tighten for clients with hard caps.
5. **Mid-month changes.** Before raising any daily budget, recompute the month's maximum: spend so far + new daily × 30.4 × (days left ÷ 30.4). Rooijmans's example: $500 → $750 with 17 days left raises the October maximum to $17,750 (Rooijmans, 2024). If that exceeds the cap, lower another campaign first.
6. **Hard caps only: pause script.** Where the client cannot tolerate the 2× day, run the pause script hourly with the agreed overdelivery percentage; it labels and pauses the campaign (Rooijmans, 2022). Pair it with an Automated Rule or second script that re-enables labelled campaigns at 00:00 account time — the pause script does not re-enable (Rooijmans, 2022). Never apply it to shared-budget campaigns (Rooijmans, 2022).
7. **End of month.** Under-pacing at day 25 is not fixed by tripling budgets — the 2× daily rule makes the maximum catch-up 2× daily × days left; set the realistic figure and tell the client (arithmetic from Rooijmans, 2024).
8. **Monthly review.** Pull the overdelivery sheet: campaigns with repeated weekly breaches get a lower daily budget; campaigns never near budget are candidates for reallocation (the "Limited by budget" decision belongs to skill 84/budget allocation, not here).

## What Google will tell you instead, and why we don't
Google's framing is that daily budgets are averages and the month is protected by the 30.4× rule, so overdelivery "evens out" [Google docs, unverified]. The canon's view is that this makes control of a client's money "annoying as hell" (Rooijmans, 2022) and that an account can be over budget within the first five days of a cycle (Breilin/Optmyzr, 2026); the daily budget "is not really your daily budget" (Rooijmans, 2024). Google's Recommendations tab only ever raises budgets (Cooney/PPC Hero, 2024 — skill 78). We script the cap ourselves and, for hard-cap clients, pause rather than trust the average.

## Failure modes
- **Shared budgets**: the pause script breaks and the per-campaign overdelivery arithmetic is wrong (Rooijmans, 2022); alert at account level only.
- **Smart Bidding campaigns paused by the overspend script**: Epiminds operating rule — no canon source; reason: the script's author built it for budget-limited clients and notes it needs a separate re-enable (Rooijmans, 2022), so on Smart Bidding we prefer budget reshaping (Breilin/Optmyzr, 2026) and keep the pause script for manual-CPC or contractually capped campaigns.
- **Accounts with PMax/Demand Gen** and a legacy iterator-based script: spend under-counted; the alert never fires (Rooijmans, 2022).
- **Strong weekday/weekend skew**: the 80/120% bands fire on Mondays; weight by day-of-week first (Breilin/Optmyzr, 2026).
- **Mid-month budget raises**: the cap moves with the raise; a pacing script that compares against the original monthly figure under-reports headroom (Rooijmans, 2024).
- **Promotions**: a 140% campaign-level breach is intended; label it `noBudgetAlert` for the period (Rooijmans, 2017).

## What to measure
- Month-end spend vs cap, per account (target: within the agreed tolerance, never over).
- Overdelivery breaches per month at daily / weekly / four-weekly levels.
- Number of pause events and hours paused, per campaign (pause script).
- Manual budget edits per month per account (Vallaeys/Optmyzr, 2026 benchmark: budgets are the most repeated manual task — the script should drive this toward zero).

## Open disagreements in the canon
Rooijmans alerts on actual breach and, for hard caps, pauses; Optmyzr projects and reshapes daily budgets. Epiminds runs both: projection bands for early warning (Breilin/Optmyzr, 2026), Rooijmans's breach alerts as the record of truth, and the pause script only where the client's cap is contractual. Nobody in the canon has published cross-account evidence on how often the 30.4× monthly rule is actually exceeded; Rooijmans's 5% four-weekly tolerance is the practitioner's answer and we keep it.
