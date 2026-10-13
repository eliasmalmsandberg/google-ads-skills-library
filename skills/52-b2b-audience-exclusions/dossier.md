# Dossier — 52 B2B audience exclusions (demographic, in-market, HHI)

Research note: shared WebSearch budget was exhausted during this category; sourcing was by direct fetch of canon archives. Sophie Fell's Search Engine Land author page (Tier 2 for exactly this topic) returned HTTP 429 and could not be read. PPC Mastery, Optmyzr, Adalysis, Brainlabs and Nils Rooijmans visible archives have no B2B-exclusion posts.

## Sources

1. **Source**: Andrea Cruz, Search Engine Land, "Google Ads for B2B: How to overcome challenges, platform limitations" (SMX Advanced write-up; page shows "guest author", her author archive lists it), https://searchengineland.com/google-ads-for-b2b-how-to-overcome-challenges-platform-limitations-386740 · **Tier** 1 · **Date** 2022-07-26 · **Claim**: Google's suggested in-market segments are often useless for B2B (an advocacy-software client's top suggestion was "High Performance and Aftermarket Auto Parts"); instead read the GA Demographics & Interests report, which covers all channels, to find statistically high- and low-performing in-market/affinity segments, then layer them into Search and Display. Lower bids on weak segments rather than excluding; raise on segments bringing a disproportionate share of quality traffic. Most platform features are built for B2C. · **Evidence or opinion**: Experience across "hundreds of B2B accounts"; one anecdote; no numbers.

2. **Source**: Andrea Cruz, Search Engine Land, "What are you optimizing for in paid search when keywords matter less?", https://searchengineland.com/what-are-you-optimizing-for-in-paid-search-when-keywords-matter-less-475565 · **Tier** 1 · **Date** 2026-04-27 · **Claim**: Manage "brand exclusion lists and negative intent themes" rather than micromanaging search terms; poor lead data fed back produces more poor leads; use on-site self-identification so users declare who they are. · **Evidence or opinion**: Opinion.

3. **Source**: Navah Hopkins, Search Engine Land, "A PPC guide to permission-based audiences", https://searchengineland.com/a-ppc-guide-to-permission-based-audiences-391228 · **Tier** 1 · **Date** 2023-01-12 · **Claim**: Observation mode's job is to show which native audiences make up your traffic so you can exclude the undesirable ones; then let Smart Bidding work. Alternative is manual bidding with audience bid adjustments. · **Evidence or opinion**: Opinion.

4. **Source**: Miles McNair, PPC Mastery, TPE #145 "Why bid adjustments are dead and what to do instead", https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: Under tCPA/tROAS/Max Conv/Max Conv Value, bid adjustments are mostly ignored; -100% is the only adjustment that reliably works, as an exclusion; he gives "a B2B campaign where desktop is the only relevant device" as a legitimate -100% case but calls even that a temporary fix — fix the cause. Smart Bidding already evaluates demographics and deeper audience segments at auction time. · **Evidence or opinion**: Practitioner position; no study.

5. **Source**: Sarah Vlietstra, ZATO, "Stop Wasting Ad Spend: A Guide to Audience Segment Exclusions", https://zatomarketing.com/blog/stop-wasting-ad-spend-a-guide-to-audience-segment-exclusions · **Tier** 1 (ZATO) · **Date** 2026-08-19 · **Claim**: Exclusion candidates: existing customers, employees, churned users, lead-form submitters, login-portal brand searchers; exclusions available in Search, Display, Shopping, PMax. · **Evidence or opinion**: Method; no data.

Reporting (platform change): Anu Adegbola, Search Engine Land, 2026-07-24, https://searchengineland.com/household-income-exclusions-spotted-in-performance-max-campaigns-483494 — HHI exclusion (top 10%, 11–20% … lower 50%, unknown) spotted in a European PMax campaign; spotted by Thomas Eccel.

## Dissenting view
Cruz (2022) says bid down weak segments rather than exclude them; McNair (2026) says those bid-downs are ignored under Smart Bidding. The disagreement is really about the bidding model: Cruz's advice is sound under manual/eCPC and was written before Search auto-used first-party lists; under Smart Bidding, -100% (exclusion) is the only lever that still does anything. Newer wins because the platform changed in between.

## What the platform currently does [Google docs]
- Search campaigns support demographic targeting/exclusion by age, gender and household income, not parental status. HHI is available in 20 countries (AU, BR, CA, CO, HK, IN, ID, IL, JP, MY, MX, NZ, PH, SG, KR, TW, TH, AE, US, VN; Russia only for Demand Gen) — not in Sweden, UK, Germany or any other European market as of the page. "Unknown" is selected by default and Google advises excluding it only if you are sure you want a narrow audience. Demographics use the targeting setting only; every demographic group is targeted by default. (https://support.google.com/google-ads/answer/2580383; 7365594)
- Audience segments can be excluded from Search, Display, Demand Gen, Standard Shopping, Video and PMax, at campaign or ad-group level; affinity and your-data segments are named; exclusions cannot be set during campaign creation; Google recommends observing performance before excluding; exclusions may not apply to users opted out of ads personalization. (https://support.google.com/google-ads/answer/2549058)
- Search can use affinity, detailed demographics, in-market and your-data segments but not custom segments or life events. (https://support.google.com/google-ads/answer/2497941)
- Observed first-party segments are used as Smart Bidding signals. (7365594)
- HHI exclusion appearing in PMax, July 2026 (Search Engine Land reporting).

## Baseline check
Read `google-ads-audit-leadgen` (Layer 6 audience checklist: "+20–40% for pricing page visitors", job-title targeting) and `google-ads-audiences` (affinity "do not use for lead gen", bid-modifier table). Both assume bid modifiers work and neither says which demographic/in-market exclusions exist on Search, where HHI is unavailable, or that demographics are target-only with Unknown on by default. This skill adds the candidate-finding procedure (GA cross-channel interests report, observation rows), the decision thresholds, the Smart Bidding reality that exclusion is the only working lever, and the geographic trap for HHI.

## Judgment calls
- Attributed the 2022 SMX write-up to Cruz on the strength of her author archive.
- Spend-without-conversion thresholds for exclusion: no canon source states one. The skill uses a threshold expressed in multiples of the campaign's target CPA and labels it as Epiminds' operating rule, not a sourced figure.
- Sophie Fell could not be read; flagged for the refresh.

- After blind review, four further operating numbers were labelled as Epiminds thresholds with no canon source: the 60-day window for reaching the step 4 threshold, the 30/90-day review cadence, the ~20 qualified-leads-a-quarter low-volume floor, and the ~20% week-on-week volume-drop alarm. Each carries its reason inline in the skill.

## Canon strength: Adequate
Four Tier 1 sources with positions and method; evidence is practitioner experience, no cross-account study.

## Invalidated by
Google adding parental status, life events or custom segments to Search; HHI becoming available in Nordic/EU markets; Smart Bidding starting to honour positive/negative audience bid adjustments; demographics gaining an observation setting.
