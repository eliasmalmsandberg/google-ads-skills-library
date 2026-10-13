---
name: n-gram-analysis
id: 10
description: Monthly n-gram pass over the search terms report to find root negatives and new ad group themes that term-by-term review misses. Not for single-term triage (use the weekly search term review) and not for PMax asset-group steering (PMax takes no asset-group negatives).
tags: Technique / Search / Optimise / Established / Monthly
last_verified: 2026-10-13
invalidated_by: Further cuts to search terms report visibility; negative keywords starting to match close variants or synonyms; Scripts/GAQL changes to the search_term_view resource; removal of PMax search term reporting.
---
## What this is
Aggregate every search term into its 1-, 2- and 3-word fragments and read performance at the fragment level. An account with ~1M search terms collapses to 30–50k n-grams (Geddes/Adalysis, 2025), and patterns that never clear a term-level threshold become obvious: "wine" sat inside 99 different queries with one conversion at a very high CPA, no single query above 60 clicks, and could be fixed with one negative instead of 99 (Geddes/Adalysis, 2017). The output is a short list of root negatives, a short list of new ad group themes, and a list of intent words that change CPA enough to deserve their own keywords.

## Where it comes from
Brad Geddes' n-gram posts (Adalysis, 2016, 2017, 2021, 2025) supply the thresholds and the decision rules; the Brainlabs Search Query Mining script as republished by Nils Rooijmans (2022, maintained 2025) supplies the free implementation and its defaults; Rooijmans' Negative Keyword Suggestions script (2024) supplies the term-level review thresholds; Navah Hopkins (SEJ, 2022) supplies the negative match-type rule; Optmyzr (2026) supplies the warning about the cost of a wrong negative.

## When to use it / when not to
Use monthly on any Search account whose search terms report is too long to read, and always before adding root-word negatives (Geddes/Adalysis, 2017: adding root words without checking n-grams first is a leading cause of keyword conflicts). Use it as step one of broad match management (Geddes/Adalysis, 2024). Do not use it on accounts with under roughly 1,000 search terms a month — term-level review is faster and the aggregation adds nothing. Do not run it over a window that mixes pre- and post-restructure data.

## Inputs
- Search terms report, last 90 days (Rooijmans, 2024 default), enabled campaigns and ad groups only (Rooijmans/Brainlabs script default, 2022).
- All negatives at ad group, campaign and shared-list level, so already-blocked queries are removed before aggregation (`checkNegatives = true`, Rooijmans/Brainlabs script, 2022).
- Target CPA or ROAS for the account, and the account's 90-day average CPA.
- Attribution model in use — DDA produces fractional conversions that make n-gram CPA meaningless at low spend (Geddes/Adalysis, 2025).

