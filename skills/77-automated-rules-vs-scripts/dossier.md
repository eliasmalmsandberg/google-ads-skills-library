# Dossier — 77 Automated rules vs. scripts — when each

## Sources

1. **Source**: Nils Rooijmans, "[Webinar] Building the modern Google Ads Automation stack" (with Ruben Runneboom, Taskforce Talks) — https://nilsrooijmans.com/daily/webinar-building-the-modern-google-ads-automation-stack (fetched) · **Tier** 1 · **Date** 2026-06-01 (webinar 2026-04-30) · **Claim**: Spectrum "simple automated rules → scripts → AI-augmented workflows → fully autonomous agents"; every problem needs the right tool. Rules: simple deterministic tasks, e.g. pause a campaign at $100 spend; adding AI to that adds risk without benefit. Scripts: structured tools that give LLMs clean data, prevent context drift and made-up figures; scripts and agents complement each other. Agents: tasks needing judgment, fed with SOPs and client context; still innovator-phase; roll out read-only first, export suggestions as CSV, expand permissions gradually, log every change with reasoning and undo; risks: prompt injection, privacy, security, safety, liability; never expose developer/refresh tokens. · **Evidence**: Framework from practice; no numbers.

2. **Source**: Frederick Vallaeys, SEL, "Automation layering is driving PPC so get onboard in 2020" — https://searchengineland.com/automation-layering-is-driving-ppc-so-get-onboard-in-2020-327123 (fetched) · **Tier** 1 · **Date** 2020-01-03 · **Claim**: Let Google run bidding and targeting; the practitioner layers monitoring and control on top; "we have to control it, we have to monitor it"; two layers: a simple alert when Google's behaviour drifts, or a script that detects and fixes. · **Evidence**: Framework.

3. **Source**: Frederick Vallaeys, SEL, "Google Ads scripts: Everything you need to know" — https://searchengineland.com/google-ads-scripts-everything-you-need-to-know-450294 (fetched) · **Tier** 1 · **Date** 2025-01-09 · **Claim**: Scripts: highly customizable, external APIs and data, dynamic adjustments; need JavaScript; 30-minute execution window; API quotas; hourly at most; 250 scripts per account; MCC scripts span accounts. Rules: no code, suited to simple tasks (pause low performers, adjust budgets), limited flexibility, no external data. Maintenance: scripts need updates for platform changes, error logs, monitoring; poorly tested scripts can overspend. Sources of scripts: Google docs, Rooijmans's library, Optmyzr's library, GitHub. · **Evidence**: Reference article; vendor-authored.

4. **Source**: Frederick Vallaeys, Optmyzr, "Advertisers Still Make 1 in 10 Google Ads Changes by Hand" — https://www.optmyzr.com/blog/google-ads-manual-work-study/ (fetched) · **Tier** 1 · **Date** 2026-09-16 · **Claim**: 72,358 accounts, Feb–Jul 2026, 578M changes: manual 10.8% of changes but 22.8% of sessions; API software 146M changes, feeds/automation 241M; sessions: API 1.99M, manual 1.34M, feeds 1.11M, Ads Scripts 1.09M; ~9 in 10 manual changes are targeting (keywords, negatives); budgets are 1% of manual volume but the most repeated task (130,800 sessions / 20,141 accounts); keyword pause/enable ~132,000 sessions, median 30 flips. Poll (n=64): 40% do not trust automation with client budgets, 34% habit, 13% client expects hands-on, 10% tools lack the feature. · **Evidence**: Cross-account study.

5. **Source**: Nils Rooijmans, "Change History Alerts" — https://nilsrooijmans.com/google-ads-script-change-history-alerts/ (fetched) · **Tier** 1 · **Date** 2023-04-11 · **Claim**: Automated Rules changes appear in change history under the user "Bulk Actions"; add it to IGNORE_USERS to suppress. Scripts run under the authorising user's email. · **Evidence**: Published script.

6. **Source**: Nils Rooijmans, "Do you want to prevent Google from spending 2x your daily budget?" — https://nilsrooijmans.com/daily/do-you-want-to-prevent-google-from-spending-2x-your-daily-budget (fetched) · **Tier** 1 · **Date** 2022-01-24 · **Claim**: The pause-on-overspend script needs "an additional rule or script" to re-enable — a concrete case of a rule and a script sharing one job. · **Evidence**: Published script.

## Dissenting view
Vallaeys (2025) frames rules as the no-code option for simple tasks and scripts as the flexible option — a capability split. Rooijmans (2026) frames it as a risk split: rules for deterministic actions precisely because they cannot be made "smart", scripts as the data layer for AI, agents only with graduated permissions. The disagreement is whether the choice is about what you can build or about what you should let act. The poll in Vallaeys's study (40% distrust automation with client budgets) is the counter-position to both: many practitioners choose neither.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] Automated Rules run at most once daily (or hourly for some budget rules), use only Google Ads metrics, can email a preview before acting, and are logged as "Bulk Actions" in change history (Rooijmans 2023 confirms the user label); Scripts run up to hourly, 30 minutes per execution (Vallaeys 2025), with `UrlFetchApp` for external data, Sheets/Drive/Gmail access, and MCC execution across accounts; auto-applied recommendations are the third automation layer and are Google-initiated (skill 78); the Google Ads API with developer token is the fourth, required for agents/MCP (Rooijmans 2026).

## Baseline check
Read `google-ads-scripts` (a scheduling table of hourly/daily/weekly tasks) and `google-ads-anomaly-detection` (rules vs scripts for alerts, unsourced). This skill adds the decision rule by determinism and blast radius (Rooijmans 2026), the capability limits with numbers (Vallaeys 2025), the evidence that the most repeated manual task is budgets (Vallaeys 2026) and the change-history attribution that lets you audit each layer.

## Judgment calls
- The skill's decision rule merges the two framings: capability (Vallaeys) gates feasibility, determinism/blast-radius (Rooijmans) gates permission.
- Google's own automation (auto-apply, Smart Bidding) is placed as "layer 0" to be monitored, per Vallaeys 2020; this placement is ours.
- "Preview before acting" for rules is stated from platform knowledge, unverified.

## Canon strength: Strong
Two Tier 1 practitioners with published frameworks, one cross-account study, two published scripts illustrating the boundary.

## Invalidated by
Google removing Automated Rules or folding them into agentic features; Scripts limits changing (30 min, hourly, 250/account); the Ads API gaining native agent tooling that collapses the scripts-as-data layer.
