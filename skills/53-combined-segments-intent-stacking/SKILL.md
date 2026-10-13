---
name: combined-segments-intent-stacking
id: 53
description: Using combined audience segments (AND/OR/NOT logic) to stack intent signals for tighter targeting. Not for Customer Match strategy (51), B2B exclusions (52), GA4 list building (54) or RLSA mode choice (50).
tags: Technique / All / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Any change to combined-segment availability by campaign type or to the AND/OR/NOT rules; Search gaining custom segments.
---
STATUS: THIN CANON — needs practitioner input

## What the dossier found
No Tier 1 or Tier 2 source publishes a method, threshold or result for combined segments. The archives checked (Optmyzr, Adalysis, Brainlabs, Nils Rooijmans, PPC Mastery newsletter, ZATO blog pages 1–7, Search Engine Land author archives for Andrea Cruz, Navah Hopkins, Fred Vallaeys, Aaron Levy and Kirk Williams) contain nothing on the topic. Adjacent positions: Cruz (Search Engine Land, 2026) argues for clustering people by shared pain point rather than one-to-one matching — intent stacking as a concept; Hopkins (Search Engine Land, 2023) argues that restricting to native audiences under Smart Bidding forfeits the algorithm's own audiences, which cuts against stacking restrictions at all; McNair (PPC Mastery, 2026) describes AND logic only in conversion value rules (one secondary condition), not in targeting. Google's combined-segments help page could not be fetched, so campaign-type availability and the current AND/OR/NOT rules are unverified. The baseline skill already gives the obvious NOT examples (pricing visitors NOT purchasers).

## What is missing
1. Any practitioner evidence that an AND-stacked segment (e.g. in-market X AND your-data list) outperforms the same lists in observation under Smart Bidding — the Hopkins position suggests it would not.
2. Current platform facts: which segment types can be combined on Search vs Display vs Demand Gen, whether combined segments can sit in observation, and size floors.
3. A decision rule for when a NOT-combination should be a combined segment rather than a plain campaign-level exclusion (skill 52 covers the latter and has sources).
4. Sophie Fell (Tier 2 for B2B audiences) could not be read (HTTP 429) and is the most likely canon holder of a view here.

## Question for Elias
Do we have any account where a combined segment in targeting mode on Search or Display beat the same lists in observation under tCPA/tROAS? If not, should this row be folded into skills 50 and 52 (exclusion logic and mode choice) rather than kept as its own skill?
