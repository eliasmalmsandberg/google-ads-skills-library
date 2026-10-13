---
name: keyword-level-ad-customizers
id: 28
description: When and how to use keyword-level ad customizers for 1:1 price or variant copy at scale, with the precedence and fallback rules and the test that decides whether they earn their conversion cost. Not for countdowns, location or feed-driven copy (29) or plain keyword insertion (23 says don't).
tags: Technique / Search / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: Changes to customizer precedence or the 40-attribute cap; removal of keyword-level customizers; AI Max text customisation overriding advertiser customizer values.
---
## What this is
A gating rule and setup spec for keyword-level customizers. The platform lets one attribute carry a different value per keyword, with the keyword value overriding ad group, campaign and account values. The evidence says customised and inserted text buys impressions and loses conversions in aggregate, so the skill allows it only where the value genuinely differs by keyword (price, model, size) and only under a labelled test.

## Where it comes from
Optmyzr's 2022 study (432,343 ads: DKI and customizers raised impressions, lowered conversions), Vallaeys (Search Engine Land, 2022), Brad Geddes / Adalysis (2026 cross-ad-group tests on keyword insertion and price patterns; 2022 creation series), Vallaeys / Optmyzr 2026 (headline-length effect). Mechanics from the Google Ads API documentation, labelled.

## When to use it / when not to
Use when an ad group holds many keywords whose correct headline differs by a value you hold in a sheet — price, monthly cost, model number, pack size, rate — and the alternative is hundreds of single-keyword ad groups. Do not use it for relevance (echoing the query), as a substitute for writing (skill 23), or in ad groups below the combination data budget (skill 22), where you could not read the result anyway.

## Inputs
- A keyword list with one value per keyword for each attribute (price/number/percent/text), and a default value that fits the 30/90 limit on its own.
- Ad group volume (impressions per combination, skill 22) and a baseline hand-written RSA.
- Label scheme for the test (skill 22 rule 6).

## Method
1. **Qualify the use case.** Proceed only if (a) the ad group or campaign clears the skill-22 data budget (well over 100 impressions per combination; Geddes/Adalysis, 2022) so the result can be read, and the value differs across enough keywords that each would otherwise need its own ad group — Epiminds operating threshold, no canon source for a keyword count; reason: below the data budget no customizer effect is readable, and above it the test in rule 6 decides, so a fixed count adds nothing — (b) the value changes often enough that hand-editing would miss updates, and (c) the value is a buying fact (price, spec), not a phrase. Keyword insertion, which only echoes the query, lost on CTR and CVR in Geddes' 2026 pattern test and is excluded by skill 23.
2. **Model the precedence before building.** Attributes link at account, campaign, ad group and keyword level; one link per level; the most specific wins (Google Ads API docs). So set the account or campaign value to the safe generic ("from €29/mo"), the ad group value where the group shares a price, and keyword values only where they differ. Up to 40 enabled attributes per account (Google Ads API docs); name them broadly ("Price", "Model") so they are reused, not multiplied.
3. **Write the default to survive on its own.** The fallback is used when the inserted value is too long or invalid, but only if the default itself fits the character limit including surrounding text (Google Ads API docs); an RSA whose customizers lack usable fallbacks can be rejected outright (Google Ads API RSA overview). Rule: the headline with the default inserted must be ≤30 characters and must read as a complete, truthful line.
4. **Keep the customised headline short.** The 30-character cap includes the inserted value (Google Ads API docs). Headlines under 20 characters had CPA $9.35 vs $18.27 for longer ones (Vallaeys/Optmyzr, 2026), so keep the whole rendered headline under 20 characters: with a typical price value of 6–8 characters ("€29/mo", "SEK 299"), that leaves roughly 12 characters for the fixed template text — arithmetic from the Vallaeys finding, not a separate threshold. Check the length with the longest live value and with the default inserted ("Only {CUSTOMIZER.Price:€29}"), rather than filling to 30.
5. **Price format.** Currency symbol or code before or after the number, no space before the number (Google Ads API docs). Store values in the exact display form; do not rely on the platform to format.
6. **Build it as a test, not a rollout.** Copy the baseline hand-written RSA under a second label and add the customised headline(s) as a second RSA or as replacement assets in one labelled set, across the same number of ad groups per version, brand excluded (Geddes/Adalysis, 2026). Judge on conversions or conversion value per impression, not CTR — the documented pattern is more impressions, fewer conversions per ad (Optmyzr, 2022; Vallaeys, 2022).
7. **Decision rule after the data budget is met.** Customised set wins on value per impression: roll out to matching ad groups and add the attribute to the update routine. Loses or ties: remove it; the price belongs in a sitelink, price asset or description instead, since Geddes' 2026 price-in-headline pattern trended worse. Unequal test (different ad group counts or volumes): rerun, do not conclude (Geddes, 2026).
8. **Maintain.** Customizer values are a feed: stale prices are policy and trust failures. Put the value sheet in the monthly loop (skill 22) and diff it against the source of truth; any keyword whose value is missing silently falls back to the default (Google Ads API docs), which is why rule 3 matters.

## What Google will tell you instead, and why we don't
Google's editor offers keyword insertion and customizers as relevance helpers, and the customizer docs frame them as a way to tailor every ad. We don't deploy them for relevance: across 432,343 ads DKI and customizers increased impressions per ad and decreased conversions per ad (Optmyzr, 2022), and in Geddes' 2026 tests ads without keyword insertion beat ads with it on CTR and conversion rate. We use customizers only to carry a buying fact that truly varies by keyword, and we make them prove it under a label.

## Failure modes
- Low-volume ad groups: the test cannot be read (skill 22); and the usual reason to want 1:1 copy there, "many small keywords", is the structure problem, not a copy problem.
- Brand campaigns: the value rarely varies by keyword; exclude (Geddes, 2026 keeps brand separate anyway).
- Premium or quote-based offers: a price in the headline is the wrong message (Geddes' 2026 B2B example: "get a quote" won on value per impression over "affordable").
- Volatile prices (travel, fuel, FX): fallback text serves silently when a value fails validation (Google Ads API docs); a stale or generic default under a "price" headline misleads the click.
- Accounts with AI Max text customisation on: Google-generated assets are not visible with the ad's own assets (Google Ads API docs, 2026), so the labelled comparison is no longer clean. Keep it off in test campaigns.
- Keyword lists above 40 distinct value types: the attribute cap (Google Ads API docs) forces reuse; if you need more than 40 attributes you need fewer attributes, not a workaround.

## What to measure
Conversions and conversion value per impression by labelled set; impressions per ad (expect the customised set to gain impressions — that is not the win); share of impressions served with the default rather than a keyword value (query the asset report for the default string); number of keywords with missing or stale values at each monthly diff.

## Open disagreements in the canon
- Geddes (2022) lists keyword insertion and customizers as neutral helpers; Optmyzr (2022) and Geddes' own 2026 tests show they cost conversions. Epiminds follows the evidence and the later Geddes: allowed only for buying facts, never for relevance.
- Whether prices belong in headlines at all: Geddes' 2026 price-pattern test trended against it but was unequal. Epiminds treats "price in headline" as a per-account test (rule 6), with the default placement in sitelinks or descriptions.
