# Dossier — 56 Feed-only PMax

## Sources

1. **Source**: Kirk Williams, ZATO, "Setting Up a Feed Only PMax Campaign – Step-By-Step Walkthrough" — https://zatomarketing.com/blog/setting-up-feed-only-pmax-campaign-step-by-step-walkthrough · **Tier** 1 · **Date** 2023-08-08, updated 2024-04-15 · **Claim**: A PMax campaign with no static assets so it runs on the product feed, like Smart Shopping without the DSA element. Setup: opt out of automatically created assets; remove pre-filled final URL, images, videos, logos, headlines, long headlines, descriptions from the asset group; set location to Presence after publishing; add audience signals after publishing (adding during setup broke saving). When to consider: no good assets or brand-risky assets; assets fit only part of the catalogue; junk placements in the placement report; stagnating PMax; as a step beyond Standard Shopping — revert to Standard Shopping after 1–2 months without a clear winner because switching loses data. Risk: Google's Aug 2023 feed-generated assets (e.g. Shorts) may make "feed-only" nominal. · **Evidence or opinion**: Method; results anecdotal ("works the majority of the time").

2. **Source**: Kirk Williams, ZATO, "Here's why the new PMax channel reporting rocks" — https://zatomarketing.com/blog/heres-why-the-new-pmax-channel-reporting-rocks · **Tier** 1 · **Date** 2025-06-13, updated 2026-05-07 · **Claim**: The channel report separates product-feed-based ads from other assets per channel. Feed-only campaigns are not purely feed-based: in one client's feed-only campaign 1.7% of traffic was not from product-feed ads (auto-generated assets). "Shop cost" in Mike Rhodes' script was commonly misread as Google Shopping only — it includes feed-based ads on Display and YouTube. YouTube "other" had fewer clicks but far more interactions; interactions ≠ clicks. · **Evidence or opinion**: Single-account screenshot data.

3. **Source**: Kirk Williams, ZATO, "7 ways to structure PMax" — https://zatomarketing.com/blog/how-to-structure-performance-max-campaigns-7-ways · **Tier** 1 · **Date** 2023-08-22, updated 2026-04-21 · **Claim**: Feed-only (#5) suggested when assets are weak or placement reports show many non-Google placements; Google auto-generates Shorts from the feed so feed-only is eligible for Shorts. · **Evidence or opinion**: Experience.

4. **Source**: Miles McNair, PPC Mastery, "TPE #147: The Bottom-Up Funnel" — https://www.ppcmastery.com/newsletter/tpe-147-bottom-up-funnel · **Tier** 1 · **Date** 2026-06-22 · **Claim**: The bottom-of-funnel starting point for ecommerce is "Standard Shopping or feed-only pMax", starting with proven best-selling products/categories, then expanding. · **Evidence or opinion**: Framework/opinion.

5. **Source**: Navah Hopkins, Optmyzr, "Here's how you can profit from the latest updates to Performance Max" — https://www.optmyzr.com/blog/new-performance-max-updates/ · **Tier** 1 · **Date** 2023-02-28 · **Claim**: Advertisers can turn off automatically created creative; without video assets, YouTube placements are an expensive waste; PMax forces spend on networks a brand may not value. · **Evidence or opinion**: Opinion.

6. **Source**: Optmyzr, "Google Ads for BFCM 2026" — https://www.optmyzr.com/blog/google-ads-bfcm-2026/ · **Tier** 1 · **Date** 2026-09-22 (2025 peak, 4,200+ accounts) · **Claim**: YouTube drew nearly 10% of PMax impressions but ~2% of conversion value. PMax ROAS by network Oct/Nov/Dec: Search 732/768/760%, YouTube 573/626/555%, Discover 657/648/477%, Content 665/926/865%, Gmail 726/786/789%. PMax vs Standard Shopping: BFCM-four-days ROAS 660% vs 584%; mixed accounts Dec: PMax 680% vs SS 666% at identical $0.64 CPC. PMax Max Conv Value 735–765% vs Max Conversions 400–441%. · **Evidence or opinion**: Cross-account data.

7. **Source**: Manuel Baudisch, smec, "4 reasons why Google is no longer a Black Box" — https://smarter-ecommerce.com/blog/en/google-ads/4-reasons-why-google-is-no-longer-a-black-box-and-4-problems-that-still-exist/ · **Tier** added-Tier-2 · **Date** 2026-02-12 · **Claim**: Feed-only strips images/video/text so PMax relies on the Merchant Center feed, focusing spend on Shopping and avoiding weak Display/Video inventory; Google reports channel volume but not channel ROAS/CPA — compute it yourself. · **Evidence or opinion**: Vendor FAQ; no data.

8. **Source**: Stewart Dunlop, PPC.io audit — https://ppc.io/blog/performance-max-audit · **Tier** added-Tier-2 · **Date** 2026-08-30 · **Claim**: Cites a smec study of 4,000 campaigns finding a median 90% of PMax cost on feed-based ads in retail accounts (secondhand; smec source not fetched). · **Evidence or opinion**: Secondhand.

## Dissenting view
Optmyzr's guide quotes Kirk Williams that low YouTube ROAS is usually the wrong reason to switch video off, and Google's own line is that full assets outperform (Optmyzr guide, 2026) [Google docs]. The disagreement is whether non-feed channels are incremental reach worth paying for at lower measured ROAS, or dilution of a Shopping budget — and whether "feed-only" even stays feed-only now that Google generates assets from the feed.

## What the platform currently does [Google docs]
- Text customization (formerly automatically created assets) and Final URL expansion are campaign settings; when text customization is on Google may generate headlines, descriptions and landing-page images; disable it (and "Landing page images") to prevent auto-generated text/images; Google recommends keeping it on (https://support.google.com/google-ads/answer/14337539).
- With Final URL expansion off, traffic goes only to feed and asset-group URLs (same page).
- Channel performance report: cost/conversions/value by channel, segmentable by "ads using product data" and "ads using video"; product-data video on YouTube and product-data ads in Gmail not yet classified as product-data (https://support.google.com/google-ads/answer/16683501, /answer/16260130); data from 2025-06-06.
- Google states a channel with no ads usually means PMax is prioritising higher-predicted-ROI channels, and that budget cannot be set per channel.
- Aug 2023 (per Williams): Google began auto-generating video (e.g. Shorts) from feed images.

## Baseline check
Read `google-ads-audit-ecommerce` (PMax asset-group checklist assumes full assets per category; Standard Shopping priority structure) — it does not mention feed-only or channel reporting. This skill adds the setup specifics, the entry/exit rules, the channel-report verification (feed vs non-feed share) and the evidence on YouTube value share.

## Judgment calls
- Entry threshold: no canon number; skill uses "no usable video/brand-safe assets" or "non-feed channels carrying >15% of spend with ROAS below the Search channel" — the 15% comes from Pooler's placement flag in Optmyzr's guide, repurposed and labelled as such.
- Exit rule: Williams' 1–2 months without a clear winner → revert.
- Secondhand smec 90% figure is quoted as secondhand only.
- Verification: 14 days from Google's 1–2 week stabilisation note (channel report doc); 5% non-feed trigger is an Epiminds rule set at ~3× Williams' observed 1.7% floor. "Feed-only = Standard Shopping with less control" for small catalogues is labelled as Epiminds' view.

## Canon strength: Adequate

## Invalidated by
Google removing the ability to opt out of auto-generated assets (making feed-only impossible), changing the channel report's product-data segmentation, or deprecating Standard Shopping (removing the comparison campaign).
