# Dossier — 39 Does QS matter under Smart Bidding — the evidence

## Sources

1. **Source**: Optmyzr PPC Town Hall 23, "How top PPC experts manage bids for lead gen" (Fred Vallaeys, Navah Hopkins, Geetanjali Tyagi) — https://www.optmyzr.com/ppc-town-hall/how-top-ppc-experts-manage-bids-for-lead-gen/ · **Tier** 1 · **Date** 30 Sep 2020 · **Claim**: Vallaeys — QS matters because it is half of Ad Rank alongside bid and reflects the CTR signal Google uses; a higher score can mean paying slightly less to hold position; never improve QS for its own sake. Hopkins — focus on quality, impression share, conversion rate and CTR rather than the score; unsure whether QS matters going forward. Tyagi — under automated bidding Google sets the bid and QS affects where it lands, so still worth watching, but never before profitability, conversion tracking and targets. Hopkins anecdote: geo-modified keywords often have higher QS and sometimes better lead quality. · **Evidence**: none cited; reasoning from auction mechanics and experience.

2. **Source**: Brad Geddes, Acquisio webinar write-up — https://www.acquisio.com/blog/?p=6300 · **Tier** 1 · **Date** undated, c.2016 · **Claim**: Ad Rank ≈ 50% bid / 40% QS / 10% extensions (estimated from $100M+ spend); CPC discounts from QS appear mainly at position 1, lower positions get rank not price; landing page status relates to impression share, not CPC; in B2B lower QS can be preferable. · **Evidence**: Geddes's own aggregated analysis; pre-Smart-Bidding-default era.

3. **Source**: Optmyzr blog (Ronia; quotes Vallaeys, Aaron Levy, Jyll Saskin Gales, Ginny Marvin) — https://www.optmyzr.com/blog/google-ads-quality-score/ · **Tier** 1, vendor caveat · **Date** 2 Mar 2026 · **Claim**: Smart Bidding optimises toward conversion signals, not keyword-level adjustments; Levy — "I wouldn't necessarily do changes solely for QS purposes at the expense of ROAS/ROI"; for PMax, conversion data quality matters more than a keyword-level score (no data); visible QS historical and aggregated, auction-time quality recalculated per query; Marvin — "I wouldn't say there's been any change really in how to think about Quality Score"; article calls QS "not a KPI" while Optmyzr sells a tracker. Only quantitative claim is a second-hand SEL note that phrase-match CPCs rose faster than broad 2023–2025. · **Evidence**: opinion; no study.

4. **Source**: Navah Hopkins, Search Engine Land — https://searchengineland.com/quality-score-ppc-394513 · **Tier** 1 · **Date** 2023 · **Claim**: QS is a health indicator not a KPI; optimise actual CTR not expected CTR; broad struggles with QS but wins cheaper positions; Ad Strength doesn't affect QS; no Smart Bidding discussion beyond PMax blending brand/non-brand. · **Evidence**: observation.

5. **Source**: WordStream (Susie Marino), "Does Quality Score still matter?" — https://www.wordstream.com/blog/ws/2021/07/19/does-quality-score-still-matter · **Tier** 2 for Mark Irvine's quoted position only (canon lists Irvine for bidding/IS) · **Date** 19 Jul 2021 (page mentions 2023/2025 updates) · **Claim**: Irvine — QS is still an equal factor in Ad Rank, the maths is unchanged, but it is no longer a "silver bullet"; fixing QS might improve results ~10% while fixing strategy might improve them 10×; Google has tripled ad size since 2013 so quality is harder to differentiate. Marino (author): "personally anti-Quality Score", not actionable, search-only, often uncorrelated with performance. Babaa: branded keyword at QS 3 despite strong performance. · **Evidence**: screenshots, no measured results.

