# Review — 27 ad-variations-account-wide-tests
**Verdict: PASS**
**Reviewed:** 2026-10-13 (blind: rubric.md + canon.md + SKILL.md only)

| Line | Holds? | Note |
|---|---|---|
| 1 Not default knowledge | yes | Label-copy pattern method with equal-set and segment rules, value-per-impression tiebreak, data-budget gate. |
| 2 Takes a position | yes | Labels by default, tool for mechanical replacement only; scopes per-ad-group vs account-wide. |
| 3 Contradicts Google | yes | Prefers own labelled data to Ad variations; refuses tests Google's tooling allows. |
| 4 Concrete | yes | 100/combination, 3 RSAs per ad group, "ad-" prefix all sourced. Explicitly asserts nothing about tool settings it could not verify. |
| 5 Failure modes | yes | Small accounts, brand mixing, 3-RSA ceiling, H3/D2 variables, AI Max, early reads. |
| 6 Operator-ready | yes | Seven numbered steps with decision conditions. |
| 7 Dated | yes | last_verified, source years, invalidated_by present. |
| 8 Dossier-bound (attributed) | yes | The unread help page is declared; no claim rests on it. Optmyzr 2023 product guidance is used only for the RSA-count fact and the tool's intended use, which is acceptable. |

## Failing lines (if FAIL)
- None.
