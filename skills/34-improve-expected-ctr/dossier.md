# Dossier — 34 Improve Expected CTR

## Sources

1. **Source**: Brad Geddes, Adalysis blog, "The impossible project: average CTRs for Quality Score" — https://adalysis.com/blog/impossible-project-average-ctrs-quality-score/ · **Tier** 1 · **Date** 11 Aug 2016 (page modified 2026) · **Claim**: the CTR needed to be rated "above average" is account- and keyword-specific, not a fixed benchmark. Two example accounts: Company 1 non-brand top terms — 3.5% CTR = below average, 8.5% = average, 14.5% = above average; a 9/10 QS needed ~9% CTR. Company 1 brand — 6% below, 15% average, 46% above; a 10 needed 46%. Company 2 brand — 15% CTR already "above average". Geddes: it is "impossible to say what CTR you need to hit" for any keyword; the only method is to find the low-QS areas and test ads for CTR; conversion-per-impression testing raises both QS and profit. · **Evidence**: campaign-level charts from two client accounts (small sample, but real data).

2. **Source**: Brad Geddes, Acquisio webinar write-up (Acquisio blog, untitled page) — https://www.acquisio.com/blog/?p=6300 · **Tier** 1 (Geddes's own analysis; outlet is a vendor) · **Date** undated, references AdWords; c. 2016–2017 · **Claim**: from analysis of $100M+ spend, Ad Rank weight estimated ~50% bid / ~40% QS / ~10% extensions. No universal "good" CTR: 1% may be strong for "television", 30% merely average for a specific commercial query. CPC discounts from higher QS appear mainly at position 1; lower down the benefit shows as rank, not price. In B2B a lower QS can be preferable because pre-qualifying copy filters casual searchers. Diagnostic: pivot clicks vs impressions by QS to find high-impression / low-click keywords; judge by conversions per impression. One travel client: QS 3 had higher CTR than QS 4 (non-linear). · **Evidence**: aggregated client data, stated as Geddes's analysis; percentages are his estimates.

3. **Source**: Navah Hopkins, Search Engine Land, "What is quality score and how to use it in PPC" — https://searchengineland.com/quality-score-ppc-394513 · **Tier** 1 · **Date** undated; table data from Feb 2023 → 2023 · **Claim**: expected CTR is "out of your control" as a rating — optimise actual CTR, not expected CTR; don't discount low-expected-CTR keywords that win elsewhere. Keywords with data typically settle at 7–9; many drift to 5–6 as impressions accumulate. A 1–2 point drop is normal; 5→2 signals a real problem. Broad match struggles more with QS but can win cheaper positions. Ad Strength does not affect QS. · **Evidence**: practitioner account observations; one table of account data.

4. **Source**: Amy Hebdon (Paid Search Magic), Copyhackers tutorial "How to write an AdWords ad" — https://copyhackers.com/write-adwords-ad/ · **Tier** 2 · **Date** 24 Apr 2018 · **Claim**: match the headline to the searched keyword — "feels like a missed opportunity to stand out, but it's what works"; a high-CTR ad can pull unqualified clicks that don't convert; sentence case out-performed title case in her tests; no exclamation marks in headlines; single-keyword ad groups only work with enough traffic — splitting dilutes CTR data; don't test a headline and a landing page at the same time. · **Evidence**: her own account tests (no numbers published).

5. **Source**: Optmyzr blog (Ronia; quotes Fred Vallaeys, Aaron Levy, Jyll Saskin Gales, Ginny Marvin), "Google Ads Quality Score" — https://www.optmyzr.com/blog/google-ads-quality-score/ · **Tier** 1 (Optmyzr) with vendor caveat · **Date** 2 Mar 2026 · **Claim**: expected CTR is relative to competitors — a 50% actual CTR can be "below average" if Google expects 70%. Visible QS is historical and "mostly based on past exact match performance"; Levy: auction-time QS "may be okay for the best queries but poor for the worst, which dominate what you can see". Gales: 7 is "really good", 6 is fine; don't chase 10. · **Evidence**: opinion; no study.

