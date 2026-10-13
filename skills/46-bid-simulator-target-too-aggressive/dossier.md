# Dossier — 46 Bid simulator & "target too aggressive" diagnosis

## Sources

1. **Source**: Frederick Vallaeys, Optmyzr — "Google is making Smart Bidding more obedient", https://www.optmyzr.com/blog/smart-bidding-budget-caps-guide/ · **Tier** 1 · **Date** 2026-08-11 · **Claim**: After the 17 Aug 2026 change, budget-limited tCPA/tROAS campaigns bid to the stated target instead of being bid-suppressed. Diagnose a gap between target and matured actual by four causes before acting: deliberate headroom, stale setting, measurement issue, or scarce-budget selection. Baseline matured performance against date-matched *average* target CPA/ROAS, excluding the conversion-delay window; wait 1–2 full conversion cycles; change one major variable at a time; unconstrained campaigns act as a control cohort. Google's Bid Target Adjustment Tool (since 2026-07-06) adjusts targets to recent performance. Google warned forecasts were unreliable 17–31 Aug 2026. · **Evidence**: analysis of Google's announcement and auto-bidding paper; mechanisms hypothesised.

2. **Source**: Nils Rooijmans — "[AMA] We did exactly what Google told us to do, and went from 15 leads to 6", https://nilsrooijmans.com/daily/ama-we-did-exactly-what-google-told-us-to-do-and-went-from-15-leads-to-6-how-to-fix · **Tier** 1 · **Date** 2026-09-16 · **Claim**: Lowering a $300 tCPA to the $220 actual CPA (Google's post-change advice) on a $5–6K/month budget-limited campaign raised CPC and cut qualified leads from 20–30/month to 6 in two weeks at full spend. Fix: restore the business-acceptable target, add a portfolio max-CPC cap at the 90th–95th percentile of converting-term CPCs, and only then tighten target / loosen cap in 10–20% steps once back at ~20 conversions/month. · **Evidence**: one reader account.

3. **Source**: Kirk Williams, ZATO — "PMax performance dropped after a tROAS change? 6 steps to troubleshoot", https://zatomarketing.com/blog/pmax-performance-dropped-after-a-troas-change-how-to-troubleshoot · **Tier** 1 · **Date** 2026-03-25 · **Claim**: A 15% tROAS increase is a normal move; before blaming it, check (1) seasonality across all channels and YoY, (2) other channels down too, (3) business changes — stockouts, price/shipping, landing page redesign, competitor promos, (4) macro, (5) account audit — tags, conversion tracking, paused campaigns, creative/audience/feed changes, (6) PMax internals before/after — search terms, products, channel spend split, landing pages. A tROAS increase makes PMax conservative on proven queries while exploring cheaper low-intent traffic. · **Evidence**: experience ("seen the stockout scenario more than once").

4. **Source**: Brad Geddes, Adalysis — "Why your campaigns are underspending (and how to fix it)", https://adalysis.com/blog/why-your-campaigns-are-underspending-and-how-to-fix-it/ · **Tier** 1 · **Date** 2026-09-01 · **Claim**: Underspend causes: high IS already (expand targeting, don't raise budget); portfolio bid cap too low (raise it); new campaign on a data-hungry strategy (switch to a less data-dependent one); negatives blocking traffic (compare impressions to Keyword Planner); PMax taking Search's top impressions (add top search terms as exact). · **Evidence**: Adalysis account data referenced, not shown.

5. **Source**: Navah Hopkins, Optmyzr — "The impact of PPC bidding strategies", https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier** 1 · **Date** 2024-09-24 · **Claim**: Keep targets within ~±10% of historical performance; targets more often hurt than help except on Manual and tROAS; Smart Bidding changes need 2–3 weeks to settle; 50+ conversions/30 days for predictable behaviour. · **Evidence**: 14,584-account study.

6. **Source**: Mike Ryan, Smarter Ecommerce (via TechWyse 2026-09-18 and SERoundtable 2026-09-15) · **Tier** added-Tier-2 (see dossier 40) · **Date** 2026-09-14 · **Claim**: Post-change median budget-limited IS: lost-to-rank ~45%→~30%, lost-to-budget 4%→33%; CPC +15.8% on budget-limited tROAS campaigns. · **Evidence**: campaign-level data, sample size unstated.

7. **Source**: Sarah Vlietstra, ZATO — "What is Smart Bidding Exploration", https://zatomarketing.com/blog/what-is-smart-bidding-exploration-google-ads · **Tier** 1 outlet · **Date** 2026-07-13 · **Claim**: Exploration (GML May 2025; Search, then PMax) lowers the effective tROAS by a 5–30% tolerance on selected traffic segments, never raises it; requires budget headroom; Google suggests a 6–8 week test read via the bid strategy report's traffic-diversity section. · **Evidence**: feature description; no results.

## Dissenting view
Google's post-Aug-2026 advice (via Marvin, in Vallaeys 2026 and TechWyse 2026) is "move the target to your current average performance"; Rooijmans' reader did that and lost two-thirds of volume. Vallaeys says diagnose first; Williams says six non-bidding checks come before any target conclusion. The disagreement is whether a target/actual gap is a setting error (Google) or information (practitioners) — and the practitioners win on the one documented case.

## What the platform currently does [Google docs]
- [Google docs] Bid simulators use the last 7 days; unavailable when the campaign is new or had few clicks, uses a shared budget, hit or nearly hit its daily budget at least once in the last 7 days, or has an experiment running/ended within 8 days. Conversion estimates need tracking, are unreliable on sparse data, need 2 weeks without tracking changes; Search/PMax/App simulators include expected late conversions, others don't. Campaign simulator flags whether a budget increase is needed. (support.google.com/google-ads/answer/2470105, fetched 2026-10-13.)
- [Google docs via Vallaeys 2026] 17 Aug 2026 change: budget-limited target campaigns bid to target; Bid Target Adjustment Tool since 6 Jul 2026; the old "20%/two-week" target-change guidance is being phased out.
- [Google docs via Vlietstra 2026] Smart Bidding Exploration tolerance 5–30%, tROAS only.
- [Google docs] Bid strategy report shows status ("Learning", "Limited") and the date-matched average target — referenced by Vallaeys 2026; page not fetched.

## Baseline check
Read `google-ads-bidding` (troubleshooting table: "Low volume → target too aggressive → raise target 10–15%") and `google-ads-budget-management` (underspend causes table). Baseline treats "spend dropped" as "target too aggressive, raise 10–15%". This skill adds: the gap-cause taxonomy, the date-matched average-target baseline, the six pre-bidding checks, the post-Aug-2026 IS signature (lost-to-budget jump), the documented failure of "set target to actual", the simulator's 7-day/non-budget-limited blind spot, and the cap-plus-target alternative.

## Judgment calls
- Position: the simulator is read only on campaigns that were not budget-limited in the last 7 days and have ≥50 conversions/30 days; otherwise it's unavailable or noise. The diagnosis runs on bid-strategy-report data instead.
- Treated Smart Bidding Exploration as Google's product answer to "too tight"; Epiminds prefers an explicit, logged target move because Exploration's effect can't be isolated from the target.

## Canon strength: Strong
Five Tier 1 sources (Vallaeys, Rooijmans, Williams, Geddes, Hopkins) plus the Ryan data.

## Invalidated by
Google changing the simulator data window or availability rules, reversing the Aug 2026 budget-limited bidding change, or changing the bid strategy report's average-target reporting.
