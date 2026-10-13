---
name: pmax-search-terms-insights
id: 57
description: What query-level data a Performance Max campaign actually exposes (categories, terms, the Blank bucket, which metrics are missing), how to pull it, and the thresholds for mining it into negatives, Search keywords and theme changes. Not for Search-campaign search term reports or n-gram analysis.
tags: Diagnostic / PMax / Optimise / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Google adding cost to term-level PMax reporting; removal of the PMax search terms report or the campaign_search_term_insight API resource; asset-group-level negatives; a change to the privacy threshold that withholds low-volume terms.
---
## What this is
PMax exposes two layers of query data: **search categories** (Google's groupings) and, since the 2025 rollout, **search terms** with conversions, clicks and impressions — but no cost at either level (Rooijmans, 2024; Vallaeys/Optmyzr, 2025) [Google docs]. A share of traffic is withheld as a Blank bucket. This skill is the operating procedure for turning that into decisions: which terms become campaign negatives, which become exact-match Search keywords, which themes to swap, and what to stop trying to read.

## Where it comes from
Nils Rooijmans' two published scripts against `campaign_search_term_insight` (2023, 2024) supply the data model and thresholds. Brad Geddes/Adalysis (2024) and Fred Vallaeys/Optmyzr (2025) supply the cross-account evidence on what PMax terms look like and how they compare to Search. Mike Rhodes' S.Cat tab (2026) supplies the brand bucketing; Navah Hopkins (2026) the audit sequence; Kirk Williams (2025) the platform timeline.

## When to use it / when not to
Use monthly on any PMax campaign spending enough to produce 100-click terms, and on launch (+14 days) to catch irrelevant themes early. Do not use it to judge channel mix (categories do not carry over to placements — Hopkins/Optmyzr, 2026) or to compute term-level CPA or ROAS: the cost field does not exist, and Optmyzr dropped CPC/CPA/ROAS from its own study for that reason (Vallaeys/Optmyzr, 2025).

## Inputs
- Per-campaign export: PMax campaign → Insights and reports → search terms insight → "view detailed data" → download (slow; one campaign at a time) (Geddes/Adalysis, 2024). Or the API resource `campaign_search_term_insight`, fields category_label, impressions, clicks, conversions, conversion value (Rooijmans, 2024).
- Brand term list for bucketing (Rhodes, 2026).
- Search campaigns' keyword list and search term report for the same window.
- Current PMax search themes.

## Method
1. **Bucket before reading.** Classify every category as Brand / Close Brand / Non-Brand / Blank; without brand terms in the config everything lands in non-brand or blank (Rhodes, 2026). Treat Blank as non-brand: >90% of uncategorised terms are non-brand in smec's experience (Baudisch, 2024). Drop terms under 10 impressions from any comparison, as Adalysis did (Geddes/Adalysis, 2024).
2. **Flag waste.** A term with ≥100 clicks and <0.5 conversions in the last 90 days is a negative candidate (Rooijmans, 2024). For high-volume accounts raise MIN_CLICKS rather than shorten the window; the script itself bails out when runtime is short (Rooijmans, 2024). Apply the flagged terms as campaign-level negatives (shared list), after previewing impact — Google's estimator takes 10 keywords per preview [Google docs]. Brand terms go through Brand Exclusions, not negatives (Hopkins/Optmyzr, 2026).
3. **Flag winners for Search.** Any non-brand term with ≥2 conversions in 90 days that is absent from your Search keywords becomes an exact-match Search keyword in an ad group with matching copy and landing page (Geddes/Adalysis, 2024; Vallaeys/Optmyzr, 2025). Expect many: 45% of PMax terms in Adalysis' 1.2M-term sample also appeared as Search terms, and Search converted better on the same term 84% of the time (Geddes/Adalysis, 2024).
4. **Check misspellings.** PMax terms are disproportionately misspelled or missing spaces (Geddes/Adalysis, 2024). Add the converting ones as exact-match keywords in Search; Google no longer reports misspellings for Search, so PMax is where you see them.
5. **Watch category drift weekly.** Flag any category whose 7-day impressions moved by more than 100 impressions AND more than 50% vs the prior 7 days (Rooijmans, 2023). A surge in an off-topic category after an asset or theme change is the earliest signal that the change expanded reach in the wrong direction.
6. **Audit themes monthly.** If search themes overlap heavily with your Search keywords, replace them: they are pulling the same auctions into PMax (Hopkins/Optmyzr, 2026). Test exact-match keyword concepts you do not run in Search as themes instead, to find incremental traffic (Hopkins/Optmyzr, 2026).
7. **Read the brand line.** If more than 30% of conversions come from brand terms despite exclusions, investigate the exclusion before anything else (Pooler, in Optmyzr guide, 2026); see skill 55.
8. **Stop at the Blank bucket.** Do not infer what withheld terms are; treat the bucket's conversions as non-brand and its size as a ceiling on what the term-level view can tell you (Rhodes, 2026; Baudisch, 2024).

## What Google will tell you instead, and why we don't
Google's help positions PMax negatives as a brand-suitability control and frames the report around conversions [Google docs]. We use it as a performance tool, mine it with click/conversion thresholds, and move the winners into Search rather than leaving them for PMax — because Search on the same term converts better most of the time (Geddes/Adalysis, 2024) and PMax reporting gives you conversions without the cost that would let you judge them (Vallaeys/Optmyzr, 2025). Google's "remove redundant keywords" recommendation runs the other way; ignore it, because removing the Search duplicate hands the term to PMax (Geddes/Adalysis, 2024).

## Failure modes
- **Low-volume campaigns**: few terms reach 100 clicks in 90 days; the waste rule never fires. Hopkins cites 60 conversions/30 days as the floor for PMax to behave (Hopkins/Optmyzr, 2026; unsourced figure) — below that, read categories only.
- **Retail-heavy accounts**: Adalysis' sample was non-retail; Shopping-driven PMax terms skew to product titles and the overlap figures may not transfer (Geddes/Adalysis, 2024).
- **Large catalogues on the script route**: the runtime cap stops the fetch; raise MIN_CLICKS or split by campaign (Rooijmans, 2024).
- **Store-goal campaigns**: store visits/sales are absent from the terms report [Google docs].
- **Reading term CVR as ROAS**: no cost, so a 10% CVR on a term you cannot price is not a scaling signal (Vallaeys/Optmyzr, 2025).

## What to measure
Count of terms flagged per month under step 2 and the spend they represented (via clicks × campaign average CPC, as an estimate only). Number of terms promoted to Search and their Search CVR after 30 days. Brand share of conversions. Blank-bucket share of clicks (if it grows, the term-level view is degrading). Category drift alerts per week.

## Open disagreements in the canon
Hopkins (2026) is comfortable comparing PMax "auction prices" by category to Search and acting on the gap; Vallaeys (2025) and Rooijmans (2024) treat cost as unavailable at the term level and stay with clicks and conversions. Epiminds follows Vallaeys and Rooijmans: no cost field, no cost conclusions — category-level cost comparisons wait until Google exposes the field.
