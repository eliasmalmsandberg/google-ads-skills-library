---
name: automated-rules-vs-scripts
id: 77
description: Decide, for any recurring action, whether it runs as a Google Ads Automated Rule, a Script, an AI-assisted workflow or an agent — by determinism and blast radius first, capability second — and how each layer is logged and audited. For anyone setting up automation on an account. Not a scripting tutorial, not a bid-strategy choice.
tags: Strategy / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google removing Automated Rules or folding them into agentic features; Scripts limits changing (30 min, hourly, 250/account); the Ads API gaining native agent tooling that collapses the scripts-as-data layer.
---
## What this is
A four-layer stack — "simple automated rules → scripts → AI-augmented workflows → fully autonomous agents" — with one principle: every problem gets the lowest layer that can do it reliably (Rooijmans, 2026). Rules are for simple deterministic tasks (pause a campaign at $100 spend); adding AI to such logic "adds risk without benefit" (Rooijmans, 2026). Scripts are customizable, pull external data and APIs, run up to hourly within a 30-minute window and API quotas, 250 per account, and across an MCC; rules need no code, use only Google Ads metrics and cannot read external data (Vallaeys, 2025). Underneath all of it sits Google's own automation (Smart Bidding, auto-apply), which the practitioner's layers exist to monitor and control: "we have to control it, we have to monitor it" (Vallaeys, 2020).

## Where it comes from
Rooijmans's 2026 webinar framework (with the rollout rules for agents), Vallaeys's 2020 automation-layering position and 2025 scripts reference, and Vallaeys's 72,358-account study of change history (2026): manual work is 10.8% of changes but 22.8% of sessions, nine in ten manual changes are targeting, and budgets are the most repeated manual task (130,800 sessions across 20,141 accounts in six months). Change-history attribution per layer is from Rooijmans's script (2023).

