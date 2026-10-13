# Dossier — 30 Campaign-name-as-headline diagnostic trick

Research note: the shared WebSearch budget was exhausted before this row; discovery was limited to direct fetches of known canon URLs. None of the canon pages read for this category (Optmyzr 2022/2024/2026, Adalysis 2022/2023/2026, Vallaeys 2021/2022, Nils Rooijmans' script index, PPC Mastery's newsletter index, Google Ads Help RSA and asset-reporting pages, Google Ads API RSA and customizer pages) describes the trick of putting an identifying string (campaign or ad group name) into a headline, description or display path to see which ad group or campaign a query actually fires from. The practice is widely used but the dossier could not find it published with a method by a canon member, and nothing was written from memory.

## Sources

- **Source:** Google Ads API — "Customize responsive search ads", https://developers.google.com/google-ads/api/docs/ads/customize-responsive-search-ads · **Tier** reference · **Date** read 2026-10 · **Claim:** Custom attributes can be linked at campaign and ad group level with the most specific link winning, and inserted into headlines or descriptions via `{CUSTOMIZER.<name>:<default>}`; display and final URLs don't support replacement. This is the mechanism such a diagnostic could be built on (an ad-group-level attribute carrying a short code), but the page does not describe the use. · **Evidence:** platform documentation.
- **Source:** Brad Geddes, Adalysis — "How to test RSAs", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** The combinations and asset views show what served; nothing about identifying serving ad groups from the SERP. · **Evidence:** n/a to this topic.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** Path fields and brace helpers exist; no diagnostic use described. · **Evidence:** n/a to this topic.

## Dissenting view
None found; no canon source takes a position.

## What the platform currently does [Google docs]
- [Google docs] About RSAs (answer/7684791): two 15-character display path fields exist; H1/H2/D1 are always shown, H3/D2 are not — so an identifier placed in H3 or D2 would not be visible on every impression.
- [Google docs] Google Ads API customizer page: ad-group-level customizer values override campaign-level; URLs cannot carry customizer text.
- [Google docs] Campaign-level asset reporting (answer/9781208): the search terms report, not ads, is where query-to-ad-group attribution normally lives; the page does not cover it. (Noted as context only; the report was not read for this dossier.)

## Baseline check
Read `google-ads-ad-copy` (display-path advice: `[Category]/[CTA]`) and `google-ads-keyword-cannibalization` was not read. Neither baseline describes the diagnostic. There is nothing sourced to add.

## Judgment calls
- Did not reconstruct the trick from general knowledge; the brief forbids it on Thin canon.
- Noted the platform constraints that any future method must respect (only H1/H2/D1 guaranteed; path fields 15 chars; customizer precedence).

## Canon strength: Thin
No Tier 1/2 source on the topic itself.

## Invalidated by
Not applicable until a method exists; any future method depends on the path-field limits and the always-shown slots.
