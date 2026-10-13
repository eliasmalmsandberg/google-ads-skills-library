---
name: custom-labels-margin-stock-season
id: 64
description: Design the custom_label scheme for a Shopping/PMax account so bids, budgets and targets follow margin, stock and seasonality instead of blended ROAS. Not for writing titles or feed rules (65) or for the campaign priority/negative structure (68).
tags: Technique / Shopping / Optimise / Established / One-off
last_verified: 2026-10-13
invalidated_by: Google changing the 5-label or 1,000-value caps, removing custom labels from PMax/AI Max listing groups, or dropping supplemental data sources from Merchant Center Next.
---
## What this is
A decision procedure for assigning the five `custom_label` slots and turning them into bidding tiers. The point is to give Smart Bidding information it does not have — margin, stock depth, season — because, as Optmyzr puts it, Smart Bidding "has no idea" whether a conversion was profitable and ROAS "hides profit" (Optmyzr/Tran-Van & Vallaeys, 2025). Kirk Williams' position is that after Google stripped most manual Shopping levers, labels are "one of the main remaining ways to direct budget and aggression" in PMax (Williams/ZATO, 2026).

## Where it comes from
Fred Vallaeys' original label method (coarse, equal-sized margin tiers; report first, restructure second) (Vallaeys/PPC Hero, 2015); Optmyzr's "truth data" play with named labels and budget rules (Optmyzr, 2025); Kirk Williams' feed-first and feed-optimisation posts (ZATO, 2026); Mike Rhodes' cost×ROAS six-bucket product matrix and its supplemental-feed export (Rhodes, 2026); Nils Rooijmans on the low-volume-SKU script (Rooijmans, 2022); Reinhard Einwagner on labels as experiments and label historicisation (smec/PPC Hero, 2017).

## When to use it / when not to
Use when margin varies materially across the catalogue, when stock-outs or thin stock are common, or when a seasonal share of the catalogue should be bid differently — and when the account is established enough that tiers will collect data. Do not bother on a catalogue where margin is near-uniform and stock is always deep: labels then only add maintenance. Do not use labels as the fix for a weak offer: Williams is explicit that the feed is the most important variable *inside Google* but offer, price and CVR matter more for the business (Williams/ZATO, 2026).

## Inputs
- A product-level "truth" table outside Google: SKU, gross margin %, units in stock, competitor price (optional), seasonality flag, promo flag (Optmyzr, 2025).
- Cost of goods or margin per SKU/category to compute break-even ROAS and POAS (Rhodes, 2026).
- Shopping/PMax product performance by item ID over a rolling window (default example: last 30 days) (Rhodes, 2026).
- Merchant Center access to add a supplemental data source keyed on `id` (Williams/ZATO, 2026).

## Method
1. **Allocate the five slots by dimension, one dimension per slot.** Each label must hold values of the same kind; don't mix "summer" and "bestseller" in one label (Vallaeys/PPC Hero, 2015). Default allocation: `custom_label_0` = margin tier, `_1` = stock state, `_2` = season/promo, `_3` = performance bucket, `_4` = "active for paid" flag (Williams/ZATO, 2026; Optmyzr, 2025). Stay well below the caps: 1,000 unique values per label, 5,000 across all five, 1–100 characters [Google docs].
2. **Start with margin only.** Optmyzr's rule is one signal first, margin tier, before adding stock or competitor price (Optmyzr, 2025). Use three to five tiers with roughly equal product counts per tier; tiers with few products never accumulate enough data to bid on (Vallaeys/PPC Hero, 2015). Name them `margin_high / margin_med / margin_low` (Optmyzr, 2025). Set each tier's target from its break-even: Rhodes' POAS uses a COGS figure you must overwrite with real margins (Rhodes, 2026).
3. **Report before you restructure.** Segment existing performance by the new label for two to four weeks. Only split bidding by a dimension if the segments actually differ: Vallaeys' seasonality rule is to sub-divide only when out-of-season products perform "significantly worse" (Vallaeys/PPC Hero, 2015). Labels are historicised — the Shopping performance report stores the label value at impression time — so you can run up to five such experiments at once and read them later even after relabelling (Einwagner/smec, 2017).
4. **Stock state.** Values: `inventory_low`, `inventory_clearance`, else blank (Optmyzr, 2025). ZATO's threshold for pulling an item from paid is fewer than two or three units (Williams/ZATO, 2026). For sized goods, label size coverage instead of raw units: all sizes = 10, two of the three most popular sizes = 7, no popular sizes = 2, interpolate between (Einwagner/smec, 2017). Cap or exclude `inventory_low` from aggressive campaigns and set an alert when its spend passes a fixed amount (Optmyzr, 2025).
5. **Performance bucket.** Classify every item on two axes, cost above/below a threshold and ROAS above/below target, giving six buckets: zombies (zero impressions), zero-conv (impressions, no conversions), meh, flukes (high ROAS, low cost), costly (high cost, low ROAS), profitable (Rhodes, 2026). Set the ROAS axis at break-even for that margin tier, not at a blended account target. Export the buckets to a supplemental feed daily (Rhodes, 2026).
6. **Budget and target rules per label** (run weekly): `margin_low` AND CPA above target → cut that segment's budget 25%; `priority_promo` AND profit-on-spend above goal → raise budget 20% (Optmyzr, 2025). `costly` for two consecutive windows → move to a tighter-tROAS, smaller-budget test campaign before excluding, and check assisted/view-through contribution first (Williams/ZATO, 2026). `flukes` → small bid/target loosening, not a budget jump (Optmyzr Smart Product Labeler, undated).
7. **"Active for paid" flag.** On large catalogues, advertise only the sellers that budget can cover and keep the rest in free listings: ZATO's example is 500,000 SKUs on $20k/month → paid on roughly the top 1,000, all 500K still sent to free listings via `excluded_destination` or a label (Williams/ZATO, 2026).
8. **Refresh cadence.** Margin tier: on cost changes, at least monthly, with a margin-tier audit monthly and profit goals revisited quarterly (Optmyzr, 2025). Stock and promo: nightly or on inventory change (Optmyzr, 2025); if prices/stock move intraday, labels need near-hourly feed updates or they are stale (Einwagner/smec, 2017). Allow 24–48 hours for new label values to reach Google Ads [Google docs].
9. **Close the "Everything else" leak.** New label values do not rebuild product groups; items land in "Everything else". Track the share of clicks from "Everything else" per campaign and re-subdivide when it grows (Vallaeys/PPC Hero, 2015). Apply labels via a supplemental feed so the primary feed is untouched, but edit the source when you can (Williams/ZATO, 2026).

