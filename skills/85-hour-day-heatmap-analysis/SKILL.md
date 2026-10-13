---
name: hour-of-day-day-of-week-heatmap-analysis
id: 85
description: When an hour × day heatmap is still worth building under Smart Bidding, what it may be used to change (schedule exclusions, pacing, call handling, diagnosis) and what it may not (bid adjustments). Not for device or audience adjustments and not for manual-bidding dayparting schedules beyond the rules stated here.
tags: Technique / All / Optimise / Established / Monthly
last_verified: 2026-10-13
invalidated_by: Google re-enabling ad-schedule bid adjustments under Smart Bidding, changing the 30.4× pacing rule for scheduled campaigns, or removing ad schedules / −100% device adjustments.
---
## What this is
A monthly hour-of-week read of cost, conversions and CPA with a fixed set of permitted actions. Position: under tCPA, tROAS and Maximize Conversions, ad-schedule bid adjustments are not applied, so the heatmap is a diagnostic and an exclusion tool, not a bidding tool. Under Max Clicks and manual CPC it remains a bidding tool and the adjustments compound, so they are capped.

## Where it comes from
McNair's position that Smart Bidding ignores most bid adjustments, with the exceptions (Max Clicks honours all; tCPA treats device as a target adjustment; device −100% excludes under any strategy) and the compounding warning (McNair/PPC Mastery, 2026). Geddes' finding that under tCPA/tROAS only device and audience adjustments exist, with his Sept-2023 test showing CPA moves within ±10% at ≥80 conversions/30 days (Geddes/Adalysis, 2023), and his rule to audit adjustments before and after any strategy switch (Geddes/Adalysis, 2020). Schedule mechanics and the 30.4× monthly pacing rule from Google Ads Help, labelled.

## When to use it / when not to
Use monthly on campaigns where (a) a human has to answer — calls, chat, bookings — and ads run outside staffed hours; (b) the client suspects time-based waste; (c) a bid-strategy switch has just happened and legacy schedule adjustments may still be sitting in the account (Geddes/Adalysis, 2020); (d) the campaign is on Max Clicks or manual CPC.

