---
name: search-term-wasted-spend-script
id: 76
description: Run Rooijmans's Negative Keyword Suggestions script (and its PMax sibling) to get a weekly, already-filtered list of zero-conversion search terms above a click and cost floor, then add negatives by rule. For Search and Shopping accounts with enough clicks that single terms clear the floor. Not for n-gram aggregation (skill 70), not for conflict checking (skill 74), not an auto-negative pipeline.
tags: Script / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Further privacy-thresholding of search_term_view; Google applying close variants to negatives; removal of campaign-level PMax negatives; API-version sunsets.
---
## What this is
A weekly script that lists search terms from the last 90 days (ending yesterday) with more than 60 clicks, more than 5 in cost and fewer than 0.5 conversions, across enabled campaigns and ad groups including Shopping, skipping any term already blocked by an ad-group, campaign or active shared negative, and emails the list with a sheet link (Rooijmans, 2024). It suggests; it does not add (Rooijmans, 2024). The PMax sibling applies 100 clicks / 90 days / 0.5 conversions to `campaign_search_term_insight` terms (Rooijmans, 2024). Rhodes's keyword-vs-search script supplies the comparison view: 90 days of keyword, search-term and DSA views plus weekly averages, so you can see which keywords the junk terms came from (Rhodes, 2024).

## Where it comes from
Rooijmans's two scripts and their thresholds (2024, maintained 2025), his soft-conversion variant with Neefischer (2023), Brainlabs's phrase-negative rule from n-grams (Gilbert/Brainlabs, 2015), and Vallaeys's automation-layering framing: alert or auto-negative on top of Google's matching, human in charge (Vallaeys, 2020).

## When to use it / when not to
Use when: the account has broad or phrase keywords, DSA or Shopping — anything where Google chooses the query; after any match-type change; on PMax once terms are visible (Rooijmans, 2024).

Do not use when: the account's terms rarely reach 60 clicks in 90 days — use the n-gram script (skill 70) so patterns aggregate, or lower the floor only with a soft conversion in place (Rooijmans/Neefischer, 2023); as an auto-apply pipeline — Rooijmans's reason is that Google's matching "changes often" so a term's status is not stable (Rooijmans, 2024).

## Inputs
- Blank Google Sheet URL, account name, alert emails; `DEBUG` true for the first run (Rooijmans, 2024).
- `PERIOD` LAST_90_DAYS; `MIN_CLICKS` 60; `MIN_COST` 5 in account currency; `MIN_CONVERSIONS` 0.5 (Rooijmans, 2024). Set `MIN_COST` to one target CPA so a listed term has already cost a conversion's worth.
- Campaign name include/exclude; brand campaigns excluded (Rooijmans, 2024).
- Client exclusion list (jobs, free, competitor names, geographies not served).
- A soft conversion action if hard conversions are sparse (Rooijmans/Neefischer, 2023).

## Method
1. **Install and schedule** weekly, Monday 06:00 (Rooijmans, 2024), after the conflict script (skill 74) has run.
2. **Set the floor.** Keep 60 clicks; raise `MIN_COST` to one target CPA; keep 0.5 conversions so partial attributed conversions do not disqualify a term (Rooijmans's defaults, 2024).
3. **Classify each listed term.** (a) On the client exclusion list → exact negative at account or shared-list level; this is the one class we add without further reading (our rule; the script only suggests). (b) Wrong intent (informational, job, DIY) → phrase negative in the campaign, or in the shared list if the pattern spans campaigns (phrase-negative rule: Gilbert/Brainlabs, 2015). (c) Right intent, wrong product/page → not a negative; fix the ad group's keyword or landing page; check it in Rhodes's keyword-vs-search sheet to see which keyword pulled it (Rhodes, 2024). (d) Right intent, no conversion yet, CPC low → leave; review next month.
4. **Pattern check.** If three or more listed terms share a word, stop adding term-level negatives and run the n-gram script on that campaign (Gilbert/Brainlabs, 2015); one phrase negative replaces many exact ones.
5. **Sparse conversions.** If the list is long and the account has under a few conversions a week, add an engaged-visit soft conversion, switch the script's conversion metric to it and re-run; off-topic close-variant patterns show sooner (Rooijmans/Neefischer, 2023). Treat soft-conversion output as a review list, never class (a).
6. **PMax.** Run the PMax script weekly; a term with >100 clicks and <0.5 conversions in 90 days becomes a campaign-level PMax negative (Rooijmans, 2024); v0.9 stacks new alerts at the top of the sheet without clearing, so mark rows as handled (Rooijmans, 2024).
7. **Close the loop.** The next week's list excludes anything now blocked (the script's already-blocked check — Rooijmans, 2024); a term reappearing means the negative's match type was too narrow.
8. **Quarterly.** Re-check negatives added under class (b) against the conflict report (skill 74) and the watchdog (skill 72).

## What Google will tell you instead, and why we don't
Google's Recommendations tab suggests negatives and offers to auto-apply them, and defaults new Search campaigns to broad match [Google docs, unverified; Cooney/PPC Hero 2024]. Rooijmans's view: Google pushes broad match "like a fitness coach demanding 'just one more rep'" and the matching is "imperfect, changes often, and keeps sending irrelevant clicks" (Rooijmans, 2024). We therefore do not accept Google's negative suggestions (unknown thresholds, auto-apply off — skill 78), and we do not auto-add from our own script either except class (a). Vallaeys's fully automatic negative layer (2020) is the alternative; we stop one layer short because the practitioner who publishes the thresholds does not automate the add (Rooijmans, 2024).

## Failure modes
- **Low-click accounts**: nothing clears 60 clicks; the list is empty and the waste is in the aggregate (skill 70).
- **Brand campaigns**: brand misspellings and navigational terms ("login", "support") appear as non-converting; exclude brand campaigns from the run and handle navigational terms by policy, not by the script (Rooijmans's campaign filters, 2024).
- **Lead-gen with offline conversions imported late**: a term can show <0.5 conversions on the day the script runs and 2 a week later; use a 90-day window and never auto-negative (Rooijmans, 2024 rationale).
- **Shopping**: product-query churn produces long lists; raise `MIN_CLICKS` or scope by campaign.
- **Privacy-thresholded terms**: spend with no visible term is untouchable by this script [Google docs, unverified].
- **PMax v0.9**: the de-duplication issue flagged on the script page can collapse terms within a category; verify against the UI before adding negatives (noted on fetch of Rooijmans, 2024).

## What to measure
- Terms listed per week, by class (a)–(d), and negatives added.
- 90-day cost of listed terms at listing time (waste identified) vs cost of the same terms after the negative (waste stopped).
- Terms reappearing after a negative (match-type misses).
- Conversions on terms later found blocked by a class (b) negative (false positives; feeds the floor decision).

## Open disagreements in the canon
Vallaeys (2020) endorses a script that adds negatives automatically as the mature layer; Rooijmans (2024) ships suggest-only because matching changes. Epiminds goes with Rooijmans for everything except the client's own exclusion list, where the term's status does not depend on Google's matching. Brainlabs's n-gram approach favours phrase negatives on patterns over exact negatives on terms; we use the term list as the trigger and the n-gram as the instrument once three terms share a word.
