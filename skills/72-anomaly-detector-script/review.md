# Review — 72 anomaly-detector-script
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Watchdog thresholds and revision history, 13-week baseline, 2-conv floor, change-history and bid guards |
| 2 Takes a position | yes | Decisions routed from the conversion layer; volume alerts closed after one check |
| 3 Contradicts Google | yes | Volume-only Google detector called insufficient; pinned apiVersion fix |
| 4 Concrete | yes | All thresholds cited; KPI-to-cadence mapping declared as Epiminds's own |
| 5 Failure modes | yes | Low volume, seasonal, Shopping, Bulk Actions floods, 10k changes, pins |
| 6 Operator-ready | yes | Eight numbered steps with explicit rules |
| 7 Dated | yes | last_verified, dated sources, invalidated_by |
| 8 Dossier-bound (attributed) | yes | Google detector behaviour labelled; all else attributed |

## Failing lines (if FAIL)
- none
