---
name: seasonality-adjustments-vs-data-exclusions
id: 44
description: Use when a Smart Bidding account has a short sale coming, or has just had a tracking outage, and someone wants to "tell the algorithm". Decides whether to use a seasonality adjustment (usually no), a data exclusion (usually yes), or neither. Not for long seasonal periods, budget planning, or manual-CPC accounts.
tags: Technique / All / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google changing seasonality-adjustment duration guidance or the 0.1–10 modifier range, changing data exclusions to conversion-based rather than click-based, or new cross-account evidence that adjustments on mainstream events stopped inflating CPCs.
---
## What this is
Two Smart Bidding controls that look similar and behave oppositely. A seasonality adjustment tells the bidder "conversion rate will be X× for these days" and the bidder believes you; a data exclusion tells it "ignore the clicks from these days" and the bidder forgets them. The evidence is lopsided: across three BFCM seasons and up to ~6,000 accounts a year, advertisers who set a seasonality adjustment saw CPC inflation roughly double (+32–37% vs +16–17%) and ROAS fall 10–17% every year, while those who did nothing held ROAS (Vallaeys/Optmyzr, 2025). Exclusions have no comparable downside when set correctly — the failure mode there is setting the window on conversions instead of clicks (Rooijmans, 2025).

## Where it comes from
Vallaeys' three-year BFCM study (2025) and the Optmyzr 2026 peak-season data (Padmanaban, 2026) for seasonality; Rooijmans (2025) for the mechanics of exclusions; Google's API and Help docs (2026) for the limits; Vallaeys (2026) for the post-Aug-2026 restraint.

## When to use it / when not to
Seasonality adjustment — use only when *all* hold: the event is one Google has no history of for this account (a first-ever flash sale, an email-only promo, a clearance), it lasts ≤7 days, and you have a defensible CVR multiplier from a comparable past event (Vallaeys/Optmyzr, 2025; Google Ads API docs, 2026). Never for BFCM, Christmas, Valentine's or any event the bidder has seen for years (Vallaeys/Optmyzr, 2025).

Data exclusion — use whenever conversion tracking was broken, double-firing or missing for a day or more on a conversion- or value-based strategy (Google Ads Help, 2026). Don't use as a reaction to a bad week with intact tracking, and don't add one because of the 17 Aug 2026 bidding change (Vallaeys/Optmyzr, 2026).

## Inputs
- Event dates and whether the account ran the same event last year
- For a novel event: a CVR multiplier from the closest comparable promo (own data)
- For an outage: the exact affected dates and share of conversions affected; the account's conversion-lag distribution (p70, p90 days from click)
- Current targets, budgets, and breakeven ROAS (1 ÷ gross margin — Padmanaban/Optmyzr, 2026)

