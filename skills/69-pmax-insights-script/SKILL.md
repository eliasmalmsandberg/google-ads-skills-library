---
name: pmax-insights-script
id: 69
description: Install and read Mike Rhodes's PMax Insights script (plus Nils Rooijmans's free PMax scripts) to get the channel split, brand share of search categories, product buckets, placements and asset-group numbers that the PMax UI hides or blurs, and act on them. For any account running PMax. Not for building PMax structure, not for Standard Shopping, not a substitute for conversion tracking fixes.
tags: Script / PMax / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google exposing channel-level spend, cost-bearing search terms and placement cost natively in the PMax UI/API; deprecation of campaign_search_term_insight or performance_max_placement_view; Google Ads Scripts API-version sunsets breaking the queries.
---
## What this is
A single-account Google Ads script (about 3,200 lines; MCC version separate) that writes a Google Sheet with 14-plus tabs on Performance Max: Spend by Channel (Shopping / Video / Display / Search-Other, actual and percentage, trended), Search Categories bucketed brand / close-to-brand / non-brand / blank from brand terms you supply, a six-bucket Product Matrix (zombies, zero-conv, meh, flukes, costly, profitable), a Product ID supplemental feed, Placements, Asset Groups, Assets (your video vs Google's auto-generated), Pages, product-title and search-category nGrams, and optional Change History (Rhodes, 2026). It is paid ($199 one-time, MCC $399). The free components (search terms v4, placements, landing pages, asset groups, nGram) are on Rhodes's GitHub, and Rooijmans publishes three free PMax scripts (non-converting terms, trending categories, placement exclusions) that cover the alerting side (Rhodes, 2025; Rooijmans, 2023–2025).

## Where it comes from
The canon names the Rhodes script as canonical for PMax reporting (canon.md). Its data sources are visible in Rhodes's free code: `campaign_search_term_insight` for categories and terms, `performance_max_placement_view` for placements, `shopping_performance_view` by product title for products, `landing_page_view` for pages, `asset_group` for asset groups (Rhodes, 2024–2025). Thresholds for acting on the output come from Rooijmans's PMax scripts (2023–2025); the limits of the search-term data come from Vallaeys (2024) and Hopkins/Optmyzr (2026).

## When to use it / when not to
Use when: any PMax campaign has run 30+ days and you need to know where the spend went (channel), how much of it was brand (search categories), which products are carrying the campaign, and which placements are junk. Run it before any PMax budget or structure decision and before telling a client PMax "works".

Do not use when: the account has no Merchant Center feed and you have not set leadgen mode (product tabs are meaningless; leadgen mode hides them and switches ROAS to CPA) (Rhodes, 2026); conversion tracking is unverified (every bucket is computed from conversions); the catalog is huge and you have not set `lotsproducts` to 1 or 2 — the run times out (Rhodes, 2026).

## Inputs
- Google Ads account with Standard or Admin access; the same Google login for Ads and Sheets (Rhodes, 2026).
- Brand terms list (drives the brand / close-to-brand / non-brand buckets).
- Break-even ROAS (or target CPA in leadgen mode) to set the Product Matrix cost and ROAS thresholds — no defaults are documented (Rhodes, 2026).
- Days of data: rolling 30 by default, or a fixed date range for promo or period comparisons (Rhodes, 2026).
- For the free Rhodes search-terms script: `NUM_DAYS` 7 and `MIN_CLICKS` 30 per category to start; raise clicks or shorten the range if it times out (Rhodes, 2025).

## Method
1. **Install.** Copy the template Sheet, paste the script under Bulk actions > Scripts, paste the Sheet URL and client name into the top lines, authorize twice, Preview, Run (Rhodes, 2026). Schedule daily if you use the Product ID supplemental feed (it must refresh daily), otherwise weekly (Rhodes, 2026).
2. **Read channel split first.** The tab shows actual and percentage spend per channel and how the split shifts over time (Rhodes, 2026). Decision rule: if the Shopping share is falling week over week while Video or Display share rises, the campaign is moving spend onto inventory you did not choose; check the Assets tab for Google auto-generated video (it is marked as Google's, not yours) and remove or replace the assets that let it run (Rhodes, 2026). If the client would not knowingly buy Display or Video at that share, escalate to the PMax structure decision (feed-only PMax or Standard Shopping) — Epiminds operating rule, no canon source in this skill for what a feed-only build does to the split; reason: this tab shows the drift, the structure skill decides the remedy.
3. **Read brand share.** On the Search Categories tab, sum spend in brand + close-to-brand. If brand-type categories dominate, PMax is largely re-buying your brand; add brand exclusions (Google's route, Hopkins/Optmyzr, 2026) and re-read ROAS with brand removed before any budget increase. Remember the term data has no cost column and may be sampled for high-volume terms (Vallaeys, 2024), so use clicks share as the proxy.
4. **Act on non-converting terms.** Rooijmans's rule: in a 90-day window, a term with >100 clicks and <0.5 conversions is a negative (Rooijmans, 2024). Add at campaign level (PMax now accepts campaign negatives; no asset-group negatives exist) or to the PMax account-level list (Hopkins/Optmyzr, 2026). Weekly, Monday 06:00 (Rooijmans, 2024).
5. **Watch category drift.** Compare last 7 days with the prior 7; flag a category when impressions move ≥100 absolute and ≥50% relative; >+100% rising-irrelevant → negatives and asset changes; <−50% → check whether budget should move (Rooijmans, 2023).
6. **Products.** Set the cost threshold and ROAS threshold in Advanced Settings, then read the matrix: High Cost + High ROAS → protect and scale; High Cost + Low ROAS → fix (title, price, feed) or exclude now (Rhodes, 2026). Zombies (zero impressions) and zero-conv products are the candidates for a separate "catch-all" PMax or a feed label; the Product ID Buckets tab is the supplemental feed that carries the label into Merchant Center (Rhodes, 2026).
7. **Placements.** The report includes anything above 10 cents/day by default (Rhodes, 2026). Apply Rooijmans's flags: any mobile app, domains outside a safe-TLD list, spammy/clickbait/political title words, video titles with excessive punctuation or capitalization, "made for kids" channels (Rooijmans, 2024). Exclusions are manual; the script only suggests (Rooijmans, 2024).
8. **Pages and asset groups.** On the Pages tab, any landing page with >30 impressions in 30 days that converts far below the campaign average is a URL-expansion leak; exclude it or turn final URL expansion off (Rhodes, 2025 code filter; Rhodes, 2026). On Asset Groups, pause or rebuild any group whose ROAS is below break-even over the window. Re-read the Campaign tab weekly (Rhodes, 2026).

## What Google will tell you instead, and why we don't
Google's PMax UI reports at campaign level with Insights cards; the asset performance view is "vague" and the channel split was unavailable for years (Rhodes, 2026). Google's search-term insights carry no cost column, only reach back to March 2023, and may be sampled (Vallaeys, 2024). Google's negatives route for brand is Brand Exclusions (Hopkins/Optmyzr, 2026) — we use it, but we also keep brand terms in the script's brand-term list so the sheet shows how much brand Google was buying before the exclusion. Rooijmans's position is that PMax is "a black box" and excluding terms is "very, VERY difficult" in the UI (Rooijmans, 2024); the script is the workaround, not an optional extra.

## Failure modes
- **Lead-gen with no feed** and leadgen mode off: product tabs are empty and ROAS columns are meaningless (Rhodes, 2026).
- **6M-product catalogs** with `lotsproducts` at 0: timeouts (Rhodes, 2026).
- **Very small accounts**: the 100-click / 0.5-conversion negative rule and the 100-impression / 50% category rule (Rooijmans, 2023–2024) will rarely trigger; shorten nothing — just read the sheet monthly.
- **High-volume accounts**: search-term rows are sampled and a term appears once per category, so totals overstate (Vallaeys, 2024; Rhodes, 2025).
- **Placement script false positives**: the TLD check cannot match multi-part TLDs such as .co.uk, and substring keyword matching flags legitimate domains (noted in the fetch of Rooijmans, 2024) — review before excluding.
- **MCC runs** with Landing Page and Change History on are slow; leave them off (Rhodes, 2026).
- **API version sunsets**: the free scripts pin `apiVersion` (v16/v17/v18) and will throw `MutateError.UNSPECIFIED` when that version retires; remove the pinned version (Rooijmans, FAQ, undated).

## What to measure
- Channel share of PMax spend, weekly, and its drift.
- Brand + close-to-brand share of search-category clicks, before and after brand exclusions.
- Negatives added per week from the non-converting rule and their 90-day clicks.
- Share of spend in costly + zero-conv product buckets; placements excluded per week.
- ROAS/CPA per asset group vs break-even.

## Open disagreements in the canon
Vallaeys (2024) and Hopkins (2026) read PMax search terms as a negatives and copy source; Rhodes and Rooijmans read brand share and category trend as the test of whether PMax deserves its budget. Epiminds goes with Rhodes/Rooijmans: read brand share and channel split first, then do the negatives work. On placements, Rooijmans's script lists suggestions only and he does not automate exclusion; Rhodes's docs likewise stop at the exclusions form. Nobody in the canon auto-applies PMax exclusions, and neither do we.
