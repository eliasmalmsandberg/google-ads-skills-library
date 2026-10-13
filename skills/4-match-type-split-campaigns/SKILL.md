---
name: match-type-split-campaigns
id: 4
description: Decide whether exact, phrase and broad should live in separate campaigns, and if so wire the cross-negatives and budgets so phrase/broad cannot take exact's queries. For established Search accounts. Not the alpha/beta harvesting flow (skill 1) and not ad-group design (skill 3).
tags: Structure / Search / Setup / Established / One-off
last_verified: 2026-10-13
invalidated_by: Removal of match types (AI Max replacing keywords); budgets/targets becoming settable at ad-group level; Google giving exact strict cross-campaign priority.
---
## What this is
A gate, then a wiring diagram. The gate: match types get their own campaigns only when you need a different budget or a different bid method per match type (Geddes/Adalysis, 2020); any other reason is a reason to keep them in one ad group. The wiring: the exact campaign takes the maximum budget, the phrase campaign carries the exact keywords as exact negatives, broad carries both exact and phrase keywords as negatives and is the budget lever you throttle to hit targets (Geddes, 2020).
See also: skill 1 (alpha-beta-structure) — the harvesting flow that moves converting beta terms into the exact tier.
See also: skill 13 (keyword-funnelling-tiered-negatives) — Hopkins's case against three parallel match-type campaigns and the two-tier alternative.

## Where it comes from
Geddes's campaign-level match-type approach and his observation of cross-campaign rotation (Adalysis, 2020); the Optmyzr 2,637-account study that exact still outperforms broad on CPA/ROAS in most accounts (Hopkins, 2023); Vallaeys/Walker's split rule and 30-conversion floor (Optmyzr Town Hall, 2025); Bacchini/Lolk on what close variants did to phrase (Optmyzr Town Hall, 2025).

## When to use it / when not to
Use when: you need exact-intent traffic to never be budget-capped while broad is capped (Geddes, 2020); exact and broad need different bid methods (e.g. exact on tROAS with limits, broad on Max Clicks with a CPC cap while it accrues data; Rooijmans, 2026 — see skill 1); the search-terms report shows phrase/broad serving queries you hold as exact, which under rotation happens even when the exact keyword exists (Geddes, 2020); each resulting campaign will still clear ~30 conversions/30 days (Vallaeys/Walker, 2025).

Do not use when: the split campaigns would carry the same target — Lolk sees near-identical targets (700/725/715) in ~80% of split accounts he reviews, which makes the split a cost with no return (Lolk, 2025, not canon); total volume is under ~60 conversions/30 days so two campaigns cannot both reach 30; the only motive is keyword-level bids, which Geddes explicitly excludes as a reason (Geddes, 2020); you expect phrase to behave like old BMM — it matches loosely now (Groeneveld/Emerce, 2022; Lolk, 2025).

## Inputs
- Keyword list by match type with 90-day cost, conversions, CPA/ROAS.
- Search terms by campaign, 90 days, flagged where the serving keyword's match type is looser than a keyword you hold for the same query.
- Per-campaign conversions/30 days and current targets and budgets.
- Budget-limited status per campaign.

