---
name: close-variant-leakage-audit
id: 11
description: Monthly per-keyword comparison of true-exact vs "exact match (close variant)" traffic to find where Google's matching is stretching intent and costing CPA. Use when exact-match CPA drifts or Smart Bidding spend on exact keywords grows without conversions. Not for broad-match query review (skill 10/16) and not a Quality Score diagnostic.
tags: Diagnostic / Search / Diagnose / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Removal of the "(close variant)" label from the search terms report; keyword prioritisation changes that make identical exact keywords reliably win; negatives beginning to match close variants or synonyms; further search-term visibility cuts.
---
## What this is
A per-keyword split of exact-match traffic into the queries that are literally the keyword and the queries Google added as close variants, with a decision rule for each keyword where the variants convert worse. The leakage is intent, not spelling: "car hire" matched to "car rental" cut conversion rate 54% and roughly tripled CPA, "PPC ads" matched to "PPC" cut conversions 63%, and "forms of trademarks" matched to "trademark forms" cut them 100% (Geddes/Adalysis, 2018). Google can detect similar meaning but not similar intent — cost vs quote, trademark vs copyright (Geddes/Adalysis, 2021).

## Where it comes from
Brad Geddes' close-variant and match-type posts (Adalysis, 2018, 2019, 2021) supply the measured CVR/CPA gaps, the 10% tolerance and the fix order; Nils Rooijmans' Monitor Close Variants script (2018, maintained 2025) supplies the per-keyword split and the 40% flags; Navah Hopkins (SEJ, 2020) supplies the structural consequence that negatives do not cover variants.

## When to use it / when not to
Run monthly on every account with exact keywords, and immediately when exact-match CPA has moved more than the account's normal month-to-month noise with no bid or landing page change. Prioritise accounts on Smart Bidding, where Rooijmans (2018) expected the impact to concentrate. Skip keywords whose close-variant spend is a trivial share of the account — a problem on 0.05% of spend does not justify restructuring (Geddes/Adalysis, 2018). Not for brand campaigns alone; brand variants need the same audit but a different fix (own the misspellings as keywords, Geddes/Adalysis, 2024 via skill 12).

## Inputs
- Search terms report, last 30 days (Rooijmans, 2018 default) for enabled Search campaigns, with the match type column, keyword, ad group, impressions, clicks, cost, conversions, conversion value.
- Keyword list with match types and current negatives at all levels.
- Target CPA/ROAS and the account's minimum-spend floor for action (Epiminds sets this at one target CPA per keyword per month; Geddes 2018 gives the principle, not the number).

## Method
1. **Split.** For each exact keyword, aggregate terms labelled "Exact match" (true exact) and "Exact match (close variant)" separately: impressions, clicks, cost, conversions, CPA for each; close-variant share of impressions, clicks, cost and conversions; CPA difference (Rooijmans script, 2018/2025). Keep a `_TOTAL_` row for the account.
2. **Screen.** Flag any keyword where close-variant share of cost ≥ 40% or the close-variant CPA is ≥ 40% worse than true-exact CPA (Rooijmans, 2018 highlight threshold). Drop flagged keywords whose close-variant spend is below the action floor.
3. **Tolerance.** A flagged keyword is acceptable if close-variant CPA is within ~10% of true-exact CPA, and usually it will be higher, not lower (Geddes/Adalysis, 2018). Outside 10%, continue.
4. **Classify the variants** by reading the terms (Geddes/Adalysis, 2018, 2021):
   - Syntax variants (plural, misspelling, word order) converting on par → leave.
   - Dropped or swapped intent word ("hire"→"rental", "tickets" dropped, "quote"→"cost", "trademark"→"copyright") → intent leak; go to step 6.
   - Question/long-tail expansions (3-word exact matching 5+ and 8+ word questions; Geddes/Adalysis, 2021) → intent leak, usually to informational.
   - Variants that convert better than the keyword → add them as exact keywords in the same ad group so they get their own bid and ad (Geddes/Adalysis, 2021).
