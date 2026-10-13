# Dossier — 43 Micro-conversion ladder for new accounts

## Sources

1. **Source**: Will Gray, WebMechanix, published on Optmyzr — "How to make value-based bidding work for you", https://www.optmyzr.com/blog/make-value-based-bidding-work-for-you/ · **Tier** added-Tier-2 for this topic (publishes the ladder, a volume threshold and a documented negative result; departs from Google's "add more conversion actions") · **Date** 2024-12-10 (updated 2026-05-08) · **Claim**: Ladder order to optimise to as data allows: (1) standard form fill (pixel) → (2) qualified form fill (pixel) → (3) MQL (CRM import) → (4) SQL (CRM import) → (5) closed deal (CRM import). The rung you can optimise to depends on that action's volume and its time-to-convert; working rule ~45 conversions in the last 30 days for that action at the level the bid strategy sits. Add new rungs as *secondary* first to avoid overcounting (one user hitting form → MQL → SQL would count three times). Google's maximum conversion window is 90 days from click, which limits how deep a rung can be. Micro-conversions were tried when volume was too low for VBB: engagement actions rose, "no corresponding increase in downstream conversion actions". · **Evidence**: practitioner experience across agency accounts; charts as images; no sample size.

2. **Source**: Navah Hopkins, Optmyzr — "The Impact of PPC Bidding Strategies", https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ · **Tier** 1 · **Date** 2024-09-24 · **Claim**: 50+ conversions in 30 days is the threshold for predictable Smart Bidding; moving from <25 to 25–50 does not reliably improve results. Max Clicks is "acceptable and underused", the most efficient Auto strategy, and most Max Clicks advertisers are low-budget; in lead gen it produced some of the cheapest CPCs and strongest ROAS. Max Conversion Value without a target beat the targeted version. Manual CPC suits only actively managed accounts with strong volume. Low spend alone should not block Smart Bidding if conversion volume is sufficient. · **Evidence**: 14,584-account study.

3. **Source**: Frederick Vallaeys, Optmyzr — "Value-based bidding guide", https://optmyzr.com/blog/value-based-bidding-guide · **Tier** 1 · **Date** 2026-07-16 · **Claim**: Google's 15 conversions/30 days is an eligibility floor; practitioners want 30–50/month. Below that, use Max Conversion Value without a target to build history. Don't stack primaries in one funnel (values add up per journey). Fragmented campaigns leave late-stage actions with insufficient signal. · **Evidence**: method and support-ticket patterns; no study.

4. **Source**: Megan Mullarky, Metric Theory — "Bending the algorithms", https://metrictheory.com/blog/bending-the-algorithms-using-googles-target-roas-bidding-on-for-customer-acquisition-goals/ · **Tier** added-Tier-2 (see dossier 42) · **Date** 2021-03-05 · **Claim**: Value a micro-conversion at final value ÷ (1 ÷ its rate of leading to the final conversion): 20% quiz-to-subscribe at $150 LTV → $30. Only ratios matter. Placebo revenue ÷ cost sets the tROAS. · **Evidence**: one client YoY test (tROAS CPA −10%, conv +51% vs tCPA CPA +22%, conv −11%).

5. **Source**: Sarah Stemen, Search Engine Land — "Value-based bidding: why it's key", https://searchengineland.com/?p=437240 · **Tier** 2 · **Date** 2024 · **Claim**: Budget-constrained lead-gen accounts can value micro-conversions (feature-sheet download, video view) based on what sales knows leads to bookings, to give the algorithm enough data; illustrative $3/$10/$15 ladder against a $10,000 booking. · **Evidence**: hypothetical; cites Mackey and McNair as supportive.

