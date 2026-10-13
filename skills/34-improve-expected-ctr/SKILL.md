---
name: improve-expected-ctr
id: 34
description: Fix "Below average" Expected CTR on keywords that carry real spend. Not for new keywords with null QS, not for ad-copy writing in general (see 35 and the ad-copy skills), not for chasing a 10/10.
tags: Technique / Search / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google changing the expected-CTR comparison set (currently exact-same-keyword, trailing 90 days) or folding assets into QS; retirement of keyword-level QS reporting.
---
## What this is
A decision procedure for keywords whose Expected CTR component reads "Below average" and which spend enough to matter. It decides whether the rating is worth fighting, which ad test to run, and which metric declares the winner. It is built on Geddes's finding that the CTR needed for "above average" is specific to the keyword and account, so there is no target CTR to aim at — only a direction to move and a test to run (Geddes/Adalysis, 2016).

## Where it comes from
Brad Geddes's Adalysis data on CTR-to-rating thresholds across client accounts (Adalysis, 2016) and his $100M+ spend analysis of Ad Rank and CPC discounts (Geddes/Acquisio webinar, c.2016). Navah Hopkins's position that expected CTR is not directly controllable and actual CTR plus conversions should lead (Search Engine Land, 2023). Amy Hebdon's ad-writing tests on headline-keyword match and SKAG dilution (Copyhackers, 2018). Aaron Levy on the query mix behind a visible score (Optmyzr, 2026).

## When to use it / when not to
Use when a keyword with meaningful spend (rule 1 below) shows Expected CTR = Below average while Ad Relevance and Landing Page Experience are Average or better. If Ad Relevance is also below average, run skill 35 first — Geddes's order is organisation first, then ad testing (Geddes/Acquisio, 2018 SMX interview; Adalysis, 2017).
Do not use on keywords showing "—": Google reports null QS when there are not enough exact-match impressions and clicks, and has since September 2016 [Google docs]. Do not use on brand terms whose CTR is already far above non-brand norms; Geddes's brand example needed 46% CTR for a 10, and the gap between a 9 and a 10 there is not worth ad churn (Geddes/Adalysis, 2016). Do not use if the business wants fewer, better clicks: in B2B a lower expected CTR from pre-qualifying copy can be the correct outcome (Geddes/Acquisio, c.2016).

## Inputs
- Keyword report, last 90 days, with: cost, impressions, clicks, CTR, conversions, conv. value, QS, Exp. CTR / Ad Relevance / LPE statuses, match type.
- Search terms report for the same keywords (to see the query mix behind the rating).
- Current RSA assets and asset performance labels for the ad group.
- Impression-weighted QS for the ad group (skill 38) so you fix groups, not single keywords.

