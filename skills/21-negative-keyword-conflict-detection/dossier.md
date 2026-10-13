# Dossier — 21 Negative keyword conflict detection

Research note: WebSearch budget exhausted; sources via sitemaps. Google's original Negative Keyword Conflicts script page (developers.google.com) was not fetched; it is cited through Rooijmans' published modification. Nils' "enhanced version" note page was not fetched separately.

## Sources

1. **Source**: Nils Rooijmans — "Negative keyword conflicts alert script – update" (v2.1.1), https://nilsrooijmans.com/negative-keyword-conflicts-alert-script-update/ · **Tier** 1 · **Date** 2023-07-24, modified 2025-05-27 · **Claim**: Modified Google's conflicts script to check only serving campaigns (Google's version also flagged ended campaigns → false alerts). Checks enabled positives in enabled ad groups/campaigns against campaign negatives, ad-group negatives and shared lists attached to enabled campaigns; normalises case/whitespace/punctuation and strips "+"; logic: broad positive blocked only by broad negative whose tokens all appear in any order; phrase positive blocked by phrase or broad negatives (phrase = contiguous in-order); exact positive blocked by any negative type whose text matches. Limits 250,000 positives / 50,000 negatives. Output sheet: customer ID, negative, conflict level, blocked positives, campaign, ad group, list name; email "Negative Keyword Conflicts Found". Uses yesterday's data (implies daily run). · **Evidence**: published script.
2. **Source**: Brad Geddes, Adalysis — "How to diagnose and work with keyword conflicts", https://adalysis.com/blog/diagnose-work-keyword-conflicts/ · **Tier** 1 · **Date** 2017-05-04 · **Claim**: Conflict = a negative blocking an active keyword; Google's alerts miss conflicts because they ignore campaign negative lists and don't always catch ad group/campaign conflicts; manual route = find ad groups with fewer impressions than expected; conflicts can hide because variants (misspellings, "run" vs "running") still get impressions; use campaign-level n-grams to check whether a negated word fails everywhere. · **Evidence**: examples (-Blue vs "Blue shoes"; "Cheap running shoes" vs -running); no rates.
3. **Source**: Brad Geddes, Adalysis — "Find and fix common negative keyword problems", https://adalysis.com/blog/find-fix-common-negative-keyword-problems-ppc-accounts/ · **Tier** 1 · **Date** 2017-02-23 · **Claim**: Causes: campaign negative added for a query from a different ad group/match type; root words added without n-gram check; standard lists applied blindly; shared lists attached to the wrong campaigns; "+" in negatives is malformed. Detection: pivot of negatives/lists per campaign; conflict reports (Bing has one; Google's checks only campaign/ad-group negatives); n-grams. · **Evidence**: [Plasma TV] vs -TV example; campaign negative counts 112/894/396/112.
4. **Source**: Brad Geddes, Adalysis — "How to work with the latest match type changes", https://adalysis.com/blog/how-to-work-with-the-latest-google-ads-match-type-changes/ · **Tier** 1 · **Date** 2019-09-24 · **Claim**: Monitor conflicts especially across multiple negative lists — the author has never seen an account with two lists that had none. · **Evidence**: experience statement.
5. **Source**: Brad Geddes, Adalysis — "How to steer the machine with negative keywords" · **Tier** 1 · **Date** 2022-05-17 · **Claim**: Workflow order n-grams → duplicates → conflicts; Google's conflict recommendations ignore match types and campaign lists. · **Evidence**: experience.
6. **Source**: Navah Hopkins, SEJ — "How to use negative keywords in paid search campaigns" · **Tier** 1 · **Date** 2020-05-12 · **Claim**: Negatives do not account for close variants (so a conflict check on literal text understates real blocking and overstates in some cases). · **Evidence**: reasoning.

## Dissenting view
No canon source argues against conflict checks. The disagreement is about tooling and scope: Google's built-in recommendation (ignores lists and match types per Geddes 2017/2022) vs a script or tool that includes shared lists; and whether literal-text matching is enough given close variants (Hopkins 2020: a negative may not block a variant the keyword still matches, so "conflict" ≠ "no impressions").

## What the platform currently does [Google docs]
- [Google docs] Negative match: broad = all words any order; phrase = words in order; exact = whole query; no close variants/expansions; plurals/synonyms manual; misspellings and casing automatic (answer/2453972, fetched 2026-10-13). The automatic-misspelling line is newer than the scripts' logic, which matches literal text.
- Google Ads Scripts "Negative Keyword Conflicts" solution exists (not fetched); Rooijmans 2023 documents its limits and his fork.
- [Google docs] Low search volume and zero-impression auto-pausing (13 months, from 11 Mar 2024 per Hopkins/SEJ 2024) are alternative explanations for keywords without impressions.

## Baseline check
Read `google-ads-negative-keywords` (quarterly "check if any negatives are accidentally blocking converting queries"). This skill adds the match-type logic of a conflict, the three levels plus shared lists, the Google-recommendation gap, the serving-campaign false-positive fix, the malformed "+" check, the variant blind spot, and a triage rule for what to change (negative vs keyword).

## Judgment calls
- Cadence: Rooijmans' script uses yesterday's data (daily); the index row says monthly. Epiminds runs the script daily for alerts and does the human review monthly.
- Misspelling handling: Google now says negatives block misspellings automatically; the script's literal match will miss conflicts caused by that. The skill flags it as a known blind spot rather than inventing logic.

## Canon strength: Adequate
One published script with explicit logic, three Geddes posts with method; evidence is example-based, no cross-account rates.

## Invalidated by
Negatives starting to match close variants/synonyms (changes the conflict definition); Scripts API changes breaking the keyword/negative/shared-set queries; Google's conflict recommendation starting to include shared lists and match types.
