# Dossier — 32 Headline count & pinning for compliance-heavy verticals

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch. No canon source devoted to finance/health/legal ad copy was reachable; the compliance case is handled as a sub-case in the RSA pinning sources, which is what the dossier records.

## Sources

- **Source:** Frederick Vallaeys, SEJ — "How To A/B Test Responsive Search Ads", https://www.searchenginejournal.com/how-to-test-responsive-search-ads/429270 · **Tier** 1 · **Date** 2021-12-17 · **Claim:** Some industries require pinning for legal reasons; if you want control, give each pinned position at least two variations; pinning a single text to a position has the biggest negative impact on CTR, CPC and CPA; pinning multiple assets balances control and performance. · **Evidence:** Optmyzr data.
- **Source:** Optmyzr (Balakrishnan) — 2022 RSA study, https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 · **Claim:** Pin only when necessary (e.g. legal or disclaimer text); don't pin everything to imitate an ETA; CTR much better with one text per pinned position but impressions 3.9× higher when multiple texts allowed in pinned positions (93,055 RSAs). · **Evidence:** cross-account study.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** "Targeted pinning": pin only a disclaimer, discount or required statement and let Google handle the rest; ETA-style full pinning gives Google little room and strength and performance can suffer. · **Evidence:** method.
- **Source:** Brad Geddes, Adalysis — "How to test RSAs", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** A pinned position blocks unpinned headlines from it; fully pinning everything usually yields "Poor" Ad Strength and fewer impressions than sibling RSAs; pinning reduces combinations and speeds learning; partial formula 2–3 per position. · **Evidence:** method and account examples.
- **Source:** Frederick Vallaeys, Optmyzr — "We analyzed ~20,000 accounts", https://www.optmyzr.com/blog/google-rsa-performance-study/ · **Tier** 1 · **Date** 2026-04-06 · **Claim:** Partial pinning led CPA/CTR/ROAS; full pinning worst CPA ($32.57 all accounts; $61.11 and 4.48% CVR in the 268 matched accounts). · **Evidence:** cross-account study.
- **Source:** Navah Hopkins, Optmyzr — "Ad Strength & Creative Study", https://optmyzr.com/blog/google-ad-strength-study · **Tier** 1 · **Date** 2024-09-09 · **Claim:** Pinning should be a creative or brand decision; leave room for Google; avoid headlines dropping into description slots. Descriptions benefit from some length. · **Evidence:** 1M+ ads.
- **Source:** Adalysis docs — "Ad testing checklist", https://docs.adalysis.com/product/inside-adalysis/ad-testing-checklist · **Tier** 1 · **Date** undated · **Claim:** Partially pin H1/H2 for data density. · **Evidence:** method.

## Dissenting view
Google's RSA page says pinning "isn't recommended for most advertisers"; Vallaeys (2021) found any pin costs CTR/CPC/CPA versus none. Against that, Geddes' "targeted pinning" and the 2022/2026 Optmyzr findings support pinning the required line. The disagreement for compliance verticals is narrower than the general one: not whether to pin the disclaimer (everyone agrees you must) but where (which slot is guaranteed to show) and how many variants to pin beside it.

## What the platform currently does [Google docs]
- [Google docs] About RSAs (answer/7684791): H1, H2 and D1 are always shown; H3 and D2 are not guaranteed; pinning one asset blocks the slot; if all positions are pinned, unpinned assets never show; recommended approach is 2–3 unique assets per position; over-pinning near-identical text lowers Ad Strength; 30/90 character limits.
- [Google docs] Google Ads API RSA overview (2026-09-30): valid pins HEADLINE_1/2/3, DESCRIPTION_1/2; several assets on one position rotate; every position must be fillable or the ad is rejected; `TEXT_DISCLAIMER` is an output-only served field type that cannot be pinned by the advertiser; `Campaign.text_guidelines` can set term exclusions and messaging restrictions for AI-generated text when AI Max is enabled; automatically created assets are not returned with the ad's assets and need a separate removal call.
- [Google docs] Ginny Marvin, SEJ (2024-04-22): pinning lowers Ad Strength; Ad Strength is not an auction factor; Google recommends 2–3 assets per position when pinning.

## Baseline check
Read `google-ads-ad-copy` (one line: "regulated industry" as a constraint; pin brand H1) and `google-ads-ad-extensions`. Neither gives the slot-guarantee rule, the two-variant rule for a mandatory line, the cost of full pinning, or the AI Max text risk for regulated copy. This skill adds those.

## Judgment calls
- The "headline count" half of the row title is resolved via the data-budget logic (skill 22) applied to the lines left unpinned, since no source gives a compliance-specific headline count.
- D1 chosen as the home for long disclaimers (90 chars, always shown) and H1/H2 for short required phrases, from the Google slot guarantees plus Geddes' targeted-pinning position.
- Two distinct wordings of the same compliant line are treated as satisfying Vallaeys' two-variant rule; legal sign-off on both is a stated precondition.

## Canon strength: Strong
Three Tier 1 practitioners with cross-account data (Optmyzr 2022, 2024, 2026; Vallaeys 2021) and Geddes' method; Google docs for slot guarantees.

## Invalidated by
Change to which slots are always shown; a native advertiser-controlled disclaimer field for Search RSAs; AI Max text customisation becoming mandatory or ignoring text guidelines.
