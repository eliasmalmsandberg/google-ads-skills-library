# Dossier — 3 SKAG vs STAG vs intent-themed ad groups

## Sources

1. **Source**: Brad Geddes (Adalysis), "Google Ads Account Organization" workshop slides — https://presentations.boussiasevents.gr/files/_boussias_conferences_content/presentations/google_marketing_conference/2020/day2/workshop_brad_geddes_googleMKT_20.pdf · **Tier**: 1 · **Date**: 2020 · **Claim**: The ad-group rule: "If the keyword isn't reflected by both the ad and the landing page, you need a new ad group." Under automated bidding keep all match types of a keyword in one ad group. If the same ads are used across several ad groups, no extra ad group is needed. Google treats "car hire" and "car rental" as one entity — CTR/CVR across the four variants: 2.7%/4.21%, 1.8%/4.15%, 1.7%/4.23%, 2.9%/4.30% — so splitting synonyms into separate ad groups buys nothing. Over-consolidation case: 1 ad group / 532 keywords / 1 ad → 0.5% CTR, 3% CVR, $300+ CPA; rebuilt to 112 formula-based ad groups (service × modifier plus geo ad groups) → 8% CTR, 11% CVR, $27 CPA. Start formulaic, customise top ad groups second. If ad relevance is average or below, check the number of keywords and unique queries per ad group. · **Evidence or opinion**: Method with single-account numbers and keyword-variant data.

2. **Source**: Brad Geddes (Adalysis), "Data study: what 5,900 accounts reveal about RSA pinning" — https://adalysis.com/blog/data-study-5900-accounts-rsa-pinning/ · **Tier**: 1 · **Date**: 2026-10-13 · **Claim**: Google's default RSA behaviour ties headline 1 to the ad group's keywords (often containing the keyword), headline 2 to CTA/benefit; in small accounts headlines repeat because Google favours assets tied to search terms when it has not tested combinations; pin keyword-related lines to position 1 and benefits/CTAs to 2 to reduce the impressions needed to learn. Implication: the ad group must be tight enough that one keyword-bearing headline is relevant to every keyword in it. · **Evidence or opinion**: 5,900-account study (ads ≥30 days, ≥250 impressions, ≥1 conversion; brand excluded).

3. **Source**: Julie Friedman Bacchini and Andrew Lolk with Fred Vallaeys, Optmyzr PPC Town Hall, "PPC in 2025" — https://www.optmyzr.com/ppctownhall/ppc-in-2025-what-to-stop-start-double-down-on · **Tier**: 2 (Bacchini); Lolk not canon, labelled · **Date**: early 2025 · **Claim**: Bacchini: "The single keyword ad group's time has come and gone"; remove SKAGs first in a new 2025 build, but don't disrupt accounts where they still perform; prefers single-*theme* ad groups for budget control and copy flexibility. Lolk: SKAGs fail as an overall strategy because phrase and close-variant matching make precise control nearly impossible. · **Evidence or opinion**: Opinion.

4. **Source**: Fred Vallaeys with Shawn Walker, Optmyzr PPC Town Hall — https://www.optmyzr.com/ppctownhall/practical-advice-on-how-to-actually-make-smart-bidding-work-for-you · **Tier**: 1 · **Date**: 2025-01-29 · **Claim**: Put themes in ad groups rather than campaigns because optimisation happens at campaign level; start simple and add granularity as data supports it. · **Evidence or opinion**: Opinion.

5. **Source**: Adalysis docs, "Ad groups with too many keywords" — https://docs.adalysis.com/tools/audit/prebuilt-alert-list/ad-groups/ad-groups-with-too-many-keywords · **Tier**: 1 (Adalysis tool default) · **Date**: undated · **Claim**: Default alert at >50 keywords per ad group because relevance of keywords to ads becomes hard to maintain. · **Evidence or opinion**: Tool default (practitioner-set threshold).

6. **Source**: Benjamin Wenner, Search Engine Land, "The Hagakure method" — https://searchengineland.com/the-hagakure-method-for-google-ads-management-432867 · **Tier**: Not canon — context · **Date**: undated (~2019 case) · **Claim**: Max 20 keywords per ad group; one landing page per ad group; Hagakure can be combined with SKAG or STAG. · **Evidence or opinion**: Method description.

7. **Source**: Ruben Löhlefink (Dentsu), Emerce — https://www.emerce.nl/achtergrond/google-ads-accountstructuren-de-afweging-tussen-single-intent-ad-groups-en-hagakure · **Tier**: Not canon — context · **Date**: undated · **Claim**: "Single Intent Ad Groups": merge where intent or landing page is identical (e.g. "kopen" vs "bestellen"); keep hyper-specific ad groups only for the keywords carrying most cost and conversions; SIAG cuts ad groups by at least half vs traditional. · **Evidence or opinion**: Opinion.

## Dissenting view
Google (and Hagakure) treat fewer ad groups as better for AI; Geddes's plumber account is the counter-evidence that an under-segmented ad group (532 keywords, one ad) ran at 0.5% CTR and $300+ CPA. The disagreement is over the unit of relevance: Google frames the ad group as a data-pooling unit; Geddes frames it as a relevance unit (keyword ↔ ad ↔ landing page), and his 2026 pinning study shows Google's own RSA serving still keys headline 1 to the ad group's keywords, so the relevance unit still matters.

## What the platform currently does [Google docs]
- Google Ads Help "The ABCs of Account Structure" (answer 14752782): move SKAGs into themed ad groups; one ad group per shared landing page/creative theme; example of 6 ad groups → 3; combine match types in one ad group and simplify to broad. No numeric keyword-per-ad-group guidance. [Google docs]
- Exact match close variants (2018–19) and phrase absorbing BMM (2021) mean a SKAG's single keyword no longer maps to a single query (Lolk, 2025, observation). [Google docs]
- RSAs are the only Search ad format; Google selects headline 1 by relevance to the ad group's keywords (Geddes, 2026, observed default).

## Baseline check
Read `google-ads-account-audit` (Layer 2: 5–20 keywords/ad group healthy, >30 flag; "tightly themed"). Baseline gives ranges without a rule. This skill adds Geddes's decision rule (new ad group only when keyword is not reflected in both ad and landing page), the synonym-entity evidence that splitting synonyms is wasted, the 2026 pinning finding that makes headline-1 relevance the practical test, the SKAG verdict from Bacchini/Lolk with the "don't disrupt what works" caveat, and the thresholds (20 per Wenner, 50 alert per Adalysis).

## Judgment calls
- SKAG, STAG and intent-themed are treated as points on one axis; the skill replaces the label debate with Geddes's rule plus a keyword cap.
- Lolk's and Löhlefink's positions are non-canon or labelled; the position rests on Geddes, Bacchini and Vallaeys.
- Optmyzr's RSA-count study could not be fetched; not cited.

## Canon strength: Strong
Geddes ×2 (method + 5,900-account study + single-account numbers), Vallaeys/Walker (Tier 1), Bacchini (Tier 2), Adalysis default.

## Invalidated by
Removal of keyword-level targeting (AI Max fully replacing keywords), RSA serving no longer keying headline 1 to ad-group keywords, or Google allowing ad-level landing-page/keyword relevance signals that make ad groups irrelevant.
