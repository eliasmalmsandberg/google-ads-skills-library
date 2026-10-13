---
name: intent-tier-keyword-taxonomy
id: 20
description: Classify keywords into intent tiers by measured CPA behaviour, group them so budgets and bids can follow intent under Smart Bidding, and decide which tiers get a campaign, an ad group, a lower bid or a negative. Use when building or rebuilding keyword lists. Not a search-term mining procedure (skills 10, 12) and not a funnel media plan beyond Search.
tags: Strategy / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Removal of campaign-level bid targets and budgets; removal of conversion values or primary/secondary conversion actions; AI Max replacing keyword-level control in Search campaigns.
---
## What this is
An intent taxonomy built from how query words move CPA, not from a textbook funnel. In one account averaging ~$450 CPA, queries containing "how" ran at more than double that, cost-question queries above $1,000, "what" queries elevated, and "quote" queries under $300 (Geddes/Adalysis, 2021). Google detects similar meaning but not similar intent — "cost" vs "quote", "trademark" vs "copyright" — and its CPA bidding does not price the difference (Geddes/Adalysis, 2021); in a later account spending millions on exact + tCPA, Smart Bidding never adjusted for "how" queries at > $1,000 CPA against a ~$300 average despite more than 10,000 clicks of evidence (Geddes/Adalysis, 2022). So the tiers must be built into structure, values and negatives, where the bidder can't ignore them.

## Where it comes from
Brad Geddes' intent-word CPA data, ad-group theming rule and n-gram classification rules (Adalysis, 2021, 2022 ×2, 2024, 2025); Navah Hopkins' auction-price grouping, match-type-by-word-count and value-setting rules (SEJ, 2019, 2024); Miles McNair's bottom-up expansion order (PPC Mastery, 2026); Vallaeys' cross-account match-type and Smart Bidding findings (Optmyzr, 2026 ×2).

## When to use it / when not to
Use when building a keyword list, when CPA varies widely inside one campaign, and when Smart Bidding is hitting its target on average while specific query families run far above it. Do not use it to split campaigns for its own sake — split only when the ad or landing page must change or when auction prices differ enough that one budget cannot serve both tiers (Geddes/Adalysis, 2022; Hopkins/SEJ, 2024). Do not apply to brand, which is its own tier with its own rule (exact-led; Vallaeys/Optmyzr, 2026).

## Inputs
- Search terms and keywords, 90 days, with cost, conversions, conversion value, CPA.
- n-gram table (skill 10) with CPA per 1-gram — the intent-word evidence.
- Keyword Planner CPC estimates per keyword family (auction price; Hopkins/SEJ, 2019).
- Conversion actions, their values and primary/secondary status.
- Current campaign/ad group structure and budgets.

## Method
1. **Measure, don't guess.** From the n-gram table, list every 1-gram and 2-gram with a CPA (or ROAS) materially different from the account average — Geddes' examples are 2× worse ("how"), > 2× worse (cost questions) and ~⅓ better ("quote") (Adalysis, 2021). These words define the tiers for this account; the textbook list is only a starting hypothesis.
2. **Assign tiers** (Epiminds synthesis of Geddes 2021 and McNair 2026):
   - Tier A, commercial-now: words converting at or below target CPA ("quote", "near me" with urgency, product + buy/price/emergency). Bottom of funnel (McNair/PPC Mastery, 2026).
   - Tier B, commercial-later: comparison and specific-solution terms converting above target but with value (comparison pages, loan-type comparisons Geddes says to serve rather than negate, 2025 via skill 10).
   - Tier C, research: "how", "what", cost-questions, tutorials — convert far above target or not at all (Geddes/Adalysis, 2021, 2022).
   - Brand and competitor: separate campaigns so they don't absorb generic budget (Hopkins/SEJ, 2019); brand on exact first (Vallaeys/Optmyzr, 2026).
3. **Unit of the tier.** Same campaign, separate ad group when the ad or landing page must differ (Geddes/Adalysis, 2022). Separate campaign only when (a) auction prices differ enough that one campaign budget cannot serve both (Hopkins/SEJ, 2019, 2024), or (b) the tier needs its own CPA/ROAS target. Do not give "near me" its own campaign by reflex — it needs its own budget and dilutes data density (Geddes/Adalysis, 2022).
4. **Per-tier bidding under Smart Bidding** (Hopkins/SEJ, 2024; Vallaeys/Optmyzr, 2026):
   - Tier A: its own campaign with the tightest tCPA/tROAS; tCPA/tROAS rather than Max strategies (Geddes/Adalysis, 2024).
   - Tier B: own campaign with a looser target if volume supports ~50 conversions/30 days (Vallaeys/Optmyzr, 2026); otherwise own ad group in the Tier A campaign with its own ad and landing page, and lower-value conversion actions so the bidder does not over-pay (Hopkins/SEJ, 2024).
   - Tier C: negative in conversion campaigns (Geddes/Adalysis, 2022), or a separate campaign with a research landing page and soft CTA only once Tier A is maxed (McNair/PPC Mastery, 2026). Expect high CTR, lower CVR, long windows (McNair/PPC Mastery, 2026).
   - Set conversion values even as placeholders and mark low-value actions secondary; compare value to CPA per tier to keep or cut (Hopkins/SEJ, 2024).
