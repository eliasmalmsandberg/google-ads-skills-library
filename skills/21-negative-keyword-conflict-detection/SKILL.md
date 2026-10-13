---
name: negative-keyword-conflict-detection
id: 21
description: Find negatives at any level, including shared lists, that block active keywords, and decide whether the negative or the keyword is wrong. Use after impression drops that follow negative additions and as routine hygiene. Not a wasted-spend review (skill 10) and not a low-search-volume diagnostic (skill 19), though both are alternative explanations for missing impressions.
tags: Diagnostic / Search / Diagnose / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Negatives starting to match close variants or synonyms (changes what a conflict is); Google Ads Scripts API changes breaking keyword/negative/shared-set queries; Google's built-in conflict recommendation starting to cover shared lists and match types.
---
## What this is
A conflict is a negative keyword blocking an active keyword you want to run (Geddes/Adalysis, 2017). They are common in any account with more than one negative list — Geddes has never seen an account with two lists that had none (Adalysis, 2019) — and Google's own conflict recommendation misses many because it ignores shared lists and match types (Geddes/Adalysis, 2017, 2022). The check is a literal-text comparison of every enabled keyword against every negative at ad-group, campaign and shared-list level, applying the negative's match-type logic (Rooijmans, 2023), followed by a triage of which side to fix.
See also: skill 74 (negative-keyword-conflict-script) — installing and triaging Rooijmans's v2.1.1 fork of the conflict script and pairing it with the conversion watchdog.

## Where it comes from
Nils Rooijmans' fork of Google's Negative Keyword Conflicts script, with its matching logic and the fix for false alerts from ended campaigns (2023, maintained 2025); Brad Geddes' conflict diagnosis and common-cause posts (Adalysis, 2017 ×2, 2019, 2022); Navah Hopkins on negatives and close variants (SEJ, 2020).

## When to use it / when not to
Run the script daily and review monthly; run the review immediately when impressions drop on a keyword or ad group after negatives were added, after applying a shared list to new campaigns, after an n-gram root-negative batch, and after any import from Microsoft Ads or a template list. Do not treat "no impressions" as proof of a conflict — low search volume and the 13-month zero-impression auto-pause are separate causes (skill 19; Hopkins/SEJ, 2024). Do not run the check against ended or paused campaigns; that is where Google's original script produced false alerts (Rooijmans, 2023).

## Inputs
- Enabled keywords in enabled ad groups in serving campaigns (status and match type).
- Negatives at ad-group and campaign level, and shared negative lists with the campaigns they are attached to.
- Keyword impressions, last 30 days vs prior 30 (for the impact ranking).
- Change history for negative additions (to date the conflict).

## Method
1. **Normalise** both sides: lowercase, collapse whitespace, strip phrase/exact punctuation, remove any "+" (Rooijmans, 2023). A "+" inside a negative is itself a defect — it was copied from old modified-broad keywords and may not block anything; list these separately (Geddes/Adalysis, 2017).
2. **Apply match logic** per pair (Rooijmans, 2023):
   - Broad positive is blocked only by a broad negative whose tokens all appear in the keyword, in any order.
   - Phrase positive is blocked by a phrase negative whose words appear contiguously in order, or by a broad negative whose tokens all appear.
   - Exact positive is blocked by any negative type whose text matches it.
   Only negatives in scope count: the ad group's own, the campaign's, and shared lists attached to that campaign (Rooijmans, 2023; Geddes/Adalysis, 2017).
3. **Rank by impact.** Sort conflicts by the blocked keyword's prior-period impressions and conversions; a conflict on a keyword that never had impressions is lower priority than one that converted last quarter (Geddes/Adalysis, 2017: conflicts often block keywords with past conversions).
4. **Confirm.** Check the ad group's impressions against expectation (Geddes/Adalysis, 2017); a blocked keyword may still show impressions through variants the negative does not cover ("cheap run shoes", misspellings), so impressions are not proof the conflict is harmless (Geddes/Adalysis, 2017; Hopkins/SEJ, 2020).
5. **Triage — which side is wrong** (Geddes/Adalysis, 2017):
   - Negative added at campaign level for a query that belonged to one ad group → move it to that ad group.
   - Root-word negative added without an n-gram check → run the campaign-level n-gram (skill 10); if the word converts anywhere in the campaign, narrow the negative to a 2–3-word phrase (Hopkins/SEJ, 2022 via skill 10).
   - Template/standard list applied blindly or attached to the wrong campaign → detach or split the list (Geddes/Adalysis, 2017).
   - Routing negative that is doing its job (the keyword exists in the owning campaign) → the duplicate keyword is wrong; pause it (Geddes/Adalysis, 2019; skill 12).
   - Keyword that should never have been added (off-theme) → remove the keyword, keep the negative.
6. **Fix and log.** Record negative, level, list, blocked keyword and the decision; re-run the script next day to confirm the conflict is gone.
7. **Consistency pass, monthly.** Pivot negative counts per campaign and per list (Geddes' example: 112 / 894 / 396 / 112 across nine campaigns signals inconsistent application); move account-wide negatives into one shared list, keep separate lists only where campaign types need different sets (Geddes/Adalysis, 2017).

## What Google will tell you instead, and why we don't
Google's built-in conflict recommendation covers campaign and ad-group negatives but not shared lists, and ignores match types (Geddes/Adalysis, 2017, 2022); its own script flagged keywords in ended campaigns (Rooijmans, 2023). We run the forked script over serving campaigns with all three levels and match-type logic, and we do the triage ourselves because the correct fix is as often "pause the duplicate keyword" as "remove the negative" (Geddes/Adalysis, 2019). Google's negative-keyword page also says "too many negatives" reduce reach; our view is that the reach lost to a conflict is the only kind that matters, and the fix is accuracy, not fewer negatives.

## Failure modes
- **Close variants.** Negatives don't match variants (Google docs, 2026; Hopkins/SEJ, 2020), so a literal-text check can report a conflict on a keyword that still serves via variants, and miss blocking that happens through the newer automatic misspelling matching (Google docs, 2026). Treat the script output as candidates, confirm with impressions.
- **Very large accounts.** The script stops above 250,000 positives or 50,000 negatives (Rooijmans, 2023); scope by campaign label.
- **Ended or seasonal campaigns.** Excluded by design; re-run when they are re-enabled (Rooijmans, 2023).
- **Ad groups with repeated identical negative sets.** One example had the same negatives in 10,000 ad groups; conflicts multiply and limits are hit — move them up a level before chasing each conflict (Geddes/Adalysis, 2017).
- **Mistaking LSV or auto-pause for a conflict.** Zero impressions have other causes (skill 19).
- **Microsoft imports.** Microsoft has no broad negatives (Hopkins/SEJ, 2022); conflicts differ per platform.

## What to measure
- Conflicts found per run, by level and by list.
- Impressions and conversions on keywords released from conflicts in the following 30 days.
- Count of "+" malformed negatives (target zero).
- Negative count per campaign and per list, variance across campaigns (Geddes/Adalysis, 2017).
- Share of conflicts resolved by pausing a duplicate keyword vs editing a negative (a high keyword share means routing is working).

## Open disagreements in the canon
- **Cadence.** Rooijmans' script reads yesterday's data, implying daily; Geddes frames it as routine management without a frequency. Epiminds: daily alert, monthly review.
- **Tool vs script.** Adalysis scans automatically; the script is free. Epiminds uses the script by default and the same logic regardless of tool.
- **Literal vs variant-aware matching.** No canon source has published variant-aware conflict logic; until one does, the literal check plus impression confirmation is the method.
