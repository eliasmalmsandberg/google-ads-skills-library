---
name: keyword-funnelling-tiered-negatives
id: 13
description: How to run a managed/discovery (alpha/beta) two-tier structure where exact keywords live in a managed campaign and phrase/broad discovery is funnelled by exact negatives, including the promotion rule and the low-volume trap. Use when building a new Search structure with discovery. Not for fixing ad-hoc overlap in an existing account (skill 12) and not a three-tier exact/phrase/broad campaign split, which Epiminds builds only when skill 4's budget/bid-method gate passes.
tags: Technique / Search / Setup / Established / One-off
last_verified: 2026-10-13
invalidated_by: Keyword prioritisation changes removing identical-exact priority; negatives matching close variants; retirement of exact or phrase match; changes to the low-search-volume threshold or the 13-month zero-impression auto-pause.
---
## What this is
A two-campaign structure: a managed campaign holding exact keywords with their own budget and bids, and a discovery campaign on phrase (or gated broad) that funnels proven queries upward. Deterministic routing comes from two things working together: an identical exact keyword in the managed campaign, which Google sets aside before phrase/broad/PMax get the query (Google docs, 2026), and an exact negative for the same query in the discovery campaign so the query cannot stay there (Geddes/Adalysis, 2016). The promotion rule, not the structure, is what makes it work: a query moves up only when it has ≥ 35 impressions and ≥ 2 conversions a month for 3 consecutive months, because anything below ~35 impressions/month goes "low search volume" in the managed campaign and is then blocked in both (Geddes/Adalysis, 2016).
See also: skill 1 (alpha-beta-structure) — the same two-tier alpha/beta structure with Rooijmans's CPC-percentile screen, the budget and bid-method split and the scale gate.
See also: skill 4 (match-type-split-campaigns) — when a budget or bid-method reason justifies separate match-type campaigns despite the maintenance cost.

## Where it comes from
Brad Geddes' alpha/beta workflow and his later keyword-serving observations (Adalysis, 2016, 2021, 2024); Navah Hopkins' argument against match-type-split campaigns (SEJ, 2020); Vallaeys' 30k-account evidence that exact is the efficiency tier and phrase the workhorse (Optmyzr, 2026).

## When to use it / when not to
Use for small and mid-size accounts (Geddes/Adalysis, 2016) building a Search structure where discovery is needed and the top terms deserve their own budget. Do not use at enterprise scale with potentially millions of keywords — the promotion workflow does not scale (Geddes/Adalysis, 2016). Do not build three parallel match-type campaigns by default — only when skill 4's gate (a budget or bid-method reason per match type, and ≥30 conversions/30 days per campaign; Geddes/Adalysis, 2020; Vallaeys/Walker, 2025) passes — because close variants apply to every match type, negatives do not follow variants, each campaign is another budget and rarely supports more than 5–7 ad groups, and the negative count eats the 10,000-per-campaign limit (Hopkins/SEJ, 2020). Do not use if the account cannot sustain a monthly promotion routine; an unmaintained tier structure is worse than one campaign.

## Inputs
- Current keyword list with match types and 90-day performance.
- Search terms by campaign and ad group, 90 days.
- Conversion volume per candidate query, monthly for 3 months.
- Keyword status column (low search volume flags).
- Budget split available for managed vs discovery.

