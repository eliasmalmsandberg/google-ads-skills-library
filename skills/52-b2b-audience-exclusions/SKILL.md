---
name: b2b-audience-exclusions
id: 52
description: Find and apply audience, demographic and household-income exclusions when a B2B account is paying for consumer traffic. Not for negative keywords, geo exclusions, or PMax placement exclusions.
tags: Technique / All / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google adding parental status, life events or custom segments to Search; HHI becoming available in European markets; Smart Bidding honouring non-(-100%) audience bid adjustments; demographics gaining an observation setting.
---
## What this is
A procedure for turning "the sales team says the leads are consumers" into a short list of exclusions that actually change delivery. Under Smart Bidding the only audience lever that still works is -100% (McNair, PPC Mastery, 2026), so the whole skill is about choosing which segments earn that, with what evidence, and without the two traps that make B2B exclusions backfire: excluding "Unknown" and assuming HHI exists in your market.
See also: skill 50 (rlsa-layering-smart-bidding) — the observe/target/exclude rule for remarketing lists and the dead bid-adjustment lever.
See also: skill 51 (customer-match-signal-vs-target) — first-party Customer Match lists as exclusions and the match-rate fix.

## Where it comes from
Andrea Cruz (Search Engine Land, 2022 and 2026) on finding real segments from cross-channel GA data instead of Google's suggestions and on negative intent themes; Navah Hopkins (Search Engine Land, 2023) on observation-then-exclude; Miles McNair (PPC Mastery, 2026) on bid adjustments being ignored under Smart Bidding; ZATO (Vlietstra, 2026) on first-party exclusion candidates. Platform availability from Google Ads Help, labelled.

## When to use it / when not to
Use when a B2B account shows one of: lead-quality complaints with a consumer pattern (personal email domains, students, job seekers), a brand or Shopping campaign being clicked by existing users heading for a login page (Vlietstra, ZATO, 2026), or in-market/affinity observation rows spending with zero qualified leads.
Do not use for low-volume accounts where the observation rows cannot reach the threshold in step 4 within 60 days (Epiminds operating threshold — no canon source; reason: two monthly reviews with no row clearing 3× cost per qualified lead); do not use as a substitute for fixing the form or the offer — Cruz (Search Engine Land, 2026) and McNair (PPC Mastery, 2026) both say fix the cause and treat the exclusion as temporary.

## Inputs
1. Audience report, segmented by in-market, affinity, detailed demographics and your-data, 90 days, per campaign, with cost, conversions and (if imported) qualified-lead conversions.
2. Demographics report (age, gender, HHI where available), same window.
3. GA4 (or GA) demographics and interests report across all channels, not only paid (Cruz, Search Engine Land, 2022).
4. CRM lead-quality export joined by GCLID, or at minimum a disqualification reason per lead.
5. Target CPA / cost per qualified lead for the campaign.
6. Country list of each campaign — HHI exists in only 20 countries, none in Europe [Google docs].

## Method
1. **Establish the bidding model first.** Under tCPA, tROAS, Max Conversions or Max Conversion Value, positive and negative audience bid adjustments are mostly ignored; -100% works (McNair, PPC Mastery, 2026). So every candidate below is binary: exclude or leave. Under Manual CPC or Maximize Clicks, Cruz's 2022 rule applies instead — lower bids on weak segments, raise on strong ones, exclude nothing yet.
2. **Make sure the rows exist.** Demographics are targeted by default and only have a targeting setting [Google docs]; audience segments show in observation only once added, and exclusions cannot be added at campaign creation [Google docs]. Add the in-market and affinity segments you suspect, in observation, and wait for data. Hopkins (Search Engine Land, 2023): observation's job is to reveal composition so you can exclude, then let Smart Bidding run.
3. **Source candidates from outside Google's suggestions.** Google's in-market suggestions for B2B are frequently irrelevant — Cruz (Search Engine Land, 2022) cites an advocacy-software client whose top suggestion was aftermarket auto parts. Use the GA interests report, which spans all channels, to find segments that over- or under-index on qualified conversions, and bring those into Google Ads observation.
4. **Exclude a Google audience segment when all three hold** (Epiminds operating threshold; no canon source publishes a number):
   - 90-day spend on the segment ≥ 3× the campaign's cost per qualified lead;
   - zero qualified leads (or, without CRM data, zero conversions) in the window;
   - the segment is consumer-shaped on its face (e.g. in-market for consumer electronics, affinity for gaming) rather than merely under-performing. Under-performing but plausible segments stay, because Smart Bidding already weighs them (McNair, PPC Mastery, 2026).