## Method
1. **Gate.** Write down the budget or bid-method reason for each proposed match-type campaign. No reason → merge match types into the ad group and stop (Geddes, 2020). Same target across the proposed campaigns → merge (Lolk, 2025, not canon).
2. **Volume check.** Projected conversions/30 days per campaign ≥30 (Vallaeys/Walker, 2025). Below that, use a portfolio strategy across the match-type campaigns so the bidder pools data while budgets stay separate (Bacchini, 2025, portfolio pooling for low volume).
3. **Exact campaign.** Holds exact keywords. Maximum or uncapped budget (Geddes, 2020). This is the tier that wins on CPA/ROAS in ~71–73% of accounts (Hopkins/Optmyzr, 2023), so it must not be the one that runs out.
4. **Phrase campaign.** Holds phrase keywords with every exact keyword from step 3 added as an exact negative (Geddes, 2020). Expect it to still catch exact-like queries via close variants; those are a signal to add the query as exact in step 3, not a bug to fight.
5. **Broad campaign.** Holds broad keywords with the exact and phrase keywords added as negatives (exact negatives for the exact set; phrase negatives for the phrase set). Budget is the lever: raise it when the account is under target, cut it when over (Geddes, 2020). Expect no CPC discount for broad (Hopkins/Optmyzr, 2023).
6. **Negatives are mandatory, not optional.** Across campaigns Google tries the most restrictive match but rotates over time, which is why the same search term shows up under two campaigns (Geddes, 2020). Without the cross-negatives the split does nothing.
7. **Keep the originals.** When adding broad or phrase variants, add them alongside the existing keywords; do not pause what works, because a removed keyword's history does not come back (Hopkins/Optmyzr, 2023).
8. **Budget for the loosening.** Set broad/phrase caps before launch; the one broad-match case in the Springbok series ran +46% cost (with +49% conversions) (Groeneveld/Emerce, 2022).
9. **Output**: the gate decision with its stated reason; the three campaigns' keyword sets; the two negative lists (exact-set, phrase-set) and where they are attached; budget caps; a 30-day review date to check step 2 held.

## What Google will tell you instead, and why we don't
- Google: combine all match types in one ad group, then simplify to broad; duplicating a keyword across match types fragments Smart Bidding data (Google Ads Help, answer 14752782). We accept the fragmentation only when a budget or bid-method reason exists (Geddes, 2020), because exact outperformed broad on CPA/ROAS in most of 2,637 accounts (Hopkins/Optmyzr, 2023) and a budget cap on exact is a direct loss of the best traffic.
- Google's UI implies the exact keyword wins the query when present. In practice rotation across campaigns produces duplicates (Geddes, 2020); hence the negatives.
- Google sells broad as cheaper reach; the CPC discount is gone (Hopkins/Optmyzr, 2023).

## Failure modes
- **Low-volume lead gen**: three campaigns under 30 conversions each become unstable (Vallaeys/Walker, 2025); pool or merge.
- **Identical targets** across the split (Lolk, 2025): maintenance cost, no gain.
- **Phrase-as-control accounts**: phrase matches loosely; a phrase campaign built to "control" queries will leak (Groeneveld, 2022; Lolk, 2025).
- **Negative drift**: new exact keywords added without mirroring into phrase/broad negatives reopen the overlap; the rotation behaviour means it shows up within weeks (Geddes, 2020).
- **Negative-averse accounts**: if broad's queries convert fine at their CPC, Vallaeys's "only a bad bid" (2025) applies — do not route them away for neatness; promote or leave.
- **Retail with seasonal swings**: broad budget as a lever can overshoot in peak; use step 8 caps.

## What to measure
- Duplicate search terms across the three campaigns (target zero; Geddes, 2020).
- CPA/ROAS by match-type campaign vs the Optmyzr pattern (exact ahead on CPA/ROAS; broad ahead on impressions; Hopkins/Optmyzr, 2023).
- Budget-limited flags on the exact campaign (any flag is a failure of step 3).
- Conversions/30 days per campaign vs the 30 floor (Vallaeys/Walker, 2025).
- Target spread across the campaigns — if they converge, merge (Lolk, 2025).

## Open disagreements in the canon
- **Budget as a valid reason to fragment data.** Google says no; Geddes (2020) and Vallaeys/Walker (2025) say budget is one of the few valid campaign-split reasons. Epiminds goes with the practitioners.
- **Phrase's role.** The canon has no phrase-specific evidence (Optmyzr tested only broad vs exact). Epiminds keeps phrase as an optional middle tier and treats it as loose.
- **Negatives vs bids.** Vallaeys/Lolk (2025) vs Geddes (2020). Epiminds uses negatives because the split's whole purpose is budget separation, which bids cannot enforce.