## Method
1. Build n-grams of length 1 to 3 (Geddes/Adalysis, 2025); go to 4 only for long-tail-heavy accounts (Rooijmans/Brainlabs script default is 1–2, 2022; Optmyzr's tool allows up to 6, 2026). Output per n-gram: instance count (number of distinct terms containing it), impressions, clicks, cost, conversions, conversion value, and the ratios (Rooijmans/Brainlabs script, 2022). Build the tables at account, campaign and ad group level — the campaign-level table is what tells you whether a word fails everywhere or only in one ad group (Geddes/Adalysis, 2017).
2. Drop n-grams below 10 impressions (Rooijmans/Brainlabs script default, 2022).
3. **Block list.** Flag n-grams with clicks > 150 and conversions = 0, plus conversions = 0 sorted by cost descending (Geddes/Adalysis, 2025). Before adding any of them, open the underlying terms (Optmyzr, 2026; Geddes/Adalysis, 2025) and apply rule 6.
4. **Expensive list.** Flag n-grams with conversions > 1, clicks > 150 and cost above a floor scaled to the account; sort by CPA descending or ROAS ascending (Geddes/Adalysis, 2025). Ignore any row whose conversions are fractional and whose spend is under roughly one target CPA — the $17,377 CPA on $173 of spend with 0.01 conversions is an artefact of DDA, not a finding (Geddes/Adalysis, 2025).
5. **Review queue.** N-grams with clicks > 60, cost > 5 currency units and conversions < 0.5 (Rooijmans, 2024 term-level defaults) go into a watch list, not a negative list. They are re-checked next month; they graduate to the block list only when they pass rule 3.
6. **Classify each flagged n-gram** (Geddes/Adalysis, 2025, 2017):
   - Unrelated to the business, high spend, zero conversions → root negative.
   - Low-intent modifier ("how", "what", "today", cost-question words) → negative in conversion campaigns, or a separate keyword at a lower bid if the intent is servable (Geddes/Adalysis, 2021: "how" ran at > 2× the ~$450 account CPA, cost-question queries > $1,000, "quote" < $300).
   - A theme you could serve (a comparison the business can win, a product variant you stock) → build an ad group with its own ad and landing page; do not negate, because a negative removes the whole theme.
   - Demand for something you don't sell yet → temporary negative, dated, reviewed when the offering exists.
7. **Match type for the negative.** Single word: phrase (identical to broad on Google, and imports to Microsoft) (Hopkins/SEJ, 2022). Two or three words where the single word would block good traffic: phrase on the specific combination, e.g. "support number" rather than "support" (Hopkins/SEJ, 2022). Add singular and plural forms yourself — negatives do not expand (Google docs; Geddes/Adalysis, 2017).
8. **Level.** Root negatives that fail at every campaign level go to the shared list; a word that fails only in one ad group gets an ad-group negative (Geddes/Adalysis, 2017). Never repeat the same list in every ad group (Geddes/Adalysis, 2017).
9. **Positive side.** N-grams with instance count high and CVR at or above account average (Geddes 2017: "napkins", 1,804 queries at 4% CVR) are checked against the keyword list; missing 2–3-grams become phrase or exact keywords in the ad group whose ad already covers them (Rooijmans/Brainlabs script, 2022).
10. Record every negative added with the n-gram evidence and the date, and run the conflict check (skill 21) before the next build.

## What Google will tell you instead, and why we don't
Google's search terms insights fold low-volume queries into themes and "other queries", and the search terms report drops queries without "enough query activity" (Google docs, 2026). That is the data n-gram analysis is designed to recover: the long tail of 10-click terms that together cost real money (Geddes/Adalysis, 2016). Google's negative keyword page also says negatives won't match close variants and that "too many" negatives reduce reach (Google docs, 2026). We treat a root negative chosen from n-gram data as the opposite of over-blocking: one negative replacing 99 term negatives (Geddes/Adalysis, 2017) reduces list size and conflict risk.

## Failure modes
- **Small accounts.** Under ~1,000 terms a month, n-grams rarely clear 150 clicks; the method produces nothing and term-level review is the right tool.
- **DDA / fractional conversions.** Any low-spend n-gram will show absurd CPA; rule 4's spend floor is mandatory (Geddes/Adalysis, 2025).
- **Multi-service accounts on shared landing pages.** A word that fails in one service line can be the core of another; campaign-level tables prevent the "negative whacking" where an ad-group negative just moves the query to a worse ad group (Geddes/Adalysis, 2017).
- **Function words and location words.** "In" and city names aggregate to large zero-conversion rows; the fix is usually localisation of ads and pages, not a negative (Geddes/Adalysis, 2016).
- **Spam-inflated conversions.** A fake-conversion burst can make a junk n-gram look like a winner, and negating it later does not un-train Smart Bidding (Optmyzr, 2026).
- **Lead-gen with long cycles.** 90 days of click data may contain conversions that haven't landed yet; use conversion lag before trusting conversions = 0.

## What to measure
- Count of search terms covered per negative added (target: many-to-one).
- Spend on zero-conversion n-grams, month over month.
- Account CPA on the "expensive" intent words before and after separation (Geddes/Adalysis, 2021).
- Impression change on keywords sharing words with new negatives (conflict signal; skill 21).
- Number of flagged n-grams converted into ad groups rather than negatives.

## Open disagreements in the canon
- **How much data before blocking.** Rooijmans' script flags terms at > 60 clicks (2024); Geddes flags n-grams at > 150 clicks (2025). Epiminds uses 150 for n-gram blocks because one root negative removes many queries, and 60 only as a review queue.
- **Negate or build.** Rooijmans' script frames poor performers as negatives (2022); Geddes argues a losing theme may be a missing ad group or missing product (2025, 2017). Epiminds follows Geddes: classify before blocking, and date any temporary negative.
- **Run cadence.** Adalysis computes weekly (2016); the Epiminds cadence is monthly because the action list is strategic (ad groups, root negatives), with the weekly term review handling urgent waste.
