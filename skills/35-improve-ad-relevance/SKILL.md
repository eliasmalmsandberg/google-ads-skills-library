---
name: improve-ad-relevance
id: 35
description: Diagnose and fix "Below average" Ad Relevance on spend-carrying keywords by deciding whether the defect is grouping or copy, then applying the narrower fix. Not for Expected CTR (34), not for Ad Strength, not for RSA writing in general.
tags: Technique / Search / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google merging ad relevance into an asset-level signal, changing the exact-same-keyword comparison set, or removing keyword-level component reporting.
---
## What this is
A two-branch procedure for the Ad Relevance component. Geddes's rule is that low ad relevance "usually signals poor organisation, ads unrelated to their keywords, or a need for different copy" (Geddes/Acquisio, c.2016), and his order of operations is organisation first, ad creative second (Geddes/Acquisio, 2018). Hopkins calls it "the easiest lever to control" because it reads how well keywords appear in the copy and how closely the keyword matches the query (Hopkins/SEL, 2023). The skill tells you which of the two defects you have before you change anything.

## Where it comes from
Geddes's structure-first diagnosis and impression-weighted ad-group prioritisation (Adalysis, 2017; Acquisio, c.2016/2018). Hopkins's decoupling of Ad Strength from QS and the branded-campaign equity effect (SEL, 2023). Hebdon's headline-keyword match and SKAG dilution tests (Copyhackers, 2018). Levy's point that the visible rating is dominated by the worst queries behind a keyword (Optmyzr, 2026).

## When to use it / when not to
Use when a keyword with real spend shows Ad Relevance = Below average. Run it before skill 34 when both Exp. CTR and Ad Relevance are below average — structure first (Geddes/Acquisio, 2018).
Do not use for: keywords with "—" (null QS since Sep 2016 for low-activity keywords [Google docs]); keywords whose rating was inherited — a broad keyword with no impressions of its own can carry the QS of an exact keyword in the same ad group [Google docs]; or to chase Ad Strength, which "does not impact quality score" (Hopkins/SEL, 2023).

## Inputs
- Keyword report (90 days): cost, impressions, clicks, conversions, QS and three component statuses, match type, ad group.
- Search terms for each flagged keyword with CTR and conversions per query.
- The ad group's RSA headlines/descriptions and the other keywords in the group.
- Impression-weighted QS per ad group (skill 38).

## Method
1. **Prioritise by ad group, not keyword.** Rank ad groups by impression-weighted QS × spend and start at the top; Geddes's method colour-codes the weak component per ad group so you fix the group's problem once (Adalysis, 2017). Work only groups in the top 80% of search spend.
2. **Classify the defect — grouping or copy.** For each flagged keyword, test two things:
   - *Grouping test*: do the flagged keyword and the group's top-spend keyword share the same noun and the same intent (buy / compare / learn)? If not → grouping defect.
   - *Copy test*: does the keyword's core phrase (or a close variant) appear in any live headline? If not, and the grouping test passed → copy defect.
   Both tests fail → grouping defect takes precedence (Geddes/Acquisio, 2018).
