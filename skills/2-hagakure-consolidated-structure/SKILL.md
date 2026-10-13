---
name: hagakure-consolidated-structure
id: 2
description: Rebuild a fragmented Search account (many thin campaigns/ad groups, SKAGs, match-type splits) into a Hagakure-style consolidated structure so Smart Bidding gets enough data per campaign. Not for accounts already on 3–5 themed campaigns, for Shopping/PMax structure, or as a cure for broken conversion tracking.
tags: Structure / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Removal of keyword match types or DSA (AI Max replacing keyword targeting); change to Smart Bidding minimum-data guidance; portfolio-level data pooling becoming default.
---
## What this is
A consolidation recipe for Search accounts that have outgrown manual-bidding structures. The target is the fewest campaigns and ad groups that still keep ad and landing page relevant to the keyword, with Smart Bidding fed by a campaign that clears a real conversion threshold. The method as Google Japan framed it is "maximum results with minimum entities": one landing page per ad group, all match types in that ad group, a DSA ad group as backstop, and the keyword set harvested from what already converts (Wenner/Search Engine Land, undated, ~2019 case). Everything else here is the canon's limits on it.
See also: skill 9 (micro-campaign-consolidation) — the low-volume repair when a merged campaign still sits under 30 conversions: portfolio pooling with a CPC cap and the scale gate.
See also: skill 14 (dsa-long-tail-harvesting) — DSA as a fenced feeder with the promotion rule for DSA-sourced queries.

## Where it comes from
Optmyzr's 14,584-account bidding study sets the volume threshold (Hopkins/Optmyzr, 2024). Vallaeys and Walker set the campaign-split rules and the 30-conversion floor (Optmyzr PPC Town Hall, 2025). Brad Geddes sets the ad-group floor — merge only while ad and landing page still fit the keyword — and supplies the counter-example of over-consolidation (Geddes/Adalysis, 2020). Bacchini supplies the SKAG verdict and the low-volume fallback (Optmyzr PPC Town Hall, 2025). Vendor and agency case series (Adchieve 2021; Springbok/Emerce 2022) are directional only.

## When to use it / when not to
Use when: the account is on or moving to tCPA/tROAS/Max Conversions and most campaigns sit under 30 conversions/30 days (Vallaeys/Walker, 2025); SKAGs or match-type-split campaigns are still in place in a new build (Bacchini, 2025); campaigns carry near-identical targets (e.g. 700/725/715% ROAS), which Lolk reports in ~80% of the split accounts he sees (Lolk, Optmyzr Town Hall, 2025 — not canon, cited for the number).

Do not use when: the account already runs few campaigns and impression share is high — Springbok's Case 3 moved cost +1%, CPA +3%, the only gain was management time (Groeneveld/Emerce, 2022); conversion tracking is broken (consolidation pools bad data faster); even one campaign would stay under 25 conversions/30 days — no account under 25 outperformed those over 50 (Hopkins/Optmyzr, 2024); SKAGs still perform in a mature account and nobody has a reason to touch them (Bacchini, 2025).

## Inputs
- Campaign list with 30-day and 90-day conversions, cost, target (tCPA/tROAS), budget, geo/language settings.
- Search terms report and keyword report, last 30/60/90 days, plus 12-month view for seasonality (Wenner/SEL).
- Landing-page impressions per week per URL (Adchieve rule input).
- Current negative lists and brand/non-brand split.
- Conversion setup: native tag vs import, attribution model, window.

## Method
1. **Fix measurement before touching structure.** Native Google Ads tag, data-driven attribution, 90-day window, enhanced conversions on (Wenner/SEL). If any of these is missing, stop; consolidation only pools whatever the tag records.
2. **Decide the campaign count from targets, not themes.** Keep two campaigns separate only if (a) they need their own budget, (b) they need targeting that cannot be set at ad-group level (geo, language, schedule), or (c) they perform differently enough to justify a different target — brand vs non-brand is the canonical case (Vallaeys/Walker, 2025). Lolk's bar for "different enough" is the order of 500% vs 300% ROAS; 700 vs 725 is not a split (Lolk, 2025, not canon). Everything that fails (a)–(c) merges.
3. **Check the merged campaign clears volume.** Projected conversions for the merged campaign over 30 days: ≥50 is the level at which any bidding strategy becomes predictably successful (Hopkins/Optmyzr, 2024); 30 is the floor below which campaigns get unstable (Vallaeys/Walker, 2025). If the whole account cannot reach 30 in one campaign, do not Hagakure it — go to step 9.
4. **Harvest the keyword set.** Join search terms and keywords with >1 conversion over the last 30/60/90 days; drop non-converters; re-run at 3/6/9/12 months so seasonal terms survive (Wenner/SEL). For DSA-sourced terms, promote on the managed-tier rule — ≥35 impressions and ≥2 conversions a month for 3 consecutive months (Geddes/Adalysis, 2016 via skill 14) — not the 5 clicks that used to be enough (Lolk, 2025, not canon).
5. **Build ad groups by landing page, bounded by relevance.** One URL per ad group (Adchieve, 2021); all match types of a keyword in the same ad group under automated bidding (Geddes, 2020; Google agrees here). Maximum 20 keywords per ad group (Wenner/SEL); Adalysis alerts at 50 (Adalysis docs, undated). Split an ad group when the keyword is not reflected by both the ad and the landing page (Geddes, 2020) — this is the floor, and it is why a 532-keyword single ad group ran $300+ CPA against $27 after a 112-ad-group rebuild (Geddes, 2020).
6. **Only give a URL its own ad group if it has traffic.** Adchieve's threshold: >3,000 impressions/week per landing page; everything below is covered by DSA (Adchieve, 2021). Scale that to the account — the point is that an ad group with no impressions is an entity with no purpose.
7. **Add a DSA ad group per campaign as backstop and discovery**, with the keyword ad groups' terms as exact negatives in the DSA group so it cannot take their traffic (Wenner/SEL). Review DSA search terms through the learning period, i.e. the 2–3 weeks Smart Bidding needs to stabilise after a change (Hopkins/Optmyzr, 2024); broad and loose phrase matching drove Springbok's Case 2 to +46% cost alongside +49% conversions (Groeneveld/Emerce, 2022).
8. **Keep a manual fallback.** Keep exact and phrase versions of the top-cost keywords in the ad group rather than going broad-only, so the account still runs if tracking breaks or Smart Bidding is paused (Löhlefink/Emerce, undated; Wenner/SEL: broad match is "not a mandatory component").
9. **If volume fails step 3: pool instead of merge.** Put the thin campaigns in a portfolio bid strategy to pool data (Bacchini, 2025), or start on manual bidding and let data accrue (Vallaeys/Walker, 2025). Revisit after 90 days — the minimum data history the Optmyzr study required before judging a bidding strategy (Hopkins/Optmyzr, 2024).
10. **Roll out in phases, highest-spend campaign first, and judge after the learning period plus conversion lag.** Google Experiments cannot test a whole-structure change (Adchieve, 2021), so the comparison is before/after on equal periods; exclude strongly seasonal windows. Expect budget demand to rise after the switch and set caps beforehand (Groeneveld/Emerce, 2022).