## Method
1. **Managed campaign (tier 1).** Exact keywords only; one theme per ad group; the campaign gets the larger budget and the tighter target. Exact is the efficiency tier in every non-brand segment across 30k accounts (Vallaeys/Optmyzr, 2026). Keep the exact copy of any keyword that also exists as phrase/broad elsewhere; do not act on "remove redundant keywords" (Geddes/Adalysis, 2024).
2. **Discovery campaign (tier 2).** Phrase keywords (post-2021 phrase behaves like the old modified broad, Geddes/Adalysis, 2021), or broad only if the campaign passes the gates in skill 16. Lower budget. Add every managed exact keyword as an exact negative here (Geddes/Adalysis, 2016). Do not use ad-group negatives for this; they hit limits fast — use a shared "→ managed" list applied to discovery (Geddes/Adalysis, 2018).
3. **Restriction check.** The same keyword in two campaigns serves from the more restricted campaign — smaller budget, fewer devices, tighter geo (Geddes/Adalysis, 2024). Make sure the managed campaign is not the more restricted one on anything except match type, or discovery will keep the query.
4. **Promotion rule, monthly.** From discovery search terms, promote a query only when it shows ≥ 35 impressions and ≥ 2 conversions in each of the last 3 months (Geddes/Adalysis, 2016). Promotion = add as exact keyword in the managed ad group whose ad and landing page fit, and add the same query as an exact negative to the "→ managed" list.
5. **Intent-split rule.** If a discovery query converts at a materially different rate from the managed keyword it resembles (Geddes' duplicate example: 18% / 32% / 20% across ad groups, 2021), it needs its own keyword and bid rather than being left to Google's selection, which favours keyword-level CTR, not conversion rate (Geddes/Adalysis, 2021).
6. **Demotion rule.** A managed exact keyword that drops to low-search-volume status is blocked in both campaigns (Geddes/Adalysis, 2016). Remove its exact negative from the discovery list so discovery can serve the query again, and leave the managed keyword paused until it re-qualifies. Google pauses zero-impression ad groups after 13 months (Hopkins/SEJ, 2024), so clear these before that.
7. **Variant hygiene.** Negatives do not match plurals or synonyms (Google docs, 2026), and close variants apply to all match types (Hopkins/SEJ, 2020). For each promoted query, add plural/singular and obvious word-order forms as exact negatives in discovery and as exact keywords in managed, otherwise the variant stays in discovery.
8. **Quarterly review** (Epiminds operating cadence — no canon source; reason: one quarter is the 3-month promotion window of rule 4, so each review sees one full promotion cycle). Count negatives in the "→ managed" list and search terms still duplicated across the two campaigns. If duplicates persist for the same families after two cycles (Epiminds threshold — no canon source; reason: one cycle can be seasonal noise, two means the families are not separable by match type), the family's intent is not separable by match type; merge it into one campaign and route by ad group (skill 12) (Hopkins/SEJ, 2020).

## What Google will tell you instead, and why we don't
Google says one broad keyword "includes everything narrower types catch", so separate exact and phrase versions are redundant, and surfaces "remove redundant keywords" (Google docs, 2026). The managed tier exists precisely because that is not how serving works in practice: the exact keyword is what gets the query set aside, and removed keywords are not remembered, so the query drifts (Geddes/Adalysis, 2024). Google also says broad should be the default; in this structure broad is a gated discovery option, not the base (Vallaeys/Optmyzr, 2026; skill 16).

## Failure modes
- **Enterprise keyword counts.** The promotion routine does not scale to enterprise accounts with potentially millions of keywords (Geddes/Adalysis, 2016).
- **Low-volume niches.** Few queries will ever hit 35 impressions + 2 conversions for 3 months; the managed tier stays empty and the structure adds nothing. Run one campaign.
- **Close-variant leakage.** Variants of promoted queries keep serving from discovery because negatives don't expand (Hopkins/SEJ, 2020); rule 7 is mandatory, and it is the maintenance cost Hopkins warns about.
- **Budget-limited managed campaign.** If managed is limited by budget, Google routes the keyword to PMax (Google docs, 2026) and to the discovery campaign by the restriction rule (Geddes/Adalysis, 2024).
- **Accounts with PMax.** PMax takes overlapping terms often (61% of overlapping impressions in Geddes' 2024 study); the managed exact keyword is what protects them, so build tier 1 before adding PMax.
- **Smart Bidding portfolios across tiers.** Epiminds position — no canon source: separate targets per tier are the point, since exact is the efficiency tier and phrase the volume tier (Vallaeys/Optmyzr, 2026); a shared portfolio target across both averages that difference away.

## What to measure
- Queries promoted per month and their CPA in managed vs their last 3 months in discovery.
- Count of search terms served by both campaigns (target: near zero after month 2).
- Managed keywords in low-search-volume status (demotion queue).
- Size of the "→ managed" negative list vs the 10,000 cap (Hopkins/SEJ, 2020).
- Spend share and CPA by tier, monthly (Vallaeys/Optmyzr, 2026 framing).

## Open disagreements in the canon
- **Is tiering still worth it?** Hopkins (2020) says no — close variants and negative limits make match-type structures a maintenance sink. Geddes (2016, 2024) keeps a managed/discovery split with strict promotion. Epiminds runs two tiers, not three, with Geddes' promotion rule and Hopkins' merge trigger (rule 8): the structure earns its keep only while duplicates fall month on month.
- **Discovery match type.** Geddes' 2016 version used modified broad; post-2021 the equivalent is phrase (Geddes, 2021), with broad only after skill 16's gates. Epiminds defaults discovery to phrase.
