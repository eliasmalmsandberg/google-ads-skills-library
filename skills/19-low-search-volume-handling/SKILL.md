---
name: low-search-volume-handling
id: 19
description: What to do with keywords flagged "Low search volume" or sitting at zero impressions — separating the two causes, the structural fixes, and the promotion trap in tiered accounts. Use when keywords are flagged or ad groups stop serving. Not for "Rarely shown due to low Quality Score" (Quality Score category) and not a keyword research procedure.
tags: Diagnostic / Search / Diagnose / Any / As needed
last_verified: 2026-10-13
invalidated_by: Google changing the low-search-volume threshold or review cadence; changes to the 13-month zero-impression ad-group auto-pause; changes to PMax routing of low-volume keywords; retirement of exact match.
---
## What this is
Two different problems that look the same in the keyword column. Low search volume (LSV) is Google deactivating a keyword with little or no search history — in practice a keyword that does not consistently get about 35 impressions a month (Geddes/Adalysis, 2016); it is rechecked roughly weekly on 12 months of worldwide searches and does not touch Quality Score (Google docs, 2026). Zero impressions on an active keyword is usually a structure problem: a "lost keyword" that loses the internal auction to a sibling under Smart Bidding, sits in an ad group with keywords at very different auction prices, or is a variant Google treats as a duplicate (Hopkins/SEJ, 2024). Since 11 March 2024 Google auto-pauses ad groups with zero impressions over 13 months and re-pauses them after 3 further months at zero if reactivated (Hopkins/SEJ, 2024). The skill decides which problem you have and whether the answer is wait, restructure, capture the demand another way, or let go.

## Where it comes from
Brad Geddes' low-volume keyword workflow and promotion rule (Adalysis, 2016) and his position on removing keywords (Adalysis, 2024); Navah Hopkins' zero-impression diagnosis and the 13-month pause details (SEJ, 2024 ×2) and her match-type-by-word-count rule (SEJ, 2020); Google's LSV documentation for platform behaviour.

## When to use it / when not to
Use when keywords are flagged LSV, when active keywords show zero impressions over 30+ days, when ad groups were auto-paused, and before promoting queries in a managed/discovery structure (skill 13). Do not use it for "Rarely shown (low Quality Score)" — that is a QS diagnosis. Do not use it to justify bulk deletion of LSV keywords: they do not harm the account (Google docs, 2026; Hopkins/SEJ, 2024) and removed keywords are not remembered by Google, so the query drifts to a worse ad group when demand returns (Geddes/Adalysis, 2024).

## Inputs
- Keyword report with status column, impressions over the last 13 months (all-time view) and last 30 days.
- Ad groups sorted by impressions, all-time; change history for pauses (Hopkins/SEJ, 2024).
- Ad group composition: keywords per ad group, CPC spread (Keyword Planner estimates), match types, duplicates.
- Campaign impression share and budget-limited status.
- Keyword Planner volume and Google Trends by region for the concept (Hopkins/SEJ, 2024).

