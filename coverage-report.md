# Coverage report — Phase 2 coverage pass

Date: 2026-10-13
Scope: the 90 rows in `google-ads-skills-index.xlsx` (via `_build/rows-*.json`) checked against (a) what the canon's Tier 1 practitioners treat as core, recurring method on their own sites, and (b) PPC OS's publicly visible structure. Only public pages were used; no paid PPC OS content was read or reproduced.

## 1. Method

1. Read `canon.md` (Tier 1 list, PPC OS benchmark note) and all 90 index rows (title, tags, "Use when").
2. For each Tier 1 practitioner, fetched their own site index, sitemap or author page and listed the recurring topics. WebSearch was unavailable for this run (shared search budget exhausted), so everything below comes from direct WebFetch of the practitioners' own pages; where a sitemap was truncated or blocked by robots, that is noted.
3. For PPC OS, fetched the public hub page and the public newsletter index, plus three public newsletter issues that expose audit/diagnostic framing.
4. Candidate = a method that (a) recurs on at least one Tier 1 site or the PPC OS public structure as a named skill/check, and (b) has no existing row covering it by title or "Use when", and (c) is not a sub-topic of an existing row. Sub-topics were skipped and are listed in §5 so the next pass does not re-propose them.

## 2. What was inspected (URLs)

PPC Mastery / PPC OS (public only)
- https://www.ppcmastery.com/hub — PPC OS section: skills list and sample outputs; Success Path course names
- https://www.ppcmastery.com/ — home; free "Audit Templates" offer, course/paths counts
- https://www.ppcmastery.com/newsletter — public issue index (TPE #144–#152)
- https://www.ppcmastery.com/newsletter/tpe-149-real-ai-account-audit — public audit walkthrough (4 phases, 13 named audits)
- https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead
- https://www.ppcmastery.com/newsletter/tpe-144-growth-vs-efficiency-why-you-can-t-maximize-both-and-how-to-choose
- sitemap.xml: fetch failed

Optmyzr / Vallaeys / Hopkins
- https://www.optmyzr.com/blog/ — index (15 posts + Town Hall)
- https://www.optmyzr.com/en/sitemap.xml — ~70 blog slugs (truncated)
- https://www.optmyzr.com/blog/google-ads-audit/ — 9-section audit (content-marketing byline, low weight)
- https://www.optmyzr.com/blog/protect-smart-bidding-from-spam/ — spam-conversion method (vendor byline, method only)
- https://www.optmyzr.com/blog/when-to-stop-using-smart-bidding/ — Vallaeys, May 2026, 50 conv/30d rule
- https://searchengineland.com/author/frederick-vallaeys — 18 articles (automation layering, PMax search terms, scripts, Bayesian incrementality)
- https://www.searchenginejournal.com/author/navah-hopkins/ — 30 "Ask a PPC" articles (learning periods, overspend with tROAS, click fraud, audits, no impressions, budget stages, tracking pitfalls)

Adalysis / Geddes
- https://adalysis.com/blog/ — index + guides (RSA handbook, QS algorithm, ad testing guide)
- https://adalysis.com/post-sitemap.xml — 116 slugs (truncated)
- https://adalysis.com/blog/evaluate-ai-max-performance/ — Geddes, Aug 2026
- https://adalysis.com/blog/launching-a-new-search-campaign-what-to-watch-in-the-first-month/ — Geddes, 2025
- (sitemap also shows the "KPI monitoring diagnosis" series: why CPC/CTR/clicks/conversions/IS changed; extension-data analysis; bid adjustments by bidding method; underspending; redundant keywords; audience bid adjustments under tCPA/tROAS)

ZATO / Kirk Williams
- https://zatomarketing.com/blog/ — index
- https://zatomarketing.com/topics/google-ads — 28 posts (campaign not serving, conversion tracking clean data, how to scale, brand bidding test, auction insights, Ad Strength)
- https://zatomarketing.com/topics/google-merchant-center — 21 posts (feed-first management, product_type / GPC / id / description optimisation, suspension for misrepresentation, excluded destinations, disapproval prevention)
- https://searchengineland.com/author/kirk-williams — 8 older articles (structure, tracking, keyword role)

Mike Rhodes
- https://www.mikerhodes.com.au/ and its sitemap — blocked by robots
- https://8020agent.com/ — metadata only: profit curve, budget optimisation, break-even ROAS
- https://github.com/mikerhodesideas and /free — script folders: pmax-assets, pmax-placements, pmax-search-terms-v4, products, check-product-data, check-video-waste-mcc, keyword_v_search, landing-page, ngram, ocid, search-term-alert, black-friday-dashboard

