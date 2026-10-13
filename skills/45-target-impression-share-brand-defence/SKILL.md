---
name: target-impression-share-brand-defence
id: 45
description: Use when competitors are bidding on the client's brand and you must decide how (or whether) to defend — Target Impression Share, manual CPC, or not bidding. Not for non-brand campaigns, not for PMax brand exclusion decisions (structure topic), and not a reason to set tIS at 100% absolute top.
tags: Strategy / Search / Protect / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google removing the bid limit from Target Impression Share, changing Ad Rank reserve pricing on uncontested auctions, or restricting competitor brand bidding by policy.
---
## What this is
Brand defence is buying your own high-intent clicks so a competitor can't. It used to be cheap insurance — Williams cites a brand term that cost ~$0.07 to guard and now costs ~$1, a 10–20× rise he attributes to Ad Rank reserve-price changes rather than competition (Williams/ZATO, 2024). That makes the *how* matter: Target Impression Share raises CTR and conversion rate via top placement but does not improve CPA or ROAS, and in a 14,584-account study it was only usable with a bid cap — the uncapped sample wasn't even statistically significant (Hopkins/Optmyzr, 2024). In the one published controlled test, capped tIS and manual CPC were a wash (Williams/ZATO, 2024).

## Where it comes from
Williams' Experiment on a ten-year client (2024) is the only controlled brand tIS-vs-manual test in the canon; his 2023–2026 posts supply the reserve-price mechanics, the funnel-spanning view of brand queries and the "kill if not incremental" rule. Hopkins (2024) supplies the cross-account tIS finding; Vallaeys (2026) the case for manual CPC as a hard ceiling.

## When to use it / when not to
Use when auction insights shows at least one competitor with meaningful overlap on exact brand terms, and brand clicks are affordable relative to blended MER (Williams/ZATO, 2026). Don't use tIS when nobody is in the auction — you're paying the reserve price for placement no one contests (Williams/ZATO, 2023). Don't use when brand converts like non-brand (some large advertisers' brand CVR and ROAS roughly equal non-brand because users research the category through the brand name — Williams/ZATO, 2024); then brand is a mid-funnel keyword and belongs under the ordinary bid strategy, not under an IS guarantee.

## Inputs
- Auction insights for the exact brand terms, last 30 and 90 days: competitor overlap rate, top-of-page rate
- Brand campaign: IS, lost IS (rank/budget), avg CPC, CPC p90 on converting terms, CPA/ROAS, share of account conversions
- Blended MER / ROAS and brand share of total conversions
- Evidence of incrementality (prior holdout, organic CTR on brand when ads were off), if any

## Method
1. **Is anyone there?** If auction insights shows no competitor with >10% overlap on exact brand over 90 days (Epiminds operating threshold — the canon gives no overlap cut-off; reason: below that a competitor is in fewer than one in ten of your auctions and can't move IS materially), don't buy placement: set manual CPC at a low bid (the cheapest way to hold a hard per-click ceiling — Vallaeys/Optmyzr, 2026) and accept whatever IS the reserve price gives. Exclude brand terms entirely only where the brand owns the organic results and nobody competes — "rare these days" (Williams/ZATO, 2026).
2. **Is brand bottom-funnel in this account?** Compare brand CVR/ROAS to non-brand. If brand is ≥3× non-brand on ROAS (Williams' illustrative 18 vs 3 — ZATO, 2022), it's a defence case; if roughly equal, treat brand as a normal keyword under the main strategy (Williams/ZATO, 2024).
3. **Set tIS from history, not from the UI.** Target = the campaign's trailing-30-day IS under the previous strategy (Williams used 92% — ZATO, 2024); placement "top of page", not absolute top unless a competitor consistently out-ranks you there. Never start at 100%.
4. **Always cap.** Max CPC limit above the typical average CPC with room to grow (Williams' $2.51 — ZATO, 2024); size it at the 90th–95th percentile of CPC on converting brand terms over the prior 10 weeks (Rooijmans, 2026). An uncapped tIS is unsupported by the data (Hopkins/Optmyzr, 2024).
5. **Give brand a higher ROAS target than non-brand**, not lower — those users were already marketed to and need a higher return to be worth paying for again (Williams/ZATO, 2026). If the client's brand "target" is below non-brand, the campaign is subsidising non-incremental sales.
6. **Test incrementality once a year**: geo holdout or a scheduled off-period on a low-stakes region; compare blended MER and organic brand clicks. If brand is over-bid and the test shows no incremental lift, kill or cut it (Williams/ZATO, 2026).
7. **Prefer tIS over manual for the labour, not the performance.** The experiment: tIS +1% clicks, −2% conversions, −1% profit vs manual with modifiers, not significant at 4,235 clicks; Williams switched to tIS because manual needs ongoing management (Williams/ZATO, 2024). If you have the hours and want a hard ceiling, manual is equally good.
8. **Watch the floor.** Track avg CPC on exact brand monthly; a rise with unchanged auction-insights overlap is a reserve-price change, not competition (Williams/ZATO, 2024) — lower the cap, don't raise the IS target.

## What Google will tell you instead, and why we don't
Google's tIS setup suggests a bid limit and nudges toward "absolute top of page" with a high percentage, and its general stance is that bid limits "aren't recommended" because they restrict optimisation (Google Ads Help, 2026). We set the target at historical IS and always cap, because the cross-account data shows tIS adds nothing to CPA/ROAS and misbehaves without a cap (Hopkins/Optmyzr, 2024), and because an uncontested brand auction still charges a reserve price (Williams/ZATO, 2023). Google's "attributed brand search" framing also treats brand clicks as an outcome of other campaigns — true, which is exactly why brand needs a *higher* ROAS bar, not a free pass (Williams/ZATO, 2026).

## Failure modes
- **Household brands** where brand queries are price comparison: tIS at a high target buys mid-funnel clicks at top-of-page prices (Williams/ZATO, 2024, 2026).
- **No competitor in the auction**: you pay the reserve price for an IS number (Williams/ZATO, 2023).
- **Small budgets**: Williams notes significance is impractical for small budgets; a tIS campaign can't be judged and will eat the budget on placement.
- **Brand share creep**: when brand is "an inordinate amount of traffic" it deserves scrutiny, not defence (Williams/ZATO, 2026).
- **TV / offline spikes**: brand volume jumps and tIS chases it at the cap; the experiment didn't control for this (Williams/ZATO, 2024). Lower the cap during known media flights.
- **Bid adjustments on tIS**: mostly ignored; only device −100% exclusions apply (McNair/PPC Mastery, 2026).

## What to measure
Monthly: exact-brand IS and lost IS to rank; avg and p90 CPC on converting brand terms; competitor overlap and outranking share; brand CPA/ROAS vs non-brand and vs its own higher target; blended MER. Annually: incrementality holdout result; share of days the cap binds.

## Open disagreements in the canon
- **tIS vs manual.** Williams' test says tie; Hopkins' data says tIS needs a cap; Vallaeys prefers manual for a hard ceiling. Epiminds: capped tIS by default (labour), manual where the client wants a hard CPC ceiling.
- **Defend at all.** Williams: while affordable and incremental, otherwise kill. We require an incrementality test before a brand budget exceeds ~15% of account spend — our own threshold, since the canon gives none.
- **Higher or lower ROAS target for brand.** Most accounts run brand with a lower target because it "always hits"; Williams argues higher. We go higher.
