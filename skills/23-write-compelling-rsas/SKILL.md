---
name: write-compelling-rsas
id: 23
description: Rules for writing a new RSA or rewriting an underperformer — how many lines, how long, what mix, what case, what to leave out. Not for pin structure (24), the ongoing test loop (22), or compliance text (32).
tags: Technique / Search / Setup / Any / As needed
last_verified: 2026-10-13
invalidated_by: Change to the 30/90 character limits or to which slots are always shown; Google routinely serving more than three headlines; mandatory AI Max text assets in Search.
---
## What this is
A writing spec for RSAs built on measured effects rather than frameworks: fewer, shorter, distinct lines in a balanced mix, judged on conversions per impression. It contradicts the "fill all 15 headlines, use every character" default that Google's UI and most templates push.

## Where it comes from
Frederick Vallaeys / Optmyzr (2026, ~20,000-account creative study: length and case effects), Navah Hopkins / Optmyzr (2024, 22,000 accounts / 1M+ ads), Brad Geddes / Adalysis (2022 series on RSA creation; 2026 account tests on keyword insertion, prices and B2B messaging; Adalysis testing checklist), Optmyzr 2022 study (DKI/customizer effect). Platform limits from Google Ads Help, labelled.

## When to use it / when not to
Use when writing a new RSA, or rewriting one that loses on conversions per impression in skill 22. Not for brand campaigns where the message is fixed by brand rules, and not for the first draft of compliance-heavy ads (skill 32 sets the pinned text first; this skill writes around it).

## Inputs
- Ad group keyword theme and the dominant query intent (researcher vs buyer — Adalysis checklist).
- The offer, 2–3 USP/authority facts, and the landing-page promise.
- The ad group's data budget from skill 22 rule 1 (decides how many unpinned lines you can afford).
- Any text that must appear in every impression (goes to skill 32 / 24 for pinning).

## Method
1. **Set the line count from the data budget, not the limit.** Start at 8–10 headlines and 3 descriptions, not 15/4. Geddes (Adalysis, 2022) shows 15 unpinned headlines produce up to 2,940 combinations; the Adalysis checklist's rule is "don't just add 15 headlines because Google allows it." Add lines only when the ad group clears 100 impressions per combination (skill 22). Google's page says more headlines means more combinations — true, and that is the cost.
2. **Write in thirds.** Roughly equal counts of (a) ad-group-relevant lines that echo the query, (b) CTAs, (c) USP or authority lines — about three of each in Geddes' example (Adalysis, 2022). Any random triple must read as one ad; one relevant line surrounded by generic ones weakens the ad (Geddes, 2022).
3. **Keep headlines under 20 characters where the message allows.** Across ~20,000 accounts, headlines under 20 characters had CPA $9.35 vs $18.27, CVR 10.39% vs 8.61% and CTR 11.77% vs 10.52% (Vallaeys/Optmyzr, 2026). Hopkins (Optmyzr, 2024) found the same direction: headlines benefit from concision. Never pad a 14-character headline to 29. But no one- or two-word lines either — they are not distinct (Geddes, 2022).
4. **Write descriptions to 61–70 characters.** That band led on CTR (12.33%), CVR (9.21%) and CPA ($11.49); 81–90 characters had the highest CPC ($1.71) and a CPA of $20.11 (Vallaeys/Optmyzr, 2026). Descriptions want some length, not the maximum (Hopkins, 2024).
5. **Default to sentence case; keep title case where an ad already performs.** RSAs performed better in sentence case in the 2024 study (Hopkins); the 2026 all-accounts cut shows headline CPA $7.46 sentence vs $27.47 title, but its common-account sample was 31 accounts, which Vallaeys himself calls too small. So: new ads in sentence case; existing title-case ads that perform are left alone and the switch is tested via skill 22 rule 6 (Hopkins, 2024).
6. **No keyword insertion or customizers by default.** DKI and ad customizers raised impressions per ad but lowered conversions per ad across 432,343 ads (Optmyzr, 2022); in Geddes' 2026 account tests ads without keyword insertion beat ads with it on both CTR and CVR. Write the keyword theme into the relevant third by hand. Reserve customizers for the cases in skills 28–29.
7. **Pick the CTA by intent and value, not by CVR.** In Geddes' 2026 B2B example "get a quote" had lower CVR than "affordable" but won on conversion value per impression. Researchers and buyers need different messages (Adalysis checklist). Write the CTA to the stage the ad group's queries are in; judge on value per impression.
8. **Prices and locations are tests, not defaults.** Prices in headlines trended worse and location mentions performed worse in Geddes' 2026 tests, both flagged as unequal tests. Put them in one ad group set under a label and test (skill 22 rule 6) before rolling out.
9. **Don't recreate an ETA.** Max-length lines, title case and three fixed headlines applied to RSAs declined almost every metric (Hopkins, 2024). If the message needs fixing in place, use partial pins (skill 24), not ETA habits.
10. **Hand off.** Lines that must appear every time go to skill 32/24 for pinning. Then launch and run skill 22.

## What Google will tell you instead, and why we don't
Google's RSA page tells you to add up to 15 headlines and 4 descriptions, reports ~15% more clicks and conversions from Poor→Excellent Ad Strength (internal data, Aug 2025), and offers keyword insertion and AI Max text customisation in the editor. We write fewer, shorter lines because the measured effects point the other way (Vallaeys 2026; Hopkins 2024) and because every unpinned line costs data (Geddes 2022). Headline length barely correlates with Ad Strength (0.056; Vallaeys, 2026), so chasing the rating will not get you shorter, better headlines. We leave AI Max text assets off: they are not listed with the ad's own assets (Google Ads API docs, 2026), so they cannot be judged or iterated.

## Failure modes
- Legal or regulated verticals where the mandatory line is itself 25–30 characters: the under-20 rule does not apply to that line; pin it (skill 32) and keep the other lines short.
- Very high-volume ad groups (50,000+ clicks a month, per Geddes' 2022 example): the data budget is not binding, so running 12–15 lines unpinned is fine and the line-count cap is relaxed.
- Brand campaigns: the "relevance third" collapses to the brand name; the thirds rule does not fit, use fewer lines and pin per skill 24.
- Markets with double-width scripts: characters count double (Google Ads Help), so the 20-character guidance is not transferable; and the length and case findings are from a sample Vallaeys says skews to experienced, likely English-heavy advertisers — treat them as hypotheses outside English (see skill 33).
- Sentence-case conversion of ads that already perform: Hopkins (2024) explicitly warns against it.

## What to measure
Conversions (or conversion value) per impression per ad and per asset after the ad group clears its data budget; headline-length and description-length distribution of the live assets; share of assets with zero impressions after 14 days (Vallaeys, 2021 threshold via skill 22).

## Open disagreements in the canon
- Line count: Google and Optmyzr's product content say fill to 15/4; Geddes and the Adalysis checklist say fewer, pinned, data-dense. Epiminds goes with Geddes, with a volume exception.
- Case: the 2026 sentence-case numbers are large but the matched-account sample is thin; Hopkins (2024) is directional. Epiminds defaults new ads to sentence case and tests rather than converts.
- Keyword insertion: Google offers it as relevance; Optmyzr 2022 and Geddes 2026 show it buys impressions at the cost of conversions. Epiminds writes relevance by hand.
