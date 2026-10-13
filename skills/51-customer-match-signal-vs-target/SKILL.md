---
name: customer-match-signal-vs-target
id: 51
description: Decide, list by list, whether a Customer Match list should be left as a Smart Bidding signal, applied as an exclusion, or applied as a target, and set the refresh cadence. Not for list-upload mechanics, consent/legal review, or PMax audience-signal composition.
tags: Strategy / All / Scale / Established / Monthly
last_verified: 2026-10-13
invalidated_by: Google removing the account-level "Use all Customer Match lists in Smart Bidding or Optimized Targeting" opt-out; changes to the 540-day membership cap or the 100-active-members eligibility rule; Customer Match becoming usable under manual bidding.
---
## What this is
A monthly decision procedure for accounts that already hold first-party lists. Since Q2 2022 (Search since Q3 2023, Shopping since Q1 2024) every Customer Match list in the account is a Smart Bidding signal whether or not you apply it [Google docs]. "Applying" a list therefore means one of two deliberate things: an exclusion, or a reach restriction. This skill decides which lists get which job and how often each is rebuilt.

## Where it comes from
Andrea Cruz (Search Engine Land, 2026) on first-party data outranking the query and on the B2B match-rate problem; Fred Vallaeys (Optmyzr PPC Town Hall, 2026) on the 90-day GCLID limit and the two-week proxy-signal rule; Navah Hopkins (Search Engine Land, 2022 and 2023) on match rates, CRM sync and the exclude-or-go-manual rule; Miles McNair (PPC Mastery, 2026) on bid adjustments being ignored under Smart Bidding; ZATO (Vlietstra 2026, Williams 2026) on which lists to exclude and when not to. Platform limits from Google Ads Help, labelled.

## When to use it / when not to
Use when the account runs Smart Bidding, holds at least one list with ≥100 members added or updated in the last 540 days (the eligibility floor [Google docs]), and someone is about to "add Customer Match to all campaigns in observation" or asks how often to re-upload.
Do not use under manual CPC or Maximize Clicks: Customer Match lists are not used by manual bidding at all [Google docs], so the only thing a list can do there is a bid adjustment or an exclusion. Do not use for PMax audience-signal design or for GA4-sourced audiences (skill 54).

## Inputs
1. Audience Manager export: every Customer Match list, its size, the date of last upload, and whether it is applied anywhere.
2. Account setting: is "Use all Customer Match lists in Smart Bidding or Optimized Targeting" checked? [Google docs]
3. Match rate per list from Audience Manager.
4. Sales-cycle length and whether offline conversions are imported.
5. Which campaigns are acquisition-only (new-customer goal or explicit "no existing customers").

## Method
1. **Confirm the signal is on.** If the account-level checkbox is unchecked, Smart Bidding ignores every unapplied list. Re-check it unless the account has a documented reason to opt out (the opt-out is per account and cannot be set at MCC level [Google docs]). Finn's reporting of the 2022 change (Search Engine Land, 2022) still holds: review this per account, because nobody did it for you.
2. **Default every list to "signal only".** Do not apply lists "in observation" to Smart Bidding campaigns. Hopkins (Search Engine Land, 2023): the audiences are already inside the bidding; the practitioner's remaining jobs are exclusion, or manual bidding with adjustments — not both. McNair (PPC Mastery, 2026): under tCPA, tROAS, Max Conversions and Max Conversion Value the adjustments you would set on an observed list are mostly ignored. An observed list on Smart Bidding is a report row and nothing else.
3. **Promote a list to exclusion when it describes people you pay to reach but never want to pay for.** Apply as campaign-level exclusion (Vlietstra, ZATO, 2026): purchasers and lead-form submitters from acquisition campaigns; current top-tier subscribers from upsell campaigns; existing users who search brand to reach a login page, from brand and Shopping campaigns. Exclusions work in Search, Display, Shopping and PMax (Vlietstra, ZATO, 2026; [Google docs]) and optimized targeting respects them [Google docs]. Do not blanket-exclude past converters everywhere: Williams (ZATO, 2026) argues they deserve a separately-messaged campaign, not a global block. Rule: exclude from acquisition, target separately for retention.
4. **Promote a list to target only when the whole campaign exists for that list.** Win-back, upsell, renewal or churn-risk campaigns where the message is wrong for anyone off-list. Targeting restricts reach [Google docs], so a targeted list must be large enough to spend the budget; if the list is near the 100-active-member floor it will stop serving when memberships age out [Google docs].
5. **Fix the match rate before judging the list.** Google reports most advertisers at 29–62% [Google docs]; Hopkins (Search Engine Land, 2022) reaches "closer to 70%" by syncing from the CRM with every identifier, not email alone. For B2B, Cruz (Search Engine Land, 2026) calls match rates "notoriously stubborn" and recommends enrichment via integration partners and clustering contacts by shared pain point. A list under 30% matched is a data-quality ticket, not an audience.
6. **Set the refresh cadence from the data path, not the calendar.**
   - CRM or Data Manager sync: append at least daily [Google docs]; Google now recommends Data Manager / Data Manager API over the Ads API for new integrations [Google docs].
   - Manual upload: weekly, same day and time [Google docs]. Hopkins (Search Engine Land, 2022) rules out downloaded CSVs on personal machines; if you must download, use MFA and delete after upload.
   - Long sales cycles: Vallaeys (Optmyzr, 2026) notes GCLID offline import only reaches back ~90 days from the click, so feed a proxy signal (qualified lead, scored engagement) within two weeks rather than waiting for the close. Same for lists: a "closed-won" list on a 24-month cycle refreshes too slowly to be a signal; build the list from the proxy stage.
