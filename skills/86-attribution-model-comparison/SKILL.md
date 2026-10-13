---
name: attribution-model-comparison-dda-vs-last-click
id: 86
description: How to explain and reconcile the gap between Google Ads conversions (DDA, click-date, modelled, value-adjusted) and the client's analytics or CRM, and how to give upper-funnel campaigns credit without pretending attribution is incrementality. Not for choosing a model (DDA is the default and the canon has no reason to override it) and not for incrementality (see 80, 81).
tags: Diagnostic / All / Diagnose / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google changing the DDA default or its 200-conversion / 2,000-interaction recommendation, the 90-day GCLID import window, the new-customer value adjustment columns, or by-conversion-time reporting.
---
## What this is
A reconciliation procedure. When a client's GA4/CRM number and the Google Ads number disagree, the gap is decomposed into five named causes — model, timing, modelling, value adjustment, and import window — before anyone argues about which number is "right". Position: keep DDA for bidding, one model and one window across every primary conversion action, report Original conversion value by conversion time to the client, and never use any attribution delta as evidence that a campaign is incremental.

## Where it comes from
Geddes' consistency rule — one attribution model and one click window across all conversion actions or "bad bids are made for your account" (Geddes/Adalysis, 2021), and his earlier framing that the model follows the question being asked (Geddes/Adalysis, 2017; 2018). The pre-canon baseline skill google-ads-attribution is named where it is corrected. Vallaeys on why platform and CRM numbers disagree by design: aggregate attribution, modelled conversions validated by holdbacks, and matching/attribution/bidding as separate processes (Vallaeys/SEL, 2026); the 90-day GCLID ceiling and the early-proxy answer for long cycles (Vallaeys & Newson/Optmyzr, 2026). Williams on adjusted vs Original conversion value (Williams/ZATO, 2026). By-time columns from Stemen (Stemen/SEJ, 2026). Platform defaults from Google Ads Help, labelled.

## When to use it / when not to
Use when the client's analytics shows a materially different conversion or revenue figure from Google Ads (our trigger: >15% gap on the same conversion definition over 30 days), when a stakeholder asks why Search/brand "gets all the credit", or when an upper-funnel campaign is about to be cut on last-click numbers.

Do not use to decide whether a campaign is incremental — attribution redistributes credit among observed ad clicks and cannot see what would have happened without them; that is skill 80/81. Do not run a model comparison on accounts under ~200 conversions/30 days: DDA still runs but credits less precisely [Google docs], and the deltas are noise.

## Inputs
- Per conversion action: model, click-through window, primary/secondary status, source (tag, GA4 import, offline import), 90-day counts (Geddes/Adalysis, 2021).
- Google Ads columns for the period: Conversions, Conversions (by conv. time), Conv. value, Conv. value (by conv. time), Original conv. value (Stemen/SEJ, 2026; Williams/ZATO, 2026).
- Whether "adjust bidding to acquire new customers" is on (Williams/ZATO, 2026).
- Client-side number: GA4 or CRM conversions for the same period, with its attribution setting and lookback.
- Median conversion lag and share of conversions landing after 90 days (Vallaeys & Newson/Optmyzr, 2026).

