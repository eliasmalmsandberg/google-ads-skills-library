---
name: value-based-bidding-lead-gen
id: 42
description: Use when a lead-gen account on tCPA produces leads of visibly different worth and you want the bidder to chase the good ones — building a proxy value ladder and moving to Max Conversion Value / tROAS. Not for accounts under ~30 conversions a month, not for single-stage funnels where every lead is worth the same, and not a replacement for offline conversion import (skill 48) when the CRM can supply real stage data.
tags: Strategy / All / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: Google changing conversion value rules, removing Max Conversion Value without a target, changing tROAS eligibility floors, or the Data Manager API changing offline value upload.
---
## What this is
tCPA treats a tyre-kicker and an enterprise demo as the same $1 of success. Value-based bidding lets you tell the bidder they are not — but only if you give it values, and lead gen rarely has real ones at click time. The method is to construct *proxy* values from stage-to-close ratios so that the ratio between conversion actions is right, even if the absolute dollars are invented (Mullarky/Metric Theory, 2021; Vallaeys/Optmyzr, 2026). In Hopkins' 14,584-account study, Max Conversion Value was the most used lead-gen strategy and beat Max Conversions by almost 300% on ROAS (Hopkins/Optmyzr, 2024) — with the caveat that ROAS on proxy values partly measures the proxy itself.

## Where it comes from
Vallaeys (2026) gives the value formula and the no-stacking rule; Mullarky (2021, added Tier 2) gives the ratio-only principle, the placebo-ROAS target maths and a YoY account test; Fleagle/WebMechanix (2022, added Tier 2) a nine-month account result; Hopkins (2024) the cross-account data on targets and thresholds; Stemen/SEL (2024) records McNair's view that VBB is the first test to run, and De Boeck's objection.

## When to use it / when not to
Use when: leads differ in close rate or deal size by at least ~2× between identifiable groups (stage, form type, segment) — the 2× is Vallaeys' own example of a group closing at 20% vs one at 10% (Vallaeys/Optmyzr, 2026) — the account has 30–50+ conversions a month across the actions you'll value (Vallaeys/Optmyzr, 2026; Hopkins/Optmyzr, 2024), and the client can tell you stage-to-close rates even roughly. Don't use when every lead is worth about the same (tCPA is already right), when volume is under ~30/month (use Max Conversion Value with no target to build history, or stay on tCPA), or when the CRM can supply actual stage outcomes — then import those instead (skill 48) and use this skill only to value the *early* actions.

## Inputs
- Conversion actions in the account and which are primary/secondary
- For each action: stage-to-close rate and average closed value (sales/finance estimate is fine)
- Last 30–90 days: conversions per action, spend, current tCPA and actual CPA
- Segment splits the client cares about (SMB vs enterprise, geo, device)
- Whether offline import exists and its latency

## Method
1. **Anchor the ladder at the close.** Value of the final action = close rate × average deal size, e.g. 10% × $5,000 = $500 (Vallaeys/Optmyzr, 2026). If the client refuses a dollar figure, anchor at estimated LTV and work backwards — absolute scale doesn't matter, the ratios do (Mullarky/Metric Theory, 2021).
2. **Value each earlier action by its path-to-close.** Action value = anchor ÷ (1 ÷ stage-to-close rate): a quiz completed by 20% of eventual subscribers at $150 LTV is $150 ÷ 5 = $30 (Mullarky/Metric Theory, 2021). A lead group closing at 20% is worth ~2× one closing at 10% (Vallaeys/Optmyzr, 2026). Keep it to 3–5 rungs — Epiminds operating threshold, no canon source; reason: each rung needs its own measured close rate, and lead-gen CRMs rarely maintain more than five stages reliably.
3. **No stacking.** If a single journey fires lead → MQL → SQL and all three are primary, Google counts $10 + $20 + $50 = $80 for one sale. Make only one rung per journey primary and demote the others to secondary, or value the later rung as the *increment* over the earlier one (Vallaeys/Optmyzr, 2026).
4. **Differentiate within a rung by segment** using conversion value rules (geo, audience, device — rules are additive, so check overlaps) rather than by splitting campaigns (Marvin/Google, 2024; skill 41).
5. **Switch to Max Conversion Value with no target** and hold 4 weeks or three conversion cycles, whichever is longer (Vallaeys/Optmyzr, 2026). Hopkins found advertisers on Max Conversion Value *without* a target did better on most metrics than those with one (Hopkins/Optmyzr, 2024), so the target comes last, not first.
6. **Set the tROAS from observed data**: target = last-30-day conversion value ÷ spend (Vallaeys/Optmyzr, 2026). That is the "placebo ROAS" — e.g. $870 value ÷ $300 cost = 290%, which maps to a $100 blended CPA (Mullarky/Metric Theory, 2021). Keep placebo ROAS above 100%; tROAS behaves worse when proxy revenue is below spend (Mullarky/Metric Theory, 2021). Move the target toward the CPA the client actually needs in steps once stable.
7. **Lock the values and the target together.** Any change to a rung value changes reported ROAS instantly; update the target the same day (Mullarky/Metric Theory, 2021). Document each change — conversion lag will otherwise make the change date look like a performance cliff (Vallaeys/Optmyzr, 2026).
8. **Test it, don't assume it.** Run tCPA vs tROAS as a campaign Experiment — McNair's top-ranked test (Stemen/SEL, 2024). Experiments need roughly 2× the conversion volume and 4–8 weeks runtime (Vallaeys/Optmyzr, 2026). Mullarky's YoY test: tROAS CPA −10% and conversions +51% vs tCPA CPA +22% and conversions −11% at the same +37% spend (Metric Theory, 2021); Fleagle's: CPL −54% over nine months (WebMechanix, 2022). Both single-account, uncontrolled — expect smaller.