## Method
1. **Qualify the keyword.** Work only keywords in the top 80% of search spend over 90 days that show Exp. CTR = Below average. Geddes's prioritisation is impression- and spend-weighted ad groups, not the lowest scores (Adalysis, 2017); Vallaeys notes a keyword with 18 impressions does not justify attention (Optmyzr, 2017).
2. **Read the query mix before touching the ad.** Pull search terms for the keyword. If the bottom half of queries by CTR is dominated by off-intent terms, the visible rating reflects those queries, not your ad — Levy: auction-time quality "may be okay for the best queries but poor for the worst, which dominate what you can see" (Optmyzr, 2026). Output: negatives first; re-check the rating after 30 days. Only proceed to rule 3 if the query mix is clean.
3. **Do not set a CTR target.** The CTR needed for "above average" varied from 14.5% (non-brand) to 46% (brand) in Geddes's client data, and 15% was already above average for another brand (Adalysis, 2016); a 7–8% non-brand CTR can still read as below average (Gales, 2026, corroborating). The rating is relative to advertisers on the exact same keyword over 90 days [Google docs]. Output: a direction (raise CTR against this keyword's own history), not a number.
4. **Decide whether CTR is even the right objective.** If the keyword's conversion rate is above the campaign median and CPC is acceptable, leave it: Hopkins — optimise for good CTR, not good expected CTR, and don't discount keywords winning in other ways (SEL, 2023). If the account is B2B lead-gen with lead-quality problems, deliberately keep qualifying copy and accept the rating (Geddes/Acquisio, c.2016).
5. **Run the ad test against conversions per impression, not CTR.** Geddes's rule: conversion-per-impression testing raises QS and profit together, where CTR-only testing raises QS and can lower profit (Adalysis, 2016); Hebdon's warning is the same — high-CTR ads can pull unqualified clicks (Copyhackers, 2018). Test design: one new RSA in the ad group with (a) the keyword's exact wording in at least one headline — Hebdon: it "feels like a missed opportunity" but it is what works (Copyhackers, 2018); (b) a more specific offer or CTA — the one Google recommendation we keep [Google docs, "5 ways"]; (c) sentence case, no exclamation marks, which Hebdon's tests favoured (Copyhackers, 2018). Winner = higher conversions per impression; CTR is the secondary read.
6. **Do not split the ad group to isolate the keyword unless it has volume.** Single-keyword ad groups only work with enough traffic; splitting dilutes CTR data across many ads (Hebdon, 2018). Threshold we use: keep the keyword where it is unless it alone has ≥100 clicks in 90 days (Epiminds operating threshold derived from Hebdon's dilution argument; not a published number).
7. **Expect the payoff in rank, not price, unless you are in position 1.** Geddes's data: CPC discounts from higher QS show mainly at position 1; lower down, improvement appears as better Ad Rank and impression share (Geddes/Acquisio, c.2016). Output: measure impression share and top-IS, not CPC, for keywords not at the top.
8. **Re-read after 30 days; stop at 7.** Hopkins: keywords with data settle at 7–9 and a 1–2 point move is noise; a 5→2 move is a real signal (SEL, 2023). Gales/Optmyzr: 7 is "really good", 6 is fine (Optmyzr, 2026). Close the ticket when the keyword reaches QS ≥7 or Exp. CTR = Average with conversions per impression flat or up.

## What Google will tell you instead, and why we don't
Google's expected-CTR advice is "make your offer more compelling, be more specific, test calls to action", with a caveat that specific ads may lower CTR but raise conversion rate [Google docs, "5 ways"]. We keep specificity and drop the rest: Google gives no way to know how far below the bar you are, and Geddes's data shows the bar moves by an order of magnitude between keywords (Adalysis, 2016). Google says QS "should not be optimised" [Google docs]; we agree for the score, but use the components as a trigger, not a target. Where Google only caveats CTR vs conversions, we make conversions per impression the test metric outright (Geddes, 2016).

## Failure modes
- **Low-volume keywords and small accounts**: the rating is built on exact-match impressions over 90 days [Google docs]; below a few hundred impressions it moves on noise and any ad test is underpowered (Vallaeys, 2017; Hebdon, 2018).
- **Broad match**: the keyword can carry a QS inherited from an exact keyword in the same ad group, and broad struggles more with QS while winning cheaper positions (Hopkins, 2023; [Google docs]).
- **Brand campaigns**: the bar is extreme (46% for a 10 in Geddes's example) and the value of 9→10 is nil (Adalysis, 2016).
- **B2B / high-ticket lead-gen**: raising CTR with generic promises lowers lead quality (Geddes/Acquisio, c.2016; Hebdon, 2018).
- **Device-specific problems**: Google keeps QS by device but never shows it; a mobile-only CTR problem looks like a copy problem (Geddes, Adalysis Q&A, undated).
- **Query-mix problems**: ad changes do nothing until negatives land (Levy, Optmyzr, 2026).

## What to measure
- Conversions per impression on the ad group (primary test metric) (Geddes, 2016).
- Actual CTR vs the keyword's own trailing-90-day CTR (direction only).
- Exp. CTR status and QS at day 30 and day 60; treat ±1–2 as noise (Hopkins, 2023).
- Search impression share and top-of-page IS for keywords below position 1 (Geddes/Acquisio, c.2016).
- CPC only for keywords that hold position 1 (Geddes/Acquisio, c.2016).

## Open disagreements in the canon
- **Is expected CTR controllable?** Hopkins says no, optimise actual CTR and ignore the rating (SEL, 2023). Geddes treats it as the primary ad-testing metric (Adalysis, 2016). Epiminds goes with Geddes on *action* (it is the only public relative-quality read) and with Hopkins on *metric* (actual CTR and conversions decide the test).
- **CTR or conversions per impression as the ad-test metric?** Geddes: conversions per impression (2016). Google's own caveat points the same way. Epiminds uses conversions per impression; CTR-only tests are allowed only on brand and on pure awareness campaigns.
- **Component weights.** Geddes's 50/40/10 Ad Rank split and the Adalysis "39% landing page" figure are his estimates from client data (Acquisio, c.2016); Google publishes no weights. We do not quote weights as fact in client reporting.
