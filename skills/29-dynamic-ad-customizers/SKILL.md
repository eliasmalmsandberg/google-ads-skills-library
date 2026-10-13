---
name: dynamic-ad-customizers
id: 29
description: When and how to use countdown, location insertion and business-data customizers in RSAs — syntax that matters, fallback safety, and the test that decides whether the dynamic line earns its place. Not for keyword-level price/variant copy (28) or promotion assets.
tags: Technique / Search / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: Changes to COUNTDOWN/LOCATION syntax or fallback behaviour; removal of business-data customizers; AI Max text customisation overriding advertiser customizer values.
---
## What this is
Rules for the three dynamic text sources — countdowns, location insertion, and business-data attributes — in RSAs. The platform makes them one brace away; the evidence says customised and location-specific text tends to buy impressions and lose conversions. So the skill gates each use, fixes the fallback so a broken value cannot serve, and runs the dynamic line as a labelled test against a hand-written control.

## Where it comes from
Brad Geddes / Adalysis (2026 pattern tests on location mentions and keyword insertion; 2022 testing method with H1 for location tests; 2022 creation series), Optmyzr 2022 study (customised text effect across 432,343 ads), Navah Hopkins / Optmyzr 2024 (concision). Syntax, precedence and fallback from the Google Ads API and Google Ads Help, labelled.

## When to use it / when not to
Use for a promotion with a hard end date, a multi-location business where the city name changes the decision, or a value held in business data that changes faster than you edit ads. Do not use location insertion in national campaigns to "feel local", countdowns on evergreen offers, or any of them in ad groups below the combination data budget (skill 22), where the effect cannot be read.

## Inputs
- Promotion end date and time, and the account time zone vs. the audience's time zones.
- Location targeting level that actually changes the offer (city, region, country).
- Business-data sheet with attribute names, types and a default per attribute.
- A hand-written control RSA and a label scheme (skill 22 rule 6).

## Method
1. **Gate each dynamic line on a decision it changes.** Countdown: only if the deadline is real and the offer ends. Location: only if the searcher's city changes what they get (a store, a delivery window, a local price); in Geddes' 2026 pattern test, ads *without* store-location mentions performed better (unequal test, to be rerun), so "local feel" is not a reason. Business data: only for a buying fact that updates faster than you can edit (skill 28's rule 1 applies).
2. **Countdown syntax and time zone.** `{COUNTDOWN(yyyy-MM-dd HH:mm:ss,daysBefore)}` counts in the account time zone; `{GLOBAL_COUNTDOWN(...)}` counts in the user's (Google Ads API docs). Epiminds default for any campaign serving more than one country is GLOBAL_COUNTDOWN, so a Helsinki searcher and a Stockholm searcher both see the deadline in their own clock. Set `daysBefore` to the length of the promotion, not longer: the countdown shows nothing before it (Google Ads API docs) and a "27 days left" headline is not urgency.
3. **Countdown placement.** It is a message, so it goes where Geddes (2022) puts price-vs-discount tests: H2, pinned with one or two non-countdown variants, so the line is seen (H1/H2/D1 are the always-shown slots per Google Ads Help) but not the only option in the slot (skill 24 rule 2). Never H3 or D2, which are not guaranteed to show.
4. **Location syntax and level.** `{LOCATION(City):Default}`; omitting the level uses the most specific available (Google Ads API docs). Always state the level explicitly and always give the default; a headline reading "Plumbers in " with nothing after it is the failure the default prevents. Keep the template short: city names are long and headlines under 20 characters had CPA $9.35 vs $18.27 (Vallaeys/Optmyzr, 2026) — "{LOCATION(City):Sweden} plumbers" not "Trusted local plumbers in {LOCATION(City):your area} today".
5. **Business data.** Attributes link at account, campaign, ad group and keyword level, most specific wins, 40 per account (Google Ads API docs). Build the default first (it must fit the character limit on its own, or the fallback cannot be used and the ad can be rejected — Google Ads API docs), then the values. Type price values with the currency symbol attached to the number (Google Ads API docs).
6. **Run it as a labelled pattern test.** Control: the hand-written RSA with the static equivalent ("Sale ends Sunday"; the city in the ad group name; the price typed). Variant: the same ad with the dynamic line. Same number of ad groups per version, brand excluded, judged on conversions or conversion value per impression (Geddes/Adalysis, 2026). The expected pattern is more impressions and fewer conversions per ad (Optmyzr, 2022) — more impressions is not the win.
7. **Decision.** Dynamic line wins on value per impression: keep, and add its data source to the monthly diff (skill 22). Loses or ties: revert to the static line; for deadlines, use the promotion asset instead and keep the headline short (Hopkins, 2024). Unequal test: rerun before concluding (Geddes, 2026).
8. **Kill switch.** Countdowns end themselves; location and business-data lines do not. Every dynamic RSA carries a label with its review date, and a promotion's static sibling lines ("Sale ends Sunday") are paused the same day the countdown expires.

## What Google will tell you instead, and why we don't
Google's docs and editor present countdowns and location insertion as ways to make ads more relevant and timely, and the customizer docs frame business data as tailoring every ad. We treat each as a hypothesis with a known downside: customised text raised impressions and lowered conversions per ad across 432,343 ads (Optmyzr, 2022), and the one location-mention test in the canon went against the location line (Geddes, 2026). The platform's account-time-zone default for COUNTDOWN is also wrong for multi-country accounts; we use GLOBAL_COUNTDOWN there.

## Failure modes
- Multi-country accounts on plain COUNTDOWN: the deadline is in the account time zone (Google Ads API docs); a midnight Stockholm end shows "0 days" an hour early in Helsinki.
- Location insertion with broad geo targeting: the inserted level falls back to whatever is available (Google Ads API docs), so a national campaign can serve "in Sweden" where the searcher expected a city, or a city where you have no presence.
- Missing or over-long defaults: the ad is rejected or the fallback never serves (Google Ads API RSA overview; customizer docs). This is a build-time check, not a runtime one.
- Low-volume ad groups and short promotions: a 5-day countdown in an ad group with a few hundred impressions a month produces no readable result (Geddes, 2022); run the promotion through the promotion asset and skip the test.
- Premium or quote-based B2B: urgency and price lines fight the "get a quote" message that won on value per impression in Geddes' 2026 example.
- AI Max text customisation on: Google-added assets are not listed with the ad's own (Google Ads API docs, 2026) and can carry their own urgency or location phrasing, contaminating the test.

## What to measure
Conversions and conversion value per impression, control vs dynamic set; impressions per ad (the expected but not decisive gain); share of impressions served with the default string (query the asset report); countdown ads still active after the end date (target zero); location-inserted values outside the service area (sample the served combinations).

## Open disagreements in the canon
- Geddes (2022) suggests H1 for location tests; his 2026 test found location mentions losing. Epiminds reads the 2026 result as the prior and the 2022 piece as the test design: location goes in only after it wins a labelled test.
- No canon source has published a countdown-specific result. Epiminds applies the general customised-text finding (Optmyzr, 2022) as the prior and tests per account; this is a judgment, and it is flagged as one.
