---
name: pmax-brand-exclusions
id: 55
description: Decide whether, and how, to take brand queries out of a Performance Max campaign — measurement, threshold, handover prerequisites, and the leak checks afterwards. Not for Search-campaign brand restrictions (AI Max) or for competitor-brand conquesting.
tags: Technique / PMax / Protect / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google extending brand exclusions beyond Search, Shopping and YouTube-search inventory; a change to broad-match-based brand-list matching; removal of the "Allow Shopping ads on excluded brand searches" option; a change to the exact-match-keyword priority rule between Search and PMax.
---
## What this is
A decision rule for brand in PMax. PMax reports a blended number; when brand queries sit inside it, profitable brand conversions hide wasteful non-brand spend behind an on-target average (Rooijmans, 2024). But excluding brand is not free: Kirk Williams has seen total brand sales fall after brand was removed from PMax even with brand pushed into Search and Shopping (Williams/ZATO, 2026). So the skill measures first, sets a threshold, and only then applies the brand list — with the handover campaigns in place before the switch.

## Where it comes from
Kirk Williams (ZATO, 2022 and 2026) on when exclusion is and isn't worth it; Nils Rooijmans (2022) on the priority rule and close variants; Mike Rhodes' PMax Insights S.Cat buckets (Rhodes, 2026) and the smec Brand Traffic Analyzer (Baudisch, 2024) for measurement; Optmyzr's 503-account overlap study (Vallaeys, 2025) for the fuzzy-match leak; Optmyzr's BFCM data (2026) and PPC.io's 84-campaign audit (Dunlop, 2026) for the distribution of brand share.

## When to use it / when not to
Use when PMax ROAS looks better than Search/Shopping and you suspect brand is the reason, when a client asks "is PMax just buying our own name", or at any PMax launch where a brand Search campaign already exists. Do not use for a DTC brand with negligible brand demand (nothing to exclude), or for a brand sold through many retailers where brand searches are price-comparison rather than navigational — Williams argues those are mid-funnel and belong in PMax (Williams/ZATO, 2022).

## Inputs
- 30–90 days of PMax search-category data bucketed Brand / Close Brand / Non-Brand / Blank, with your brand terms entered in the script config (Rhodes, 2026) — or the smec analyzer's brand vs non-brand time series (Baudisch, 2024).
- The brand Search campaign: its daily budget, Search lost IS (budget), and its keyword list including misspellings.
- Whether a brand Standard Shopping campaign exists.
- The PMax campaign's bid strategy and target.

