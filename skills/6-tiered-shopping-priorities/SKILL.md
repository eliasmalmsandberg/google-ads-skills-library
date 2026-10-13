---
name: tiered-shopping-priorities
id: 6
description: Use Standard Shopping campaign priorities (high/medium/low) plus negatives to route queries by intent tier (generic → category → brand/SKU) and bid each tier differently. Not for PMax-only accounts.
tags: Structure / Shopping / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Removal of campaign priority from Standard Shopping; Standard Shopping retired in favour of PMax; brand lists available in Standard Shopping.
---
STATUS: THIN CANON — needs practitioner input

## What the dossier found
- One Tier 1 source covers the mechanism, and only for the brand tier: Rooijmans (2025) runs the brand Shopping campaign at *low* priority with high CPCs and brand terms as negatives on all high/medium-priority non-brand campaigns, with three conditions — every brand-campaign product also in the non-brand campaigns; non-brand budgets never exhaust before brand; identical schedule/device/audience/location across tiers. He explicitly rejects the inverse build (brand campaign matching broadly, negatives scripted out) as money-losing and list-limit-breaking.
- Rooijmans (2025) also sets the PMax negative method (shared list applied to PMax; never account-level negatives), which matters because PMax outranks Standard Shopping for the same products.
- Non-canon positions: Lolk (Optmyzr Town Hall, 2025) is doubling down on Standard Shopping over feed-only PMax but says most Shopping splits are pointless because targets end up identical; split only for different ROAS targets (his example 500% vs 300%). Humphrey (SEL, 2026) rebuilt non-brand as granular Standard Shopping with product-group priorities and bids, brand controlled by negatives + priority + tROAS + sometimes a portfolio max-CPC cap.
- Brand lists are not available in Standard Shopping (SEL brand-settings write-up; Rooijmans, 2025), so negatives and priority are the only routing tools.

## What is missing
- The canon's Shopping lead (Kirk Williams/ZATO) and the original three-tier query-level method (Röttgerding) could not be retrieved this pass; web search budget ran out before Shopping research and the ZATO blog index pages listed no structure posts.
- No fetched source gives the generic/category/SKU three-tier wiring (which negatives go on which priority tier, how bids step across tiers), promotion thresholds between tiers, or any account evidence that tiering beats a single Standard Shopping campaign under tROAS.
- Google's campaign-priority help page was not fetched, so the exact serving rule (priority before bid; fall-through on budget exhaustion) is recorded only as Rooijmans's description.

## Question for Elias
Do you have a Kirk Williams / ZATO or PPC Mastery reference for the three-tier Shopping priority structure (generic → category → brand/SKU) that you want this skill built on — and is the Epiminds position that tiers exist for query routing (the Röttgerding/Williams tradition) or only for separate ROAS targets (Lolk's position)? With one of those, the brand-tier rules above become the third tier of a complete skill.
