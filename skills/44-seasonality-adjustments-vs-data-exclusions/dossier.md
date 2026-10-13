# Dossier — 44 Seasonality adjustments vs. data exclusions

## Sources

1. **Source**: Frederick Vallaeys, Optmyzr — "BFCM seasonality adjustments study", https://www.optmyzr.com/blog/bfcm-seasonality-adjustments-study/ · **Tier** 1 · **Date** 2025-11-19 · **Claim**: Over three BFCM seasons (2022–2024; 4,292 / 5,114 / 5,886 accounts), advertisers who set a seasonality adjustment during BFCM saw CPC inflation roughly double that of those who didn't (+36.7% vs +17%; +32% vs +16%; +34% vs +17%) and ROAS fall every year (−17%, −10%, −15.7%) while the no-adjustment group held ROAS (−2%, −1.5%, +5.7%). Revenue growth was higher with adjustments (+50.5/+52.8/+39.9% vs +25/+30.3/+33.8%). Observed BFCM CVR lift without adjustment: +17.5% (2022), +11.9% (2023), +7.5% (2024) — shrinking. Recommendation: no adjustments for mainstream predictable events (BFCM, Christmas, Valentine's); use them for brand-specific spikes Google has no history for (one-off flash sales, email-only promos, clearances); acceptable when the goal is revenue regardless of efficiency. Invest in guardrails (CPC anomaly alerts, pacing monitors, bid-cap automations) instead of predicting CVR. Illustrative precision risk: guessing +50% CVR when it's +40% overbids ~7%. · **Evidence**: observational, cross-account, three years; no controls for selection; adjustment size not defined.

2. **Source**: Lakshmi Padmanaban, Optmyzr — "Google Ads for BFCM 2026: what 4,200+ accounts reveal", https://www.optmyzr.com/blog/google-ads-bfcm-2026/ · **Tier** 1 outlet (content staff relaying Optmyzr data) · **Date** 2026-09-22 · **Claim**: Keep seasonality adjustments off unless Google has no history for the account. During the four BFCM days Standard Shopping ROAS fell 22%, PMax 13%; CPCs 29–46% above the prior week; week after Cyber Monday Shopping CVR −7.3% vs pre-BFCM and CPC +10.2%. Breakeven ROAS = 1 ÷ gross margin; if the gap between usual target and breakeven is under ~20% there's no room to chase peak volume; example rule: if ROAS stays 50 points above breakeven and stock allows, raise daily budgets 20%. · **Evidence**: 4,211 accounts, 22,800 campaigns, Oct–Dec 2025.

3. **Source**: Nils Rooijmans — "Data exclusions", https://nilsrooijmans.com/daily/data-exclusions · **Tier** 1 · **Date** 2025-10-16 · **Claim**: Exclusions are set on clicks, not conversions; excluded conversions still show in reporting (only Smart Bidding ignores them). Because of conversion delay you must exclude the clicks that *could* have produced the broken conversions: tracking faulty 12–14 Oct, with >30% of conversions lagging more than a day and a ~2-day typical delay → exclude 10–14 Oct. · **Evidence**: reading of Google's help page; worked example.

4. **Source**: Frederick Vallaeys, Optmyzr — "Google is making Smart Bidding more obedient", https://www.optmyzr.com/blog/smart-bidding-budget-caps-guide/ · **Tier** 1 · **Date** 2026-08-11 · **Claim**: Google advises against adding data exclusions or bid limits solely because of the 17 Aug 2026 change; Vallaeys agrees — add exclusions or structural controls only when traffic and business evidence justify them; snapshot settings and annotate every change. · **Evidence**: analysis.

5. **Source**: Navah Hopkins, Optmyzr — "Impact of PPC bidding strategies", https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier** 1 · **Date** 2024-09-24 · **Claim**: Budget changes in Smart Bidding need 2–3 weeks to settle; keep targets within ±10% of history. · **Evidence**: 14,584-account study.

## Dissenting view
Google's documentation positions seasonality adjustments as the correct tool for any expected 1–7 day CVR change and the obvious thing to do before a sale. Vallaeys' three-year data says that for events Google already has history on, the adjustment doubles CPC inflation and costs 10–17 points of ROAS. The disagreement is about who predicts the lift better: the advertiser (who knows the promo) or the bidder (which has three years of the same weekend across millions of accounts). The study says the bidder, for mainstream events; the advertiser, only for events the bidder has never seen.

## What the platform currently does [Google docs]
- [Google docs] Seasonality adjustments: multiplier 0.1–10.0 on expected conversion rate; scope campaign (up to 2,000) or channel; devices optional; "best for short events of 1–7 days", less effective beyond 14 days (Google Ads API docs, updated 2026-09-30).
- [Google docs] Data exclusions: only for conversion- and value-based Smart Bidding; Search, Display, Shopping, PMax (not Hotel/Travel); set on clicks, and conversions from excluded clicks are excluded; aim to exclude ≥90% of affected clicks, accounting for conversion delay; excluded conversions remain in reporting; don't remove an exclusion once applied; avoid backfilling (reporting backfill possible ≥5 days later); bids and spend may drop temporarily — adjust targets/budgets after applying; if a week or more of clicks is affected, fluctuations may last 1–2 conversion cycles; future exclusions take effect within a day (support.google.com/google-ads/answer/10370710, fetched 2026-10-13).
- [Google docs via Vallaeys 2026] After the 17 Aug 2026 change Google advises against adding data exclusions because of the change itself.

## Baseline check
Read `google-ads-bidding` ("Seasonal spikes → temporarily lower target"; quarterly "apply seasonal bid adjustments proactively") and `google-ads-budget-management` (seasonal budget calendar). Baseline recommends seasonality adjustments proactively and never mentions data exclusions. This skill adds the three-year evidence that adjustments hurt on mainstream events, the "no-history" rule for when they help, the click-not-conversion mechanics of exclusions with the lag-widened window, Google's own ≥90%/don't-remove/1–2-cycle rules, and the post-exclusion target handling.

## Judgment calls
- Treated the Optmyzr BFCM study as decisive despite its selection-bias caveat, because it's the only multi-year cross-account evidence and the direction is consistent all three years.
- Position: default off for seasonality adjustments; on only for novel events ≤7 days; exclusions for any outage ≥1 day, window widened by the account's conversion-lag p70.
- Padmanaban piece cited for the peak-day numbers and the breakeven rule, attributed to Optmyzr data.

## Canon strength: Strong
Four Tier 1 sources, two with large cross-account datasets.

## Invalidated by
Google changing seasonality-adjustment duration guidance or modifier range, changing data exclusions to conversion-based rather than click-based, or publishing evidence that adjustments on mainstream events stopped inflating CPCs.
