---
name: micro-conversion-ladder
id: 43
description: Use when a new or small account has too few macro conversions (under ~30 a month) for Smart Bidding to learn and you need a signal to bid to in the meantime. Not for accounts already above ~50 conversions a month, and not a licence to make engagement events primary conversions.
tags: Strategy / All / Setup / New / One-off
last_verified: 2026-10-13
invalidated_by: Google removing the primary/secondary conversion distinction, changing the Smart Bidding data floors, or retiring Maximize Clicks.
---
## What this is
A ladder of conversion actions, from shallow (form fill) to deep (closed deal), where exactly one rung is primary at a time and you move the primary rung deeper as volume allows (Gray/WebMechanix, 2024). It exists because Smart Bidding is unpredictable below 50 conversions in 30 days and moving from under 25 to 25–50 does not reliably help (Hopkins/Optmyzr, 2024), so a new account has to earn its way to macro-conversion bidding. The trap is bidding to any action that has volume: in Gray's accounts, optimising to engagement micro-conversions raised engagement and produced "no corresponding increase in downstream conversion actions" (Gray/WebMechanix, 2024).
See also: skill 42 (value-based-bidding-lead-gen) — valuing the rungs and switching to value-based bidding once the ladder has volume.
See also: skill 48 (offline-conversion-import-lead-stages) — importing CRM lead stages as the deeper rungs, with the 45-in-30-days-inside-the-window rule.

## Where it comes from
Hopkins' 14,584-account study (2024) sets the volume thresholds and shows Max Clicks is the efficient low-volume strategy. Vallaeys (2026) gives the 30–50 practitioner floor and the no-stacking rule. Gray/WebMechanix (2024, added Tier 2) gives the ladder, the ~45/30-day graduation rule and the negative result. Mullarky (2021, added Tier 2) gives rung valuation by ratio. Stemen/SEL (2024) and Newson/Vallaeys (2026) carry the pro-micro-signal case.

## When to use it / when not to
Use when the deepest action you can measure gets fewer than ~30 conversions a month at the level the bid strategy sits (Vallaeys/Optmyzr, 2026), the account is new or recently restructured, and the client can tell you which earlier actions precede a sale and at what rate. Don't use when the macro action already clears ~50/month — go straight to it (Hopkins/Optmyzr, 2024). Don't use to "rescue" a mature account that lost volume; that is a target or structure problem. Don't use time-on-site or page-depth events unless the client's own data shows the rate at which they precede a sale.

## Inputs
- Every measurable action from first touch to sale, with monthly volume and median time-to-complete
- For each earlier action: the share that goes on to the macro action (from CRM or analytics; a sales-team estimate is acceptable for a first pass)
- Monthly budget and expected clicks
- Current bid strategy and which actions are primary

## Method
1. **Draw the ladder.** Order actions by depth: form fill → qualified form fill → MQL → SQL → closed (Gray/WebMechanix, 2024); for ecommerce: add-to-cart → begin checkout → purchase. Record monthly volume and time-to-complete per rung.
2. **Qualify each rung.** A rung qualifies as a bidding signal only if the client's data gives its rate of leading to the macro action. Gray's engagement events failed because they had volume but no known path-to-sale (Gray/WebMechanix, 2024). Newson's six-minute visit worked because it was picked as an intent marker on his own evidence (Newson/Vallaeys, 2026). Geddes recommends a "quality visit" event for campaigns under 10 conversions/month (Geddes/Adalysis, 2025) — acceptable only under the same condition. No rate, no rung.
3. **Pick the primary rung**: the deepest qualifying rung with ≥45 conversions in the last 30 days at the bid-strategy level (Gray/WebMechanix, 2024) and a time-to-complete well inside the 90-day click window (Gray/WebMechanix, 2024). Every other rung is secondary — never stack primaries, or one journey counts three times and values add up (Gray/WebMechanix, 2024; Vallaeys/Optmyzr, 2026).
4. **If no rung clears 45**: do not bid to conversions at all yet. Run Maximize Clicks with a bid cap — the most efficient automated strategy in Hopkins' data, and the one most low-budget accounts actually use — and spend the time on landing page conversion rate (Hopkins/Optmyzr, 2024). Manual CPC is the worse option: it only pays off in actively managed, high-volume accounts (Hopkins/Optmyzr, 2024).
5. **Value the rungs** so that when you move to Max Conversion Value the ratios are already right: rung value = macro value ÷ (1 ÷ rung-to-macro rate); a 20% rate on a $150 macro gives $30 (Mullarky/Metric Theory, 2021). Only the ratios matter.
6. **Bid strategy by stage**: Max Clicks (no qualifying rung) → Max Conversions or Max Conversion Value with *no target* on the primary rung (Vallaeys/Optmyzr, 2026; Hopkins/Optmyzr, 2024 found no-target beat targeted) → add a target only once the primary rung clears ~50/30 days.
7. **Graduate.** Each month, check the next-deeper rung: when it clears 45 in 30 days, make it primary and demote the current one to secondary. If it arrives by CRM import, confirm the median time-to-complete is under ~60 days first — beyond that the bidder reads early days as failures (Gray/WebMechanix, 2024; see skill 49). Vallaeys argues a signal returned within ~2 weeks steers bidding and one returned at 90 days barely does (Vallaeys/Optmyzr, 2026).
8. **Consolidate before you climb.** If campaigns are fragmented, the deep rung will never clear 45 per campaign — "insufficient signal" (Vallaeys/Optmyzr, 2026). Merge first, then graduate.

