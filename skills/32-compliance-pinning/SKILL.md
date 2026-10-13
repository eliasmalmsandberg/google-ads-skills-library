---
name: compliance-pinning
id: 32
description: How to build RSAs for finance, health, legal and other verticals where a disclaimer or required phrase must appear on every impression — which slot, how many variants, how many free lines. Not the general pin strategy (24) or the writing spec (23).
tags: Strategy / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Change to which slots are always shown (H1/H2/D1); a native advertiser-controlled disclaimer field for Search RSAs; AI Max text customisation becoming mandatory or ignoring text guidelines.
---
## What this is
A build rule for RSAs that carry mandatory text. The constraint is simple and often violated: only H1, H2 and D1 are shown on every impression, so a disclaimer pinned to H3 or D2 is not a disclaimer. Around that, the skill applies the pinning evidence — two or three variants per pinned slot, never one; never pin everything — so compliance does not become the full-pinned configuration that costs the most.

## Where it comes from
Frederick Vallaeys / Optmyzr (SEJ 2021: legal pinning and the two-variant rule; 2026 ~20,000-account study), Optmyzr 2022 RSA study (93,055 RSAs), Navah Hopkins / Optmyzr (2024), Brad Geddes / Adalysis (2022 "targeted pinning" and testing method; Adalysis checklist). Slot guarantees and AI Max text controls from Google Ads Help and the Google Ads API docs, labelled.

## When to use it / when not to
Use when legal, regulatory or brand sign-off requires specific wording in every ad: APR/representative-example lines, "capital at risk", medical-device or prescription qualifiers, "advertising" labels for law firms, licence numbers. Not for lines you merely want shown every time — that is skill 24's hybrid configuration — and not as a reason to pin every slot.

## Inputs
- The required wording(s), with sign-off, and their character counts.
- Which impressions the requirement covers (all? only ads mentioning a product? only when a rate is shown?).
- Ad group volume and combination budget (skill 22 rule 1).
- Whether AI Max text customisation is on anywhere in the campaign.

## Method
1. **Put the required text in an always-shown slot.** H1, H2 and D1 are always shown; H3 and D2 are not guaranteed (Google Ads Help). A disclaimer up to 90 characters goes in D1; a short required phrase up to 30 characters goes in H1 or H2. Nothing mandatory ever sits in H3 or D2.
2. **Pin two or three compliant variants to that slot, not one.** Pinning a single text to a position has the biggest negative impact on CTR, CPC and CPA (Vallaeys, 2021), and ad groups allowing multiple texts in pinned positions got 3.9× the impressions of those that did not (Optmyzr, 2022). Write two or three sign-off-approved wordings of the same disclaimer (different sentence order, "capital at risk" vs "your capital is at risk") and pin all of them to the slot; they rotate (Google Ads API docs). If legal allows only one wording, pin that one and accept the measured cost, and log it as a known drag.
3. **Pin only what is required.** Geddes' "targeted pinning": pin the disclaimer, discount or required statement and let the rest rotate (Adalysis, 2022). Full pinning is the worst configuration on CPA ($32.57 across all accounts; $61.11 with 4.48% CVR in the 268 matched accounts; Vallaeys/Optmyzr, 2026) and usually yields "Poor" Ad Strength plus fewer impressions than a sibling RSA (Geddes, 2022). A compliance ad is a partially pinned ad with one locked slot, not an ETA.
4. **Fill the remaining slots per the data budget.** The required slot removes one position from the combination count; budget the unpinned lines with skill 22 rule 1 (well over 100 impressions per combination; Geddes, 2022). Typical build for a mid-volume ad group: D1 = 2–3 pinned disclaimers; H1 = 2–3 pinned relevance lines (Adalysis checklist pins H1/H2 for data density); H2/H3 and D2 unpinned with 4–6 short headlines (under 20 characters where possible — CPA $9.35 vs $18.27; Vallaeys, 2026) and 1–2 descriptions. Do not fill to 15/4.
5. **Write the free lines so no combination contradicts the disclaimer.** Any random triple must read as one compliant ad (Geddes, 2022, on balance of lines). A "0% interest" headline rotating against a representative-APR disclaimer in D1 is a policy problem the pin map cannot fix; remove the line.
6. **Turn off or fence AI Max text customisation.** Automatically created assets are not listed with the ad's own assets and need a separate removal call (Google Ads API docs, 2026); they can serve beside your pinned disclaimer with wording nobody signed off. In regulated campaigns leave `TEXT_ASSET_AUTOMATION` opted out (the Search default per the API docs). If it must be on, set `Campaign.text_guidelines` term exclusions and messaging restrictions (Google Ads API docs) and treat that as a mitigation, not a control.
7. **Ignore the Ad Strength drop, record the serving share.** Pinning lowers Ad Strength by design and Ad Strength is not an auction factor (Marvin, 2024); a commenter on Geddes' 2022 series saw the drop with no change in impression share. What you do watch: a compliance RSA losing impressions to a less-pinned sibling in the same ad group (Geddes, 2022). If that happens, the fix is more variants in the pinned slot (rule 2), not fewer pins.
8. **Test wording within the rule, never outside it.** The pinned slot is itself a test surface: two compliant wordings pinned to D1 are an A/B on the disclaimer's phrasing, read on conversions per impression once the budget is met (Vallaeys, 2021; Geddes, 2022). Message tests go in H2 per Geddes' position roles (2022).

