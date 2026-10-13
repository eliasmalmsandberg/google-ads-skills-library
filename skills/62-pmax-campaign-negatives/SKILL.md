---
name: pmax-campaign-negatives
id: 62
description: How to use campaign-level negative keywords in Performance Max — what they do and don't block, the limits, which terms qualify, and when a Search keyword is the better tool. Not for brand (skill 55), not for placement or content exclusions (skill 60).
tags: Technique / PMax / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: PMax negatives extending to Display, Video or Discover inventory; asset-group-level negatives; a change to the 10,000-per-campaign or 1,000-per-account limits; removal of the PMax search terms report.
---
## What this is
Campaign-level negatives in PMax arrived in beta in January 2025 and generally with the April 2025 search-terms rollout (Rooijmans, 2025; Williams/ZATO, 2025). They block Search and Shopping inventory only — nothing on Display, YouTube, Gmail or Discover (Bhandari/Optmyzr, 2026) [Google docs]. The campaign limit is 10,000, the account-level list 1,000 (Bhandari/Optmyzr, 2026; Hopkins/Optmyzr, 2026). Asset groups cannot take negatives (Hopkins/Optmyzr, 2026). This skill is the rule set for what goes in.

## Where it comes from
Nils Rooijmans (2024, 2025) on the three routes, the list convention and the click/conversion thresholds; Brad Geddes/Adalysis (2024) and Fred Vallaeys/Optmyzr (2025) on when a Search keyword beats a negative; Hopkins and Bhandari (Optmyzr, 2026) on limits and the impact preview; Kirk Williams (ZATO, 2023, 2025) on the account-level trap and the rollout.

## When to use it / when not to
Use when the PMax search terms report or insights show irrelevant, informational or wrong-intent queries with clicks and no conversions, and after any theme or asset change that drifted categories. Do not use for brand terms — those go through Brand Exclusions (Hopkins/Optmyzr, 2026) — and do not expect negatives to fix wasted Display or video spend; they never touch that inventory (Bhandari/Optmyzr, 2026).

## Inputs
- PMax search terms export (per campaign) or `campaign_search_term_insight` output: term, category, impressions, clicks, conversions, conversion value — no cost (Rooijmans, 2024).
- Search campaigns' keyword list for the same account.
- A shared negative keyword list dedicated to PMax, named with a leading asterisk so it sorts to the top (Rooijmans, 2025).

## Method
1. **Pick the route.** Default to a shared list attached to the PMax campaign(s); use direct campaign negatives for one-off terms. Never use the account-level list for PMax hygiene: it negates the term in every Search campaign too and is capped at 1,000 (Rooijmans, 2025; Hopkins/Optmyzr, 2026; Williams/ZATO, 2023 — "the nuclear option").
2. **Qualify waste.** A term qualifies as a negative candidate at ≥100 clicks and <0.5 conversions over 90 days (Rooijmans, 2024). On large accounts raise the click floor rather than shorten the window. Below the floor, leave it — the term has not had the clicks to prove anything.
3. **Check the keyword alternative first.** If the term has conversions and is not in your Search keywords, do not negate it: add it as an exact-match Search keyword with matching copy and landing page, so Search takes the auction under the identical-keyword rule (Geddes/Adalysis, 2024; Vallaeys/Optmyzr, 2025). Search converts better on the same term 84% of the time in Adalysis' data (Geddes/Adalysis, 2024). Negate in PMax only if the term is worthless everywhere.
4. **Choose match type by intent.** Use phrase or broad negatives for intent words (jobs, free, how to, manual, login) and exact negatives for specific wrong products; match type is set with the usual symbols [Google docs].
5. **Preview, then add anyway.** Run Google's impact estimate in batches of 10 [Google docs]. Read a projected conversion loss as the conversions that term was bringing — if step 3 moved them to Search, the loss is expected and not a reason to stop. Treat a large projected loss on a term you have not keyworded as a flag to go back to step 3.
6. **Cover misspellings.** PMax terms skew heavily to misspellings and missing spaces (Geddes/Adalysis, 2024). Converting misspellings become exact-match Search keywords; non-converting ones are usually not worth a negative slot unless they recur.
7. **Cadence.** Weekly alert from the script (Rooijmans, 2024); periodic review of the list, adding brand close variants and low-performing PMax terms as they surface (Rooijmans, 2025).
8. **Turn off the recommendations that undo this.** Auto-apply "remove redundant keywords" and similar keyword-removal recommendations hand terms back to PMax (Vallaeys/Optmyzr, 2025; Geddes/Adalysis, 2024).

## What Google will tell you instead, and why we don't
Google's help places PMax negatives under brand suitability — a tool for blocking unsafe queries — and offers an impact estimate that projects conversion loss from adding them [Google docs]. We use negatives as a routine performance control on a click/conversion threshold (Rooijmans, 2024), and we read the projected loss as a routing question rather than a stop sign, because the same term usually converts better in Search (Geddes/Adalysis, 2024). We also refuse Google's redundant-keyword recommendation for the same reason (Vallaeys/Optmyzr, 2025).

## Failure modes
- **Low-volume campaigns**: the 100-click floor never triggers; forced lower floors produce negatives on noise. Read categories, not terms.
- **Display/video-heavy PMax**: waste is on inventory negatives do not reach; use placement and content exclusions instead (Bhandari/Optmyzr, 2026).
- **Hotel/travel PMax**: negatives unsupported [Google docs].
- **Retail with long-tail product queries**: exact negatives on individual product misspellings eat the 10,000 limit for no return; use phrase intent negatives.
- **Account-level route in multi-campaign accounts**: a PMax negative silently blocks a Search keyword elsewhere (Rooijmans, 2025).
- **No PMax search terms data** (store-goal campaigns, or terms in the Blank bucket): nothing to qualify against [Google docs].

## What to measure
Negatives added per month and the clicks they represented over the prior 90 days. Terms promoted to Search instead, and their Search CVR after 30 days. Category drift after each batch (skill 57, step 5). Distance to the 10,000 limit. Count of keyword-removal recommendations auto-applied (should be zero).

## Open disagreements in the canon
Rooijmans and Hopkins treat the negative as the primary tool; Geddes and Vallaeys treat the Search keyword as primary and the negative as the fallback. Epiminds goes keyword-first on any term with conversions and negative-first on terms with none, because the studies show Search wins the same term most of the time and a negative throws that value away.
