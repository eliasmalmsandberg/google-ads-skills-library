---
name: ad-disapproval-alert-script
id: 75
description: Install Rooijmans's three policy scripts — Disapproved Ads, Past Violations ("STALE" topics Google never notifies on) and Disapproved Products — with the cadence and escalation a compliance-sensitive vertical needs. For pharma, finance, health, gambling, alcohol, anything where disapprovals are frequent and silent. Not for writing compliant ads, not for appeals strategy beyond the first appeal.
tags: Script / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Changes to ad_group_ad.policy_summary fields or policy topic naming; Shopping Content API deprecation in favour of the Merchant API; Google adding reliable notifications for past-violation and limited statuses.
---
## What this is
Three scripts. (1) Disapproved Ads: GAQL on `ad_group_ad` where `policy_summary.approval_status = DISAPPROVED`, campaign enabled and not ended, ad group and ad enabled, date TODAY; writes campaign, ad group, ad ID, ad type, status and the policy topics as a "Disapproval Reason"; emails only when at least one is found (Rooijmans, 2020; v2.0 2022). (2) Past Violations: same query, keeps ads whose policy topic contains "STALE" — ads Google leaves disapproved after the policy no longer applies, a status that "generates no notification" and yields zero impressions until appealed (Rooijmans, 2022). (3) Disapproved Products: products with clicks in the last 30 days whose Merchant Center "Shopping" destination status is disapproved, with the first issue, fix and documentation link, sorted by clicks (Rooijmans, 2022).
See also: skill 67 (merchant-center-diagnostics) — mapping disapproval patterns to causes, the suspension timers and migration pre-emption.

## Where it comes from
Rooijmans's three scripts (2020–2022, maintained 2025) and his own cases: a 2019 wave of "Malicious or unwanted software" disapprovals across accounts with no malware, three weeks and many support contacts to clear (Rooijmans, 2020); product disapprovals that "go unnoticed for weeks or even months" (Rooijmans, 2022). The change-history script (Rooijmans, 2023) is the companion for finding what triggered a wave.

## When to use it / when not to
Use when: the vertical draws policy reviews (health, finance, gambling, alcohol, political, adult-adjacent); ad tests run on few ads per group so one disapproval invalidates the test (Rooijmans, 2020); Shopping accounts of any size (silent product drops — Rooijmans, 2022).

Do not treat it as complete: the DISAPPROVED filter misses "Eligible (limited)" ads [Google docs, unverified]; the products script reports only the first item-level issue and has no history (Rooijmans, 2022); none of the three sends an all-clear, so a silent inbox is not proof of a run (Rooijmans, 2022).

## Inputs
- Blank Google Sheet URL and alert email (one address in the ads scripts; comma-separated in the products script) (Rooijmans, 2020–2022).
- Products script: `GMC_ID`, `MIN_CLICKS` 1, `PERIOD` LAST_30_DAYS, `ACCOUNT_NAME`; Shopping Content API enabled under Advanced APIs (Rooijmans, 2022).
- The appeal owner (who files, who approves copy changes) and the client's compliance contact.
- Approved-user list for the change-history script (Rooijmans, 2023).

## Method
1. **Install all three.** Daily at 07:00 account time; add an hourly schedule for the ads script during launches and the two weeks after any policy update in the vertical (Rooijmans suggests hourly or daily, 2020; the split is ours).
2. **Read the reason column.** Policy topics are names only, not explanations (Rooijmans, 2020). Map each topic to one of: (a) copy/asset fix needed; (b) destination/site fix needed; (c) certification or authorisation missing (pharma, finance); (d) false positive to appeal.
3. **Act within the day.** (a) and (b): fix and resubmit; pause the ad only if it is the sole ad in the group and the fix will take longer than a day. (c): the account cannot run that ad until certified; pause and escalate to the client. (d): appeal from the ad's status hover: Appeal → reason "changes made to comply" (even when none were, if Google's finding is wrong, state that in the appeal text) → Submit (appeal path from Rooijmans, 2022).
4. **Past violations are a weekly sweep.** Any "STALE" row is an ad with zero impressions that nobody was told about (Rooijmans, 2022). Appeal in bulk; re-enable; expect impressions to return (Rooijmans, 2022).
5. **Products: top-down by clicks.** Fix the highest-click products first; use the fix and documentation columns; confirm in Merchant Center; because only the first issue is listed, re-check the product after the first fix (Rooijmans, 2022).
6. **Waves.** If the ads script returns many rows at once, open the change-history sheet: new ads, final-URL or tracking-template changes by an unlisted user in the last 7 days explain most waves (Rooijmans, 2023). If there is no change, treat as a review-system wave and escalate to support with the full sheet — the 2019 case took three weeks (Rooijmans, 2020).
7. **Keep history.** The ads and products scripts clear the sheet each run (Rooijmans, 2020–2022); copy each day's rows to a log tab (or set `COPY_SPREADSHEET`-style archiving) so you can show the client how long an ad was dark.
8. **Verify the run.** Weekly, confirm "last run" in the Scripts list; none of the scripts sends an all-clear (Rooijmans, 2022).

## What Google will tell you instead, and why we don't
Google's route is notification emails and the Policy Manager [Google docs, unverified]. The canon's experience is that past-violation ("STALE") disapprovals generate no notification and sit at zero impressions (Rooijmans, 2022), product disapprovals sit unnoticed for weeks (Rooijmans, 2022), and automated review errors can disapprove whole accounts for malware that does not exist (Rooijmans, 2020). We do not rely on Google's notifications; we poll the policy fields daily and keep our own log. Google's "fix disapproved ads" auto-apply recommendation stays off (skill 78); copy changes are ours.

## Failure modes
- **Many ads with "Eligible (limited)"**: not caught by the DISAPPROVED filter; check Policy Manager weekly in alcohol, gambling and healthcare [Google docs, unverified].
- **Large Shopping catalogs**: the products script pages the Content API 250 at a time and can time out; raise `MIN_CLICKS` so only clicked products are checked (Rooijmans, 2022).
- **Hourly schedule with no state**: the same disapproval emails every hour because the sheet is cleared each run (Rooijmans, 2020); keep hourly for launches only.
- **MCC**: single-account scripts; the MCC version is by request (Rooijmans, 2020).
- **Appeals filed reflexively**: Epiminds operating rule — no canon source; classify first (step 2) and appeal only class (d); reason: the appeal form asks what changed to comply (Rooijmans's appeal path, 2022), and a blanket appeal cannot answer it.
- **Code fragility**: the products script's error handling reads an undefined response after a failed API call and can stop the run (noted on fetch of Rooijmans, 2022); check logs after any Merchant Center outage.

## What to measure
- Disapproved ads and products found per day; time from detection to fix or appeal.
- Ads with "STALE" topics found per week (should trend to zero after the first sweep).
- Share of disapprovals by class (a)–(d); appeal success rate.
- Impressions lost: ad impressions in the 7 days before disapproval × days dark.

## Open disagreements in the canon
Rooijmans attributes the 2019 mass disapprovals to automated review and offers no evidence beyond the resolution time (2020); the skill treats that as a hypothesis and asks for change-history evidence first (step 6). On cadence the author offers hourly or daily; Epiminds runs daily plus hourly at launch because the scripts carry no state and hourly produces repeat emails. Nobody in the canon has published cross-account rates of silent disapprovals; the "weeks or months" claim is the author's practice, so the logged dark-time metric is how we test it.