## Method
1. **Normalise the account before comparing anything.** Every primary conversion action on the same model (DDA) and the same click-through window; mixed models or windows across actions produce inconsistent bidding and un-comparable reports (Geddes/Adalysis, 2021). Secondary actions can differ; they do not feed bidding.
2. **Decompose the gap in this order; stop recording when the residual is under ~10%.** (The ~10% stop, the ≥20% assist line in step 4, the ~4-week feed age in step 6 and the >10-point residual alert under What to measure are Epiminds operating thresholds — no canon source; reason: 10% is below the modelled residual Vallaeys says to expect as normal (Vallaeys/SEL, 2026) so chasing it is wasted work; 20% is where a last-click cut would materially misjudge a campaign; 4 weeks reflects Vallaeys' note that the bidder validates new signals over time (Vallaeys/SEL, 2026); a 10-point residual swing is larger than any month-on-month modelling change we have seen and usually a tag or import break.)
   a. **Timing.** Re-pull Google Ads by conversion time. The default columns book conversions and value to the click date, so a month with long lag under-reports this month and over-reports an earlier one (Stemen/SEJ, 2026; Vallaeys/SEL, 2026). The client's analytics reports by conversion date. This alone usually explains the largest share for anything with >7 days median lag.
   b. **Value adjustment.** Compare Conv. value with Original conv. value. If they differ, the new-customer adjustment (or a value rule) is inflating Conv. value "intentionally … as a bidding signal"; Original conv. value is the ground truth for the client (Williams/ZATO, 2026). Report Original.
   c. **Model.** Switch the Google Ads view to last click for the same actions and compare per campaign. The DDA-minus-last-click delta per campaign is the "credit moved" number; brand and retargeting lose, generic and upper-funnel gain. This is reporting, not evidence (see step 5).
   d. **Modelling and consent.** The residual between Google Ads (by conv. time, Original value, last click) and GA4/CRM on the same definition is modelled conversions and matching differences; Google fills consent/identifier gaps with models validated by holdback experiments and treats them as a normal component (Vallaeys/SEL, 2026). Expect this residual to persist; document it as a percentage and track it monthly rather than trying to eliminate it.
   e. **Import window.** For offline/CRM conversions, any sale closing more than 90 days after the click never enters Google Ads via GCLID (Vallaeys & Newson/Optmyzr, 2026). Quantify the share of CRM revenue beyond 90 days; that share is structurally invisible to the platform.
3. **Build the client number.** Client-facing report = Google Ads conversions by conversion time, Original conv. value, DDA, with the modelled-residual % and the >90-day share stated. The CRM number sits next to it, not reconciled to it: "systems will disagree … they answer different questions with different data" (Vallaeys/SEL, 2026).
4. **Give upper-funnel credit without over-claiming.** Where step 2c moves ≥20% of a campaign's conversions between models, the campaign is doing assist work; keep it off the cut list on last-click grounds. But a DDA share is still a redistribution of observed clicks; if the client needs to know whether cutting it loses sales, run 80.
5. **Fix the feed, not the model.** Long-cycle accounts: send a scored early proxy (engagement- or qualification-based) within ~2 weeks rather than waiting for the sale; "if you can get within two weeks something to give back to Google, it starts to steer the ship" (Vallaeys & Newson/Optmyzr, 2026). Import calls, CRM stages and offline revenue; conversions that live only in GA/Adobe/CRM cannot drive decisions in Google Ads (Geddes/Adalysis, 2021). Use redundant signals — pixel plus offline import plus enhanced identifiers — because "multiple incomplete signals" beat one supposedly complete one (Vallaeys/SEL, 2026).
6. **Re-check after any change.** Imported or modelled conversions appear in reporting before they influence bidding; the bidder validates new signals over time (Vallaeys/SEL, 2026). Do not judge a bidding change against a conversion feed that is less than ~4 weeks old.

## What Google will tell you instead, and why we don't
- Google's UI presents Conv. value and ROAS as the headline; with the new-customer checkbox on they are deliberately inflated for bidding (Williams/ZATO, 2026). We report Original conv. value to clients and keep the inflated column for the bidder only.
- Google's default columns are by click date. Every "why is last month different now" conversation is this; we report by conversion time (Stemen/SEJ, 2026) and explain the lag once, in writing.
- Google's model comparison invites "pick the model that makes the account look best". We fix the model (DDA) and the window across actions (Geddes/Adalysis, 2021) and use the comparison only to size assist credit, never to justify a budget.
- Google's DDA recommendation of 200 conversions and 2,000 interactions in 30 days is a precision note, not a gate [Google docs]; the older "300 conversions or fall back to last click" rule (the pre-canon baseline skill, google-ads-attribution) is out of date — DDA now runs regardless of volume [Google docs]. We leave DDA on in small accounts and widen the residual tolerance instead.

## Failure modes
- **Small accounts (<200 conv/30 days).** DDA credits imprecisely [Google docs]; per-campaign model deltas swing month to month. Report at account level only.
- **Long-cycle B2B / wealth / enterprise.** The >90-day share can exceed half of revenue (Vallaeys & Newson's example is a 24-month cycle; Vallaeys & Newson/Optmyzr, 2026). The platform number cannot reconcile and should not be forced; use the proxy feed in step 5.
- **Consent-heavy EU markets.** The modelled residual is large and legitimate (Vallaeys/SEL, 2026); a client demanding a zero residual is asking for a number that does not exist.
- **Accounts with value rules or new-customer bidding on.** Any ROAS quoted from Conv. value is wrong for finance (Williams/ZATO, 2026).
- **Mixed GA4-import and tag conversions as primaries.** Double counting and mixed models in one bidding signal (Geddes/Adalysis, 2021); normalise first.
- **Lead-gen with LLM-sourced leads.** A growing share of leads arrives with no Google path at all (65% in one Newson client; Vallaeys & Newson/Optmyzr, 2026); the attribution delta then says nothing about Google Ads performance.

## What to measure
Monthly: Google Ads conversions by click date vs by conversion time (lag share), Conv. value vs Original conv. value (adjustment share) (Williams/ZATO, 2026), DDA vs last click per campaign (assist share), Google Ads vs GA4/CRM residual %, and the share of CRM revenue closing >90 days after click (Vallaeys & Newson/Optmyzr, 2026). Alert if the residual moves >10 points in a month — that is usually a tag, consent or import break, not attribution.

## Open disagreements in the canon
- **One number or several.** Geddes: one model, one window, so bidding and reporting are consistent (Geddes/Adalysis, 2021). Vallaeys: platform and CRM will disagree by design; hold both and explain (Vallaeys/SEL, 2026). Epiminds: Geddes' rule inside Google Ads (it is about bidding integrity), Vallaeys' rule at the client interface (it is about reporting honesty). The two do not conflict once scoped.
- **Whether a model comparison is worth running at all.** Geddes (2017/2018) treats model choice as answering a question; the baseline treats it as a pre-switch check. Epiminds runs it only to size assist credit for campaigns facing a last-click cut, because DDA is the default and the canon offers no evidence that any alternative model bids better.