3. **Grouping defect: move, don't split, unless volume allows.** Move the keyword into an existing ad group whose ad already matches it. Create a new ad group only if the keyword alone has ≥100 clicks in 90 days — Hebdon: single-keyword groups only work with enough traffic; splitting dilutes CTR data across ads (Copyhackers, 2018). The 100-click gate is Epiminds's operating threshold, not a published one. Add the keyword as a new keyword and pause the old one; editing in place removes the original and its history (Hopkins/SEL, 2023).
4. **Copy defect: put the keyword's wording in the ad.** Add a headline that uses the searched phrase; Hebdon: it "feels like a missed opportunity to stand out, but it's what works" (Copyhackers, 2018). Add Geddes's "supporting keywords" — the secondary nouns from the search terms — to a description (Geddes/Acquisio, c.2016). Do not pin to force it unless the group is brand or regulated; pinning is a test, not a default.
5. **Check the query mix before declaring the copy fixed.** Pull search terms; if below-median-CTR queries are off-intent, add negatives — Levy: the poor queries "dominate what you can see" in the rating (Optmyzr, 2026); Optmyzr's own fix list for ad relevance starts with search-term coverage (Optmyzr, 2026).
6. **Do not change match type to fix relevance.** Match-type changes don't affect QS, and testing a new match type doesn't erase history [Google docs; Hopkins/SEL, 2023]. If you want a tighter query set, add an exact keyword alongside and let the broad one inherit.
7. **If the account has no separate brand campaign, build one first.** Hopkins: brand traffic in its own campaign gives new non-brand ad groups a 6–7 start instead of 5 (SEL, 2023). Ad relevance work on a mixed brand/non-brand group is wasted until this is done.
8. **Re-read at 30 days.** Hopkins: a 1–2 point QS move is noise; a 5→2 drop is a real signal (SEL, 2023). Close when Ad Relevance = Average or above, or when the keyword has been moved to a group whose impression-weighted QS is ≥7.

## What Google will tell you instead, and why we don't
Google's fix list is "align wording with search terms, split ad groups whose keywords can't be served by one ad, group by theme" [Google docs, "5 ways"]. We keep alignment and theme, but we do not split by default: Hebdon's tests show splits dilute CTR data in small groups (Copyhackers, 2018), and Geddes's prioritisation says fix the high-impression group's problem once rather than multiply groups (Adalysis, 2017). Google's UI also pushes Ad Strength beside every RSA; Hopkins's position, which we follow, is that Ad Strength is a creative-quality score and does not affect QS, so "Poor" Ad Strength is never a reason to rewrite an ad whose Ad Relevance is Average or better (Hopkins/SEL, 2023). Google says moving an ad group with the same ads and keywords to another campaign doesn't change ad quality [Google docs]; we use that — restructuring campaigns does not reset relevance, so move freely.

## Failure modes
- **Low-volume accounts**: the rating is built on exact-match impressions over 90 days [Google docs]; with few hundred impressions it moves on noise and any split starves the ads (Hebdon, 2018).
- **Broad-match-heavy structures**: a broad keyword may show an inherited rating [Google docs]; your copy change is judged against queries you don't see unless you pull search terms (Levy/Optmyzr, 2026).
- **Mixed brand/non-brand groups**: brand equity masks non-brand relevance problems (Hopkins, 2023).
- **Device-specific problems**: Google segments QS by device and never shows it; a mobile-only relevance issue looks like a copy problem (Geddes, Adalysis Q&A, undated).
- **Regulated verticals** where the keyword wording cannot appear in the ad (policy): the copy branch is unavailable; use the grouping branch and accept Average.
- **Accounts that fix ad relevance to raise Ad Strength**: the two are independent (Hopkins, 2023); you can lower one while raising the other.

## What to measure
- Ad Relevance status per keyword at day 0, 30, 60 (Hopkins, 2023 on noise bands).
- Impression-weighted ad-group QS before/after (Adalysis, 2017).
- CTR and conversions per impression of the ad group after the copy change (Geddes, 2016, via skill 34).
- Share of search-term impressions on off-intent queries after negatives (Optmyzr/Levy, 2026).
- Ad Strength is recorded but not a success metric (Hopkins, 2023).

## Open disagreements in the canon
- **Copy first or structure first?** Hopkins: copy is the easiest lever (SEL, 2023). Geddes: organisation first, then creative (Acquisio, 2018). Epiminds goes with Geddes, with the rule-2 classification making the choice explicit instead of defaulting either way.
- **Should you split ad groups to fix relevance?** Google says yes [Google docs]; Hebdon says only with enough traffic (2018). Epiminds: move before split; split only above the 100-click gate.
- **What the visible rating is based on.** Optmyzr's 2026 piece asserts it is "mostly past exact match performance" without a source; Google says the comparison set is advertisers on the exact same keyword over 90 days [Google docs]. We rely on the Google statement for the mechanism and on Levy for the practical consequence.
