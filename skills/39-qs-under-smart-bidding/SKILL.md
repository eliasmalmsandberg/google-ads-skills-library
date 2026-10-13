---
name: qs-under-smart-bidding
id: 39
description: The evidence inventory and Epiminds position on how much effort Quality Score work deserves in accounts on Smart Bidding, with an effort-allocation rule. Use when scoping QS work or answering a client who asks whether QS still matters. Not a fixing procedure (34–38).
tags: Research / Search / Optimise / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google publishing how Smart Bidding treats quality components, a canon cross-account study of QS work under Smart Bidding, or removal of keyword-level QS.
---
## What this is
A short, honest inventory of what the canon actually knows about Quality Score under Smart Bidding, and the rule Epiminds derives from it. The headline: every practitioner in the canon says QS still matters, none says it is the lever that moves accounts, and nobody has published a controlled study of QS work under Smart Bidding. The strongest data points are Geddes's finding that QS discounts CPC mainly at position 1 and otherwise buys rank (Geddes/Acquisio, c.2016) and Vallaeys's observation that a uniform 2-point reported QS drop left CPCs "a mixed bag" across accounts (Optmyzr, 2015).

## Where it comes from
Vallaeys, Hopkins and Tyagi's three-way split on PPC Town Hall (Optmyzr, 2020). Geddes's Ad Rank weighting estimate and position-1 CPC finding (Acquisio, c.2016) and his "ten across the board, stop worrying" rule (Acquisio interview, undated). Levy's ROAS-first rule and the query-mix point (Optmyzr, 2026). Hopkins's health-indicator framing (SEL, 2023). Mark Irvine's "10% vs 10×" framing (quoted in WordStream, 2021; Tier 2 on bidding). Google's own statement that QS is a diagnostic and not an auction input [Google docs].

## When to use it / when not to
Use when deciding how many hours a month go to QS work in a Smart Bidding account, when a client asks whether QS still matters, or when a proposal needs a defensible position.
Do not use to justify skipping skills 34–36 on an account whose money keywords are at QS ≤ 4 — Geddes's position is that QS matters precisely for accounts doing it badly (Acquisio interview, undated). Do not use for PMax or Shopping: QS is keyword-level Search only [Google docs], and the canon's PMax view is that conversion data quality matters more than any keyword score (Optmyzr/Levy, 2026).

## Inputs
- Impression-weighted QS for brand and non-brand separately (skill 38).
- Share of non-brand Search impressions at QS ≤ 4 and ≥ 7.
- Position data: share of impressions at absolute top for the top-spend keywords.
- Current bid strategy per campaign and whether conversion tracking is trusted (Hopkins: don't run Smart Bidding on conversions you don't trust — Optmyzr Town Hall, 2020).

## Method
1. **State the mechanism correctly.** The 1–10 score is a diagnostic and not an auction input; the auction uses real-time quality signals that the score reflects [Google docs]. Vallaeys fact-checked this framing (quoted in Gales, 2026, corroborating) and still holds that quality is roughly half of Ad Rank alongside the bid (Optmyzr Town Hall, 2020); Geddes's estimate from $100M+ spend was ~40% QS, ~50% bid, ~10% extensions (Acquisio, c.2016 — his estimate). Smart Bidding sets the bid; it does not change the quality half (Tyagi, Optmyzr Town Hall, 2020). Output: QS work is not made irrelevant by Smart Bidding; it is made secondary.
2. **Record what the evidence supports and what it doesn't.**
   - Supported: QS affects where an auto-set bid lands and whether assets show (Tyagi, 2020; Gales, 2026 corroborating). CPC discounts show mainly at position 1; elsewhere the payoff is rank and impression share (Geddes, c.2016). Reported-QS movement does not map cleanly to CPC — the 2015 incident moved QS 2 points and CPCs went up, down and flat (Vallaeys, 2015).
   - Not supported by any canon source: a CPC-by-QS multiplier table; any measured lift from QS work in a Smart Bidding account; any claim that Smart Bidding ignores quality.
   Output: no CPC-savings promise goes into a proposal.
3. **Effort rule.** Irvine's framing — QS work might move results ~10%, strategy 10× (WordStream, 2021) — and Levy's rule — never trade ROAS for QS (Optmyzr, 2026) — set the budget. Epiminds allocation per Search account on Smart Bidding:
   - Non-brand wQS ≥ 7 and ≤ 10% of non-brand impressions at QS ≤ 4 → zero scheduled QS hours; monitor via skill 37/38 only. Geddes: "ten across the board", stop worrying (Acquisio interview, undated).
   - Non-brand wQS 5–7 → QS work only inside the ad-group queue from skill 38 (wQS < 6, cost > 0), capped at 10% of monthly optimisation time.
   - Non-brand wQS < 5 or > 30% of impressions at QS ≤ 4 → treat as an account-structure and ad problem, not a QS problem: Geddes's order is organisation, then ad testing (Acquisio, 2018); run 35 then 34 before anything else. This is also the only case where QS work precedes bid-strategy work.
   The wQS cut-points are Epiminds operating thresholds built from Hopkins's bands (7–9 settled, 5–6 drift; SEL, 2023) and Gales/Optmyzr's "7 is really good, 6 is fine" (Optmyzr, 2026).
