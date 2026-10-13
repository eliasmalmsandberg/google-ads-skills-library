# Dossier — 24 Pinning strategies

Research note: WebSearch budget exhausted mid-category; sources reached by direct fetch. No public PPC Mastery page on pinning could be reached (their newsletter index showed no RSA issue); the "Why I almost never pin" podcast found in search is Rothman PPC, not canon, and was not used.

## Sources

- **Source:** Frederick Vallaeys, Optmyzr — "We analyzed ~20,000 Google Ads accounts", https://www.optmyzr.com/blog/google-rsa-performance-study/ · **Tier** 1 · **Date** 2026-04-06 · **Claim:** All accounts: partial pinning led on CPA ($13.68), CTR (11.88%), ROAS (365.15%), CVR (10.55%); full pinning worst CPA ($32.57) and CTR (8.49%). 268 common accounts: partial and no pinning similar CPA (~$26), partial better CTR and ROAS; full pinning best ROAS but CPA $61.11 and CVR 4.48%. Recommendation: partial pinning (pin a core message), avoid full pinning. · **Evidence:** ~20,000-account study with a common-account subset.
- **Source:** Navah Hopkins, Optmyzr — "Ad Strength & Creative Study", https://optmyzr.com/blog/google-ad-strength-study · **Tier** 1 · **Date** 2024-09-09 · **Claim:** Some pinning best for CPA, ROAS, CPC; no pinning close second on CPA; conversion rates suffered when assets were pinned; fully pinned had best CTR by a small margin; overall pinning is flat vs none except ROAS, so it is a creative/brand decision; leave room for Google, avoid headlines dropping into description slots. · **Evidence:** 22,000+ accounts, 1M+ ads.
- **Source:** Optmyzr (Balakrishnan) — "Optmyzr study: RSA performance", https://www.optmyzr.com/blog/optmyzr-study-responsive-search-ad-performance/ · **Tier** 1 · **Date** 2022-08-17 · **Claim:** Over 93,055 RSAs: pinning every position gave strong CTR and CVR (advertisers recreating ETAs); CTR much better when only one text was pinned per position; impressions per ad group 3.9× higher when multiple texts were allowed in pinned positions. Pin only when necessary (legal/disclaimer); don't pin everything to imitate an ETA. · **Evidence:** cross-account study.
- **Source:** Frederick Vallaeys, SEJ — "How To A/B Test Responsive Search Ads", https://www.searchenginejournal.com/how-to-test-responsive-search-ads/429270 · **Tier** 1 · **Date** 2021-12-17 · **Claim:** No pins gave best CTR with lower CPC and CPA; pinning a single text to a position had the biggest negative effect on CTR, CPC and CPA; if you want control give each pinned position at least two variations; some industries must pin for legal reasons. · **Evidence:** Optmyzr data.
- **Source:** Brad Geddes, Adalysis — "How to test RSAs in Google Ads and Microsoft Ads", https://adalysis.com/blog/how-to-test-responsive-search-ads-rsa-in-google-ads-and-microsoft-ads/ · **Tier** 1 · **Date** 2022-09-16 · **Claim:** Pinning reduces combinations the machine must test; partially pinned formula is 2–3 assets per headline position; H1 for ad-group relevance, H2 for CTA/benefit, H3 supporting H2; H1 suits location tests, H2 price-vs-discount tests; fully pinning everything usually yields "Poor" Ad Strength and fewer impressions than sibling RSAs; a pinned position blocks unpinned headlines from it; unpinned-only is for large data (50,000+ clicks/month example). · **Evidence:** method plus worked account examples.
- **Source:** Brad Geddes, Adalysis — "RSA optimization series Part 2", https://adalysis.com/blog/rsa-optimization-series-part-2-learn-to-create-and-test-rsas-in-google-ads/ · **Tier** 1 · **Date** 2022-02-23 · **Claim:** Spectrum: no pins (high volume), partial (keyword line to H1), ETA-style (H1–H3 fixed; little room, strength and performance can suffer), hybrid (relevance in H1, USP/CTA in H2 or H3), targeted (disclaimer/offer only). Commenter John: pinning dropped Ad Strength with no change in impression share. · **Evidence:** method.
- **Source:** Adalysis docs — "Ad testing checklist", https://docs.adalysis.com/product/inside-adalysis/ad-testing-checklist · **Tier** 1 · **Date** undated · **Claim:** Partially pin, especially H1 and H2, to improve data density and relevance. · **Evidence:** method.
- **Source:** Brad Geddes, Adalysis — SMX Advanced video post, https://adalysis.com/blog/watch-the-video-of-our-smx-advanced-session-how-to-test-rsas-like-a-pro/ · **Tier** 1 · **Date** 2023-10-03 · **Claim:** (comment reply) pinning is "so underused by smaller companies" who lack the 90,000 impressions to let Google test combinations. · **Evidence:** opinion.

## Dissenting view
Vallaeys (2021) says no pins give the best CTR, CPC and CPA; Vallaeys (2026) and Hopkins (2024) find partial pinning leads or ties. Google's RSA page says pinning "isn't recommended for most advertisers". The disagreement is about what partial pinning costs: in 2021 any single-asset pin hurt; by 2024–2026 the cross-account data shows partial pinning at least neutral and often best, while full pinning is consistently the worst on CPA and CVR.

## What the platform currently does [Google docs]
- [Google docs] About RSAs (answer/7684791): H1, H2 and D1 always shown; H3 and D2 not guaranteed; pinning one asset blocks others from that slot; if every position is pinned, unpinned assets never show; pinning not recommended for most advertisers; suggested approach is 2–3 unique assets per position or one or two keyword headlines pinned; over-pinning similar text lowers Ad Strength.
- [Google docs] Google Ads API RSA overview (updated 2026-09-30): valid pins are HEADLINE_1/2/3 and DESCRIPTION_1/2; several assets pinned to one position rotate; every position must be fillable or the ad is rejected (NOT_ENOUGH_AVAILABLE_ASSET_LINKS_FOR_VALID_COMBINATION).
- [Google docs] Ginny Marvin, SEJ (2024-04-22): pinning lowers Ad Strength; Google recommends pinning two or three assets per position when possible; Ad Strength is not an auction factor.

## Baseline check
Read `google-ads-ad-copy` (mentions pinning H1 for brand only). This skill adds the measured outcomes by pinning level (Optmyzr 2022/2024/2026), the 2–3-per-position partial formula and the H1/H2/H3 role split (Geddes), and the volume rule for when to leave an ad unpinned.

## Judgment calls
- Resolved the Vallaeys-2021 vs 2024/2026 conflict by date (platform changed; newer studies win per canon rule 3) and by evidence size.
- Set the volume threshold for "no pins" from Geddes' 50,000-clicks/month example and 100-impressions-per-combination rule rather than inventing a number.
- Full pinning is permitted only as a deliberate test arm or compliance case (skill 32).

## Canon strength: Strong
Three cross-account studies (Optmyzr 2022, 2024, 2026) plus Adalysis method and account examples.

## Invalidated by
Google changing which positions are guaranteed (H1/H2/D1), allowing pins to more than three headline positions, or making unpinned serving mandatory under AI Max.
