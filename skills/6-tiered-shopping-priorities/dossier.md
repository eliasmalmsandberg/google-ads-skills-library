# Dossier — 6 Tiered campaign priorities for Shopping

## Sources

1. **Source**: Nils Rooijmans, "[AMA] How do you run BRAND campaigns in Shopping?" — https://nilsrooijmans.com/daily/ama-how-do-you-run-brand-campaigns-in-shopping · **Tier**: 1 · **Date**: 2025-11-19 (updated 2026-01-26) · **Claim**: Two-tier priority use: brand Shopping campaign at *low* priority with high CPCs and only the products wanted on brand queries; brand terms as a negative list on all non-brand (high/medium priority) campaigns; three conditions — every brand-campaign product must also sit in the non-brand campaigns; non-brand campaigns must not exhaust budget before brand, or non-brand queries fall through to the low-priority campaign; identical schedule/device/audience/location across tiers. Rejects the "brand campaign broad, script negatives out" inverse (loses money, hits list limits). · **Evidence or opinion**: Method from own accounts, no numbers.

2. **Source**: Nils Rooijmans, "How to add negative keywords to your Performance Max campaigns" — https://nilsrooijmans.com/how-to-add-negative-keywords-to-your-performance-max-campaigns/ · **Tier**: 1 · **Date**: 2025-01-03 (updated 2025-05-02) · **Claim**: Prefers a shared negative list applied to PMax (via the modification request form at the time; per-campaign PMax negatives were in beta); do not use account-level negatives because they hit non-PMax campaigns. · **Evidence or opinion**: Method.

3. **Source**: Andrew Lolk with Julie Bacchini and Fred Vallaeys, Optmyzr PPC Town Hall "PPC in 2025" — https://www.optmyzr.com/ppctownhall/ppc-in-2025-what-to-stop-start-double-down-on · **Tier**: 2 (Bacchini); Lolk not canon, labelled · **Date**: early 2025 · **Claim**: Lolk is "doubling down" on Standard Shopping and sees no reason to prefer feed-only PMax over it; split Shopping campaigns only when categories need different ROAS targets (jeans ~500% vs shoes ~300%); most splits he sees carry identical targets. · **Evidence or opinion**: Opinion/anecdote.

4. **Source**: Maggie Humphrey (Cypress North), Search Engine Land — https://searchengineland.com/separating-brand-non-brand-campaigns-roas-484080 · **Tier**: Not canon (agency) · **Date**: 2026-07-31 · **Claim**: Rebuilt non-brand as Standard Shopping with granular product segmentation, bidding differently by product group and priority; Standard Shopping cannot target brand-only queries, so brand control is negatives + priority + aggressive tROAS + sometimes a portfolio max-CPC cap. · **Evidence or opinion**: Single-account YoY.

5. **Source**: SEL brand-settings write-up — https://searchengineland.com/google-ads-brand-settings-452578 · **Tier**: Reference (Google feature) · **Date**: undated · **Claim**: Brand inclusion/exclusion are not Standard Shopping features (Shopping appears only as a PMax exclusion scope). Nils (2025) confirms brand lists in Standard Shopping was a bug.

6. **Not retrievable on 2026-10-13**: Kirk Williams/ZATO Shopping structure posts (blog index pages 1, 2 and 6 list no structure posts; SEL author page shows a Jan 2019 SMX structure recap and a Sep 2022 PMax/Smart Shopping piece without URLs); Martin Röttgerding's original three-tier "query-level bidding" article (PPC Hero URL failed); Google Ads Help on campaign priority (answers 7101544 and 6275295 — the latter is custom labels). Web search budget was exhausted before Shopping research began.

## Dissenting view
Lolk (2025) argues most Shopping splits are pointless because the targets end up identical; Humphrey (2026) builds granular product-group tiers. The disagreement is whether tiers exist for query routing (Röttgerding/Williams tradition, unretrieved) or for target separation (Lolk) — only the latter is supported by a fetched source, and it is not canon.

## What the platform currently does [Google docs]
- Campaign priority (high/medium/low) decides which Standard Shopping campaign enters the auction for a product before bid; lower priority serves when the higher-priority campaign is out of budget or does not hold the product — this is the mechanism Nils's three conditions guard (Nils, 2025, practitioner description; Google Help page not fetched). [Google docs — unverified this pass]
- PMax takes precedence over Standard Shopping for the same products in the same account (widely stated; not verified from a Google page this pass). [Google docs — unverified]
- Brand lists are not available in Standard Shopping (SEL write-up; Nils, 2025). [Google docs via SEL]
- PMax campaign-level negatives moved from beta toward general availability during 2025 (Nils, 2025).

## Baseline check
Read `google-ads-negative-keywords` and `google-ads-keyword-cannibalization`; neither covers Shopping priorities. The baseline has no Shopping structure skill. What this skill would add: the priority mechanics as a query-routing device, the brand tier (Nils), and the budget-exhaustion failure condition.

## Judgment calls
- Only one canon source (Nils) covers priority tiers, and only the brand tier. The three-tier query-level method the row describes could not be sourced from the canon this pass. Per the brief, the skill is a stub.
- Lolk's and Humphrey's positions are recorded for the practitioner follow-up.

## Canon strength: Thin
One Tier 1 source on the specific mechanism (Nils, brand tier only); Lolk and Humphrey are not canon; Kirk Williams (the canon's Shopping lead) not retrievable.

## Invalidated by
Removal of campaign priority from Standard Shopping, Standard Shopping being retired in favour of PMax, or brand lists becoming available in Standard Shopping.
