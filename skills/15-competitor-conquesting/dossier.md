# Dossier — 15 Competitor conquesting

Research note: WebSearch budget exhausted; sources via sitemaps. searchengineland.com rate-limited. Kirk Williams, Sophie Fell and Julie Bacchini content on competitor bidding could not be located without search. Optmyzr blog URL guesses failed. The canon here is method-rich but evidence-poor.

## Sources

1. **Source**: Navah Hopkins, Search Engine Journal — "Ask a PPC: How to protect a budget from competitor-branded terms", https://www.searchenginejournal.com/ask-a-ppc-how-to-protect-a-budget-from-competitor-branded-terms/559521/ · **Tier** 1 · **Date** 2025-11-13 · **Claim**: Default is to exclude competitor intent from generic campaigns with phrase negatives (exact where a competitor name resembles a generic phrase), kept in a shared list updated from search terms. Bid on competitors only deliberately: own campaign, own budget and goal; one ad group per competitor; no DKI; competitor names out of ad copy; a few key rivals only; for awareness drop ROAS targets, for performance set high ROAS thresholds; value conversions differently and use CPC floors/bid caps so automation isn't drawn to cheap, unprofitable clicks; audit search terms for new variants/misspellings; segment by device/location/audience. Brand exclusions (PMax/AI campaigns) are distinct from negatives and close variants may still get through, so negatives remain necessary. Trade-off: blocking competitor terms forfeits comparison shoppers; do it only for consistently underperforming queries. · **Evidence**: none — assertions (competitor clicks convert lower, CPCs deceptively low) and a hypothetical. Author is Microsoft Product Liaison.
2. **Source**: Navah Hopkins, SEJ — "How to bypass big brands bidding up your terms", https://www.searchenginejournal.com/big-brands-bidding-your-terms/470824/ · **Tier** 1 · **Date** 2022-11-21 · **Claim**: Defensive side: test synonyms/misspellings of the expensive term one at a time; bid caps on conversion-based strategies (cap ≤ 10% of daily budget keeps enough clicks; too low kills volume); in-market/affinity exclusions and first-party audiences. · **Evidence**: none.
3. **Source**: Brad Geddes, Adalysis — "Get more Auction Insights competitor information with this free Data Studio template", https://adalysis.com/blog/get-more-auction-insights-competitor-information-with-this-free-data-studio-template/ · **Tier** 1 · **Date** 2019-06-11 · **Claim**: Separate "actual competitors" (same offering) from "impression competitors" (same SERP, different offering); trend competitor coverage — monthly-budget rivals drop off near month end, quarterly-budget rivals fade late in the quarter; heatmap of IS × overlap rate to find rivals who compete only in some campaigns; the UI shows 5–10 competitors while reports can hold 1,000+. · **Evidence**: template and screenshots; no results.
4. **Source**: Navah Hopkins, SEJ — "How to use keyword intent to boost PPC performance", https://www.searchenginejournal.com/keyword-intent-boost-ppc-performance/293997/ · **Tier** 1 · **Date** 2019-05-29 · **Claim**: Branded and competitor terms in separate campaigns so they don't absorb budget from generic concepts. · **Evidence**: opinion.
5. **Source**: Brad Geddes, Adalysis — "Should you remove redundant keywords?" · **Tier** 1 · **Date** 2024-07-03 · **Claim**: Brand defence data point: brand term 53% CTR, > 40% CVR, $0.23 CPA; misspelled brand queries leaking to PMax. · **Evidence**: account data (used for the brand-defence baseline, not conquesting).
6. **Source**: Navah Hopkins, Optmyzr — "Search terms available again in Performance Max", https://www.optmyzr.com/blog/performance-max-search-terms/ · **Tier** 1 · **Date** 2026-09-25 · **Claim**: Use Brand Exclusions in PMax for brand and competitor brands rather than ordinary negatives. · **Evidence**: method.

## Dissenting view
Hopkins (2025) herself carries the dissent: blocking competitor terms forfeits buyers comparing options, so the exclusion default is only justified for consistently underperforming queries. No canon source publishes account data showing conquesting CPA vs generic CPA; the "competitor clicks convert worse" claim is asserted, not measured. The disagreement is default-exclude (Hopkins 2025) vs deliberate test; neither side has published evidence.

## What the platform currently does [Google docs]
- [Google docs] Brand lists / brand inclusions and exclusions for Search (with broad match / AI Max) and PMax exist and are separate from negatives; conversion thresholds apply to AI-optimised formats (Hopkins 2025 and Hopkins/Optmyzr 2026 describing Google docs; Google page not fetched).
- [Google docs] Negatives: phrase/exact logic; no close variants; misspellings automatic (answer/2453972, fetched 2026-10-13).
- [Google docs] Trademark policy: not fetched; the skill relies on Hopkins' rule to keep competitor names out of ad copy and off DKI.

## Baseline check
Read `google-ads-keywords` (competitor section: separate campaign, one ad group per competitor, "[Competitor] alternative" keywords, never disparage) and `google-ads-negative-keywords`. This skill adds the exclude-first default with the shared-list mechanism, the bidding controls (value differentiation, CPC floors/bid caps, high-ROAS thresholds or no target for awareness), the Auction Insights method for choosing which rivals and when they are weak, the brand-exclusion vs negative distinction, and an explicit statement that the canon has no published performance evidence for conquesting.

## Judgment calls
- Canon strength is Adequate by the letter (3+ Tier 1 sources) but the evidence is near-zero; the skill says this plainly and treats conquesting as a gated test with a kill rule, not a strategy with known returns.
- Trademark policy specifics are omitted because the Google page was not fetched; the skill keeps Hopkins' conservative copy rule.

## Canon strength: Adequate
Three Tier 1 sources with method; no published performance data on conquesting.

## Invalidated by
Changes to Google's brand list / brand exclusion features; trademark policy changes affecting competitor names in ads; removal of bid caps/CPC floors from portfolio strategies; AI Max removing keyword-level control over competitor terms.
