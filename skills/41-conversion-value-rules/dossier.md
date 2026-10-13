# Dossier — 41 Conversion value rules

## Sources

1. **Source**: Frederick Vallaeys, Optmyzr — "All about Value Rules: bid adjustments for Smart Bidding", https://www.optmyzr.com/blog/bid-adjustments-back-smart-bidding-google · **Tier** 1 · **Date** 2021-08-23 (FAQ 2021-08-26) · **Claim**: A rule changes the conversion *value* Google sees, so under tROAS it behaves like a bid adjustment (2× value at 200% tROAS → 2× bid, $5→$10 in his example). Using rules to replicate geo/device bid adjustments is a mistake: Google already learns those conversion-rate differences from tracking, so you stack adjustments and bid wrong. A good rule is based on something you haven't told Google — LTV, store value, margin. Rules affect bidding only on tROAS, Max Conversion Value (and Smart Shopping then); reported conversion values change account-wide, which breaks stakeholder reports unless agreed up front; not restated backwards; "Value rule adjustment" segment shows originals. Ordering: most granular location wins; audiences checked Customer Match → remarketing → affinity/in-market → demographics; ties go to multiply over add, then larger. At most two segment types per rule set. Multiplier 0.5×–10×, or add a fixed amount. Less precise than offline value import, but simpler. · **Evidence**: illustrative maths; no account data.

2. **Source**: Sarah Vlietstra, ZATO — "Precision bidding: how to use conversion value rules effectively", https://zatomarketing.com/blog/precision-bidding-how-to-use-conversion-value-rules-effectively · **Tier** 1 outlet (ZATO; cited outside its strongest topic) · **Date** 2026-10-07 · **Claim**: Rules take one condition, or two where both must be met; add or multiply; multiply <1 to decrease (e.g. demote existing remarketing-list users). Use device for B2B where device signals lead value, location where AOV differs, audiences for lifecycle. "Limited benefit"; only give Google information it hasn't already figured out. Report via "Value rule adjustment" segment or the "Original conv. value (rule applied / no rule applied)" columns. · **Evidence**: none quantitative.

3. **Source**: Ginny Marvin (Google Ads Liaison), Search Engine Journal — "Assigning conversion values to make VBB work for lead gen", https://searchenginejournal.com/assigning-conversion-values-to-make-value-based-bidding-work-for-lead-gen/526349 · **Tier** Reference only · **Date** 2024-09-11 · **Claim**: Rules adjust by location, audience (first-party or Google lists) or device; account or campaign level; Search, Shopping, Display, PMax; start with a few rules on the most critical attributes; "rules are additive, so overlapping rules combine"; same adjusted value appears in reporting; revisit regularly. · **Evidence**: vendor, hypothetical.

4. **Source**: Google Ads API docs — "Conversion value rules", https://developers.google.com/google-ads/api/docs/conversions/conversion-value-rules · **Tier** Reference only · **Date** page updated 2026-10-06 (v25) · **Claim**: Conditions: audience, device, geo, itinerary (allowlist only), no-condition. ADD (>0), MULTIPLY (0.5–10 inclusive), SET (allowlist/store-only). At most one rule applies per conversion: campaign-level set beats customer-level; set with matching conversion category beats empty; first matching rule in list order; geo most precise wins; audience hierarchy, ties multiply > add > larger multiplier. `conversions_value` and `all_conversions_value` reflect the rule. A rule set holds at most two dimensions. · **Evidence**: documentation.

5. **Source**: Ashwin Balakrishnan, Optmyzr — "Conversion value tools", https://www.optmyzr.com/blog/conversion-value-tools/ · **Tier** 1 outlet, product content (cite with care) · **Date** 2022-03-28 · **Claim**: Values should be based on context Google doesn't capture (margin, deal size, LTV); requires Max Conversion Value with or without tROAS; a 1–5 segment score relative to the average conversion drives the multiplier. · **Evidence**: product description.

6. **Source**: Miles McNair, PPC Mastery — "TPE #145: Why bid adjustments are dead", https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: Under Smart Bidding most bid adjustments are ignored; value rules are the replacement for geo/device/audience adjustments but only on Max Conversion Value and tROAS — they do nothing on Max Conversions or tCPA. Only one value rule applies per conversion; audience priority Customer Match → your data/similar → affinity/in-market → demographics. Example 1.2× multiplier. · **Evidence**: Google's support table; no data.

7. **Source**: Navah Hopkins, Optmyzr — "Impact of PPC bidding strategies", https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier** 1 · **Date** 2024-09-24 · **Claim**: 50+ conversions/30 days is the floor for predictable Smart Bidding behaviour. · **Evidence**: 14,584-account study.

## Dissenting view
Marvin (Google) presents value rules as a first-line lever for lead gen ("start with a few basic rules on the most critical attributes"). Vallaeys (2021) and Vlietstra (2026) both say the benefit is limited and that most of what advertisers want to encode (geo and device conversion-rate differences) Google already knows — rules only add information when they carry something off-platform. The disagreement is whether a rule is a bid adjustment (Google's framing to ex-manual bidders) or a value correction (the practitioner framing).

## What the platform currently does [Google docs]
- [Google docs] Conditions: geo, device, audience, itinerary (allowlisted); multiply 0.5–10×, add >0; at most two dimensions per set; at most one rule applies per conversion with the precedence order above (API docs, 2026-10-06).
- [Google docs] Adjusted values flow into reported conversion value and all derived metrics; segment "Value rule adjustment" exposes original vs adjusted (API docs 2026; Vallaeys 2021).
- [Google docs] Rules affect bidding on value-based strategies only — Max Conversion Value / tROAS (Vallaeys 2021 FAQ; Balakrishnan 2022); apply to Search, Shopping, Display, PMax (Marvin 2024).
- [Google docs] Discrepancy to flag: Marvin (2024) says overlapping rules are "additive"; the API doc (2026) says at most one rule applies per conversion with precedence. Treat the API doc as current.

## Baseline check
Read `google-ads-bidding` (bid adjustments section: "with Smart Bidding device adjustments are mostly overridden") and `google-ads-conversion-tracking`. Baseline does not mention conversion value rules at all. This skill adds the mechanism (value → bid under tROAS), the stacking trap, the "only what Google doesn't know" qualification rule, the precedence order, the 0.5–10× range, the reporting side-effect and the reporting columns.

## Judgment calls
- Canon strength is Adequate on sources but the evidence is method-only — no practitioner has published account results for value rules. The skill says so and treats rules as a low-risk, low-benefit lever.
- Took the position that the only defensible rules are (a) off-platform value differences (margin, LTV, deal size by segment/geo) and (b) demotion multipliers (<1×) for existing customers / low-value audiences; geo/device uplift rules copied from old bid adjustments are refused.
- Index row says "favour an audience/location/device without splitting campaigns"; the skill reframes that: favour only where the *value* differs, not the conversion rate.

## Canon strength: Adequate
Two Tier 1 sources with method (Vallaeys; Vlietstra/ZATO), Google docs for mechanism; no account evidence anywhere in the canon.

## Invalidated by
Google changing the multiplier range, the two-dimension limit, the one-rule-per-conversion precedence, or extending rules to non-value bid strategies.
