# Dossier — 89 Ad rotation settings under Smart Bidding

## Sources

1. **Source** Brad Geddes, Adalysis, "Why Google Ads 'Optimize' often misses your best ad", https://adalysis.com/blog/google-ads-optimize-ad-serving-often-fails/ · **Tier** 1 · **Date** 2018-09-18 (page modified 2026-04-28) · **Claim** "Optimize" rotation misallocates: an ad better on CTR, CVR and conversions-per-impression got ~20× fewer impressions than a weaker ad; new ads either starve (82 impressions in 7 days vs 2,000+ for the incumbent) or get heavy preference regardless of results; when one ad leads CTR and another leads conversions, Google favours the CTR leader; with 4–5+ ads per group serving looked random. In comments: Google applies Optimize to any campaign on Smart Bidding even when rotation is set to Rotate, and this is rarely disclosed. Recommendation: Rotate for serious tests and when adding many new ads; Optimize acceptable if you are not testing. · **Evidence or opinion** A few ad groups from one advertiser, with impression and metric data; one CTR gap noted as not significant.

2. **Source** Brad Geddes, Adalysis, "5 common Google Ads misconceptions (with answers)", https://adalysis.com/blog/5-common-pieces-of-misinformation-about-google-ads-their-corrections/ · **Tier** 1 · **Date** 2019-03-12 · **Claim** "Optimize ad rotation showing the worst ads" listed as a common automation failure; Google's automated ads are "great at CTR and terrible at conversion rates"; humans are better at ad testing and auditing the machine. · **Evidence or opinion** Opinion, no figures.

3. **Source** Brad Geddes, Adalysis, "Data study: What 5,900 accounts reveal about RSA pinning", https://adalysis.com/blog/data-study-5900-accounts-rsa-pinning/ · **Tier** 1 · **Date** 2026-10-13 · **Claim** 5,900+ accounts, ads ≥30 days, ≥250 impressions, ≥1 conversion, unbranded, URL-expansion campaigns excluded. "Google also often falls back on CTR for ad serving." Weighted: CTR falls and CVR rises with more pinning; unweighted: conversions per 1,000 impressions rise steadily with pinning. Unpinned RSAs average 13.53 headlines; 69% use 15. Pin-3 ads are also the most actively tested, so pinning alone may not explain CVR. · **Evidence or opinion** Observational cross-account study; vendor sells the RSA tooling. Used here for the CTR-serving claim and for the "control the test through pins" alternative.

4. **Source** Google Help, "About ad rotation", https://support.google.com/google-ads/answer/112876 · **Tier** Reference · **Date** undated · See platform section.

5. **Source** Google Help, "About applying recommendations automatically", https://support.google.com/google-ads/answer/10279006 · **Tier** Reference · **Date** undated; AAR "Add RSAs" removed 2026-01-26 · **Claim** "Using optimized ad rotation" is an auto-apply recommendation in the Ads & assets category.

Not canon, context only: Aaron Slusky, Search Engine Land (~2015), starts with "Rotate indefinitely" to test, then tests Optimize for conversions; notes Google once removed Rotate indefinitely and restored it after community pushback. No data. Menachem Ani, SEJ 2024-06-11, keeps the "optimized ad rotation" auto-apply enabled while disabling AARs that change bids/budgets/targeting. No data.

Not reached: Optmyzr's RSA-count-per-ad-group study (URL guesses failed; search budget exhausted). PPC Mastery RSA testing material not reachable without search. Stated as a gap.

## Dissenting view
Menachem Ani (SEJ, 2024) and Google both treat optimized rotation as benign enough to auto-apply. Geddes (2018, 2019, 2026) says Optimize is tuned for clicks and misallocates against conversion winners. The disagreement is about *what the test is for*: if the account is not running ad tests, Optimize's occasional good calls beat nothing (Geddes concedes this, 2018); if it is, Optimize corrupts the test. Under Smart Bidding the platform removes the choice, so the real disagreement collapses into whether to test ads at all via rotation, or via other instruments.

## What the platform currently does [Google docs]
- [Google docs] Two options in Search, Shopping and Display: "Optimize" (ads tuned for *clicks* per auction using keyword, search term, device and location signals; serving stays roughly even when ads perform similarly or traffic is low; Ad Rank still gates serving) and "Do not optimize" (ads enter auctions more evenly, indefinitely; not recommended by Google; quality differences still produce uneven impression share). No default stated on the page. "If you use Smart Bidding, which prioritizes conversions, Google Ads will automatically use the 'Optimize' ad rotation setting." The page does not say whether a "Do not optimize" selection is honoured in that case. https://support.google.com/google-ads/answer/112876
- [Google docs] "Using optimized ad rotation" is an available auto-apply recommendation. https://support.google.com/google-ads/answer/10279006
- [Google docs, via Geddes comments 2018] Smart Bidding campaigns are served with Optimize regardless of the rotation setting.
- Historical [SEL Slusky]: Google removed "Rotate indefinitely" once and restored it after pushback (undated, pre-2016).

## Baseline check
Read `google-ads-account-audit` (no mention of ad rotation) and `google-ads-ad-copy` not read (out of scope for this agent's category; the baseline list has no rotation skill). The baseline audit does not say that the rotation setting is moot under Smart Bidding, that Optimize is click-tuned, or how to test ads when rotation cannot be controlled. This skill adds the decision table and the substitute testing instruments.

## Judgment calls
- Position: the rotation setting is irrelevant on Smart Bidding campaigns (Google Help plus Geddes 2018); set "Do not optimize" only on Manual/Enhanced CPC campaigns that are actively testing. On Smart Bidding, ad testing moves to pinned-variant RSAs, Ad variations experiments and asset-level reporting — the pinning path leans on Geddes 2026, which is observational.
- The "two RSAs per ad group during a test, one otherwise" rule is Epiminds' operating rule, consistent with Geddes 2018's "4–5+ ads looks random" finding; flagged as such. The Optmyzr RSA-count study would have been the proper source and could not be fetched.
- Ani (SEJ) excluded from claims; cited as the opposing position only.
- Post-review: the Ad variations claim ("only serving control Google still honours") had no source and is relabelled an Epiminds operating rule; the "bidding loss outweighs testing gain" comparison is labelled Epiminds judgment (Geddes 2018 mentions advertisers dropping Smart Bidding over Optimize, but no comparison exists); the "few hundred impressions a week" low-traffic line is labelled an operating approximation.

## Canon strength: Adequate
Three Adalysis sources, one with cross-account data (2026), one with small-sample data (2018), one opinion (2019) — all one practitioner. No second Tier 1 voice on rotation specifically was reachable.

## Invalidated by
Google honouring "Do not optimize" under Smart Bidding; Google re-tuning Optimize to conversions rather than clicks; removal of the rotation setting entirely; Ad variations experiments being withdrawn.