## Method
1. **Measure brand share.** Compute brand+close-brand clicks ÷ total categorised PMax clicks, and brand conversions ÷ total PMax conversions, over the last 30 days. Treat the Blank bucket as non-brand: smec's experience is that >90% of uncategorised terms are non-brand (Baudisch, 2024). Benchmarks: across 84 PMax campaigns the median brand click share was 14%, 38% of campaigns were above 20%, 14% above 50% (Dunlop/PPC.io, 2026).
2. **Apply the threshold.**
   - Brand clicks <10% of PMax clicks and brand conversions <30%: leave brand in. The 10% line is an Epiminds/dossier rule derived from PPC.io's distribution — reason: it sits below the 14% median, the half of campaigns where the management-cost argument holds (Dunlop/PPC.io, 2026). Williams' position is that exclusion is rarely worth the management cost at low share and risks the handover loss he has observed (Williams/ZATO, 2026).
   - Brand clicks ≥20% of PMax clicks, or brand conversions ≥30% (the Pooler flag in Optmyzr's guide, 2026): exclude, subject to step 3.
   - Between 10% and 20% clicks: run the exclusion as a dated test for one full conversion cycle and compare total brand revenue (Search + Shopping + PMax) before vs after; keep it only if blended brand revenue holds.
3. **Check the handover prerequisites before excluding.** The exclusion only works if something else catches the demand:
   - Brand Search campaign is not budget-limited (Search lost IS budget ≈ 0). A budget-capped brand campaign is the documented failure case for keeping PMax off brand (Beltman, in Rooijmans, 2022).
   - Brand Search contains the close variants and misspellings as exact match. Optmyzr found PMax still triggers on fuzzy brand matches despite brand exclusions, and recommends adding branded misspellings as exact-match keywords (Vallaeys/Optmyzr, 2025).
   - If brand Shopping traffic is to leave PMax too, a brand Standard Shopping campaign exists (Williams/ZATO, 2022). If it does not, tick "Allow Shopping ads on searches that mention excluded brands" and exclude only the text/search side.
4. **Apply at campaign level with a brand list**, never with account-level negatives: account negatives are capped at 1,000 and hit every Search campaign too (Hopkins/Optmyzr, 2026; Williams/ZATO, 2023 calls the account-level route "the nuclear option"). Use Brand Exclusions, not keyword negatives, for the brand itself (Hopkins/Optmyzr, 2026). Request any missing brand through the list UI; it is usable immediately by the requester [Google docs].
5. **Expect the number to move.** Brand exclusions apply only to Search, Shopping and YouTube-search inventory [Google docs]; Display/Video/Discover remain. PMax ROAS will fall — Optmyzr's 2025 peak-season data shows PMax branded ROAS at 741–811% vs non-branded 713–743% (Optmyzr, 2026), so the drop is usually modest, but set the client's expectation and re-baseline the tROAS target against the non-brand number from step 1.
6. **Verify the leak after 14 days** — Epiminds/dossier rule derived from Google's "allow 1–2 weeks for stabilization" after PMax changes [Google docs]; reason: earlier reads are still moving. Re-run step 1. Brand share should fall toward the Blank/unknown floor. If brand clicks persist above 5% (Epiminds/dossier rule — reason: half the 10% leave-in line, so anything above it would still have been worth acting on), the misses are fuzzy variants: add them to the brand Search campaign as exact match (Vallaeys/Optmyzr, 2025) and, if the brand is missing from Google's library, request it.
7. **Verify total brand revenue.** Compare brand revenue summed across Search + Shopping + PMax for the 4 weeks after vs the 4 weeks before — the re-audit window Dunlop uses after PMax fixes (Dunlop/PPC.io, 2026). If it is down and brand Search impression share is not near 100%, revert and fix brand Search first; this is the failure Williams reports (Williams/ZATO, 2026).

## What Google will tell you instead, and why we don't
Google's help frames exclusions as reach-reducing — "apply only where needed", monitor for missed conversions — and positions PMax as full-funnel [Google docs]. We exclude anyway above the threshold because the blended number is not a performance read: brand conversions mask non-brand waste (Rooijmans, 2024) and the campaign cannot carry separate brand and non-brand targets. Google also says brand-list matching covers misspellings and variants automatically [Google docs]; Optmyzr's 503-account data shows fuzzy brand matches still leak into PMax, so we keep the exact-match variant list in Search regardless (Vallaeys/Optmyzr, 2025).

## Failure modes
- **Multi-retailer or household brands**: brand queries are price-comparison, not navigation; excluding removes mid-funnel demand (Williams/ZATO, 2022).
- **Budget-capped brand Search**: PMax exclusion hands brand queries to nobody; brand sales fall (Beltman, in Rooijmans, 2022).
- **Low-spend accounts**: management cost exceeds the gain; Williams keeps brand combined in low-spend accounts (Williams/ZATO, 2026).
- **No brand Standard Shopping campaign** but Shopping checkbox unticked: brand product-listing demand goes unserved.
- **Lead-gen with incomplete offline conversion import**: brand conversions are often the only clean signal PMax has; removing them weakens learning (dossier judgment; the canon evidence here is e-commerce).
- **Rebranded or new brand not in Google's list**: nothing is excluded until the request is processed.

## What to measure
Brand vs non-brand click and conversion share in PMax (Rhodes S.Cat or smec analyzer), weekly. Blended brand revenue across all campaign types, 4 weeks pre/post. Brand Search impression share and lost IS (budget). PMax non-brand ROAS vs the Search non-brand baseline. Residual brand share after exclusion (target: under 5%, the Epiminds rule in step 6).

## Open disagreements in the canon
Williams (2022, 2026) vs Rooijmans (2022) and the smec/Rhodes tooling: whether brand belongs in PMax at all. Williams says it is mid-funnel data the algorithm should see and that exclusion has cost him brand sales; Rooijmans says brand distorts the read and must be isolated. Epiminds goes with measurement plus threshold: below 10% share we take Williams' view; above 20% we take Rooijmans', because that is where the blended number stops being a usable control.