Nils Rooijmans
- https://nilsrooijmans.com/ and https://nilsrooijmans.com/free-google-ads-scripts-the-ultimate-list/ — 22-script public catalogue (budget overdelivery, close variants, negative conflicts, n-gram, high CPC alerts, redirects, search partner ROAS, feed update frequency, disapproved products/ads, past violations, missing RSA ad groups, trending search terms, PMax trending categories / non-converting terms / placement suggestions, gender bid adj, monthly budget alert, change history alerts, negative suggestions, Lin-Rodnitzky ratio)
- https://nilsrooijmans.com/google-ads-script-lin-rodnitzky-ratio/

Brainlabs
- https://www.brainlabsdigital.com/blog/ — 12 recent posts; no script posts on page 1 (script posts live on Search Engine Land and are older)
- https://www.brainlabsdigital.com/performance-max-channel-controls/ — alpha feature, not launched

Andrea Cruz
- https://searchengineland.com/author/andrea-cruz — 15 articles (PMax for B2B 2026, "optimizing when keywords matter less" 2026, B2B Google Ads limitations)

## 3. PPC OS public structure as found (hub page, 2026-10-13)

Skills named on the public hub, with the public one-line framing:
- Performance Analysis — trends, the "why" behind metric shifts, actions ranked by impact; sample output "Weekly Review"
- Account Audit — "24 diagnostics across 5 modules"; critical issues ranked by impact (module names not public)
- Search Terms — mines large search-term exports, high-intent queries, n-gram negatives, Editor CSV
- Quality Scores — three components, keywords with biggest CPC impact
- Landing Pages — "6-pillar structural audit per LP": hero, benefits, social proof, page speed, copy/messaging, guarantee
- RSA & Ad Copy — "15+ headlines tagged by purpose", CSV export
- Competitor Research — differentiation gaps, messaging opportunities
- Tracking Audit — "50-point check" across tags, conversions, attribution, consent; named checks: Enhanced Conversions, Consent Mode v2, Offline Conversion Tracking, Attribution model, Duplicate conversion actions, Primary/secondary classification
- Offer Strategy — six pillars: value prop, differentiation, risk removal, urgency, social proof, specificity
- Bids & Budgets — audits and validates targets, reallocates budgets, tracks CPC trends
- Feeds — titles and secondary attributes, supplemental feed CSV
- pMax — brand share, overlap with other campaigns, non-brand ROAS
- Account Health Report — sub-scores: Tracking, Campaign Structure, Landing Pages, Quality Scores, Ad Quality (RSAs)

Success Path courses (public names): Google Ads Success Formula; Goal Setting Mastery; Conversion Tracking Mastery; Bids & Budgets Mastery; Search Mastery (launch checklist); Performance Max Mastery; Shopping Mastery; Landing Page Mastery; Google Ads Basics. Vault: dashboards, scripts, optimisation checklists, target calculators.

