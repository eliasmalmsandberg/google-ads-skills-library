---
name: rlsa-layering-smart-bidding
id: 50
description: Decide for each remarketing list on a Search campaign under Smart Bidding whether it goes in observation, becomes a targeted ad group/campaign, or becomes an exclusion — and when a bid adjustment is still worth setting. Not for Display/Video remarketing, PMax signals, or list construction (skills 51, 54).
tags: Strategy / Search / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google documenting that Smart Bidding honours audience bid adjustments other than -100%; removal of observation mode from Search; conversion value rules extended to tCPA/Max Conversions; Google ending automatic use of first-party lists as Search signals.
---
## What this is
RLSA was a bid-adjustment technique. Under Smart Bidding the adjustments are mostly ignored (McNair, PPC Mastery, 2026), observed first-party lists are already bidding signals [Google docs], and since Q3 2023 Customer Match lists are used on Search whether or not you apply them [Google docs]. What remains is a three-way choice per list — observe, target, exclude — and a narrow set of cases where a bid adjustment or a value rule still carries information Google lacks. This skill makes that choice.

## Where it comes from
Miles McNair (PPC Mastery, 2026) on which adjustments survive Smart Bidding and on value-rule hierarchy and inflation; Navah Hopkins (Search Engine Land, 2023) on exclude-or-go-manual; ZATO (Vlietstra 2026 on value rules and exclusions; Williams 2026 on past converters); Andrea Cruz (Search Engine Land, 2022) as the pre-change position. Platform behaviour from Google Ads Help, labelled.

## When to use it / when not to
Use on any Search campaign on tCPA, tROAS, Max Conversions or Max Conversion Value that has remarketing, Customer Match or GA4 lists available, when someone proposes "+30% for pricing-page visitors".
Do not use under Manual CPC or Maximize Clicks: there, adjustments are honoured (McNair, PPC Mastery, 2026) and the baseline-style modifier approach is correct. Do not use for Display, Video or Demand Gen, where targeting and optimized targeting interact differently [Google docs].

## Inputs
1. Bid strategy per campaign.
2. Lists available: name, source (tag / GA4 / Customer Match), size, duration.
3. Audience report in observation, 90 days: impressions, cost, conversions, conversion value per list, per campaign.
4. Monthly conversions per campaign, and the account's agreed Smart Bidding conversion floor.
5. Whether the list's members should get a different message or landing page than everyone else.

