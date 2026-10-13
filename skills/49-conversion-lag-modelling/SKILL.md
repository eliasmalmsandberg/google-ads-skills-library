---
name: conversion-lag-modelling
id: 49
description: Use before any verdict on "recent performance" in an account with multi-day conversion lag — monthly, and whenever someone says last week looks bad. Produces a maturity curve and a matured/expected read for the open window. Not for attribution-window selection (baseline), not for incrementality, and not a replacement for skill 46 when the drop survives the lag check.
tags: Diagnostic / All / Diagnose / Established / Monthly
last_verified: 2026-10-13
invalidated_by: Google changing conversion-time reporting or the lag-bucket segments, the 90-day click window, or how late conversions are weighted in Smart Bidding.
---
## What this is
Google reports conversions against the click date, so the last N days always look worse than they will end up — by exactly the share of conversions that haven't arrived yet. Every Smart Bidding verdict has to be made on matured data against date-matched targets, with the conversion-delay window excluded (Vallaeys/Optmyzr, 2026); misreading lag as a performance drop is one of the two most common bidding mistakes Optmyzr sees (Vallaeys/Optmyzr, 2026). The skill turns the account's own lag distribution into a maturity curve and two numbers for the open window: what has landed and what will.

## Where it comes from
Vallaeys (Optmyzr 2026 ×2; SEL 2026) supplies the rules — exclude the delay window, 1–2 full cycles, late signals are weighted later than they're reported. Rooijmans (2025) supplies the lag-share rule for widening any click-based window. Google docs supply the by-conversion-time reporting and the simulator/exclusion lag behaviour. The curve construction itself is Epiminds' method on those primitives — the canon gives no published one.

## When to use it / when not to
Use monthly on every account, and before any read of a period that ends inside the account's p90 lag. Mandatory for lead gen, B2B, considered ecommerce, and any account with offline or imported conversions (imported conversions appear in reporting before the bidder fully weights them — Vallaeys/SEL, 2026). Skip it when p90 lag is under 1 day and no imports exist — then the open window is only yesterday. Don't use it to explain away a real post-event dip: the week after Cyber Monday showed CVR 7.3% below pre-peak and CPC 10.2% higher in 4,211 accounts (Padmanaban/Optmyzr, 2026); maturity doesn't fix that.

## Inputs
- 6–12 months of conversions by conversion-lag bucket / days-to-conversion, per primary conversion action (Google Ads API segments, 2026)
- Conversions by click date vs by conversion time for the same period
- Conversion window per action (max 90 days — Gray/WebMechanix, 2024)
- Import cadence and latency for offline/CRM actions (skill 48)
- Date of any target, budget or tracking change