## Method
1. **Classify each flagged keyword.**
   - Status = Low search volume → demand problem; go to rule 2.
   - Status = Eligible, zero impressions ≥ 30 days (Epiminds operating threshold — no canon source; reason: four of Google's roughly weekly rechecks, Google docs 2026, with no reactivation) → structure problem; go to rule 4.
   - Ad group paused by Google → 13-month rule; go to rule 6.
2. **LSV, new concept or seasonal.** Wait; Google rechecks about weekly and reactivates on any rise (Google docs, 2026). Check Keyword Planner and Trends for the concept and region (Hopkins/SEJ, 2024). Do nothing for at least one review cycle on new brands, products or seasons.
3. **LSV, persistent (3+ months)** (Epiminds operating threshold — no canon source; reason: matches the 3-consecutive-month window Geddes uses to judge a query's volume as stable, Adalysis 2016, and covers a quarter of weekly rechecks). Do not loosen a short keyword to broad: single words on anything but exact are wasteful (Hopkins/SEJ, 2020) and broad on thin data has no competent bidder (skill 16). Options in order:
   a. If a phrase keyword of 3+ words exists that would cover the concept, rely on it and leave the exact keyword in place (it costs nothing; Geddes/Adalysis, 2024).
   b. If the concept matters and no phrase covers it, add a phrase or a 5+-word broad keyword isolated in its own ad group with other keywords as exact+phrase negatives (Hopkins/SEJ, 2020), or run DSA on the relevant pages to see how people actually search for it (Hopkins/SEJ, 2024).
   c. Shorten the phrase only if the shorter form still carries the same intent (Google docs, 2026 suggests shortening; Geddes/Adalysis, 2021 shows dropped words change intent).
   d. Remove only when approaching account limits (Google docs, 2026).
4. **Zero impressions on an eligible keyword.** Check in order (Hopkins/SEJ, 2024): ad approval and editorial review (trademark, credit); duplicate variants Google treats as the same keyword (the higher Ad Rank one serves; Google docs, 2026); bids and budget competitive for the concept (Keyword Planner); the campaign not budget-limited (a limited campaign routes keywords to PMax; Google docs, 2026).
5. **Structural fix.** If the ad group has more than ~20 keywords or the campaign more than ~10 ad groups (Hopkins/SEJ, 2024 flags these sizes), separate keywords with different values and auction prices so they don't compete for one budget; put high-value low-volume keywords in their own campaign with its own budget rather than leaving them to lose the internal Smart Bidding auction (Hopkins/SEJ, 2024). Keep each campaign's keywords close in CPC (Hopkins/SEJ, 2019 via skill 20).
6. **Auto-paused ad groups.** If 13 months at zero, let it go; move the concept into another campaign or cover it with sitelinks (Hopkins/SEJ, 2024). Reactivate only with a structural change (rule 5), because a reactivated group at zero is re-paused after 3 months (Hopkins/SEJ, 2024).
7. **Tiered-structure trap.** In a managed/discovery setup, never promote a query to an exact keyword in managed until it has ≥ 35 impressions and ≥ 2 conversions a month for 3 consecutive months; promoting earlier makes it LSV in managed while the exact negative blocks it in discovery, so it serves from neither (Geddes/Adalysis, 2016). If this has already happened, remove the discovery negative first.
8. **Log and revisit monthly** (Epiminds operating cadence — no canon source; reason: the thresholds in rules 1 and 3 are measured in months). LSV keywords are re-evaluated by Google continuously; keep a monthly report of status changes and impressions on reactivated keywords.

## What Google will tell you instead, and why we don't
Google's LSV page offers: wait, remove and find alternatives, broaden the match type, or shorten the phrase (Google docs, 2026). We keep "wait". We reject "remove" as a default because removed keywords are forgotten and the query drifts (Geddes/Adalysis, 2024), and the keyword is harmless where it is (Hopkins/SEJ, 2024). We reject "broaden" for short terms because single words beyond exact are wasteful (Hopkins/SEJ, 2020) and broad needs the gates in skill 16. We accept "shorten" only when the shortened form keeps the intent, since dropped words measurably change intent (Geddes/Adalysis, 2021). Google also surfaces the 13-month auto-pause as hygiene; we use it as a trigger to inspect structure before accepting the pause.

## Failure modes
- **Niche B2B and long-tail accounts.** Many legitimate keywords sit under ~35 impressions a month; a tiered structure will strand them (Geddes/Adalysis, 2016). Run one campaign with phrase coverage instead.
- **Seasonal keywords.** LSV in the off-season is normal; the 13-month window covers a full season (Hopkins/SEJ, 2024), so don't restructure for seasonality.
- **Regional accounts.** The LSV check uses worldwide search history (Google docs, 2026), so a keyword can be LSV even where local demand exists; Trends by region tells you (Hopkins/SEJ, 2024).
- **Budget-limited campaigns.** Zero impressions may be routing to PMax, not demand (Google docs, 2026); fix budget before restructuring.
- **Quality Score confusion.** "Rarely shown (low QS)" is a different status with a different fix; don't apply this method.
- **Bulk "remove LSV keywords" recommendations.** Deleting them cleans the UI and loses control (Geddes/Adalysis, 2024).

## What to measure
- Count of LSV keywords and their monthly status changes (reactivations).
- Impressions on keywords within 30 days of a structural fix (rule 5).
- Ad groups within 3 months of the 13-month auto-pause threshold (queue for review).
- Keywords with zero impressions in campaigns flagged budget-limited (routing signal).
- In tiered accounts: promoted keywords that went LSV within 3 months (promotion-rule breaches; Geddes/Adalysis, 2016).

## Open disagreements in the canon
- **Remove or keep.** Google and tidy-account practice remove LSV keywords; Geddes (2024) keeps keywords as a rule. Epiminds keeps them unless account limits bind.
- **Auto-pause.** Hopkins (2024) supports the 13-month pause; others see lost control. Epiminds accepts the pause but inspects structure first, because a lost keyword is often a structure symptom (Hopkins/SEJ, 2024).
- **The 35-impression figure.** A 2016 practitioner observation (Geddes) not confirmed on Google's page; Epiminds uses it as a working threshold and watches reactivations to recalibrate.