## Method
1. **Put every list in observation on every Search campaign, once.** Observation does not restrict reach [Google docs] and is the only way to get per-list rows; Hopkins (Search Engine Land, 2023) frames its purpose as revealing composition so you can exclude. Observation cannot be added at ad-group creation [Google docs], so this is a post-launch step.
2. **Do not set positive bid adjustments on observed lists under Smart Bidding.** McNair (PPC Mastery, 2026): tCPA, tROAS, Max Conversions and Max Conversion Value mostly ignore them; Smart Bidding already weighs remarketing-list membership and conversion-path history at auction time [Google docs]. The +15% to +100% tables are a Manual CPC artefact. Remove existing ones so the UI stops implying they do something; the exception is a campaign on Maximize Clicks, which respects all adjustments (McNair, PPC Mastery, 2026).
3. **Exclude when the list should never see the campaign.** -100% is the one adjustment that works under every strategy (McNair, PPC Mastery, 2026, on device; applied here to audiences as a labelled analogy — use the exclusion control, not a -100% adjustment, for clarity). Vlietstra (ZATO, 2026): purchasers and form submitters out of acquisition; login-portal brand searchers out of brand; and when non-brand budget is tight, test excluding all past visitors from non-brand so the budget buys new people. Do not exclude past converters globally — Williams (ZATO, 2026) wants them in a deliberate segment of their own.
4. **Target (restrict) only when the message changes.** Targeting restricts reach [Google docs]; the justification is never "to bid more" (that is step 2's dead lever) but that list members need different copy, a different landing page, or broader keywords than cold traffic can afford. Build it as a separate ad group with the list in targeting, or a separate campaign when:
   - the targeted ad group would clear the account's Smart Bidding conversion floor on its own within a month (Epiminds operating threshold; no canon source states one), and
   - the main campaign excludes the same list, so the two do not compete.
   If it cannot clear the floor, keep it as an ad group in the main campaign so it shares the strategy's learning.
5. **Use a conversion value rule only for information Smart Bidding cannot infer.** Available only under Max Conversion Value and tROAS; one rule applies per conversion; audience hierarchy is Customer Match → your data → affinity/in-market → detailed demographics (McNair, PPC Mastery, 2026). Vlietstra (ZATO, 2026) gives the one legitimate RLSA-shaped use: multiply by <1 for conversions from users already in a remarketing list whose value you know is lower (e.g. repeat buyers on a new-customer campaign). McNair (PPC Mastery, 2026) advises against them in general because reported values inflate — a 50% rule on a €100 sale reports €150 — so document every rule next to the reporting it distorts.
6. **Re-read the observation rows quarterly, not weekly.** A list whose rows show conversion rate far above the campaign's is confirmation that Smart Bidding already bids it up, not a prompt to add an adjustment. The rows exist to find exclusion candidates (step 3) and message candidates (step 4).
7. **Check the PMax overlap.** Williams (ZATO, 2026) reports PMax absorbing standalone remarketing; if the same lists are PMax signals and the targeted RLSA ad group's volume fell as PMax grew, retire the ad group rather than defend it.

Output: per campaign, a list table with mode {observation, target: ad group/campaign, exclude}, the reason (message / exclusion / signal-only), any value rule with its multiplier and the reporting note, and the review date.

## What Google will tell you instead, and why we don't
Google's UI still offers bid adjustments on observed audiences under every strategy, and its help text says you can raise or lower bids for an observed group [Google docs]. We don't under Smart Bidding, because McNair (PPC Mastery, 2026) and Hopkins (Search Engine Land, 2023) both treat those adjustments as inert, and Google's own documentation says the lists are already signals [Google docs]. We also go against the common "move high performers to targeting after 30 days" advice in the baseline: targeting restricts reach [Google docs] and buys nothing a signal does not already give, unless the message changes.

## Failure modes
- Manual CPC / Maximize Clicks campaigns: step 2 is wrong there; adjustments work (McNair, PPC Mastery, 2026) and Cruz's bid-down-not-exclude rule (Search Engine Land, 2022) applies.
- Low-volume accounts: a targeted RLSA campaign below the conversion floor starves; keep it as an ad group.
- Brand campaigns with heavy existing-user traffic: excluding login-portal searchers (Vlietstra, ZATO, 2026) can expose brand terms to competitors when those users were the bulk of brand volume; watch brand impression share after the exclusion.
- Accounts on tCPA / Max Conversions that want value rules: unavailable [Google docs via McNair, 2026]; the only remaining lever is exclusion.
- iOS, non-signed-in and ads-personalization-opted-out users: exclusions may not apply [Google docs]; expect leakage in mobile-heavy consumer accounts.
- Accounts that already opted out of Customer Match auto-inclusion: lists only act as signals when applied; step 1 is mandatory there, not optional.

## What to measure
- Count of non-(-100%) audience bid adjustments on Smart Bidding campaigns (target zero).
- For every exclusion: list spend in the campaign after application (target zero) and brand impression share where brand is affected.
- For every targeted ad group/campaign: conversions per month against the floor; retire or merge under it.
- For every value rule: reported vs tracked conversion value delta, so the inflation McNair (PPC Mastery, 2026) describes is visible.
- Remarketing vs PMax spend and conversions quarter-on-quarter (step 7).

## Open disagreements in the canon
- Bid down vs exclude vs ignore: Cruz (2022) bids down, Hopkins (2023) excludes or goes manual, McNair (2026) says only -100% works. We follow McNair/Hopkins under Smart Bidding and Cruz under manual bidding; the platform change dates the disagreement.
- Value rules: Vlietstra (ZATO, 2026) "limited benefit, only for what Google can't infer" vs McNair (PPC Mastery, 2026) "generally advise against". We allow the single down-value case and nothing else.
- Past converters: Vlietstra (ZATO, 2026) excludes from acquisition; Williams (ZATO, 2026) keeps them as a strategy. We exclude from acquisition and target in a retention ad group — the same resolution as skill 51.
