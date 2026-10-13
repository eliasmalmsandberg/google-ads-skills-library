# Dossier — 9 Micro-campaign consolidation for low-volume accounts

## Sources

1. **Source**: Navah Hopkins, Optmyzr, "The impact of PPC bidding strategies" — https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier**: 1 · **Date**: 2024-09-24 · **Claim**: 14,584 accounts: 50+ conversions/30 days is where any bidding strategy becomes predictably successful; <25 → 25–50 does not reliably improve performance; no account under 25 outperformed those over 50; manual bidding also improves with volume; setting targets/bid caps more often hurt than helped in the data. · **Evidence or opinion**: Cross-account observational study.

2. **Source**: Fred Vallaeys with Shawn Walker, Optmyzr PPC Town Hall — https://www.optmyzr.com/ppctownhall/practical-advice-on-how-to-actually-make-smart-bidding-work-for-you · **Tier**: 1 · **Date**: 2025-01-29 · **Claim**: ≥30 conversions per campaign per 30 days (vs Google's 15); split themes into ad groups not campaigns; separate campaigns only for budget, non-ad-group-level targeting, or materially different performance; for low volume use soft conversions (add-to-cart, engaged visit, product view) with values to train, as secondary until hard conversions have volume; new low-data campaigns often start on manual bidding; small incremental bid scripts. · **Evidence or opinion**: Opinion with practice.

3. **Source**: Julie Friedman Bacchini (with Lolk, Vallaeys), Optmyzr PPC Town Hall "PPC in 2025" — https://www.optmyzr.com/ppctownhall/ppc-in-2025-what-to-stop-start-double-down-on · **Tier**: 2 · **Date**: early 2025 · **Claim**: Lead-gen accounts often sit below the volume Smart Bidding needs; pool data via portfolio bidding: "How can you pool more of your data to provide it to the platform?" Lolk (not canon): ~30 conversions/month for PMax to work at all, ~300 to be effective. · **Evidence or opinion**: Opinion.

4. **Source**: Nils Rooijmans, "[AMA] We did exactly what Google told us to do, and went from 15 leads to 6, how to fix?" — https://nilsrooijmans.com/daily/ama-we-did-exactly-what-google-told-us-to-do-and-went-from-15-leads-to-6-how-to-fix · **Tier**: 1 · **Date**: 2026-09-16 · **Claim**: $5–6k/month account on tCPA $300 (actual ~$220, 20–30 leads/month) lowered tCPA to $220; CPC crept up, leads fell to 6 in two weeks with budget still fully spent. Fix: tCPA *portfolio* with a max CPC limit; tCPA back to the acceptable $300; take converting search terms (conv ≥1) from the 10 weeks before the change, sort CPC, set max CPC at the 90th–95th percentile; once back to ~20 conversions/month, lower tCPA and raise the cap in 10–20% steps. Smart Bidding predicts better at 20–30 conv/month. · **Evidence or opinion**: Single-account diagnosis with numbers.

5. **Source**: Nils Rooijmans, "Nail it before you scale it" — https://nilsrooijmans.com/daily/nail-it-before-you-scale-it · **Tier**: 1 · **Date**: 2026-05-25 · **Claim**: Client told to spend more so Smart Bidding could learn; tracking counted form fills not SQLs; PMax had weak signals. Cut budgets first, rebuilt tracking on SQLs/sales, moved spend from PMax to Search on exact keywords from best-converting terms, tCPA with bid limits, raised the lower limit every other day for two weeks; scale gate = 30 SQLs in two weeks, then remove the lower limit and set the upper at 50% of tCPA; 17 new clients below target CPA two weeks later. "Scaling a broken setup doesn't fix things; it just makes the leak bigger." · **Evidence or opinion**: Single-account result.

6. **Source**: Nils Rooijmans, "[AMA] What settings do you immediately change when taking over an account?" — https://nilsrooijmans.com/daily/ama-what-settings-do-you-immediately-change-when-taking-over-an-account · **Tier**: 1 · **Date**: 2026-06-17 · **Claim**: Disable auto-applied recommendations (auto-added broad keywords and Display Expansion "advertise to everyone except your customers"); Search partners off until mature; location "Presence" not "Presence or interest". · **Evidence or opinion**: Practice.

7. **Source**: Brad Geddes (Adalysis) workshop slides — https://presentations.boussiasevents.gr/files/_boussias_conferences_content/presentations/google_marketing_conference/2020/day2/workshop_brad_geddes_googleMKT_20.pdf · **Tier**: 1 · **Date**: 2020 · **Claim**: Create a campaign only for a different geo, budget control, network, targeting type or organisational simplicity; "over engineering" can leave zero ads showing; multi-ad-group testing suits small-data accounts. · **Evidence or opinion**: Method.

## Dissenting view
Hopkins's data (2024) says 25–50 conversions is not reliably better than <25, which undercuts the idea that merging two 12-conversion campaigns into one 24-conversion campaign helps; the gain only shows at 50+. Vallaeys/Walker (2025) and Bacchini (2025) still consolidate/pool at lower volumes. The disagreement is whether consolidation below 50 buys stability (fewer relearning events, one budget) even if it does not buy measurable performance — the skill takes the stability position and says so.

## What the platform currently does [Google docs]
- Google's stated Smart Bidding guidance is 15 conversions in 30 days (as cited by Vallaeys/Walker, 2025); learning status is shown per campaign and re-triggers on budget/target/structure changes. [Google docs]
- Auto-applied recommendations can add broad keywords and expand networks unless disabled (Rooijmans, 2026). [Google docs]
- Portfolio bid strategies allow bid limits on tCPA/tROAS; campaign-level tCPA does not expose a max CPC (Rooijmans, 2026; Google docs). [Google docs]
- Secondary conversion actions and campaign-level conversion goals exist (Vallaeys/Walker, 2025). [Google docs]

## Baseline check
Read `google-ads-account-audit` (Layer 6: <30 conv/month → manual/Max Clicks; Tier 1 flag <10 conv/month) and `google-ads-bidding` headings. Baseline gives a strategy table by volume. This skill adds the study thresholds (25/50), the merge rules (Vallaeys/Walker; Geddes), the portfolio-with-CPC-cap fix and its percentile rule (Rooijmans), the soft-conversion training path, the pre-scale gate (30 SQLs/2 weeks), and the account-settings hygiene that leaks small budgets.

## Judgment calls
- "<15–30 conv/month" in the row is read against Hopkins's bands: under 25 the data says structure alone will not fix it; the skill therefore pairs consolidation with pooling and CPC caps rather than promising performance from merging.
- Lolk's PMax thresholds are labelled non-canon.

## Canon strength: Strong
Hopkins/Optmyzr (cross-account evidence), Rooijmans ×3 (single-account evidence with numbers), Vallaeys/Walker and Geddes (method), Bacchini (Tier 2).

## Invalidated by
Google exposing bid limits on campaign-level tCPA (removes the portfolio reason), changes to Smart Bidding's learning model that make low-volume campaigns stable, or removal of secondary/soft conversion goals.
