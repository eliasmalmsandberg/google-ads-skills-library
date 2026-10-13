---
name: brand-incrementality-test
id: 81
description: How to answer "is our brand spend incremental?" — first by removing brand contamination from PMax reporting, then by a holdout keyed to competitor presence on the brand SERP. Not for general channel incrementality (see 80) or for deciding brand campaign structure.
tags: Technique / Search / Diagnose / Established / As needed
last_verified: 2026-10-13
invalidated_by: Removal or change of PMax brand exclusions / Search brand lists; changes to Conversion Lift minimums; Google altering serving preference between exact-match keywords and PMax for brand queries.
---
## What this is
A two-stage procedure. Stage 1 measures how much of the account's "performance" is brand traffic hiding inside PMax and makes brand visible as its own line. Stage 2 decides whether a holdout is worth running — using competitor presence on the brand SERP as the prior — and, if so, how to run it. Position: brand spend is assumed non-incremental until the SERP says otherwise, but the test is skipped when conquesting competitors are present because the holdout then measures something the client will not accept losing.
See also: skill 5 (brand-nonbrand-firewall) — the negative mesh that keeps brand out of non-brand campaigns once brand is measured.
See also: skill 55 (pmax-brand-exclusions) — the brand-share threshold, handover prerequisites and leak check for taking brand out of PMax.

