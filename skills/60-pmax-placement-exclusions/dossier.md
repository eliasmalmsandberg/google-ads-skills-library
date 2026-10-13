# Dossier — 60 PMax placement exclusions & display/video spend

## Sources

1. **Source**: Nils Rooijmans, "How To Exclude Website Placements from your Performance Max Campaigns" — https://nilsrooijmans.com/how-to-exclude-website-placements-from-your-performance-max-campaigns/ · **Tier** 1 · **Date** 2024-12-21, modified 2025-01-29 · **Claim**: PMax placement exclusions can only be set at account level (All campaigns → Content → Exclusions → Account); not per campaign. Reasons: brand suitability, irrelevant audience (exotic TLDs like .xyz/.tk), cost control, compliance. His view: PMax maximises spend, not profit. · **Evidence or opinion**: Method; client examples; no numbers.

2. **Source**: Nils Rooijmans, "Google Ads Script – PMax Placement Exclusion Suggestions v1.2.6" — https://nilsrooijmans.com/google-ads-script-pmax-placement-exclusion-suggestions/ · **Tier** 1 · **Date** 2024-12-14, modified 2025-05-27 · **Claim**: Reads `performance_max_placement_view` (impressions only; no cost). Defaults: 30-day lookback (7 for weekly runs), MIN_IMPRESSIONS 1. Flags: TLD outside .com/.edu/.org/.net/.nl/.be; domain <3 or >25 chars, hyphens, 3+ consecutive digits, 3+ repeated characters, punycode; spammy/adult/phishing/scam words in the domain; YouTube videos with political/clickbait titles, "!!"/"??", heavy caps, currency+digits, language outside EN/ES, made-for-kids; all mobile app placements flagged ("almost certainly low conversion value"). Emails a sheet; does not apply exclusions. · **Evidence or opinion**: Published script; app claim unsupported by data.

3. **Source**: Nils Rooijmans, "Excluding all Mobile App Placements… the quicker and easier way" — https://nilsrooijmans.com/excluding-all-mobile-app-placements-the-quicker-and-easier-way/ · **Tier** 1 · **Date** 2025-01-01, modified 2025-10-28 · **Claim**: Paste his sheet of ~140 mobile app category placements into account-level exclusions in one go. · **Evidence or opinion**: Method.

4. **Source**: Mike Rhodes, PMax Insights script page — https://mikerhodes.com.au/scripts/pmax · **Tier** 1 · **Date** 2026 · **Claim**: Placements tab lists websites, YouTube channels and apps, defaulting to placements spending more than $0.10/day (configurable), with a link to the PMax Exclusions form; Spend by Channel tab tracks shopping/video/display/search-other share over time; Assets tab shows video assets with spend and whether each is yours or auto-generated. · **Evidence or opinion**: Published tool. (Free v28 code on GitHub pulls campaign cost, product-level cost via shopping_performance_view and asset-interaction cost; the channel arithmetic lives in the template sheet, not inspected.)

5. **Source**: Aayushi Bhandari, Optmyzr — https://www.optmyzr.com/blog/manage-and-optimize-performance-max-campaigns/ · **Tier** 1 · **Date** 2026-09-08 · **Claim**: Google's docs/support said PMax placement exclusions only worked via the UI; an Optmyzr experiment showed zero spend on API-excluded placements and Google later confirmed the API route works. Account-level exclusion targets mobile apps, YouTube videos/channels and websites with no conversions. Levitate Foundry reported +30% PMax ROAS from excluding low-intent placements (vendor case). Weaker-looking channel ROAS should guide tests, not restrict spend (their view). · **Evidence or opinion**: Vendor experiment + case claim.

6. **Source**: Optmyzr PMax guide (Dii Pooler; Kirk Williams quoted) — https://www.optmyzr.com/guide/performance-max/ · **Tier** 1 · **Date** updated 2026-09-30 · **Claim**: Flag any placement over 15% of total spend; exclude on patterns, not impressions alone; Williams: low YouTube ROAS is usually the wrong reason to turn video off. · **Evidence or opinion**: Heuristics.

