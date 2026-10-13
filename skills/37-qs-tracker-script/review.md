# Review — 37 qs-tracker-script
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)
Pass 2

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Null handling since 2016, GAQL path for components, impression-weighted series, 2015 reporting-bug signature, component index. |
| 2 Takes a position | yes | Keeps the series despite Hopkins; imputes 6; never pauses. |
| 3 Contradicts Google | yes | Aggregates QS against Google's explicit "do not aggregate". |
| 4 Concrete | yes | Pass-1 gaps fixed: 0.5/1.0 alert triggers (2.5×/5× Vallaeys's band), the 3-day/30-day rule, the QS ≤ 4 + 100-impression label gate and the small-account size are all labelled Epiminds operating thresholds with reasons. The 30-minute Scripts limit still lacks a [Google docs] tag — platform fact, note only. |
| 5 Failure modes | yes | Small accounts, MCC sheet growth, broad inheritance, reporting incidents, pause scripts, time zones. |
| 6 Operator-ready | yes | Config, fields, tabs, aggregates and alert rules specified. |
| 7 Dated | yes | |
| 8 Dossier-bound (attributed) | yes | Parker and PPC.io flagged as non-canon. |

## Failing lines (if FAIL)
- None.
