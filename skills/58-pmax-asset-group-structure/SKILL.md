---
name: pmax-asset-group-structure
id: 58
description: How to split a Performance Max campaign into asset groups — by product/landing page or by audience — and the one case where audience-split is justified. Not for campaign-level segmentation (performance buckets, brand, feed-only) and not for asset writing.
tags: Strategy / PMax / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google making audience signals hard targets; asset-group-level bidding targets; changes to listing-group mechanics.
---
## What this is
The rule for what an asset group is *for*. Audience signals are hints, not targets: PMax may show any asset group to any audience it predicts will convert [Google docs], and Kirk Williams documented road-cycling creative served to families and family creative to commuters in a campaign split by audience (Williams/ZATO, 2022). So an asset group that differs from its neighbours only by audience signal is, in Jyll Saskin Gales' audit language, redundant (Optmyzr guide, 2026). What reliably differs between asset groups is the product set (listing group), the landing page and the creative — so that is what you split on.

## Where it comes from
Kirk Williams (ZATO, 2022 asset-groups post with Ginny Marvin's reply; 2023 structures) for the mechanics and the product-type position; Optmyzr's guide (Saskin Gales, Williams; 2026) and Bhandari (Optmyzr, 2026) for the redundancy rule; Mike Rhodes' PMax Insights asset-group tab (2026) for reading the result; Google's asset-group reporting caveats.

## When to use it / when not to
Use when building a new PMax campaign or restructuring one whose asset groups were created by audience. Do not use for a narrow catalogue (a single product type): product-type splitting is not useful there (Williams/ZATO, 2023) — one asset group, or a feed-only campaign (skill 56). Campaign-level questions (performance buckets, brand, new-customer) are separate.

## Inputs
- Product-type hierarchy in the feed (needs at least three tiers to be usable for splitting — Williams/ZATO, 2023) and custom labels (five available — Williams/ZATO, 2023).
- Landing pages per product group.
- Creative inventory: which images/videos/headlines fit which products.
- Asset-group performance (spend, clicks, conversions, ROAS, AOV) from Rhodes' Asset Groups tab or the UI (Rhodes, 2026) [Google docs].

## Method
1. **Define the unit.** One asset group per set that differs on at least two of: product subset (listing group), landing page, creative. If two candidate groups share all three and differ only by audience signal, merge them (Saskin Gales in Optmyzr guide, 2026; Bhandari/Optmyzr, 2026).
2. **Split by product type first.** Product types carry their own audience segmentation and give control over assets and landing page per group (Williams/ZATO, 2023). Use the product_type hierarchy at the tier where creative actually changes; where a single asset fits 80% of the catalogue, keep one group and let listing groups do the work.
3. **Audience split only in the one case.** Split the same products into two asset groups by audience only when the creative differs materially (different video, different headlines, different landing page) *and* you accept that both groups can show to anyone (Williams/ZATO, 2022; Marvin's reply, in Williams/ZATO, 2022). Google's guidance is not to put the same products in multiple asset groups (per Williams/ZATO, 2022); Williams' use case justifies breaking it; identical assets with different signals never do.
4. **Keep signals light.** Add audience signals after publishing (Williams/ZATO, 2023) and treat them as a launch accelerator, not structure; Hopkins' view is that signals can hurt after learning (Hopkins/Optmyzr, 2023) — record it, review signals at 60 days.
5. **Check for dead weight at 30 days.** If one asset group or the top 20% of products carry more than 80% of spend, the split is not doing anything — move the starved products to their own campaign with its own budget rather than another asset group (Pooler in Optmyzr guide, 2026; Williams/ZATO, 2023 for the campaign-level Heroes/Zombies method). Williams' audit of a 350K-product campaign in one asset group found 50 products with sales in 30 days (Williams/ZATO, 2023).
6. **Read asset-group performance as diagnostic, not as a kill rule.** Conversions are not split across ad components and Google warns against removing groups on CPA/ROAS alone [Google docs]; a group with worse ROAS but a distinct product set still earns its place — a group with worse ROAS and the same product set as another is the one to merge.
7. **Separate what needs a budget or target.** Anything that needs its own tROAS or budget — promotions, margin tiers, new-customer pushes — is a campaign, not an asset group; there are no asset-group bids (Williams/ZATO, 2022, 2023).

## What Google will tell you instead, and why we don't
Google's UI nudges toward audience-themed asset groups, and its reply to Williams was that multiple asset groups "can be used for tailored messaging" while signals remain hints (Marvin, in Williams/ZATO, 2022). We split on products and landing pages instead because the audience split cannot be enforced — the system serves across groups — so the only thing an audience-named group guarantees is duplicated creative (Williams/ZATO, 2022; Optmyzr guide, 2026). We also break Google's "no product in two groups" line in the single case of materially different creative for the same products (Williams/ZATO, 2022).

## Failure modes
- **Single-product-type catalogues**: nothing to split; one group (Williams/ZATO, 2023).
- **Feeds without a three-tier product_type or with all five labels already used**: no clean split key (Williams/ZATO, 2023).
- **Lead gen with one landing page**: asset groups differ only by creative; keep to two or three and test creative, not audiences.
- **Very large catalogues**: groups starve; the fix is campaign-level budget separation, not more asset groups (Williams/ZATO, 2023).
- **Agencies reporting by asset group as if it were targeting**: the report shows where PMax chose to spend, not who it reached.

## What to measure
Spend concentration: share of spend in top 20% of asset groups/products (flag above 80%). Per-group spend, conversions, ROAS, AOV from the Asset Groups tab (Rhodes, 2026). Count of asset groups whose assets are identical to another's (target zero). Landing-page CVR per group.

## Open disagreements in the canon
Williams (2022) wants audience-specific creative per asset group for the same products and thinks Google's no-duplication rule is too simple; Saskin Gales and Bhandari (Optmyzr, 2026) treat audience-only splits as redundant. Epiminds goes product-first and allows Williams' audience split only with distinct creative, because signals do not constrain delivery and identical creative across groups buys nothing.
