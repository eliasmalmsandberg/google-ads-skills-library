---
name: title-structure-research
id: 66
description: What the published evidence actually says about Shopping title structure and CTR, and the protocol for finding out in a given account. Use when Shopping CTR is low and titles are generic. Not for the mechanics of applying title changes (65) or for description/product_type work.
tags: Research / Shopping / Optimise / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google changing the ~70-character displayed cut-off or the 150-character title limit, AI Max / dynamic titles overriding merchant titles by default, or Merchant Center removing attribute rules and supplemental sources (the test mechanism).
---
## What this is
A research brief, not a template. The published, methodology-bearing evidence on Shopping titles is thin: one controlled test (CommerceHub, 2016), the practitioners' working rules (Williams/ZATO, 2025–2026), and a tool method for mining your own titles (Rhodes, 2026). The large CTR-lift numbers circulating online come from feed-tool vendors without a stated method and are excluded here. The position: titles are built from the account's own converting search terms, front-loaded to the ~70-character display cut, and every structural rule is tested half/half before rollout.

## Where it comes from
Kirk Williams' title guide and feed-first posts (ZATO, 2025–2026); Mike Rhodes' PMax Insights Title and nGram tabs (Rhodes, 2026); Brianna Harlow's CommerceHub title tests on PPC Hero (CommerceHub, 2016, admitted as Tier 2 for this topic because it publishes a controlled test). Google's `title` spec is used only for limits and display behaviour.

## When to use it / when not to
Use when Shopping or PMax feed CTR is below the account's historical level, titles are SKU-like or generic ("Men's Shirt"), or variants share one title. Do not start here when the problem is price (ZATO: offer, pricing and CVR outrank the feed for business results) (Williams/ZATO, 2026), when products are disapproved or limited (run 67 first), or on a catalogue under a few hundred SKUs where half/half tests will not reach a read in 2–4 weeks (Williams/ZATO, 2025).

## Inputs
- Search-term report for Shopping/PMax, last 90 days, with conversions by term (Williams/ZATO, 2025).
- Product performance by title and by title n-gram: cost, conversions, ROAS per 1-, 2-, 3-word phrase (Rhodes, 2026).
- Current titles with character counts; the display cut is ~70 characters, fewer on mobile (Williams/ZATO, 2025) [Google docs: 150 max, ~70 shown].
- Access to attribute rules or a supplemental source to change titles on a subset (Williams/ZATO, 2025).

## Method
1. **Establish what is known, and what is not.** Evidence that passes the inclusion rule: (a) removing "women's" from titles in women-only categories, half/half with control over 70 days, produced ~5% more revenue per day than expected (CommerceHub, 2016); (b) standard colour words beat boutique ones for query volume — "yellow flats" had >10× the searches of "mustard flats" and the product still surfaced for "mustard" (CommerceHub, 2016); (c) brand-first suits resellers, brand-last suits manufacturers because the seller name already shows in the ad (CommerceHub, 2016); (d) words placed past ~70 characters are not seen before the click (Williams/ZATO, 2025). Not evidenced in any source that passes the rule: a universal attribute order, an optimal length, or a CTR multiplier. Do not promise one.
2. **Mine the account's own words.** Pull converting search terms; the language that converts goes to the front of the title (Williams/ZATO, 2025). Run the n-gram split on existing titles and rank 1–3-word phrases by ROAS and cost; phrases that sit with high ROAS are candidates to promote, phrases that sit with cost and no conversions are candidates to drop (Rhodes, 2026). Treat this as pattern, not cause — it tells you what to test (Rhodes, 2026).
3. **Write by vertical, not by template.** Specialist goods take model-level specificity ("Trek Domane SL 5 Disc", not "Trek Road Bike"); commodity apparel takes attribute-first language ("Gore-Tex Hiking Boots" before brand) (Williams/ZATO, 2025). Apply the two evidenced structural rules: drop gender in single-gender categories; normalise colours to standard names (CommerceHub, 2016). Place brand by seller type: reseller first, manufacturer last (CommerceHub, 2016).
4. **Front-load.** Everything that decides the click sits inside the first 70 characters; use the rest for variant and secondary attributes (Williams/ZATO, 2025) [Google docs]. Stay inside Google's prohibited-content list (no price, promo, caps, symbols) [Google docs].
5. **Test half/half.** Pick one brand or product type, apply the new titles to half the products via attribute rule or supplemental source, leave the other half untouched, compare CTR and impressions after 2–4 weeks (Williams/ZATO, 2025). The CommerceHub test ran 70 days and measured revenue per day against expectation (CommerceHub, 2016); for small groups use the longer window.
6. **Decide and roll.** If CTR and impressions rise on the treated half, roll to the control half (CommerceHub, 2016). If impressions fall while CTR rises, hold for the full window before judging; a drop in CTR or CVR right after a feed change is itself a diagnostic (Williams/ZATO, 2026).
7. **Record the rule you learned** per vertical in the account's feed notes; the next title round starts from step 2, not from a template.

## What Google will tell you instead, and why we don't
Google's spec shows fixed example formats (apparel: name, size, colour; electronics: brand, model, storage, colour) and promotes "automatic title improvements" that rewrite your title from landing-page signals [Google docs]. We write from the account's converting queries instead of a format, because a template that fits a t-shirt does not fit a road bike (Williams/ZATO, 2025), and we test rather than assume: the one controlled test on record removed a word Google's apparel examples would keep (CommerceHub, 2016). Google's own spec concedes dynamic titles make no change when your title already best fits the query [Google docs], which is the argument for doing this work rather than leaving it to Google.

## Failure modes
- **Trusting vendor lift numbers.** "200–300% CTR" claims come without method or control; using them as a target sets up a failed project (dossier exclusion of Peghin/PPC Hero, 2026).
- **Low-volume catalogues.** Half/half on a 40-SKU brand will not separate in 2–4 weeks; extend toward the 70-day window or test at category level (CommerceHub, 2016; Williams/ZATO, 2025).
- **Keyword stuffing.** Titles that read as a keyword list lose the human reader; Williams' two-audience rule is explicit that the goals conflict (Williams/ZATO, 2025).
- **Variants sharing a title.** The Title tab aggregates by distinct title, so variant performance hides; use the ID tab before deciding a title is bad (Rhodes, 2026).
- **AI Max for Shopping accounts.** Text customisation rewrites titles to the query; title-structure tests may read noisy there, and whether the manual work still matters is an open question (Vlietstra/ZATO, 2026).
- **Changing titles during a disapproval or migration spike.** CTR movement will be confounded (Williams/ZATO, 2026).

## What to measure
- CTR and impressions, treated half vs control half, 2–4 weeks (Williams/ZATO, 2025); revenue per day vs expected over 70 days for the longer read (CommerceHub, 2016).
- n-gram ROAS table before and after (Rhodes, 2026).
- Share of titles inside 70 characters for the deciding words (Williams/ZATO, 2025).
- CTR/CVR drop alerts after any feed change (Williams/ZATO, 2026).

## Open disagreements in the canon
- **Does title structure still matter under AI Max / dynamic titles?** Vlietstra says it may become obsolete and needs testing (ZATO, 2026); Williams keeps titles as the primary lever (ZATO, 2026). We keep doing the work, because Google only rewrites when your title is not the best fit [Google docs], and we re-test it in AI Max accounts.
- **Brand first or last.** CommerceHub splits by seller type (2016); Google's examples lead with brand for electronics [Google docs]. We follow CommerceHub's split and test it per account.
