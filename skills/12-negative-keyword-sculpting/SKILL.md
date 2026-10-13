---
name: negative-keyword-sculpting
id: 12
description: Route each query to the campaign and ad group that should own it, using exact and phrase negatives at the right level, when the same term is served from several places (Search vs Search, Search vs PMax, Search vs DSA). Use when the search terms report shows one term in 2+ campaigns or ad groups. Not for wasted-spend negatives (skill 10) and not for building a tiered match-type structure from scratch (skill 13).
tags: Technique / Search / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google changing keyword prioritisation so identical keywords always win regardless of campaign restrictions; negatives starting to match close variants; removal of campaign-level PMax negatives; AI Max replacing keyword-level control in Search (DSA auto-upgrade to AI Max scheduled Feb 2027).
---
## What this is
Deciding, per query family, which campaign and ad group gets to serve it, and enforcing that with negatives rather than trusting Google's prioritisation. The cost of not doing it is measurable: one search term served from 12 ad groups ran CPA from $24 to $43 depending on which ad and landing page won (Geddes/Adalysis, 2024); the same query converted at 10% in one ad group and 1% in another (Geddes/Adalysis, 2022); and in 3,300+ non-retail PMax campaigns, 45% of PMax search terms were also Search terms, PMax took more impressions 61% of the time where they overlapped, and Search had the higher conversion rate 84% of the time (Geddes/Adalysis, 2024).

## Where it comes from
Brad Geddes' negative-keyword and overlap posts (Adalysis, 2017, 2022, 2024 ×2) supply the serving rules Google actually applies, the data and the list architecture; Navah Hopkins (SEJ, 2020, 2022) supplies the brand/generic and DSA routing rules and the single-word negative pattern; Nils Rooijmans (2025) supplies the PMax list mechanics.

## When to use it / when not to
Use whenever the search terms report, segmented by campaign and ad group, shows the same term served from more than one place; after launching any new campaign, match type expansion, DSA or PMax; and before acting on Google's "remove redundant keywords" recommendation (answer: don't; Geddes/Adalysis, 2024). Do not use it to chase every duplicate — act on terms with enough data to show a CVR or CPA difference (10–50 clicks with no conversions is too little; Geddes/Adalysis, 2017). Do not use it as a substitute for fixing an ad group whose ad doesn't match its keywords.

## Inputs
- Search terms report, 90 days, with campaign, ad group, keyword, match type, clicks, cost, conversions, CVR.
- Keyword export across all campaigns with match types; all negatives by level and list.
- PMax search terms exported per campaign (Geddes/Adalysis, 2024) and DSA search terms.
- Campaign restrictions (budget, device, geo) — because Google serves a duplicated keyword from the most restricted campaign (Geddes/Adalysis, 2024).
- The ownership map: which campaign is meant to own brand, each product line, generics, discovery.

## Method
1. **Find duplicates.** Pivot search terms by term × campaign × ad group; keep terms appearing in 2+ places with combined clicks above the data floor (Geddes/Adalysis, 2022; 2017).
2. **Decide the owner** per term family by the ad and landing page that fits, not by campaign seniority: if the ad or landing page needs to differ, the term belongs in a separate ad group; if not, the split doesn't matter (Geddes/Adalysis, 2022). Where data exists, the owner is the ad group with the best CVR at comparable CPA (Geddes/Adalysis, 2019, 2024).
3. **Make the owner eligible first.** Add the term as an exact keyword in the owning ad group before blocking it elsewhere, so Google has an identical exact keyword to set aside for the auction (Geddes/Adalysis, 2024; Google docs, 2026). Never delete the exact "redundant" copy — removed keywords are forgotten and the query drifts to a worse ad group (Geddes/Adalysis, 2024).
4. **Block the non-owners at the lowest level that fully covers the leak** (Geddes/Adalysis, 2017):
   - Same campaign, other ad groups → exact negative in each non-owning ad group (Geddes/Adalysis, 2019). For two ad groups that keep trading a term because of close variants, use the single distinguishing word as a negative in each other's ad group ("software" in the "platform" group and vice versa) (Hopkins/SEJ, 2022).
   - Other campaign → phrase negative at campaign level or in a shared routing list applied to the non-owning campaigns. Add plural/singular and synonym forms; negatives do not expand (Google docs, 2026).
   - Never block by repeating the same list in every ad group; move it up (Geddes/Adalysis, 2017).
