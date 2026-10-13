---
name: impression-share-decomposition-decision-rule
id: 84
description: Monthly rule for turning a lost-impression-share reading into one of three actions — budget, bid target, or quality/assets — and for telling a real IS change from a bidding-behaviour artefact. Not for setting IS targets as a bid strategy (Target IS) or for competitor analysis (see 83).
tags: Diagnostic / All / Diagnose / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Google reinstating bid suppression on budget-limited tCPA/tROAS campaigns; changes to eligible-impression estimation; removal of the budget/rank split in lost-IS columns.
---
## What this is
A decomposition: first explain *why* lost IS moved (five causes), then route the campaign to budget, bid-target, or quality work using cost-per-conversion as the tiebreaker. Position: rank loss is fixed with assets and Quality Score before bids; budget loss is fixed by reallocation before new money; and since August 2026 a jump in lost-to-budget on a tCPA/tROAS campaign is first assumed to be Google's bidding change, not demand.

## Where it comes from
Brad Geddes' three Adalysis diagnostics on budget loss, rank loss, and IS-driven conversion gains (Adalysis, 2019; 2019; 2024), plus the Adalysis tool's 10%-for-three-days budget trigger (Adalysis docs, 2026). Mike Ryan's cross-account medians on what happened to IS after Google stopped suppressing bids on budget-limited campaigns (Ryan/Smarter Ecommerce, 2026). The incremental-volume arithmetic from PPC Hero (Oumedian, 2015). Platform definitions from Google Ads Help, labelled.

## When to use it / when not to
Use monthly on every Search and Shopping campaign, and immediately when lost IS (budget or rank) moves more than ~10 points month on month or stays above 10% for three consecutive days (Adalysis docs, 2026). Use before any budget request to a client.

Do not use on Search Partners traffic (excluded from IS) [Google docs], on daily data (IS is estimated per day and lags 24–48 h; small daily moves are noise) [Google docs], or on PMax as if it were Search — PMax IS blends Search and Shopping eligible impressions [Google docs] and the rank/budget split there is not actionable at keyword level.

## Inputs
- Campaign-level, 30-day and prior-30-day: Search IS, lost IS (budget), lost IS (rank), top IS, abs-top IS, cost/conversion or ROAS, conversions, avg CPC, impressions [Google docs].
- Change history for the period: budgets, bid targets, bid strategy switches, keyword/negative/DSA/match-type changes (Adalysis, 2019).
- Impression-weighted QS per ad group, 30-day cost per ad group (Adalysis docs, 2026).
- Asset count per ad group (distinct asset types) (Adalysis, 2024).
- Whether the campaign is on tCPA/tROAS and was flagged "limited by budget" before 17 Aug 2026 (Ryan, 2026).

## Method
1. **Explain the move before acting.** For each campaign where lost IS changed, attribute the change to one of five causes, checked in this order (Adalysis, 2019):
   a. No account change but search volume moved → seasonality; compare with the same period last year.
   b. Targeting change: negatives/pauses lower budget loss; new keywords, DSA, removed negatives raise it.
   c. CPC change with no bid edit → automated bidding moved bids silently; check avg CPC trend against target.
   d. QS change: rising QS opens more auctions and converts rank loss into budget loss; falling QS raises CPCs and budget loss.
   e. Budget change.
   If the cause is (a) or (b), the IS move is explained and usually needs no action beyond confirming CPA/ROAS still hold.
2. **Aug-2026 check for tCPA/tROAS campaigns.** If the campaign was budget-limited before 17 Aug 2026 and lost-to-budget jumped while lost-to-rank fell, treat it as the bid-suppression removal: across smec's accounts median lost-to-rank went ~45%→~30% and lost-to-budget ~4%→~33% with median CPC +15.8% (Ryan, 2026). This is not new demand. Decide between: raise the target toward the ROAS/CPA actually delivered, raise budget, or move to Maximize Conversions, which cannot be budget-limited by design (Ryan, 2026). Do not read step 3 as "the campaign wants more money" until this is settled.
3. **Budget-loss route.** Condition: lost IS (budget) >10% for three consecutive days (Adalysis docs, 2026) AND the campaign is at or under its CPA/ROAS target.
   a. Budget can grow → raise it; a campaign within target should carry very little budget loss (Adalysis, 2019).
   b. Budget is fixed → rank all budget-capped campaigns by cost/conversion ascending; move money from under-spending or above-target campaigns into the cheapest-converting capped campaign (Adalysis, 2024). Size the request with: available impressions = impressions ÷ IS; incremental impressions = available × lost IS (budget); × CTR × CPC = cost; × CVR = conversions (Oumedian/PPC Hero, 2015).
   c. Budget fixed and no donor campaign → cut the least profitable targeting (pause keywords with CPA above account average or zero conversions) or lower the bid target, accepting that loss migrates to rank (Adalysis, 2024).
   Budget loss is tolerable only in experimental or awareness campaigns; never in remarketing or any campaign under target (Adalysis, 2019).