## What Google will tell you instead, and why we don't
Google's Recommendations push "add conversion actions" and "switch to Maximize Conversions" on low-volume accounts, and its tCPA floor is 15 conversions in 30 days (Google Ads Help via Vallaeys/Optmyzr, 2026). We don't: 15 is eligibility, not reliability — 30–50 is the practitioner floor and 50 is where the cross-account data turns predictable (Vallaeys/Optmyzr, 2026; Hopkins/Optmyzr, 2024). And "more conversion actions" as primaries is exactly the stacking that inflates counts and, in Gray's accounts, bought engagement instead of sales (Gray/WebMechanix, 2024). Where we also depart from the usual advice: Manual CPC is not the safe start; Max Clicks is (Hopkins/Optmyzr, 2024).

## Failure modes
- **Engagement events as rungs** (scroll, time on site, video view) without a known path-to-sale rate: more of the event, no more sales (Gray/WebMechanix, 2024).
- **Sub-$1.5K/month accounts**: below Hopkins' study floor; no evidence any automated strategy behaves (Hopkins/Optmyzr, 2024).
- **Long B2B cycles** where the only qualifying rung takes >60–90 days: it is outside or at the edge of the click window; stay on the shallower rung and import the deep one as secondary for reporting (Gray/WebMechanix, 2024).
- **Lead-quality clients**: a form-fill primary will buy junk forms; add a qualified-form rung (phone validation, company email) before leaving Max Clicks.
- **Ecommerce with uniform cart-to-purchase rates**: add-to-cart as primary just moves the conversion count; use it only until purchases clear 45/month.
- **Tiny addressable markets** (a few hundred named accounts): volume will never arrive; manual control beats any ladder (Cruz/SEL, 2026).

## What to measure
Per rung, monthly: volume, rung-to-next-rung rate, median time-to-complete. Macro CPA alongside primary-rung CPA — if primary-rung CPA falls and macro CPA doesn't within one to two full conversion cycles — Vallaeys' wait-before-judging window (Vallaeys/Optmyzr, 2026) — the rung is a correlate, not a cause (Gray's failure signature — Gray/WebMechanix, 2024). Max Clicks phase: CPC, landing-page CVR. Graduation check monthly.

## Open disagreements in the canon
- **Do micro-conversions work as bidding signals at all?** Gray says no in his accounts (2024); Stemen/McNair (2024), Geddes (2025) and Newson (2026) say yes when well-chosen. Epiminds goes with the qualification rule: a rung needs a known path-to-sale rate; otherwise Max Clicks.
- **Manual CPC vs Max Clicks at low volume.** Most how-to content (and the baseline) says Manual; Hopkins' data says Manual pays only with volume and active management. We go Max Clicks with a cap.
- **Threshold**: 45 (Gray) vs 50 (Hopkins) vs 30–50 (Vallaeys). We use 45 to graduate a rung and 50 to add a target.
