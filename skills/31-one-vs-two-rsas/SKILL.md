---
name: one-vs-two-rsas
id: 31
description: Decide how many RSAs an ad group runs — one, two or three — from volume and testing intent, with the evidence for two as the default. Not for what goes in them (23) or how they are pinned (24).
tags: Research / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: A change to the per-ad-group RSA limit; removal of per-ad reporting; a single auto-generated ad per ad group under AI Max.
---
## What this is
The ad-count rule. The only cross-account evidence finds two RSAs per ad group gave a conversion-rate lift that one or three did not; the practitioner case for one RSA is unsupported opinion; Google also says two, for its own reasons. Epiminds' default is two, with one allowed below a volume floor and three only as a short-lived test arm — and with a rule for the documented failure of two: Google over-serving the worse ad.

## Where it comes from
Optmyzr's 2022 RSA study (13,671 accounts), Frederick Vallaeys (SEJ 2021; SMX Advanced 2022 via Search Engine Land), Brad Geddes / Adalysis (2022 testing method with account examples), Nils Rooijmans' missing-RSA script (2022). The one-RSA position is from Morten Kristoffersen (SavvyRevenue on Optmyzr's blog, 2025), cited as opinion.

## When to use it / when not to
Use at build, at restructure, and whenever an audit flags ad groups with one or three-plus RSAs. The sources do not segment by bid strategy, so this skill applies the same rule under Smart Bidding and manual bidding and says so; the over-serving behaviour in rule 4 is what you will see in any current account.

## Inputs
- Per ad group: enabled RSA count, 30-day impressions, 7-day impressions, conversions.
- Per RSA: impressions, conversions per impression (skill 22), combination count (skill 22 rule 1).
- Whether a messaging test is live in the ad group (skill 22 rule 4; skill 27).

## Method
1. **Floor: every enabled ad group with traffic has at least one RSA.** Rooijmans' script (2022) flags ad groups below a minimum RSA count and alerts when a flagged ad group passed 1,000 impressions in the last 7 days; use the same thresholds. Ad groups with RSAs got 1.6× the conversions of those without (Vallaeys, 2022).
2. **Default: two RSAs.** Across 13,671 accounts, two RSAs per ad group produced a conversion-rate lift that one or three did not, and more RSAs meant significantly more impressions (Optmyzr, 2022); Vallaeys (2022) calls two "ideal for conversion rates". Build the second RSA around a different value proposition or CTA, not a reshuffle of the first (Vallaeys, 2021).
3. **Exception: one RSA when the ad group cannot pay for two.** If the ad group's impressions divided by its combination count is under 100 even with partial pins (Geddes/Adalysis, 2022 floor), a second ad only halves what each ad learns; run one partially pinned RSA (skill 24) and iterate it through cross-ad-group pattern tests (skill 22 rule 6). This is the only case where the one-RSA argument (Kristoffersen, 2025) is adopted, and it is adopted for Geddes' reason, not his.
4. **Guard against over-serving.** With two or three RSAs Google frequently gives one most of the impressions even when it underperforms; in Geddes' example one RSA took 10× the impressions at under half the conversion rate of its siblings, and pausing it added 200+ conversions in the next 30 days (Adalysis, 2022). Monthly: compare conversions per impression between the RSAs once both clear the data budget; if the most-served ad is worse, pause it and replace it (skill 22 rule 4). Never read two RSAs as "Google picked the winner".
5. **Three only as a test arm with an end date.** Up to three RSAs per ad group for theme tests, each pinning 1–3 assets to the same headline position (Geddes, 2022; Vallaeys, 2021 allows up to three around different value propositions). Three is also the practical maximum (Geddes, 2022; Optmyzr, 2023). Set the end condition at launch: the data budget is met (well over 100 impressions per combination in that ad group; Geddes, 2022) and the arms differ on conversions per impression (Vallaeys, 2021). If the budget is not met within the test window you set at launch — Epiminds operating threshold, no canon source for a fixed week count; reason: Geddes (2022) says low-volume ad groups never produce a consistent read, so an open-ended third arm only splits impressions — pause the lowest conversions-per-impression ad and return to two.
6. **Unique final URLs are not a requirement.** Google's page asks for a unique final URL per RSA; the practitioner sources make no such condition and a second ad with a different landing page is a landing-page test, not an ad test (it confounds skill 22). Use the same URL unless the landing page is the variable.
7. **Audit rule.** Flag: zero RSAs (fix now), one RSA above the rule-3 floor (add a second with a distinct message), three-plus RSAs with no test end date (pause the lowest conversions-per-impression ad).

## What Google will tell you instead, and why we don't
Google's RSA page recommends at least two RSAs per ad group, each with Good or Excellent Ad Strength and its own final URL, citing ~6.6% more conversions from a second RSA and ~3.7% from a third (internal data, Aug 2025). We agree on two, for a different reason — the Optmyzr 2022 conversion-rate finding — and we reject the three conditions attached: Ad Strength is not a performance signal (skill 25), unique final URLs turn an ad test into a landing-page test, and a third RSA is not an incremental gain to be kept but a test arm to be retired (Geddes, 2022), because Google's serving will not reliably favour the better ad (Geddes, 2022).

## Failure modes
- Low-volume ad groups (a few hundred impressions a month): two RSAs give inconsistent weekly metrics and nothing to compare (Geddes, 2022); rule 3 applies.
- Very high-volume ad groups (50,000+ clicks a month in Geddes' example): a single unpinned RSA can be run and read on its own; the second ad here is purely a test instrument (Geddes, 2022 strategy 2: your messages vs. the algorithm).
- Two RSAs that are reshuffles of each other: no messaging difference to learn from; the 2022 finding is about distinct ads (Vallaeys, 2021 builds them around different value propositions).
- Brand ad groups: the message is fixed; two near-identical brand RSAs only split impressions. Run one, partially pinned (skill 24), unless testing a brand CTA.
- Accounts where the second RSA was added to satisfy a Google recommendation or Ad Strength prompt: it will be filled to 15/4 and lift combinations past the data budget (skill 22); fix the asset count before judging the ad count.

## What to measure
RSA count distribution by ad group (zero/one/two/three-plus); impression share between sibling RSAs and their conversions per impression (the over-serving check); conversions per ad group before and after moving from one to two in ad groups above the floor; number of three-RSA ad groups past their test end date.

## Open disagreements in the canon
- One vs. two: Kristoffersen (2025, opinion) says one concentrates learning; Optmyzr (2022, data) and Vallaeys (2022) say two lifts conversion rate; Geddes (2022) uses two or three as test instruments. Epiminds goes with the data (two) and uses one only where volume forces it.
- Whether Google serves the better ad: Geddes (2022) shows it often does not; Google's framing assumes it does. Epiminds assumes it does not and checks monthly.
- Smart Bidding specifically: no source isolates it. Epiminds applies the rule regardless and will revise if a bid-strategy-segmented study appears.
