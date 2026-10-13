---
name: impression-weighted-qs
id: 38
description: How to compute, read and report account-, campaign- and ad-group-level Quality Score weighted by impressions, and when a change in it means something. Use for monthly QS reporting and for building the QS work queue. Not for fixing components (34–36) or arguing whether QS matters (39).
tags: Technique / Search / Diagnose / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Google publishing a native weighted account-level quality metric, removing keyword-level QS, or changing the null-QS rule.
---
## What this is
The rule that the only account-level QS number Epiminds reports is the impression-weighted one, with a defined weighting basis, a null rule, a noise band and a work-queue rule. The simple average of keyword QS is misleading: a QS 1 keyword with one impression next to a QS 10 keyword with 10,000 impressions averages 5.5 but the traffic experiences a 10 (Geddes/Adalysis, 2017). Weighting by impressions shows "which QS levels actually receive traffic, since low-QS keywords with few impressions matter less" (Vallaeys/Optmyzr, 2015).
See also: skill 37 (qs-tracker-script) — the daily script that produces the series this skill reads.

## Where it comes from
Geddes's impression-weighted aggregation and spend-ranked ad-group priority (Adalysis, 2017). Vallaeys's diagnostic sequence and the ±0.2 normal-movement band observed across accounts (Optmyzr, 2015) and his case for ad-group aggregation (Optmyzr, 2017). Optmyzr's published tracker formula — weighted by Google Search impressions on all devices, null = 6, components 2/6/10, ad groups QS < 6 with cost > 0 (Optmyzr help, current). Parker's dual-line (weighted vs keyword-count) chart (SEL, c.2019). Levy's trend-not-snapshot rule (Optmyzr, 2026). Hopkins's noise bands (SEL, 2023).

## When to use it / when not to
Use monthly for reporting, and whenever anyone asks "what's the account's Quality Score". Use it as the first cut for the QS work queue.
Do not use the number as a target or a KPI in a client contract — Hopkins: health indicator, not KPI (SEL, 2023); Levy: never trade ROAS for it (Optmyzr, 2026). Do not compute it for campaigns without keywords (QS is keyword-level only [Google docs]). Do not compare it across accounts in different verticals: the components are rated against advertisers on the exact same keyword [Google docs], so a 6 in one auction set is not a 6 in another.

## Inputs
- Keyword-level daily or monthly pull: QS (with nulls preserved), the three component statuses, Search-network impressions by device, cost, conversions, ad group, campaign.
- Prior-period values of the same (from skill 37 or the "(hist.)" columns with day segment [Google docs]).

## Method
1. **Formula.** wQS = Σ(QS_k × imp_k) / Σ(imp_k) over keywords with imp_k > 0, where imp_k is Google Search impressions across all devices (Optmyzr help, current). Compute at ad group, campaign and account. Record the weighting basis in the report: Optmyzr saw account values move when the basis changed from desktop-only to all devices (Tyagi/Optmyzr, undated), so the basis is part of the number.
2. **Null rule.** Keywords showing "—" (not enough exact-match data since Sep 2016 [Google docs]) are included with QS imputed as 6, the neutral value Optmyzr uses (Optmyzr help). Report the share of impressions on null keywords alongside; if it exceeds 20% of Search impressions, flag wQS as provisional (Epiminds threshold; no published cut-off — Google's own change made nulls common in new accounts).
3. **Component indices.** Map Below = 2, Average = 6, Above = 10 and weight the same way (Optmyzr help), or 1/2/3 (Parker/SEL, c.2019). Report all three; the overall QS is not an exact average of them (Optmyzr help), so the indices are read separately.
4. **Always show the keyword-count mean next to wQS.** Parker plots both (SEL, c.2019). The gap is diagnostic: wQS ≫ mean means the account carries a long tail of poor low-volume keywords (clean-up candidates, not QS work); wQS ≪ mean means the money keywords are the problem (skills 34–36).
5. **Noise band.** Vallaeys's observed normal account-level movement is about ±0.2 (Optmyzr, 2015). Monthly rule: |Δ wQS| ≤ 0.2 → "stable", no commentary; 0.2–0.5 → note the campaign(s) driving it; > 0.5 → investigate with rule 6 (the 0.5 pivot is an Epiminds operating threshold — no canon source; reason: 2.5× Vallaeys's band, well below the 2-point reporting-bug step). A uniform ~2-point step across every account on the same day is a Google reporting change until proven otherwise — that was the 2015 incident, and CPCs did not move with it (Optmyzr, 2015).
6. **Investigation order when wQS moves.** (a) Confirm against the Google Ads UI "(hist.)" columns for the top-10 spend keywords [Google docs]; (b) compare the impression distribution by QS level start vs end — did impressions shift to lower levels, or did levels fall? (Vallaeys/Optmyzr, 2015); (c) check whether new keywords or a match-type expansion added null/low-QS impressions (Hopkins/SEL, 2023: broad struggles more with QS); (d) only then look at components. Levy's rule: act on a sustained downward trend across themes, not a snapshot (Optmyzr, 2026).
7. **Work queue.** Ad groups with wQS < 6 and cost > 0, sorted by cost descending (Optmyzr help) — equivalently Geddes's impression-weighted QS × spend ranking (Adalysis, 2017). Cap the queue at the ad groups covering 80% of the cost in that list (80% is an Epiminds operating threshold — no canon source; reason: Optmyzr and Geddes sort by cost but publish no cut-off). Each item goes to the component skill its weakest index points to.
8. **Reporting line.** One sentence per month: wQS, Δ vs last month classified by rule 5, share of impressions at QS ≤ 4, and the count/cost of ad groups in the queue. Nothing else about QS goes in the client report (Hopkins, 2023; Levy, 2026).

