# Review — 69 pmax-insights-script
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)
Pass 3 (post-overlap edits)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Script data sources by GAQL resource, Product Matrix buckets, lotsproducts flag, Rooijmans drift/negative thresholds |
| 2 Takes a position | yes | Brand share and channel split first, negatives second; nobody auto-applies exclusions |
| 3 Contradicts Google | yes | Script exists because the UI hides channel split and cost; disputes PMax reporting defaults |
| 4 Concrete | yes | $199/$399, 100 clicks/0.5 conv, 100 imp/50%, 10 cents/day, 30 impressions all cited; Epiminds rule in step 2 labelled |
| 5 Failure modes | yes | No feed, huge catalogs, tiny and huge accounts, TLD false positives, MCC, API sunsets |
| 6 Operator-ready | yes | Eight numbered steps with decision rules per tab |
| 7 Dated | yes | last_verified, invalidated_by, source years |
| 8 Dossier-bound (attributed) | yes | Rhodes/Rooijmans/Vallaeys/Hopkins named per claim |

## Failing lines (if FAIL)
- None.
