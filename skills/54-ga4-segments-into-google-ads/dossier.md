# Dossier — 54 GA4 first-party segments into Google Ads

Research note: shared WebSearch budget was exhausted during this category; sourcing was by direct fetch of canon archives and Google docs. No canon source has a dedicated "GA4 audiences into Google Ads" piece in its visible archive; the practitioner material here is the parts of broader pieces that address GA4-built lists.

## Sources

1. **Source**: Kirk Williams, ZATO, "eCommerce Remarketing in Google Ads: What Actually Works", https://zatomarketing.com/blog/ecommerce-remarketing-in-google-ads-what-actually-works · **Tier** 1 · **Date** 2026-04-28 (updated 2026-05-05) · **Claim**: Do not rely solely on GA4 for conversion tracking and list building; build lists from the Google Tag directly, which "tends to produce more accurate targeting with fewer gaps". Build pageview-without-conversion lists at product-category level; keep past converters as a distinct segment rather than excluding them everywhere; a 30-day all-visitor list performed "surprisingly well" in Demand Gen. Benchmarks: ID parameters should fire ≥60% of the time; product-ID match to the Merchant Center feed ≥90%. PMax may be absorbing standalone remarketing — audit per account. · **Evidence or opinion**: Experience across managed accounts; the thresholds are his own.

2. **Source**: Andrea Cruz, Search Engine Land, "Why Performance Max looks different for B2B in 2026", https://searchengineland.com/why-performance-max-looks-different-for-b2b-in-2026-467876 · **Tier** 1 · **Date** 2026-01-26 · **Claim**: Website remarketing audiences "don't deliver the same level of performance as first-party customer data"; import a customer list; down-funnel signals are the foundation. · **Evidence or opinion**: Opinion.

3. **Source**: Andrea Cruz, Search Engine Land, "What are you optimizing for in paid search when keywords matter less?", https://searchengineland.com/what-are-you-optimizing-for-in-paid-search-when-keywords-matter-less-475565 · **Tier** 1 · **Date** 2026-04-27 · **Claim**: Remarketing lists capture a "verified intent state"; feed mid-funnel behaviours (whitepaper, webinar) that precede large contracts; use on-site experiences so users self-identify. · **Evidence or opinion**: Opinion.

4. **Source**: Fred Vallaeys, Optmyzr PPC Town Hall, "What do you optimize for when the sale happens 2 years later?", https://www.optmyzr.com/ppctownhall/optimize-ppc-long-sales-cycles · **Tier** 1 · **Date** 2026-08-12 · **Claim**: Score engagement signals (blog reads, newsletter sign-ups) to predict who converts years later; feed a proxy within two weeks. A former in-house team used a six-minute on-site visit as an in-market proxy they rated over 80% confident (Newson's account). · **Evidence or opinion**: Method; one practitioner's historical account.

5. **Source**: Navah Hopkins, Search Engine Land, "A PPC guide to permission-based audiences", https://searchengineland.com/a-ppc-guide-to-permission-based-audiences-391228 · **Tier** 1 · **Date** 2023-01-12 · **Claim**: Website traffic and conversions count as first-party audiences only with consent; first-party audiences improve PMax via signals; observation reveals composition. · **Evidence or opinion**: Opinion.

## Dissenting view
Williams (ZATO, 2026) says build lists from the Google Tag, not GA4; Google's GA4 docs and the GA4 Customer Match beta push GA4 as the audience source. The disagreement is about data completeness: GA4 audiences depend on GA4's consent, sampling and identity settings and add 24–48 hours of latency, while a Google Ads tag list is populated directly. Cruz (2026) sits to one side: whichever tag builds them, site-visitor lists underperform customer lists.

## What the platform currently does [Google docs]
- GA4 audiences export to Google Ads once the property is linked and "Enable Personalized Advertising" is on; they appear in the Google Ads shared library. For DV360/SA360, Google signals or user-provided data collection must be on. Audiences export to unlimited destinations. (https://support.google.com/analytics/answer/9267572)
- Limits: 100 audiences per standard property (400 for 360); 10 conditions per audience; 500 characters per condition; archiving is permanent. Membership max 540 days; 14 months with/without "reset on new activity" depending on setting; receiving product applies its own policies. (9267572)
- Latency: a new audience takes 24–48 hours to accumulate; new users take a day or two to be included. Google Ads list size differs from GA audience size. (9267572)
- Backfill: when a Google Ads audience is created, Analytics adds users who met the criteria in the last 30 days; Ads user lists are prepopulated with up to 30 days of data. (9267572)
- GA4 Customer Match (open beta): user-provided data collection + link + personalized ads lets hashed first-party data supplement exported audiences; Google signals not required for consented first-party remarketing. (https://support.google.com/analytics/answer/15606276)
- In Google Ads, observed first-party segments are used as Smart Bidding signals; Search recommends observation. (https://support.google.com/google-ads/answer/7365594)
- Your-data segments can be excluded in Search, Display, Shopping, Video, Demand Gen, PMax. (2549058)

## Baseline check
Read `google-ads-audiences` (funnel-based segment table with durations; "analytics-tracking: GA4 audience import" as a related skill) and `google-ads-audit-leadgen` (GA4 linked check). Neither says which lists belong in GA4 and which in the Ads tag, the 24–48 h / 30-day backfill behaviour, the 100-audience cap, or that site-visitor lists are second-class signals next to customer lists. This skill adds the split rule (GA4 for behavioural/engagement segments the tag cannot express; Ads tag for the transactional lists), the proxy-signal design for long cycles, and the audit thresholds.

## Judgment calls
- Treated Newson's six-minute / 80% figure as an anecdote reported in the Town Hall, attributed to the Town Hall, not as Vallaeys' own claim.
- Williams writes about e-commerce; the GA4-vs-tag position is applied here to lead gen as well, flagged as an extension.
- No canon source gives a minimum list size or a membership-duration rule for GA4-sourced audiences; the skill uses Google's 30-day backfill and 540-day cap as the only numeric anchors and states the durations as Epiminds defaults.

## Canon strength: Adequate
Four Tier 1 sources touch the topic with method or position; none is a study; the central practitioner claim (tag over GA4) is a single-source position.

## Invalidated by
GA4 removing the 30-day backfill or changing the 100-audience cap; GA4 Customer Match leaving beta with different mechanics; Google Ads deprecating tag-based remarketing lists in favour of GA4-only audiences; consent-mode changes that alter which GA4 users are exportable.
