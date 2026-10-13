# Rubric — a skill PASSES only if every line holds

The reviewer sees only this file, canon.md and the SKILL.md under review. Verdict is PASS or FAIL; on FAIL, name the failing line numbers and the specific sentence or gap that fails each.

1. **Not default knowledge.** A strong LLM given a good prompt would not already produce this. Named methods, specific thresholds, published study findings, script logic and practitioner positions count; generic setup steps and textbook explanations do not. If most of the skill is default knowledge, it is cut or sharpened until this is true.
2. **Takes a position.** Where experts disagree, the skill says which way Epiminds goes and why. "It depends" without a decision rule fails.
3. **Contradicts Google somewhere.** At least one recommendation goes against what Google's UI or docs push. If the topic has no such point, the skill says so explicitly and justifies it.
4. **Concrete.** Every threshold, number, cadence or rule is specific and traces to a named source in the "Where it comes from" or inline citations. Unsourced numbers fail.
5. **Failure modes.** A "when this is wrong" section: account types, volumes, verticals or situations where the method doesn't apply or backfires.
6. **Operator-ready.** Written as inputs → decision rules → outputs, so an agent or a new hire can run it without the author. Numbered method steps with explicit conditions.
7. **Dated.** Has `last_verified`, the sources' dates, and an `invalidated_by` line naming the platform changes that would break it.
8. **Dossier-bound.** No claim in the skill that isn't attributed to a source the skill names. The reviewer cannot see the dossier, so this is checked by attribution: any material claim without a named source fails.