Do not use it to set schedule bid adjustments on tCPA / tROAS / Maximize Conversions campaigns — they are not applied (Geddes/Adalysis, 2023; McNair/PPC Mastery, 2026). Do not build it on campaigns under ~80 conversions/30 days; cells will not clear the floor (borrowed from Geddes' audience-test floor; Geddes/Adalysis, 2023). Do not use for App campaigns (no ad schedules) [Google docs].

## Inputs
- 90-day campaign report segmented by hour of day and day of week: impressions, cost, conversions, conversion value (by conversion time where lag matters).
- Bid strategy per campaign and the list of existing ad-schedule, device, location and audience adjustments (Geddes/Adalysis, 2020).
- Staffed hours for any conversion that needs a human; lead-handling SLA.
- Daily budget and whether the campaign is budget-limited.
- Time zone of the account vs the customers.

## Method
1. **Audit before analysing.** List every bid adjustment on the campaign. If the strategy is tCPA / tROAS / Max Conv and schedule adjustments exist, they were inherited from an earlier strategy and do nothing — remove them so no one reads them as active (Geddes/Adalysis, 2020; McNair/PPC Mastery, 2026). If the strategy is Max Clicks or manual, note that device × schedule × location adjustments multiply (+25% × +15% × +10% stacks) (McNair/PPC Mastery, 2026).
2. **Build the 7 × 24 table** of cost, conversions, CPA (or ROAS) over 90 days. Mark any cell with fewer than ~10 conversions as unreadable and aggregate to day-part blocks (e.g. 6 four-hour blocks) until each block has ≥80 conversions — the floor Geddes used before trusting a CPA move under target bidding (Geddes/Adalysis, 2023). Read blocks, not cells.
3. **Identify exclusion candidates only.** A block qualifies for exclusion when all three hold: CPA ≥ 2× campaign CPA over the full 90 days; the block carries ≥10% of spend; and the cause is structural (no one answers the phone, store closed, B2B buyers absent at 03:00) rather than noise. Anything short of all three stays live — Smart Bidding already uses time of day as a signal and will bid down a weak block on its own, which is McNair's root-cause argument against patching with adjustments (McNair/PPC Mastery, 2026).
4. **Apply exclusions as schedule, not as −90%.** On Smart Bidding, a schedule bid adjustment of −90% is ignored; only the schedule itself (serving window) or a −100% device adjustment actually stops serving (McNair/PPC Mastery, 2026). Set the ad schedule to exclude the block.
5. **Re-check pacing after scheduling.** With a schedule, the campaign still paces to 30.4 × daily budget per month regardless of how many hours it runs [Google docs]; the removed hours' budget flows into the remaining hours. If the campaign was budget-limited, expect CPC to rise in the live hours; read the next 30 days' CPA before adding a second exclusion.
6. **Call-handling alignment.** Where the conversion is a call or a lead that must be worked within an SLA, compare the heatmap of conversions with staffed hours. If >20% of conversions land outside staffed hours, the fix is staffing or an after-hours flow first, exclusion second; a schedule that cuts those hours removes demand the heatmap says exists.
7. **Max Clicks / manual CPC only.** Schedule adjustments are honoured (McNair/PPC Mastery, 2026). Set them from the block CPA ratio (block CPA ÷ campaign CPA, inverted), cap any single adjustment at ±30%, and cap the stacked product of all adjustments on a cell at ±50% to avoid the compounding McNair warns about (McNair/PPC Mastery, 2026). Review monthly; remove them all before switching to a target strategy (Geddes/Adalysis, 2020).
8. **Diagnosis use.** A sudden shift in the heatmap's shape (conversions moving to new hours or days) with no schedule change is a change in demand, tracking (conversion-time vs click-time booking) or a competitor's budget cycle (see 83). Read it as a signal, not as something to adjust.

## What Google will tell you instead, and why we don't
- The UI still shows ad-schedule bid adjustments on every Search campaign, including those on tCPA/tROAS, and the Recommendations tab will not tell you they are ignored. Geddes' and McNair's reading of Google's own compatibility table is that under target bidding only device (as a target adjustment) and audience (as priority) exist, and under tROAS only device −100% (Geddes/Adalysis, 2023; McNair/PPC Mastery, 2026). We delete inherited schedule adjustments rather than leave them as decoration.
- Google's help example (a dog-sled business limiting ads to Tuesdays 8–11) [Google docs] encourages tight scheduling. Under Smart Bidding the bidder is already time-aware; we exclude only structural blocks (step 3), because a tight schedule concentrates 30.4× pacing into fewer hours and raises CPC [Google docs].
- Google's conversion value rules are offered as the Smart-Bidding-era replacement for adjustments. McNair's caution is that one rule applies per conversion and the reported value is inflated (McNair/PPC Mastery, 2026); we do not use value rules to encode time of day.

## Failure modes
- **Low-volume campaigns (<80 conv/30 days).** No block clears the floor (Geddes/Adalysis, 2023); the heatmap shows noise and someone schedules on it.
- **Long-lag conversions.** Click-date booking puts conversions in the hour of the click, not the sale; use by-conversion-time columns or the "bad" hours are simply the hours before the office opens.
- **Multi-time-zone targeting.** The account time zone is not the customer's; a national campaign's heatmap blends three or more local days.
- **Budget-limited campaigns.** Exclusions raise CPC in the remaining hours because pacing stays at 30.4× [Google docs]; the CPA gain evaporates.
- **E-commerce with 24-hour checkout.** Almost no block is structural; step 3's third condition is rarely met and exclusions just remove sales.
- **Accounts that switched strategies without an adjustment audit.** Legacy adjustments either sit unused or re-activate on a switch back to manual (Geddes/Adalysis, 2020).
- **Call-only / lead-gen with no after-hours flow.** The heatmap will show conversions at hours no one works; excluding them hides a staffing problem (step 6).

## What to measure
Monthly: block-level cost, conversions, CPA over rolling 90 days; share of conversions outside staffed hours; the list of active adjustments per campaign and strategy (Geddes/Adalysis, 2020); for any exclusion applied, campaign CPA and avg CPC in the live hours 30 days before vs after, with the pacing rule in mind [Google docs]. For Max Clicks/manual campaigns, the stacked adjustment product per cell against the ±50% cap (McNair/PPC Mastery, 2026).

## Open disagreements in the canon
- **Are surviving adjustments worth using?** Geddes tested device and audience adjustments under tCPA/tROAS and found directional impression effects with CPA within ±10%, and recommends them (Geddes/Adalysis, 2023). McNair treats everything except device −100% as dead and says fix the root cause (McNair/PPC Mastery, 2026). For *schedule* adjustments they agree: none apply under target bidding. Epiminds follows McNair for schedules (exclusion or nothing) and leaves device/audience adjustments to their own skills.
- **Heatmap construction.** No canon source publishes a heatmap method or a per-cell conversion floor; the 80-conversion block floor here is borrowed from Geddes' audience test (Geddes/Adalysis, 2023). The following are Epiminds operating thresholds — no canon source — stated so a reviewer can challenge them: the 2× CPA / 10% spend exclusion rule (reason: a block has to be both clearly worse and large enough to matter); the ~10-conversion per-cell unreadable mark in step 2 (reason: below ten, one conversion moves cell CPA by >10%); the >20% outside-staffed-hours trigger in step 6 (reason: at that share the staffing fix outweighs any schedule gain); and the ±30% single / ±50% stacked caps in step 7 (reason: McNair's compounding example reaches ~58% from three modest adjustments (McNair/PPC Mastery, 2026), and 50% is where a stacked bid stops resembling the campaign's CPA economics).
