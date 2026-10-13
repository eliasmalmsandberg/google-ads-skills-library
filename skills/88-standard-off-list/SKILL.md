---
name: standard-off-list
id: 88
description: The four defaults Epiminds switches off on every new campaign and every takeover — search partners, Display Expansion, Final URL expansion, auto-apply recommendations — and the single test that earns each one back. Not for placement exclusions, negative keywords or location options (see 87).
tags: Setting / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google defaulting search partners or Display Expansion to off; partner-site reporting or exclusions arriving for Search; Final URL expansion defaulting to off or gaining keyword-level control; auto-apply recommendations being removed or moved to MCC level.
---
## What this is
Four settings Google ships on (or pushes on) that spend budget outside the thing the campaign was built to do. Epiminds turns all four off at build and on takeover, then re-enables a setting only when a named test says so. Auto-apply is listed last but matters most: it is the mechanism that quietly turns the other three back on.
See also: skill 17 (search-partners-display-expansion) — the per-campaign search-partner evaluation in detail: the 20% cost-per-conversion gap, the 50-partner-click floor and the alert script.
See also: skill 61 (pmax-url-expansion) — the Final URL expansion decision by account type, the structural leaks to exclude and the page-feed method.
See also: skill 78 (recommendations-auto-apply-opt-out) — the full auto-apply opt-out procedure, the standing dismiss list and the change-history alert that proves the opt-out holds.
See also: skill 87 (location-options-presence) — the location option (Presence) set alongside these defaults on every takeover.

## Where it comes from
Nils Rooijmans' takeover checklist and auto-apply posts (2023, 2026); Brad Geddes / Adalysis on evaluating search partners by CPA (2023); Fred Vallaeys / Optmyzr on an auto-applied keyword removal (2023) and the 503-account PMax–Search overlap study (2025); Navah Hopkins / Optmyzr's 17,380-account Optimization Score study (2024); Seer Interactive's Display Expansion test (2021, added Tier 2 for this topic). Google Help for current defaults.

## When to use it / when not to
Every new Search, Shopping and PMax campaign; the first hour of any inherited account; and after any large build, because that is when defaults slip through. Not a quarterly task: the earn-back tests below are run once per setting per campaign, then on a 90-day cadence (Epiminds operating cadence, see Output) only for settings that were earned back.

## Inputs
- Per campaign: Networks (search partners, Display Network), PMax Final URL expansion and URL exclusions, PMax Display controls (Search Partner Network / Google Display Network, reported by PPC News Feed, 30 April 2026, from screenshots shared by Adriaan Dekker, Renaldo Spin and Barry Schwartz).
- Account: Recommendations → Auto-apply → Manage and History tabs (Google Help).
- Campaign is budget-constrained? (Lost IS (budget) > 0.)
- Campaign maturity: ~50 conversions in the last 30 days under Smart Bidding (Vallaeys/Optmyzr, 2026 — the floor skill 17 requires before trusting the network split) and ≥ 50 partner clicks in the comparison period (Rooijmans, 2019). Rooijmans (2026) gates earn-back on "mature" campaigns without a number; the library uses skill 17's figures.
- Segment → Network report per campaign, 30–90 days.

## Method
1. **Auto-apply off, first.** Turn off every auto-apply recommendation at account level (it cannot be set at MCC level — Google Help). Rooijmans found it the single setting beginners most often get wrong across 80+ audits: it broadens keywords, switches bid strategies, generates CTR-up/CVR-down creative, and raises budgets without holding CPA (Rooijmans, 2026). Vallaeys documented the "remove redundant keywords" item deleting a brand keyword that had 7 conversions, with brand CPC up more than 130% afterwards (Vallaeys/Optmyzr, 2023). The case for accepting is weak: in 17,380 accounts only 5.5% accepted any recommendation, 19% reached a 90+ score without accepting one, and the recommendations that were accepted were hygiene — conflicting negatives, missing assets (Hopkins/Optmyzr, 2024).
   - Keep a monthly habit: read the queue, apply hygiene items by hand, decline anything touching bids, budgets, match types, networks or targeting (Rooijmans, 2026).
   - If a setting you turned off is back on, the AAR queue did it; check History before blaming a colleague (Rooijmans, 2023).