## Method
1. **Classify the trigger.** (a) Upcoming promo → go to 2. (b) Tracking problem → go to 5. (c) "Performance looks off" with intact tracking → neither tool; go to skills 46/49.
2. **Mainstream event test.** If the account ran this event in a prior year, the bidder has the history: do nothing to bidding (Vallaeys/Optmyzr, 2025). Observed BFCM CVR lift without any adjustment was +17.5%, +11.9%, +7.5% across 2022–2024 — shrinking, which is why a fixed multiplier overshoots (Vallaeys/Optmyzr, 2025). Spend the effort on guardrails: CPC anomaly alerts, pacing monitors, bid caps (Vallaeys/Optmyzr, 2025; skill 40).
3. **Novel event test.** If no history: set a seasonality adjustment at campaign or channel scope for ≤7 days (Google Ads API docs, 2026), with the multiplier from your comparable event, discounted — guessing +50% when it's +40% overbids ~7% for the whole window (Vallaeys/Optmyzr, 2025). Remove it the day the promo ends. Never extend past 14 days (Google Ads API docs, 2026).
4. **Efficiency room check** before any peak play: if (usual tROAS − breakeven ROAS) is under ~20 points, there is no room to chase volume; if ROAS is holding 50+ points above breakeven and stock allows, raise daily budgets 20% instead of touching bidding (Padmanaban/Optmyzr, 2026). Budget changes take 2–3 weeks to settle (Hopkins/Optmyzr, 2024), so do it before the event, not during.
5. **Outage: define the click window, not the conversion window.** Exclusions apply to clicks; conversions attributed to excluded clicks are dropped (Google Ads Help, 2026; Rooijmans, 2025). Start the exclusion *before* the outage by the account's conversion lag: tracking broken 12–14 Oct with a ~2-day typical lag and >30% of conversions lagging over a day → exclude 10–14 Oct (Rooijmans, 2025). Rule: start = first broken day − p70 lag days. Aim to cover ≥90% of affected clicks (Google Ads Help, 2026).
6. **Apply once, never remove.** Removing an applied exclusion causes more disruption than leaving it (Google Ads Help, 2026). Don't backfill conversions for bidding; reporting backfill is possible ≥5 days later (Google Ads Help, 2026).
7. **Re-set targets after the exclusion.** Bids and spend may drop; if a week or more of clicks was excluded, expect 1–2 conversion cycles of fluctuation (Google Ads Help, 2026). Loosen tROAS/tCPA by no more than ~10% (Hopkins/Optmyzr, 2024) and restore it after the cycle, or the account overspends (Google Ads Help, 2026).
8. **Annotate everything** — snapshot settings and date every adjustment or exclusion so the lag doesn't make the change date look like a performance cliff (Vallaeys/Optmyzr, 2026).

## What Google will tell you instead, and why we don't
Google positions seasonality adjustments as the correct tool for any expected 1–7 day conversion-rate change (Google Ads API docs, 2026), which in practice means "set one before your sale". We don't: on events the bidder has already seen, the adjustment doubled CPC inflation and cost 10–17 points of ROAS three years running (Vallaeys/Optmyzr, 2025). Revenue was higher with adjustments (+40–53% vs +25–34%), so the tool is defensible only when the brief is volume regardless of efficiency (Vallaeys/Optmyzr, 2025) — say so to the client in those words. On exclusions we follow Google's mechanics but go further than its UI, which lets you set the window on the broken days alone: the window must be widened by the conversion lag or you leave the damage in (Rooijmans, 2025).

## Failure modes
- **Mainstream retail peaks** (BFCM, Christmas, Valentine's for gifting): adjustments hurt (Vallaeys/Optmyzr, 2025).
- **Long promos** (>14 days): the adjustment degrades; the bidder should relearn instead (Google Ads API docs, 2026).
- **Thin-margin accounts** where target minus breakeven is <20 points: no room for any peak play (Padmanaban/Optmyzr, 2026).
- **Lead gen with multi-day lag** and an exclusion set only on the broken days: the pre-outage clicks that converted into the broken period stay in the model (Rooijmans, 2025).
- **Manual CPC / Max Clicks campaigns**: exclusions do nothing — conversion- and value-based strategies only (Google Ads Help, 2026).
- **Hotel/Travel campaigns**: exclusions unsupported (Google Ads Help, 2026).
- **Panicking after a bad week**: an exclusion with intact tracking throws away real signal and triggers 1–2 cycles of fluctuation for nothing (Google Ads Help, 2026).

## What to measure
Promo window: CPC vs the prior week (29–46% above is normal at BFCM without any adjustment — Padmanaban/Optmyzr, 2026), ROAS vs breakeven, CVR vs last year's event. Post-exclusion: daily spend and bid-strategy status for 1–2 conversion cycles; target restored on schedule. Always on: a CPC anomaly alert at campaign level (Vallaeys/Optmyzr, 2025).

## Open disagreements in the canon
- **Who predicts the lift.** Google's tooling assumes the advertiser; Vallaeys' data says the bidder, for known events. Epiminds: bidder for known events, advertiser (discounted) for novel ones ≤7 days.
- **Revenue vs efficiency.** Adjustments did raise revenue. We default to efficiency and switch only on an explicit volume brief.
- **How wide to set an exclusion.** Google says cover ≥90% of affected clicks; Rooijmans widens by observed lag. We use p70 lag as the start offset, and p90 for accounts where more than 30% of conversions lag over a day.
