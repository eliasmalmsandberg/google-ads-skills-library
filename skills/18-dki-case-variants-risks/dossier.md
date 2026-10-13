# Dossier — 18 Keyword insertion case variants and DKI risks

Research note: WebSearch budget exhausted; sources via sitemaps. No Tier 1 or Tier 2 canon source with a DKI method and evidence was found: Adalysis' RSA handbook does not mention DKI; Optmyzr blog URL guesses failed; searchengineland.com rate-limited; PPC Mastery public material lists no DKI issue. PPC Hero DKI articles were fetched and evaluated against the inclusion rule; they fail it (dated 2007–2016, single-account or no data, no Google disagreement) and are recorded but not added to Tier 2.

## Sources

1. **Source**: Navah Hopkins, SEJ — "How to protect a budget from competitor-branded terms", https://www.searchenginejournal.com/ask-a-ppc-how-to-protect-a-budget-from-competitor-branded-terms/559521/ · **Tier** 1 · **Date** 2025-11-13 · **Claim**: In competitor campaigns, avoid dynamic keyword insertion and keep competitor names out of ad copy. · **Evidence**: assertion; one line in a broader piece.
2. (Not canon, recorded) Carrie, PPC Hero — "4 pitfalls of DKI", https://ppchero.com/4-pitfalls-of-dynamic-keyword-insertion-dki/, 2009-09-22: malformed code (extra space breaks it), misspelled keywords inserted into headlines (isolate misspellings in their own ad group without DKI), DKI with broad match produced irrelevant headlines (use exact), single-keyword headlines look spammy (add fixed text, e.g. "Buy {KeyWord:Red Shoes} Now!"). No data. Fails inclusion rule.
3. (Not canon, recorded) Cassie Oumedian, PPC Hero — "How DKI helped increase impression share by 36%", 2016-07-06: single-account headline test; impression share +36%, IS lost to rank −34%, CPC −20%, CTR +18%, CVR +57%; excluded competitor, misspelling and broad-string ad groups; no baselines or significance; duration stated inconsistently. Fails inclusion rule (single account, no reproducibility).
4. (Not canon, recorded) Joe, PPC Hero — "The quality of DKI", 2007-03-26: DKI doesn't directly affect Quality Score; if you need DKI to get every keyword into the ad, the ad group has too many keywords. No data.

## Dissenting view
Within the non-canon material: Oumedian (2016) reports gains from headline DKI; Carrie (2009) and Joe (2007) treat DKI as a symptom of poor ad-group theming. No canon source takes either side with evidence.

## What the platform currently does [Google docs]
- [Google docs] Keyword insertion inserts the ad group keyword that triggered the ad (not the search term) using `{KeyWord:fallback}`; fallback used when no keyword fits or the keyword is too long for the field; works the same across match types; ads with inserted keywords must comply with policy, especially when using recommended keywords (support.google.com/google-ads/answer/2454041 and /74992, fetched 2026-10-13). Neither page documents the capitalisation codes (keyword / Keyword / KeyWord / KEYWord / KEYWORD) or RSA-specific behaviour — the capitalisation rules commonly cited could not be verified from Google docs in this build.
- [Google docs] Trademark policy page not fetched.

## Baseline check
Read `google-ads-keywords` and `google-ads-ad-copy` (baseline ad copy skill not opened in detail; keywords skill has no DKI content). The baseline library has no DKI guidance; a model's default knowledge covers the capitalisation codes and "use with exact match, tight ad groups" — which is exactly what the canon fails to go beyond.

## Judgment calls
- Thin canon: one line from one Tier 1 source. Stub written per the brief; no skill written from memory.
- PPC Hero material not added to Tier 2.

## Canon strength: Thin
Fewer than 2 Tier 1/2 sources with method on this topic.

## Invalidated by
Google changing keyword insertion syntax or removing it from RSAs; policy changes on inserted trademarks.