6. **Source**: Jyll Saskin Gales, Inside Google Ads podcast ep. 107 "Quality Score explained" — https://iga.buzzsprout.com/2295853/episodes/18592384 · **Tier** not in canon (ex-Googler; used only as a corroborating example) · **Date** 12 Feb 2026 · **Claim**: a 7–8% non-brand CTR can still be rated below-average expected CTR relative to auction competitors; bid strategy and conversion tracking don't affect QS directly but can be root causes of poor expected CTR. · **Evidence**: opinion.

7. **Source**: Fred Vallaeys, Optmyzr, "Five ways Optmyzr tracks Quality Score that AdWords can't" — https://www.optmyzr.com/blog/five-ways-optmyzr-tracks-quality-score-that-adwords-cant · **Tier** 1 · **Date** 16 May 2017 · **Claim**: the 1–10 score is "based on position-normalized data"; a keyword with 18 impressions may not justify attention; aggregate at ad group level for more data. · **Evidence**: vendor description of its own tracker built on billions of data points.

## Dissenting view
Navah Hopkins (SEL, 2023) says expected CTR is effectively outside the advertiser's control and should be ignored in favour of actual CTR and conversion outcomes; Geddes (2016, Acquisio) treats expected CTR as a primary ad-testing metric, moved by CTR tests. The disagreement is whether the rating responds to ad work quickly enough to be worth targeting directly. Hebdon (2018) and Google both warn that higher CTR can mean worse clicks — the second axis of disagreement is CTR vs. conversion-per-impression as the test metric.

## What the platform currently does [Google docs]
- [Google docs] "About Quality Score for Search campaigns" (support.google.com/google-ads/answer/6167118, fetched 2026-10-13): the three components are rated Above average / Average / Below average against advertisers whose ads showed for the *exact same keyword* over the last 90 days. QS is "a diagnostic tool", "not an input in the ad auction", "not a key performance indicator and should not be optimised or aggregated". "—" appears when there aren't enough exact-match searches. Device, location, time of day and assets are not captured in QS. Changing match type doesn't affect QS; a broad keyword can carry the QS of an exact keyword in the same ad group.
- [Google docs] "5 ways to use Quality Score" (answer/6167130): for expected CTR below average — make the offer more compelling, be more specific, test CTAs; "specific ads may lower CTR but raise conversion rates".
- [Google docs] Null QS replaced the default 6 for new/low-activity keywords from the week of 12 Sep 2016 (Google Ads Developers blog, 15 Aug 2016; SEL/Marvin 15 Aug 2016). Historical QS columns added May 2017 with data back to 22 Jan 2016 (SEL/Marvin 15 May 2017).

## Baseline check
Read `google-ads-quality-score` and `google-ads-ad-copy`. The baseline gives a generic "keyword in headline, extensions, split ad groups" list and a made-up ~55% component weight. This skill adds: the account-specific CTR thresholds (Geddes's data), the position-1-only CPC discount, the B2B case for deliberately lower expected CTR, conversions-per-impression as the test metric, the SKAG dilution warning, and a decision rule for when *not* to chase the rating.

## Judgment calls
- The Acquisio page is undated; cited as c.2016 on the strength of its AdWords references. Geddes's Ad Rank split (50/40/10) is his estimate, labelled as such.
- Hebdon is Tier 2 for ad copy/QS per canon; used for method only.
- Gales is not canon; cited only as a corroborating example of the "high actual CTR, still below average" case, never as the reason for a rule.
- The 2026 Optmyzr article is content-marketing with Vallaeys/Levy quotes; used for Levy's query-mix point and the relative-CTR example only.

## Canon strength: Strong
Geddes (two sources with account data), Hopkins, Optmyzr/Levy, Hebdon — 3+ Tier 1/2 with some data.

## Invalidated by
Google changing the expected-CTR comparison set (currently exact-same-keyword, 90-day window) or folding assets into QS; retirement of keyword-level QS reporting.
