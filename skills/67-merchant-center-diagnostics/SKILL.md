---
name: merchant-center-diagnostics
id: 67
description: Detect product disapprovals and eligibility losses before they cost spend, map the disapproval pattern to its cause, and work inside Google's suspension timers. Use when products are disapproved or limited, or when Shopping/PMax spend shifts unexpectedly. Not for feed-override mechanics (65) or title work (66).
tags: Diagnostic / Shopping / Diagnose / Any / Weekly
last_verified: 2026-10-13
invalidated_by: Google changing the misrepresentation warning windows (7/28 days) or 7-business-day review, removing the Content API product-status endpoint, or moving diagnostics wholly into Google Ads with a different issue taxonomy.
---
## What this is
A detection-plus-triage routine. Detection runs daily by script and is weighted by clicks, because the loss is not "some products are disapproved" but "the products that were earning are disapproved and nobody noticed" — Rooijmans has seen clients lose more than 10% of Shopping performance to disapprovals unnoticed for weeks or months (Rooijmans, 2022). Triage runs weekly and works from the specific flagged items to the general cause, never the other way round (Williams/ZATO, 2024).
See also: skill 75 (ad-disapproval-alert-script) — the Disapproved Products script alongside the ad-policy scripts, with the policy-vertical cadence.

## Where it comes from
Nils Rooijmans' disapproved-products alert, PMax Shopping spend-drop alert and hourly feed-fetch scripts (Rooijmans, 2022–2024); Kirk Williams' tax-suspension, site-migration and `id` posts (ZATO, 2024–2026); ZATO's PMax audit order and product-diagnostics notes (Talhelm/ZATO, 2026; Vlietstra/ZATO, 2026). Google's automatic item updates, misrepresentation and identifier pages supply only the platform timers and triggers.

## When to use it / when not to
Use weekly on every Shopping/PMax account, daily by script, and immediately when: PMax spend leaves Shopping for Display/YouTube (Rooijmans, 2024; Talhelm/ZATO, 2026); a site migration, re-platform or feed-app switch is scheduled (Williams/ZATO, 2026); a warning email arrives (the clock is already running) [Google docs]. Not for accounts without Merchant Center, and not as the first move when CTR fell but eligibility is clean — that is 66.

## Inputs
- Content API access (Merchant Center ID, Shopping Content API enabled in Google Ads Scripts) (Rooijmans, 2022).
- `shopping_performance_view` by product id with clicks over the last 30 days (Rooijmans, 2022).
- Merchant Center Needs attention / Diagnostics, and the Products → Product Diagnostics view inside Google Ads for linked accounts (Vlietstra/ZATO, 2026).
- Merchant Center tax, shipping and automatic-updates settings (Williams/ZATO, 2024) [Google docs].
- Change log: feed edits, title/description/product_type changes, migrations, with dates (Talhelm/ZATO, 2026).

## Method
1. **Daily detection, clicks-weighted.** Run the disapproved-products script: products with clicks ≥ `MIN_CLICKS` (default 1; raise it so only earning products alert) in the last 30 days whose Shopping destination status is "disapproved", written to a sheet sorted by clicks with the first issue's reason and doc link, emailed as a count (Rooijmans, 2022). Pair it with the PMax check: did each PMax campaign serve on Shopping yesterday and spend above its threshold? A "no" is usually stock-out, disapproval, or a listing-group/custom-label filter error (Rooijmans, 2024).
2. **Weekly triage: specific → general.** Open the flagged items first and read the issue text; do not start from a theory (Williams/ZATO, 2024). The script records only the first issue per product, so open the product for the full list before acting (Rooijmans, 2022).
3. **Map the pattern to the cause.**
   - Price/availability mismatch across many SKUs, especially on sites that change prices more than once a day → fetch cadence or automatic item updates. Google's own doc says automation may disapprove rather than update when values change often, and stops if mismatches become numerous [Google docs]; fix with hourly Content API fetches, since the UI allows one scheduled fetch a day (Rooijmans, 2022).
   - Missing size/colour/gender on items that aren't apparel → wrong Google product category pulled in vertical-required attributes; override the inferred category (Williams/ZATO, 2025).
   - Text-policy disapprovals → promotional phrases ("Free Shipping", "Best Price"), ALL CAPS, emojis, links in descriptions (Williams/ZATO, 2025) [Google docs: no promo text in titles].
   - Identifier disapprovals → wrong GTIN/MPN; missing an available identifier gives limited visibility rather than disapproval [Google docs].
   - A spike of disapprovals in the days after a migration → recrawl; most clear within a few days, the rest need manual work; changed URLs without 301s disapprove ads (Williams/ZATO, 2026).
   - Account-level tax suspension → shipping & handling taxed on site but unticked in Merchant Center, or city/county rates exceeding the state rate; set a manual state rate one point above the highest city rate (over-estimating is tolerated, under-estimating is not) (Williams/ZATO, 2024).
