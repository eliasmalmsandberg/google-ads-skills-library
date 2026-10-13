---
name: bid-simulator-target-too-aggressive
id: 46
description: Use when spend or volume dropped after a tCPA/tROAS change, or a Smart Bidding campaign is under-delivering and someone says "the target is too aggressive". Decides whether it is, using the bid strategy report and (when it's actually available) the simulator. Not for manual-CPC campaigns, not a learning-period explainer, and not for conversion-lag artefacts (skill 49 first).
tags: Diagnostic / All / Diagnose / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google changing the simulator data window or availability rules, reversing the 17 Aug 2026 budget-limited bidding change, or changing the bid strategy report's average-target reporting.
---
## What this is
"Target too aggressive" is the default diagnosis for any volume drop, and the default fix is "raise it 10–15%". Half the time the target is fine and the drop is a stockout, a tracking break or lag (Williams/ZATO, 2026; Vallaeys/Optmyzr, 2026). The other half, the usual fix is also wrong since 17 Aug 2026: budget-limited campaigns now bid to the stated target instead of rationing, so a target moved to "current actual" buys more expensive clicks, not more volume — one documented account went from 20–30 leads a month to 6 in two weeks at full spend (Rooijmans, 2026). The simulator, meanwhile, is unavailable on exactly the campaigns in question: it uses the last 7 days and won't show for a campaign that hit its daily budget even once in that window (Google Ads Help, 2026).

## Where it comes from
Vallaeys (2026) supplies the gap taxonomy and the date-matched baseline; Williams (2026) the six non-bidding checks; Rooijmans (2026) the post-change counterexample and the cap-plus-target fix; Geddes (2026) the underspend causes; Hopkins (2024) the ±10% and settle-time rules; Ryan (2026) the post-change IS signature; Google docs for the simulator's limits.

## When to use it / when not to
Use when a tCPA/tROAS/Max-with-target campaign shows a ≥20% fall in matured conversions or spend over 2+ weeks, or has been "Limited" in the bid strategy report for a week. Don't use within the first 2–3 weeks after any target or budget change — that's settle time, not a signal (Hopkins/Optmyzr, 2024). Don't use until skill 49 has confirmed the drop survives the lag window. Don't use on a campaign with <50 conversions/30 days — below that the question "is the target right" has no stable answer (Hopkins/Optmyzr, 2024).

## Inputs
- Bid strategy report: status, date-matched average target vs matured actual CPA/ROAS, by week
- IS, IS lost to rank, IS lost to budget — weekly, before and after the change
- Avg CPC and CPC on converting search terms (p90), before/after
- Conversions/30 days; conversion-lag p70
- Change history: target, budget, tracking, creative, feed, landing pages
- Business context: stock, price, promos, other channels' trend (Williams/ZATO, 2026)

## Method
1. **Rule out non-bidding causes first** — Williams' six: seasonality across all channels and YoY; other channels down too; stockouts, price/shipping, landing page redesign, competitor promos; macro; tags, conversion tracking, paused campaigns, creative/audience/feed changes; then the campaign's own before/after on search terms, products, channel split, landing pages (Williams/ZATO, 2026). If any of these explains the drop, stop here.
2. **Baseline correctly.** Compare *matured* actual CPA/ROAS to the date-matched *average* target from the bid strategy report, excluding the conversion-delay window (Vallaeys/Optmyzr, 2026). A target changed 10 days ago is not "the target" for last month's clicks.
3. **Name the gap cause** — one of four: deliberate headroom (you set it loose on purpose), stale setting (business changed), measurement issue (tracking or lag), or scarce-budget selection — the campaign was beating target only because budget rationing picked the cheapest auctions (Vallaeys/Optmyzr, 2026). Only "stale" and "scarce-budget" are target problems.
4. **Read the IS signature.** Post-Aug 2026, a budget-limited campaign whose lost-to-budget IS jumped (median 4%→33% in Ryan's data) while lost-to-rank fell and CPC rose ~16% is bidding to target as designed, not failing (Ryan/Smarter Ecommerce, 2026). If instead IS lost to rank rose and spend fell with CPC flat, the target is binding too hard — or a portfolio bid cap is excluding auctions (Geddes/Adalysis, 2026).
5. **Simulator — only if usable.** It needs 7 days without hitting the daily budget, no shared budget, no experiment in the last 8 days, and ≥2 weeks without tracking changes; its conversion estimates are unreliable on sparse data (Google Ads Help, 2026). When it shows, read the required-budget and conversions-vs-target curve for where the next 10% of target buys <5% volume — that's the knee. If it doesn't show, say so in the write-up; don't eyeball a guess from a different campaign.
6. **Move the target, not to actual.** Change in steps of ≤10% of history (Hopkins/Optmyzr, 2024). If the campaign is budget-limited and over-performing its target, Google's advice is to set target to actual (via Vallaeys/Optmyzr, 2026); we don't — Rooijmans' case shows the volume collapse. Keep the business-acceptable target and add a portfolio max-CPC cap at the 90th–95th percentile of converting-term CPCs (Rooijmans, 2026; skill 40), then tighten target / loosen cap alternately in 10–20% steps once volume is back (Rooijmans, 2026).
7. **Underspend without a target problem**: IS already high → expand targeting, don't raise budget; new campaign on tCPA/tROAS with no history → switch to a less data-hungry strategy; impressions far below Keyword Planner → check negatives; PMax taking Search's top impressions → add the top search terms as exact (Geddes/Adalysis, 2026).
8. **Hold 1–2 full conversion cycles** after any change, change one variable at a time, keep an unconstrained campaign as control (Vallaeys/Optmyzr, 2026). Snapshot settings and annotate.

## What Google will tell you instead, and why we don't
Google's post-change guidance and its Bid Target Adjustment Tool (since 6 Jul 2026) move the target toward recent average performance (Vallaeys/Optmyzr, 2026). We don't, because the one documented case of following it cut volume by two-thirds (Rooijmans, 2026), and because "recent average" on a formerly budget-limited campaign was a rationing artefact, not an achievable target at full spend (Vallaeys/Optmyzr, 2026). Google also offers Smart Bidding Exploration (5–30% tROAS tolerance on chosen segments) as the answer to a tight target (Vlietstra/ZATO, 2026); we prefer an explicit, logged target move, because Exploration's effect can't be separated from the target in the read-out.

## Failure modes
- **Under 50 conversions/30 days**: any target reading is noise (Hopkins/Optmyzr, 2024).
- **Budget-limited in the last 7 days**: no simulator; practitioners who "read" one are reading another campaign (Google Ads Help, 2026).
- **Long-lag lead gen**: the "drop" is unmatured data; run skill 49 first (Vallaeys/Optmyzr, 2026).
- **Stockout / feed outages in ecommerce**: looks exactly like a target problem on PMax (Williams/ZATO, 2026).
- **17–31 Aug 2026 window**: Google itself said forecasts were unreliable; don't diagnose on it (Vallaeys/Optmyzr, 2026).
- **Shared budgets**: campaign simulator unavailable, and lost-to-budget IS is pooled (Google Ads Help, 2026).
- **Portfolios with a cap**: a cap set too low mimics an aggressive target — check the cap before the target (Geddes/Adalysis, 2026).

## What to measure
Weekly: matured actual vs date-matched average target; IS lost to rank vs budget; CPC and converting-term p90 CPC; conversions/30 days vs the 50 floor; bid strategy status. After a change: 1–2 cycles before verdict; control campaign delta.

## Open disagreements in the canon
- **Target to actual.** Google says yes; Rooijmans' case says no; Vallaeys says diagnose first. Epiminds: never on a formerly budget-limited campaign; elsewhere only in ≤10% steps.
- **Cap vs target.** Vallaeys warns caps add risk; Rooijmans uses them as the primary lever post-change. We use the cap when the drop is CPC-driven, the target when it's rank-driven.
- **Exploration vs explicit moves.** Google and ZATO describe Exploration neutrally; we treat it as a last resort because it hides the counterfactual.
