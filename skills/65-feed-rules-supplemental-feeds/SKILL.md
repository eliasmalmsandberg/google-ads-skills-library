---
name: feed-rules-supplemental-feeds
id: 65
description: How to change titles, labels, promotions, prices or exclusions in Merchant Center without touching the primary feed, and how to keep that override layer from silently breaking the account. Not for deciding what the labels or titles should say (64, 66) or for diagnosing disapprovals (67).
tags: Technique / Shopping / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google removing supplemental sources or attribute rules from Merchant Center Next, dropping the Advanced data source management add-on, making id matching case-insensitive, or lifting the once-a-day scheduled-fetch limit.
---
## What this is
The operating rules for Merchant Center's override layer: supplemental sources (keyed on `id`) and attribute rules (formerly feed rules). The position: use the layer for things that must change faster than the primary feed can, keep it as thin as possible, and move every permanent change back into the source. Kirk Williams' default is to change the primary whenever you can, because layered sources make problems hard to diagnose (Williams/ZATO, 2024).

## Where it comes from
Kirk Williams' Merchant Center Mastery series on supplemental sources, attribute rules, the `id` attribute and title testing (ZATO, 2024–2026); Mike Rhodes' PMax Insights ID-tab export to a supplementary feed (Rhodes, 2026); Nils Rooijmans' hourly feed-fetch script and the Google `low_volume_skus` sheet-as-supplemental pattern (Rooijmans, 2022). Google's attribute-rule operation list and automatic item updates are used only to state what the platform does.

## When to use it / when not to
Use when: the ecommerce platform or feed app cannot expose the field you need (custom labels, promotion_id, a rewritten title) or cannot ship the change this week; you need an emergency correction (price during a suspension) before the primary can be fixed; you are running a title test on a subset; a script is writing performance labels nightly (Williams/ZATO, 2024; Rhodes, 2026; Rooijmans, 2022). Do not use it to carry the whole catalogue, to permanently own price or availability, or as a substitute for fixing the source — all three are how overrides go stale and block the primary (Williams/ZATO, 2024).

## Inputs
- Merchant Center Next with the "Advanced data source management" add-on enabled; without it supplemental sources and attribute rules are hidden (Williams/ZATO, 2024) [Google docs].
- The exact `id` values from the primary feed, with case preserved (Williams/ZATO, 2024, 2025).
- The primary feed's scheduled fetch time (Williams/ZATO, 2024).
- The list of attributes to change, and nothing else (Williams/ZATO, 2024).

