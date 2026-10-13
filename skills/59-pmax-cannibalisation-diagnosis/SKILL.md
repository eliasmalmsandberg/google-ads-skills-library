---
name: pmax-cannibalisation-diagnosis
id: 59
description: Prove or disprove that a Performance Max campaign is taking Search (brand or non-brand) traffic that Search was already winning, and decide what to do about it. Not for Search-vs-Search keyword overlap (see the cannibalization baseline) and not for PMax vs Standard Shopping product overlap.
tags: Diagnostic / PMax / Diagnose / Established / Monthly
last_verified: 2026-10-13
invalidated_by: A change to the rule that an identical Search keyword takes precedence over PMax; cost appearing in the PMax search terms report; Google shipping Search-vs-PMax or channel-level controls; removal of the PMax search terms report.
---
## What this is
A diagnosis that separates three things people call "cannibalisation": (a) PMax entering auctions Search was eligible for and winning them, (b) PMax entering auctions Search had become ineligible for (budget, bid floor, geography), and (c) overlap that costs nothing because the two convert the same. Overlap itself is near-universal — 91% of 503 accounts at keyword level, 97% at term level (Vallaeys/Optmyzr, 2025) — so the question is never "is there overlap" but "is Search losing auctions it would have won, and does it convert better when it wins".

## Where it comes from
Optmyzr's 503/511-account study (Vallaeys, 2025) and Adalysis' 3,300-campaign study (Geddes, 2024) for overlap and win rates; Kirk Williams (ZATO, 2023) on auction eligibility; Nils Rooijmans (2022) on the priority rule; Mike Rhodes' PMax Insights tabs (2026) for brand buckets and change dating; PPC.io (Dunlop, 2026) for the verdict rule; Optmyzr's BFCM data (2026) for mixed-account benchmarks.

## When to use it / when not to
Use when Search conversions or impression share fell after a PMax launch or budget increase, when PMax ROAS beats Search by a margin brand share could explain, or monthly in any account running both. Do not use on PMax campaigns under a month old or on accounts where Search is budget-capped — fix the cap first, because an ineligible Search campaign is the leading alternative explanation (Vallaeys/Optmyzr, 2025; Beltman in Rooijmans, 2022).