## What Google will tell you instead, and why we don't
Google's help shows labels as a way to build product groups *inside* one campaign and offers two margin values, LowMargin/HighMargin [Google docs]. Two margin values are too coarse to set tiers from break-even, and the canon uses labels to split campaigns and budgets, not just product groups: separate budgets and targets per margin tier are the whole point (Optmyzr, 2025; Williams/ZATO, 2026). Google also sources stock status automatically from the site; ZATO manages availability itself because automated sourcing "tends to introduce errors" and stock status decides eligibility (Williams/ZATO, 2026).

## Failure modes
- **Small catalogues / low volume.** Fewer than a few hundred SKUs or under a few conversions per tier per week: tiers never get data and bids are set on noise. Start coarser (two tiers) or don't tier (Vallaeys/PPC Hero, 2015).
- **Uniform margin.** Private-label single-category stores gain nothing from margin tiers; use stock and season only.
- **Zombie campaigns.** Building a separate campaign for low-volume items often cannibalises the main campaign, and PMax may already be correctly ignoring those SKUs; only run one when the audience, query and product cluster are genuinely different (Williams/ZATO, 2026). Rooijmans' low-volume-SKU script is the opposite play (Rooijmans, 2022); default to Williams unless you can show the items are starved rather than unwanted.
- **Stale dynamic labels.** Stock/promo labels on a once-daily feed are wrong for most of the day in fast-moving inventory; this is how you pay for clicks on products you cannot fulfil (Einwagner/smec, 2017; Rooijmans, 2022).
- **Label cap.** Marketplaces or auto-generated values (e.g. release year per SKU) blow past 1,000 values per label and get silently ignored [Google docs].
- **Treating the feed as the business lever.** If CVR or price is the problem, labels will relabel the problem (Williams/ZATO, 2026).

## What to measure
- POAS or profit-on-spend per margin tier, not blended ROAS (Rhodes, 2026; Optmyzr, 2025).
- Spend share and conversions by label, segmented in the product report; share of clicks in "Everything else" per campaign (Vallaeys/PPC Hero, 2015).
- Spend on `inventory_low` and on out-of-stock-at-click (Optmyzr, 2025).
- Bucket migration month over month: count moving costly → profitable and zombies → anything (Rhodes, 2026).

## Open disagreements in the canon
- **Low-volume products: campaign or leave alone?** Rooijmans/Google's script and Optmyzr's "Zombies" bucket say isolate and bid up (Rooijmans, 2022; Optmyzr, undated); Williams says that usually cannibalises and PMax already judged them (Williams/ZATO, 2026). Epiminds follows Williams: isolate only after step 3 shows the items get impressions elsewhere in the catalogue's query space but none here.
- **How many margin tiers.** Vallaeys: a handful, equal-sized (2015); Google: two [Google docs]. We use three to five, equal-sized, because a two-value split cannot express a break-even ladder.
- **Source of truth for stock.** Google automated sourcing vs ZATO's self-managed availability; we side with ZATO (Williams/ZATO, 2026).