## Method
1. **Choose the layer.** One attribute, many products, derivable from existing data (prepend brand to title, set product_type from URL, map promotion_id by condition) → attribute rule on the primary source [Google docs operations: Set to, Extract, Take latest, Prepend, Append, Find & Replace, Calculate, Split & Choose, Clear]. Per-product values that come from outside the feed (margin tier, performance bucket, promo flag, a corrected price) → supplemental source keyed on `id` (Williams/ZATO, 2024). Permanent fix → edit the source and remove the override afterwards (Williams/ZATO, 2024, 2026).
2. **Build the supplemental source from the Sheets template, then strip it.** Keep `id` plus only the columns you will change. Everything in the supplemental source is hard-coded over the primary for those attributes: import 500 attributes to change 3 and the other 497 stop updating from the primary (Williams/ZATO, 2024).
3. **Match on `id` exactly.** `id` is case-sensitive; "ABC123" and "abc123" are two products. If the match report shows zero matches, check case first — Shopify IDs pasted from Google Ads reporting are a known cause (Williams/ZATO, 2024, 2025). Never change `id` to "clean it up": it overwrites the product and its history (Williams/ZATO, 2025).
4. **Schedule the pull one hour after the primary feed loads**, run a manual update on first setup, and rename the source for the attribute it edits so the next person can see what it does (Williams/ZATO, 2024).
5. **Attach via rules and test before applying.** The supplemental source is attached to the primary through its attribute rules; save as draft, preview, then apply. "Never skip the test" (Williams/ZATO, 2024) [Google docs: draft → preview → apply].
6. **Know the layering order.** Williams describes it as: feed/Content API → supplemental source → attribute rules → Google's automated improvements → manual product edits, each later layer overriding the earlier for the attributes it touches (Williams/ZATO, 2024). Automatic item updates sit above your feed for price, sale price, availability and condition, and on a detected mismatch may disapprove the product rather than update it [Google docs].
7. **Automate what changes nightly.** Performance labels and exclusions: export from a product-performance script into the sheet daily (Rhodes, 2026) or use the `low_volume_skus` script that writes a custom label to a sheet used as a supplemental feed (Rooijmans, 2022). If price or stock move intraday, trigger feed fetches hourly through the Content API — the Merchant Center UI allows one scheduled fetch a day (Rooijmans, 2022).
8. **Title tests run through this layer.** Apply the rewritten title to half of a brand or product type via a rule or supplemental source, keep the other half as control, read CTR and impressions after 2–4 weeks (Williams/ZATO, 2025).
9. **Retire, don't delete.** When an override is no longer needed, disassociate the supplemental source from the primary's rules; deleting it loses the ability to reattach (Williams/ZATO, 2024). Then move the change into the source.
10. **Emergency price fix during a suspension**: correct price via supplemental → let Google re-verify → suspension lifts → fix the primary → disassociate the override (Williams/ZATO, 2024).

## What Google will tell you instead, and why we don't
Google turns automatic item updates on by default and reads price/availability from your structured data [Google docs]. We keep stock status under our own control and treat automatic sourcing as a source of errors (dead products, stale state) rather than a safety net (Williams/ZATO, 2026); where prices change more than once a day Google's own doc says automation may disapprove rather than update [Google docs], which is the case Rooijmans' hourly fetch exists for (Rooijmans, 2022). Google also says never reuse an `id`; Williams reuses it when the new product is a true replacement so history carries over (Williams/ZATO, 2025).

## Failure modes
- **Catalogue dumped into the supplemental source.** Every column present now overrides the primary; price and availability go stale and products are disapproved for mismatch (Williams/ZATO, 2024) [Google docs].
- **Feed-app or platform migration changes `id` format.** Google sees a new catalogue, history resets, supplemental matches drop to zero (Williams/ZATO, 2025, 2026).
- **Multiple supplemental sources editing the same attribute.** The hierarchy decides, not you; diagnose by disassociating one at a time (Williams/ZATO, 2024).
- **Fast-moving inventory on once-a-day fetch.** Clicks on wrong prices and out-of-stock items; hourly fetch or platform API sync needed (Rooijmans, 2022).
- **Small accounts without the add-on.** Nothing in this skill works until Advanced data source management is enabled; a feed app's own rules may be simpler (Williams/ZATO, 2024).
- **Title rules without a control.** Attribute rules applied to 100% of a category give no read on whether the change helped (Williams/ZATO, 2025).

## What to measure
- Match report count after each supplemental update; zero or a sudden drop = `id` problem (Williams/ZATO, 2024).
- Disapprovals for price/availability mismatch after any override on those fields [Google docs].
- Count of active supplemental sources and attribute rules, reviewed monthly, with each one justified or disassociated (Williams/ZATO, 2024).
- For title tests: CTR and impressions, test half vs control half, 2–4 weeks (Williams/ZATO, 2025).

## Open disagreements in the canon
- **Overrides on price/availability.** Williams uses them for emergencies (2024); PPC Hero's Kelly says manual price/stock edits should be avoided because they fight automated updates (2025, not canon). We allow the override only with a dated removal step (method step 10).
- **Automation vs self-managed stock.** Google defaults automation on; Williams manages stock himself (2026). We follow Williams and audit automation's disapprovals rather than relying on it.
