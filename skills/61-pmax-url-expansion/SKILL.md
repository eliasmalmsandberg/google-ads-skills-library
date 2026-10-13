---
name: pmax-url-expansion
id: 61
description: Decide the Final URL expansion setting for a Performance Max campaign by account type, and lock down where traffic can land with exclusions and page feeds. Not for DSA, and not for asset-text generation beyond its link to expansion.
tags: Setting / PMax / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: A change to the default-on setting; the ability to exclude the campaign's own final URL or homepage; expansion folding into AI Max page controls; removal of page feeds from PMax.
---
## What this is
Final URL expansion is on by default and lets PMax swap your final URL for any same-domain page it judges more relevant, and generate text and images from that page [Google docs]. Kirk Williams has watched it send PMax traffic to /photos/ and /login/ pages (Williams/ZATO, 2023); half of 84 audited campaigns had served at least one expanded URL (Dunlop/PPC.io, 2026). Off, traffic goes only to page-feed and asset-group URLs [Google docs]. This skill sets the switch by account type and closes the gaps the exclusions leave.

## Where it comes from
Kirk Williams (ZATO, 2023 page-feeds post; 2023 Ghostbusters; 2023 feed-only) for the leak evidence, page-feed method and when to switch off; Diana Talhelm (ZATO, 2026) for the audit step; PPC.io (Dunlop, 2026) for prevalence and the lead-gen rule; Navah Hopkins (Optmyzr, 2023) on page feeds as DSA-style targeting; Mike Rhodes' Pages tab (2026) for monitoring. Optmyzr (Bhandari, 2026) supplies the dissent.

## When to use it / when not to
Use at every PMax build and whenever a landing-page report shows pages you did not choose. Not relevant to store-goal-only campaigns, where expansion is unsupported [Google docs].

## Inputs
- Account type: lead gen, feed-only/product-restricted e-commerce, or multi-category e-commerce.
- Site URL structure (does path = category? are there /account, /login, /careers, /blog paths?).
- Landing-page report built per PMax campaign by name (Williams/ZATO, 2023) or Rhodes' Pages tab (Rhodes, 2026).
- Page feed CSV with labels (Williams/ZATO, 2023).

## Method
1. **Set the switch by account type.**
   - Lead gen: off (Dunlop/PPC.io, 2026). One or two conversion pages; everything else is a leak.
   - Feed-only or product-label-restricted e-commerce: off, so the campaign stays on the labelled products' URLs (Williams/ZATO, 2023 Ghostbusters; feed-only walkthrough, 2023).
   - Multi-category e-commerce with a logical URL structure: on, with the exclusions in steps 3–4 and a page feed (Williams/ZATO, 2023; Dunlop/PPC.io, 2026). Williams notes the rules approach "falls apart" when URLs are not structured — then switch off.
2. **Set text customization consistently.** Expansion and text customization are separate toggles; Google's own guidance for a single landing page is text customization on, expansion off [Google docs]. For feed-only builds opt out of automatically created assets entirely (Williams/ZATO, 2023).
3. **Exclude the structural leaks** when expansion is on: account, login, cart/checkout, careers, blog, support, media/photo paths, via Rules (include the path, exclude pages under it) or explicit URLs [Google docs]. Google's own example is a careers page.
4. **Handle the two things exclusions cannot do.** The campaign's final URL cannot be excluded, and the homepage may still serve on some inventory when a Merchant Center feed is attached [Google docs]. So never set the homepage as the asset group's final URL; use the most specific category page and exclude the homepage explicitly [Google docs].
5. **Use a page feed for broad control** (Williams/ZATO, 2023): label good pages by category and unwanted pages "exclude"; with expansion on it signals preferred pages and can restrict non-product ads to labelled pages; with expansion off it is the whitelist [Google docs]. Hopkins frames this as DSA-style control for non-ecommerce sites (Hopkins/Optmyzr, 2023).
6. **Monitor landing pages weekly in month one, monthly after.** Flag any expanded page with an unusual traffic increase, weak engagement or low conversion value, and exclude it before touching budget or tROAS (Talhelm/ZATO, 2026). Filter the report by campaign name; campaign-type filters did not work for Williams (Williams/ZATO, 2023).
7. **Expect a 24–48 hour lag** after changing either toggle [Google docs]; do not judge the effect inside that window.

## What Google will tell you instead, and why we don't
Google ships expansion on, recommends keeping text customization on for performance, and Optmyzr's product guidance follows it — find campaigns with expansion off and enable it (Bhandari/Optmyzr, 2026) [Google docs]. We switch it off for lead gen and product-restricted campaigns because the leak is documented (Williams/ZATO, 2023), common (Dunlop/PPC.io, 2026), and the exclusion tooling cannot close the homepage and final-URL gaps [Google docs]. Nobody in the canon has published a controlled test showing Google's page choice converts better; until one exists, the advertiser's page wins.

## Failure modes
- **Multi-category stores with unstructured URLs**: rules cannot describe what to exclude; switch off instead (Williams/ZATO, 2023).
- **Marketplaces, multi-brand or multi-domain sites**: Google itself warns of mismatched generated headlines; use generic descriptions or a page feed [Google docs].
- **Expansion off with a thin page feed**: with expansion off, only page-feed and asset-group URLs can serve [Google docs], so a feed of a handful of pages is the whole eligible site.
- **Store-goal campaigns**: setting unsupported [Google docs].
- **Switching settings and judging too soon**: changes to either toggle take 24–48 hours to apply [Google docs]; a landing-page read inside that window reflects the old setting.

## What to measure
Share of PMax clicks on URLs not in the asset group or page feed (target zero when off; falling when on). Conversion rate of expanded vs chosen pages. Count of excluded URLs/rules. Time since last landing-page review.

## Open disagreements in the canon
Optmyzr (Bhandari, 2026) says turn it on for relevance; Williams (2023), Talhelm (2026) and PPC.io (2026) treat it as a leak. Epiminds goes off for lead gen and restricted campaigns and on-with-fences only for structured multi-category stores, because the leak is evidenced and the relevance gain is not.
