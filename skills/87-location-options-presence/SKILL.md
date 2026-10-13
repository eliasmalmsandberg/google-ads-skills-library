---
name: location-options-presence-vs-interest
id: 87
description: Decide the location option (Presence vs Presence-or-interest) for every new campaign and prove leakage on inherited ones. Not for choosing which locations to target, radius sizing, or location bid adjustments.
tags: Setting / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google removing the "Presence" targeting option (as it removed "Search interest" in April 2023); a native User-location report returning to the UI; location bid modifiers becoming available under tCPA/tROAS.
---
## What this is
The rule for the one campaign setting Google hides under "Location options": whether ads serve to people *in* the target area (Presence) or also to anyone anywhere who has *shown interest* in it (Presence-or-interest, the default). Epiminds sets Presence on every campaign unless a user-location CPA test earns the exception.
See also: skill 7 (geo-split-vs-bid-adjustments) — whether a geo gets its own campaign or stays in a shared one, and the 30/50 conversion volume test.

## Where it comes from
Nils Rooijmans' takeover checklist and his matched-vs-user-location posts (2024, 2026); Brad Geddes / Adalysis on when interest targeting is right and the CPA test that decides it (2021); Optmyzr's "check value before you exclude" rule (2025); Brainlabs' worldwide-targeting audit script (Gilbert, SEL). Google Help and the Ads API blog for what the options are since April 2023.

## When to use it / when not to
Use on every new campaign build (Search, Shopping, PMax, Display, Demand Gen) and in the first hour of any inherited account. Hotel campaigns are Presence-only by platform rule, so skip them (Google Help). Do not use this to pick target locations or radii; it only governs *who inside/outside those locations* is eligible.

## Inputs
1. Campaign type and the business's service model: local service, national/online, or destination/travel/relocation.
2. Current `Location options` value per campaign (Presence-or-interest is the default; "Search interest" and the Presence-or-interest *exclusion* no longer exist since 14 April 2023, with auto-migration from 24 April 2023 — Google Ads API blog, 2023).
3. Is the campaign budget-constrained (Lost IS (budget) > 0)?
4. A Report Editor custom report with **User location** (not the UI's Matched locations) over the last 30+ days: cost, conversions, value, split inside vs outside the targeted area (Rooijmans, 2024).

## Method
1. **Audit for no location target at all.** Any campaign with zero location targets is worldwide. Flag it before anything else; Brainlabs' audit script exists precisely for this after large builds (Gilbert/Brainlabs, SEL).
2. **Set Presence on every new campaign.** Rooijmans puts it in the first two settings he changes on any takeover, alongside turning off search partners (Rooijmans, 2026). Local service businesses: Presence, no exceptions (Geddes, 2021). National advertisers that serve the whole country: Presence with the country selected (Geddes, 2021).
3. **If budget-constrained, Presence regardless of vertical.** When the campaign is not hitting its budget, remove the interest-based audience and serve only to people physically there; the interest segment is the lowest-quality marginal spend (Geddes, 2021).
4. **The only allowed exception is a measured one.** Travel, hospitality, relocation, destination retail, and national/online sellers whose customers research from elsewhere may run Presence-or-interest (Geddes, 2021; Google Help cites +5% Search conversions for Travel/Real Estate/Education, internal data May–June 2022). To keep it, you must show from the User-location report that outside-area cost per conversion is within 2× the inside-area figure. Geddes's own account showed roughly $16 inside vs $1,000 outside — that gap is the signature of interest traffic that should be cut (Geddes, 2021). The 2× line is Epiminds' operating threshold, not a source number.
5. **Never judge leakage from Matched locations.** The UI report shows the location that *matched*, which under Presence-or-interest can be the place of interest, not where the user sits: an Amsterdam user searching "hotels in Riga" reports as Riga (Rooijmans, 2024). Build the Report Editor "User location" report, give it at least 30 days of data before excluding anything (Optmyzr, 2025), then act.
6. **Pair Presence with exclusions on PMax.** PMax leaks out-of-area leads even with Presence set; add location exclusions for the leaking regions (Rooijmans, 2024; Ed Leake: exclude "just to be safe"). Exclusion is Presence-only by platform rule, so you can only exclude people *in* a place, not people interested in it (Google Ads API blog, 2023).
7. **Do not auto-exclude an off-target area that converts.** If a region you did not plan for converts at or better than target, move it into its own campaign and test instead of excluding (Optmyzr, 2025).
8. **Under tCPA/tROAS there is no bid modifier for location, only on/off** (Geddes, 2021). So the decision is binary: include with Presence, or exclude.

Output: each campaign tagged Presence (default) or Presence-or-interest (exception, with the inside/outside CPA pair recorded and a 90-day re-check date), plus a PMax exclusion list.

## What Google will tell you instead, and why we don't
Google defaults to and recommends Presence-or-interest, warns that "most campaigns see fewer impressions" when you switch away, and reserves Presence for "sensitive verticals" (Google Help). Fewer impressions is the point: the removed impressions are people outside the area. Google's own +5% conversion figure is for three verticals over 12 days of internal data (Google Help, 2022) and is exactly the exception the method allows; it is not evidence for a plumber or a B2B SaaS. Rooijmans' line — Presence "unless fraudulent clicks are part of the growth strategy" (2026) — is the canon's position.

## Failure modes
- **Travel, hospitality, education, relocation, event ticketing.** Presence cuts real demand; run the exception test in step 4 before switching (Geddes, 2021; Google Help, 2022).
- **Multi-country or cross-border e-commerce with one campaign per market.** Shoppers often search from a neighbouring country; Presence per market can drop legitimate orders. Measure by user location first.
- **Low-volume accounts.** Under ~30 conversions in the window, the inside/outside CPA comparison is noise; default to Presence and skip the exception test.
- **Accounts whose "leakage" is actually VPN or mobile-carrier IP mislocation.** Presence will not fix it; exclusions on observed user locations will.
- **Reading Matched locations as proof.** Anyone who audits from the default UI report will conclude there is no leak (Rooijmans, 2024).

## What to measure
- Share of cost and conversions from outside the targeted area (User-location report), before and 30 days after the change.
- Inside vs outside cost per conversion; the exception survives only while outside ≤ 2× inside.
- Impression and click drop after switching to Presence, to be reported as removed waste, not lost reach.
- PMax: lead-location mismatch count per month after exclusions are added.

## Open disagreements in the canon
Geddes (2021) treats Presence-or-interest as the better starting point for national and online sellers and uses exclusions to trim; Rooijmans (2024, 2026) and Optmyzr (2025) start from Presence and expand only on proof. Epiminds goes with Presence-first because the cost of being wrong is asymmetric: lost interest traffic is recoverable by flipping the setting, while interest spend on a budget-constrained campaign displaces in-area demand that was converting (Geddes's own budget-constrained rule, 2021). No cross-account study on this setting exists in the canon; the thresholds here come from one account example and operating judgment.
