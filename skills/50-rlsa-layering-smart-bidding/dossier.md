# Dossier — 50 RLSA layering under Smart Bidding

Research note: shared WebSearch budget was exhausted during this category; sourcing was by direct fetch of canon archives and Google docs. No canon source has a 2024+ piece titled on RLSA specifically; the material is the RLSA-relevant parts of pieces on bid adjustments, exclusions and remarketing.

## Sources

1. **Source**: Miles McNair, PPC Mastery, TPE #145 "Why bid adjustments are dead and what to do instead", https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: Bid adjustments still work under Manual CPC and Maximize Clicks; under tCPA, tROAS, Max Conversions, Max Conversion Value and Target Impression Share they are mostly ignored while the UI still offers them; Smart Bidding already evaluates demographics, conversion-path history and deeper audience segments at auction time. Exceptions: Max Clicks respects all; device adjustments under tCPA act as target adjustments; -100% device works everywhere as an exclusion. Conversion value rules (Max Conv Value / tROAS only) can apply to audiences, one rule per conversion, with audience hierarchy Customer Match → your data/similar → affinity/in-market → detailed demographics; he generally advises against them because reported values inflate (50% rule on €100 reports €150). Adjustments compound multiplicatively (+25% mobile, +15% evenings, +10% Amsterdam). · **Evidence or opinion**: Practitioner position; no study.

2. **Source**: Navah Hopkins, Search Engine Land, "A PPC guide to permission-based audiences", https://searchengineland.com/a-ppc-guide-to-permission-based-audiences-391228 · **Tier** 1 · **Date** 2023-01-12 · **Claim**: Native audiences are built into Smart Bidding; observation mode's purpose is to see composition and exclude undesirable segments; "either exclude and let Smart Bidding work, or use manual bidding with audiences as bid adjustments"; targeting only native audiences in observation forfeits the algorithmic audiences. · **Evidence or opinion**: Opinion.

3. **Source**: Sarah Vlietstra, ZATO, "Precision Bidding: How to Use Conversion Value Rules Effectively", https://zatomarketing.com/blog/precision-bidding-how-to-use-conversion-value-rules-effectively · **Tier** 1 (ZATO) · **Date** 2026-10-07 · **Claim**: Value rules can be audience-, device- or location-based with an optional secondary condition (both must hold); multiply by <1 to down-value conversions from users "already in your remarketing list"; the feature "has limited benefit" and should only carry information Smart Bidding cannot already infer. · **Evidence or opinion**: Method; no data.

4. **Source**: Sarah Vlietstra, ZATO, "Stop Wasting Ad Spend: A Guide to Audience Segment Exclusions", https://zatomarketing.com/blog/stop-wasting-ad-spend-a-guide-to-audience-segment-exclusions · **Tier** 1 (ZATO) · **Date** 2026-08-19 · **Claim**: In remarketing campaigns exclude purchasers and form submitters; if non-brand budget is tight, test excluding all past site visitors from non-brand; exclude login-portal brand searchers from brand/Shopping. · **Evidence or opinion**: Method; no data.

5. **Source**: Kirk Williams, ZATO, "eCommerce Remarketing in Google Ads: What Actually Works", https://zatomarketing.com/blog/ecommerce-remarketing-in-google-ads-what-actually-works · **Tier** 1 · **Date** 2026-04-28 · **Claim**: Keep past converters as a distinct segment with a deliberate strategy rather than excluding them; build lists on the Google Tag; PMax may be absorbing standalone remarketing. · **Evidence or opinion**: Experience across managed accounts.

6. **Source**: Andrea Cruz, Search Engine Land, "Google Ads for B2B: How to overcome challenges, platform limitations", https://searchengineland.com/google-ads-for-b2b-how-to-overcome-challenges-platform-limitations-386740 · **Tier** 1 · **Date** 2022-07-26 · **Claim**: Layer segments on Search and lower bids on weak ones rather than excluding; raise on segments bringing a disproportionate share of quality traffic. · **Evidence or opinion**: Experience, "hundreds of B2B accounts"; pre-dates Search auto-inclusion of Customer Match (Q3 2023).

## Dissenting view
Cruz (2022) treats audience bid adjustments on Search as the working lever; McNair (2026) says they are ignored under Smart Bidding. The disagreement is about whether the practitioner's bid adjustment adds information Smart Bidding does not already have; Google's own statement that observed first-party segments are Smart Bidding signals and that bids are optimized on remarketing-list membership (7065882, 7365594) sides with McNair. Newer beats older here because the platform changed in between.

## What the platform currently does [Google docs]
- Observation is the recommended setting for Search and Shopping; targeting restricts reach; observation cannot be added at ad-group creation; for Smart Bidding campaigns, first-party segments in observation are used as signals. (https://support.google.com/google-ads/answer/7365594)
- Smart Bidding optimizes bids on remarketing-list membership for Search, Display and Hotel; device targets can be set under tCPA. (https://support.google.com/google-ads/answer/7065882)
- Since Q3 2023 Search campaigns on Smart Bidding automatically use all Customer Match lists as signals whether or not applied. (https://support.google.com/google-ads/answer/10550383)
- Your-data segments can be excluded at campaign or ad-group level in Search; exclusions may not apply to users opted out of ads personalization. (2549058)
- Search supports affinity, in-market, detailed demographics and your data; not custom segments or life events. (2497941)
- Similar segments retired; optimized targeting on by default outside Search. (12463119)

## Baseline check
Read `google-ads-audiences` (RLSA table: "Observation — always, no downside"; bid-modifier table +15% to +100%; "shift high-value audiences to Targeting after 30 days") and `google-ads-audit-leadgen` ("+20–40% for pricing page visitors"). Both assume bid modifiers are honoured and recommend them as the RLSA mechanism. This skill replaces that with the three-way decision (observation / targeting / exclusion) under Smart Bidding, where positive modifiers do nothing, and gives the conditions under which targeting mode or a separate campaign is justified.

## Judgment calls
- Treated -100% on an audience as functionally identical to an exclusion for decision purposes, by analogy to McNair's device -100% rule, and labelled the analogy.
- No canon source gives a volume threshold for splitting a targeted RLSA campaign; the skill expresses it in conversions per month relative to the account's Smart Bidding floor and labels it an Epiminds operating threshold.

## Canon strength: Adequate
Five Tier 1 sources with positions and method; no cross-account evidence on bid-adjustment behaviour under Smart Bidding.

## Invalidated by
Google documenting that Smart Bidding honours audience bid adjustments (other than -100%); removal of observation mode from Search; conversion value rules becoming available on tCPA / Max Conversions; Google ending automatic use of Customer Match / first-party lists as Search signals.
