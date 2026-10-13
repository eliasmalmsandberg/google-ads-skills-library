# Dossier — 84 Impression share decomposition decision rule

## Sources

1. **Source**: Brad Geddes, Adalysis blog, "PPC & KPI monitoring: how to diagnose and work with impression share loss due to budget" — https://adalysis.com/blog/ppc-kpi-monitoring-how-to-diagnose-and-work-with-impression-share-loss-due-to-budget/ · **Tier** 1 · **Date** 2019-07-25 (modified 2026-03-23) · **Claim**: Lost IS (budget) moves for five reasons — search-volume change, targeting change, CPC change (incl. silent CPC shifts under automated bidding), QS change (higher QS converts rank-loss into budget-loss), budget change. Rule: if within CPA/ROAS target and budget can rise, there should be very little budget loss; if budget is fixed, move money from under-spending/less profitable campaigns into the campaign with budget loss and the lower cost/conv (example: 24% lost-to-budget campaign with lowest cost/conv). Lowering bids stretches budget ($1 CPC/$100 = 100 clicks; $0.75 = 133) but pushes loss into rank. Budget loss is acceptable in experimental/awareness campaigns, never in remarketing or profitable campaigns. · **Evidence or opinion**: Method with account examples (search volume +130%, impressions +16%).

2. **Source**: Brad Geddes, Adalysis blog, "how to diagnose lost search impression share rank & top impression share changes" — https://adalysis.com/blog/ppc-kpi-monitoring-how-to-diagnose-lost-search-impression-share-rank-top-impression-share-changes/ · **Tier** 1 · **Date** 2019-09-04 (modified 2026-04-10) · **Claim**: Rank loss and top IS move together but not in lockstep; diagnose in order: QS trend, max CPC / bid strategy change (automated bidding silently drops keyword bids — watch avg CPC), targeting changes, asset count, then graph top/abs-top IS against QS, CPC, conversions, CPA. · **Evidence or opinion**: Method; one example of QS 5→10 after LP and ad testing.

3. **Source**: Brad Geddes, Adalysis blog, "How to use impression share analysis to get more Google Ads conversions" — https://adalysis.com/blog/how-to-use-impression-share-analysis-to-get-more-google-ads-conversions/ · **Tier** 1 · **Date** 2024-03-20 (modified 2026-03-23) · **Claim**: Sequence for budget-limited: shift budget to the cheapest-converting budget-capped campaign (example: 22% lost to budget, lowest cost/conv); pause keywords with CPA above account average or zero conversions to free impressions; lowering tCPA/raising tROAS gains conversions per budget at the cost of rank loss ($20→$18 example). For rank-limited keywords: assets first (fewer than 4–5 distinct assets → add), then QS, raise bids last ("usually the last step"). Benchmarks: non-brand IS >80% excellent; brand >90% (>95% large brands); many well-managed accounts sit at 10–30% IS. · **Evidence or opinion**: Method with worked examples; benchmarks are practitioner opinion.

4. **Source**: Adalysis docs, "Impression share analysis" — https://docs.adalysis.com/tools/performance/impression-share-analysis · **Tier** 1 (tool implementation of Geddes' method) · **Date** current 2026 · **Claim**: Budget-boost alert fires when lost IS (budget) stays above 10% for three consecutive days (customisable); rank side prioritises ad groups by impression-weighted QS × 30-day cost. · **Evidence or opinion**: Tool rule.

5. **Source**: Mike Ryan (Smarter Ecommerce), "Google ends its bid suppression era: what it means for your ROAS" — https://smarter-ecommerce.com/blog/en/google-ads/google-ends-its-bid-suppression-era-what-it-means-for-your-roas/ · **Tier** added-Tier-2 for this topic (publishes cross-account medians, method, and contradicts Google's "never intended" framing with data) · **Date** 2026-09-17 · **Claim**: After Google stopped suppressing bids on budget-limited tCPA/tROAS campaigns (17 Aug 2026, rollout complete 27 Aug), median CPC on budget-limited tROAS campaigns rose 15.8% while non-limited fell 13%; median lost IS (rank) on budget-limited campaigns fell from ~45% to ~30% and lost IS (budget) rose from ~4% to ~33%; overall IS fell 40%→31%. Before the change, over half of budget-limited campaigns over-delivered ROAS vs. 30% of non-limited. Options: accept, raise tROAS toward delivered ROAS, raise budget, or switch to Maximize Conversions (cannot be budget-limited by design). · **Evidence or opinion**: Cross-account medians from smec's client base (sample size not stated).

