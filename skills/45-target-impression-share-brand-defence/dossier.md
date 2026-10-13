# Dossier — 45 Target impression share for brand defence

## Sources

1. **Source**: Kirk Williams, ZATO — "Google Ads testing case study: brand bidding — manual or Target Impression Share?", https://zatomarketing.com/blog/google-ads-testing-case-study-brand-bidding-manual-or-target-impression-share · **Tier** 1 · **Date** 2024-03-27 (updated 2026-04-21) · **Claim**: Google Ads Experiment, one brand Search campaign, 3 Feb–11 Mar 2024, 4,235 clicks: Manual CPC (with device/location/audience modifiers) vs tIS set at 92% (the prior 30-day manual IS) with a max CPC cap of ~$2.51, set above typical average CPC. Result: tIS +1% clicks, −2% conversions, −1% profit — manual "won" by a negligible margin; he switched to tIS anyway because manual needs ongoing management, and has since raised both the IS target and the cap. Not statistically significant; single account; brand spikes from other media not controlled. · **Evidence**: one controlled experiment with numbers.

2. **Source**: Kirk Williams, ZATO — "Why does Google Ads allow bidding on brand terms?", https://zatomarketing.com/blog/why-does-google-ads-allow-bidding-on-brand-terms · **Tier** 1 · **Date** 2024-05-23 · **Claim**: Brand isn't always bottom-funnel: one large advertiser's brand CVR and ROAS were nearly equal to non-brand because users research the category via the brand name. Close variants and PMax push more competitors into brand auctions. Bid-floor (reserve price) changes are, in his view, the main reason brand CPCs rose — a term that cost ~$0.07 to guard now ~$1, a 10–20× increase on high-QS terms against the same competitors. Brand conversions carry lower true profit than reported because the demand came from elsewhere. · **Evidence**: one client's data, auction insights trends.

3. **Source**: Kirk Williams, ZATO — "Why perfect brand segmentation in Google Ads is overrated", https://zatomarketing.com/blog/why-perfect-brand-segmentation-in-google-ads-is-overrated · **Tier** 1 · **Date** 2026-03-05 · **Claim**: Brand searches span the funnel (price checks, reviews, competitor hunting); a brand click is not automatically won because competitors bid. Brand should carry a *higher* ROAS target than non-brand because those users were already marketed to. Brand spend is fine while affordable; if over-bid and tests show it's not incremental, kill it. Separate brand Search campaign when brand and non-brand targets differ. Exclude brand terms only where the brand owns the organic results and nobody competes — "rare these days". Judge on blended ROAS/MER. Removing brand from PMax dipped overall brand sales in his accounts. · **Evidence**: experience; no data.

4. **Source**: Kirk Williams, ZATO — "Let's talk Google Ads bid floors (reserve prices)", https://zatomarketing.com/blog/lets-talk-google-ads-bid-floors-or-reserve-prices · **Tier** 1 · **Date** 2023-01-25 · **Claim**: With no competing bidder, Google charges a reserve price tied to Ad Rank thresholds, so uncontested brand clicks still cost well above $0.01; ineligible auctions don't count toward IS. Monitor Search IS and QS anomalies. Ginny Marvin (2023-02-16) confirmed thresholds are dynamic and decade-old. · **Evidence**: reasoning plus Google's policy docs.

5. **Source**: Navah Hopkins, Optmyzr — "The impact of PPC bidding strategies", https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier** 1 · **Date** 2024-09-24 · **Claim**: Target Impression Share improves CTR and CVR through top-of-page placement but does not improve CPA or ROAS; tIS "clearly needs caps" — the uncapped tIS sample wasn't even statistically significant. Caps help ROAS-oriented strategies most. · **Evidence**: 14,584-account study.

6. **Source**: Frederick Vallaeys, Optmyzr — "When to stop using Smart Bidding", https://www.optmyzr.com/blog/when-to-stop-using-smart-bidding/ · **Tier** 1 · **Date** 2026-05-28 · **Claim**: Smart Bidding can spend without limit; bid caps on portfolios help in some ROAS cases but add risk; Manual CPC is the safest way to set a hard per-click ceiling. · **Evidence**: 14,584-account research referenced; opinion on caps.