## What Google will tell you instead, and why we don't
Google says tROAS is eligible at 15 conversions in 30 days and quotes ~14% more conversion value for tCPA→tROAS switchers (Marvin/Google, 2024). We treat 15 as an eligibility floor, not a reliability threshold — 30–50 is the practitioner bar, and 25–50 did not reliably beat <25 in cross-account data (Vallaeys/Optmyzr, 2026; Hopkins/Optmyzr, 2024). The 14% measures conversion value the advertiser defined, not lead quality or revenue, from undisclosed 2021 data (Marvin/Google, 2024, as read by SEJ). And Google's instinct is to set a target at launch; the evidence says start without one (Hopkins/Optmyzr, 2024).

## Failure modes
- **Uniform leads** (one form, one product, one segment): the ladder has one rung; you've rebuilt tCPA with extra steps.
- **Under 30 conversions/month across valued actions**: the bidder learns noise; Smart Bidding is unpredictable below 50 (Hopkins/Optmyzr, 2024).
- **Wrong ratios**: value strategies are biased toward whatever you weighted (De Boeck via Stemen/SEL, 2024). If sales guessed the demo-to-close rate at 30% and it is 8%, you will buy demos at 4× their worth. Re-check ratios against CRM every quarter — Epiminds operating cadence, no canon source; reason: Vallaeys names stale CRM values as a common breakage but gives no interval (Vallaeys/Optmyzr, 2026), and a quarter is the shortest period over which a B2B close rate can be re-measured.
- **Stacked primaries** inflate value 2–3× per journey and the tROAS target becomes meaningless (Vallaeys/Optmyzr, 2026).
- **Long sales cycles with values arriving by offline import**: lag misattributes and the bidder reads early days as failures (Vallaeys/Optmyzr, 2026); use skill 49 before judging.
- **Fragmented campaigns**: late-stage rungs end up with too little volume per campaign — "insufficient signal" (Vallaeys/Optmyzr, 2026). Consolidate first.
- **Client who reads ROAS literally**: proxy ROAS is not money. Report CPA by rung alongside it or the client will ask why 290% ROAS isn't in the bank.

## What to measure
Per rung: conversions, cost per rung, share of total value. Blended: value ÷ spend vs target, matured (excluding the lag window). Lead-quality truth: CRM close rate and deal size of leads generated after the switch vs before, at 60–90 days. Experiment read-out at ≥4 weeks and ≥3 conversion cycles (Vallaeys/Optmyzr, 2026). Quarterly (Epiminds cadence, see Failure modes): re-derive rung ratios from the CRM.

## Open disagreements in the canon
- **Target at launch or later.** Google and most how-to content set a tROAS immediately; Hopkins' data says no-target Max Conversion Value did better (2024). Epiminds: no target for the first four weeks, then set from observed value/spend.
- **Is proxy-value ROAS evidence?** Mullarky and Fleagle report ROAS/CPL wins on proxy values; De Boeck says you're measuring your own weights. We use the proxy ROAS to steer and the CRM close rate to judge.
- **Real values vs proxies.** Google and Vallaeys prefer real revenue; Mullarky shows placebo values work when only ratios matter. We use proxies at the top of the funnel and real imported values at the bottom (skill 48), never proxies where real data exists.