2. **Search partners off at build.** Rooijmans switches partners off on every takeover, with location set to Presence (Rooijmans, 2026); Epiminds applies this to new, small and budget-constrained campaigns (Geddes's own exception), but on takeover of an established, budget-unconstrained campaign partners are not switched off blind — the Network segment already exists, so decide by skill 17's 20% cost-per-conversion rule (Geddes/Adalysis, 2023). Google does not name partner sites for Search and only allows campaign-level on/off, so there is nothing to optimise inside the network (Geddes/Adalysis, 2023; Google Help).
   - **Earn-back rule:** once a campaign is mature (Rooijmans, 2026, re-enables partners only for mature campaigns; the ~50 conversions/30 days gate from skill 17 is stated in Inputs) and is *not* budget-constrained, turn partners on and compare the Network segment once it holds ≥ 50 partner clicks (Rooijmans, 2019). Keep them only if partner cost per conversion is within 20% of Google Search (Rooijmans, 2019; skill 17); ignore CTR and CVR, which are always lower on partners (Geddes/Adalysis, 2023). Geddes's examples: $185 partner CPA vs $11 on Google search (cut), one account where partners were cheaper (keep), and partner CPA up to 17× Google's under Smart Bidding, which does not reliably hold the target there (Geddes/Adalysis, 2023).
   - Budget-constrained campaigns never get partners back; they need the highest-quality clicks they can buy (Geddes/Adalysis, 2023).
   - Run Rooijmans' partner-vs-Google comparison script so divergence after earn-back emails you rather than waiting for the next audit (Rooijmans, 2023).
3. **Display Expansion on Search: off, no earn-back by default.** Google says it spends only unspent Search budget "at similar cost per conversion" (Google Help). Seer's test on under-budget tCPA campaigns found cost roughly doubled with CPL +51% (US) and +184% with conversions −33% (UK), both significant (Seer, 2021). Rooijmans names auto-applied Display Expansion as the way to "advertise to everyone except your customers" (2026). The only test case: a Search campaign that is under budget, low volume, *and* optimises to upper-funnel actions as well as leads — run it as a 2-week test and cut any campaign with zero display conversions (Seer, 2021). Lead-gen on tCPA with a single primary conversion: never.
4. **Final URL expansion off on PMax, unless you own the page feed.** It is on by default, swaps your landing page for any page on the domain and writes its own headline (Google Help). Keywordless reach is where PMax–Search overlap comes from: in 503 accounts, 91% had PMax search terms that exactly matched a Search keyword, and where the two differed by more than 10%, Search won on CTR and CVR more often than PMax (Vallaeys/Optmyzr, 2025). Expansion behaves like DSA, which peaked at 21% of spend in Q2 2022 before PMax absorbed it (Ryan/smec, 2025).
   - **Earn-back rule:** turn it on only with a page feed attached and "URL contains" exclusions covering /blog, careers, about, policy and out-of-stock sections (Google Help), *and* brand exclusions and a brand campaign in place, because brand exclusions still leak fuzzy matches (Vallaeys/Optmyzr, 2025). Re-check the PMax search-category report 30 days later.
   - Text customization is a separate toggle; turn it off at the same time unless you have reviewed the generated assets (Google Help).
5. **PMax Display controls.** Where the Display controls setting is visible (PPC News Feed, 30 April 2026, citing Dekker, Spin and Schwartz; rollout status unclear in that report), treat Search Partner Network and Google Display Network in PMax by the same rules as steps 2 and 3.

Output: a four-line settings record per campaign (partners / display expansion / URL expansion / AAR), each either `off` or `on — earned <date>, re-check <date+90>`. The 90-day re-check is an Epiminds operating cadence — no canon source; reason: long enough for a 30-day earn-back test plus two monthly Network-segment reads.

## What Google will tell you instead, and why we don't
Google pre-selects partners, labels Display Expansion "Recommended" (PPC News Feed, 19 June 2025, citing Jyll Saskin Gales: pre-ticked in August 2024, no longer pre-ticked for new Search campaigns from June 2025, "not confirmed across all accounts"), defaults URL expansion on "for broad reach", and surfaces auto-apply as the fast route to a higher Optimization Score (Google Help). The canon's answer: the score does not need recommendations (Hopkins/Optmyzr, 2024), partners are unreportable and unexcludable on Search (Geddes/Adalysis, 2023), Display Expansion's "similar CPA" claim failed a controlled test (Seer, 2021), and expansion creates the overlap Google says its priority rules prevent (Vallaeys/Optmyzr, 2025).

## Failure modes
- **Mature, budget-unconstrained accounts with low Google-search volume** (niche B2B, long-tail services): partners can be the cheaper network; the off-at-build rule costs volume until the earn-back test runs. Geddes's lower-partner-CPA account is the warning.
- **Retail PMax with thousands of SKUs and no maintained page feed.** URL expansion off means product pages not in asset groups get no PMax Search traffic; here the earn-back path (feed + exclusions) is mandatory, not optional.
- **Tiny accounts (< $500/month — the floor Hopkins/Optmyzr used to exclude accounts from the 2024 study; adopted as an Epiminds operating cut-off).** The 30-conversion earn-back thresholds are never met; keep everything off permanently rather than running underpowered tests.
- **Agencies with Google-rep relationships.** Reps re-enable AAR; the History tab, not the rep, is the record (Rooijmans, 2023).
- **Brand awareness campaigns** where display reach is the objective: Display Expansion is not waste by definition; run a Display campaign instead so the spend is reportable.

## What to measure
- AAR History: zero applied items per month after step 1.
- Network segment per campaign: partner share of cost and partner CPA/ROAS vs Google search, monthly for earned-back campaigns.
- Display Expansion test: cost delta, conversions delta, CPL delta at 2 weeks (Seer's three metrics).
- PMax: share of search-category spend that overlaps Search keywords; brand share of PMax conversions after URL-expansion changes.

## Open disagreements in the canon
Partners: Rooijmans (2026) says off, then on for mature campaigns; Geddes (2023) says on, then cut by CPA, except small budget-limited accounts. Both agree on the test and on the small-account exception; they differ on the starting state. Epiminds starts off at build (every new campaign is in Geddes's exception) and, on takeover of an established unconstrained campaign, keeps Geddes's on-and-measure (skill 17), because his is the position with account data and the Network segment gives the baseline either way. Final URL expansion has no direct Tier 1 test either way — the rule here is built from Google's description, the overlap study and the DSA analogy, and is the weakest of the four.