## When to use it / when not to
Use when: a task is being done by hand more than weekly (the study's definition of waste: bulk-scale work done in the interface — Vallaeys/Optmyzr, 2026); when someone proposes an agent for a job a rule can do (Rooijmans, 2026); when a client says they do not trust automation with budgets — 40% of practitioners polled said the same (Vallaeys/Optmyzr, 2026), so the answer is a layer with a preview and an undo, not no automation.

Do not use it to: choose a bid strategy (Google's layer 0 is a given here); justify agents on a live account without the graduated permissions in step 6 (Rooijmans, 2026).

## Inputs
- The action: trigger condition, data needed, what changes, how often.
- Whether the data is all inside Google Ads metrics (rule-eligible) or needs external data, calculations across entities, sheets or email (script) (Vallaeys, 2025).
- Blast radius: the maximum spend or entities a wrong execution can touch before the next human look.
- Reversibility: can the change be undone from change history in one step.
- Who authorises: scripts run under the authorising user and are attributed to that email; rules appear as "Bulk Actions" (Rooijmans, 2023).

## Method
1. **Is it deterministic?** If the trigger and action can be stated as "when metric X over window W crosses T, do Y" with no judgment, it is rule-eligible (Rooijmans, 2026). Else go to step 3.
2. **Can a rule do it?** Rules use Google Ads metrics only, one entity type per rule, daily (hourly for some budget rules), with an email preview option [Google docs, unverified]; no external data, no cross-entity maths (Vallaeys, 2025). Pause at spend cap, pause ads with 0 conversions after N clicks, raise a capped budget for a dated promo: rule. If the logic needs a baseline (13-week averages), a sheet, a URL fetch or an external cap: script. Rooijmans's overspend pause is the boundary case — the script pauses on cost > budget × (1 + tolerance) and "an additional rule or script" re-enables at midnight (Rooijmans, 2022); use the rule for the re-enable.
3. **Script it when** the action is deterministic but needs data a rule cannot see: pacing against a monthly cap across PMax (skill 71), conversion watchdogs (skill 72), URL checks (skill 73), conflicts (skill 74), term lists (skill 76), policy polling (skill 75). Scripts run hourly at most, 30 minutes each; batch queries and fetch only needed fields (Vallaeys, 2025).
4. **Alert vs act.** Within scripts, start with the alert form (Vallaeys's "simple automation that flags drift", 2020) and move to the acting form only when the action is deterministic and reversible and the alert has been right for a quarter. Rooijmans's published scripts for negatives, placements and conflicts all stop at "suggest" (Rooijmans, 2023–2024).
5. **AI-assisted workflow when** judgment is needed but a human applies: ad copy drafts, term classification, placement review. Feed the model from script output so the numbers are the account's, not invented — scripts are the "structured tools that give LLMs clean data" (Rooijmans, 2026). Output is a CSV or sheet a human reviews (Rooijmans, 2026).
6. **Agent only with graduated permissions**: read-only API or MCP first; suggestions exported as CSV and applied by a person; permissions widened only as trust accumulates; every suggested change logged with its reasoning and its undo (Rooijmans, 2026). Never expose developer or refresh tokens; weigh privacy, security, safety and liability before any agent touches a client account; prompt injection is a live risk (Rooijmans, 2026).
7. **Audit by layer.** Daily change-history alert (Rooijmans, 2023): rules appear as "Bulk Actions", scripts under the authorising email, Google's own changes under system users. Whitelist "Bulk Actions" only after reviewing each rule (Rooijmans, 2023).
8. **Prioritise what to automate.** Start with the most repeated manual tasks in the account's own change history — in the cross-account data that is budgets, then keyword pause/enable (median 30 flips per session) and negatives (Vallaeys/Optmyzr, 2026).
9. **Maintenance.** Scripts break on API-version sunsets and platform changes; review quarterly, keep error logs, and never run an untested script live — a bad one can overspend (Vallaeys, 2025; Rooijmans FAQ, undated).

## What Google will tell you instead, and why we don't
Google's automation offer is Smart Bidding plus auto-applied recommendations, with Automated Rules as the legacy no-code layer [Google docs, unverified]. Vallaeys's position since 2020 is that Google's layer must be monitored and controlled by the practitioner's own automation, not trusted (Vallaeys, 2020); Rooijmans's is that AARs are the most expensive setting in a beginner's account (Rooijmans, 2026 — skill 78). We treat Google's automation as layer 0 to be watched, run rules only for deterministic actions, scripts for everything needing data, and agents only read-only until proven. Google's suggestion to let AI act broadly is the opposite of the canon's rollout rule.

## Failure modes
- **Agencies that script everything**: rules are cheaper to audit and cannot overspend from a bug; using a script for "pause at $100" is the error Rooijmans names (2026).
- **Rules on Smart Bidding campaigns**: a daily pause/enable rule disrupts learning; prefer budget reshaping (skill 71).
- **Scripts with hard-coded account values** in an MCC: silent wrong actions in other accounts (Vallaeys, 2025).
- **Agents on accounts with shared budgets, PMax or imported conversions**: an agent that cannot see cost for PMax in the campaign iterator (Rooijmans, 2022) will reason on partial data; keep it read-only.
- **Clients who distrust automation** (40% of practitioners do — Vallaeys/Optmyzr, 2026): start with alert-only scripts and rule previews; acting automation without a preview loses the account.
- **Copied scripts with pinned API versions**: they stop at sunset (Rooijmans FAQ, undated).

## What to measure
- Manual changes per month per account by type (from change history) — the study's benchmark is 10.8% of changes and 22.8% of sessions manual (Vallaeys/Optmyzr, 2026); drive budgets and keyword flips down first.
- Actions by layer per month: rules ("Bulk Actions"), scripts, AI-assisted (human-applied), agent.
- Alerts that became acting automations after a quarter of correct alerts.
- Script failures and rule misfires caught by the change-history audit.

## Open disagreements in the canon
Vallaeys (2025) splits rules and scripts by capability; Rooijmans (2026) by determinism and risk. Epiminds applies Rooijmans's test first (may it act?) and Vallaeys's second (can it?), because the cost of a wrong acting automation is the client, not the engineering time. On agents, Rooijmans allows them with graduated permissions; Vallaeys's 2026 study shows practitioners still do bulk work by hand out of distrust. We side with graduated permissions and log every agent suggestion, so distrust is answered with an audit trail rather than with more manual work.