6. **Source**: Jyll Saskin Gales, Inside Google Ads ep. 107 — https://iga.buzzsprout.com/2295853/episodes/18592384 · **Tier** not canon (ex-Googler; corroboration only) · **Date** 12 Feb 2026 · **Claim**: the 1–10 score is a proxy for the real-time ad quality used in each auction; Vallaeys fact-checked the diagnostic-vs-auction distinction as correct; bid strategy and conversion tracking don't affect QS directly but can be root causes of poor expected CTR; bid "probably set by Smart Bidding by now" and Ad Rank still weighs quality. · **Evidence**: opinion.

7. **Source**: Fred Vallaeys, Optmyzr, "Here's why your Quality Score suddenly plummeted" — https://www.optmyzr.com/blog/why-did-my-quality-score-plummet · **Tier** 1 · **Date** 30 Mar 2015 · **Claim**: across a handful of accounts, a uniform ~2-point reported QS drop produced costs and CPCs that were "a mixed bag" — up, down, flat. · **Evidence**: multi-account observation; the single piece of outcome data on reported QS vs CPC in the canon.

8. **Source**: Brad Geddes, Acquisio interview — https://www.acquisio.com/blog/?p=3743 · **Tier** 1 · **Date** undated (Acquisio Summit era) · **Claim**: if scores are "ten across the board" stop worrying; QS mainly applies to advertisers doing it poorly; not every account should try to improve it; methods are organisation and ad testing. · **Evidence**: opinion.

## Dissenting view
The canon splits three ways. Vallaeys/Tyagi/Irvine: the auction maths is unchanged, quality still halves the bid you need, so it matters even when Google sets the bid. Hopkins/Levy: the score is a lagging aggregate; work on quality, conversions and ROAS and let the score follow. Geddes (older): it matters a lot for accounts doing it badly and not at all for accounts doing it well — and sometimes a lower score is correct. The disagreement is about marginal value: nobody in the canon claims QS is irrelevant, and nobody has published a controlled study of QS work under Smart Bidding.

## What the platform currently does [Google docs]
- [Google docs] answer/6167118 (fetched 2026-10-13): QS is a diagnostic; "not an input in the ad auction"; "not a key performance indicator"; the auction uses real-time ad quality signals. Google's auction documentation continues to name expected CTR, ad relevance and landing page experience as Ad Rank quality components (as summarised in Optmyzr 2026 and Gales 2026; the help page itself describes QS as a reflection of those).
- [Google docs] Smart Bidding sets bids per auction from conversion signals; no Google documentation states that QS components are excluded from or weighted differently under Smart Bidding (none found; absence noted).
- [Google docs] Null QS since Sep 2016; historical columns since May 2017.
- Ginny Marvin (reference only): no change in how to think about QS (quoted in Optmyzr, 2026).

## Baseline check
Read `google-ads-quality-score` and `google-ads-bidding`-adjacent sections of the QS baseline. The baseline asserts QS improvements lower CPC "even if the reported number lags" and offers a CPC multiplier table with no source. This skill replaces that with the actual evidence inventory: what each canon practitioner claims, what data exists (Geddes's position-1 finding, Vallaeys's mixed-bag CPCs, Irvine's 10% vs 10× framing), what does not exist (any controlled study), and an effort-allocation rule derived from it.

## Judgment calls
- Classified as Research: the output is a position and an effort budget, not a procedure for fixing QS.
- WordStream is not canon; used only for Mark Irvine's quoted position (Tier 2 on bidding) and to document the sceptic case; Marino and Babaa are recorded, not relied on.
- Gales is used only to corroborate the proxy framing Vallaeys fact-checked.
- No cross-account study linking QS work to Smart Bidding outcomes was found in any canon source; the skill says so rather than inventing a CPC curve.

## Canon strength: Adequate
Five Tier 1/2 practitioners with positions (Vallaeys, Hopkins, Tyagi, Geddes, Levy, Irvine); evidence limited to Geddes's aggregated analysis and Vallaeys's 2015 incident data. Not Thin, because the positions and their reasoning are published; not Strong, because no one brings a study.

## Invalidated by
Google publishing how Smart Bidding treats quality components, a canon cross-account study of QS work under Smart Bidding, or removal of keyword-level QS.
