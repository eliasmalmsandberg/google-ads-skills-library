---
name: improve-landing-page-experience
id: 36
description: Decide whether a "Below average" Landing Page Experience is worth fixing, diagnose it at page level (shared pages, device split), and pick the fix that moves eligibility and volume. Not for CRO/conversion-rate work, not for Expected CTR or Ad Relevance (34, 35).
tags: Technique / Search / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google replacing crawler-based LPE with a separately reported Core Web Vitals or engagement signal, removing LPE from the keyword report, or changing the exact-same-keyword comparison set.
---
## What this is
A page-level procedure for the Landing Page Experience component. The core position comes from Geddes's cross-client data: LPE status showed no measurable relationship to CPC, but below-average pages had lower impression share than above-average pages at the same QS (Geddes/Acquisio, c.2016). So LPE work is an eligibility and volume lever, not a price lever, and it is diagnosed per URL, not per keyword (Adalysis, 2017).

## Where it comes from
Geddes's $100M+ spend analysis of LPE vs CPC and impression share, and his device-split diagnostic (Acquisio, c.2016; Adalysis Q&A, undated). The Adalysis ten-step landing-page checklist (Parker on Adalysis, 2016) and shared-page triage (Adalysis, 2017). Hopkins's load and layout-shift thresholds and no-index rule (SEL, 2023). Hebdon's mobile and "don't test page and headline together" rules (Copyhackers, 2018). Levy's promise/device/speed checklist (Optmyzr, 2026).

## When to use it / when not to
Use when LPE = Below average on keywords in the top 80% of search spend, after Ad Relevance and Expected CTR have been handled (34, 35) — Adalysis's own ordering is ad testing for CTR, organisation for relevance, then "page speed or a new page" for LPE (Adalysis docs, 2017).
Do not use: to lower CPC — Geddes found no CPC relationship (Acquisio, c.2016); on keywords with "—" (null QS for low-activity keywords since Sep 2016 [Google docs]); when the page converts above the account median and the ask is a QS number — Levy: don't change solely for QS at the expense of ROAS (Optmyzr, 2026).

## Inputs
- Keyword report (90 days) with final URL, cost, impressions, clicks, conversions, impression share, QS and the three statuses.
- The same report segmented by device.
- Analytics by landing page and device: bounce/engagement rate, load time.
- PageSpeed Insights (or equivalent) results for each flagged URL, mobile and desktop.
- Crawl status of each flagged URL (is it reachable and indexable by Google's crawlers — crawler data can feed ad quality [Google docs]).

## Method
1. **Aggregate by URL, not keyword.** Group flagged keywords by final URL and count keywords Above / Average / Below on each page; work the pages with the most below-average spend first (Adalysis, 2017). A page shared by many ad groups with mixed statuses is a relevance problem at the keyword end, not a page problem — send those keywords to skill 35.
2. **Run the device split before touching the page.** Compare bounce rate, average position and CPC by device for good vs poor pages (Geddes, Adalysis Q&A, undated). If mobile bounce is ≥1.5× desktop on the poor pages and not on the good ones, the fix is mobile-only and the rest of this method is skipped for desktop. Google holds QS by device but never shows it [Google docs; Geddes, undated], so this is the only way to see it.
3. **Check crawlability and speed thresholds.** Page must be reachable by Google's crawlers [Google docs]. Targets: load in ~2 seconds or less and no layout shift within 5 seconds of render (Hopkins/SEL, 2023); measure, then apply PageSpeed Insights recommendations (Adalysis/Parker, 2016). If the page fails either threshold on mobile, stop here — fix speed first and re-read in 30 days (Hebdon, 2018: slow or unreadable mobile pages lower LPE).
4. **Check promise match.** The ad's headline claim and CTA must be visible on the page without scrolling; land on the product or service page with a buy or enquiry CTA, not a category or home page (Adalysis/Parker, 2016; Levy/Optmyzr, 2026). Do not add keyword stuffing: Google says exact search wording need not appear [Google docs], and Geddes frames the page signal as "supporting words", not a word-level heat map (Adalysis Q&A, undated).
5. **Check transparency items.** Contact details and registered address linked from every page, privacy policy linked from the footer, an About page (Adalysis/Parker, 2016). Hebdon reports the privacy-policy effect is real but inconsistent (Copyhackers, 2018) — treat as a 30-minute hygiene fix, never a project.
6. **Decide replace vs repair.** If the page fails rule 3 and rule 4 together, and a page elsewhere in the account carries the same keyword theme with Above-average status, point the keywords at that page rather than rebuilding (Adalysis, 2017: find high-performing pages to replicate). Otherwise repair in the order 3 → 4 → 5.
7. **Set paid landing pages to no-index/no-follow** unless they are also organic landing pages (Hopkins/SEL, 2023).
8. **Never change the page and the ad in the same window.** Hebdon: testing a headline and a landing page at once skews the data (Copyhackers, 2018). Page changes first; ad tests start after the 30-day re-read.
9. **Re-read at 30 and 60 days on impression share, not CPC.** Expect the payoff as impression share and eligibility (Geddes/Acquisio, c.2016). An Above-average LP is unlikely to show below QS 7 under Geddes's estimated ~3.5-point LP weight (Acquisio, c.2016 — his estimate, not Google's), so a keyword stuck at ≤6 with LP Above average has a different problem.

