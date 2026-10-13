---
name: broken-url-checker-script
id: 73
description: Run Google's Link Checker solution for 404s and Rooijmans's Check-for-Redirects script for 3xx and fetch errors across ads, keywords and sitelinks, configured to avoid 403 false positives and to cover the URLs PMax actually lands on. For large sites or sites whose pages change often. Not for landing-page quality or speed testing, not for Merchant Center link disapprovals.
tags: Script / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Removal or quota reduction of UrlFetchApp in Scripts; Google making "Destination not working" disapprovals immediate and complete; removal of PMax final URL expansion.
---
## What this is
Two scripts on one schedule. Google's Link Checker solution (reference) fetches every final URL on enabled ads, keywords and sitelinks, treats HTTP ≥400 and exceptions as broken, keeps its progress in a spreadsheet so it can resume across 30-minute runs, and emails a summary [Google docs, unverified]. Rooijmans's Check-for-Redirects script fetches the same URL set with redirect-following switched off so the first status code is captured, flags 301/302/303/307/308 and any fetch exception, requests each unique URL once per run, writes a "Redirect Report" tab with 30-day clicks per ad and keyword, and emails when at least one is found (Rooijmans, undated script page). Google's checker does not catch redirects (Rooijmans, undated).
See also: skill 61 (pmax-url-expansion) — the Final URL expansion setting that creates the expanded landing pages this checker must cover.

## Where it comes from
Rooijmans's redirect script and his two method posts: why redirects matter (dropped tracking parameters, slower pages, cross-domain analytics breaks — Rooijmans, 2023) and why link checkers lie with 403s (User-Agent, IP allow-lists, auth, rate limits — Rooijmans, 2023). Rhodes's free landing-page script shows where PMax sends traffic (`landing_page_view.unexpanded_final_url`, PMax, 30 days, >30 impressions), which is the URL set a checker must cover when final URL expansion is on (Rhodes, 2024).

## When to use it / when not to
Use when: the site has hundreds or thousands of unique landing URLs; the client's SEO or web team changes URL structures, trailing slashes or protocols without telling you (the three causes Rooijmans names, 2023); after any site migration; on any account where PMax final URL expansion is on.

Do not use when: the site is a handful of static pages — a manual check after each change is enough; when the client's server blocks automated fetches and will not allow-list Google's fetch IPs — the script returns 403 on every URL and tells you nothing (Rooijmans, 2023).

## Inputs
- Blank Google Sheet URL and alert email (Rooijmans, undated).
- The list of enabled ads, keywords, ad-group and campaign sitelinks (the script reads them; account-level sitelinks are not covered) (Rooijmans, undated).
- A browser-like User-Agent string to set in `UrlFetchApp` options, and the client's IT contact for IP allow-listing (Rooijmans, 2023).
- For PMax: the "paths" tab from Rhodes's landing-page script (Rhodes, 2024).

## Method
1. **Install the 404 layer.** Google's Link Checker, weekly. It handles the resume-across-runs problem for large accounts; keep its spreadsheet as the state store [Google docs, unverified].
2. **Install the redirect layer.** Rooijmans's script, weekly, Preview first (Rooijmans, undated). Both scripts on the same day so one report covers both classes.
3. **Kill 403 false positives before trusting output.** If the first run shows 403s on pages that open in a browser: set a browser User-Agent in the fetch options; ask IT to allow-list Google's published fetch IP ranges; add any required headers; lower request volume (Rooijmans, 2023). Only after this is a 403 treated as broken.
4. **Classify each flagged row.** 4xx/5xx or exception → broken: pause the ad or sitelink if the page will not be back within the day, else fix the page. 301/308 → permanent redirect: update the Final URL to the destination and tell SEO so link equity is handled (Rooijmans, undated). 302/303/307 → temporary redirect: check that the redirect keeps URL parameters; if tracking parameters are dropped, fix the same day — this is the harm that actually shows up in data, as under-reported conversions feeding Smart Bidding (Rooijmans, 2023).
5. **Prioritise by clicks.** The redirect report carries 30-day clicks per ad and keyword; work top-down. Sitelink rows show "UNKNOWN" clicks (Rooijmans, undated) — treat them as high priority because they are account-wide.
6. **Cover PMax.** Run Rhodes's landing-page script monthly; any URL on the "paths" tab that is not in your ad final URLs is a URL-expansion landing page (Rhodes, 2024). Feed those URLs through the same fetch checks; a broken expanded URL is invisible to the ad-level checkers.
7. **Setup discipline.** At campaign build, check every final URL with the Redirect Path extension before launch; the script is the ongoing control, not the first check (Rooijmans, 2023).
8. **Maintenance.** Quarterly, Preview both scripts; large sites may need the campaign-level split or the MCC version to stay inside the 30-minute runtime (Rooijmans, undated).

## What Google will tell you instead, and why we don't
Google's control is the "Destination not working" policy disapproval and the Link Checker's 4xx logic; neither sees a 301 that silently drops your tracking parameters, and the Link Checker "does not catch redirects" (Rooijmans, undated). Google's product lead argues redirects "slow things down which can impact your QS" (quoted by Rooijmans, undated); we do not chase redirects for QS — Rooijmans's own three-account test found QS improved or barely moved after fixing them (Rooijmans, undated). We chase them because of parameter loss and conversion under-reporting (Rooijmans, 2023). Auto-applied "fix broken URLs" recommendations are off (skill 78); the fix is logged by us.

## Failure modes
- **Bot-blocking servers / WAFs**: 403 on everything until allow-listed (Rooijmans, 2023).
- **Thousands of unique URLs** (large e-commerce): the redirect script has no resume logic and will time out; run per campaign or use the MCC version (Rooijmans, undated); keep Google's checker, which resumes, as the 404 layer.
- **Account-level sitelinks**: not checked by the redirect script (Rooijmans, undated); check manually.
- **Rate-limited sites**: the script's one-request-per-URL cache helps, but a weekly run on a small server can still trip rate limits and produce false 429/403s (Rooijmans, 2023).
- **PMax with URL expansion**: the ad-level URL set is not the served URL set (Rhodes, 2024).
- **Single-page apps** that return 200 with an in-app "not found": neither script sees it; only a content check would.

## What to measure
- Broken URLs and redirects found per run, and clicks in the prior 30 days on them (Rooijmans's report columns).
- Time from detection to fix.
- Share of flagged URLs that were 403 false positives after the User-Agent/IP fix (target: zero).
- PMax expanded URLs outside the ad URL set, per month.

## Open disagreements in the canon
Rooijmans's writing says redirects hurt QS; his data says the QS effect is small or nil. Epiminds takes the data: redirects are a tracking and speed issue, fixed in priority order of clicks and parameter loss, and we do not promise QS gains. The canon has no cross-account evidence on how much spend lands on broken pages; Google's checker and Rooijmans's script are hygiene controls, and we run them because the cost of a run is minutes and the cost of a missed migration is a month of dead clicks.
