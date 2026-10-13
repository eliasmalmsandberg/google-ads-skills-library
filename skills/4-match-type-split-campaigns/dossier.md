# Dossier — 4 Match-type-split campaigns with cross-negatives

## Sources

1. **Source**: Brad Geddes (Adalysis), "Google Ads Account Organization" workshop slides — https://presentations.boussiasevents.gr/files/_boussias_conferences_content/presentations/google_marketing_conference/2020/day2/workshop_brad_geddes_googleMKT_20.pdf · **Tier**: 1 · **Date**: 2020 · **Claim**: Campaign-level match-type approach: brand and exact take the maximum budget; the phrase campaign carries exact-match negatives; broad is used to steer budget toward targets. Separate match types into their own ad groups or campaigns only for budget reasons or a different bid method — not for keyword-level bids; under automated bidding, otherwise keep match types together. Keyword matching: in one campaign Google shows the "most exact" match; across campaigns it tries the "most restrictive" but rotates among matches over time, causing duplicate search terms. · **Evidence or opinion**: Method; cross-campaign behaviour from observation.

2. **Source**: Navah Hopkins, Optmyzr, broad vs exact study — https://optmyzr.com/blog/optmyzr-study-broad-match-bidding · **Tier**: 1 · **Date**: 2023-09-27 · **Claim**: 2,637 accounts, same-account comparison: exact better on CPA in 70.79% of accounts (median gap 100.71%), ROAS 72.52% (113.47%), CTR 85.65%, CPC 56.55%, CVR 56.73%; broad better on impressions in 52.89% and marginally on cost share; no CPC discount for broad any more (floor rose ~5–10%). Phrase not tested. Recommend adding broad alongside existing keywords rather than replacing them, and keeping "safety nets" and a separate data-collection budget when testing broad. · **Evidence or opinion**: Cross-account study.

3. **Source**: Fred Vallaeys with Shawn Walker, Optmyzr PPC Town Hall — https://www.optmyzr.com/ppctownhall/practical-advice-on-how-to-actually-make-smart-bidding-work-for-you · **Tier**: 1 · **Date**: 2025-01-29 · **Claim**: A separate campaign is justified only by its own budget, targeting not settable at ad-group level, or materially different performance; ≥30 conversions per campaign per 30 days. · **Evidence or opinion**: Opinion.

4. **Source**: Bacchini/Lolk/Vallaeys, Optmyzr PPC Town Hall "PPC in 2025" — https://www.optmyzr.com/ppctownhall/ppc-in-2025-what-to-stop-start-double-down-on · **Tier**: 2 (Bacchini); Lolk labelled · **Date**: early 2025 · **Claim**: Phrase and close variants make precise control nearly impossible (Lolk); Vallaeys "no bad keyword, only a bad bid"; Lolk: ~80% of split campaigns he sees carry near-identical targets (700/725/715), which makes the split pointless. · **Evidence or opinion**: Opinion/anecdote.

5. **Source**: Gavin Groeneveld (Springbok), Emerce, Hagakure tests — https://www.emerce.nl/cases/google-ads-drie-testen-met-de-hagakure-structuur · **Tier**: Not canon — context · **Date**: 2022-01-20 · **Claim**: "Phrase" is also interpreted broadly by Google; the only broad-match case rose +46% cost with +49% conversions; budgets can rise sharply after loosening match. · **Evidence or opinion**: Three single-account before/afters.

## Dissenting view
Google (answer 14752782) and Vallaeys's "only a bad bid" line say: one ad group, all match types, let the bidder price it; duplicating keywords across match types fragments Smart Bidding data. Geddes allows the split only for budget or bid method. The disagreement is whether a per-match-type *budget* is a legitimate reason to accept data fragmentation; Geddes and Vallaeys/Walker (budget as a valid split reason) say yes, Google says no.

## What the platform currently does [Google docs]
- Close variants on exact (2018–19), phrase absorbing BMM (Feb–Jul 2021); BMM retired. "Phrase" matches loosely (Groeneveld, 2022; Lolk, 2025). [Google docs]
- Google's structure guidance: merge match types into one ad group, then broad only; duplicating a keyword across match types "fragments the data" (answer 14752782). [Google docs]
- Google's keyword-prioritisation help page (answer 9586770) could not be fetched 2026-10-13; the cross-campaign "most restrictive, but rotates" behaviour is Geddes's observation (2020), not a Google statement.

## Baseline check
Read `google-ads-keyword-cannibalization` (Type 2 match-type overlap; cross-campaign negatives) and `google-ads-keywords` headings. Baseline explains overlap and the negative fix. This skill adds the admission rule (only for budget or bid method — Geddes; Vallaeys/Walker), the per-campaign volume floor, the exact-negatives-in-phrase mechanism and the rotation reason for it, the evidence that exact still wins most metrics (Optmyzr 2023), and the Lolk test that most splits have identical targets and should be merged.

## Judgment calls
- Overlaps with skill 1 (alpha/beta). Skill 1 is the harvesting flow; this skill is the standing structure decision: whether to keep match types in separate campaigns at all, and how to wire negatives when you do.
- Phrase campaign is included because the row names it; the canon has no phrase-specific evidence (Optmyzr tested only broad vs exact), and the skill says so.

## Canon strength: Adequate
Geddes (method), Hopkins/Optmyzr (evidence), Vallaeys/Walker (opinion), Bacchini (opinion).

## Invalidated by
Removal of match types (AI Max replacing keywords), shared budgets/targets becoming settable at ad-group level (which removes the only valid reason to split), or Google giving exact strict cross-campaign priority.
