# Dossier — 85 Hour-of-day / day-of-week heatmap analysis

## Sources

1. **Source**: Miles McNair, PPC Mastery newsletter TPE #145, "Why bid adjustments are dead and what to do instead" — https://www.ppcmastery.com/newsletter/tpe-145-why-bid-adjustments-are-dead-and-what-to-do-instead · **Tier** 1 · **Date** 2026-05-04 · **Claim**: "Google just ignores most of the bid adjustments you set" under Smart Bidding; the adjustment menus (device, schedule, location, audience) remain in the UI and look effective. Exceptions: Maximize Clicks honours all adjustments; Target CPA treats device adjustments as target adjustments; device −100% works as an exclusion under any Smart Bidding strategy. Under Manual CPC / Max Clicks, adjustments still apply and compound (+25% × +15% × +10%). Under tROAS / Max Conv Value, conversion value rules can adjust value by location/device/audience, one rule per conversion, and they inflate reported value — use sparingly. · **Evidence or opinion**: Practitioner position referencing Google's support table; no account data.

2. **Source**: Brad Geddes, Adalysis, "How audience bid adjustments work with Target CPA & Target ROAS" — https://adalysis.com/blog/how-audience-bid-adjustments-work-with-target-cpa-target-roas-bidding/ · **Tier** 1 · **Date** 2023-10-31 (test data Sept 2023; mod. 2026-04-28) · **Claim**: "Most bid adjustments aren't compatible with automated bidding"; under tCPA/tROAS only device and audience adjustments exist — ad-schedule adjustments are not available; device adjustments scale the target ($50 CPA × −50% mobile = $25 target); audience adjustments shift serving priority directionally. Test: positive adjustments raised impressions by less than the modifier; CPA changes within ±10% for audiences with ≥80 conv/30 days, none beyond 20%. A reader comment cites Google help: existing adjustments are not used with tROAS except device −100%. · **Evidence or opinion**: Single-account test with numbers.

3. **Source**: Brad Geddes, Adalysis, "How bid adjustments are used by bidding method" — https://adalysis.com/blog/how-bid-adjustments-are-used-by-bidding-method/ · **Tier** 1 · **Date** 2020-02-03 (mod. 2026-03-23) · **Claim**: Adjustments set under manual bidding persist and silently re-apply (or sit unused) after a bid-strategy switch; a +50% mobile adjustment becomes a +50% target adjustment under tCPA; audit all adjustments before and after any strategy change. · **Evidence or opinion**: Method; compatibility matrix is an image (not extracted).

4. **Source**: Google Ads Help, "About ad schedules" — https://support.google.com/google-ads/answer/2404248 · **Tier** Reference only · **Date** current · Default "All day"; schedules restrict serving to chosen days/hours; schedule bid adjustments exist; with a schedule, campaigns pace to 30.4× average daily budget per month regardless of scheduled days; not available for App campaigns; Smart Bidding interaction not covered on this page.

Not found: a canon page publishing a hour-of-week heatmap method or script (Brainlabs 24/7 bidding script, Mike Rhodes' heatmap script, Optmyzr hour-of-week) — URLs failed to resolve, Mike Rhodes' site blocks fetch, Brainlabs' tools page failed. Nils Rooijmans and Adalysis site searches returned nothing on dayparting. Google's Smart Bidding bid-adjustment compatibility page could not be fetched by guessed ID.

## Dissenting view
Geddes (2023) tests and recommends audience (and device) adjustments under tCPA/tROAS as directional levers; McNair (2026) says adjustments are dead under Smart Bidding apart from device −100%. Both agree ad-schedule adjustments do nothing under target/maximise strategies. The disagreement is whether the surviving device/audience adjustments are worth using (Geddes: yes, directionally; McNair: only −100% exclusions, fix the root cause instead). A reader comment on Geddes' post argues time of day is a signal Smart Bidding already uses and should be left alone.

## What the platform currently does [Google docs]
- Ad schedules restrict serving; schedule-level bid adjustments exist in the UI; monthly pacing = 30.4 × daily budget regardless of scheduled days [Google docs, answer 2404248].
- Smart Bidding compatibility (per practitioners citing Google's table, not fetched directly): Max Clicks honours all adjustments; tCPA uses device as a target adjustment; tROAS ignores all but device −100% (McNair, 2026; Geddes, 2023 comment citing Google help).
- Conversion value rules (location/device/audience) adjust value under tROAS / Max Conv Value (McNair, 2026).

## Baseline check
Read `google-ads-segmentation` and `google-ads-account-audit` (Layer 3c: ads outside business hours when calls are the conversion). Baseline treats hour/day as a bid-adjustment opportunity. This skill reverses that for Smart Bidding accounts: the heatmap's only legitimate outputs are schedule exclusions, budget-pacing checks, call-handling alignment and diagnosis — not bid adjustments — and it lists what still applies under Max Clicks / manual.

## Judgment calls
- No canon source publishes the heatmap *construction*; the skill describes the analysis at the level the canon supports (hour × day table of cost, conversions, CPA with a conversion floor per cell) and cites the conversion floor from Geddes' 80-conversion audience test as the only analogous practitioner threshold, labelled as borrowed.
- Took McNair's stricter position over Geddes' directional one for schedule adjustments (both agree on that case), and Geddes' for device/audience (he has test data).

## Canon strength: Adequate
Two Tier 1 practitioners with method; one single-account test; no cross-account evidence on dayparting.

## Invalidated by
Google re-enabling ad-schedule bid adjustments under Smart Bidding, changing the 30.4× pacing rule for scheduled campaigns, or removing ad schedules / −100% device adjustments.
