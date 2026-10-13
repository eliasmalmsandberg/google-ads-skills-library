---
name: dsa-long-tail-harvesting
id: 14
description: Run Dynamic Search Ads as a fenced discovery engine on a large site, harvest converting queries into exact keywords, and keep DSA from competing with the keywords it feeds. Use when keyword coverage is incomplete on a site with many pages. Not for using DSA as a primary traffic source, and time-limited: Google auto-upgrades DSA campaigns to AI Max in February 2027.
tags: Strategy / Search / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: The scheduled February 2027 automatic upgrade of DSA campaigns to AI Max; removal of DSA search term reporting; changes to keyword prioritisation between DSA/AI Max and keyword campaigns.
---
## What this is
DSA used as backfill and a query feeder, not a destination (Geddes/Adalysis, 2016). The setup has three parts: site targets segmented only as far as the numbers justify, a fence of negatives so DSA cannot take queries your keywords already own (Hopkins/SEJ, 2020), and a monthly harvest that moves converting DSA queries into exact keywords in the campaign whose ad and landing page fit (Geddes/Adalysis, 2024). It has an expiry: Google has scheduled DSA campaigns for automatic upgrade to AI Max in February 2027 (Google docs, 2026), so the value of the method is the keyword inventory you harvest before then.

## Where it comes from
Brad Geddes' DSA testing method (Adalysis, 2016) and his keyword-serving observations (Adalysis, 2024); Navah Hopkins' DSA negatives rule, which contradicts Google's guidance (SEJ, 2020), and her DSA-for-discovery setup with a bid cap (SEJ, 2024 ×2). Google's DSA documentation supplies targeting mechanics and the AI Max date.

## When to use it / when not to
Use on sites with deep category trees (Geddes' example had 4–8 levels, 2016) or large product/service inventories where the keyword list is known to be incomplete, and when you can commit to a monthly harvest. Do not use as the main traffic source — treat DSA as backfill (Geddes/Adalysis, 2016). Do not run it on sites with dynamic or list-heavy pages, out-of-stock pages, or weak HTML titles, because the headline comes from the page title and query (Google docs, 2026). Do not run it without the fence in rule 3; unfenced DSA competes with your keywords (Hopkins/SEJ, 2020).

## Inputs
- Site map or page feed with labels (category, top sellers, exclusions); HTML titles checked.
- Keyword export across Search campaigns (for the fence).
- Search terms by campaign, including DSA terms (which show no keyword and "Exact" as match type; Google docs, 2026).
- Target CPA/ROAS, and the alpha/beta promotion thresholds from skill 13.

## Method
1. **Targeting.** Start specific — URL_Contains groups or a labelled page feed — rather than the whole site (Google docs, 2026). Segment into ad groups by site section and keep splitting only while CTR, CVR or cost-per-conversion keeps improving; in Geddes' appliance test, splitting past the "juicer" level cut impressions sharply with no further metric gain, so that is where segmentation stops (Geddes/Adalysis, 2016). Exclude non-commercial pages and apply negative site phrases such as "out of stock" (Geddes/Adalysis, 2016).
2. **Creative.** Write descriptions specific to each segment; specific lines raise CTR and conversions (Geddes/Adalysis, 2016). Test two DSAs per ad group on different value propositions; carry winners into the matching text-ad groups (Geddes/Adalysis, 2016). Do not rely on ad customizers in DSA descriptions; they stopped serving in May 2024 (Google docs, 2026).
3. **Fence.** Add every actively targeted keyword in the account as a negative in the DSA campaign (Hopkins/SEJ, 2020). Use a shared "→ keyword campaigns" list so each monthly harvest extends it automatically. Brand goes in the fence too.
4. **Bidding.** For a new DSA campaign whose purpose is discovery, Max Clicks with a bid cap to estimate cost and volume (Hopkins/SEJ, 2024); move to tCPA/tROAS once the campaign has the conversion volume a target strategy needs (≥ 50/30 days; Vallaeys/Optmyzr, 2026 via skill 16).
5. **Monthly harvest.** From DSA search terms over the last 90 days, promote a query when it meets the managed-tier rule: ≥ 35 impressions and ≥ 2 conversions per month for 3 consecutive months (Geddes/Adalysis, 2016 via skill 13), or earlier when a single query has already converted at or under target CPA with enough spend to matter. Promotion = exact keyword in the Search ad group whose ad and landing page already fit (Geddes/Adalysis, 2024) + the same query added to the fence list.
6. **Protect the harvested keyword.** The identical exact keyword is what Google sets aside before DSA/AI Max/PMax get the query (Google docs, 2026); the fence negative is the enforcement, because Google's stated priority does not reliably hold (Geddes/Adalysis, 2024; Hopkins/SEJ, 2020).
7. **Negative harvest.** Irrelevant DSA queries with spend and no conversions go through the n-gram pass (skill 10) for root negatives and the page-level fix: if a page keeps attracting the wrong queries, exclude the page or fix its title (Google docs, 2026).
8. **Read the feeder monthly.** DSA's share of total conversions should fall as keywords are harvested; if it rises, the fence is incomplete or the keyword campaigns are budget-limited (Google docs, 2026: budget-limited Search campaigns lose keywords to automated campaigns).
9. **Before February 2027.** Complete the harvest, export the fence and the DSA search terms, and decide whether the AI Max upgrade is wanted; if not, pause or convert the DSA campaign ahead of the automatic upgrade (Google docs, 2026).

## What Google will tell you instead, and why we don't
Google's position is that DSA fills gaps and does not compete with your keywords, and it recommends mixing DSA with keyword targeting (Hopkins/SEJ, 2020 describing Google's guidance; Google docs, 2026). Hopkins saw DSA perform differently with and without keyword negatives and recommends fencing every targeted keyword out (SEJ, 2020); Geddes positions DSA as backfill to be tested like any ad, not a Google-managed traffic source (Adalysis, 2016). Google also plans to fold DSA into AI Max (Google docs, 2026); we use DSA as a keyword-building tool precisely because AI Max removes the keyword-level control that harvesting creates.

