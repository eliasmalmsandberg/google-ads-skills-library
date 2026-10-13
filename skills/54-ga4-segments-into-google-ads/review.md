# Review — 54 ga4-segments-into-google-ads
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Tag-vs-GA4 split with Williams' 60%/90% fire-rate thresholds, 100-slot cap management, proxy-signal design with CRM gate, PMax absorption check. |
| 2 Takes a position | yes | Tag for transactional lists, GA4 only for conditions the tag cannot express; CRM join required before promoting any proxy. |
| 3 Contradicts Google | yes | Rejects the GA4-first linking flow as default remarketing source. |
| 4 Concrete | yes | Platform numbers labelled [Google docs]; 30/90/540 durations explicitly "Epiminds defaults (not sourced figures)"; 60%/90% to Williams. The "alarm at 80 of 100" buffer is unlabelled but is a monitoring alarm against a sourced cap, not a decision rule. |
| 5 Failure modes | yes | GA4-only tag deployments, EU consent decline, low-traffic lead gen, agency cap exhaustion, no CRM join, lead-gen extension of e-commerce evidence. |
| 6 Operator-ready | yes | Inputs, eight numbered steps, list-register output. |
| 7 Dated | yes | last_verified, dated sources, invalidated_by. |
| 8 Dossier-bound (attributed) | yes | All material claims attributed; McNair claim is named even though routed "as summarised in skill 50". |

## Failing lines (if FAIL)
- none. Suggested tidy-ups: label the "80 of 100" alarm and the quarterly verification cadence in step 7 as Epiminds choices.