4. **Sequence against the bidding work.** Tyagi: profitability, conversion tracking, targets and keywords come before QS (Town Hall, 2020). If conversion tracking is untrusted, QS work waits — fixing the signal moves the auto-bid more than any quality gain (Hopkins, Town Hall, 2020).
5. **Measure the payoff as rank and volume, not CPC.** Geddes (c.2016) and Vallaeys (2015) both show CPC is the wrong readout. For QS work in Smart Bidding accounts, success = absolute-top impression share and search impression share on the worked ad groups at the same tCPA/tROAS, with conversions per impression flat or up (Geddes, 2016, via skill 34).
6. **Watch the query mix, which Smart Bidding changes.** Broad match plus Smart Bidding expands the queries behind a keyword; the visible score is dominated by the worst of them (Levy, Optmyzr, 2026), and broad runs lower QS while winning cheaper positions (Hopkins, SEL, 2023). A falling wQS after a broad-match expansion is expected and is not a reason to revert the expansion unless rule 5's metrics also fall.
7. **Re-examine annually.** No canon practitioner has published data since the Smart Bidding default; the position is reasoning, not measurement (dossier finding). Refresh this skill when any canon source publishes a cross-account study.

## What Google will tell you instead, and why we don't
Google says QS is "not a key performance indicator and should not be optimised" [Google docs]; Marvin's line is that nothing has changed in how to think about it (quoted in Optmyzr, 2026). We agree it is not a KPI. We disagree with the inference the UI invites — that with diagnostic scores and automated bids, quality work is optional. We take Tyagi's position: Google sets the bid, quality decides where it lands (Optmyzr Town Hall, 2020), bounded by Levy's rule that it never costs ROAS (Optmyzr, 2026). We equally reject the agency-content CPC-by-QS savings table: no canon source supports it and Vallaeys's 2015 data contradicts a clean mapping (Optmyzr, 2015).

## Failure modes
- **Accounts with bad structure masquerading as "Smart Bidding will handle it"**: Geddes's whole case is that QS punishes accounts doing it badly (Acquisio interview, undated); rule 3's third tier exists for them.
- **B2B lead-gen where low QS is deliberate**: pre-qualifying copy lowers expected CTR and improves lead quality (Geddes/Acquisio, c.2016); QS hours here are wasted or harmful.
- **Brand-dominated accounts**: wQS looks fine while non-brand is weak; rule 3 is computed on non-brand only.
- **PMax, Shopping, DSA-heavy accounts**: no keyword QS; the canon's advice is conversion data quality (Optmyzr/Levy, 2026).
- **Untrusted conversion tracking**: any QS gain is swamped by bid errors (Hopkins, Town Hall, 2020).
- **Clients promised CPC savings**: the only outcome data in the canon shows mixed CPC movement (Vallaeys, 2015); promise rank and impression share, or nothing.

## What to measure
- Non-brand wQS and share of impressions at QS ≤ 4 (skill 38), quarterly.
- Absolute-top and search impression share on worked ad groups at constant targets (Geddes, c.2016).
- Conversions per impression on worked ad groups (Geddes, 2016).
- Hours spent on QS work vs the rule-3 cap.
- CPC — recorded, never the success metric (Vallaeys, 2015).

## Open disagreements in the canon
- **Does QS still earn attention?** Vallaeys/Tyagi/Irvine: yes, the auction maths is unchanged (Town Hall, 2020; WordStream, 2021). Hopkins: focus on quality itself and the outcome metrics (Town Hall, 2020; SEL, 2023). Epiminds: yes, but budgeted — rule 3.
- **Is the visible score a usable proxy for auction-time quality?** Gales and Vallaeys say it is the best available proxy (2026); Levy says it is dominated by the worst queries behind each keyword (2026). Epiminds reads it impression-weighted and alongside search terms, per skills 38 and 34.
- **Price or rank?** Geddes: rank except at position 1 (c.2016); Vallaeys: "slightly less per click" to hold position (2020). Epiminds measures rank and impression share; CPC is noted, not claimed.
- **How much does QS weigh in Ad Rank?** Geddes's 40% is an estimate from his data (c.2016); Vallaeys says "half" (2020); Google publishes no weight. We do not quote a weight to clients.
