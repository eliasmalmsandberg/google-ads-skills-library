# Dossier — 58 Asset groups by product vs. by audience

## Sources

1. **Source**: Kirk Williams, ZATO, "Asset Groups in Google Performance Max Campaigns" — https://zatomarketing.com/blog/asset-groups-in-google-performance-max-campaigns · **Tier** 1 · **Date** 2022-04-21, updated 2023-03-14 · **Claim**: Asset groups can be split by product via listing groups, but you cannot pair specific assets with specific audiences for the same product: audience signals are generalised, and an asset group can show to any audience the algorithm deems viable. Example: road-cycling imagery served to families, family videos to commuters. Google recommends not placing the same products in multiple asset groups; Williams argues this ignores how different audiences buy the same product. Ginny Marvin (Google) replied: audience signals aren't hard targets, multiple asset groups can carry tailored messaging, the system learns from non-converting combinations. · **Evidence or opinion**: Illustrative scenario; public exchange with Google.

2. **Source**: Kirk Williams, ZATO, "7 ways to structure PMax" — https://zatomarketing.com/blog/how-to-structure-performance-max-campaigns-7-ways · **Tier** 1 · **Date** 2023-08-22, updated 2026-04-21 · **Claim**: Use product types for asset groups ("natural audience segmentation built into the products", more control over assets and landing pages per group) and historical-performance buckets (Heroes/Sidekicks/Villains/Zombies) for campaign structure. Product type needs at least three hierarchy tiers; custom labels limited to five. Segmenting by product type is not useful for a narrow catalogue. · **Evidence or opinion**: Experience; cites ProductHero (2021) and Miles McNair for the performance buckets.

3. **Source**: Optmyzr PMax guide (quotes Jyll Saskin Gales, Kirk Williams) — https://www.optmyzr.com/guide/performance-max/ · **Tier** 1 (Optmyzr) · **Date** updated 2026-09-30 · **Claim**: Create a new asset group when messaging, audience intent or product focus differs. Saskin Gales' audit example: three asset groups with identical assets and only different audience signals is redundant. Large advertisers layer multiple campaigns with asset groups; SMBs use one campaign filtered to a few products. Flag if >80% of spend sits in the top 20% of products or asset groups. · **Evidence or opinion**: Practitioner heuristics.

4. **Source**: Aayushi Bhandari, Optmyzr, "How to Manage and Optimize Your Performance Max Campaigns" — https://www.optmyzr.com/blog/manage-and-optimize-performance-max-campaigns/ · **Tier** 1 · **Date** 2026-09-08 · **Claim**: Duplicating the same assets across asset groups with only the audience signal changed creates redundancy, not segmentation. · **Evidence or opinion**: Vendor guidance.

5. **Source**: Mike Rhodes, PMax Insights script page — https://mikerhodes.com.au/scripts/pmax · **Tier** 1 · **Date** 2026 · **Claim**: Asset Groups tab reports spend, clicks, conversions, ROAS and AOV (Shopping) per asset group; Assets tab shows which video assets are yours vs auto-generated. · **Evidence or opinion**: Published tool.

6. **Source**: Navah Hopkins, Optmyzr, Feb 2023 updates — https://www.optmyzr.com/blog/new-performance-max-updates/ · **Tier** 1 · **Date** 2023-02-28 · **Claim**: Asset-group-level reporting and budget pacing added Feb 2023; audience signals can hurt performance after the learning period (her view). · **Evidence or opinion**: Opinion.

7. **Source**: Kirk Williams, ZATO, "Ghostbusters" — https://zatomarketing.com/blog/scaling-performance-max-campaigns-profitably-introducing-the-zato-ghostbusters-pmax-campaign · **Tier** 1 · **Date** 2023-03-14 · **Claim**: Audit anecdote: 350K products in one PMax campaign and one asset group; only 50 had sales in 30 days, ~1,200 any clicks. · **Evidence or opinion**: Single-account anecdote.

## Dissenting view
Williams (2022) wants audience-specific asset groups for the same products and argues Google's "don't duplicate products" guidance oversimplifies; Saskin Gales and Bhandari (Optmyzr, 2026) say audience-only splits with duplicated assets are redundant. Ginny Marvin (Google) says multiple asset groups can carry tailored messaging but signals are not targets. The disagreement is whether audience signals are strong enough to make an audience-split asset group behave differently from a product-split one.

## What the platform currently does [Google docs]
- Audience signals are optional hints; PMax "may show ads to relevant audiences outside of your signals" (https://support.google.com/google-ads/answer/14530785).
- Asset group reporting: conversions, conversion value, conversion rate, cost per conversion at asset-group level; Google warns against removing asset groups on higher CPA/lower ROAS alone; conversions are not split across ad components (https://support.google.com/google-ads/answer/13872527). Reporting added Feb 2023 (Hopkins).
- Google's asset-group best-practice page could not be fetched; Williams (2022) reports Google recommends not placing the same products in multiple asset groups.
- Listing groups filter products per asset group; campaign limit of asset groups per campaign not verified in fetched pages.

## Baseline check
Read `google-ads-audit-ecommerce` (checklist: "separate asset groups per product category", "listing group filters", "audience signals per asset group", "high-margin isolated in own asset group"). This skill adds why product-split beats audience-split (signals are not targets, the Marvin exchange), the redundancy rule, the three-tier product-type and five-label constraints, and the reporting caveats.

## Judgment calls
- Position: structure asset groups by product/landing-page group; audience-split only when creative genuinely differs and you accept the same products appearing in more than one group (Williams' case). Grounded in Williams 2023 and the Optmyzr redundancy rule.
- No canon number for asset groups per campaign; the skill gives a rule (one per creative+landing-page+product set that differs) rather than a count.
- Hopkins' "signals can hurt after learning" is recorded, not adopted.

- Unit rule ("differs on at least two of product subset / landing page / creative") is an Epiminds rule derived from Optmyzr's "when messaging, audience intent or product focus differs" plus the Saskin Gales redundancy rule. 60-day signal review = two 30-day dead-weight cycles (Epiminds rule). The 80%-catalogue-fit wording and the "two or three" lead-gen count were cut as unsourced.

## Canon strength: Adequate

## Invalidated by
Google making audience signals hard targets or adding asset-group-level bidding targets (both of which Williams asked for), or changing listing-group mechanics.
