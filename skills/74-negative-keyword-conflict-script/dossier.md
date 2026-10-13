# Dossier — 74 Negative keyword conflict script

## Sources

1. **Source**: Nils Rooijmans, "Negative Keyword Conflicts Alert Script (update)" v2.1.1 — https://nilsrooijmans.com/negative-keyword-conflicts-alert-script-update/ (fetched) · **Tier** 1 · **Date** pub 2023-07-24, mod 2025-05-27; original by the Google Ads Scripts team · **Claim**: Pulls `keyword_view` for enabled, serving campaigns / enabled ad groups / enabled keywords for yesterday; checks ad-group negatives, campaign negatives and active shared lists attached to enabled campaigns; normalises text (lowercase, collapse whitespace, strip brackets/quotes, remove "+"); match rules — broad negative blocks when all its tokens appear in the positive in any order; phrase negative blocks when its words appear contiguously in order; exact negative blocks only identical text; broad positives are blocked only by broad negatives, phrase positives by broad or phrase, exact positives by any. Reports level (Campaign / Ad Group / Negative list) plus account ID, negative, blocked positives, campaign, ad group, list name. Change vs Google's original: adds `campaign.serving_status = "SERVING"` because the original "also looks at keywords in campaigns that have ended", a "major drawback" that makes people ignore the alerts. Settings: SPREADSHEET_URL, COPY_SPREADSHEET false, RECIPIENT_EMAILS, CAMPAIGN_LABEL '', MAX_POSITIVES 250,000, MAX_NEGATIVES 50,000; errors out above the limits — restrict by label. Email says you "may wish to delete" the conflicting negatives; conflicts often come from accidental negatives by team members. · **Evidence**: Published script; own experience of false alerts, no counts.

2. **Source**: Mike Rhodes, GitHub `mikerhodesideas/free` — `search-term-alert-evolution` (cloned 2026-10-13) · **Tier** 1 · **Date** 2025 · **Claim**: The watchdog script was built because a practitioner "added a new and smart (I thought) negative keywords list" that was too broad and "ended up blocking the brand + most of the converting search terms" until noticed; the fix was a conversion-drop alert on top terms. · **Evidence**: Documented case (no figures).

3. **Source**: Nils Rooijmans, "Negative Keyword Suggestions" script — https://nilsrooijmans.com/google-ads-script-negative-keyword-suggestions/ (fetched) · **Tier** 1 · **Date** 2024-10-21 · **Claim**: Uses the same broad/phrase/exact blocking rules to skip search terms already blocked; suggests only, never applies, because Google's matching "is imperfect, changes often". · **Evidence**: Published script.

4. **Source**: Nils Rooijmans, "Change History Alerts" — https://nilsrooijmans.com/google-ads-script-change-history-alerts/ (fetched) · **Tier** 1 · **Date** 2023-04-11 · **Claim**: Example alerts include non-brand keywords added to a brand campaign and accidental application of a Google recommendation; daily `change_event` review is how accidental negatives are traced to a user. · **Evidence**: Published script.

5. **Source**: Daniel Gilbert/Brainlabs, SEL n-gram script — https://searchengineland.com/brainlabs-script-find-best-worst-search-queries-using-n-grams-228379 (fetched) · **Tier** 1 · **Date** 2015 · **Claim**: `checkNegatives` option ignores queries already excluded by current negatives — the same conflict logic applied to queries rather than keywords; set false if the script times out. · **Evidence**: Published script.

## Dissenting view
Google's original solution reports every conflict including in ended campaigns; Rooijmans filters to serving campaigns because the noise makes people ignore alerts (2023). The disagreement is about recall vs signal: Google's version never misses a conflict, Rooijmans's never cries wolf. Rooijmans's email advice is to delete the negative; the Rhodes watchdog case shows the other option — keep the negative, fix the list scope — because the negative may be right for non-brand and wrong for brand.

## What the platform currently does [Google docs]
Google docs unreachable from this environment on 2026-10-13 (proxy denial). From prior knowledge, labelled unverified: [Google docs, unverified] Google publishes the "Negative Keyword Conflicts" solution script (single and MCC) on which Rooijmans's copy is based; the Recommendations tab shows "Remove conflicting negative keywords" and this is one of the auto-apply options; negative keywords do not use close variants (exact negatives block only the exact term, phrase negatives the phrase in order), and since 2024 account-level negative keywords exist for Search and Shopping and a separate PMax account-level list (Hopkins/Optmyzr 2026, dossier 69) — Rooijmans's v2.1.1 queries ad-group, campaign and shared-list negatives and does not mention account-level negatives.

## Baseline check
Read `google-ads-negative-keywords` and `google-ads-scripts`. The baseline says to "check for conflicts" without the match-type blocking rules, the serving-status fix, the limits, the account-level-negative gap or the delete-vs-rescope decision. This skill adds all of them.

## Judgment calls
- Account-level negatives are flagged as a probable gap in the script (not covered by its queries per the fetched description); the skill tells the operator to check that list manually.
- Position taken: a conflict is resolved by rescoping the negative (move from shared list to the campaigns it belongs in) rather than deleting, unless the negative was accidental.
- Daily cadence inferred from the script's YESTERDAY window.

## Canon strength: Adequate
Rooijmans (published script with full logic) plus Rhodes (case) and Brainlabs (same logic in a second tool); no cross-account evidence.

## Invalidated by
Google applying close variants to negative keywords (would change the blocking rules); removal of shared negative lists or `keyword_view`; the script's 250k/50k limits being hit by default on enterprise accounts after a GAQL paging change.
