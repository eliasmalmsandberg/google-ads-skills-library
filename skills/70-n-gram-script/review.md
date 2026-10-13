# Review — 70 n-gram-script
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)
Pass 3 (post-overlap edits)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Brainlabs script parameters, Rooijmans v2.0/v2.2 GAQL fixes, Geddes 150-click block rule, Query Count filter |
| 2 Takes a position | yes | 150-click aggregate + Query Count >=2 to block; 60-click review queue; soft-conversion n-grams as review list only |
| 3 Contradicts Google | yes | Google offers no word-level aggregation; n-gram as hygiene for close variants |
| 4 Concrete | yes | All defaults and thresholds cited; build-rule thresholds and PMax monthly cadence labelled Epiminds with reasons; privacy-threshold line flagged [Google docs, unverified] |
| 5 Failure modes | yes | Low volume, brand-heavy, large accounts, PMax, shared sets, pinned API versions |
| 6 Operator-ready | yes | Ten numbered steps with parameter values |
| 7 Dated | yes | last_verified, invalidated_by, source years |
| 8 Dossier-bound (attributed) | yes | Attributed; the one unverified Google-docs claim is labelled as such |

## Failing lines (if FAIL)
- None.
