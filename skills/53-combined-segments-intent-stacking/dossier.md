# Dossier — 53 Combined segments for intent stacking

Research note: shared WebSearch budget was exhausted before this row; sourcing was by direct fetch of canon archives (Optmyzr, Adalysis, Brainlabs, Nils Rooijmans, PPC Mastery, ZATO pages 1–7, Search Engine Land author archives for Cruz, Hopkins, Vallaeys, Levy, Williams). None has a piece on combined segments. Google's combined-segments help page (answer/9389231) failed to fetch on three URL variants, so even the platform section below is partial.

## Sources

No canon source addresses combined segments (AND/OR/NOT audience logic) directly. Adjacent material only:

1. **Source**: Andrea Cruz, Search Engine Land, "What are you optimizing for in paid search when keywords matter less?", https://searchengineland.com/what-are-you-optimizing-for-in-paid-search-when-keywords-matter-less-475565 · **Tier** 1 · **Date** 2026-04-27 · **Claim**: Cluster people by shared pain point rather than one-to-one list matching; example of bidding on an IT director who has researched SOC 2 compliance — intent stacking as a concept, not as a combined-segment configuration. · **Evidence or opinion**: Opinion.
2. **Source**: Navah Hopkins, Search Engine Land, "A PPC guide to permission-based audiences", https://searchengineland.com/a-ppc-guide-to-permission-based-audiences-391228 · **Tier** 1 · **Date** 2023-01-12 · **Claim**: Targeting only native audiences in observation forfeits Smart Bidding's built-in audiences; exclude and let Smart Bidding work. Implies stacked restriction is counter-productive under Smart Bidding, but does not discuss combined segments. · **Evidence or opinion**: Opinion.
3. **Source**: Miles McNair, PPC Mastery, TPE #145, https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: Conversion value rules allow one secondary condition (both must hold) — the only AND logic a canon source describes, and it is for value, not targeting. · **Evidence or opinion**: Method.

## Dissenting view
None available on the topic itself. The nearest tension is Hopkins (2023) — don't restrict native audiences under Smart Bidding — against the premise of the row, which is to restrict harder with AND/NOT logic.

## What the platform currently does [Google docs]
- Search campaigns can use affinity, in-market, detailed demographics and your-data segments; custom segments and life events are not available on Search. (https://support.google.com/google-ads/answer/2497941)
- Audience segments can be excluded on Search, Display, Shopping, Video, Demand Gen and PMax at campaign or ad-group level; exclusions apply to first-party data and may not reach users opted out of ads personalization. (2549058)
- Lookalike segments exist only in Demand Gen and since Feb 2026 act as a signal, not a boundary (ZATO reporting 2026-04-21; 2497941).
- Combined segments page (9389231) could not be fetched; its current AND/OR/NOT mechanics and campaign-type availability are unverified in this dossier.

## Baseline check
Read `google-ads-audiences`: it gives two "combined list" examples (pricing visitors NOT purchasers; demo visitors NOT Customer Match customers). That is already what a model produces unprompted; nothing in the canon fetched here takes it further.

## Judgment calls
- Did not write the skill from memory. Combined-segment mechanics (which types can be ANDed on Search vs Display, the Demand Gen rules, observation availability) are exactly the kind of platform detail that drifts, and no practitioner source gives a method or a result for intent stacking.

## Canon strength: Thin
Zero canon sources on the topic; three adjacent sources with no method for combined segments.

## Invalidated by
Any change to combined-segment availability by campaign type or to the AND/OR/NOT rules; Search gaining custom segments.