6. **Source**: Fred Vallaeys & David Newson, Optmyzr PPC Town Hall — "What do you optimize for when the sale happens 2 years later?", https://www.optmyzr.com/ppctownhall/optimize-ppc-long-sales-cycles · **Tier** 1 host, guest anecdote · **Date** 2026-08-12 · **Claim**: An engaged-visit threshold (six minutes on a wealth-management site) was used as an intent marker with ">80% confidence" of in-market status; Fred argues a signal fed back within ~2 weeks steers bidding, waiting 90 days doesn't. · **Evidence**: single-advertiser anecdote, no numbers beyond the stated confidence.

7. **Source**: Brad Geddes, Adalysis — "What's the most popular Google Ads bid strategy?", https://adalysis.com/blog/whats-the-most-popular-google-ads-bid-strategy/ · **Tier** 1 · **Date** 2025-11-11 · **Claim**: Across 16,825 non-brand Search campaigns (3 months, 2025), Max Conversions is by far the most common strategy; tCPA only exceeds 50% usage above 1,000 conversions/month. Max Conversions suits campaigns under 10 conversions/month. For low-volume campaigns he suggests treating a "quality visit" (defined by an event or time on site) as a conversion so the campaign can use tCPA or Max Conversions; Max Clicks users without conversion data can use an interaction goal. Campaigns on tCPA/tROAS without reliable tracking should fix tracking or switch. · **Evidence**: cross-campaign usage data; the quality-visit advice is opinion.

## Dissenting view
Geddes (2025) sits with the pro-micro-signal camp — a "quality visit" as a conversion for low-volume campaigns — but gives no result for it. Gray (2024) is the direct dissent against the whole idea: in his accounts, bidding to micro-conversions produced more micro-conversions and no more sales. Stemen (2024) and Newson (2026) say micro-signals chosen *by the sales team* for predictive power do work. The disagreement is about whether the micro-action is a cause or a correlate of buying: a feature-sheet download selected because it predicts bookings is a different signal from "time on site" picked because it has volume.

## What the platform currently does [Google docs]
- [Google docs] tCPA/tROAS eligibility is 15 conversions in 30 days on Search; Max Conversions / Max Conversion Value have no stated floor (per Vallaeys 2026).
- [Google docs] Primary vs secondary conversion actions: only primary actions feed bidding; secondaries are reported only (per Gray 2024 and Vallaeys 2026, both citing Google's conversion settings).
- [Google docs] Maximum click-through conversion window is 90 days (per Gray 2024).
- [Google docs] Google's Recommendations tab routinely suggests "add conversion actions" and "use Maximize Conversions" on low-volume accounts; its bid-strategy report flags "limited (not enough data)" — labelled from practitioner descriptions, not fetched.

## Baseline check
Read `google-ads-bidding` ("0–10 conv/month → Manual CPC; 10–30 → Max Conversions or Manual") and `google-ads-conversion-tracking` ("exclude micro-conversions or they pollute the signal"). The baseline forbids micro-conversions as bidding signals and prescribes Manual CPC at low volume. This skill adds: Hopkins' evidence that Manual CPC is wrong at low volume and Max Clicks is the efficient start; the one-primary-rung ladder with Gray's ~45/30-day graduation threshold; the secondary-first rule; the ratio-valuation of a rung; and Gray's negative result as a guard rail on which micro-actions qualify.

## Judgment calls
- Gray/WebMechanix added as topic-scoped Tier 2 (method + threshold + a published negative result).
- Took the position that only one rung is primary at a time and that a micro-action qualifies only if the client's own data shows it precedes a sale at a known rate; otherwise Max Clicks + landing-page work is the honest option (Hopkins).
- The index row says "Setup / New" but the useful evidence comes from lead-gen accounts; the skill is written for lead gen and low-volume ecommerce alike, with the ecommerce note that add-to-cart is the only micro-action with a known ratio.

## Canon strength: Adequate
Two Tier 1 (Hopkins with cross-account data; Vallaeys method) plus two added Tier 2 with account results, one of them negative.

## Invalidated by
Google removing the primary/secondary distinction, changing the Smart Bidding data floors, or retiring Maximize Clicks.
