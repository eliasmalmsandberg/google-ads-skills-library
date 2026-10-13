# Dossier — 61 URL expansion off + final URL control

## Sources

1. **Source**: Kirk Williams, ZATO, "What are Page Feeds in Performance Max campaigns?" — https://zatomarketing.com/blog/what-are-page-feeds-performance-max-campaigns · **Tier** 1 · **Date** 2023-07-19, updated 2026-04-21 · **Claim**: With expansion on, Google can send traffic to any URL on the site — he has seen /photos/ and /login/ pages take PMax traffic. Build a landing-page report per PMax campaign by name (filtering by campaign type didn't work). Page feeds (announced Feb 2023) do three things: signal preferred pages, restrict non-product ads to labelled pages, or exclude pages; label unwanted URLs "exclude". For a few exclusions use native controls; for broad control use page feeds. Expansion off limits PMax to feed product URLs — "a good option in some set ups". · **Evidence or opinion**: Method; one-campaign examples; no data.

2. **Source**: Kirk Williams, ZATO, "Ghostbusters" — https://zatomarketing.com/blog/scaling-performance-max-campaigns-profitably-introducing-the-zato-ghostbusters-pmax-campaign · **Tier** 1 · **Date** 2023-03-14 · **Claim**: In a product-label-restricted PMax campaign, turn URL expansion off so the campaign stays on the labelled products. · **Evidence or opinion**: Method.

3. **Source**: Kirk Williams, ZATO, feed-only walkthrough — https://zatomarketing.com/blog/setting-up-feed-only-pmax-campaign-step-by-step-walkthrough · **Tier** 1 · **Date** 2023-08-08 · **Claim**: Opt out of automatically created assets in a feed-only build. · **Evidence or opinion**: Method.

4. **Source**: Diana Talhelm, ZATO, "PMax performance dropped? Here's what to audit first" — https://zatomarketing.com/blog/pmax-performance-dropped-heres-what-to-audit-first · **Tier** 1 (ZATO) · **Date** 2026-05-18 · **Claim**: Audit step: look for expanded landing pages with unusual traffic increases, weak engagement or poor conversion value; fix by excluding weak landing pages before touching budget or tROAS. · **Evidence or opinion**: Checklist.

5. **Source**: Aayushi Bhandari, Optmyzr — https://www.optmyzr.com/blog/manage-and-optimize-performance-max-campaigns/ · **Tier** 1 · **Date** 2026-09-08 · **Claim**: Recommends finding campaigns with Final URL expansion off and enabling it so Google can serve a more relevant page; Optmyzr monitors expanded pages separately with a landing-page health monitor. · **Evidence or opinion**: Vendor recommendation (dissent).

6. **Source**: Stewart Dunlop, PPC.io audit — https://ppc.io/blog/performance-max-audit · **Tier** added-Tier-2 · **Date** 2026-08-30 · **Claim**: 42 of 84 campaigns (50%) served at least one expanded URL. Recommends expansion off for lead gen and an exclusion list for e-commerce. · **Evidence or opinion**: Own-account data.

7. **Source**: Navah Hopkins, Optmyzr, Feb 2023 updates — https://www.optmyzr.com/blog/new-performance-max-updates/ · **Tier** 1 · **Date** 2023-02-28 · **Claim**: Page-feed targeting in PMax works like DSA and gives non-ecommerce advertisers focused control over which parts of the site get budget. · **Evidence or opinion**: Opinion.

8. **Source**: Mike Rhodes, PMax Insights — https://mikerhodes.com.au/scripts/help/pmax-insights/what-all-the-tabs-do · **Tier** 1 · **Date** 2026 · **Claim**: Pages tab shows which landing pages get traffic and which convert. · **Evidence or opinion**: Published tool.

## Dissenting view
Optmyzr (Bhandari, 2026) recommends turning expansion on for relevance; Williams (2023), Talhelm (2026) and PPC.io (2026) treat it as a leak to monitor or switch off. The disagreement is whether Google's page choice beats the advertiser's for the same query — and nobody in the canon has published a controlled comparison.

## What the platform currently does [Google docs]
- Final URL expansion is on by default; on = PMax may replace the final URL with a more relevant same-domain page and generate assets from it; off = traffic only to page-feed and asset-group URLs (https://support.google.com/google-ads/answer/14337539). Not supported for store-goal-only campaigns.
- URL exclusions: list URLs, use page-feed custom labels, or Rules (include a path, exclude pages under it); the campaign's own final URL cannot be excluded — to keep the homepage from serving, use a more specific final URL and exclude the homepage; with a Merchant Center feed the homepage may still serve on some inventory such as Shopping ads in Gmail (https://support.google.com/google-ads/answer/14337773).
- Text customization (formerly automatically created assets) is the toggle that lets Google generate headlines/descriptions/landing-page images; Google recommends keeping it on; for one specific landing page keep text customization on and expansion off; changes take 24–48 hours.
- Page feeds: with expansion on they help verify indexing but do not limit URLs; with expansion off, only feed and asset-group URLs serve.

## Baseline check
Read `google-ads-audit-ecommerce` (no URL expansion content) and `google-ads-keyword-cannibalization` (mentions DSA overlap). This skill adds the default-on fact, the exact exclusion mechanics and their gaps (final URL and homepage), the page-feed label method, and a by-account-type rule.

## Judgment calls
- Position: off for lead gen and for any product-restricted or feed-only campaign; on with exclusions and a page feed only for multi-category e-commerce with a clean URL structure. Grounded in Williams (2023), PPC.io (2026), and Google's own "expansion off = feed and asset-group URLs only".
- PPC.io's 50% figure is Tier 2 and own-account; used as a prevalence indicator only.
- Weekly landing-page review in month one; monthly after.

## Canon strength: Adequate

## Invalidated by
Google changing the default, allowing the final URL/homepage to be excluded, merging expansion into AI Max page controls, or removing page feeds from PMax.