## What Google will tell you instead, and why we don't
Google's help page says QS "is not a key performance indicator and should not be optimised or aggregated with the rest of your data" [Google docs], and the UI offers only per-keyword scores with a numeric filter that silently drops nulls [Google docs, 2016 change]. We aggregate because the canon's method depends on it: Geddes's prioritisation, Vallaeys's bug detection and Optmyzr's work queue are all impression-weighted aggregates (Adalysis, 2017; Optmyzr, 2015; Optmyzr help). We agree with Google that it is not a KPI — rule 8 limits it to one line — and we go further than Google's "don't aggregate" in the other direction: the unweighted average that most agencies report is the one that actually misleads (Geddes, 2017).

## Failure modes
- **Accounts under a few hundred daily Search impressions**: one keyword dominates the weighting; read quarterly, not monthly (Vallaeys/Optmyzr, 2017, on keywords with 18 impressions not justifying attention).
- **Brand-heavy accounts**: brand keywords at 9–10 with most impressions hide a non-brand account at 4–5. Report wQS for brand and non-brand separately; Hopkins notes brand equity lifts non-brand starting scores (SEL, 2023), so mixing them also hides the lift.
- **Broad-match-heavy accounts**: a broad keyword with no impressions of its own can carry an exact keyword's score [Google docs], and broad's own scores run lower (Hopkins, 2023); wQS will drift down on expansion without any ad or page change.
- **Mobile-heavy accounts**: the all-devices basis materially changes the value (Tyagi/Optmyzr, undated); never compare against a desktop-only series.
- **New accounts**: most impressions are null-QS for weeks [Google docs]; the imputed 6 makes wQS look fine. Rule 2's provisional flag exists for this.
- **Seasonal query mix**: a seasonal spike on poorer keywords moves wQS with no quality change; rule 6(b) catches it.

## What to measure
- wQS (account, campaign, ad group), monthly, with the weighting basis stated (Optmyzr help).
- Keyword-count mean and the gap to wQS (Parker, c.2019).
- Share of Search impressions at QS ≤ 4, 5–6, ≥ 7 (Vallaeys, 2015 distribution method).
- Share of impressions on null-QS keywords [Google docs].
- Component indices, weighted (Optmyzr help; Parker, c.2019).
- Count and cost of ad groups with wQS < 6 and cost > 0 (Optmyzr help).

## Open disagreements in the canon
- **Report it at all?** Hopkins: watch quality, impression share, CTR and conversion rate instead (Optmyzr PPC Town Hall, 2020; SEL, 2023). Vallaeys/Tyagi: keep it as a gauge (Town Hall, 2020). Epiminds reports it, in one line, impression-weighted.
- **Weight by impressions or by cost?** Geddes and Optmyzr weight the metric by impressions and rank the work by spend (Adalysis, 2017; Optmyzr help); Vallaeys's 2015 sequence ranks ad groups by spend × low QS. Epiminds: impressions for the metric, cost for the queue. Cost-weighting the metric would let CPC changes move it with no quality change.
- **Noise band.** The ±0.2 figure is one practitioner's observation from 2015 (Optmyzr); no newer published band exists. We use it and will replace it with the account's own 12-month standard deviation once skill 37 has a year of data.
