# Dossier — 59 PMax cannibalising brand/Search — diagnosis

## Sources

1. **Source**: Frederick Vallaeys, Optmyzr, "Is Performance Max Cannibalizing Your Search Campaigns? Our New Data Study Says… Probably" — https://www.optmyzr.com/blog/is-pmax-cannibalizing-search/ · **Tier** 1 · **Date** 2025-07-31 (data 2025-02-01 to 02-28) · **Claim**: Part 1 (503 accounts): 91.45% of accounts had PMax search terms exactly matching a Search keyword; 56.29% of 5,768 Search campaigns and 27.86% of 40,642 ad groups affected; overlap on all match types including exact. CTR: Search better 28.4%, PMax better 16.0%, no difference 55.7%. CVR: Search better 18.9%, PMax better 6.2%, no difference 74.9%. Part 2 (511 accounts, 424,820 terms): 97.26% of accounts overlap at search-term level; CTR Search won 32.4% vs PMax 24.2%; CVR Search better 7.7% vs PMax 4.3%. Differences <10% treated as insignificant; cost excluded. Fixes: add converting PMax queries as exact-match keywords in Search; check Search eligibility (targeting, bids, budgets); turn off auto-apply recommendations that remove "redundant" keywords; add branded misspellings as exact match. · **Evidence or opinion**: Cross-account study; author notes eligibility was not tested.

2. **Source**: Brad Geddes, Adalysis, "Is Performance Max cannibalizing your Search ads?" — https://adalysis.com/blog/is-performance-max-cannibalizing-your-search-ads-a-deep-dive-into-search-term-overlap/ · **Tier** 1 · **Date** 2024-12-12 · **Claim**: 3,300+ non-retail PMax campaigns, ~1.2M terms (terms <10 impressions excluded). 2.8% of PMax terms matched a Search keyword; 67% of PMax campaigns had some overlap (range 0–100%). 45% of PMax terms also appeared as Search search terms. On the same term PMax had more impressions 43% of the time (61% where overlap existed); Search had higher CTR 65%, higher CVR 84.18%, higher conversion value 84.62% of the time. Suggests PMax may hold higher Ad Rank. Ignore "remove redundant keywords"; for lead gen consider pausing PMax. Google's two help files are inconsistent on priority. Reader comment: PMax took 83% of impressions on one exact-match query. · **Evidence or opinion**: Cross-campaign study.

3. **Source**: Kirk Williams, ZATO, "Campaign auction eligibility and Performance Max behavior" — https://zatomarketing.com/blog/campaign-auction-eligibility-and-performance-max-behavior · **Tier** 1 · **Date** 2023-01-05 · **Claim**: Google decides which eligible campaign enters an auction. A Search brand campaign whose bid sits under the bid floor for that user's auction becomes ineligible and PMax takes the brand search. Geography and other limits also remove eligibility. Hard to verify without term data. · **Evidence or opinion**: Reasoned hypothesis from experience; no data.

4. **Source**: Nils Rooijmans, newsletter 2022-04-14 — https://nilsrooijmans.com/performance-max-how-do-you-make-sure-pmax-is-not-going-after-branded-searches/ · **Tier** 1 · **Claim**: PMax takes the query only if no Search keyword exactly matches it (campaign not limited by budget/targeting) and no higher-Ad-Rank keyword matches; close variants must be in the Search campaign. Beltman counter: fails when brand Search is budget-limited. · **Evidence or opinion**: Reading of Google docs plus practitioner counterexample.

5. **Source**: Kirk Williams, ZATO, "How to structure Performance Max campaigns – 7 ideas" — https://zatomarketing.com/blog/how-to-structure-performance-max-campaigns-7-ways · **Tier** 1 · **Date** 2023-08-22, updated 2026-04-21 · **Claim**: PMax "will always cannibalize" eligible Standard Shopping traffic on the same products; still runs both for incremental clicks on core terms. · **Evidence or opinion**: Experience.

6. **Source**: Mike Rhodes, PMax Insights (S.Cat tab, Change History tab) — https://mikerhodes.com.au/scripts/pmax · **Tier** 1 · **Date** 2026 · **Claim**: S.Cat buckets brand/close/non-brand/blank; Change History tab joins change data with performance to date the shift. · **Evidence or opinion**: Published tool.

