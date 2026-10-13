# Dossier — 83 Auction insights trend reading

## Sources

1. **Source**: Brad Geddes, Adalysis, "Finding competitive insights in the Auction Insights report" (video transcript) — https://adalysis.com/blog/finding-competitive-data-insights-using-the-auction-insights-report/ · **Tier** 1 · **Date** 2021-11-09 (mod. 2026) · **Claim**: Read overlap rate as the primary number ("you showed ads at the same time, not just competition level"); a competitor with low IS but high position-above rate is bidding high for few impressions (likely high CPA); a competitor with IS well above yours has more budget or better QS; prioritise ad comparison against highest-overlap competitors. Segment account → campaign → region (example: 43% overlap in one country while low overall) and separate brand from non-brand because brand campaigns distort. Track weekly; competitors whose overlap drops at month-end have run out of budget — cheaper clicks late in the month. Raise bids on competition only when the goal is conquest, never because of CPA/ROAS. In-UI report shows ~8–15 competitors; Data Studio shows hundreds. · **Evidence or opinion**: Method with illustrative account numbers (10%, 16%, 68%, 80% examples), explicitly not benchmarks.

2. **Source**: Brad Geddes, Adalysis, "Free Data Studio template: Get more competitor Auction Insights" — https://adalysis.com/blog/get-more-auction-insights-competitor-information-with-this-free-data-studio-template/ · **Tier** 1 · **Date** 2019-06-11 (mod. 2026-04-28) · **Claim**: Weekly-segment page for trend lines; monthly-budget competitors' coverage "falls off dramatically" at month-end, quarterly-budget competitors peak early in the quarter and taper; watch the competitors who most often hold top positions (they anchor offers); heatmap of IS × overlap finds competitors concentrated in a few campaigns; separate "actual" from "impression" competitors. · **Evidence or opinion**: Method + template; no numbers.

3. **Source**: Brad Geddes, Adalysis, "How to use your Auction Insights data to differentiate your ads" — https://adalysis.com/blog/how-to-use-your-auction-insights-data-to-differentiate-your-ads/ · **Tier** 1 · **Date** 2019-03-05 (mod. 2026-03-23) · **Claim**: Classify each advertiser as true competitor vs impression competitor; turn the true competitors' positioning into ad messaging tests (multi-ad-group tests first); repeat per country/region/product line. · **Evidence or opinion**: Method; one example concluding "no true competitor on the list".

4. **Source**: Brad Geddes, Adalysis, "KPI monitoring & diagnosis: why do your CPC and cost change?" — https://adalysis.com/blog/kpi-monitoring-diagnosis-why-does-your-cpc-and-cost-change/ · **Tier** 1 · **Date** 2020-01-13 (mod. 2026-03-23) · **Claim**: Order of checks for a CPC change: targeting changes → bid changes (incl. silent automated-bidding moves; "the most common reason CPCs change is because you changed your bids") → competitor changes via auction insights (rising competitor top-of-page rate and outranking share = they raised ad rank; falling competitor visibility can lower your CPC) → QS trend → segment by keyword type / funnel / device. Under automated bidding a 25% CPC rise with unchanged CPA is the system working. Worked example: CPC −34%, impressions −85%, clicks −75% from pausing expensive keywords in a holiday period. · **Evidence or opinion**: Method with account examples.

5. **Source**: Brad Geddes, Adalysis, "How to diagnose changes to your impression and search volume" — https://adalysis.com/blog/ppc-kpi-monitoring-how-to-diagnose-changes-to-your-impression-search-volume/ · **Tier** 1 · **Date** 2019-07-16 (mod. 2026) · **Claim**: Estimate search volume = impressions ÷ IS; compare volume trend to impression trend to separate demand shifts (market) from account-driven ones; if volume rises faster than impressions, a lost-IS metric is rising; first ask whether a peak period was entered/left (compare YoY), then budgets/CPCs, targeting, position; check conversions alongside (example: impressions +16%, conversions +49%). · **Evidence or opinion**: Method with one example.

6. **Source**: Google Ads Help, "About Auction insights" — https://support.google.com/google-ads/answer/2579754 · **Tier** Reference only · see below.

Not found: Optmyzr, Rooijmans, PPC Mastery or Brainlabs pages on auction-insights trend reading (site searches returned nothing or were blocked). Optmyzr's Q2 2026 benchmark report (20k+ accounts) is gated; its teaser says AI Overviews are compressing paid inventory and that individual accounts "pulled sharply apart" while the median barely moved — not cited for numbers.

## Dissenting view
Geddes' own two positions sit in tension: the 2021 piece says raise bids on competition only for conquest, never for CPA/ROAS; the 2020 CPC piece treats a 25% CPC rise with flat CPA under automated bidding as "working correctly" — i.e. the bidder may already be responding to competitor pressure. The practical disagreement is whether a competitor-driven CPC rise is a reason to act (manual-era view) or a reason to check CPA and leave the bidder alone (Smart Bidding view). No second Tier 1 author on the topic was reachable.

## What the platform currently does [Google docs]
- Six metrics for Search (IS, overlap rate, outranking share, position-above rate, top-of-page rate, abs-top-of-page rate); Shopping gets IS, overlap, outranking only (Search Network only); PMax gets Search and Shopping auction insights at account/campaign level for ads served after Nov 2021 [Google docs].
- Segmentable by time and device for Search and Shopping; keyword/ad group/campaign level for Search [Google docs].
- No row shown when your IS is below 10%; search partners excluded; Shopping filters out very-low-impression auctions [Google docs].
- Shopping data from Oct 2014 [Google docs].

## Baseline check
Read `google-ads-account-audit` (Layer 4 IS benchmarks; auction insights mentioned only as a rank-loss check) and `google-ads-anomaly-detection`. This skill adds the diagnostic order for a "no internal change" performance shift, the search-volume-vs-impressions split, the budget-cycle signatures (month-end/quarter-start), the impression-vs-true-competitor classification, the "low IS + high position-above = aggressive bidder" read, and the brand/non-brand and region segmentation rules.

## Judgment calls
- All practitioner sources are Geddes; labelled Adequate rather than Strong despite the count, because one voice with illustrative numbers is not three.
- The month-end budget-cycle signal is a pattern claim without published data; the skill flags it as "to confirm on your data".

- Review fix (2026-10-13): the 15% month-on-month trigger, 10% overlap floor, 13-week window, 20%-for-4-weeks new-entrant rule and 1-point QS move are labelled Epiminds operating thresholds; no canon source.

## Canon strength: Adequate
Five Tier 1 posts, one author, method with illustrative examples; no cross-account evidence.

## Invalidated by
Google changing auction-insights metric definitions, the 10% IS display floor, time segmentation, or removing keyword-level auction insights; AI Max / keywordless Search removing the keyword level entirely.
