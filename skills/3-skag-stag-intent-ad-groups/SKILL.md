---
name: skag-stag-intent-ad-groups
id: 3
description: Decide ad-group granularity for a new Search build or restructure — when a keyword gets its own ad group, when synonyms share one, and how many keywords an ad group can carry. Not for campaign-level splits (see skills 2, 4, 7) and not an RSA-writing guide.
tags: Strategy / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: AI Max or similar fully replacing keyword targeting; RSA serving no longer keying headline 1 to ad-group keywords.
---
## What this is
One decision rule replaces the SKAG/STAG/intent label debate: a keyword needs its own ad group only when it is not reflected by both the ad and the landing page (Geddes/Adalysis, 2020). Everything that shares an ad and a page shares an ad group; everything that does not, does not. SKAGs sit at one end of that rule (every keyword its own ad+page) and Hagakure at the other (one ad group per page); the rule says where on the axis a given account lands.

## Where it comes from
Geddes's account-organisation method and his plumber rebuild (Adalysis, 2020), his 5,900-account RSA pinning study showing Google still keys headline 1 to the ad group's keywords (Adalysis, 2026), Bacchini's SKAG verdict and Vallaeys/Walker's "themes in ad groups, not campaigns" (Optmyzr Town Hall, 2025), and the Adalysis audit default of 50 keywords per ad group (Adalysis docs, undated).

## When to use it / when not to
Use when: building a new Search account; a restructure is on the table; ad relevance is average or below in high-spend ad groups (Geddes, 2020); ad groups have grown past 50 keywords (Adalysis docs); an inherited SKAG account is being moved to Smart Bidding.

Do not use when: a legacy SKAG account is performing and nobody has a reason to touch it — Bacchini's rule is to not disrupt accounts where SKAGs still perform (Bacchini, 2025); the campaign is DSA or AI Max where keyword-to-ad relevance is not under your control.

## Inputs
- Keyword list with match types, cost, conversions, ad relevance / QS components.
- Search terms per ad group (unique queries count).
- Landing-page map: which URL each keyword should go to.
- RSA inventory per ad group and headline-1 pinning status.

## Method
1. **Cluster by landing page first.** Every keyword goes to the URL that answers it; keywords with different URLs are in different ad groups (Geddes, 2020 — the page is half the rule).
2. **Within a page cluster, cluster by ad.** Write the headline-1 line that would be pinned for the group (the keyword-bearing line Google serves in position 1 by default; Geddes, 2026). If one headline-1 is honest for all keywords in the cluster, they are one ad group. If not, split until it is. This is the STAG/intent test made concrete: the group is as wide as one keyword headline can cover.
3. **Do not split synonyms Google treats as one entity.** "Car hire" and "car rental" variants performed identically (CTR 1.7–2.9%, CVR 4.15–4.30% across the four combinations; Geddes, 2020); separate ad groups for them only dilute data. Same for close variants — exact and phrase no longer map one keyword to one query (Bacchini/Lolk, 2025).
4. **Keep all match types of a keyword in the same ad group** under Smart Bidding (Geddes, 2020). Match-type separation belongs at campaign level and only for budget/bid-method reasons (see skill 4).
5. **Cap the ad group.** Target ≤20 keywords (Wenner/SEL, undated, Hagakure rule); the Adalysis audit flags >50 as unmaintainable relevance (Adalysis docs). Over 20, go back to step 2 and look for a second headline-1.
6. **Build formulaically, then customise.** Start with templated ad groups (service × modifier, plus geo ad groups where the page differs); customise ads for the top-spend ad groups as a second pass — Geddes's plumber account went from 1 ad group/532 keywords/1 ad (0.5% CTR, 3% CVR, $300+ CPA) to 112 formula-based ad groups (8% CTR, 11% CVR, $27 CPA) (Geddes, 2020).
7. **Pin headline 1 to the keyword line in small accounts.** Low-data accounts show repeated headlines because Google has not tested combinations; pinning the keyword line to position 1 and the benefit/CTA to 2 cuts the impressions needed to learn (Geddes, 2026). If you will not run ad tests, pin one or two positions only (Geddes, 2026).
8. **Diagnose later with the relevance check.** Ad relevance average or below → count keywords and unique queries in the ad group; if either is high, split (Geddes, 2020).
9. **Output**: an ad-group map (URL, headline-1 line, keyword list ≤20, match types together), a list of ad groups merged because they shared ad+page, and the top-spend ad groups flagged for custom copy.

## What Google will tell you instead, and why we don't
- Google's structure guidance consolidates SKAGs into themed ad groups and shows 6 → 3 ad groups as the model, with no limit on how far to merge (Google Ads Help, answer 14752782). We stop merging at the ad+page relevance rule because Google's own RSA serving keys headline 1 to the ad group's keywords (Geddes, 2026) and an over-merged ad group ran at 0.5% CTR (Geddes, 2020).
- Google positions RSA asset mixing as making ad-group tightness unnecessary. In small accounts Google repeats the keyword-matched headlines because it has not tested combinations (Geddes, 2026), so the ad group's keyword set is still what the searcher sees.
- Google has no quantitative keyword cap; we carry 20 target / 50 alert (Wenner; Adalysis docs).

## Failure modes
- **Legacy SKAG accounts that perform**: restructuring triggers relearning for no gain (Bacchini, 2025).
- **Large catalogues with templated pages**: one headline-1 per product line may still mean hundreds of ad groups; that is correct per the rule, but only if each gets ≥ the impressions needed to learn — otherwise pin (Geddes, 2026) or accept DSA for the long tail (skill 2).
- **Single-page sites / one landing page**: the page half of the rule collapses; granularity comes only from the ad test, so expect few ad groups and heavier reliance on pinning.
- **Accounts where keyword synonyms genuinely differ in intent** (e.g. "cheap" vs "best"): those are not entity synonyms; the headline-1 test will split them — do not force-merge on Geddes's car-hire example.
- **Intent-themed groups built on the agency's taxonomy rather than the page**: relevance drops if the group spans two URLs; step 1 comes before step 2 every time.

## What to measure
- Ad relevance and QS components per ad group after the change (Geddes, 2020).
- Keywords and unique queries per ad group (≤20 target; >50 alert; Wenner; Adalysis docs).
- CTR and CVR per ad group vs the pre-restructure baseline (the plumber account is the magnitude reference; Geddes, 2020).
- Headline-1 served share and repeat-headline incidence in small ad groups (Geddes, 2026).

## Open disagreements in the canon
- **How far to consolidate.** Hagakure/Google: one ad group per landing page. Geddes: ad + page relevance, which is usually more granular. Epiminds goes with Geddes; his is the only side with numbers for the failure case.
- **SKAGs.** Bacchini and Lolk say dead; Geddes's rule can still produce a one-keyword ad group where a keyword has a unique page and ad. Epiminds does not build SKAGs by policy but accepts single-keyword ad groups that fall out of the rule.
- **Keyword cap.** 20 (Hagakure) vs 50 (Adalysis alert) vs none (Google). Epiminds targets 20 and treats 50 as the audit flag.
