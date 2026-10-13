---
name: offline-conversion-import-lead-stages
id: 48
description: Use when a B2B or long-cycle lead-gen account wants Smart Bidding to optimise to SQL or closed-won from the CRM rather than form fills. Not for the one-off CSV upload mechanics (baseline covers that), not for accounts where the qualified stage won't reach ~45 a month, and not a substitute for proxy values on the early stages (skill 42).
tags: Technique / All / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: Google changing the GCLID upload/restatement windows, the 90-day click window, Data Manager source cadences, or deprecating classic offline conversion import in favour of enhanced conversions for leads only.
---
## What this is
The decision of *which* CRM stage to make the primary conversion, how to stage the import so the bidder isn't triple-counting one journey, and how fast the signal has to come back to be worth bidding on. The mechanics (GCLID, hashed email, Data Manager) are the easy part. Projects fail on plumbing and timing: CRMs with no open API, feeds that stop silently after the June 2026 API migration, and stages that arrive too late to be inside the click window (Vallaeys/Optmyzr, 2026; Newson/Vallaeys, 2026).
See also: skill 43 (micro-conversion-ladder) — the shallow end of the ladder and Max Clicks before any rung qualifies.
See also: skill 42 (value-based-bidding-lead-gen) — proxy values for the early stages that the CRM cannot supply.

## Where it comes from
Gray/WebMechanix (2024, added Tier 2) supplies the stage ladder and the 45-in-30-days-inside-the-window rule. Vallaeys (Optmyzr 2026; SEL 2026; Town Hall 2026) supplies the lag, cadence and failure patterns. Cruz (SEL 2026) and Hopkins (SEL 2026) set the "source of truth first, verify it flows back" bar.

## When to use it / when not to
Use when: the client has a CRM with stage definitions that sales actually maintains; the qualified stage (SQL or equivalent) happens ≥45 times in 30 days at the level the bid strategy sits (Gray/WebMechanix, 2024); and median time from click to that stage is comfortably under 90 days (Gray/WebMechanix, 2024). Don't use as the primary signal when the cycle is 6–24 months — GCLID import "doesn't go that far back" and a signal that arrives at 90 days barely steers bidding (Newson/Vallaeys, 2026); import it as secondary for reporting and bid on an earlier stage. Don't use for a few-hundred-account ABM programme — manual control beats any imported signal at that volume (Cruz/SEL, 2026).

## Inputs
- Stage definitions and monthly counts: form → qualified form → MQL → SQL → opportunity → closed-won
- Median and 90th-percentile days from click to each stage
- CRM type and API access (Salesforce with or without API, HubSpot, other)
- Current import source and cadence (Data Manager source type, or legacy)
- GCLID capture coverage: share of CRM leads with a stored, case-correct GCLID; share with email/phone

