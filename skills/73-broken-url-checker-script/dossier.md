# Dossier — 73 404 / broken URL checker

## Sources

1. **Source**: Nils Rooijmans, "Google Ads Script – Check for Redirects" — https://nilsrooijmans.com/google-ads-redirect-alert-script/ (fetched) · **Tier** 1 · **Date** undated page; reader comment 2023-08-02 · **Claim**: Fetches every enabled ad, keyword and sitelink Final URL (desktop and mobile) with redirect-following off so the first response code is captured; 301/302/303/307/308 = redirect; any fetch exception = "ERROR TESTING URL"; one request per unique URL (cache); writes to a "Redirect Report" tab with last-30-day clicks for ads/keywords ("UNKNOWN" for sitelinks); emails when ≥1 found; ad-group sitelinks with campaign fallback; account-level sitelinks not covered. Run weekly after Preview. States that Google's broken link checker does not catch redirects. Author's three-account test of removing redirects: QS improved or hardly changed; results "hard to interpret". · **Evidence**: Published script; small inconclusive test.

2. **Source**: Nils Rooijmans, "Redirects — don't let them hurt you" — https://nilsrooijmans.com/daily/redirects-dont-let-them-hurt-you (fetched) · **Tier** 1 · **Date** 2023-08-01 · **Claim**: Redirects slow load (CVR, QS), often drop URL parameters that conversion tracking needs (under-reported conversions, bad for Smart Bidding), cross-domain redirects are bad for analytics; links break after setup through SEO URL changes, CMS trailing-slash changes, HTTP→HTTPS; check with the Redirect Path extension at setup and the script continuously. · **Evidence**: Reasoning, no data.

3. **Source**: Nils Rooijmans, "error: 403 response code" — https://nilsrooijmans.com/daily/error-403-response-code (fetched; also in his Scripts FAQ) · **Tier** 1 · **Date** 2023-08-15 · **Claim**: Link checkers report 403 on pages that load in a browser; causes: User-Agent blocking, IP allow-listing (Google's fetch IPs), missing auth cookies, rate limiting; fixes: set a browser User-Agent in `UrlFetchApp`, whitelist Google's published IP ranges, add headers, reduce request volume. · **Evidence**: Troubleshooting from practice.

4. **Source**: Jamie Newton, PPC Hero (Hanapin), "Do your AdWords scripts keep giving you timeout errors?" — https://ppchero.com/do-your-adwords-scripts-keep-giving-you-timeout-errors/ (fetched) · **Tier** fails inclusion (tool promotion, no method); noted only for the problem statement: accounts with hundreds to thousands of unique URLs hit script timeouts and fetch limits · **Date** 2015-03-04 · **Evidence**: None.

5. **Source**: Mike Rhodes, GitHub `mikerhodesideas/free` — `landing-page` (cloned 2026-10-13) · **Tier** 1 · **Date** 2024 (v70) · **Claim**: Pulls `landing_page_view.unexpanded_final_url` for PMax, LAST_30_DAYS, impressions >30, into a "paths" tab — i.e. the list of URLs PMax actually sends traffic to, which is the URL set a checker must cover when final URL expansion is on. · **Evidence**: Published code.

## Dissenting view
Rooijmans holds that redirects hurt QS and tracking and must be chased (2023), yet his own three-account test showed QS "improved or hardly changed" after fixing them (undated script page). The disagreement is with himself and with Google's product lead quote he cites ("slows things down which can impact your QS"): the measurable harm from redirects is tracking-parameter loss, not a QS lift. PPC Hero (2015, not canon) argues scripts cannot scale to thousands of URLs and a hosted tool is needed; Rooijmans's design answers with per-URL caching and weekly cadence.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] Google publishes the "Link Checker" solution script (single-account and MCC) that fetches final URLs for ads, keywords and sitelinks, treats HTTP ≥400 and fetch exceptions as broken, stores progress in a spreadsheet across runs to survive the 30-minute limit, and emails a summary; `UrlFetchApp` carries a daily fetch quota and Google's own policy disapproves ads whose destination does not work ("Destination not working"). PMax final URL expansion sends traffic to URLs not in the ad, visible in `landing_page_view` (Rhodes 2024 code confirms the resource).

## Baseline check
Read `google-ads-scripts` (no URL checker) and `google-ads-account-audit`. The baseline does not mention the Link Checker solution, redirect detection, 403 false positives, the per-URL cache pattern, or PMax URL expansion as a coverage gap. This skill does.

## Judgment calls
- All Tier 1 practitioner material is from one practitioner (Rooijmans) across three items; Google's Link Checker is the canonical 404 script and is reference-only. Rated Adequate rather than Thin because the three Rooijmans items are independent methods (redirect detection, 403 handling, why it matters) and the canon lists hygiene scripts as his strongest topic; flagged here for the reviewer.
- PPC Hero is cited for the problem statement only and marked as failing inclusion.
- Position taken on redirects: fix for tracking-parameter reasons, not QS.

## Canon strength: Adequate
One Tier 1 practitioner with three published items (script plus two method posts), one Tier 1 code reference for PMax coverage; Google reference for the 404 script.

## Invalidated by
Removal or quota reduction of `UrlFetchApp` in Scripts; Google making "Destination not working" disapprovals immediate and complete (would make the 404 layer redundant); PMax final URL expansion being removed (would shrink the URL set to check).
