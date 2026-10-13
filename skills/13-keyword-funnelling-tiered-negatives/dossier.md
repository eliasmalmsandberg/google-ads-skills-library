# Dossier — 13 Keyword funnelling via tiered negatives

Research note: WebSearch budget exhausted; sources found via sitemaps. edleake.com (Tier 2, alpha/beta) could not be fetched. searchengineland.com rate-limited.

## Sources

1. **Source**: Brad Geddes, Adalysis — "Managing low volume keywords in an alpha/beta (managed/discovery) workflow", https://adalysis.com/blog/managing-low-volume-keywords-alphabeta-manageddiscovery-workflow/ · **Tier** 1 · **Date** 2016-04-12 · **Claim**: Discovery (beta) campaign on (then) modified broad at lower budget; when a query consistently converts, add it as an exact negative in discovery and as an exact keyword in the managed (alpha) campaign. Promotion rule: ≥ 35 impressions and ≥ 2 conversions per month for 3 consecutive months, because a keyword that doesn't consistently get ~35 impressions/month goes "low search volume" and then shows from neither campaign. Suits small/mid accounts; unmanageable at enterprise scale. · **Evidence**: author's experience; no data.
2. **Source**: Navah Hopkins, SEJ — "Match-type changes & campaign structure choices", https://www.searchenginejournal.com/match-type-changes-campaign-structure-choices/352648/ · **Tier** 1 · **Date** 2020-03-10 · **Claim**: Against match-type-split campaigns: each campaign is another budget to manage, a campaign rarely supports more than 5–7 ad groups, close variants apply to all match types and negatives do not cover them, so protecting a keyword needs many more negatives and eats the 10,000-negatives-per-campaign limit. Use broad only for 5+-word keywords alone in an ad group with all other keywords as exact+phrase negatives. · **Evidence**: reasoning.
3. **Source**: Brad Geddes, Adalysis — "Should you remove redundant keywords?", https://adalysis.com/blog/should-you-remove-redundant-keywords/ · **Tier** 1 · **Date** 2024-07-03 · **Claim**: Keep exact alongside phrase/broad; same keyword in several campaigns serves from the most restricted campaign; identical exact keyword gets set aside for the auction. · **Evidence**: 12 ad groups serving one term, CPA $24–$43; removal cases where wrong ad groups took over.
4. **Source**: Brad Geddes, Adalysis — "Working with Google's BMM / phrase match changes", https://adalysis.com/blog/working-with-googles-broad-match-modifier-phrase-match-changes/ · **Tier** 1 · **Date** 2021-02-05 · **Claim**: Google chooses the serving keyword on keyword-level CTR/CPC and favours higher CTR; intent-differing terms should be separate keywords at their own bids. · **Evidence**: duplicate term converting 18% / 32% / 20% across ad groups.
5. **Source**: Frederick Vallaeys, Optmyzr — match-type study, https://www.optmyzr.com/blog/google-ads-match-type-performance/ · **Tier** 1 · **Date** 2026-05-11 · **Claim**: Exact leads efficiency, phrase is the workhorse, broad is discovery; each match type should be checked against the purpose it is meant to serve. · **Evidence**: 30k accounts.
6. **Source**: Brad Geddes, Adalysis — "Exact match is no longer exact", https://adalysis.com/blog/exact-match-is-no-longer-exact-match-are-you-managing-the-changes-correctly/ · **Tier** 1 · **Date** 2018-12-03 · **Claim**: Ad-group negatives hit limits quickly; prefer lists; restructure when limits block the negative strategy. · **Evidence**: account examples.

## Dissenting view
Hopkins (2020) is the dissent: match-type tiers "don't make sense anymore" because close variants leak across tiers and negatives don't follow variants, so the structure costs more negatives and budgets than it returns. Geddes (2016, 2024) keeps a two-tier managed/discovery split with a strict promotion rule. The disagreement is whether deterministic routing is achievable at acceptable maintenance cost after the 2018–2021 match changes.

## What the platform currently does [Google docs]
- [Google docs] Identical exact keyword beats phrase/broad/AI Max/PMax; then relevance; then Ad Rank; near-duplicate broad keywords are deduplicated by Ad Rank (answer/7478529, fetched 2026-10-13).
- [Google docs] Negatives don't match close variants; add plurals/synonyms manually; misspellings handled automatically (answer/2453972, fetched 2026-10-13).
- [Google docs] Low search volume: keyword inactive until it has search history; rechecked ~weekly on 12-month worldwide history (answer/2616014, fetched 2026-10-13). Zero-impression ad groups auto-paused after 13 months from 11 Mar 2024 (Hopkins/SEJ 2024 citing the Ads developer blog).

## Baseline check
Read `google-ads-keywords` (match type migration: start exact+phrase, add broad later) and `google-ads-keyword-cannibalization`. This skill adds the alpha/beta promotion rule with numbers (35 impressions + 2 conversions × 3 months), the low-search-volume trap that breaks tiering, the reasons the three-tier (exact/phrase/broad) structure fails under close variants, and the Epiminds position (two tiers, campaign-level, not three).

## Judgment calls
- Epiminds position: two tiers (managed exact + discovery phrase/broad in a separate campaign), not three parallel match-type campaigns — Hopkins' maintenance argument (2020) against three tiers is accepted; Geddes' promotion discipline (2016) is kept for two.
- Geddes' 2016 rule references modified broad for discovery; the skill substitutes phrase (post-2021 phrase ≈ old BMM per Geddes 2021) or gated broad (skill 16).

## Canon strength: Strong
Three Geddes posts (two with data), Hopkins' structural counter-argument, Vallaeys' 30k-account match-type evidence.

## Invalidated by
Keyword prioritisation changes removing exact-identical priority; negatives matching close variants; Google retiring exact or phrase match; changes to the low-search-volume threshold or the 13-month zero-impression pause.
