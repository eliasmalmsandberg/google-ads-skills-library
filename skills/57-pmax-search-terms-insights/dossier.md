# Dossier — 57 PMax search terms insights — what you can see and mine

## Sources

1. **Source**: Nils Rooijmans, "Google Ads Script – Performance Max Non-Converting Search Term Alerts" — https://nilsrooijmans.com/google-ads-script-pmax-non-converting-search-term-alerts/ · **Tier** 1 · **Date** 2024-03-06, modified 2025-05-27 · **Claim**: Queries the `campaign_search_term_insight` resource via GAQL: first categories (category_label, clicks), then search terms within each category; metrics available are impressions, clicks, conversions, conversion value — no cost. Defaults: 90-day lookback, MIN_CLICKS 100, CONVERSION_THRESHOLD 0.5; flagged terms become negatives. Run weekly (Monday 06:00). Script stops with 180s left and warns; raise MIN_CLICKS or shorten lookback on big accounts. · **Evidence or opinion**: Published script.

2. **Source**: Nils Rooijmans, "Google Ads Script – PMax Trending Search Categories" — https://nilsrooijmans.com/google-ads-script-pmax-trending-search-categories/ · **Tier** 1 · **Date** 2023-08-21, modified 2025-05-09 · **Claim**: Compares last 7 days vs prior 7 days of impressions per category; report only categories with absolute change >100 impressions AND relative change >50%. Weekly run. · **Evidence or opinion**: Published script.

3. **Source**: Brad Geddes, Adalysis, "Is Performance Max cannibalizing your Search ads? A deep dive into search term overlap" — https://adalysis.com/blog/is-performance-max-cannibalizing-your-search-ads-a-deep-dive-into-search-term-overlap/ · **Tier** 1 · **Date** 2024-12-12 · **Claim**: How to pull PMax terms in the UI (campaign → Insights and reports → search terms insight → "view detailed data" → download, per campaign; slow). Excluded terms under 10 impressions. 3,300+ non-retail PMax campaigns, ~1.2M terms: 45% of PMax terms also appear as Search search terms; Search had higher CVR 84% of the time; many PMax terms are misspellings/missing spaces. Recommends adding top PMax terms as exact-match Search keywords. · **Evidence or opinion**: Cross-campaign study.

4. **Source**: Frederick Vallaeys, Optmyzr, "Is PMax cannibalizing Search" study — https://www.optmyzr.com/blog/is-pmax-cannibalizing-search/ · **Tier** 1 · **Date** 2025-07-31 · **Claim**: Compared CTR and CVR only, because Google did not report PMax search-term cost at the time; differences under 10% treated as insignificant. 97% of 511 accounts had search-term overlap with Search. Use search-term insights to find converting PMax queries missing from Search and add as exact match. · **Evidence or opinion**: Cross-account study.

5. **Source**: Mike Rhodes, PMax Insights S.Cat tab docs — https://mikerhodes.com.au/scripts/help/pmax-insights/scat-tab · **Tier** 1 · **Date** 2026 · **Claim**: Buckets Brand / Close Brand / Non-Brand / Blank (Google withholds for privacy); requires brand terms in config; read ROAS and CVR by bucket and category. · **Evidence or opinion**: Published tool.

6. **Source**: Navah Hopkins, Optmyzr, "Search Terms Available Again in Performance Max" — https://www.optmyzr.com/blog/performance-max-search-terms/ · **Tier** 1 · **Date** 2026-09-25 · **Claim**: Audit: (1) check overlap between search themes and Search keywords, swap themes if high; (2) add negatives at campaign level (or account level), preview impact first; brand via Brand Exclusions; (3) compare PMax vs Search auction prices per category — much cheaper PMax may mean spend is going to visual inventory or budget too low; she cites 60 conversions/30 days as the minimum for PMax (unsourced). Asset groups cannot take negatives; account-level negatives capped at 1,000; categories do not carry over to placements. · **Evidence or opinion**: Method/opinion.

7. **Source**: Kirk Williams, ZATO, "Big April 2025 PMax changes" — https://zatomarketing.com/blog/big-april-2025-pmax-changes-just-announced-search-terms-channel-level-reporting-and-more · **Tier** 1 · **Date** 2025-04-30 · **Claim**: Google rolled out a PMax search terms report (queries triggering impressions and clicks) and a channel performance report; "black box to glass box" — more insight, still no channel controls; use the terms data to refine campaign-level negatives. · **Evidence or opinion**: Platform commentary.

8. **Source**: Manuel Baudisch, smec, Brand Traffic Analyzer — https://smarter-ecommerce.com/blog/en/google-ads/pmax-brand-script/ · **Tier** added-Tier-2 (see dossier 55) · **Date** 2024-09-12 · **Claim**: Uncategorised terms appear blank; >90% are non-brand in his experience; matching is CONTAINS. · **Evidence or opinion**: Experience estimate.

9. **Source**: Optmyzr PMax guide (Dii Pooler checklist) — https://www.optmyzr.com/guide/performance-max/ · **Tier** 1 · **Date** updated 2026-09-30 · **Claim**: Investigate if >30% of conversions come from brand terms despite exclusions; if >80% of spend sits in the top 20% of products or asset groups. · **Evidence or opinion**: Heuristic.

## Dissenting view
Hopkins (2026) treats the restored search-term visibility as sufficient to run PMax like Search (themes, negatives, auction-price comparison). Rooijmans (2024) and Williams (2025) stress what is still missing: no cost per term, no asset-group-level negatives, no channel controls, and the Blank bucket. The disagreement is about how much weight a term-level CVR deserves when the cost side is invisible.

## What the platform currently does [Google docs]
- "About the search terms report in Performance Max" (https://support.google.com/google-ads/answer/16327396): lists search terms that triggered PMax ads with performance metrics, landing pages and ad formats; conversions emphasised, clicks and impressions mentioned, cost not listed; store visit/store sales conversions not available; data available from March 2023 onward. Negatives for Search and Shopping inventory at account or campaign level; Display/Video via excluded content keywords in Content Suitability.
- Search term insights (categories) exposed via the API resource `campaign_search_term_insight` with impressions, clicks, conversions, conversion value (per Rooijmans' scripts; no cost field).
- Channel performance report: cost, conversions, conversion value by channel, date ranges after 2025-06-06 (https://support.google.com/google-ads/answer/16260130).
- Negative keyword impact estimate: previews projected % change in conversions/value, up to 10 keywords per preview, PMax Search and Shopping inventory only (https://support.google.com/google-ads/answer/16973204).
- Campaign-level negatives in PMax: Search and Shopping inventory only; shared lists allowed (https://support.google.com/google-ads/answer/15726455).

## Baseline check
Read `google-ads-keyword-cannibalization` (mentions "Search Insights in PMax" only as a pointer) and `google-ads-audit-ecommerce` (no PMax term handling). This skill adds the data model (categories vs terms, which metrics exist, what Blank means), the script thresholds, the download path, and what to do with each finding.

## Judgment calls
- Treat cost as unavailable at term level and work in clicks and conversions (Rooijmans; Vallaeys). Google's report page does not list cost; if cost appears later, update.
- Hopkins' 60-conversion figure is recorded but not used as a rule (unsourced).
- Monthly cadence per the row; Rooijmans runs weekly — skill uses weekly alerts, monthly review.

## Canon strength: Strong

## Invalidated by
Google adding cost to term-level PMax reporting, removing the search terms report or the `campaign_search_term_insight` resource, allowing asset-group-level negatives, or changing the privacy threshold that creates the Blank bucket.
