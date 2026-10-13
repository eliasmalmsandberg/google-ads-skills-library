# Dossier — 51 Customer Match as signal vs. target

Research note: the shared WebSearch budget ran out partway through this category, so sourcing was done by fetching canon sites and author archives directly. Search Engine Land's site search and Sophie Fell's author page were blocked (robots / HTTP 429). Optmyzr, Adalysis, Brainlabs, Nils Rooijmans and PPC Mastery archives were checked and have no Customer Match-specific posts in their visible listings.

## Sources

1. **Source**: Andrea Cruz (VP Media Strategy B2B, Monks), Search Engine Land, "What are you optimizing for in paid search when keywords matter less?", https://searchengineland.com/what-are-you-optimizing-for-in-paid-search-when-keywords-matter-less-475565 · **Tier** 1 · **Date** 2026-04-27 · **Claim**: Google's bidding now weights Customer Match / first-party data above the query itself — after a Data Manager API integration the system "knows which users in the auction match your closed-won deals". B2B match rates are "notoriously stubborn"; fix by enriching via integration partners and clustering contacts by shared pain point rather than one-to-one list matching. Remarketing lists capture a "verified intent state". Feed mid-funnel events (whitepaper, webinar) that precede large contracts; poor lead data in → poor leads out. · **Evidence or opinion**: Opinion from 15+ years of B2B accounts; no data.

2. **Source**: Andrea Cruz (Tinuiti), Search Engine Land, "Why Performance Max looks different for B2B in 2026", https://searchengineland.com/why-performance-max-looks-different-for-b2b-in-2026-467876 · **Tier** 1 · **Date** 2026-01-26 · **Claim**: Import a customer list so the system can model similar characteristics; website remarketing audiences "don't deliver the same level of performance as first-party customer data"; down-funnel conversion signals are the foundation. · **Evidence or opinion**: Opinion; no figures.

3. **Source**: Fred Vallaeys (Optmyzr) with David Newson, PPC Town Hall, "What do you optimize for when the sale happens 2 years later?", https://www.optmyzr.com/ppctownhall/optimize-ppc-long-sales-cycles · **Tier** 1 · **Date** 2026-08-12 · **Claim**: GCLID offline import only reaches back ~90 days from click, so for long cycles feed a proxy signal back to Google within two weeks rather than waiting. Prediction models scoring engagement (blog reads, newsletter sign-ups) can estimate who converts two years out; a local model can find commonalities in CRM data and pass them to platforms without handing over the raw list. Wealth-management-sized volumes make offline data hard to use. · **Evidence or opinion**: Method and one practitioner's account; no cross-account data.

4. **Source**: Navah Hopkins, Search Engine Land, "First-party data: 4 internal checks to make sure you're ready", https://searchengineland.com/first-party-data-core-questions-383035 · **Tier** 1 · **Date** 2022-03-24 · **Claim**: Email-only lists impede match rate; her experience puts match rate "closer to 70%" when lists are set up for sync across platforms; use CRM sync integrations rather than manual download; Google confirmed brands may use up to five domains in a first-party data set. · **Evidence or opinion**: Practitioner experience; the 70% and five-domain figures are unsourced.

5. **Source**: Navah Hopkins, Search Engine Land, "A PPC guide to permission-based audiences", https://searchengineland.com/a-ppc-guide-to-permission-based-audiences-391228 · **Tier** 1 · **Date** 2023-01-12 · **Claim**: First-party audiences improve PMax via audience signals and seed similar-user modelling; native audiences are already inside Smart Bidding, which is the reason to hand bidding to the network; use observation mode to see audience composition and exclude bad segments; either exclude and let Smart Bidding work, or go manual bidding with bid adjustments — not both. · **Evidence or opinion**: Opinion plus one Q3-2022 pop-up example (12.5% engagement, 27% conversion) that measures the offer, not Customer Match.

6. **Source**: Miles McNair (PPC Mastery), TPE #145 "Why bid adjustments are dead and what to do instead", https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: Under tCPA/tROAS/Max Conv/Max Conv Value, Google mostly ignores bid adjustments although the UI still offers them; only -100% device works as an exclusion. Conversion value rules (Max Conv Value / tROAS only) can apply to audiences, with a hierarchy of Customer Match → your data/similar → affinity/in-market → detailed demographics; he generally advises against value rules because reported values are inflated (a 50% rule on a €100 sale reports €150). · **Evidence or opinion**: Practitioner position; no study data.

7. **Source**: Sarah Vlietstra (ZATO), "Stop Wasting Ad Spend: A Guide to Audience Segment Exclusions", https://zatomarketing.com/blog/stop-wasting-ad-spend-a-guide-to-audience-segment-exclusions · **Tier** 1 (ZATO outlet) · **Date** 2026-08-19 · **Claim**: Exclude existing purchasers and lead-form submitters from new-customer campaigns (optionally all site visitors); exclude existing users searching brand to reach a login page from brand/Shopping campaigns; exclusions now work in Search, Display, Shopping and PMax. · **Evidence or opinion**: Method; no account data.

