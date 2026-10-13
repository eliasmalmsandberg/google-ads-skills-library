# Dossier — 17 Search partners & Display expansion exclusion test

Research note: WebSearch budget exhausted; sources via sitemaps. No canon source on Display Expansion for Search campaigns could be located or fetched, and Google's help page for the Networks setting (search partners default, Display Expansion) could not be fetched (several URL candidates failed). Search-partner canon is solid; the Display Expansion half is stated as an Epiminds default with the reasoning, not as a sourced finding.

## Sources

1. **Source**: Brad Geddes, Adalysis — "How to evaluate search partners on Google Ads & Microsoft Ads", https://adalysis.com/blog/how-to-evaluate-search-partners-on-google-ads-microsoft-ads/ · **Tier** 1 · **Date** 2023-02-14 (updated Aug 2024) · **Claim**: Segment by network; decide per campaign (the only level partners can be toggled on Google) on CPA or ROAS, not CTR or CVR — lower CTR/CVR on partners is normal and not a reason to exclude. Do not block partners by default; some campaigns do better on partners. Exception: small-budget accounts losing IS to budget can block by default. Google gives no per-partner reporting or exclusion; Smart Bidding does not always hit partner targets. · **Evidence**: 134,488 Google Search clicks vs 57 partner clicks in one view; remove case: partner CPA $185 vs $11 on Google Search; keep case: partner CPA lower than Google Search; Smart Bidding campaigns where partner CPA was 17× Google Search while others were fine.
2. **Source**: Nils Rooijmans — "Google Ads Script: Search Partner Alerts", https://nilsrooijmans.com/google-ads-script-search-partner-alerts/ · **Tier** 1 · **Date** 2019-10-20, modified 2025-05-09 (v1.2) · **Claim**: Per enabled campaign, compare partner vs Google Search cost per conversion; alert when the gap exceeds 20% (CPA_DIFF_THRESHOLD = 0.2) with at least 50 partner clicks (CLICK_THRESHOLD = 50); default period LAST_365_DAYS (30/60/90-day options); run monthly; opt flagged campaigns out of partners. Attributes the problem to "Smart pricing" which cannot be opted out of. · **Evidence**: script; thresholds published.
3. **Source**: Nils Rooijmans — "Google Search Partner performance after auction change", https://nilsrooijmans.com/google-search-partner-performance-after-auction-change/ · **Tier** 1 · **Date** 2022-01-11 · **Claim**: Google moved the AdSense auction (where partner ads compete) to position-first bidding on 17 Nov 2021 (cites Google support doc); many campaigns saw partner traffic jump and conversion value fall; check Segment > Network around that date; exclude at campaign level if underperforming. · **Evidence**: screenshots from own accounts; no figures in text.
4. **Source**: Frederick Vallaeys, Optmyzr — "When to stop using Smart Bidding", https://www.optmyzr.com/blog/when-to-stop-using-smart-bidding/ · **Tier** 1 · **Date** 2026-05-28 · **Claim**: Smart Bidding needs ~50 conversions/30 days to be reliable (used here to set the minimum data for a per-campaign partner decision under Smart Bidding). · **Evidence**: 14k-account internal research.

## Dissenting view
Rooijmans (2019, 2022) leans to excluding partners when they underperform and attributes the damage to Smart pricing; Geddes (2023) explicitly says don't block by default and shows accounts where partners had lower CPA. The disagreement is about the default: opt-out-first vs measure-first. Both agree the decision is per campaign on CPA/ROAS.

## What the platform currently does [Google docs]
- [Google docs] Search partners are "hundreds of non-Google websites, as well as YouTube"; ads appear on partner search results, site directory pages, product detail pages and YouTube search/watch pages; pay per click; partners must follow Google policy (support.google.com/google-ads/answer/2616017, fetched 2026-10-13). The page does not state the default-on setting or the opt-out path.
- [Google docs, not fetched] The Networks setting page with "Include Google search partners" (default on) and "Include Google Display Network" (Display Expansion for Search) could not be fetched. Practitioner sources confirm partners are campaign-level toggles (Geddes 2023; Rooijmans 2022). Display Expansion behaviour is not documented in this dossier.
- Position-first bidding in the AdSense/partner auction from 17 Nov 2021 (Rooijmans 2022 citing Google support).

## Baseline check
Read `google-ads-keywords` and `google-ads-negative-keywords` — neither covers networks. The baseline library has no search-partner or Display Expansion content. This skill adds the per-campaign CPA/ROAS decision rule, the 20%-gap / 50-click alert thresholds, the 2021 auction change, the Smart-Bidding caveat with the 17× example, and the "don't exclude on CTR/CVR" rule.

## Judgment calls
- Display Expansion: no canon source. Epiminds default is off at campaign creation, with the reasoning stated in the skill (a Search campaign's targets, negatives and search-term review don't apply to Display placements, so a Search-campaign CPA target cannot be audited there). This is labelled as an Epiminds position, not a sourced finding, and flagged for a future dossier.
- Default for search partners follows Geddes (measure first) for established accounts and Rooijmans/Geddes' small-budget exception (off first) for new or budget-limited campaigns.

## Canon strength: Adequate
Search partners: Strong (Geddes with numbers, two Rooijmans posts with thresholds). Display Expansion: no canon source. Combined: Adequate, with the Display half flagged.

## Invalidated by
Google adding per-partner reporting or exclusions (would change the method from toggle to placement-level); removal of the campaign-level partner toggle; changes to the partner auction (another position/pricing change like Nov 2021); Google documenting Display Expansion behaviour differently from the assumption stated here.
