---
name: conversion-value-rules
id: 41
description: Use when a tROAS or Max Conversion Value account needs the bidder to value conversions from one geo, device or audience differently — because their real worth differs — without splitting campaigns. Not for replicating old geo/device bid adjustments, not for tCPA/Max Conversions accounts (rules don't affect their bidding), and not a substitute for importing real values.
tags: Technique / All / Optimise / Established / One-off
last_verified: 2026-10-13
invalidated_by: Google changing the multiplier range (0.5–10×), the two-dimension limit, the one-rule-per-conversion precedence, or extending rules to non-value bid strategies.
---
## What this is
A value rule multiplies or adds to the conversion value Google records when a conversion matches a geo, device or audience condition. Under tROAS, bid is proportional to predicted value, so a 2× rule is effectively a 2× bid adjustment — $5 becomes $10 at a 200% target (Vallaeys/Optmyzr, 2021). That makes it the only "bid adjustment" that still works under Smart Bidding, and also the main way it gets misused: encoding a conversion-rate difference Google already learned from your tracking stacks the adjustment and bids wrong (Vallaeys/Optmyzr, 2021). The practitioners who've written on it agree the benefit is limited and the qualifying test is simple — the rule must carry information Google doesn't have (Vallaeys/Optmyzr, 2021; Vlietstra/ZATO, 2026).
See also: skill 42 (value-based-bidding-lead-gen) — building the proxy value ladder for lead gen and moving to Max Conversion Value / tROAS.

## Where it comes from
Vallaeys (2021) is the mechanism and the stacking warning; Vlietstra/ZATO (2026) the current-UI method, the demotion use and the reporting columns; Google API docs (2026) the precedence and limits. No one in the canon has published account results for value rules — this skill is a method, not a study.

## When to use it / when not to
Use when: the bid strategy is tROAS or Max Conversion Value (rules don't touch tCPA/Max Conversions bidding — Vallaeys/Optmyzr, 2021); you can name an *off-platform* reason a segment's conversions are worth more or less — margin, deal size, LTV, store sales (Vallaeys/Optmyzr, 2021; Balakrishnan/Optmyzr, 2022); and splitting the campaign would starve one side of volume. Don't use when the only argument is "this device/region converts better" — Google already prices that (Vallaeys/Optmyzr, 2021). Don't use when the client's reporting can't absorb changed conversion values (see Method 6).

## Inputs
- Bid strategy per campaign (value-based or not)
- Per candidate segment (geo / device / audience): conversion count last 90 days, and the off-platform value evidence (CRM deal size, margin by region, LTV by list)
- Existing audiences in the account (Customer Match, remarketing) and whether existing customers are excluded
- Who consumes reported conversion value, and whether they've agreed to adjusted values

## Method
1. **Qualify the segment.** Write the one-line reason the segment's conversions are worth X× the average. If the reason is a conversion-rate or CPA difference, stop — that's already in the bidder (Vallaeys/Optmyzr, 2021). If the reason is deal size, margin, LTV or offline close rate, continue.
2. **Compute the multiplier from value, not from performance.** Multiplier = segment average value ÷ account average value, clamped to Google's 0.5–10× range (Google API docs, 2026; Vallaeys/Optmyzr, 2021). Don't round up for "aggression": at 200% tROAS a 2× rule already doubles the bid (Vallaeys/Optmyzr, 2021).
3. **Prefer demotion rules.** The lowest-risk rule is a <1× multiplier on an audience you overvalue by default — existing customers or a remarketing list whose conversions would have happened anyway (Vlietstra/ZATO, 2026). Pair with the new-customer value setting rather than duplicating it.
4. **Respect the structure limits.** A rule takes one condition or two combined (both must hold); a rule set holds at most two dimensions; at most one rule applies per conversion — campaign-level beats account-level, most precise geo wins, audiences follow the Customer Match → remarketing → interest → demographic order, ties go multiply > add > larger (Google API docs, 2026; Vallaeys/Optmyzr, 2021). So: one set, few rules, no overlapping geos.
5. **Minimum volume**: ≥50 conversions in 30 days in the segment before you trust the rule did anything — below that Smart Bidding is unpredictable on any signal (Hopkins/Optmyzr, 2024). And confirm the strategy: rules do nothing on Max Conversions or tCPA (McNair/PPC Mastery, 2026).
6. **Agree the reporting change first.** Adjusted values flow into every conversion-value metric and are not restated backwards (Google API docs, 2026; Vallaeys/Optmyzr, 2021). Tell the client, then report with "Original conv. value (rule applied)" vs "(no rule applied)" columns or the "Value rule adjustment" segment (Vlietstra/ZATO, 2026).
7. **Read it after 2–3 weeks** — Hopkins' settle window for Smart Bidding changes (Hopkins/Optmyzr, 2024) — on share of conversions with a rule applied, segment share of spend, and matured ROAS computed on *original* values. If spend shifted toward the segment and original-value ROAS held or improved, keep it. If original-value ROAS fell, the rule encoded a conversion-rate guess, not a value difference — remove it.
8. **Review quarterly** and re-derive multipliers from the CRM (Marvin/Google, 2024, is right on this point; the values drift).

## What Google will tell you instead, and why we don't
Google's lead-gen guidance is to "start with a few basic rules on the most critical attributes" — location, audience, device — and treats rules as the first lever for lead gen VBB (Marvin/Google, 2024). We treat them as the last: a rule only helps when it says something Google doesn't already know, and most geo/device differences it does (Vallaeys/Optmyzr, 2021; Vlietstra/ZATO, 2026). Google's help copy also says overlapping rules are "additive" (Marvin/Google, 2024); the API documentation says at most one rule applies per conversion with a precedence order (Google API docs, 2026). We build to the API doc.

## Failure modes
- **tCPA / Max Conversions accounts**: the rule changes reported value and nothing else (Vallaeys/Optmyzr, 2021).
- **Migrated manual-CPC accounts** that port old +30% mobile / −20% region adjustments as rules: double-counted, bids skew, ROAS on original values falls (Vallaeys/Optmyzr, 2021).
- **Overlapping geos** (country rule + city rule): only the most precise applies; the country rule silently does nothing in that city (Google API docs, 2026).
- **Stakeholder dashboards built on conversion value**: numbers change on the day the rule starts, with no restatement (Vallaeys/Optmyzr, 2021).
- **Low-volume segments** (<50 conv/30 days): no readable effect, but reported value still moves.
- **Clients who want "more bids in London"**: a value rule is not a reach lever; if London isn't worth more per conversion, use budget and targeting.

## What to measure
Share of conversions with rule applied; segment share of spend before/after; matured ROAS on original values (rule applied vs not); CPA by segment. Quarterly: multiplier vs current CRM value ratio.

## Open disagreements in the canon
- **Bid adjustment or value correction?** Google frames rules for ex-manual bidders; Vallaeys and Vlietstra frame them as value corrections with limited benefit. Epiminds: value corrections only; refuse rules justified by conversion rate.
- **Additive vs one-rule precedence.** Google Help (Marvin 2024) vs Google API docs (2026) and McNair (2026), who both say one rule per conversion. We follow the API docs and design rule sets with no overlaps so the question never matters.
- **Evidence gap.** No practitioner has published results; we run every rule as a before/after on original-value ROAS and treat the method as provisional.