## Inputs
- PMax search terms export per campaign (Insights and reports → search terms insight → view detailed data), 30–90 days; drop terms under 10 impressions (Geddes/Adalysis, 2024).
- Search campaigns' search term report and keyword list, same window.
- Search campaign diagnostics: Search lost IS (budget), Search lost IS (rank), location settings.
- Brand term list; PMax S.Cat buckets (Rhodes, 2026).
- Change history with dates of PMax launch/budget/target changes (Rhodes' Change History tab joins these to performance).

## Method
1. **Date the shift.** Plot Search clicks, conversions and impression share weekly for 8 weeks before and after the PMax change. If Search IS fell in the same week PMax spend rose, continue; if it fell earlier or later, look elsewhere first (seasonality, bids, competitors).
2. **Rule out Search ineligibility before blaming PMax.** Check: Search lost IS (budget) above 0 on the affected campaign; a tROAS/tCPA target tightened in the window; geo or schedule limits; brand bids low enough to sit under bid floors (Williams/ZATO, 2023). Any of these makes Search ineligible for part of the auctions, and PMax takes them by design — the fix is Search-side, not a PMax exclusion (Vallaeys/Optmyzr, 2025).
3. **Build the overlap table.** Normalise terms (lowercase, strip punctuation), join PMax terms to Search terms, and compute: share of PMax clicks on overlapping terms; share of overlapping terms that exactly match a Search keyword. Adalysis' non-retail benchmark: 45% of PMax terms also appear as Search terms, but only 2.8% exactly match a keyword (Geddes/Adalysis, 2024). A keyword-match share far above that means your Search keywords are losing auctions they should win under Google's identical-keyword rule — which Optmyzr found happening on exact match in practice (Vallaeys/Optmyzr, 2025).
4. **Compare performance on the overlap only.** For each overlapping term with enough volume, compare CTR and CVR between campaign types; treat differences under 10% as noise (Vallaeys/Optmyzr, 2025). Expect Search to win CVR when there is a difference: 84% of the time in Adalysis' data, 19% vs 6% in Optmyzr's with 75% no-difference (Geddes/Adalysis, 2024; Vallaeys/Optmyzr, 2025). Do not compute CPA or ROAS per term — PMax reports no cost at term level (Vallaeys/Optmyzr, 2025).
5. **Split brand from non-brand.** Read the S.Cat buckets (Rhodes, 2026). If brand is the bulk of the overlap and brand Search IS is below ~95%, this is a brand-handover problem: run skill 55 (brand exclusions) and add brand close variants to Search as exact match (Rooijmans, 2022; Vallaeys/Optmyzr, 2025).
6. **Verdict.** PMax is cannibalising if, after step 2 is clean: (i) overlapping terms carry more than a quarter of PMax clicks, (ii) Search wins CVR on the majority of those terms by more than 10%, and (iii) PMax non-brand ROAS has been below the Search non-brand baseline for two consecutive months (Dunlop/PPC.io, 2026). Dunlop's framing applies: a campaign that only redistributes conversions Search already won has moved the credit and added a fee (Dunlop/PPC.io, 2026).
7. **Act in this order.** (a) Add the overlapping non-brand converting terms as exact-match keywords in Search with matching ad copy and landing page (Geddes/Adalysis, 2024; Vallaeys/Optmyzr, 2025). (b) Turn off auto-apply recommendations that remove "redundant" keywords (Vallaeys/Optmyzr, 2025). (c) Only then add campaign-level negatives in PMax for terms where Search clearly wins (skill 62). (d) If the verdict holds, cut PMax budget by half and re-audit after four weeks (Dunlop/PPC.io, 2026). (e) Lead gen with a persistent verdict: pausing PMax and expanding Search is a legitimate outcome (Geddes/Adalysis, 2024).
8. **Re-measure after 4 weeks.** Repeat steps 3–4. Overlap will not reach zero; the target is Search IS restored on the promoted keywords and PMax non-brand ROAS at or above the Search baseline.

## What Google will tell you instead, and why we don't
Google's help says an identical Search keyword takes precedence over PMax, so overlap on exact match should not happen [Google docs]. Both cross-account studies found it does (Vallaeys/Optmyzr, 2025; Geddes/Adalysis, 2024), and Adalysis notes Google's second help file concedes phrase and broad keywords can lose to PMax. Google's recommendations engine will also offer to remove "redundant" keywords; removing the Search duplicate hands the term to PMax, so we refuse that recommendation (Geddes/Adalysis, 2024; Vallaeys/Optmyzr, 2025).

## Failure modes
- **Budget-capped or target-constrained Search**: the diagnosis will blame PMax for auctions Search declined (Vallaeys/Optmyzr, 2025).
- **Mixed retail accounts**: Adalysis' overlap figures are non-retail; Shopping-driven PMax overlaps differently and PMax vs Standard Shopping on the same products is a separate problem — Williams says PMax will always take eligible Shopping traffic (Williams/ZATO, 2023). Optmyzr's December data in mixed accounts had PMax 680% vs Standard Shopping 666% ROAS at identical CPCs, i.e. no clear loser (Optmyzr, 2026).
- **New or low-volume PMax**: fewer than 10 impressions per term leaves nothing to compare (Geddes/Adalysis, 2024).
- **Brand-dominated accounts**: step 5 will account for nearly all overlap; the non-brand verdict cannot be reached.
- **One-month snapshots**: Optmyzr's study was one month and the author flags it; require two months before cutting budget.

## What to measure
Search IS and lost IS (budget/rank) on affected campaigns, weekly. Share of PMax clicks on overlapping terms. Win rate (CVR) on overlapping terms, Search vs PMax. PMax non-brand ROAS vs Search non-brand ROAS, monthly. Count of terms promoted to Search and their Search IS after 30 days.

## Open disagreements in the canon
Hopkins (Optmyzr, 2023) called the cannibalisation worry "unfounded"; Optmyzr's own 2025 study and Adalysis (2024) found overlap almost everywhere with Search converting better when there is a difference. Vallaeys (2025) still cautions that Search ineligibility, not PMax, may explain much of it. Epiminds goes with the studies and Vallaeys' caveat together: overlap is assumed, ineligibility is checked first, and a cut is made only on the two-month rule.
