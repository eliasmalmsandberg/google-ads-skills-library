# GOAL: Build the Epiminds Google Ads skills library

You are building a library of Google Ads skills and SOPs for Epiminds. The bar is the best independent practitioners in the world, not Google's best practices. Work autonomously through the phases below. Do not ask me questions unless a decision is irreversible or the canon is genuinely too thin to proceed; take the most reasonable reading and log it.

## What "done" means
A folder structure containing, for every row in the index: a research dossier, a skill file, and a review verdict of PASS. Plus the shared files (canon, rubric, template) that make the library auditable and refreshable.

## Inputs
- `google-ads-skills-index.xlsx` (attached or in the project) — the 90 skills with tags and priorities. This is the backlog AND the single source of truth for progress: you update it, never a copy. Its `Status`, `Folder link`, `Last verified`, `Invalidated by`, `Canon strength` and `Review` columns are yours to fill; leave every other column alone. Keep the file's existing formatting, dropdowns and the Summary/Tag legend tabs intact (edit with openpyxl, then recalculate).
- The canon list below. Treat it as a starting point; extend it only with sources that meet the inclusion rule.
- `../google-ads-skills/skills/` — Elias's existing public repo of 21 broad Google Ads skills. Treat these as the **baseline of what a model already knows**. Read the relevant one before writing each new skill; the new skill must go beyond it (rubric line 1). Never copy from them, and never write into that repo.

## Phase 0 — Scaffold (do this first, once)
Create this structure:

```
/google-ads-skills/
  canon.md
  rubric.md
  template.md
  google-ads-skills-index.xlsx   (the attached file, moved here; the live index)
  changelog.md
  /skills/
    /<id>-<slug>/
      dossier.md
      SKILL.md
      review.md
```

