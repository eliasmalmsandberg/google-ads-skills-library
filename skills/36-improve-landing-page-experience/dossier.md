# Dossier — 36 Improve Landing Page Experience

## Sources

1. **Source**: Brad Geddes, Acquisio webinar write-up — https://www.acquisio.com/blog/?p=6300 · **Tier** 1 · **Date** undated, c.2016 · **Claim**: from $100M+ spend analysis — landing pages showed no measurable relationship to CPC; below-average landing pages have lower impression share than above-average ones at the same QS (1–6); Adalysis estimated landing page at ~39% of the QS equation (~3.5 points), implying an above-average LP cannot appear below QS 7; QS is calculated at many granular intersections so one number hides it. · **Evidence**: Geddes's own cross-client analysis; weights are estimates.

2. **Source**: Wesley Parker (guest) on Adalysis blog, "10 steps to improving landing page experience" — https://adalysis.com/blog/10-steps-improving-landing-page-experience/ · **Tier** 1 (Adalysis-published; guest author) · **Date** 15 Mar 2016 · **Claim**: ten steps in four groups — ad-to-page match (headline match, all info needed to convert, remove duplicate content), transparency (contact details and registered address, privacy policy in the footer, About page), navigation (land on the advertised product/service page with purchase or enquiry CTA; returns/size guides findable), speed (measure with Pingdom, fix with PageSpeed Insights). Speculates Google's underlying LP assessment is pass/fail with weak correlation to the displayed status. · **Evidence**: checklist from practice; cites Adalysis 39% study and WordStream CPC figure (28.6% for 5→7) which the article itself flags as >3 years old.

3. **Source**: Brad Geddes, Adalysis blog Q&A with reader "Mark" — https://adalysis.com/?p=1848 · **Tier** 1 · **Date** undated (AdWords era) · **Claim**: Google's LP inputs appear to include help-file items (privacy policy, navigation), "supporting words", and long-click/bounce data; no universal good bounce rate (lead-gen runs higher than ecommerce); diagnostic — compare bounce rate, average position and CPC by device for good vs poor pages to see if mobile alone drives the problem; Google keeps QS segmented by device and never indicates a device-specific issue. Google Support told Mark the keywords should be on the general website; Mark disputed it. · **Evidence**: opinion plus one reader's informal review.

4. **Source**: Navah Hopkins, Search Engine Land, "What is quality score and how to use it in PPC" — https://searchengineland.com/quality-score-ppc-394513 · **Tier** 1 · **Date** 2023 · **Claim**: LPE = does the page carry through the ad's promise plus UX — load in ~2 seconds or less, no layout shift within 5 seconds of render, navigation, intent match; use behavioural tools (Clarity, Hotjar); work with SEO; paid landing pages are often better no-index/no-follow. · **Evidence**: practitioner thresholds; no study.

5. **Source**: Brad Geddes, Adalysis, "Six ways Adalysis can help you improve quality scores" — https://adalysis.com/blog/six-ways-adalysis-can-help-diagnose-improve-quality-scores/ · **Tier** 1 · **Date** 16 May 2017 · **Claim**: group landing pages used across ad groups and count keywords above/average/below on each; find pages that need replacing and high-performing pages to replicate; LPE fixes start from the page, not the keyword. Adalysis QS docs: for LPE "look at page speed or consider a new page". · **Evidence**: product method.

6. **Source**: Amy Hebdon, Copyhackers — https://copyhackers.com/write-adwords-ad/ · **Tier** 2 · **Date** 24 Apr 2018 · **Claim**: slow mobile load or unreadable mobile pages lower LPE; missing privacy policy can hurt, inconsistently; don't test a headline and a landing page at once; a gym client doubled conversion rate moving from a dedicated landing page to the full site (conversion, not LPE). · **Evidence**: own client results, no numbers beyond "doubled".

7. **Source**: Optmyzr blog (quotes Aaron Levy) — https://www.optmyzr.com/blog/google-ads-quality-score/ · **Tier** 1, vendor caveat · **Date** 2 Mar 2026 · **Claim**: Levy's LPE checklist — does the page deliver the ad's promise, work on all devices, load quickly; don't make changes solely for QS at the expense of ROAS. · **Evidence**: opinion.

## Dissenting view
Geddes's data says landing page status has no measurable CPC relationship and shows up in impression share instead (Acquisio, c.2016); the WordStream CPC-savings figure that Parker repeats (2016) implies the opposite. The disagreement is whether LPE work pays in price or in eligibility/volume — and therefore which metric proves it worked. Hebdon's gym case (dedicated page → full site doubled conversions) also cuts against the "dedicated landing page" default (2018).

## What the platform currently does [Google docs]
- [Google docs] answer/6167118 (fetched 2026-10-13): LPE rated Above/Average/Below vs advertisers on the exact same keyword, trailing 90 days; information from Google's crawlers may be used to assess ad quality and reflected in QS; device, location, time of day not captured.
- [Google docs] answer/6167130 "5 ways": deliver what the search asks for; "exact search wording doesn't need to appear on the page"; conversion rate "doesn't affect your landing page status"; make the site mobile-friendly and faster.
- [Google docs] Historical LPE column ("Landing Page Exper. (hist.)") available since May 2017 with daily segmentation (SEL/Marvin, 15 May 2017).

## Baseline check
Read `google-ads-quality-score`. Baseline gives the generic list (keyword on page, LCP <2.5s, mobile, trust signals, no interstitials). This skill adds: page-level (not keyword-level) diagnosis, the device-split test from Geddes, the impression-share-not-CPC payoff rule from Geddes's data, Hopkins's 2s/5s thresholds and no-index rule, the shared-page-across-ad-groups triage, and the explicit decision that LPE is the last component to fund.

## Judgment calls
- Parker's piece is on the Adalysis blog under Geddes's byline with a guest credit; treated as Tier 1 outlet / practitioner checklist, with the WordStream CPC figure excluded from the skill.
- The 39% / 3.5-point weight is Geddes's estimate; used only to explain why an above-average LP rarely shows below QS 7, flagged as estimate.
- Google's "exact wording need not appear" is accepted — Geddes's "supporting words" framing agrees; the baseline's "keyword in H1" rule is dropped.

## Canon strength: Adequate
Geddes (data on CPC/impression share; two further pages), Hopkins (thresholds), Hebdon, Levy — 2+ Tier 1/2 with some evidence, but only Geddes brings account data.

## Invalidated by
Google replacing crawler-based LPE with a Core Web Vitals/engagement signal published separately, removing LPE from the keyword report, or changing the exact-same-keyword comparison set.
