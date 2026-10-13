---
name: auction-insights-trend-reading
id: 83
description: Monthly procedure for reading auction insights as a time series to explain a performance shift with no internal change — separating market demand, competitor ad-rank moves, and your own bidder's behaviour. Not for IS budget/rank routing (see 84) or for competitor ad-copy research.
tags: Diagnostic / Search / Diagnose / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Google changing auction-insights metric definitions, the 10% IS display floor, or time segmentation; removal of keyword-level auction insights under keywordless Search.
---
## What this is
A fixed order of checks that puts auction insights third, after targeting and bids, and reads it weekly-segmented against your own CPC, IS and search-volume estimate. Position: a competitor-driven CPC rise under Smart Bidding is a reason to check CPA, not to bid; auction insights is used to name the cause and to time budget, not to chase rank.

## Where it comes from
Geddes' Adalysis series: the CPC-change diagnostic order (Adalysis, 2020), the search-volume-vs-impressions split (Adalysis, 2019), the auction-insights reading rules and segmentation (Adalysis, 2021), the weekly-trend template and budget-cycle signatures (Adalysis, 2019), and the true-vs-impression competitor classification (Adalysis, 2019). Metric definitions and limits from Google Ads Help, labelled. All practitioner method is one author; see the open disagreements.

## When to use it / when not to
Use when CPC, IS, CTR or conversions moved more than ~15% month on month (Epiminds operating threshold — no canon source; reason: Geddes' worked examples start at 25–34% moves (Adalysis, 2020) and 15% is the smallest move we have found worth a diagnostic) and change history shows no edit that explains it; use monthly as a standing check on the top-spend campaigns. Use before any conversation with a client about "competitors are bidding us up".

Do not use on campaigns whose IS is under 10% — Google shows no auction-insights rows [Google docs]. Do not use on search-partner traffic (excluded) [Google docs]. Do not use Shopping position metrics; Shopping has only IS, overlap and outranking share [Google docs]. Do not use it to justify bid increases outside a conquest objective (Adalysis, 2021).

## Inputs
- Auction insights for the affected campaigns, segmented by week, last 13 weeks, exported (the UI shows ~8–15 competitors; a connector/Looker export shows all) (Adalysis, 2021; 2019).
- Your weekly: impressions, IS, lost IS (budget/rank), avg CPC, CPA/ROAS, conversions.
- Estimated search volume per week = impressions ÷ IS (Adalysis, 2019).
- Change history for 90 days; bid strategy and targets.
- QS trend (impression-weighted) for the campaign.
- Brand and non-brand campaigns kept separate; a competitor list per region for multi-country accounts (Adalysis, 2021).

## Method
1. **Rule out yourself first.** Targeting changes (adds, pauses, negatives, match types, audiences) → bid changes, including silent moves by automated bidding; "the most common reason CPCs change is because you changed your bids" (Adalysis, 2020). If either explains the shift, stop; auction insights is not the cause.
2. **Split market from account.** Plot estimated search volume (impressions ÷ IS) against impressions, weekly (Adalysis, 2019).
   - Volume moved, impressions moved with it, IS flat → demand shift. Check whether a peak period was entered or left and compare year on year; competitors are not the story.
   - Volume flat, impressions down, lost IS (rank) up → go to step 3.
   - Volume flat, impressions down, lost IS (budget) up → CPC rose; go to step 3 to see whether a competitor caused it.
3. **Read auction insights as a series, not a snapshot.** For each competitor with overlap rate ≥10% in any week (the 10% overlap floor, the 13-week window in Inputs, and the ">20% overlap for 4+ weeks" new-entrant rule below are Epiminds operating thresholds — no canon source; reason: 10% mirrors Google's own IS display floor [Google docs], 13 weeks gives three monthly budget cycles for the signature in Adalysis (2019; 2021), and 4 weeks is the shortest run Geddes' 3-week rule plus one week of confirmation allows):
   - Competitor top-of-page rate and outranking share rising across 3+ consecutive weeks while yours fall → they raised ad rank (bid or QS); this is the competitor-pressure signature (Adalysis, 2020).
   - Competitor IS low but position-above rate high → an aggressive bidder taking few, expensive impressions; likely high CPA on their side; do not match (Adalysis, 2021).
   - Competitor IS well above yours, overlap high → more budget or better QS than you; a structural competitor, not an event (Adalysis, 2021).
   - Competitor overlap collapses in the last week of each month, or tapers through a quarter → budget-cycle advertiser; expect cheaper clicks in that window and shift budget there (Adalysis, 2019; 2021). Confirm on at least two cycles before acting.
   - A new domain appears and holds >20% overlap for 4+ weeks → new entrant; classify in step 5.
4. **Check QS before blaming anyone.** A falling QS raises your CPC and lowers your top-of-page rate with no competitor change at all (Adalysis, 2020). If impression-weighted QS dropped ≥1 point in the window (Epiminds operating threshold — no canon source; reason: QS is an integer and one point is the smallest real move), treat QS as the primary cause and competitor movement as secondary.
5. **Classify competitors.** True competitor (sells what you sell to the same buyer) vs impression competitor (shares the SERP, not the customer) (Adalysis, 2019). Only true competitors go into the client narrative and the ad-messaging backlog; impression competitors are noise even at high overlap.
6. **Decide.**
   - Cause = demand → no bidding action; adjust budget pacing and forecasts.
   - Cause = competitor ad rank, you are on Smart Bidding, CPA/ROAS still on target → no action; a CPC rise with flat CPA under automated bidding is the bidder working (Adalysis, 2020). Record it.
   - Cause = competitor ad rank, CPA/ROAS off target → fix QS and assets first (see 84), then consider the target; raise bids for rank only if the campaign's objective is conquest (Adalysis, 2021).
   - Cause = competitor withdrawal (overlap and top-of-page falling) → expect lower CPC; check that the bidder is capturing the cheaper IS rather than pocketing it as under-delivery, and lift budget if lost IS (budget) appears.
   - Cause = QS → treat as 84 rank route.
7. **Segment before reporting.** Repeat at campaign and region level: overlap can be 43% in one country while trivial overall (Adalysis, 2021). Never present an account-level auction-insights table that mixes brand and non-brand; brand campaigns distort it because competitors mostly do not bid on your brand (Adalysis, 2021).

## What Google will tell you instead, and why we don't
- Google's UI presents auction insights as a snapshot table and its recommendations respond to "competitors outranking you" with bid or budget increases. Geddes' order puts your own targeting, bids and QS before competitor moves (Adalysis, 2020) and allows rank-chasing only under a conquest objective (Adalysis, 2021). We never raise a bid or target because of this report alone.
- Google shows ~8–15 competitors and no rows under 10% IS [Google docs]. The new entrant that matters usually starts below that line; we export weekly and keep all domains (Adalysis, 2019).
- Target Impression Share bidding is Google's native answer to losing rank to a competitor. The aggressive-bidder pattern — low IS, high position-above — is exactly what that strategy produces on the other side, and Geddes reads it as a likely high-CPA advertiser (Adalysis, 2021). We do not join them.

## Failure modes
- **Low-IS campaigns (<10%).** No data [Google docs]; the method cannot run. Use IS decomposition (84) only.
- **Shopping.** No position-above or top-of-page metrics; only IS, overlap, outranking, Search Network only [Google docs]. Step 3's rank signatures reduce to outranking share.
- **PMax.** Account/campaign level only, Search and Shopping blended [Google docs]; competitor moves cannot be tied to a query set.
- **Multi-country accounts read at account level.** Country-specific competitors are invisible in the blend (Adalysis, 2021).
- **Brand campaigns in the mix.** Competitor overlap on brand is structurally low; blending brand understates competition (Adalysis, 2021).
- **Short windows.** One week of auction insights is a snapshot; the budget-cycle and ad-rank signatures need 3+ weeks and ideally two cycles (Adalysis, 2019; 2021) — a single month-end dip is not a pattern.
- **Smart Bidding already responding.** The bidder may have moved your CPC in response to the competitor before you read the report; step 1 will show "bid change" with no edit, and the correct read is step 6's "CPA on target → no action" (Adalysis, 2020).

## What to measure
Weekly, per top-spend campaign: your IS, lost IS (budget/rank), avg CPC, QS, estimated search volume; per competitor with ≥10% overlap: overlap rate, position-above rate, top-of-page rate, outranking share (Adalysis, 2021; [Google docs]). Keep a dated competitor log with classification (true/impression) and the budget-cycle flag. Report the cause code from step 6 and whether CPA/ROAS held.

## Open disagreements in the canon
- **Single-author canon.** Every practitioner rule here is Geddes; no second Tier 1 voice on auction-insights trend reading was reachable. Epiminds applies the method as written and flags the budget-cycle signal as a hypothesis to confirm on the client's own data rather than a known pattern.
- **Act on competitor pressure or not.** Geddes 2021: bid up only for conquest. Geddes 2020: under automated bidding, a 25% CPC rise with flat CPA is correct behaviour. Epiminds: the 2020 rule governs Smart Bidding accounts (check CPA, leave the bidder alone); the 2021 rule governs manual/Max Clicks accounts and any explicit conquest campaign. Reason: on Smart Bidding the response has already happened by the time the report is read.