Public newsletter audit framing (TPE #149): Phase 1 Context (30+ business questions: goals, growth vs efficiency, LTV, margin, payback); Phase 2 "13 small audits that stack": conversion tracking, the offer, account structure, keywords, search terms, bid strategies, budgets, competitor comparison, placements, Quality Scores, campaign settings, landing pages, RSAs; Phase 3 Trends across 7/30/90/365-day windows; Phase 4 Roadmap by impact vs effort.

## 4. Coverage verdict per Tier 1 source

| Source | Covered well by existing rows | Core methods with no row |
|---|---|---|
| Mike Rhodes | PMax insights script (69), placements (60), brand cannibalisation (59), n-gram (10/70), keyword-vs-search-term (11) | Product-level performance bucketing (products script); PMax asset/asset-group review (pmax-assets); profit curve / break-even ROAS for targets and budgets (8020agent) |
| Vallaeys / Optmyzr | Ad Strength (25), RSA count (31), broad match (16), portfolio caps (40), VBB (42), PMax search terms (57) | Bid strategy selection incl. when to leave Smart Bidding (May 2026); automation layering as a strategy; budget reallocation; spam-conversion contamination |
| Geddes / Adalysis | QS components (34–38), ad testing significance (82), RSA testing (22/26), IS decomposition (84), negative conflicts (21), close variants (11), auction insights (83) | KPI-change root-cause series (why CPC/CTR/clicks/conv changed); AI Max evaluation (Aug 2026); bid adjustments by bidding method; first-month launch watch; ad assets/extension analysis; underspending (partly 46) |
| Kirk Williams / ZATO | Custom labels (64), feed rules (65), titles (66), MC diagnostics (67), sculpting (68), feed-only PMax (56), tIS brand defence (45) | Feed attributes beyond titles (product_type, GPC, id); MC account suspension recovery; campaign-not-serving diagnosis; scaling method |
| Nils Rooijmans | n-gram (70), negative conflicts (74), close variants (11), pacing (71), disapproval alerts (75), PMax negatives (62), placements (60) | Change-history alerts; Lin-Rodnitzky ratio; (high-CPC alert and redirect check are sub-topics of 40 and 73) |
| PPC Mastery (public) | RSA/pinning (23/24), structure under Smart Bidding (2/9), PMax structure (58), conversion value rules (41) | Account audit, tracking audit, performance analysis/weekly review, target setting from unit economics, growth-vs-efficiency scaling, bid adjustments under Smart Bidding, landing page audit, launch checklist |
| Brainlabs | QS tracker (37), n-gram (70), wasted spend (76) | None new that passes the canon rule; PMax channel controls is unlaunched (not proposed) |
| Andrea Cruz | PMax diagnostics (59/57), VBB (42), OCI (48) | AI Max / "optimising when keywords matter less" (joins the AI Max row); PMax for B2B is a sub-topic of 58/63 |
| Navah Hopkins | Micro-conversions (43), brand defence (45), auto-apply (78), budget pacing (71) | Learning periods and what resets them; click fraud / invalid traffic; no-impressions diagnosis; regular audit cadence |

## 5. Considered and skipped (sub-topic or out of scope)

- PMax channel controls (Brainlabs, Sep 2026) — alpha, unconfirmed by Google; revisit when launched.
- Google AI Brief (Vallaeys, Jun 2026) — too new, no practitioner method yet.
- Offer Strategy six-pillar score (PPC OS) — not a Google Ads method; out of library scope.
- Competitor messaging research (PPC OS) — sub-topic of 83 Auction insights + 23 Write RSAs.
- Custom segments / affinity lists (ZATO, Adalysis) — sub-topic of Audiences rows 50–54.
- Account-level mobile app exclusion (Nils, Adalysis) — sub-topic of 60 and 88.
- Duplicate/redundant keywords (Adalysis, Optmyzr) — folded into the Account audit row.
- Daily budget overdelivery alerts (Nils, Hopkins) — sub-topic of 71.
- Conversion value rules (ZATO 2026, TPE #145) — covered by 41.
- Lead quality with CRM data (SEL Aug 2026) — covered by 42/48.
- Demand Gen placements (PPC OS audit) — outside the Search/Shopping/PMax campaign-type vocabulary.
- Primary/secondary conversion actions, duplicate actions, Consent Mode v2 — inside the proposed Tracking audit row, not separate rows.

## 6. Proposals (23)

Library-level audit rows (PPC OS exposes these framings publicly; the library has none):
1. Full account audit — multi-module diagnostic (P1)
2. Conversion tracking audit (P1)
3. Weekly account review routine (P2)

Method rows:
4. Performance change root-cause diagnosis (P1)
5. Bid strategy selection — Smart Bidding vs manual, target vs maximise (P1)
6. Targets from unit economics — break-even ROAS, profit curve, growth vs efficiency (P1)
7. Smart Bidding learning period — what resets it, change-size rules (P1)
8. AI Max for Search — test design and evaluation (P1)
9. Product performance bucketing for Shopping/PMax (P1)
10. Bid adjustments under Smart Bidding — what still applies (P2)
11. Budget reallocation across campaigns by marginal return (P2)
12. Scaling without breaking efficiency — budget and target step rules (P2)
13. Campaign not serving / zero impressions troubleshooting (P2)
14. New Search campaign launch checklist and first-30-days watch (P2)
15. Ad assets (sitelinks, callouts, snippets, images) — build and evaluate (P2)
16. Feed attribute optimisation beyond titles (P2)
17. Merchant Center account suspension recovery (P2)
18. PMax asset group and asset performance review (P2)
19. Spam conversions and invalid traffic polluting Smart Bidding (P2)
20. Landing page audit for paid search (P2)
21. Automation layering — guardrail automations over Google's automation (P2)
22. Change history monitoring (P3)
23. Lin-Rodnitzky ratio as a search-term health metric (P3)

The row-level JSON (tags from the index vocabulary) was returned to the coordinator with this report. None of the 23 duplicates an existing title or "Use when".