5. **Brand vs generic.** Brand and competitor terms as negatives in every generic campaign; brand converts better and cheaper and distorts generic CPA if it leaks (Hopkins/SEJ, 2020). Add brand misspellings as exact keywords in the brand campaign rather than relying on Google's spelling correction, which Geddes observed failing while misspelled brand queries served through PMax (Geddes/Adalysis, 2024).
6. **Search vs PMax.** Export PMax search terms campaign by campaign; terms the Search campaign should own become exact Search keywords with matching ad copy and landing page (Geddes/Adalysis, 2024). Then add the Search campaign's core terms to the PMax campaign's negatives (campaign-level, with Google's impact preview) or to a shared list applied to PMax; avoid account-level negatives because they hit every campaign (Rooijmans, 2025). Brand goes in PMax brand exclusions, not negatives (Hopkins/Optmyzr, 2026). Check the Search campaign is not budget-limited and the keyword is not low-volume, the two conditions under which Google routes to PMax anyway (Google docs, 2026).
7. **Search vs DSA.** Add every actively targeted keyword as a negative in the DSA campaign, despite Google's position that DSA won't compete with keywords (Hopkins/SEJ, 2020).
8. **Campaign restriction trap.** If the same keyword exists in two campaigns, expect the one with the smaller budget, fewer devices or tighter geo to serve it (Geddes/Adalysis, 2024). Either remove the keyword from the restricted campaign or accept that the restriction decides ownership.
9. **Verify.** After 2–4 weeks (Epiminds operating cadence — no canon source; reason: long enough for the routed term family to accumulate clicks in the owning ad group, short enough to catch variant migration before the next monthly n-gram pass), re-pivot. Variants (plural, order, misspelling) will still migrate because Google does not reliably serve the ad group with the matching keyword (Geddes/Adalysis, 2022); add the specific variant negative or keyword, then run the conflict check (skill 21).
10. **List hygiene.** Account-wide blocks live in one shared list; separate lists only where campaign types need different sets (Geddes/Adalysis, 2017). Name routing lists by owner ("→ owned by Brand"). Strip any "+" copied from old BMM keywords; it may not block anything (Geddes/Adalysis, 2017).

## What Google will tell you instead, and why we don't
Google recommends removing redundant keywords and states that broader match types "include everything narrower types catch", so one broad keyword can replace exact and phrase versions (Google docs, 2026). Geddes' answer is a flat "no": an identical exact keyword is what gets a query set aside for the right ad group, removed keywords are not remembered, and accounts that followed the recommendation saw inappropriate ad groups take queries that used to route correctly (Geddes/Adalysis, 2024). Google also says PMax respects keyword targeting; across 3,300 campaigns PMax still won the impression 61% of the time where terms overlapped, and Google's two help pages on the priority rule contradict each other (Geddes/Adalysis, 2024). Google's conflict recommendations ignore match types and campaign lists, so we run our own (Geddes/Adalysis, 2022).

## Failure modes
- **Small accounts.** Below roughly 10,000 clicks per 90 days, route by ad/landing-page fit only — an Epiminds adaptation of Geddes' figure, which he gives as "enough data for a machine to learn from" (Geddes/Adalysis, 2022), not as a routing floor; below it, CVR differences between ad groups are treated as noise.
- **Over-sculpted match-type campaigns.** Match-type-split structures multiply the negatives needed because close variants apply to all match types and negatives don't cover them; Hopkins (SEJ, 2020) stopped using them. Skill 13 covers when a tiered structure is still worth it.
- **Retail PMax.** The overlap study excluded retail; Shopping-feed PMax routing follows different rules (Geddes/Adalysis, 2024).
- **Negative limits.** 10,000 per campaign (Hopkins/SEJ, 2020); the account-level PMax list holds 1,000 (Hopkins/Optmyzr, 2026). Restructure before you run out.
- **Budget-limited owners.** If the owning Search campaign is limited by budget, Google serves from PMax regardless of your negatives (Google docs, 2026).

## What to measure
- Number of search terms served from 2+ ad groups, and share of impressions they represent (28% in one travel account; Geddes/Adalysis, 2019).
- CPA and CVR of routed term families before vs after, in the owning ad group.
- PMax-vs-Search overlap share after routing (Geddes/Adalysis, 2024 baseline: 45% of PMax terms).
- Brand CPA in the brand campaign and brand-term spend leaking into generic or PMax.
- Negative count per campaign and per list, trend (list growth is a restructure signal).

## Open disagreements in the canon
- **Google's priority rules vs observed behaviour.** Google documents identical-exact-wins; Geddes (2019, 2024) documents exceptions. Epiminds builds the exact keyword and the negatives — belt and braces — because the exact keyword costs nothing and the negative is what actually enforces ownership.
- **How many campaigns.** Hopkins (2020) wants fewer campaigns and fewer negatives; Geddes (2018) restructures when negatives can't cleanly separate intent. Epiminds splits campaigns only when the ad or landing page must differ or budgets must be separate (Geddes, 2022), and otherwise routes at ad-group level.
