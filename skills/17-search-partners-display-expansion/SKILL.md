---
name: search-partners-display-expansion
id: 17
description: Per-campaign decision on the two network defaults Google switches on for Search campaigns — search partners and Display Expansion — with the thresholds for excluding partners. Use at campaign creation and when auditing an inherited account. Not a placement audit (Google gives no per-partner report) and not a Display campaign guide.
tags: Setting / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google adding per-partner reporting or exclusions; removal of the campaign-level partner toggle; another change to the partner auction like the November 2021 position-first move; Google documenting Display Expansion behaviour differently from the assumption stated below.
---
## What this is
Two settings, two different answers. Search partners are decided per campaign, on cost per conversion or ROAS against the campaign's goal, and never on CTR or conversion rate — lower CTR and CVR on partners is normal and is not a reason to exclude them (Geddes/Adalysis, 2023). The spread is wide enough to justify the work: in one account partner CPA was $185 against $11 on Google Search; in another, partner CPA was lower than Google's; under Smart Bidding some campaigns ran partner CPA at 17× Google Search while others were fine (Geddes/Adalysis, 2023). Display Expansion for Search campaigns has one controlled test (Seer Interactive, 2021, Tier 2 for this topic — see skill 88); the Epiminds default is off, for the reasons given in the method.
See also: skill 88 (standard-off-list) — the four-default off-list including Final URL expansion and auto-apply, and Seer Interactive's Display Expansion test.

## Where it comes from
Brad Geddes' evaluation method and account numbers (Adalysis, 2023); Nils Rooijmans' Search Partner Alerts script with its thresholds (2019, maintained 2025) and his note on the November 2021 partner auction change (2022); Vallaeys' Smart Bidding data threshold (Optmyzr, 2026) for the minimum data under automated bidding.

## When to use it / when not to
Use at every Search campaign build and in every inherited-account audit, then monthly via the alert script. Do not decide at account level — Google only allows the toggle per campaign and performance differs per campaign (Geddes/Adalysis, 2023). Do not act on a single month of partner data in a low-volume campaign; the thresholds below need 50 partner clicks (Rooijmans, 2019).

## Inputs
- Campaign performance segmented by network (Google Search vs search partners), last 365 days by default, with 30/60/90-day views (Rooijmans, 2019).
- Campaign CPA/ROAS target; impression share lost to budget.
- Bid strategy per campaign and its 30-day conversion count.
- Date of campaign creation (for the Nov 2021 auction change check on older campaigns).

## Method
1. **Default at creation.**
   - Established accounts with budget headroom: leave search partners on and measure (Geddes/Adalysis, 2023: do not block by default).
   - New campaigns, small budgets, or campaigns already losing impression share to budget: switch partners off at creation — the one exception Geddes allows (Adalysis, 2023). Turn on later as a test when budget is unconstrained.
   - Display Expansion: off. The one controlled test in the canon is Seer Interactive's (2021, Tier 2 for this topic; skill 88): on under-budget tCPA campaigns cost roughly doubled with CPL +51% (US) and +184% with conversions −33% (UK). The Epiminds reason stands alongside it: the campaign's keywords, negatives, search-term review and CPA target are Search instruments that do not audit Display placements, so spend there cannot be judged by the campaign's own method.
2. **Measure per campaign.** Segment by network. Compute partner vs Google Search cost per conversion (or ROAS) with the Diff columns Rooijmans' script writes: clicks, avg CPC, cost, conversions, cost per conversion (Rooijmans, 2019).
3. **Data floor.** Ignore campaigns with fewer than 50 partner clicks in the period (Rooijmans, 2019). Under Smart Bidding, also require the campaign to have ~50 conversions in 30 days before trusting the split, because below that the bidder itself is unreliable (Vallaeys/Optmyzr, 2026).
4. **Exclusion rule.** If partner cost per conversion is more than 20% worse than Google Search for the campaign (Rooijmans, 2019: CPA_DIFF_THRESHOLD 0.2) and the campaign is otherwise meeting target, opt the campaign out of partners. If the campaign misses target on both networks, fix the campaign first; partners are not the problem.
5. **Keep rule.** If partner CPA/ROAS is within 20% or better, keep partners on regardless of CTR or CVR (Geddes/Adalysis, 2023).
6. **Smart Bidding check.** Under tCPA/tROAS, verify the partner segment separately every month: Smart Bidding does not reliably hit targets on partners and the miss can be large (17×; Geddes/Adalysis, 2023). Rooijmans attributes partner damage to Smart pricing, which cannot be opted out of (2019).
7. **Legacy campaigns.** For campaigns live before 17 November 2021, look at Segment > Network impressions/clicks around that date; the partner auction moved to position-first bidding and many campaigns saw partner traffic jump with conversion value falling (Rooijmans, 2022). If partners were never re-evaluated after that, run rules 2–5 now.
8. **Automate.** Schedule the Search Partner Alerts script monthly; it emails campaigns breaching the 20% gap with ≥ 50 clicks and writes them to a sheet (Rooijmans, 2019). Act on the email with rules 4–5.
9. **Re-test.** A campaign opted out can be re-tested when budget constraints lift; run it for a full period with ≥ 50 partner clicks before re-deciding.

## What Google will tell you instead, and why we don't
Google switches both networks on at creation and provides no per-partner reporting and no per-partner exclusion, only the campaign-level toggle (Geddes/Adalysis, 2023). We keep partners only where the campaign's own CPA/ROAS data says so, and we turn Display Expansion off because a Search campaign has no instrument to audit Display spend. Google's partner page describes the inventory and pay-per-click but says nothing about the default or how to evaluate it (Google docs, 2026).

## Failure modes
- **Low-volume campaigns.** Under 50 partner clicks the comparison is noise (Rooijmans, 2019); the default decision (rule 1) stands.
- **Brand campaigns.** Partner inventory on YouTube search and product pages can carry brand queries cheaply; apply the same CPA test but expect the "keep" outcome more often (Geddes/Adalysis, 2023: some campaigns do better on partners).
- **Judging on CTR/CVR.** The most common error; partners always look worse on those (Geddes/Adalysis, 2023).
- **Account-level decisions.** Partners that fail in one campaign may succeed in another (Geddes/Adalysis, 2023).
- **Microsoft imports.** Microsoft has publisher reports and website exclusion lists Google lacks (Geddes/Adalysis, 2023); do not copy a Google-side toggle decision across.
- **Display Expansion assumption.** The off default rests on one Tier 2 test (Seer, 2021); a campaign where Display Expansion demonstrably converts at target is a reason to keep it on, documented as an exception (skill 88's test case).

## What to measure
- Partner share of clicks, cost and conversions per campaign, monthly.
- Partner vs Google Search cost per conversion gap per campaign (alert at > 20%; Rooijmans, 2019).
- Number of campaigns opted out and the CPA change in the following period.
- Under Smart Bidding: partner-segment CPA vs the tCPA target (Geddes/Adalysis, 2023).
- Any spend attributed to Display from a Search campaign (should be zero under the default).

## Open disagreements in the canon
- **Default on or off.** Geddes (2023): measure first; Rooijmans (2019, 2022): exclude where underperforming, with a presumption that Smart pricing is hurting. Epiminds: on-and-measure for established, unconstrained campaigns; off for new or budget-limited ones (Geddes' own exception), then the 20% rule decides.
- **Display Expansion.** No Tier 1 source; Seer's 2021 test (Tier 2) is the only evidence and points the same way as the Epiminds default. Flagged for a future dossier.