## What Google will tell you instead, and why we don't
Google's RSA page says pinning "isn't recommended for most advertisers" and the editor lowers Ad Strength as you pin; Google's own disclaimer field type (`TEXT_DISCLAIMER`) is output-only and cannot be set by the advertiser for Search RSAs (Google Ads API docs). We pin because the requirement leaves no choice, and we pin the way the data says costs least: 2–3 variants in one always-shown slot (Vallaeys, 2021; Optmyzr, 2022; Vallaeys, 2026), everything else free (Geddes, 2022). We also decline the Ad Strength prompts to unpin or to add more headlines, because the rating is not a performance measure (skill 25) and more unpinned lines in a compliance ad only raise the odds of a bad combination (rule 5).

## Failure modes
- Disclaimers over 90 characters: they do not fit D1; split the requirement with legal (short qualifier in H2 plus the full text on the landing page) rather than pushing text into D2, which is not guaranteed to show (Google Ads Help).
- Legal permits exactly one wording: rule 2 cannot be met; you carry the single-pin cost (Vallaeys, 2021). Compensate with more variants in the other pinned slot and fewer unpinned lines, and set the client's expectation on CTR.
- Low-volume ad groups: the locked slot helps data density (Geddes, 2022), but if the ad group still cannot clear 100 impressions per combination, pin H1 and H2 too and run cross-ad-group pattern tests only (skill 22 rule 6).
- Multi-market accounts where the required text differs by country: one RSA cannot carry two legal regimes; split by campaign, and do not use location insertion to swap disclaimers (fallback behaviour for location tags is unspecified in the API docs).
- Brand campaigns in regulated verticals: brand name in H1 plus disclaimer in D1 leaves little to rotate; keep one RSA, partially pinned (skill 31 rule 3 logic), rather than two near-identical ads.

## What to measure
Share of impressions where the required line served (should be 100% by construction — verify in the combinations view); impression share between the compliance RSA and any sibling; conversions per impression by pinned-variant wording; count of automatically created assets present in regulated campaigns (target zero); Ad Strength logged, not targeted.

## Open disagreements in the canon
- Pin anything at all: Vallaeys (2021) found no pins best; Vallaeys (2026) and Hopkins (2024) found partial pinning best or tied. For compliance the question is moot — the line must show — and Epiminds follows the newer studies on how to pin it.
- Where the disclaimer lives: no canon source states a slot; Epiminds derives D1/H1/H2 from Google's slot guarantees plus Geddes' targeted-pinning position, and flags this as a judgment.
- How many free lines: no compliance-specific count exists; Epiminds applies the general data-budget rule (Geddes, 2022) and the Adalysis checklist's "don't add 15 because you can".