7. **Source**: Kirk Williams, ZATO — "Should you always exclude brand from Performance Max? It's complicated", https://zatomarketing.com/blog/should-you-always-exclude-brand-from-performance-max-campaigns-its-complicated · **Tier** 1 · **Date** 2022-12-15 (updated 2026-04-21) · **Claim**: Bottom-funnel brand is the case for segmenting out (illustrative 18 ROAS brand vs 3 non-brand), because those users would convert via direct/organic/email anyway; for household brands, brand searches sit in the interest stage and behave like mid-funnel keywords. · **Evidence**: experience.

8. **Source**: Miles McNair, PPC Mastery — "TPE #145: Why bid adjustments are dead", https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: Target Impression Share, like the other Smart Bidding strategies, ignores most bid adjustments; device −100% exclusions are respected. · **Evidence**: Google's support table.

9. **Source**: Nils Rooijmans — "[AMA] …15 leads to 6", https://nilsrooijmans.com/daily/ama-we-did-exactly-what-google-told-us-to-do-and-went-from-15-leads-to-6-how-to-fix · **Tier** 1 · **Date** 2026-09-16 · **Claim**: Size a portfolio max-CPC cap at the 90th–95th percentile of CPC on search terms with ≥1 conversion over the prior 10 weeks. · **Evidence**: one reader account.

10. **Source**: Google Ads Help — "About Target CPA bidding" (answer/6268632), fetched 2026-10-13 · **Tier** Reference only · **Claim**: Bid limits exist on portfolio strategies only and Google says setting them "isn't recommended" because they restrict automatic bid optimisation.

## Dissenting view
Williams' 2024 experiment says manual CPC and capped tIS are a wash on a defended brand; Hopkins' data says tIS doesn't improve CPA/ROAS at all and is only usable with a cap; Vallaeys prefers manual CPC when a hard ceiling matters. The live disagreement is whether brand defence should be bought at all when CPCs have risen 10–20× on floor changes (Williams 2024): Williams' answer is "while affordable and incremental", which is a test, not a rule.

## What the platform currently does [Google docs]
- [Google docs via Hopkins 2024 / Williams 2024] Target Impression Share takes a location (absolute top / top / anywhere), a percentage, and a max CPC bid limit; Google's UI suggests the limit and nudges toward absolute-top targets. (Google's tIS help page could not be fetched on 2026-10-13; details taken from the practitioner descriptions above.)
- [Google docs via Williams 2023] Reserve prices from Ad Rank thresholds apply even with no competitor; ineligible auctions are excluded from IS.
- [Google docs via Williams 2024] Google introduced "attributed brand search" metrics (ZATO sitemap lists the post; not fetched) — platform framing that brand searches are an outcome of other campaigns.
- [Google docs via McNair 2026] tIS ignores most bid adjustments except device −100% exclusions.

## Baseline check
Read `google-ads-bidding` ("Brand Search: Manual CPC or Target IS — protect brand terms efficiently"; tIS "ignores conversion efficiency"). Baseline names the two options and stops. This skill adds: the experiment result and its settings (92% / cap above avg CPC), the cross-account finding that tIS needs a cap, the reserve-price reason uncontested brand still costs money, the incrementality test and the "kill if not incremental" rule, the higher-ROAS-target position for brand, and the decision between tIS, manual and not bidding.

## Judgment calls
- Took the position: defend with tIS only with a cap, target set to historical IS not 100%, and only after auction insights shows a real competitor; otherwise manual CPC at a low bid to collect the reserve-priced clicks cheaply; run a geo holdout once a year to test incrementality.
- Treated Williams' single experiment as the best available evidence, with its non-significance stated.
- Google's tIS help page failed to fetch; platform behaviour is attributed through practitioner descriptions and flagged.

## Canon strength: Strong
Four Tier 1 pieces from Williams (one controlled experiment), Hopkins' cross-account data, Vallaeys.

## Invalidated by
Google removing the bid limit from Target Impression Share, changing Ad Rank reserve pricing on uncontested auctions, or restricting competitor brand bidding by policy.