4. **Rank-loss route.** Condition: lost IS (rank) is the larger component and the campaign is at or under target. Work in this order and stop when IS recovers (Adalysis, 2024):
   a. Assets: ad groups with fewer than 4–5 distinct asset types → add assets.
   b. Quality Score: prioritise ad groups by impression-weighted QS × 30-day cost (Adalysis docs, 2026); fix ad relevance and landing page there.
   c. Bids last: raise tCPA / lower tROAS only after a and b, because raising bids generally raises CPA or lowers ROAS (Adalysis, 2024).
   Graph top IS and abs-top IS against QS, avg CPC, conversions and CPA over 90 days to confirm the driver (Adalysis, 2019).
5. **Over-target campaigns.** If CPA/ROAS is worse than target, lost IS of either kind is not a problem to fix; it is the efficiency lever working. Lower the target or cut targeting first (Adalysis, 2024), and re-run step 3 next month.
6. **Output.** Per campaign: cause (a–e), route (budget / rank / efficiency / Aug-2026 artefact), action, projected incremental conversions (budget route only — rank-side gains are not forecastable because CTR and CPC both rise with position; Oumedian/PPC Hero, 2015), and the number to re-check next month.

## What Google will tell you instead, and why we don't
- Google's column help proposes top IS and abs-top IS as bid targets [Google docs]. We do not bid to a position share; Geddes' order is assets, then QS, then bids last, because bidding into rank loss raises CPA (Adalysis, 2024).
- Google's framing of the August 2026 change is that over-delivering ROAS on budget-limited campaigns "was never the intended behaviour" (Ryan, 2026, quoting Google). The data shows budget-limited campaigns' CPCs rose 15.8% and overall IS fell 40%→31% (Ryan, 2026); we treat a post-August lost-to-budget jump as a cost increase to be managed, not a growth signal.
- "Limited by budget" and Google's budget recommendations assume the current CPC is right. Geddes' point is that lowering CPC stretches the same budget into more clicks ($1→$0.75 CPC turns 100 clicks into 133) (Adalysis, 2019); we test the bid target before accepting the budget recommendation.

## Failure modes
- **Low-volume campaigns (<1,000 impressions/month).** IS is estimated and daily values swing [Google docs]; monthly decomposition on tiny bases produces false causes. Aggregate to 90 days.
- **Brand campaigns.** Benchmarks differ: Geddes treats >90% (>95% for large brands) as the target and anything lower as a rank or budget problem to fix immediately (Adalysis, 2024). The reallocation logic of step 3b does not apply — brand is the donor, never the recipient, unless brand IS itself is below 90%.
- **Shopping.** Only the first impression per search counts and only Search Network traffic [Google docs]; rank loss in Shopping is mostly feed/price-driven and the asset/QS route in step 4 does not apply.
- **PMax.** Blended Search + Shopping IS [Google docs] with no keyword-level rank diagnosis; use only the budget route.
- **Seasonal verticals.** A search-volume spike reads as budget loss (Geddes' example: volume +130%, impressions +16%; Adalysis, 2019). Raise budgets ahead of predictable peaks rather than reacting to the IS column.
- **Accounts that sit at 10–30% IS by design.** Many well-managed accounts do (Adalysis, 2024); a low IS is not itself a defect if CPA/ROAS and volume targets are met.

## What to measure
Monthly per campaign: lost IS (budget), lost IS (rank), top IS, abs-top IS, avg CPC, cost/conversion, conversions — with the prior month and the cause code assigned. Track the three-day >10% budget trigger (Adalysis docs, 2026). For any campaign routed to budget, record projected vs. realised incremental conversions after 30 days. For tCPA/tROAS campaigns, record CPC and IS on either side of 17 Aug 2026 as the baseline for the Aug-2026 artefact check (Ryan, 2026).

## Open disagreements in the canon
- **Whether budget loss still signals opportunity.** Geddes (2019, 2024): budget loss on an under-target campaign is money on the table. Ryan (2026): after August 2026 a third of budget-limited campaigns' impressions are now lost to budget because bids are no longer suppressed, at higher CPC. Epiminds: Geddes' rule stands for campaigns that were never budget-limited before August 2026; for those that were, step 2 runs first and the target is adjusted before any budget is added. Reason: adding budget at a 15.8% higher CPC without re-checking the target buys the same clicks for more money.
- **IS benchmarks.** Geddes' 80% / 90% / 95% lines are opinion (Adalysis, 2024); no cross-account study backs them. We use them as audit flags, not as targets to bid toward.