## Where it comes from
Rooijmans on brand contamination of PMax data and the exclusion method (close-variant negatives auto-populated from the brand campaign's search terms) (Rooijmans, 2022; 2024). Haus's three-cell PMax geo tests: excluding brand more CAC-efficient for new customers in 100% of tests, +27% incremental revenue with brand included for high-AOV brands, Google overstating PMax-with-brand by ~33% (Haus, 2024 — vendor, cited for method and data). The eBay field experiments showing brand search ads with no measurable short-term benefit (Blake, Nosko & Tadelis, 2015). Vallaeys on reading small-budget Google lift results (Vallaeys/SEL, 2025).

## When to use it / when not to
Use when a client questions brand spend, when PMax reports ROAS far above the non-brand Search campaigns, or before any PMax-vs-Search budget decision. Use Stage 1 on every account at onboarding.

Do not run Stage 2 when the brand campaign spends under ~5% of the account (Epiminds operating threshold — no canon source; reason: at that share even a factor of zero reallocates less than the test's holdout opportunity cost) — the test cannot move a decision; when a competitor is actively bidding on the brand name and the client will not tolerate lost brand clicks for 14+ days; or when in-scope conversions are below the ~300/month signal threshold (Haus, 2024).

## Inputs
- Brand term list with close variants and misspellings, taken from the brand campaign's search-term report (Rooijmans, 2024).
- PMax search-term/search-category data and conversions for 90 days.
- Brand Search campaign: IS, abs-top IS, CPC, conversions, budget status (must not be budget-limited for Stage 1 to work; Rooijmans, 2022).
- Auction Insights for the brand campaign: competitor overlap rate and top-of-page rate on brand terms.
- Organic rank for the brand term and sitelink coverage.
- AOV and new-vs-returning split (Haus's high-AOV exception; Haus, 2024).

## Method
**Stage 1 — make brand visible (always)**
1. Run the PMax brand-traffic split (script or search-category insights) and record brand share of PMax conversions and conversion value (Rooijmans, 2024).
2. If brand share of PMax conversions > ~20% (Epiminds operating threshold — no canon source; reason: below that share the restated ROAS moves less than month-to-month noise), restate PMax ROAS with brand removed before any other analysis; Google overstated PMax-with-brand performance by ~33% in Haus's Caraway case (Haus, 2024).
3. Exclude brand from PMax: shared negative list auto-populated with every close variant found in the brand campaign's search terms (Rooijmans, 2024), plus the platform brand exclusion. Confirm the brand Search campaign is not budget-limited, otherwise PMax takes the overflow and the exclusion is cosmetic (Rooijmans, 2022).
4. Re-read PMax after 30 days. The non-brand PMax number is the one that goes into the client report from now on.

**Stage 2 — decide whether brand Search itself is incremental**
5. **Set the prior from the SERP, not from the ad platform.** Pull Auction Insights on brand terms. The >10% overlap line below is an Epiminds operating threshold — no canon source; reason: it is the floor at which Google shows an auction-insights row at all [Google docs], so a competitor under it is not measurably present.
   - No competitor with >10% overlap on brand terms, organic #1 with sitelinks → prior is "non-incremental": this is the eBay condition, where paid brand clicks substituted for organic clicks with no measurable short-term benefit (Blake, Nosko & Tadelis, 2015).
   - One or more competitors with >10% overlap or regularly above you → prior is "incremental enough": the holdout would measure lost clicks to a conquestor, and Haus's data shows brand-inclusive setups winning on blended revenue in half of tests and by +27% for high-AOV brands (Haus, 2024). Skip the holdout; test bid-down instead (step 8).
6. **Run the holdout only under the first prior.** Design: geo split, brand Search paused in treatment geos, control geos unchanged; outcome = total conversions/revenue in the geo across all channels, not the brand campaign's conversions (Haus, 2024 design). Duration ≥14 days plus median conversion lag. If the client has ≥1,000 observed conversions and ≥$5k budget in scope, a Google Conversion Lift study on the brand campaign is an acceptable substitute [Google docs], read with step 7.
7. **Read.** Incremental conversions = treatment total − scaled control total. Incrementality factor = incremental ÷ brand-campaign-reported conversions (Haus, 2024). For a Google study, discount probability-of-lift below 90% and any result under ~300 in-scope conversions as a hypothesis; priors from similar campaigns are doing the work at that size (Vallaeys/SEL, 2025).
8. **Act.** The factor bands (0.3 / 0.7) and the 20–30% reduction for 30 days are Epiminds operating thresholds — no canon source; reason: 0.3 is roughly the ~33% overstatement Haus found on PMax-with-brand (Haus, 2024) read as a floor, 0.7 is where the discount stops changing the budget decision, and 30 days is the shortest window that clears one conversion cycle for most clients.
   - Factor < 0.3 → cut brand spend to a defensive floor: exact-match only, Target IS or manual CPC at the minimum that holds abs-top IS, no broad/phrase brand.
   - Factor 0.3–0.7 → keep brand, but report brand conversions × factor to the client and remove brand from any blended ROAS used to justify budget.
   - Factor > 0.7, or prior was "incremental enough" → keep brand at full coverage; test a 20–30% CPC/target reduction for 30 days and watch abs-top IS and the competitor's top-of-page rate instead of running a holdout.
9. **Separate new from returning.** Haus's cleanest finding was on new-customer CAC (excluding brand from PMax more efficient in 100% of tests, ~40% lower CAC) (Haus, 2024). Read the holdout by new-customer conversions where the client tracks them; a brand campaign can be non-incremental on total revenue and still non-incremental on new customers for the same reason — it is harvesting people who already decided.

## What Google will tell you instead, and why we don't
- Google's PMax and brand reporting present brand conversions at full value inside blended ROAS; Rooijmans' point is that brand conversions "inflate PMax performance and give it ample room to waste money" (Rooijmans, 2024). Stage 1 removes brand before any ROAS is quoted.
- Google's "search lift" and small-budget Conversion Lift studies will produce a lift number for brand at low volume; the number is prior-driven and Google does not expose the prior (Vallaeys/SEL, 2025). We do not accept a brand lift study under ~300 in-scope conversions as evidence either way.
- Google Ads reps' default advice is to keep brand coverage at ~100% IS regardless. The eBay experiments found no measurable short-term benefit from brand ads when organic dominates the SERP (Blake, Nosko & Tadelis, 2015); we make that the prior and require the SERP to argue otherwise.

## Failure modes
- **Budget-limited brand campaigns.** Exclusion from PMax just moves brand clicks to PMax overflow (Rooijmans, 2022); Stage 1 must fix budget first.
- **Competitor conquesting.** A holdout under this condition reports a large "incremental" loss that is really lost brand clicks to a competitor; the decision is about defence, not incrementality (our synthesis of the eBay/Haus disagreement).
- **High-AOV, low-volume brands.** Haus's data shows brand inclusion winning (+27% incremental revenue above $238 AOV) (Haus, 2024); the ~300-conversion floor (Haus, 2024) is rarely met, so the test is both unwise and underpowered.
- **Retail with marketplace resellers.** Resellers bid on the brand; the SERP prior flips to "incremental enough" even without a direct competitor.
- **Multi-brand or house-of-brands accounts.** Close-variant lists leak across brands; build the negative list per brand campaign (Rooijmans, 2024).
- **Short tests.** Under 14 days plus lag, brand's delayed organic substitution has not shown up; Haus and Google both floor at 14 days (Haus, 2024; [Google docs]).

## What to measure
Stage 1 monthly: brand share of PMax conversions and value, PMax ROAS ex-brand (Rooijmans, 2024). Stage 2: control vs treatment total conversions and new-customer conversions, brand-campaign-reported conversions, the incrementality factor, abs-top IS and competitor top-of-page rate on brand terms before/after (Haus, 2024). Re-test when a new competitor appears in brand Auction Insights.

## Open disagreements in the canon
- **Is brand search incremental?** eBay: no measurable short-term benefit (Blake, Nosko & Tadelis, 2015). Haus: including brand in PMax wins on blended revenue in half of tests and clearly for high-AOV brands (Haus, 2024). Rooijmans takes no position on incrementality; he wants brand measured separately (Rooijmans, 2022; 2024). Epiminds: eBay's result is the prior for a dominant-organic, no-competitor SERP; Haus's result is the prior when competitors or high AOV are present; the SERP decides which prior applies (step 5), and only the first case gets a holdout. Reason: the holdout is expensive and the second case's answer is already "defend".
- **Where to test.** Haus prefers geo holdouts on total revenue; Google offers Conversion Lift on the campaign's own conversions [Google docs]; Vallaeys accepts Google's maths with judgment (Vallaeys/SEL, 2025). Epiminds: geo on total revenue when volume allows; Google study only above 1,000 conversions, read with the step 7 discount.