## Method
1. **Build the curve per primary action.** From a closed period (ended ≥ conversion window ago), compute cumulative share of conversions landed by day 0, 1, 2, 3, 7, 14, 30, 60, 90 after click. Record p50, p70, p90. Rebuild monthly — lag drifts with mix, and post-change windows (e.g. 17–31 Aug 2026) are unreliable for forecasts (Vallaeys/Optmyzr, 2026). For imported actions add the pipeline latency to every bucket (skill 48).
2. **Declare the open window.** Any day within p90 lag of today is open. No CPA/ROAS verdict is issued on open days — "matured performance against date-matched targets, excluding the conversion-delay window" (Vallaeys/Optmyzr, 2026). If p90 > 30 days, report on the matured period and the open period separately, every time (Epiminds operating cut-off, no canon source; reason: at that lag a monthly report has no closed days at all, so a single blended number would be entirely unmatured).
3. **Read the open window two ways.** Matured = conversions landed so far. Expected = landed ÷ maturity(days since click), summed per day. Present both and the gap; the gap is the only honest "recent performance". This arithmetic is Epiminds' construction on Google's by-conversion-time reporting; the rule it serves is Vallaeys'.
4. **Trigger rule.** A drop counts only if *expected* conversions for the open window are ≥20% below the matured run rate (Epiminds operating threshold, no canon source; reason: double Hopkins' ±10% target tolerance, to leave room for the error in the expected number), or matured CPA/ROAS for closed days is off date-matched target by more than the ±10% tolerance Hopkins found targets tolerate (Hopkins/Optmyzr, 2024). Then go to skill 46. Anything smaller inside the open window is lag.
5. **Widen every click-based window by lag.** Data exclusions, before/after tests, experiment reads: if more than 30% of conversions take over a day, widen the window by the typical delay on the front end (Rooijmans, 2025); Google's own rule is to "account for conversion delay" and cover ≥90% of affected clicks (Google Ads Help, 2026). Use p70 as the offset, p90 where the 30% rule bites.
6. **Cycle rule for change evaluation.** One conversion cycle = p90 lag. Wait 1–2 full cycles after any target or budget change (Vallaeys/Optmyzr, 2026), ≥3 cycles or 4 weeks for an experiment read (Vallaeys/Optmyzr, 2026). Budget changes alone need 2–3 weeks to settle (Hopkins/Optmyzr, 2024) — take the longer.
7. **Imported-conversion caveat.** Offline and modelled conversions show in reporting before the bidder weights them (Vallaeys/SEL, 2026), so the matured CPA can look better than the bidder's view for a cycle. Don't tighten targets on a freshly imported stage until one cycle after it first lands.
8. **Simulator alignment.** Search, PMax and App simulators already include expected late conversions; Display/Video/Shopping simulators count only conversions recorded in the 7-day period (Google Ads Help, 2026). Apply your maturity factor to the latter before comparing to the former.
9. **Client reporting.** Every report carries three labels: closed period (verdict allowed), open period (matured + expected), and the p90 used. A 2-week feedback loop is what steers bidding; 90 days is too late to matter (Vallaeys/Newson, 2026) — which is the argument for also fixing import latency, not just modelling it.

## What Google will tell you instead, and why we don't
Google's UI defaults to click-date reporting with a "Learning"/"Limited" badge and a Recommendations panel that reacts to last 7 days, and its Bid Target Adjustment Tool adjusts targets on recent performance (Vallaeys/Optmyzr, 2026). We don't act on a 7-day view in any account whose p90 lag is longer than that, and we don't let a tool reset targets on open-window data. Google's point that the bidder already accounts for lag (Vallaeys/SEL, 2026) is true for *bidding*; it does not make the *reporting* mature, which is where the human mistakes happen.

## Failure modes
- **Sub-day lag ecommerce**: the curve is flat; the skill adds nothing but a label.
- **Long B2B cycles with p90 > 60 days**: most of any month is open; the expected number carries wide error — present ranges, and push for an earlier stage (skill 43/48).
- **Mix shifts**: a new campaign type or geo changes the lag; a stale curve over- or under-corrects. Rebuild monthly.
- **Real post-peak dips** (Padmanaban/Optmyzr, 2026): maturity restores expected volume that isn't coming.
- **Tracking breaks inside the open window**: lag modelling hides them for days; keep skill 44's exclusion path and daily zero-conversion alerts separate.
- **Backfilled imports**: a batch upload lands weeks of conversions on one day; by-conversion-time reporting spikes and the curve is corrupted for that month.

## What to measure
Monthly: p50/p70/p90 lag per primary action; curve drift vs last month; share of the last 30 days that is open; expected-vs-matured gap at month end and its realised error a cycle later (calibration). Per change: cycles elapsed before the verdict.

## Open disagreements in the canon
- **Operator-modelled vs bidder-handled.** Vallaeys (SEL 2026) says the bidder handles lag; Rooijmans builds it into every window by hand. Epiminds: the bidder handles bidding, we handle reporting and every human decision.
- **Lag dashboards vs incrementality.** Brainlabs' line (2026, not canon) is that the lag that matters is upper-funnel influence over weeks. We treat that as a separate question; this skill only stops false alarms.
- **Window offset.** Google says ≥90% of affected clicks; Rooijmans says widen by typical delay when >30% lag over a day. We use p70 as default, p90 when the 30% rule bites.