7. **Source**: Navah Hopkins, Optmyzr, Feb 2023 updates — https://www.optmyzr.com/blog/new-performance-max-updates/ · **Tier** 1 · **Date** 2023-02-28 · **Claim**: Without video assets, YouTube placements are an expensive waste; PMax forces spend on networks a brand may not value; content suitability center added for Display/YouTube. · **Evidence or opinion**: Opinion.

8. **Source**: Optmyzr BFCM 2026 data — https://www.optmyzr.com/blog/google-ads-bfcm-2026/ · **Tier** 1 · **Date** 2026-09-22 · **Claim**: YouTube ~10% of PMax impressions, ~2% of conversion value; ROAS by network Oct/Nov/Dec: Search 732/768/760%, YouTube 573/626/555%, Discover 657/648/477% (Discover CVR halved Nov→Dec), Content 665/926/865%, Gmail 726/786/789%. · **Evidence or opinion**: 4,200-account data.

9. **Source**: Kirk Williams, ZATO, channel reporting — https://zatomarketing.com/blog/heres-why-the-new-pmax-channel-reporting-rocks · **Tier** 1 · **Date** 2025-06-13 · **Claim**: Channel report separates feed-based from other ads per channel; YouTube "other" shows more interactions than clicks — interactions are not clicks; "it sucks to have a Channel Report and no Channel Controls". · **Evidence or opinion**: Single-account observation.

10. **Source**: Manuel Baudisch, smec — https://smarter-ecommerce.com/blog/en/google-ads/4-reasons-why-google-is-no-longer-a-black-box-and-4-problems-that-still-exist/ · **Tier** added-Tier-2 · **Date** 2026-02-12 · **Claim**: Placement view is a firehose (e.g. 50,000 domain lines); examples: US retailer spending on Polish domains, a "Flashlight App". Google gives channel volume, not channel ROAS/CPA. · **Evidence or opinion**: Examples.

## Dissenting view
Optmyzr (Bhandari, 2026) and Williams (in Optmyzr's guide) say weak channel ROAS should prompt tests, not restriction, and that cutting YouTube on ROAS alone is wrong. Rooijmans flags every mobile app and Hopkins calls video spend without video assets waste. The disagreement is whether non-Search PMax inventory is incremental reach that under-reports (view-through, assisted) or dilution that must be fenced.

## What the platform currently does [Google docs]
- PMax placement report: impressions only; Google says it "shouldn't be used to evaluate performance" and is a brand-safety tool; Search is not a placement; Google O&O grouped; search partner sites included since March 2024 (https://support.google.com/google-ads/answer/11465047).
- Placement exclusions for PMax are respected at account and MCC level for Display, Search Partners and Video; inventory types Maximum (default)/Moderate/Limited; five sensitive Display categories excludable; Display/Video keyword exclusions via Content Suitability (https://support.google.com/google-ads/answer/13607727).
- Channel performance report: cost, conversions, value by channel (Search, Display, YouTube, Discover, Maps, Gmail, Search partners) from 2025-06-06; no per-channel budget; "allow 1–2 weeks for stabilization"; a channel with no ads usually means PMax prioritised others (https://support.google.com/google-ads/answer/16260130).
- Negatives do not apply to Display/Video inventory (https://support.google.com/google-ads/answer/15726455).

## Baseline check
Read `google-ads-audit-ecommerce` (no placement content) and `google-ads-scripts` (generic scripts; nothing on placements). This skill adds the account-level-only mechanic, the script criteria and thresholds, the spend-per-day floor from Rhodes, the channel-report ROAS computation, and the position on apps and video.

## Judgment calls
- Position on mobile apps: exclude all app categories by default for e-commerce and lead gen (Rooijmans), acknowledging his claim is experience-based.
- Video: do not fence YouTube on ROAS alone (Williams); fence it when there is no advertiser video (Hopkins) or when channel ROAS is below half the Search channel for two months (dossier rule built on the BFCM network gaps).
- Spend floor for review: Rhodes' $0.10/day; Pooler's 15% single-placement flag for action.

## Canon strength: Strong

## Invalidated by
Google adding campaign-level placement exclusions or channel-level budget/bid controls in PMax; adding cost to the placement report; changing the account-level exclusion scope.