7. **Run the 540-day audit monthly.** Memberships expire at 540 days and a list goes ineligible with fewer than 100 members added or updated in that window [Google docs]; enforced from 7 April 2025 (Adegbola, Search Engine Land, 2025). Any list not uploaded in 60 days — eight missed weekly uploads against Google's weekly manual-upload guidance [Google docs] (Epiminds operating threshold — no canon source; reason: long enough to be a broken pipeline rather than a holiday, far enough from the 540-day cap to fix) — goes on the "refresh or delete" row; a list you cannot refresh is removed so it stops polluting the signal pool.
8. **Do not use conversion value rules as a substitute for list bid adjustments.** McNair (PPC Mastery, 2026) advises against them because reported values inflate (a 50% rule on a €100 sale reports €150); Vlietstra (ZATO, 2026) limits them to information Smart Bidding cannot already see. A Customer Match membership is exactly what it already sees.

Output: a table of lists with one of {signal, exclude from <campaigns>, target in <campaign>, refresh-or-delete}, match rate, last upload, cadence, owner.

## What Google will tell you instead, and why we don't
Google's UI nudges you to add lists to campaigns in observation. We don't, because Google's own docs say unapplied lists are already used by Smart Bidding and McNair (PPC Mastery, 2026) says the resulting bid adjustments are mostly ignored. The second nudge is conversion-based customer lists plus enhanced conversions for "real-time" refresh [Google docs]; take it, but Cruz (Search Engine Land, 2026) is the reason to also feed mid-funnel proxies — Google's real-time list only holds people who already converted.

## Failure modes
- Manual CPC or Maximize Clicks accounts: lists are not used by bidding [Google docs]; the "signal" premise is false there.
- Lists near 100 active members, small B2B lists, wealth-management-sized volumes (Vallaeys, Optmyzr, 2026): too small to target, too noisy to matter as a signal; exclusions only.
- EEA/UK/Switzerland accounts: since March 2024 lists do not serve on partner inventory or third-party exchanges [Google docs]; a targeted list reaches owned-and-operated inventory only.
- iOS 14+ mobile web Safari traffic: segments, including exclusions, may not apply to non-signed-in users [Google docs].
- Accounts opted out of auto-inclusion: step 2 inverts — nothing is a signal unless applied.
- Retention businesses: blanket purchaser exclusions remove the best buyers; Williams (ZATO, 2026) is the dissent to apply.

## What to measure
- Match rate per list monthly; alarm under 30% (floor of Google's 29–62% range) and target 70% (Hopkins, Search Engine Land, 2022).
- Days since last upload per list; alarm at 60 days, the step 7 threshold (Epiminds operating threshold — no canon source), against the 540-day cap [Google docs].
- Share of acquisition-campaign conversions from excluded lists after exclusion is applied (should go to ~0; if not, the exclusion is not applied at campaign level).
- For targeted lists: impression share lost to budget vs list size, to catch the serving stop at the 100-member floor.

## Open disagreements in the canon
- Exclude past customers vs target them separately: Vlietstra (ZATO, 2026) vs Williams (ZATO, 2026). We do both: exclude from acquisition, target in retention. Never signal-only in acquisition — that pays to re-reach buyers.
- Value rules on audiences: McNair (PPC Mastery, 2026) generally no; Vlietstra (ZATO, 2026) only for information Google lacks. We follow McNair for Customer Match, since the list is already in the bidding.
- Match-rate benchmark: Google's 29–62% [Google docs] vs Hopkins' ~70% (2022) vs Cruz's "stubborn" B2B (2026). 70% is the B2C ceiling with full identifiers; lower is accepted for B2B; sub-30% is broken.
