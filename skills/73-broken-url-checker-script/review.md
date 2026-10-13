# Review — 73 broken-url-checker-script
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Redirect-following off to capture first status, 403 false-positive causes, PMax expanded-URL coverage |
| 2 Takes a position | yes | Redirects treated as tracking/speed issue, not QS; priority by clicks and parameter loss |
| 3 Contradicts Google | yes | Rejects Google's QS framing and Destination-not-working as sufficient control |
| 4 Concrete | yes | >30 impressions, 30-day clicks, 30-minute runtime all cited |
| 5 Failure modes | yes | WAFs, large catalogs, account-level sitelinks, rate limits, PMax expansion, SPAs |
| 6 Operator-ready | yes | Eight numbered steps with classification table |
| 7 Dated | yes | last_verified, dated sources, invalidated_by |
| 8 Dossier-bound (attributed) | yes | Google checker behaviour labelled; Rooijmans/Rhodes attributed throughout |

## Failing lines (if FAIL)
- none
