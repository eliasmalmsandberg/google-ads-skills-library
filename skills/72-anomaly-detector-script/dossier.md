# Dossier — 72 Anomaly detector script

## Sources

1. **Source**: Mike Rhodes, GitHub `mikerhodesideas/free` — `search-term-alert` ("Search Term Watchdog") and `search-term-alert-evolution` (cloned 2026-10-13; repo last commit 2025-10-22) · **Tier** 1 · **Date** 2025 · **Claim**: Monitors the TOP_N (default 100) search terms by cost, account- or campaign-level, SEARCH / SHOPPING / BOTH. Current window = last 7 full days (ending yesterday); baseline = the 13 weeks (91 days) before that, divided by 13 to give a weekly average. Rules: if baseline avg conversions ≤ MIN_AVG_CONV_FOR_ALERT (2) → always OK; RED if current conversions = 0 and baseline avg > 2; YELLOW if current ÷ baseline avg ≤ PERCENT_THRESHOLD (20%). Email trigger ALWAYS / YELLOW_OR_RED / RED_ONLY (default RED_ONLY); TESTING_MODE true by default. Origin: a practitioner added a too-broad negative list that blocked brand and converting terms and asked for a watchdog; first draft used 50%/80% drops, revised because 0→0 and 0→1 on low-volume terms generated noise. · **Evidence**: Published code with thresholds and the revision log.

2. **Source**: Nils Rooijmans, "7 ways to use scripts to scale your agency" — https://nilsrooijmans.com/daily/7-ways-to-use-scripts-to-scale-your-agency (fetched) · **Tier** 1 · **Date** 2023-02-13 (mod 2024-01-11) · **Claim**: Anomaly alerts at daily, weekly and monthly cadence on impressions, clicks, cost, conversions, conversion rate, cost/conv, ROAS, linking to a sheet with the changes; plus default-settings drift alerts, account-offline alert (declined card/depleted budget) by email and SMS, budget pacing, change-history alerts. No numeric thresholds published. · **Evidence**: Agency practice description.

3. **Source**: Nils Rooijmans, "this change history alert saved our conversion tracking" — https://nilsrooijmans.com/daily/this-change-history-alert-saved-our-conversion-tracking (fetched) · **Tier** 1 · **Date** 2025-12-02 · **Claim**: A client's third-party tool rewrote tracking templates on a Saturday; the change-history alert caught it; otherwise OCI would have broken, conversions under-tracked and "smart bidding would have almost certainly gone haywire". · **Evidence**: Own-account case.

4. **Source**: Nils Rooijmans, "High CPC Bid Alerts" script — https://nilsrooijmans.com/script-to-receive-high-cpc-bid-alerts/ (fetched) · **Tier** 1 · **Date** 2019-03-17 (mod 2025-05-09) · **Claim**: Hourly check of enabled keywords in manual-CPC campaigns with bid > CPC_THRESHOLD (default 5.00); built after a $1.90 bid was entered as $19. · **Evidence**: Published script, own case.

5. **Source**: Nils Rooijmans, Scripts FAQ "MutateError.UNSPECIFIED: Specified version 'v[X]' not supported" — https://nilsrooijmans.com/google-ads-scripts-faq/mutateerror-unspecified-specified-version-vx-not-supported-heres-your-fix/ (fetched) · **Tier** 1 · **Date** undated · **Claim**: Google's Account Anomaly Detector pins `'apiVersion': 'v10'` in its config; when the version sunsets the script dies; comment out the version line. · **Evidence**: Published fix.

6. **Source**: Stewart Dunlop, PPC.io, "Performance Max scripts" roundup — https://ppc.io/blog/performance-max-scripts-google-ads (fetched) · **Tier** not canon (listing only; used to locate, not to support claims) · **Date** 2026-01-23 · **Claim**: Lists Rooijmans's "PMax Anomaly Detector": hourly spend, clicks, conversions vs the same hour in previous weeks, email alerts, thresholds configurable. The Rooijmans page itself could not be fetched. · **Evidence**: Secondary description only.

## Dissenting view
Google's Account Anomaly Detector (reference) compares today-so-far with the same weekday's average and alerts on impressions, clicks and cost; Rhodes's watchdog deliberately ignores anything with a baseline under 2 conversions a week and alerts only on conversions, because his first version (50%/80% drops on impressions and conversions) produced noise on low-volume terms (Rhodes, 2025). The disagreement is about what to monitor: volume metrics (catch an account going dark fast) vs conversion metrics on the top spenders (catch the expensive mistakes). Rooijmans runs all seven KPIs at three cadences (2023) — the broadest net, with thresholds unpublished.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] Google publishes the "Account Anomaly Detector" solution script (single and MCC versions) that compares the current day's impressions, clicks and cost with the historical average for that weekday and hour and emails when outside a configurable multiple; the version in circulation pins an API version (Rooijmans FAQ confirms the v10 pin). Google Ads Scripts run at most hourly, 30-minute runtime. Google also offers "custom alerts"/automated-rule email notifications per metric at campaign level.

## Baseline check
Read `google-ads-anomaly-detection` (diagnosis hierarchy, unsourced 30%/20%/2× monitoring rules) and `google-ads-scripts`. This skill adds the two practitioner designs with their exact windows and thresholds (Rhodes: 7-day vs 13-week baseline, min 2 conv/week, 20% yellow, zero red; Rooijmans: three cadences, seven KPIs, change-history and bid guards), the reason volume-based alerts are noisy, and the API-version maintenance trap.

## Judgment calls
- The Rhodes watchdog is used as the canonical conversion-anomaly design because it is the only one in the canon with published thresholds and a published revision rationale.
- Google's Account Anomaly Detector is treated as the volume-anomaly layer, reference only.
- PPC.io is used only to note that a PMax hourly detector by Rooijmans exists; nothing in the skill depends on it.

## Canon strength: Adequate
Two Tier 1 practitioners with published scripts (Rhodes with thresholds; Rooijmans with cadence/KPIs and guard scripts); no cross-account evidence.

## Invalidated by
Deprecation of `search_term_view` or `change_event` in Scripts; Scripts frequency or runtime limits changing; Google removing the Account Anomaly Detector solution or changing its API pin again.