## What Google will tell you instead, and why we don't
Google: "deliver what the search asks for", mobile-friendly, faster, and "use conversion rate to measure and optimize — it doesn't affect your landing page status" [Google docs, "5 ways"]. We agree on the first three. We disagree on measurement in two ways. First, the payoff metric is impression share and eligibility, not CPC — Geddes's data found no CPC relationship (Acquisio, c.2016) — so the WordStream-style "QS 5→7 saves 28.6%" claim repeated in agency content is not used (Adalysis/Parker, 2016, which itself flags the figure as stale). Second, Google's UI invites you to fix LPE keyword by keyword; the canon does it by URL, because the status belongs to the page (Adalysis, 2017). Google Support has told advertisers the keywords should appear on the general website (reported in Adalysis Q&A, undated); Google's own help page now says exact wording need not appear [Google docs], and we follow the help page, not Support.

## Failure modes
- **Lead-gen vs ecommerce bounce norms**: there is no universal good bounce rate; lead-gen runs higher (Geddes, Adalysis Q&A, undated). Rule 2 compares good vs poor pages within the account, never against a benchmark.
- **Dedicated landing pages that hide the site**: Hebdon's gym client doubled conversion rate moving from a dedicated page to the full site (Copyhackers, 2018); a thin "landing page" can fail the navigation and transparency checks (Adalysis/Parker, 2016).
- **Low-volume keywords**: the status is relative to advertisers on the exact same keyword over 90 days [Google docs]; with little data it will not move visibly in 30 days.
- **Pages behind consent walls, logins or geo-redirects**: crawler data feeds ad quality [Google docs]; if the crawler sees a wall, nothing on the page matters.
- **Shared template pages across many ad groups**: a template fix moves every keyword at once; make sure the ad groups you did not intend to touch are not mid-test (rule 8).
- **Regulated verticals** (finance, health) where the promise cannot be stated on the page: accept Average and stop.

## What to measure
- Count of keywords Above / Average / Below per URL, by spend (Adalysis, 2017).
- Search impression share and lost-IS (rank) for flagged keywords at day 0/30/60 (Geddes/Acquisio, c.2016).
- Mobile vs desktop bounce ratio on good vs poor pages (Geddes, undated).
- Load time and layout shift per flagged URL against 2 s / 5 s (Hopkins, 2023).
- Conversion rate per page (recorded for the ROAS guard, not as an LPE metric — Google says it does not affect the status [Google docs]; Levy, 2026).

## Open disagreements in the canon
- **Does LPE pay in CPC or in volume?** Geddes's data: volume/impression share, no CPC relationship (Acquisio, c.2016). Agency content built on WordStream's CPC curve says price (repeated in Adalysis/Parker, 2016). Epiminds measures impression share; CPC claims are not made to clients.
- **How much does LPE weigh?** Adalysis's estimate was ~39% (Acquisio, c.2016); Geddes himself reads Google's underlying assessment as possibly pass/fail (Adalysis/Parker, 2016). Google publishes no weight. We use the weight only to explain the "Above-average LP rarely below 7" pattern, labelled as an estimate.
- **Dedicated landing page or site page?** Parker's checklist assumes a dedicated page (2016); Hebdon's case shows a full site can convert better (2018). Epiminds: start from the product/service page on the main site, build dedicated pages only when the site page fails rules 3–5.
