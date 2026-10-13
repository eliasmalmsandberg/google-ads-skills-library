# Dossier — 20 Intent-tier keyword taxonomy with per-tier bidding

Research note: WebSearch budget exhausted; sources via sitemaps. searchengineland.com rate-limited (429). Sophie Fell (Tier 2, B2B intent) could not be located without search.

## Sources

1. **Source**: Brad Geddes, Adalysis — "Working with Google's BMM / phrase match changes", https://adalysis.com/blog/working-with-googles-broad-match-modifier-phrase-match-changes/ · **Tier** 1 · **Date** 2021-02-05 · **Claim**: Intent words move CPA predictably; separate them as keywords with their own bids or negate them; Google detects similar meaning but not similar intent (cost vs quote, trademark vs copyright); Google's CPA bidding doesn't account for intent-driven CVR differences. · **Evidence**: account at ~$450 CPA: "how" > 2×, cost-question queries > $1,000, "quote" < $300, "what" elevated.
2. **Source**: Brad Geddes, Adalysis — "How to steer the machine with negative keywords", https://adalysis.com/blog/how-to-steer-the-machine-with-negative-keywords/ · **Tier** 1 · **Date** 2022-05-17 · **Claim**: Smart Bidding never adjusted bids down for "how" queries despite > 10,000 clicks of data; negatives are the guardrail. · **Evidence**: account CPA ~$300 vs "how" queries > $1,000.
3. **Source**: Brad Geddes, Adalysis — "How to create proper keyword-themed ad groups", https://adalysis.com/blog/how-to-create-proper-keyword-themed-ad-groups-for-google-ads-accounts/ · **Tier** 1 · **Date** 2022-01-18 · **Claim**: Split terms into separate ad groups when the ad or landing page must change; otherwise the split doesn't matter; avoid a separate "near me" campaign because a campaign needs its own budget and data density matters; RSAs don't remove the need for themed groups. · **Evidence**: one-account walkthrough (6,800 terms; 11,512 keywords → 416/174/516 ad groups by sensitivity).
4. **Source**: Brad Geddes, Adalysis — "5 steps before broad match", https://adalysis.com/blog/6-steps-you-should-take-before-using-broad-match-keywords/ · **Tier** 1 · **Date** 2024-04-30 · **Claim**: tCPA/tROAS over Max strategies; mixed-signal ad groups hurt matching. · **Evidence**: experience.
5. **Source**: Navah Hopkins, SEJ — "How to use keyword intent to boost PPC performance", https://www.searchenginejournal.com/keyword-intent-boost-ppc-performance/293997/ · **Tier** 1 · **Date** 2019-05-29 · **Claim**: Plan keywords on auction price × customer journey × volume/value; don't mix keywords with very different auction prices in one campaign because the budget can't serve both; brand and competitor in separate campaigns; match type by word count — 1 word exact only, 2 words exact+phrase, 3 words phrase+exact (+modified broad with care), broad from 5 words. · **Evidence**: 2019 SERP screenshots; opinion.
6. **Source**: Navah Hopkins, SEJ — "Choosing your keyword champion", https://www.searchenginejournal.com/choosing-keyword-champion-setting-up-success-auction/508435/ · **Tier** 1 · **Date** 2024-03-15 · **Claim**: Keep keywords in a campaign close in auction price (budgets are campaign-level); set conversion values (placeholders allowed) and primary/secondary actions so low-value actions don't inflate; compare conversion value to CPA to keep or cut; swap expensive wording for cheaper variants; discovery via DSA/PMax themes/broad with negatives. · **Evidence**: hypothetical lawyer example; no data.
7. **Source**: Miles McNair, PPC Mastery — "TPE #147: The Bottom-Up Funnel", https://www.ppcmastery.com/newsletter/tpe-147-bottom-up-funnel · **Tier** 1 · **Date** 2026-06-22 · **Claim**: Start at bottom-of-funnel (commercial intent: "emergency plumber near me"), expand to mid-funnel research terms ("how to fix a leaking pipe") only when BoFu is maxed; MiFu brings high CTR, lower CVR, longer windows; exceptions: no existing demand, long B2B cycles, prohibitive BoFu CPCs. · **Evidence**: experience since 2018; no data.
8. **Source**: Frederick Vallaeys, Optmyzr — match-type study · **Tier** 1 · **Date** 2026-05-11 · **Claim**: Exact for high-intent/high-value keywords; brand should be exact-led (phrase 8.22% vs exact 8.18% CVR on brand, both ~36% better than broad). · **Evidence**: 30k accounts.
9. **Source**: Frederick Vallaeys, Optmyzr — "When to stop using Smart Bidding" · **Tier** 1 · **Date** 2026-05-28 · **Claim**: Smart Bidding cannot see LTV/margin/deal size; ~50 conv/30 days needed per strategy. · **Evidence**: 14k accounts.

## Dissenting view
Geddes (2022) argues against intent-based campaign splits unless the ad or landing page must change, preferring data density; Hopkins (2019, 2024) splits campaigns by auction price and journey stage so budgets and bids can differ. The disagreement is about the unit of the tier: ad group (Geddes) vs campaign (Hopkins). Smart Bidding's handling of intent is the second disagreement: Google says the bidder learns it; Geddes (2022) shows a case where it never did.

## What the platform currently does [Google docs]
- [Google docs] Bid strategies and budgets are campaign-level; portfolio strategies can span campaigns (general platform behaviour; specific page not fetched).
- [Google docs] Broad match uses landing page and other ad-group keywords as signals (answer/7478529, fetched 2026-10-13) — mixed-intent ad groups contaminate matching.
- [Google docs] Conversion actions can be primary/secondary and carry values; Smart Bidding optimises to primary (general; Hopkins 2024 describes).

## Baseline check
Read `google-ads-keywords` (intent table: transactional/commercial/informational/navigational with "bid aggressively / lower priority") and `google-ads-search-term-mining`. This skill adds the measured CPA multipliers by intent word (Geddes 2021), the rule that Smart Bidding does not reliably price intent (Geddes 2022), the auction-price grouping rule (Hopkins 2019/2024), the match-type-by-word-count rule, the bottom-up expansion order (McNair 2026), the value-setting mechanism for tiered bidding under Smart Bidding, and the split-only-if-ad/LP-changes test.

## Judgment calls
- "Per-tier bidding" under Smart Bidding is implemented through separate campaigns with separate targets or through conversion values, not bid adjustments; this is the synthesis of Hopkins (2024) and Vallaeys (2026) and is labelled as such.
- Unit of tier: Epiminds follows Geddes for ad-group splits inside a campaign and Hopkins for campaign splits only where auction price or budget must differ.

- Review fix (2026-10-13): quarterly re-tier is an Epiminds operating cadence (three monthly n-gram passes before a CPA shift counts as a trend); Geddes 2025 (n-gram classification rules, 'today' example) added to 'Where it comes from'.

## Canon strength: Adequate
Geddes supplies the only numbers (intent-word CPA); Hopkins and McNair supply method without data; Vallaeys supplies supporting cross-account evidence on exact/brand.

## Invalidated by
Removal of campaign-level targets/budgets (e.g. mandatory account-level bidding); Google removing conversion value rules or primary/secondary conversion actions; AI Max replacing keyword-level control in Search.