Output: a campaign map (which campaigns survive and why under 2a–c), the projected 30-day conversions per surviving campaign, the ad-group list with URL and keyword count, the DSA negative set, and the rollout order.

## What Google will tell you instead, and why we don't
- Google's structure guidance says merge match types "then simplify by just using broad match" and cites 62% of Smart Bidding advertisers on broad as primary (Google Ads Help, answer 14752782, data Jan–Feb 2023). We keep exact/phrase on the top-cost terms as a fallback (Löhlefink; Wenner) and go broad per ad group only after the campaign clears the volume floor, because the loose matching is what blew up Springbok's cost (Groeneveld/Emerce, 2022).
- Google's data guidance is 15 conversions in 30 days (as cited by Vallaeys/Walker, 2025). The 14,584-account study shows that "era has passed": sub-25 never beats 50+, and 25–50 is not reliably better than <25 (Hopkins/Optmyzr, 2024). We plan for 30 minimum and 50 target.
- Google frames consolidation as always good for AI. Geddes's plumber account is the counter-case: one ad group for everything is also "consolidated" and it ran at 0.5% CTR (Geddes, 2020). Consolidation stops at ad/landing-page relevance.

## Failure modes
- **Small lead-gen accounts** under 25–30 conversions in one campaign: structure will not fix the data problem; Adchieve's worst case was its smallest account (Adchieve, 2021). Pool instead (Bacchini, 2025).
- **High impression share already**: nothing to gain but admin time (Springbok Case 3, 2022).
- **Broad-first retail with weak negatives**: cost can rise ~46% in weeks (Springbok Case 2, 2022).
- **Multi-product B2B needing different copy per product**: merging past landing-page relevance lowers ad relevance (Geddes, 2020; Löhlefink).
- **Structure and Smart Bidding switched together**: you cannot tell which did it; Adchieve saw larger uplifts in exactly those cases (Adchieve, 2021).
- **Mature SKAG accounts that perform**: do not disrupt without a reason (Bacchini, 2025).

## What to measure
- Conversions per campaign per 30 days against the 30/50 thresholds (Vallaeys/Walker, 2025; Hopkins/Optmyzr, 2024).
- Before/after on equal, non-seasonal periods: cost, conversions, CPA/ROAS, impressions, CTR, CVR — the Springbok table is the template (Groeneveld/Emerce, 2022).
- DSA share of spend and DSA search terms that should become keywords (≥35 impressions and ≥2 conversions a month for 3 months; Geddes/Adalysis, 2016 via skill 14).
- Ad relevance / QS per merged ad group as the signal you consolidated past relevance (Geddes, 2020).
- Budget-limited status in the first two weeks after the switch (Groeneveld/Emerce, 2022).

## Open disagreements in the canon
- **Ad-group granularity.** Hagakure proponents (Wenner; Adchieve) merge to one ad group per URL; Geddes holds that the ad group boundary is ad + landing-page relevance, which can mean many ad groups even under automation (Geddes, 2020). Epiminds goes with Geddes: URL is the starting rule, relevance is the stopping rule, because his is the only source with a before/after showing over-consolidation failing.
- **Broad match as the default match type.** Google and some Hagakure writers make broad the end state; Wenner says it is optional and Löhlefink keeps exact/phrase as fallback. Epiminds keeps the fallback until the campaign shows 50+ conversions/30 days (Hopkins/Optmyzr, 2024) and clean search terms.
- **Where the volume threshold sits.** 15 (Google), 30 (Vallaeys/Walker, 2025), 50 (Hopkins/Optmyzr, 2024). Epiminds plans for 30 as the floor and 50 as the design target, since the only cross-account evidence is the Optmyzr study.