6. **Source**: Cassie Oumedian, PPC Hero, "Is your account leaving money on the table from lost impression share?" — https://www.ppchero.com/is-your-account-leaving-money-on-the-table-from-lost-impression-share · **Tier** 2 (PPC Hero is on the canon watch list; cited only for the incremental-volume arithmetic) · **Date** 2015-04-15 · **Claim**: Available impressions = impressions ÷ IS; incremental impressions = available × lost IS (budget); × CTR → clicks; × CPC → cost; × CVR → conversions. Rank-based gains are not forecastable this way because CTR and CPC both rise with rank. · **Evidence or opinion**: Worked example (23,169 impr at 32% IS → ~72.5k available; 64% budget loss → ~46k impr, 732 clicks, $32.6k, 6 conv).

7. **Source**: Google Ads Help, "About impression share" — https://support.google.com/google-ads/answer/2497703 and "Search top IS / abs top IS" — https://support.google.com/google-ads/answer/7501826 · **Tier** Reference only · see below.

Search budget for this build was exhausted during this skill; no Optmyzr/Hopkins page on IS could be located by direct URL (two guessed URLs failed to fetch). Noted here, not invented.

## Dissenting view
Geddes (2024) says raise bids last for rank-limited keywords; Google's own column help suggests using top IS / abs-top IS as bid targets [Google docs]. The disagreement is about whether rank loss is primarily a bid problem (Google: bid to a position-share target) or a quality/asset problem to be fixed before spending more (Geddes). Ryan (2026) adds a second tension: since Aug 2026 a budget-limited campaign's "lost to budget" number is partly manufactured by Google no longer lowering bids, so budget loss is no longer a clean signal that the campaign "wants" more budget at current efficiency.

## What the platform currently does [Google docs]
- IS is estimated per day from auctions where the ad showed or was competitive enough to show; eligible impressions estimated from targeting, approvals and quality; Search Partners excluded; data lags 24–48 h; small daily moves are noise [Google docs, answer 2497703].
- Lost top IS (budget/rank) and lost abs-top IS (budget/rank) exist as separate columns; eligible top impressions are estimated as if not budget-constrained [Google docs, answer 7501826].
- PMax IS = (Search + Shopping impressions) / eligible Search + Shopping [Google docs].
- 17–27 Aug 2026: Google stopped lowering bids on budget-limited tCPA/tROAS campaigns (Search, Shopping, PMax, Demand Gen, Travel); the Bid Target Adjustment tool has been available since 6 Jul 2026 (Ryan, 2026; Ginny Marvin quoted — reference only).

## Baseline check
Read `google-ads-account-audit` (Layer 4 benchmarks: lost-to-budget <20%, lost-to-rank <30%) and `google-ads-budget-management`. This skill adds the five-cause decomposition of a *change* in lost IS, the Adalysis ordering (assets → QS → bids last), the budget-reallocation rule keyed to cost/conversion, the 10%-for-3-days trigger, the incremental-volume arithmetic and its rank-side caveat, and the Aug 2026 behaviour change that re-labels rank loss as budget loss.

## Judgment calls
- Mike Ryan added as Tier 2 for this topic; his medians are the only published post-Aug-2026 data found.
- The baseline's "<20% / <30%" lines are not carried over; no canon source states them.
- Audit-level IS benchmarks (80% non-brand, 90–95% brand) are Geddes' opinion and are labelled as such in the skill.

- Review fix (2026-10-13): the <1,000 impressions/month floor and 90-day aggregation are labelled Epiminds operating thresholds; no canon source (90 days mirrors the Adalysis lost-IS history window).

## Canon strength: Strong
Three Tier 1 Adalysis posts plus tool rule, one added Tier 2 with cross-account data, one Tier 2 for arithmetic.

## Invalidated by
Google reinstating bid suppression on budget-limited campaigns, changes to how eligible impressions are estimated, or removal of the budget/rank split in lost-IS columns.
