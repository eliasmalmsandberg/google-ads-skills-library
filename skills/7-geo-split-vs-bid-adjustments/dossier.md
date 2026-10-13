# Dossier — 7 Geo-split campaigns vs. bid adjustments

## Sources

1. **Source**: Brad Geddes (Adalysis), "Google Ads Account Organization" workshop slides — https://presentations.boussiasevents.gr/files/_boussias_conferences_content/presentations/google_marketing_conference/2020/day2/workshop_brad_geddes_googleMKT_20.pdf · **Tier**: 1 · **Date**: 2020 · **Claim**: Location options: one campaign per location is easier to adjust, test and budget but means more campaigns; one campaign with ad customizers means fewer campaigns but some ads will not show properly. Create a new campaign for a different geo, budget control, network or targeting type. Put top regions in high-budget campaigns and secondary regions in lower-budget ones; shared budgets help. Geographic ad groups can sit inside a formula-based structure (the plumber rebuild used service × modifier plus geo ad groups). "Never an absolute"; over-engineering can leave zero ads showing. · **Evidence or opinion**: Method; one account example.

2. **Source**: Fred Vallaeys with Shawn Walker, Optmyzr PPC Town Hall — https://www.optmyzr.com/ppctownhall/practical-advice-on-how-to-actually-make-smart-bidding-work-for-you · **Tier**: 1 · **Date**: 2025-01-29 · **Claim**: Separate campaigns only for own budget, targeting not settable at ad-group level (geo is one), or materially different performance; ≥30 conversions/campaign/30 days. Against Google's "let the algorithm find customers": explicitly target known high-performing locations, income brackets and in-market segments and use exclusions rather than observation. · **Evidence or opinion**: Opinion with practice.

3. **Source**: Navah Hopkins, Optmyzr, bidding-strategy study — https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier**: 1 · **Date**: 2024-09-24 · **Claim**: 50+ conversions/30 days per campaign is where any bidding strategy becomes predictably successful; <25 never beats 50+; targets/bid caps more often hurt. · **Evidence or opinion**: 14,584-account study.

4. **Source**: Nils Rooijmans, "[AMA] What settings do you immediately change when taking over an account?" — https://nilsrooijmans.com/daily/ama-what-settings-do-you-immediately-change-when-taking-over-an-account · **Tier**: 1 · **Date**: 2026-06-17 · **Claim**: Change location targeting from "Presence or interest" to "Presence" — otherwise you pay for clicks from people merely interested in a location "unless fraudulent clicks are part of your growth strategy". · **Evidence or opinion**: Practice.

5. **Source**: Google Ads Help, "About bid adjustments" (answer 2732132) — https://support.google.com/google-ads/answer/2732132 · **Tier**: Reference only · **Date**: current 2026-10-13 · **Claim**: Location bid adjustments range −90% to +900%, campaign level, most specific overrides. Under Target CPA, Target ROAS and Maximize Conversions, location, ad-schedule, audience, call and demographic bid adjustments are not supported ("won't be supported"); only Maximize Clicks uses them. Device: tCPA uses device adjustments to modify the CPA target; tROAS/Max Conversions/Max Conversion Value/Target IS allow only −100%. Ad schedules are enforced as serving windows, not multipliers. Where −100% is not possible, Smart Bidding still honours targeting and exclusions. · **Evidence or opinion**: Platform statement.

6. **Source**: Google Ads Help, "The ABCs of Account Structure" (answer 14752782) — https://support.google.com/google-ads/answer/14752782 · **Tier**: Reference only · **Date**: data Jan–Feb 2023 · **Claim**: Remove device segmentation because Smart Bidding already factors device; segment campaigns by business objective only. · **Evidence or opinion**: Platform guidance.

## Dissenting view
Google: do not segment by geo/device; the bidder handles it; location bid adjustments are not even used under tCPA/tROAS. Vallaeys/Walker (2025): target and exclude explicitly rather than trusting observation. Geddes (2020): split when a geo needs its own budget. The disagreement is about whether "Smart Bidding factors in location" is sufficient when the business needs a geo to get a fixed share of budget or its own message — the canon says the bidder's weighting is not a budget guarantee.

## What the platform currently does [Google docs]
- Location bid adjustments are ignored under tCPA/tROAS/Max Conversions/Max Conversion Value; only Max Clicks (and manual) use them; −100% device opt-out works everywhere; schedules act as on/off windows (answer 2732132). [Google docs]
- Location option "Presence or interest" is the default; "Presence" must be set per campaign (Rooijmans, 2026). [Google docs]
- Location targeting, exclusions and campaign budgets remain campaign-level settings — the reason geo cannot be an ad-group split (Vallaeys/Walker, 2025). [Google docs]

## Baseline check
Read `google-ads-segmentation` (geo tiering by CPA ratio, modifiers −20–35%, split when a city drives 30%+ revenue; says Smart Bidding "automatically accounts for" location and manual modifiers "still apply on top"). The baseline is wrong on the last point for tCPA/tROAS: Google states location adjustments are not supported there. This skill adds that platform fact, the canon's split rule (budget, campaign-level targeting, materially different performance), the per-campaign volume floor the split must clear, the "Presence" setting, and Geddes's two-model trade-off (campaign per location vs ad customizers).

## Judgment calls
- The decision rule is built around the Google doc fact (adjustments ignored under Smart Bidding) plus canon volume thresholds; no canon source gives a geo-specific CPA-ratio threshold, so the skill does not invent one — it uses the campaign-existence rule instead.
- Campaign type "All" in the row: the skill is written for Search and Shopping campaign-level geo settings; PMax geo is settings-only and the same rule applies.

## Canon strength: Adequate
Geddes (method), Vallaeys/Walker (opinion), Hopkins/Optmyzr (volume evidence), Rooijmans (practice); Google docs supply the mechanism.

## Invalidated by
Google re-enabling location bid adjustments under Smart Bidding, ad-group-level location targeting, or per-geo budget allocation inside one campaign.
