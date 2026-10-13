# Dossier — 75 Ad disapproval alert script

## Sources

1. **Source**: Nils Rooijmans, "Disapproved Ads Alerts" script — https://nilsrooijmans.com/google-ads-script-disapproved-ads-alerts/ (fetched) · **Tier** 1 · **Date** pub 2020-01-23, v2.0 June 2022 (AWQL→GAQL, policy findings added), mod 2025-05-09 · **Claim**: GAQL on `ad_group_ad` where `policy_summary.approval_status = DISAPPROVED`, campaign ENABLED and serving status not ENDED, ad group and ad ENABLED, `segments.date` TODAY; records campaign, ad group, ad ID, ad type, approval status, policy topic entries joined as "Disapproval Reason"; clears and rewrites the sheet each run; emails "[GOOGLE ADS ALERT] - Disapproved Ads" only when ≥1 found. Run hourly or daily. Why: disapprovals distort tests, cut reach, and block keywords; in 2019 multiple accounts got "Malicious or unwanted software" disapprovals with no malware, which took three weeks and many support contacts to clear; he suspects automated review errors. Limitations: no history, single email address, single account (MCC on request), "Ad Status" column actually holds approval status. · **Evidence**: Published script; own-account cases.

2. **Source**: Nils Rooijmans, "Past Violations Alert" script — https://nilsrooijmans.com/google-ads-script-past-violations-alert/ (fetched) · **Tier** 1 · **Date** 2022-07-11 (mod 2025-05-09) · **Claim**: Same query; flags any policy topic containing "STALE" (case-insensitive) — ads Google keeps disapproved after the policy no longer applies; "this status generates no notification" and the ad gets zero impressions until someone appeals. Appeal path: hover status → Appeal → reason "changes made to comply" → select ads → Submit. Hourly or daily. · **Evidence**: Published script.

3. **Source**: Nils Rooijmans, "Disapproved Products Alerts" script — https://nilsrooijmans.com/google-ads-script-disapproved-products-alerts/ (fetched) · **Tier** 1 · **Date** 2022-09-06 (mod 2025-05-09) · **Claim**: `shopping_performance_view` products with clicks ≥ MIN_CLICKS (1) over PERIOD (LAST_30_DAYS), then Shopping Content API product statuses (250/page) for the "Shopping" destination = disapproved; first item-level issue's description, detail, documentation link; sorted by clicks; emails count. Disapprovals "go unnoticed for weeks or even months". Daily; needs GMC_ID and the Shopping Content API enabled under Advanced APIs. Limitations: first issue only, no history, no all-clear email. · **Evidence**: Published script.

4. **Source**: Nils Rooijmans, "Change History Alerts" — https://nilsrooijmans.com/google-ads-script-change-history-alerts/ (fetched) · **Tier** 1 · **Date** 2023-04-11 · **Claim**: Daily `change_event` review; used here as the companion that explains a disapproval wave (new ads or URL changes by an unlisted user). · **Evidence**: Published script.

## Dissenting view
Rooijmans's 2020 post suspects automated review errors behind mass disapprovals; the page offers no evidence for the cause, only the three-week resolution. No canon source argues that Google's own notifications are sufficient; the practical disagreement in the canon is cadence — hourly (Rooijmans suggests hourly or daily) costs nothing in Scripts but produces repeated emails because the sheet is cleared each run and there is no state. The skill takes daily plus an hourly run only during launches.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] Google emails account-level policy notifications depending on the user's notification settings, and the Policy Manager lists disapprovals and limited-approval ads; "Eligible (limited)" is a distinct status the script's DISAPPROVED filter does not catch; the `ad_group_ad.policy_summary` fields (approval_status, review_status, policy_topic_entries) are the GAQL source Rooijmans's query uses; appeals are filed from the ad status hover or Policy Manager; Merchant Center item disapprovals are visible via the Content API `productstatuses` (Rooijmans 2022 confirms the resource).

## Baseline check
Read `google-ads-scripts` (a disapproval monitor using the legacy `PolicySummary.ReviewStatus` iterator and `getHeadlinePart1` — pre-RSA, pre-GAQL) and `google-ads-anomaly-detection`. This skill adds the GAQL query and filters, the "STALE" past-violations class that generates no notification, the Merchant Center product layer, and the compliance-vertical cadence and escalation.

## Judgment calls
- All practitioner material is from one Tier 1 source across three scripts; rated Adequate (independent methods, hygiene scripts are his named strength) and flagged for the reviewer.
- "Eligible (limited)" is named as a gap from platform knowledge, labelled unverified.
- Cadence position (daily, hourly at launch) is ours; both options are the author's.

## Canon strength: Adequate
One Tier 1 practitioner with three published scripts and own-account cases; no cross-account evidence.

## Invalidated by
Changes to `ad_group_ad.policy_summary` fields or policy topic naming (the "STALE" string match); Shopping Content API deprecation in favour of the Merchant API (the products script's status call); Google adding reliable push notifications for past-violation and limited statuses.