## Method
1. **Fix the capture first.** Auto-tagging on; GCLID captured on every page and stored case-sensitively with the lead (Google Ads Help, 2026). Measure the share of CRM leads with a GCLID; where it is low (consent, stripped parameters), run enhanced conversions for leads in parallel so hashed email/phone can match when the click ID is missing (Vallaeys/SEL, 2026). EC-for-leads changes matching, not which stage you bid on.
2. **Choose the primary stage by two conditions**: (a) ≥45 conversions in the last 30 days at the bid-strategy level, (b) median click-to-stage well inside 90 days (Gray/WebMechanix, 2024). For most B2B accounts that is SQL or "qualified lead", not closed-won. Form fill stays primary until the qualified stage clears 45 — an agency that optimised only to MQLs and ignored form-fill rate ended up with a volume complaint (Gray/WebMechanix, 2024).
3. **Import every deeper stage as secondary first**, with its value, for at least one cycle before promoting it; otherwise one journey counts as three conversions (Gray/WebMechanix, 2024; Vallaeys/Optmyzr, 2026). Only one stage is primary per journey.
4. **Set the feedback cadence to beat two weeks.** Vallaeys' rule: a signal returned within ~2 weeks steers bidding; one returned at 90 days is usually too late (Newson/Vallaeys, 2026). Data Manager cadences differ by source: Salesforce/HubSpot connectors import the last 14 days on first run then deltas; cloud storage/SFTP/Sheets re-import 90 days each run; warehouses import the last 14 days each run (Google Ads Help, 2026). Pick the source whose cadence you can run daily.
5. **If the CRM has no API** (common with Salesforce tiers), use a HubSpot two-way sync on the handful of fields needed, or have sales log stage changes in a second system that can export (Newson/Vallaeys, 2026). Don't wait for the enterprise CRM project.
6. **Monitor the feed as a conversion action**, not a data task: check conversion-goal diagnostics and confirm stage updates are actually arriving (Hopkins/SEL, 2026). The June 2026 move to the Data Manager API can stop legacy pipelines silently (Vallaeys/Optmyzr, 2026). Alert on zero imports for 2 days and on GCLID-match rate dropping >20% week on week — Epiminds operating thresholds, no canon source; reason: a daily-run pipeline that misses two consecutive runs is broken, not late, and a one-fifth match-rate fall exceeds normal weekly variation in the accounts we run.
7. **Judge on matured data only.** Imported conversions show in reporting before they are fully weighted in optimisation (Vallaeys/SEL, 2026), and lag misattributes results to the wrong day (Vallaeys/Optmyzr, 2026). Read performance by click date with the lag window excluded (skill 49), and give any stage promotion ≥3 conversion cycles before changing again (Vallaeys/Optmyzr, 2026).
8. **Consolidate campaigns before promoting a deep stage.** Fragmented campaigns leave late stages with insufficient signal per campaign (Vallaeys/Optmyzr, 2026).

## What Google will tell you instead, and why we don't
Google recommends enhanced conversions for leads over classic import for new setups, on easier setup and cross-device/engaged-view matching (Google Ads Help, 2026), and its onboarding flow nudges you to import closed-won with revenue as the primary conversion. We treat EC-for-leads as an identifier fallback, not the project — the binding constraints are CRM access, cadence and stage timing (Newson/Vallaeys, 2026; Vallaeys/Optmyzr, 2026). And we rarely make closed-won primary: it almost never clears 45 in 30 days inside the window; SQL does (Gray/WebMechanix, 2024).

## Failure modes
- **Cycles over ~90 days** (enterprise SaaS, wealth management): the stage you want is outside the window; GCLIDs expire 90 days after the click (Vallaeys/Newson, 2026) and a conversion's value can be restated for 55 days after it is first recorded (Vallaeys/Optmyzr, 2021). Bid on the earlier stage.
- **Small lists / tiny TAM**: wealth-management-sized lists never reach platform volumes (Newson/Vallaeys, 2026).
- **Sales teams that don't maintain stages**: stale CRM values feed stale bids (Vallaeys/Optmyzr, 2026).
- **Phone-heavy lead gen** with call-tracking label mismatches: attribution confusion on exactly the leads you want (Hopkins/SEL, 2026).
- **Consent-heavy markets** where a large share of leads carry no GCLID: without EC-for-leads the imported sample is biased toward consenting users.
- **Multiple primaries**: triple-counting inflates the apparent CPA improvement after launch (Gray/WebMechanix, 2024).

## What to measure
Weekly: imports per stage, GCLID/email match rate, days-from-click per stage (median, p90), zero-import days. Monthly: primary-stage count vs the 45 threshold; promotion candidates; CPA per stage by click date, matured. After any Google API or Data Manager change, and at least quarterly (Epiminds operating cadence, no canon source; reason: the June 2026 migration showed pipelines fail silently — Vallaeys/Optmyzr, 2026): re-verify the pipeline end to end.

## Open disagreements in the canon
- **Primary stage: SQL vs closed-won.** Google's framing and many agencies push closed-won with revenue; Gray's volume-and-window rule usually lands on SQL. Epiminds: SQL primary, closed-won secondary with value, revisit when closed-won clears 45/30 days.
- **GCLID vs EC-for-leads.** Google prefers EC-for-leads; Vallaeys frames it as the fallback for missing click IDs. We run both from day one and judge by match rate.
- **How fast is fast enough.** Vallaeys says ~2 weeks; the Data Manager connectors run on 14-day lookbacks, which is compatible only if the job runs daily. We require a daily run.
