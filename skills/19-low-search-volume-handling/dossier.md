# Dossier — 19 Low search volume / rarely shown keyword handling

Research note: WebSearch budget exhausted; sources via sitemaps. The Google Ads developer blog announcement of the zero-impression ad-group pause (Jan 2024) could not be fetched; it is cited through Hopkins (SEJ, 2024) who links it. searchengineland.com rate-limited.

## Sources

1. **Source**: Brad Geddes, Adalysis — "Managing low volume keywords in an alpha/beta (managed/discovery) workflow", https://adalysis.com/blog/managing-low-volume-keywords-alphabeta-manageddiscovery-workflow/ · **Tier** 1 · **Date** 2016-04-12 · **Claim**: A keyword that doesn't consistently get ~35 impressions a month is marked low search volume and won't trigger ads. In a managed/discovery structure, promoting a query too early makes it LSV in managed while an exact negative blocks it in discovery — it shows from neither. Rule: promote only at ≥ 35 impressions and ≥ 2 conversions per month for 3 consecutive months. · **Evidence**: author's experience; no account figures.
2. **Source**: Navah Hopkins, SEJ — "What is the impact of having zero-impression keywords/ad groups?", https://www.searchenginejournal.com/what-is-the-impact-having-zero-impression-google-ad-keywords-ad-groups/510252/ · **Tier** 1 · **Date** 2024-04-04 · **Claim**: Distinguish LSV (keyword still earns some impressions/clicks; niche or exact-match cause; Google says LSV keywords don't harm Quality Score) from zero impressions (low demand or "lost keyword" from structure: Smart Bidding winners/losers inside one campaign, conflicting auction prices in one ad group/campaign, duplicate variants Google treats as duplicates). Google pauses ad groups with zero impressions over 13 months from 11 March 2024; reactivated groups are re-paused after 3 months at zero. Large structures (> 20 keywords/ad group, > 10 ad groups/campaign) are the usual cause. Diagnose: sort ad groups by impressions on all-time; check change history; healthy IS suggests groups are fine. Fix: restructure so differently-valued keywords don't share a budget; separate high-value from high-volume low-value; remove duplicate variants. If no impressions in 13 months, let it go; move the concept or cover with sitelinks. · **Evidence**: reasoning; cites the Ads developer blog; no data.
3. **Source**: Navah Hopkins, SEJ — "Why have my Google Ads not got any impressions?", https://www.searchenginejournal.com/ask-a-ppc-why-have-my-google-ads-not-got-any-impressions/515178/ · **Tier** 1 · **Date** 2024-06-13 · **Claim**: 5+-word exact keywords may get zero impressions; check approval/editorial review, duplicates, bid/budget competitiveness via Keyword Planner, Google Trends for regional demand; use DSA to see how people actually search; limited broad with many negatives and bid caps; separate campaign budget for the idea or pause. Google will pause keywords with zero impressions over 13 months. · **Evidence**: opinion.
4. **Source**: Brad Geddes, Adalysis — "Should you remove redundant keywords?" · **Tier** 1 · **Date** 2024-07-03 · **Claim**: Keep keywords; Google doesn't remember removed ones; identical exact keywords get set aside — relevant to the "remove LSV keywords" recommendation. · **Evidence**: account cases.
5. **Source**: Navah Hopkins, SEJ — "Match-type changes & campaign structure choices" · **Tier** 1 · **Date** 2020-03-10 · **Claim**: Single words on anything but exact are wasteful; broad only for 5+-word terms isolated with negatives — the structural alternative to "broaden the match type" for LSV. · **Evidence**: reasoning.

## Dissenting view
Google's help page recommends removing LSV keywords or broadening match type; Geddes (2024) argues against removing keywords generally, and Hopkins (2020) argues against loosening match types on short terms. Within the canon, Hopkins (2024) supports Google's 13-month auto-pause ("let it go") while noting others "lament lost control". The disagreement is whether LSV is a hygiene problem (remove) or a structure/volume problem (wait, restructure, or capture via phrase/DSA).

## What the platform currently does [Google docs]
- [Google docs] Low search volume: "very little to no search history on Google"; keyword inactive until traffic rises; rechecked regularly (about a week) using worldwide searches over the past 12 months; no link to QS, bids or creatives; doesn't harm the account; suggested fixes: wait, remove and find alternatives, broaden match type, shorten the phrase (support.google.com/google-ads/answer/2616014, fetched 2026-10-13; no date on page). Geddes' "~35 impressions/month" threshold (2016) is a practitioner figure, not on Google's page.
- [Google docs] Ad groups with zero impressions for 13 months auto-paused from 11 March 2024; re-paused after 3 months at zero if reactivated (Hopkins/SEJ 2024 citing the Ads developer blog; blog not fetched).
- [Google docs] Keywords may serve from PMax instead of Search when the keyword is low search volume (answer/7478529, fetched 2026-10-13).
- [Google docs] "Rarely shown due to low Quality Score" status: page not fetched; not covered in this dossier.

## Baseline check
Read `google-ads-keywords` (status table: "Low search volume: <10 searches/month — pause or use broad variant"; "Rarely shown due to QS: fix QS first"). This skill adds the 35-impressions/month practitioner threshold, the LSV-vs-zero-impression distinction with structural causes, the promotion trap in tiered structures, the 13-month auto-pause with its date and re-pause rule, the PMax routing consequence, and the position against "just broaden the match type".

## Judgment calls
- "Rarely shown due to low Quality Score" is out of scope here (Google page not fetched; QS category owns it); the skill says so.
- The baseline's "<10 searches/month" figure is not in any canon source; the skill uses Geddes' ~35 impressions/month with its date and the caveat that it is 2016 practitioner observation.

- Review fix (2026-10-13): the 30-day zero-impression window (four weekly Google rechecks), the 3-month persistence window (mirrors Geddes' 3-consecutive-month volume test) and the monthly revisit are Epiminds operating thresholds/cadence, labelled as unsourced in SKILL.md.

## Canon strength: Adequate
Geddes (2016) and two Hopkins pieces (2024) with method; Geddes 2024 supporting; evidence is practitioner observation, not data.

## Invalidated by
Google changing the LSV threshold or review cadence; changes to the 13-month zero-impression auto-pause; changes to PMax routing of LSV keywords; Google retiring exact match.