### canon.md
Write it with these sections:
1. **Inclusion rule** — a source belongs in the canon if it (a) publishes its actual method, not just takes; (b) disagrees with Google in public at least sometimes; (c) shows evidence — data, studies, scripts, account results — rather than only opinion. Agency blogs, "10 tips" content, and Google's own recommendations fail this rule.
2. **Tier 1 — the bar.** The practitioners whose view wins when sources conflict. Start from this list; for each, verify on inspection that they still pass the inclusion rule and note their strongest topics:
   - **Mike Rhodes** (8020agent) — scripts, PMax insights, automation; the PMax script is canon for everything PMax.
   - **Fred Vallaeys / Optmyzr** — the published studies (ad strength vs performance, broad match, RSA counts, automation layering); evidence over opinion.
   - **Brad Geddes / Adalysis** — Quality Score, ad testing methodology, statistical significance for ads, account structure.
   - **Kirk Williams / ZATO** — Shopping, feeds, PMax vs Standard Shopping, e-commerce structure.
   - **Nils Rooijmans** — Google Ads scripts; the n-gram, anomaly and hygiene scripts.
   - **Miles McNair and Bob Meijer / PPC Mastery** — RSA writing and testing, pinning, structure under Smart Bidding, bid strategy choice, audits. Their public material (YouTube, blog, newsletter, podcast) is Tier 1.
   - **Brainlabs (Daniel Gilbert et al.)** — published scripts and methods: QS tracker, search term tools, structure.
   - **Andrea Cruz** — PMax, Smart Bidding diagnostics, conversion tracking and value-based bidding.
   - **Navah Hopkins** — bid strategies, budget pacing, how Smart Bidding actually behaves; useful for the "what Google tells you vs what happens" sections.
   - **Ginny Marvin** (Google Ads Liaison) — reference only for platform behaviour and what changed when; never for recommendations.
   **Benchmark system: PPC OS** (https://www.ppcmastery.com/hub#ppc-os) — PPC Mastery's paid, agent-oriented Google Ads knowledge base (reference docs, SOPs, skills). It is the structural bar this library is measured against: topic coverage, SOP granularity, and the audit/diagnostic framing (e.g. a 24-diagnostic account audit, a 50-point tracking audit). Use only its publicly visible structure and topic list to check our coverage; do not reproduce or paraphrase its paid content. Where our index lacks a topic PPC OS covers, add a row in the Phase 2 coverage pass.
3. **Tier 2 — supporting.** Cite for specific topics, not generally. Start from: Aaron Levy (structure, measurement), Amy Hebdon / Paid Search Magic (QS, ad copy), Julie Friedman Bacchini (account hygiene, small accounts), Mark Irvine (bidding, structure), Ed Leake (Alpha/Beta structure, scripts), Sophie Fell (B2B search), Anders Hjorth / Innovell (bidding research), Frederick Boutin and the Google Ads Scripts community for script variants. Add others per topic as the dossiers surface them; drop any that fail the inclusion rule.
4. **Reference only.** Google Ads Help and developer docs: used solely to state what the platform currently does. Never cited as the reason to do something.
5. **Conflict rule.** Tier 1 beats Tier 2. Evidence beats opinion at any tier. Newer beats older if the platform changed in between. When Tier 1 sources disagree with each other, the skill must present both positions and take one, with the reason.
6. **Watch list** — newsletters, changelogs and feeds to sweep in the quarterly refresh.

Before moving on, send me the Tier 1 list with any drops or additions in one message, then continue without waiting.

### rubric.md
A skill PASSES only if every line holds:
1. **Not default knowledge.** A strong LLM given a good prompt would not already produce this. If it would, the skill is cut or sharpened until this is true.
2. **Takes a position.** Where experts disagree, it says which way Epiminds goes and why.
3. **Contradicts Google somewhere.** At least one recommendation goes against what Google's UI or docs push. If the topic has no such point, say so explicitly and justify.
4. **Concrete.** Every threshold, number, cadence or rule is specific and traces to a dossier source.
5. **Failure modes.** A "when this is wrong" section: account types, volumes, or situations where the method doesn't apply or backfires.
6. **Operator-ready.** Written as inputs → decision rules → outputs, so an agent or a new hire can run it without the author.
7. **Dated.** Has `Last verified`, the sources' dates, and an `Invalidated by` line naming the platform changes that would break it.
8. **Dossier-bound.** No claim in the skill that isn't in the dossier.

### template.md
The SKILL.md structure every skill follows:
```
---
name: <slug>
id: <index id>
description: <one line: when to use this; what it is NOT for>
tags: type / campaign / phase / maturity / cadence
last_verified: <date>
invalidated_by: <platform changes that would break this>
---
## What this is
## Where it comes from (canon sources, 2–3 lines)
## When to use it / when not to
## Inputs
## Method (the decision rules; numbered)
## What Google will tell you instead, and why we don't
## Failure modes
## What to measure
## Open disagreements in the canon
```

## Phase 1 — Build loop (repeat per skill)
Work in priority order: all P1 first, then P2, then P3. Within a priority, group by category so research carries over. For each skill:

1. **Research dossier** (`dossier.md`). Read canon.md first. Find 4–6 sources from the canon for this specific topic. For each: source, tier, date, the specific claim, and whether it's evidence or opinion. Must include at least one dissenting view and a sentence on what the disagreement is actually about. Record what the platform currently does from Google docs, labelled as such. End with a `Canon strength` rating. If strength is Thin (fewer than 2 Tier 1/2 sources), do not write the skill from memory: write a stub SKILL.md marked `STATUS: THIN CANON — needs practitioner input`, log it, and move on.
2. **Write the skill** (`SKILL.md`) from the dossier only, in the template.
3. **Review** (`review.md`). Spawn a separate reviewer that sees only rubric.md, canon.md and SKILL.md — not the dossier, not the conversation. It returns PASS or FAIL with the failing rubric lines. On FAIL, revise and re-review; after two fails, mark `STATUS: NEEDS ELIAS` and move on.
4. **Update the xlsx** — set `Status` (Drafting → Review → Done), `Folder link` (relative path to the skill folder), `Last verified`, `Invalidated by`, `Canon strength`, `Review` — and append one line to `changelog.md`. Do this after every skill, not in batches, so progress survives an interrupted session.

Send me a one-line progress message after every 5 skills. After each category is complete, send the category's skills for review in one message and continue to the next category without waiting.

## Phase 2 — Library-level checks (after all skills)
1. **Overlap pass.** Find skills that say the same thing; merge or cross-reference. Find contradictions between skills; resolve against canon.md and log the decision.
2. **Coverage pass.** Reading the canon's Tier 1 sources as a whole, and PPC OS's public topic list, list methods treated as core that have no skill in the library. Add them as new rows in the xlsx (next ID, tagged, Status "Proposed"); don't write them yet.
3. **Thin-canon report.** One list of every THIN CANON and NEEDS ELIAS skill with the specific question I need to answer for each.

## Phase 3 — Keep it current
Set up a quarterly scheduled task that: reads canon.md's watch list, checks each skill's sources and the platform changelog for changes since `Last verified`, and flags affected rows in the xlsx (Status "Re-check" plus the reason in `Notes`). It does not edit skills. It sends me the flagged list.

## Resuming
If the folder already exists, do not re-scaffold. Read the xlsx, skip every row with Status Done or NEEDS ELIAS, and continue from the next open row in priority order.

## Working rules
- Every claim traces to the dossier. If you can't source it, it doesn't go in.
- Paraphrase sources; don't quote at length.
- Write for a Google Ads practitioner. No definitions of basics, no preamble.
- Prefer a sharp, narrow skill over a broad, hedged one.
- Log every judgment call in changelog.md with the reason.
- When you finish a phase, say so in one line and keep going.