7. **Source**: Optmyzr, "Google Ads for BFCM 2026" — https://www.optmyzr.com/blog/google-ads-bfcm-2026/ · **Tier** 1 · **Date** 2026-09-22 · **Claim**: In mixed accounts (PMax + Standard Shopping), December ROAS was PMax 680% vs Standard Shopping 666% at identical $0.64 CPCs; PMax-only accounts 798%, Standard-only 625%. · **Evidence or opinion**: 4,200-account data.

8. **Source**: Stewart Dunlop, PPC.io, "Audit Performance Max before you trust its ROAS" — https://ppc.io/blog/performance-max-audit · **Tier** added-Tier-2 (see dossier 55) · **Date** 2026-08-30 · **Claim**: A PMax campaign that only redistributes conversions Search and Shopping already won "has moved the credit and added a fee". Verdict rules: underperforming = non-brand ROAS below the Search baseline for two months → cut budget by half; wait four weeks after fixes before re-auditing. · **Evidence or opinion**: Own-account method; 84 campaigns.

9. **Source**: Navah Hopkins, Optmyzr, "Here's how you can profit from the latest updates to Performance Max" — https://www.optmyzr.com/blog/new-performance-max-updates/ · **Tier** 1 · **Date** 2023-02-28 · **Claim**: Pre-2023 inability to set campaign negatives fed suspicion that branded conversions were credited as non-branded; she called the cannibalisation concern "unfounded" at the time. · **Evidence or opinion**: Opinion (now contradicted by Optmyzr's own 2025 study).

## Dissenting view
Hopkins (2023) called cannibalisation "unfounded"; Optmyzr's own 2025 study and Adalysis 2024 found overlap in 91–97% of accounts, with Search winning on CVR most of the time where there was a difference. Williams (2023) accepts cannibalisation of Standard Shopping as a given and still runs both. The live disagreement is whether overlap equals harm: Vallaeys notes most term comparisons showed no significant difference, and that Search ineligibility (budget, bids, geo) rather than PMax aggression may explain many cases.

## What the platform currently does [Google docs]
- Priority (as quoted by Rooijmans 2022 and Geddes 2024 from Google help): a Search keyword identical to the query takes precedence over PMax; otherwise the ad with the higher Ad Rank serves. Adalysis notes a second help file says phrase/broad keywords can lose to either campaign type.
- PMax search terms report exists (data from March 2023; conversions, clicks, impressions; no cost) — https://support.google.com/google-ads/answer/16327396.
- Channel performance report with cost/conversions by channel for dates after 2025-06-06 — https://support.google.com/google-ads/answer/16260130.
- Brand exclusions (Search, Shopping, YouTube search) and campaign-level negatives (Search and Shopping inventory) are available — https://support.google.com/google-ads/answer/14505308, /answer/15726455.
- Google Ads has no incrementality test for PMax vs Search; experiments exist for PMax vs Standard Shopping/uplift but are not covered here.

## Baseline check
Read `google-ads-keyword-cannibalization` (covers Search-vs-Search overlap, a generic PMax paragraph with the exact-match-wins rule, and a cost formula using CPC gaps) and `google-ads-audit-ecommerce`. This skill adds the published overlap rates and win rates, the eligibility checks (budget, bid floor, geo), the before/after timeline method, and a verdict rule — and drops the CPC-gap cost formula because PMax term cost is not reported.

## Judgment calls
- Verdict thresholds: canon gives only PPC.io's "non-brand ROAS below Search baseline for two months" rule (Tier 2). Adopted, with the Optmyzr 10%-difference significance floor.
- The baseline's CPC-gap cost formula is not usable (no PMax term cost); the skill estimates displaced clicks instead.
- Search ineligibility is treated as the first hypothesis, per Vallaeys' caveat, before blaming PMax.

## Canon strength: Strong

## Invalidated by
A change to the exact-match priority rule; cost appearing in the PMax search terms report; Google shipping campaign-level channel or Search-vs-PMax controls; removal of the PMax search terms report.