Reporting (not canon, context only): Greg Finn, Search Engine Land, 2022-05-04, https://searchengineland.com/google-ads-customer-match-lists-smart-bidding-optimized-targeting-384922 — reports the auto-inclusion announcement and advises reviewing each account's lists because opt-out is per account. Anu Adegbola, Search Engine Land, 2025-02-13, https://searchengineland.com/google-tightens-customer-match-data-rules-in-major-privacy-update-451887 — reports the 540-day cap effective 2025-04-07.

Rejected on inspection (fail inclusion rule — no method evidence, vendor/agency marketing): Seer Interactive (Scott Thomas, 2025-02-19), PPC Hero (Kelvin Newman, 2024-07-23).

## Dissenting view
Kirk Williams (ZATO, 2026-04-28, https://zatomarketing.com/blog/ecommerce-remarketing-in-google-ads-what-actually-works) argues against blanket-excluding past converters — "many brands wrongly exclude or fold them into general visitor pools" — and wants a deliberate strategy for them instead. Vlietstra (same agency) recommends excluding purchasers from acquisition campaigns. The disagreement is about whether a past-customer list's default job is exclusion or a separately-messaged target; both agree it should not be left as an undifferentiated signal.

## What the platform currently does [Google docs]
- Since Q2 2022 campaigns on Smart Bidding or optimized targeting automatically use all Customer Match lists in the account as signals, whether or not a list is applied to the campaign. Rollout: YouTube Q4 2022, Search and Demand Gen Q3 2023, Shopping and Gmail Q1 2024. Opt-out is an account-level checkbox ("Use all Customer Match lists in Smart Bidding or Optimized Targeting"); not available at MCC level; lists already applied keep being used after opt-out. Manual bidding does not use the lists. (https://support.google.com/google-ads/answer/10550383)
- Membership duration is capped at 540 days (enforced 2025-04-07). A list stays eligible only if ≥100 members were added or updated in the last 540 days. (10550383; 6379332)
- Google's refresh guidance: manual uploads weekly on a fixed day; API/Data Manager appends at least daily; "conversion-based customer lists" + enhanced conversions update in real time. Most advertisers' match rates fall between 29% and 62% (Google data footnoted Jan 2021–Dec 2022). (https://support.google.com/google-ads/answer/10010286)
- Google recommends Data Manager / Data Manager API over the Ads API for new integrations. (10550383)
- Since early March 2024 Customer Match lists no longer serve on Google Partner Inventory / third-party exchanges in the EEA, UK and Switzerland; owned-and-operated inventory only. (6379332)
- Similar segments were retired; optimized targeting is on by default and uses first-party segments as hints; optimized targeting respects customer-data exclusions. (https://support.google.com/google-ads/answer/12463119)
- Lookalike segments exist only in Demand Gen and since Feb 2026 act as a bidding signal rather than a targeting boundary (ZATO reporting, 2026-04-21; Google: 2497941).
- GA4 Customer Match (open beta) supplements exported GA4 audiences with hashed user-provided data. (https://support.google.com/analytics/answer/15606276)

## Baseline check
Read `google-ads-audiences` and `google-ads-audit-leadgen`. The baseline says "add Customer Match to all campaigns in Observation mode" and states a 1,000-user minimum and 40–60% email match rates with no source. This skill replaces that with the actual platform behaviour (lists are used as signals whether or not applied, since 2022–2024), the decision rule for when a list should still be applied as an exclusion or a target, the 540-day/100-member eligibility maths, and a refresh cadence derived from Google's documented limits and Vallaeys' two-week proxy-signal rule.

## Judgment calls
- Treated the Hopkins 2023 piece as hers: the article page shows no byline but her Search Engine Land author archive lists it.
- Treated ZATO's Sarah Vlietstra as Tier 1 by outlet (ZATO is a Tier 1 practitioner shop) while noting her pieces carry no account data.
- The baseline's "1,000 minimum" is not in current Google docs; the only documented threshold is 100 active members per 540 days. The skill uses the documented one.
- Finn (SEL news) and Adegbola (SEL news) are cited as reporting of platform changes, not as practitioner authority.

## Canon strength: Adequate
Five Tier 1 sources with method and positions; evidence is practitioner experience and Google's own match-rate range, not a cross-account study.

## Invalidated by
Google removing the account-level auto-inclusion opt-out, changing the 540-day cap or 100-member eligibility rule, or making Customer Match available as a Smart Bidding signal under manual bidding.