5. **Duplicate-serving check.** Filter the same close-variant term across ad groups; where it is served from 2+ ad groups with different CVR (24% vs 18.86%; 18%/32%/20% in Geddes' examples, 2018, 2021), add an exact negative to every ad group except the best converter (Geddes/Adalysis, 2019).
6. **Fix, in this order** (Geddes/Adalysis, 2018):
   a. Add the leaking variant as a phrase or exact negative at the campaign or shared-list level if the intent is wrong account-wide; at ad-group level only if the problem is isolated, because ad-group negatives hit limits fast.
   b. Add singular/plural and synonym forms of the negative yourself — negatives do not expand (Google docs, 2026; Hopkins/SEJ, 2020).
   c. If the variants are many and the keyword is 3+ words, convert the keyword to phrase and watch impressions, which can jump sharply (Geddes/Adalysis, 2018).
   d. If the leak crosses a product line ("hire" vs "rental"), restructure into separate campaigns so negatives can be clean (Geddes/Adalysis, 2018).
   e. Where Google drops a word, add the shortened form as its own keyword with its own bid so you control it rather than Google (Geddes/Adalysis, 2018, 2021).
7. **Re-run after 30 days.** Because Google picks the serving keyword on keyword-level CTR/CPC, not ad-group CVR (Geddes/Adalysis, 2021), expect some variants to migrate to another keyword rather than disappear; repeat step 5.

## What Google will tell you instead, and why we don't
Google's docs say exact match covers searches with "the same meaning or intent" and that an identical exact keyword takes priority over everything else (Google docs, 2026). Geddes measured the "same intent" claim against account data and found a 54% CVR drop on hire→rental and 100% on trademark forms (2018), and found exact keywords losing to lower-performing ad groups despite the stated priority rules, which have "so many exceptions" they are of little practical use (2019). Google also says negatives automatically handle misspellings now (Google docs, 2026); we still add misspelled negatives explicitly because every practitioner source in the canon assumes they are not covered (Geddes 2017; Hopkins 2020) and the cost of a redundant negative is zero.

## Failure modes
- **Low-volume keywords.** Under a few hundred clicks a month per keyword the true-exact vs variant CPA comparison is noise; aggregate to ad group or use the n-gram view (skill 10).
- **Brand keywords.** Variant misspellings of the brand are usually your best traffic; never negate them — add them as keywords (Geddes/Adalysis, 2024).
- **Over-negating in Smart Bidding accounts.** Rooijmans (2018) expected the variant expansion to matter mainly under Smart Bidding; removing variants that convert within tolerance starves the algorithm of cheap conversions.
- **Accounts already restructured by match type.** Hopkins (SEJ, 2020) notes match-type-split campaigns multiply the negatives needed because variants apply to every match type; fix structure (skill 13) before auditing variants.
- **Multi-language or implied-word languages.** Google applies reordered/implied-word variants only in listed languages (Google docs, 2026); audit scope differs by market.
- **Search-term visibility.** The report omits low-activity queries (Google docs, 2026), so measured leakage understates the true figure; treat the result as a floor.

## What to measure
- Close-variant share of exact-match cost and conversions, per campaign, monthly trend.
- CPA gap (close variant vs true exact) on the top 20 exact keywords by spend.
- Count of terms served from 2+ ad groups (Geddes/Adalysis, 2019: 28% of impressions in one travel account).
- Impressions on keywords after adding negatives (conflict signal; skill 21).
- Share of flagged variants resolved by adding a keyword vs adding a negative.

## Open disagreements in the canon
- **Is leakage net-negative by default?** Geddes (2018) says some accounts do as well or better on variants but calls it uncommon; Hopkins (2019) argues looser matching can carry quality intent. Epiminds position: measure per keyword, burden of proof on the variant, because the measured failures are large (−54% to −100% conversions) and the measured wins are small and rare.
- **Screen threshold.** Rooijmans' 40% flags (2018) and Geddes' 10% tolerance (2018) are different numbers for different jobs; Epiminds uses 40% to select keywords to read and 10% to decide whether to act.
