# Dossier — 62 PMax campaign-level negatives

## Sources

1. **Source**: Nils Rooijmans, "How to add negative keywords to your performance max campaigns" — https://nilsrooijmans.com/how-to-add-negative-keywords-to-your-performance-max-campaigns/ · **Tier** 1 · **Date** 2025-01-03, modified 2025-05-02 · **Claim**: Three routes: account-level (he recommends against — negates terms in non-PMax campaigns too), shared negative list attached to PMax (his preferred; at the time applied via Google's PMax modification form), campaign-level (then beta). Name lists with a leading asterisk so they sort first. Update periodically with brand terms and low-performing PMax search terms, found with his non-converting search term script. · **Evidence or opinion**: Method.

2. **Source**: Nils Rooijmans, "PMax Non-Converting Search Term Alerts" script — https://nilsrooijmans.com/google-ads-script-pmax-non-converting-search-term-alerts/ · **Tier** 1 · **Date** 2024-03-06, modified 2025-05-27 · **Claim**: Defaults 90-day lookback, ≥100 clicks, <0.5 conversions → negative candidate; weekly run. Data: `campaign_search_term_insight` (impressions, clicks, conversions, value; no cost). · **Evidence or opinion**: Published script.

3. **Source**: Aayushi Bhandari, Optmyzr, "How to Manage and Optimize Your Performance Max Campaigns" — https://www.optmyzr.com/blog/manage-and-optimize-performance-max-campaigns/ · **Tier** 1 · **Date** 2026-09-08 · **Claim**: PMax supports up to 10,000 campaign-level negative keywords, matching Search; they apply only to Search and Shopping inventory, so Display/YouTube/Gmail/Discover need placement or location exclusions. · **Evidence or opinion**: Vendor doc; limit stated.

4. **Source**: Navah Hopkins, Optmyzr, "Search Terms Available Again in Performance Max" — https://www.optmyzr.com/blog/performance-max-search-terms/ · **Tier** 1 · **Date** 2026-09-25 · **Claim**: Asset groups cannot take negatives; account-level PMax negatives capped at 1,000; add at campaign level (Keywords > Negative keywords) or account level; use Google's preview before committing; brand terms via Brand Exclusions. · **Evidence or opinion**: Method.

5. **Source**: Brad Geddes, Adalysis — https://adalysis.com/blog/is-performance-max-cannibalizing-your-search-ads-a-deep-dive-into-search-term-overlap/ · **Tier** 1 · **Date** 2024-12-12 · **Claim**: Prefer adding top PMax terms as exact-match Search keywords (with relevant ad copy/landing page) over relying on negatives alone; ignore Google's "remove redundant keywords". Search converts better on the same term 84% of the time. · **Evidence or opinion**: Cross-campaign study.

6. **Source**: Frederick Vallaeys, Optmyzr — https://www.optmyzr.com/blog/is-pmax-cannibalizing-search/ · **Tier** 1 · **Date** 2025-07-31 · **Claim**: Add branded misspellings as exact-match Search keywords because PMax still triggers on fuzzy brand matches despite brand exclusions; turn off auto-apply recommendations that remove keywords. · **Evidence or opinion**: Study + recommendation.

7. **Source**: Kirk Williams, ZATO, "Big April 2025 PMax changes" — https://zatomarketing.com/blog/big-april-2025-pmax-changes-just-announced-search-terms-channel-level-reporting-and-more · **Tier** 1 · **Date** 2025-04-30 · **Claim**: Search term data now supports campaign-level negatives; Search Partners performance visible but still not excludable. · **Evidence or opinion**: Platform commentary.

8. **Source**: Kirk Williams, ZATO, "7 ways" — https://zatomarketing.com/blog/how-to-structure-performance-max-campaigns-7-ways · **Tier** 1 · **Date** 2023-08-22, updated 2026-04-21 · **Claim**: Account-level exclusion is "the nuclear option" because it also removes the terms from Search and Standard Shopping. · **Evidence or opinion**: Opinion.

## Dissenting view
Geddes (2024) and Vallaeys (2025) treat negatives as secondary: the primary fix for a term PMax should not own is a Search keyword that outranks it. Rooijmans (2024–25) and Hopkins (2026) treat negatives as the primary waste control. The disagreement is about whether the term has value anywhere (keyword it) or none (negate it).

## What the platform currently does [Google docs]
- "Negative keywords in Performance Max campaigns" (https://support.google.com/google-ads/answer/15726455): negatives can be added to all campaigns (account level) or to a specific PMax campaign; match type set via symbols; apply to Search and Shopping inventory only; an existing negative keyword list can be selected when adding to a campaign. No launch date or limit stated on the page.
- Brand suitability page (https://support.google.com/google-ads/answer/13607727): campaign-level negatives framed as blocking non-brand-safe queries; account-level negatives limited to 1,000 per account; Display and Video use excluded content keywords in Content Suitability; Hotel/travel PMax doesn't support negatives.
- Impact estimate (https://support.google.com/google-ads/answer/16973204): preview projected % change in conversions or conversion value for up to 10 keywords at a time; PMax Search and Shopping inventory only.
- Search terms report in PMax with conversions/clicks/impressions, data from March 2023 (https://support.google.com/google-ads/answer/16327396).
- Timeline per practitioners: campaign-level negatives in beta Jan 2025 (Rooijmans), generally available with the search terms rollout around April 2025 (Williams).

## Baseline check
Read `google-ads-keyword-cannibalization` (cross-campaign negatives for Search; one line on PMax Search Insights) and `google-ads-scripts` (generic negative-adding script against the Search query report). This skill adds the PMax-specific mechanics (inventory scope, 10,000 campaign / 1,000 account limits, no asset-group negatives, shared lists, the impact preview), the click/conversion thresholds from a published PMax script, and the keyword-first rule.

## Judgment calls
- Treat Google's impact preview as information, not a veto: a projected conversion loss on a term Search converts better on is the point, not a problem (Geddes' study supports the keyword-first route).
- Shared-list-first follows Rooijmans; campaign-direct negatives for one-offs.
- Brand terms are excluded here (skill 55 covers brand lists).

## Canon strength: Strong

## Invalidated by
Google extending PMax negatives to Display/Video/Discover inventory, allowing asset-group-level negatives, changing the 10,000/1,000 limits, or removing the PMax search terms report that feeds the thresholds.
