# Review — 67 merchant-center-diagnostics
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Clicks-weighted disapproval script with MIN_CLICKS, PMax Shopping-share alert, specific→general triage, tax-rate one-point buffer, migration window rule, timer-aware appeal sequencing. |
| 2 Takes a position | yes | Data before support; hourly fetches over automatic updates; id change only for a single history-less product. |
| 3 Contradicts Google | yes | Automatic item updates as a disapproval source; feed first instead of target/budget on PMax drops; deliberate `id` change. |
| 4 Concrete | yes | 10% (Rooijmans), 7/28 days and 7 business days [Google docs], one point above highest city rate (Williams), four-hour window (Williams), MIN_CLICKS default 1 (Rooijmans). |
| 5 Failure modes | yes | Alert fatigue, single-issue blindness, fast prices, bulk appeals, tax buffer on CTR, linked-account propagation. |
| 6 Operator-ready | yes | Daily/weekly split, seven steps, pattern→cause table, measures. |
| 7 Dated | yes | last_verified, dated sources (2020–2026), invalidated_by. |
| 8 Dossier-bound (attributed) | yes | Non-canon dissent (Pascoe/PPC Hero 2020) labelled. |

## Failing lines (if FAIL)
- none.
