# Dossier — 14 DSA as a long-tail harvesting engine

Research note: WebSearch budget exhausted; sources found via sitemaps. searchengineland.com (Cruz, Vallaeys) rate-limited. Brainlabs DSA content unreachable. PPC Hero DSA articles were fetched (Stephanie White 2018; iProspect case 2015) and evaluated against the canon inclusion rule: they publish method but no reproducible evidence and do not contradict Google — not added to Tier 2; recorded here for completeness only.

## Sources

1. **Source**: Brad Geddes, Adalysis — "DSA testing: what you need to know to test Dynamic Search Ads effectively", https://adalysis.com/blog/dsa-testing-what-you-need-to-know-to-test-dynamic-search-ads-effectively/ · **Tier** 1 · **Date** 2016-01-19 · **Claim**: Treat DSA as backfill, not primary traffic; segment site targets only until an additional level stops moving CTR/CVR/CPI (blender → juicer example: impressions dropped sharply at the juicer level and metrics stopped improving); write description lines specific to each segment; use negative keywords and negative site phrases ("out of stock"); test 2+ DSAs per ad group on different value propositions; run the same lines in text-ad groups for comparison. · **Evidence**: one appliance-retailer segmentation test; chart not readable.
2. **Source**: Navah Hopkins, SEJ — "How to use negative keywords in paid search campaigns", https://www.searchenginejournal.com/negative-keywords-paid-search-campaigns/365834/ · **Tier** 1 · **Date** 2020-05-12 · **Claim**: Add all actively targeted keywords as negatives in the DSA campaign to avoid bidding against yourself — Google's official position is that DSA won't compete with keywords and recommends mixing them; the author disagrees from her own results. · **Evidence**: author's observation of DSA performing differently with vs without negatives; no numbers.
3. **Source**: Navah Hopkins, SEJ — "Why have my Google Ads not got any impressions?", https://www.searchenginejournal.com/ask-a-ppc-why-have-my-google-ads-not-got-any-impressions/515178/ · **Tier** 1 · **Date** 2024-06-13 · **Claim**: Use DSA to surface how people actually search; pair DSA with Max Clicks and a bid cap to estimate cost and volume for new concepts. · **Evidence**: opinion.
4. **Source**: Navah Hopkins, SEJ — "Choosing your keyword champion", https://www.searchenginejournal.com/choosing-keyword-champion-setting-up-success-auction/508435/ · **Tier** 1 · **Date** 2024-03-15 · **Claim**: Use DSA, PMax search themes and broad match for discovery, with negatives as waste guardrails. · **Evidence**: opinion.
5. **Source**: Brad Geddes, Adalysis — "5 steps before broad match", https://adalysis.com/blog/6-steps-you-should-take-before-using-broad-match-keywords/ · **Tier** 1 · **Date** 2024-04-30 · **Claim**: Google has fixed DSA-era indexing issues such as privacy-policy pages being targeted (contextual note). · **Evidence**: observation.
6. **Source**: Brad Geddes, Adalysis — "Should you remove redundant keywords?" · **Tier** 1 · **Date** 2024-07-03 · **Claim**: Add harvested queries as exact keywords with matching ad/landing page; identical exact keywords get set aside for the auction. · **Evidence**: account data (12 ad groups, CPA $24–43).
7. (Not canon, recorded) Stephanie White, PPC Hero — "DSA for advanced users", 2018: page-feed targeting with labels (rating, category, top sellers, exclusions); exclusion label for low-ROAS URLs; one client, no figures. Alexandre Valadon (iProspect) via PPC Hero, 2015: DSA replaced paused generic campaigns; clicks +70.5% on 26.7% lower budget, conversions +113%, CPA −65.5%; single client, no baselines. Neither passes the inclusion rule (no reproducible evidence, no Google disagreement).

## Dissenting view
Google's position (and the iProspect case) treats DSA as a traffic engine that coexists with keywords without competing. Hopkins (2020) and Geddes (2016) treat it as backfill/discovery that must be fenced with negatives and whose winners must be moved out into keyword campaigns. The disagreement is whether DSA is a destination or a feeder.

## What the platform currently does [Google docs]
- [Google docs] DSA targeting: page feeds (up to 100 per account), Google-generated categories, URL_Contains / URL_Equals, whole site; headlines generated from the query and landing page with the HTML title as the strongest signal; advertiser writes only descriptions; recommends regular search-term review and negatives; ad customizers in DSA descriptions stopped serving 31 May 2024; **campaigns using DSA will be automatically upgraded to AI Max in February 2027** (support.google.com/google-ads/answer/2471185, fetched 2026-10-13).
- [Google docs] Search terms from DSA show no keyword and "Exact" in the match type column (answer/2472708, fetched 2026-10-13).
- [Google docs] Keyword prioritisation: identical exact keyword in a Search campaign beats phrase/broad/AI Max/PMax (answer/7478529). DSA's place in the order is not stated on the page; Hopkins (2020) reports DSA competing with keywords in practice.

## Baseline check
Read `google-ads-keywords` (DSA section: "discovery tool… mine search terms → add winners as exact") and `google-ads-search-term-mining` (DSA workflow: run 30–60 days, harvest converting queries, negative irrelevant ones). This skill adds the segmentation stop rule (segment until metrics stop moving), the fence (all targeted keywords as DSA negatives, against Google's guidance), the bid-cap/Max-Clicks discovery setup, the harvest-and-protect loop with the identical-exact rule, the negative-site-phrase control, and the February 2027 AI Max upgrade as a hard expiry.

## Judgment calls
- Evidence in the canon for DSA is thin on numbers (one Geddes segmentation test, Hopkins' qualitative observation); strength is Adequate, not Strong.
- The Feb 2027 AI Max auto-upgrade means this skill has a known end date; the skill says so and frames DSA as a harvesting tool to run and harvest from before that date.
- Harvest thresholds (impressions/conversions) are borrowed from the alpha/beta promotion rule (Geddes 2016, skill 13) rather than invented.

- Review fix (2026-10-13): monthly harvest cadence, the 'one target CPA of spend' early-promotion floor, the small-site rule (no page count in canon) and the conversion-lag caution are all Epiminds operating choices, labelled as unsourced in SKILL.md.

## Canon strength: Adequate
Two Tier 1 practitioners with method; limited numeric evidence; Google docs for platform state.

## Invalidated by
The scheduled February 2027 auto-upgrade of DSA campaigns to AI Max; removal of DSA search term reporting; changes to keyword prioritisation between DSA/AI Max and keyword campaigns.