5. **Match type by tier and word count** (Hopkins/SEJ, 2019; Vallaeys/Optmyzr, 2026): Tier A single words exact only; two-word Tier A exact + phrase; three-word phrase + exact; broad only from five words and only in a gated discovery setup (skill 16). Brand exact-led.
6. **Auction-price check.** Within a campaign, keywords should sit close in CPC (Hopkins/SEJ, 2019, 2024). A Tier A word priced 5× the rest either gets its own campaign or a cheaper synonym ("lawyer" for "attorney"; Hopkins/SEJ, 2024).
7. **Expansion order.** Build and max Tier A first; move to Tier B/C only when Tier A impression share is capped or CPCs make the target impossible (McNair/PPC Mastery, 2026). Exceptions: new categories with no demand, long B2B cycles, awareness goals (McNair/PPC Mastery, 2026).
8. **Quarterly re-tier** (Epiminds operating cadence — no canon source; reason: the n-gram pass that feeds step 1 runs monthly, and three passes are needed before a word's CPA shift is treated as a trend rather than a month's noise). Re-run step 1; words migrate tiers as ads and pages change. A Tier C word that starts converting is moved up with its own ad group, not left to Google's matching (Geddes/Adalysis, 2021).

## What Google will tell you instead, and why we don't
Google's position is that Smart Bidding prices intent from signals, so manual tiering is unnecessary and consolidation into fewer campaigns and ad groups helps the bidder. The canon has a documented case where Smart Bidding never corrected a 3× CPA intent family with > 10,000 clicks of evidence (Geddes/Adalysis, 2022), Smart Bidding cannot see LTV, margin or deal size (Vallaeys/Optmyzr, 2026), and consolidation into mixed-intent ad groups degrades both matching and RSA relevance (Geddes/Adalysis, 2024, 2022). We encode intent in structure, values and negatives so the bidder cannot average it away.

## Failure modes
- **Low-volume accounts.** Splitting tiers into campaigns pushes each below ~50 conversions/30 days and breaks Smart Bidding (Vallaeys/Optmyzr, 2026); keep tiers as ad groups and use values.
- **Lead gen without value data.** Per-tier bidding via values needs at least placeholder values and primary/secondary separation (Hopkins/SEJ, 2024); without them Tier B/C are negatives or nothing.
- **Over-splitting.** Each campaign is another budget and rarely supports more than 5–7 ad groups (Hopkins/SEJ, 2020); Geddes warns that splits that don't change ad or page just dilute data (Adalysis, 2022).
- **Long-cycle B2B.** Tier C may be where deals start; McNair lists long cycles as an exception to bottom-up (PPC Mastery, 2026). Measure with lagged conversions before negating.
- **Textbook intent words.** The CPA effect of a word is account-specific; "today" was a losing word in one account (Geddes/Adalysis, 2025) and may not be in another. Step 1 is mandatory.
- **Shared landing pages.** Tiers on a shared page cannot be served differently; broad match reads the page (Google docs, 2026).

## What to measure
- CPA/ROAS per tier, monthly, against each tier's target.
- Share of spend in Tier C inside conversion campaigns (target: near zero).
- Tier A impression share (the trigger for expansion; McNair/PPC Mastery, 2026).
- CPC spread within each campaign (Hopkins/SEJ, 2019).
- Conversion value per tier vs CPA (Hopkins/SEJ, 2024).

## Open disagreements in the canon
- **Ad group or campaign as the tier unit.** Geddes (2022) favours data density and splits only for ad/page; Hopkins (2019, 2024) splits campaigns by auction price and journey. Epiminds: ad-group splits by default, campaign splits only for price/budget or target differences.
- **Does Smart Bidding learn intent?** Google says yes; Geddes (2022) documents a case where it never did. Epiminds does not rely on it; the structure carries the intent.
- **Research terms: negate or serve.** Geddes (2022) negates in conversion campaigns; McNair (2026) serves them later as a separate phase. Epiminds does both in sequence: negate in Tier A, serve in a Tier C campaign only after Tier A is maxed.
