---
name: feed-only-pmax
id: 56
description: When to run a Performance Max campaign with no creative assets (feed-only), how to build it so it stays feed-only, and how to verify with the channel report that it did. Not for lead-gen PMax, and not a Standard Shopping vs PMax decision on its own.
tags: Strategy / PMax / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google removing the opt-out from auto-generated assets; a change to the channel report's "ads using product data" segmentation; deprecation of Standard Shopping as the comparison campaign.
---
## What this is
A PMax campaign stripped of every static asset so it serves from the Merchant Center feed — Smart Shopping without the DSA layer (Williams/ZATO, 2023). It is not purely feed-only any more: Google generates assets from the feed, and in one of Williams' feed-only campaigns 1.7% of traffic came from non-feed ads (Williams/ZATO, 2025). The point is control over where the budget goes: non-feed channels carry measurably weaker value — YouTube drew ~10% of PMax impressions but ~2% of conversion value across 4,200 accounts in the 2025 peak (Optmyzr, 2026).

## Where it comes from
Kirk Williams (ZATO, 2023 walkthrough; 2023 structures; 2025 channel report) for setup, entry/exit rules and the feed-vs-non-feed reading; PPC Mastery (McNair, 2026) for where feed-only sits in the funnel; Navah Hopkins (Optmyzr, 2023) on forced video spend; Optmyzr's BFCM data (2026) for channel value shares; smec (Baudisch, 2026) for the rationale.

## When to use it / when not to
Use when an e-commerce account has no usable or brand-safe creative, when assets fit only part of the catalogue, when the placement report is full of junk, or when a full-asset PMax has stagnated and you want a structural change (Williams/ZATO, 2023). PPC Mastery treats "Standard Shopping or feed-only PMax" as the bottom-of-funnel starting point before any asset-heavy campaign (McNair/PPC Mastery, 2026). Do not use for lead gen (no feed) or for brands whose incremental growth is coming from video — Williams says low YouTube ROAS alone is usually the wrong reason to cut video (Williams in Optmyzr guide, 2026).

## Inputs
- Merchant Center feed with approved products; product-type hierarchy and custom labels for listing groups.
- Channel performance report for any existing PMax (cost, conversions, value by channel, segmented by "ads using product data") [Google docs].
- Placement report for the existing PMax.
- Standard Shopping performance for the same products as the comparison baseline.

## Method
1. **Decide entry.** Build feed-only if any of: (a) no video or brand-safe image assets exist; (b) the existing PMax's non-feed channels (Display, YouTube "other", Discover, Gmail) take more than 15% of cost with ROAS below the Search channel in the channel report (15% borrowed from the Pooler placement flag in Optmyzr's guide, 2026); (c) the placement report shows many non-Google placements (Williams/ZATO, 2023). Otherwise keep full assets and fix the assets.
2. **Build it so it stays feed-only** (Williams/ZATO, 2023):
   - Campaign settings: opt out of automatically created assets / text customization, and switch off "Landing page images" [Google docs]; turn Final URL expansion off so traffic goes only to feed URLs [Google docs].
   - Asset group: remove the pre-filled final URL, images, videos, logos, headlines, long headlines and descriptions. Logos may auto-apply if the account opted in; remove them.
   - Location: set advanced targeting to Presence after publishing.
   - Audience signals: add after publishing, not during setup (saving failed for Williams when added during creation).
   - Bidding: Maximise conversion value with a tROAS — Max Conversions ran at 400–441% ROAS vs 735–765% for Max Conversion Value in PMax across Optmyzr's 2025 peak data (Optmyzr, 2026).
3. **Structure listing groups by what you want to control**, not by everything: start with proven sellers (McNair/PPC Mastery, 2026); segment by product type when buyer groups differ, or by historical performance buckets (Williams/ZATO, 2023).
4. **Verify after 14 days** in the channel report: share of cost on "ads using product data" should be near 100%; non-feed share above ~5% means an opt-out was missed or Google is generating assets — check the Assets view for auto-generated video (Williams/ZATO, 2025) [Google docs]. Note that "Shop cost" in Rhodes' script, and feed-based cost in the channel report, include feed ads on Display and YouTube, not just Google Shopping (Williams/ZATO, 2025).
5. **Compare against Standard Shopping on the same products** for 1–2 months. Optmyzr's mixed-account December data had PMax 680% vs Standard Shopping 666% ROAS at identical $0.64 CPCs — the two are close, so the comparison must be on your own products (Optmyzr, 2026). If there is no clear winner after 1–2 months, revert to Standard Shopping; every further switch loses learning (Williams/ZATO, 2023).
6. **Exit to full assets** only when you have a video or image set that fits the products in the asset group, and then as a separate asset group or campaign so the feed-only read survives (Williams/ZATO, 2023).

## What Google will tell you instead, and why we don't
Google recommends keeping text customization on "for better performance" and treats an empty channel as PMax choosing higher-ROI inventory [Google docs]. We switch the generation off and accept the narrower campaign because PMax forces spend onto networks you may not value (Hopkins/Optmyzr, 2023), the non-feed channels carry a fraction of the value they take in impressions (Optmyzr, 2026), and Google reports channel volume but not channel ROAS, so the dilution is invisible unless you compute it (Baudisch/smec, 2026).

## Failure modes
- **Catalogues with strong video creative and proven YouTube incrementality**: you remove the channel that was driving new demand (Williams in Optmyzr guide, 2026).
- **Small catalogues or single-product stores**: a feed-only PMax is a Standard Shopping campaign with less control; run Standard Shopping.
- **Accounts that opted into auto-generated logos/video**: the campaign quietly becomes full-asset; verify in step 4 (Williams/ZATO, 2025).
- **Expecting Shopping-only placements**: feed ads still serve on Display and YouTube as dynamic product ads (Williams/ZATO, 2025).
- **Switching every month**: data loss on each flip; hold the 1–2 month window (Williams/ZATO, 2023).

## What to measure
Cost share on "ads using product data" vs other (channel report), weekly. ROAS per channel computed by hand (cost and value by channel). Feed-only PMax vs Standard Shopping ROAS and CPC on matched products over 4–8 weeks. Count of auto-generated assets appearing in the Assets view.

## Open disagreements in the canon
Williams (2023, 2025) and McNair (2026) treat feed-only as a legitimate default for e-commerce; Williams also warns (in Optmyzr's guide, 2026) against turning off video on ROAS alone, and Hopkins (2023) regards forced video spend as waste without good assets. Epiminds goes feed-only when the assets are absent or weak, and full-asset only with creative that fits the asset group — the asset quality decides, not the channel ROAS by itself.