5. **Demographic exclusions on Search are limited to age, gender and HHI** [Google docs]. Age: exclude 18–24 only when the CRM disqualification reasons show students or juniors as a named pattern, and never exclude "Unknown" — it is on by default, is the largest bucket, and Google's own warning is that excluding it blocks people you want [Google docs]; for B2B, work-profile users are heavily "Unknown". Gender: no B2B case. HHI: only usable in the 20 listed countries (US, CA, AU, IN, JP, BR, MX, SG and others) [Google docs]; for Nordic and EU campaigns the control does not exist on Search, so an "exclude lower 50% HHI" recommendation is not implementable — say so rather than leaving a ghost task. If HHI appears in your PMax settings (seen in a European campaign in July 2026 per Search Engine Land reporting), treat it as a rollout test, not a dependable control.
6. **Apply first-party exclusions regardless of performance data** (Vlietstra, ZATO, 2026): existing customers and lead-form submitters from acquisition campaigns; employees; churned users where the CRM tags them; login-portal brand searchers from brand and Shopping. These are campaign-level exclusions. Optimized targeting respects customer-data exclusions [Google docs].
7. **Pair every exclusion with an intent negative.** Cruz (Search Engine Land, 2026) manages "negative intent themes" rather than individual search terms; a consumer-shaped audience usually arrives through consumer-shaped queries (free, salary, jobs, DIY). Exclusion without the negatives moves the consumer traffic to another segment.
8. **Review at 30 and 90 days** (Epiminds operating cadence — no canon source; reason: 30 days to catch volume loss, 90 days to match the observation window in Inputs). Exclusions may not apply to users opted out of ads personalization [Google docs], so expect leakage. If qualified-lead share did not improve by the 90-day review, the consumer traffic was not audience-shaped; remove the exclusion and look at the offer, the form and the landing page (McNair, PPC Mastery, 2026; Cruz, Search Engine Land, 2026).

Output: an exclusion sheet per campaign — segment, level (campaign/ad group), evidence (spend, qualified leads, CRM pattern), paired negatives, review date — plus a "not implementable in this market" line for HHI where applicable.

## What Google will tell you instead, and why we don't
Google's audience UI offers bid adjustments on observed segments as the primary control and keeps "Unknown" selected with a warning. We ignore the bid adjustments because McNair (PPC Mastery, 2026) and Hopkins (Search Engine Land, 2023) both treat them as dead under Smart Bidding; we agree with Google on "Unknown" and say so, because excluding it is the most common way a B2B exclusion pass halves volume without raising quality. Google's in-market suggestions are not a candidate source (Cruz, Search Engine Land, 2022).

## Failure modes
- Low-volume B2B accounts (under ~20 qualified leads a quarter — Epiminds operating threshold, no canon source; reason: below this no single segment can show 3× cost per qualified lead with zero leads in 90 days): no segment reaches the threshold in step 4; exclusions become guesses.
- Accounts on Manual CPC: step 1 inverts; bid-downs are the tool, not exclusions.
- European accounts asked for HHI exclusions: the control is absent on Search [Google docs].
- Products with a prosumer or SMB-owner buyer: "consumer-shaped" in-market segments (home office, small business software) are the buyer; step 4's third test fails and the exclusion cuts pipeline.
- PMax-heavy accounts: audience exclusions exist [Google docs] but the asset-group signal does most of the work; excluding here without also fixing conversion signals (Cruz, Search Engine Land, 2026) changes little.
- iOS mobile web, non-signed-in users: segment exclusions may not apply [Google docs]; expect leakage in mobile-heavy accounts.

## What to measure
- Qualified-lead share (CRM) per campaign before and 90 days after the exclusion set.
- Spend on excluded segments after application (should be zero at campaign level; if not, the exclusion sits at the wrong level).
- Volume: impressions and conversions week-on-week; a drop over ~20% (Epiminds operating threshold — no canon source; reason: beyond normal week-on-week noise in a B2B account) with no quality gain means a segment that mattered was removed — the "Unknown" or prosumer traps above.
- Share of leads from personal email domains, as the proxy when the CRM has no quality stage.

## Open disagreements in the canon
- Bid down vs exclude: Cruz (2022) vs McNair (2026). We follow McNair under Smart Bidding and Cruz under manual bidding; the platform changed in between.
- Observe-before-exclude (Hopkins, 2023; Google docs) vs apply first-party exclusions immediately (Vlietstra, 2026). We apply first-party exclusions immediately and observe only Google-defined segments; your own customers never need a test to prove they should not be in acquisition.
- Whether audience exclusions matter at all once CRM-qualified conversions are imported (Cruz, 2026 implies the signal does the work): we keep them as a cost control, since Google still charges for the click that teaches the model.