4. **Work inside the timers.** Most account-level misrepresentation warnings give 7 or 28 calendar days; egregious categories suspend with no warning and are rarely reinstated; reviews typically take 7 business days; a bulk appeal filed while violating offers remain can fail immediately and limit future appeals [Google docs]. Rule: remove or fix every flagged offer *before* requesting review; use a supplemental source for an emergency price correction, then repair the primary (see 65) (Williams/ZATO, 2024).
5. **Pause, don't delete.** A product that must leave paid for a while gets `excluded_destination: Shopping_ads` and stays in free listings; deleting the SKU drops its history (Vlietstra/ZATO, 2026). A product stuck in a policy loop with no path out may be re-submitted under a new `id`, accepting that its history resets (Williams/ZATO, 2025).
6. **Pre-empt migrations.** A month ahead: confirm `id` values will not change, feed-provider credentials and sync frequency are re-pointed, 301s are mapped; migrate in the lowest-traffic four-hour window early in the week, never Friday; watch diagnostics through the window and expect a short disapproval rise (Williams/ZATO, 2026).
7. **Read spend shifts as feed symptoms first.** When PMax performance drops, check Merchant Center eligibility (disapprovals, limited, feed errors, out-of-stock, recent attribute changes) before touching tROAS or budget; compare the drop's date with the change log; don't react to one or two days (Talhelm/ZATO, 2026).

## What Google will tell you instead, and why we don't
Google's automatic item updates are on by default and framed as a safety net for occasional mismatches [Google docs]; the canon treats them as a disapproval source on fast-moving catalogues and manages availability directly with hourly fetches (Rooijmans, 2022; Williams/ZATO, 2026). When PMax drops, Google's reflex advice is to adjust target or budget; ZATO calls those blunt instruments and checks the feed first (Talhelm/ZATO, 2026). Google says never reuse or change an `id`; Williams changes it deliberately to escape a stuck disapproval (Williams/ZATO, 2025).

## Failure modes
- **Alerting on every disapproval.** With `MIN_CLICKS` at 1 on a large catalogue the inbox fills and the team stops reading; raise the threshold to the click level that matters (Rooijmans, 2022).
- **Single-issue blindness.** The script captures one issue per product; fixing it and re-submitting can surface the next one and restart the clock (Rooijmans, 2022).
- **Fast-moving prices on a once-a-day feed.** Price-mismatch disapprovals recur no matter how many you fix (Rooijmans, 2022) [Google docs].
- **Bulk appeal with offers still live.** Immediate failure and reduced appeal rights [Google docs].
- **Tax buffer in price-sensitive categories.** The one-point over-estimate raises displayed price and can trim CTR at the margin (Williams/ZATO, 2024).
- **Marketplaces and multi-client accounts.** Linked-account issues propagate; a non-compliant linked account can suspend the parent (dossier dissent source, Pascoe/PPC Hero, 2020, not canon) — confirm linked accounts in triage.

## What to measure
- Clicks (last 30 days) on currently disapproved products, daily; target zero on the top sellers (Rooijmans, 2022).
- Days-to-clear per disapproval reason, weekly (Williams/ZATO, 2026 for migration spikes).
- Share of PMax spend on Shopping vs other channels, daily (Rooijmans, 2024; Talhelm/ZATO, 2026).
- Count of price/availability mismatch disapprovals per fetch cycle (Rooijmans, 2022) [Google docs].
- Warning-window days remaining on any open account-level issue [Google docs].

## Open disagreements in the canon
- **Start with Google support or with your data?** Pascoe (PPC Hero, 2020) opens with support chat; Williams starts from the flagged products and settings (2024). We start with the data and use support for the review request only.
- **Automatic item updates on or off.** Google defaults on; the canon tolerates it only on slow-moving catalogues and replaces it with hourly fetches elsewhere (Rooijmans, 2022; Williams/ZATO, 2026).
- **Changing `id` to escape a disapproval.** Williams allows it (2025); it contradicts his own "never change ids" rule for migrations (2026). We allow it only for a single product with no history worth keeping.
