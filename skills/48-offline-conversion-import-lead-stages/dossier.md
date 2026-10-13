# Dossier — 48 Offline conversion import with lead stages

## Sources

1. **Source**: Will Gray, WebMechanix, published on Optmyzr — "How to make value-based bidding work for you", https://www.optmyzr.com/blog/make-value-based-bidding-work-for-you/ · **Tier** added-Tier-2 for this topic (see dossier 43) · **Date** 2024-12-10 · **Claim**: Stage ladder: form fill (pixel) → qualified form fill (pixel) → MQL (CRM import) → SQL (CRM import) → closed (CRM import). Optimise to the deepest stage with ~45 conversions in the last 30 days at the bid-strategy level *and* a time-to-stage inside Google's 90-day click window. Import new stages as secondary first to avoid triple-counting one journey. A prior agency that optimised only to MQLs and ignored form-fill rate created a volume complaint. · **Evidence**: agency practice; no sample size.

2. **Source**: Frederick Vallaeys, Optmyzr — "Value-based bidding guide", https://optmyzr.com/blog/value-based-bidding-guide · **Tier** 1 · **Date** 2026-07-16 · **Claim**: Stale CRM values and unmonitored offline-import feeds are the common breakages; offline import migrated to the Data Manager API from 2026-06-15 and legacy pipelines can stop silently; reported GCLID windows 90 days to upload, 55 days to restate (verify). Conversion lag misattributes results to the wrong day. Fragmented campaigns leave late-stage conversions with insufficient signal. Testing needs ≥3 conversion cycles. · **Evidence**: method, Google docs, support patterns.

3. **Source**: Frederick Vallaeys, Search Engine Land — "Why PPC measurement feels broken (and why it isn't)", https://searchengineland.com/ppc-measurement-broken-468574 · **Tier** 1 · **Date** 2026-02-10 · **Claim**: Imported or modelled conversions can appear in reporting before they are fully weighted in optimisation — bidding systems validate new signals over time. Offline imports are server-to-server and less affected by browser privacy loss; they reduce dependence on pixels, don't replace them. Enhanced conversions (hashed email) match conversions when click IDs are missing. · **Evidence**: experience; no numbers.

4. **Source**: Fred Vallaeys & David Newson, Optmyzr PPC Town Hall — https://www.optmyzr.com/ppctownhall/optimize-ppc-long-sales-cycles · **Tier** 1 host · **Date** 2026-08-12 · **Claim**: GCLID import "doesn't go that far back" — a 24-month cycle can't be closed-loop reported; a signal fed back within ~2 weeks steers bidding, waiting 90 days is usually wrong; many Salesforce clients have no open API, so agencies use HubSpot two-way sync on selected fields or a second logging system; wealth-management lists are too small to reach platform volumes. · **Evidence**: practitioner anecdote.

5. **Source**: Andrea Cruz, Search Engine Land — "Why Performance Max looks different for B2B in 2026", https://searchengineland.com/why-performance-max-looks-different-for-b2b-in-2026-467876 · **Tier** 1 · **Date** 2026-01 · **Claim**: First requirement is importing the source of truth from Salesforce/CRM; a bare form fill with no qualification leaves the bidder unable to define success; qualified downstream signals are the foundation; account-based programs with a few hundred named accounts are better on manual control. · **Evidence**: 15 years' practice; no data.

6. **Source**: Navah Hopkins, Search Engine Land — "5 priorities for lead gen in AI-driven advertising", https://searchengineland.com/lead-gen-ai-driven-advertising-priorities-473660 · **Tier** 1 · **Date** 2026-04-07 · **Claim**: Validate that lead status updates and downstream signals are *actually flowing back*; review conversion goal diagnostics regularly; call-tracking label mismatches confuse phone-lead attribution. · **Evidence**: qualitative.

7. **Source**: Harrison Carroll / Nils Rooijmans — not used here (see dossiers 40, 42).

## Dissenting view
Google (Help 7012522) now recommends enhanced conversions for leads *over* GCLID import for new adopters. Vallaeys (2026) treats EC-for-leads as the fallback when click IDs are missing, and Newson/Vallaeys (2026) point out the real constraint is the CRM's API and the lag, not the identifier. The disagreement is about where the project fails: Google frames it as matching (identifier), the practitioners frame it as plumbing (CRM access, cadence, stage definitions) and timing (which stage arrives fast enough to bid on).

## What the platform currently does [Google docs]
- [Google docs] Offline conversion import needs auto-tagging, GCLID captured on every page and stored case-sensitively with the lead (support.google.com/google-ads/answer/7012522, fetched 2026-10-13).
- [Google docs] Data Manager import timing: cloud storage/SFTP/Sheets sources re-import the last 90 days each run; Salesforce and HubSpot import the last 14 days on first run then deltas; warehouses (BigQuery, Snowflake, MySQL, etc.) import the last 14 days each run (answer/7012522).
- [Google docs] Enhanced conversions for leads pairs SHA-256 hashed, normalised first-party data (email, phone in E.164) with imported offline conversions and matches to signed-in Google users; Google recommends it over classic OCI for new setups, citing easier setup, engaged-view and cross-device conversions (answer/7012522, answer/9888656).
- [Google docs via Vallaeys 2026] Offline upload moved to the Data Manager API from 2026-06-15; GCLID upload window 90 days, restatement window 55 days (to verify).
- [Google docs via Gray 2024] Maximum click-through conversion window is 90 days.

## Baseline check
Read `google-ads-conversion-tracking` (offline import section: GCLID capture snippet, CSV format) and `google-ads-attribution` (click windows). Baseline covers the mechanics of one upload. This skill adds: which stage to make primary and the 45/30-day + inside-the-window rule, secondary-first staging, the ~2-week feedback target, the Data Manager source cadences and the June 2026 API migration as a silent-failure risk, the CRM-access workarounds, and the measurement rule that imported conversions are reported before they are weighted.

## Judgment calls
- Treated EC-for-leads as a parallel identifier path, not a replacement for stage import: it changes matching, not which stage you bid on.
- Took the position that SQL (or "qualified lead") is the usual primary stage for B2B, because closed-won rarely clears 45/30 days inside 90 days; closed-won stays imported as secondary with value.
- Gray/WebMechanix added as topic Tier 2 (as in dossier 43).

## Canon strength: Strong
Four Tier 1 sources (Vallaeys ×3 pieces, Cruz, Hopkins) plus one added Tier 2 with the operational thresholds; evidence is practitioner method rather than a cross-account study.

## Invalidated by
Google changing the GCLID upload/restatement windows, the 90-day click window, Data Manager source cadences, or deprecating classic offline conversion import in favour of enhanced conversions for leads only.
