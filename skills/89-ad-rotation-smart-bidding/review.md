# Review — 89 ad-rotation-under-smart-bidding
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)
Pass 2

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Geddes's 20× misallocation, 82-vs-2,000 starvation, CTR-leader bias, 5,900-account pinning data; test-flag rule. |
| 2 Takes a position | yes | Optimize only when no test is live; pinned-variable two-RSA test on Smart Bidding. |
| 3 Contradicts Google | yes | "Do not optimize" during tests; rejects the comparable-vs-equal exposure framing. |
| 4 Concrete | yes | Two-ad cap labelled; the low-traffic approximation is now labelled as an Epiminds approximation with no canon threshold. |
| 5 Failure modes | yes | Low traffic, brand, Manual-for-rotation, single-RSA pressure, Shopping/Display. |
| 6 Operator-ready | yes | Classify → set → test design → AAR → audit, with output spec. |
| 7 Dated | yes | |
| 8 Dossier-bound (attributed) | yes | Pass-1 gaps fixed: the Ad variations recommendation is now an explicitly labelled operating rule that admits no source tests how well the split is honoured; the "bidding loss outweighs testing gain" claim is labelled Epiminds judgment with Geddes's 2018 note as the only adjacent evidence. |

## Failing lines (if FAIL)
- None.
