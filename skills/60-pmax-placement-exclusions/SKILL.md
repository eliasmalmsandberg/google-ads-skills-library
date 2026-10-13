---
name: pmax-placement-exclusions
id: 60
description: Monthly control of where Performance Max spends off-Search — reading the channel split, excluding placements by pattern at account level, and deciding what to do about Display, YouTube and app spend. Not for keyword negatives (skill 62) or brand lists (skill 55).
tags: Technique / PMax / Optimise / Any / Monthly
last_verified: 2026-10-13
invalidated_by: Campaign-level placement exclusions or channel-level budget/bid controls in PMax; cost appearing in the PMax placement report; a change to the account-level exclusion scope.
---
## What this is
PMax gives a placement report with impressions only, which Google says not to use for performance [Google docs], and — since June 2025 — a channel report with cost and conversions but no channel ROAS column and no channel controls (Williams/ZATO, 2025) [Google docs]. Placement exclusions apply only at account level (Rooijmans, 2024). This skill is the monthly routine that turns those three facts into exclusions and a channel decision.

## Where it comes from
Nils Rooijmans' three placement posts and exclusion-suggestion script (2024–25); Mike Rhodes' PMax Insights placements and channel tabs (2026); Optmyzr's channel data from 4,200 accounts (2026), its API-exclusion experiment (Bhandari, 2026) and the Pooler/Williams heuristics in its guide (2026); Navah Hopkins (2023) on forced video spend; Kirk Williams (2025) on reading the channel report.

## When to use it / when not to
Use monthly on every PMax campaign, and within a week of any asset addition (new video changes the channel mix). Do not use it to fence YouTube on ROAS alone when the account has real video creative and growing brand demand — Williams calls that usually the wrong reason (Williams in Optmyzr guide, 2026). Lead gen and e-commerce both apply; store-goal campaigns have different inventory and are out of scope.

## Inputs
- Placement report (`performance_max_placement_view`), 30 days, impressions per placement [Google docs].
- Rhodes' Placements tab, which attributes spend and defaults to placements above $0.10/day (Rhodes, 2026).
- Channel performance report, 30 days: cost, conversions, conversion value per channel, segmented by "ads using product data" and "ads using video" [Google docs].
- Existing account-level exclusion list and MCC lists.
- Whether the campaign has advertiser-supplied video (Assets tab shows yours vs auto-generated — Rhodes, 2026).

## Method
1. **Compute channel ROAS yourself.** Google reports channel volume, not ROAS/CPA (Baudisch/smec, 2026); divide value by cost per channel. Benchmarks from the 2025 peak: Search 732–768%, YouTube 555–626%, Discover 477–657%, Content 665–926%, Gmail 726–789%; YouTube took ~10% of impressions for ~2% of value (Optmyzr, 2026). Read YouTube "interactions" as not clicks (Williams/ZATO, 2025).
2. **Fence video when there is nothing to show.** If the campaign has no advertiser video and YouTube/Display "other" carries cost, Google is serving auto-generated creative; Hopkins' position is that YouTube spend without video assets is expensive waste (Hopkins/Optmyzr, 2023). Either supply video or go feed-only (skill 56). If advertiser video exists, do not cut on ROAS alone (Williams in Optmyzr guide, 2026); act only when channel ROAS has sat below half the Search channel for two consecutive months (dossier rule).
3. **Exclude all mobile app categories by default** at account level using Rooijmans' pasted list of ~140 app category placements (Rooijmans, 2025); his script flags every app placement as almost certainly low-value (Rooijmans, 2024). Keep apps only for an app-install or gaming advertiser.
4. **Pull placement suggestions weekly, by pattern.** Run the exclusion-suggestion script with a 7-day lookback (Rooijmans, 2024). Its flags: TLD outside .com/.edu/.org/.net/.nl/.be (add your market's TLDs); domains under 3 or over 25 characters, with hyphens, 3+ consecutive digits, repeated characters or punycode; scam/adult/clickbait words in the domain; YouTube videos with political or clickbait titles, "!!"/"??", heavy caps, currency amounts, made-for-kids, or a language outside your allowed list (Rooijmans, 2024). Exclude on patterns, not on impressions alone (Pooler in Optmyzr guide, 2026).
5. **Review spend, not impressions, for the rest.** Use Rhodes' $0.10/day floor to list placements worth a look (Rhodes, 2026); the native report has no cost [Google docs]. Any single placement above 15% of campaign spend is a flag (Pooler in Optmyzr guide, 2026) — exclude it unless it is a Google O&O surface, which cannot be excluded.
6. **Apply at account level**, via the UI or the API — Google support said API exclusions did not work for PMax; Optmyzr's experiment showed zero spend on API-excluded placements and Google later confirmed (Bhandari/Optmyzr, 2026). Use an MCC placement exclusion list for patterns shared across clients [Google docs]. Remember negatives never reach this inventory (Bhandari/Optmyzr, 2026).
7. **Set inventory type deliberately.** Google defaults to Maximum; use Moderate as the standard for brand-conscious clients and Limited only under a written brand-safety requirement [Google docs].
8. **Re-check in two weeks.** Allow 1–2 weeks for the channel mix to stabilise after changes [Google docs]; compare channel cost shares and the suggestions sheet. If exclusions keep growing without the Display/YouTube cost share falling, the problem is the asset set, not the placements — go to step 2.

## What Google will tell you instead, and why we don't
Google says the placement report "shouldn't be used to evaluate performance" and is a brand-safety tool, that a quiet channel means PMax prioritised better ones, and that the default inventory type is Maximum [Google docs]. We attach spend to placements through the script (Rhodes, 2026), compute channel ROAS ourselves (Baudisch/smec, 2026), exclude apps wholesale (Rooijmans, 2024, 2025) and fence video that has no creative behind it (Hopkins/Optmyzr, 2023) — because PMax maximises spend, not profit (Rooijmans, 2024), and the non-Search channels carry a fraction of the value they take in impressions (Optmyzr, 2026).

## Failure modes
- **App-install or gaming advertisers**: the app exclusion removes the audience.
- **Brands whose demand is video-created**: fencing YouTube on ROAS kills the upper funnel; Williams' warning applies (Williams in Optmyzr guide, 2026).
- **Multi-market accounts**: the script's TLD whitelist flags legitimate local domains; extend the list before running (Rooijmans, 2024).
- **Small accounts**: the 15% single-placement flag fires on noise; require the placement to persist across two months.
- **Expecting campaign-level control**: exclusions are account-wide and hit every PMax and Display campaign in the account (Rooijmans, 2024).
- **Reading YouTube interactions as clicks**: inflates perceived video engagement (Williams/ZATO, 2025).

## What to measure
Channel cost share and hand-computed ROAS per channel, monthly. Count of exclusions added per month and the impressions they carried. Share of spend on Google O&O vs third-party placements. Presence of auto-generated video assets. Single-placement spend concentration (max share).

## Open disagreements in the canon
Optmyzr (Bhandari, 2026; Williams quoted in its guide) says weak channel ROAS should prompt tests, not fencing; Hopkins (2023) and Rooijmans (2024) treat forced video and app inventory as waste to cut. Epiminds cuts apps by default and fences video only when there is no advertiser creative or a sustained two-month ROAS gap, because the channel data shows large value gaps but the incrementality of video is not measured by in-platform ROAS.