## Failure modes
- **Small sites.** With a few dozen pages, category targeting is coarser than your keyword list; DSA adds nothing to harvest.
- **Dynamic, list-heavy or thin pages.** Headline quality collapses because it is generated from the page (Google docs, 2026); Geddes flags such pages as poor broad-match signals too (Adalysis, 2024).
- **Unfenced accounts.** DSA takes queries that keywords already own and the harvest counts them as "new" (Hopkins/SEJ, 2020).
- **Budget-limited keyword campaigns.** Harvested keywords route back to automated campaigns if their Search campaign is limited by budget (Google docs, 2026).
- **Attribution lag.** 90-day DSA windows in long-cycle lead gen undercount conversions; apply conversion lag before judging a query.
- **Single-account evidence.** The only numbers in the canon are from one segmentation test (Geddes/Adalysis, 2016); expect to calibrate segmentation depth per site.

## What to measure
- Queries harvested per month and their CPA in the keyword campaign vs in DSA.
- DSA share of account conversions, monthly trend (should fall).
- DSA search terms matching an existing keyword (fence leakage; target zero).
- CTR/CVR/cost-per-conversion by segmentation level during setup (Geddes/Adalysis, 2016).
- Fence list size vs the per-campaign negative limit.

## Open disagreements in the canon
- **Destination vs feeder.** Google and single-client case studies present DSA as a traffic engine; Geddes (2016) and Hopkins (2020) as backfill and discovery. Epiminds: feeder, with the fence, because the measured cost of unfenced DSA is self-competition and the measured benefit of a feeder is the keyword inventory.
- **Whether to fence at all.** Google says it is unnecessary; Hopkins says her results say otherwise. Epiminds fences; the cost is one shared list.
