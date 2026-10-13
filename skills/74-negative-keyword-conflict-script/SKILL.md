---
name: negative-keyword-conflict-script
id: 74
description: Run Rooijmans's v2.1.1 fork of Google's Negative Keyword Conflicts script daily, read conflicts by level, and resolve them by rescoping the negative rather than deleting it; pair it with a conversion watchdog so a bad negative list is caught by its damage as well as by its logic. For Search accounts with many shared lists or many editors. Not for choosing negatives (skill 76), not for PMax.
tags: Script / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google applying close variants to negative keywords; removal of shared negative lists or keyword_view; GAQL paging changes that push the script's 250k/50k limits.
---
## What this is
A daily script that lists every enabled keyword in a serving campaign that is blocked by an ad-group negative, a campaign negative or an active shared list, with the level and the blocking negative, written to a sheet and emailed (Rooijmans, 2023). It is Google's solution script with one change that matters: `campaign.serving_status = "SERVING"` added to the keyword query, because Google's original also reports keywords in ended campaigns — a "major drawback" that makes people ignore the alerts (Rooijmans, 2023). The blocking rules it applies: a broad negative blocks when all its tokens appear in the keyword in any order; a phrase negative when its words appear contiguously in order; an exact negative only on identical text; broad positives can only be blocked by broad negatives, phrase positives by broad or phrase, exact positives by any (Rooijmans, 2023).
See also: skill 21 (negative-keyword-conflict-detection) — the conflict method itself: match-type logic, impact ranking and the which-side-is-wrong triage.

## Where it comes from
Rooijmans's fork and settings (2023, maintained 2025). The same matching logic appears in his negative-suggestions script (2024) and in Brainlabs's n-gram `checkNegatives` option (Gilbert/Brainlabs, 2015). The reason the script is not enough on its own is Rhodes's documented case: a "smart" new negative list blocked the brand and most converting terms until someone noticed the conversion drop (Rhodes, 2025).

## When to use it / when not to
Use when: more than one shared negative list is applied across campaigns; more than one person or tool edits negatives; after any bulk negative upload; whenever brand and non-brand campaigns share lists.

Do not rely on it when: the account exceeds the script's limits (250,000 positives / 50,000 negatives — it stops with an error; restrict with CAMPAIGN_LABEL) (Rooijmans, 2023); for PMax, where the script does not read campaign negatives; for account-level negatives, which its queries do not cover [Google docs, unverified; Rooijmans's v2.1.1 queries ad-group, campaign and shared lists only] — check that list by hand.

## Inputs
- Blank Google Sheet URL; `COPY_SPREADSHEET` false overwrites each run (Rooijmans, 2023).
- Recipient emails; `CAMPAIGN_LABEL` to scope large accounts (Rooijmans, 2023).
- The map of which shared lists are meant for which campaign types (brand / non-brand / competitor) — the script reports conflicts, you decide scope.
- Yesterday's data; schedule daily (the query window is yesterday) (Rooijmans, 2023).

## Method
1. **Install the fork, not Google's original.** Use Rooijmans's v2.1.1 so ended campaigns are excluded (Rooijmans, 2023). Preview, then schedule daily.
2. **Triage by level.** "Negative list" conflicts first (they hit every campaign the list is attached to), then "Campaign", then "Ad Group" (Rooijmans's level column, 2023).
3. **Decision per conflict.** (a) Negative was accidental (added by a team member, or by an applied recommendation — the two sources Rooijmans names, 2023): delete it and log who added it from change history (Rooijmans, 2023). (b) Negative is right for some campaigns and wrong for this one (brand term in a non-brand list, competitor term in brand): do not delete; move it to a list scoped to the campaigns it belongs in, or add it as a campaign-level negative there. The Rhodes case is the reason: the broad list was right for non-brand and fatal for brand (Rhodes, 2025). (c) Positive keyword is the mistake (a junk keyword someone added): remove the keyword.
4. **Match-type reading.** A broad negative blocking an exact positive usually means the negative's single token is too generic ("free", "cheap") — convert it to phrase or exact rather than deleting (rules from Rooijmans, 2023). A phrase negative blocking a phrase positive is a direct intent clash; decide which intent the campaign owns.
5. **Pair with the watchdog.** Run Rhodes's Search Term Watchdog alongside: it alerts when a top term's conversions go to zero against a 13-week baseline (Rhodes, 2025). The conflict script catches keyword/negative logic; the watchdog catches negatives that block search terms the keywords never listed — which is exactly how the brand-blocking list did its damage (Rhodes, 2025).
6. **After bulk uploads.** Run the conflict script in Preview immediately after any negative-list upload, before the daily run, and read the full sheet.
7. **Monthly.** Check account-level negatives by hand against brand and top converting keywords (not covered by the script); review lists attached to campaigns that have changed type (brand→non-brand splits).

## What Google will tell you instead, and why we don't
Google's Recommendations tab surfaces "Remove conflicting negative keywords" and offers to auto-apply it [Google docs, unverified]; Google's own solution script reports conflicts in ended campaigns too (Rooijmans, 2023). We run the filtered fork, we never auto-apply removal (skill 78), and our default resolution is to rescope, not delete — the negative usually exists for a reason, and Google's recommendation only knows that two strings clash, not which campaign owns the intent. Rooijmans's email template says you "may wish to delete" (2023); we treat delete as one of three outcomes (step 3).

## Failure modes
- **Enterprise accounts** above 250k positives or 50k negatives: hard stop; split by label (Rooijmans, 2023).
- **Accounts with ended campaigns still holding keywords**: Google's original floods; the fork fixes this (Rooijmans, 2023).
- **Brand/non-brand sharing lists**: every brand keyword shows as blocked after a non-brand list update — this is a real conflict, resolve by scope, not by muting the alert (Rhodes, 2025 case).
- **Negatives that block search terms but not keywords** (DSA, broad-match expansions): invisible to this script; the watchdog is the only catch (Rhodes, 2025).
- **One-day window**: a conflict created and resolved within a day is never reported; a conflict in a campaign paused yesterday is not reported until it serves again (Rooijmans, 2023).
- **Account-level negatives** and PMax negatives: not covered [Google docs, unverified].

## What to measure
- Conflicts per run by level and by resolution (deleted / rescoped / keyword removed).
- Conflicts traced to a named user or to an applied recommendation (change history), per month.
- Watchdog REDs that coincided with a negative-list change in the prior 7 days.
- Blocked keywords' prior-30-day conversions (how much the conflict cost before detection).

## Open disagreements in the canon
Google's solution maximises recall (every conflict, every campaign); Rooijmans filters to serving campaigns to keep the alert readable (2023). Epiminds runs the filtered fork and accepts the small recall loss on paused campaigns, re-checking after any re-enable. On resolution, Rooijmans's template defaults to deleting the negative; the Rhodes case and our own list-scoping practice argue for rescoping first. We go with rescoping: deleting fixes today's conflict and recreates tomorrow's waste.
