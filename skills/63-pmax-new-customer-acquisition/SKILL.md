---
name: pmax-new-customer-acquisition
id: 63
description: How Google defines a "new customer" in the customer acquisition goal, why the value premium corrupts reported ROAS, and which mode and definition to use when a client wants to pay more for new customers. Not for retention/re-engagement goals or for building Customer Match lists.
tags: Strategy / PMax / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: A change to the 540-day auto-detection window; removal of the Original conv. value column; the premium becoming bidding-only (non-reporting); in-platform incrementality testing for lifecycle goals; removal of New Customer Only mode.
---
## What this is
The customer acquisition goal has a definition problem and a reporting problem. Definition: "new" means a purchaser with no tracked conversion in the last 540 days, not a new visitor and not someone outside your remarketing lists (Williams/ZATO, 2021/2026) [Google docs]. Reporting: in the default "bid higher" mode the premium you assign is added to Conv. value — a $100 sale with a $50 premium reports $150 — so ROAS rises on invented revenue (Williams/ZATO, 2021/2026). This skill is the rule for using the goal without either problem reaching the client's numbers.

## Where it comes from
Kirk Williams (ZATO, 2021 updated 2026; 2026 settings post; 2023 structures) for the mechanics and the position; PPC Mastery (McNair, 2026) for the nCAC/LTV frame that justifies paying more for new customers; Fred Vallaeys (Optmyzr, 2026) for value-integrity rules; Google's lifecycle docs for current behaviour.

## When to use it / when not to
Use when a client with repeat purchase behaviour wants acquisition priced on LTV — PPC Mastery's frame: acquisition cost is for new customers only, and a 3:1 LTV:nCAC on profit is the healthy benchmark (McNair/PPC Mastery, 2026). Do not use when the existing-customer list is under 1,000 members (Google says this reduces the goal's success) [Google docs], when purchase tracking is incomplete (auto-detection then mislabels returning buyers as new), or for one-off-purchase products where "new" and "any" are the same thing.

## Inputs
- Existing-customer Customer Match list(s): size, source (CRM/API/GA4/upload), refresh cadence [Google docs].
- Whether the new_customer tag parameter is implemented on the conversion tag [Google docs].
- Account-level lifecycle settings: existing-customer definition and the first-purchase value (Williams/ZATO, 2026).
- Per-campaign: whether "Adjust your bidding to help acquire new customers" is checked (Williams/ZATO, 2026).
- Columns: Conv. value, Original conv. value, New customers, CAC, New customer lifetime value [Google docs].

## Method
1. **Fix the definition before the mode.** Do not rely on Google's 540-day auto-detection alone; it is built from tracked purchases and loses coverage to cookie deletion and opt-outs [Google docs]. Use a Customer Match list of all purchasers (≥1,000 members) plus the tag parameter, which overrides auto-detection and is Google's own recommended way to shrink the Unknown and Returning gaps [Google docs]. Williams' instruction: add multiple customer lists including remarketing lists (Williams/ZATO, 2021/2026).
2. **Audit the inflation already present.** Compare Conv. value with Original conv. value per campaign. If Conv. value is significantly higher, a lifecycle adjustment or value rule is inflating the reported number; Original conv. value is the ground truth (Williams/ZATO, 2026). Also check for value stacking — more than one primary purchase action counting the same sale (Vallaeys/Optmyzr, 2026). Do this before any client report mentions new-customer counts (Williams/ZATO, 2026).
3. **Choose the mode.**
   - Default: campaign checkbox unchecked; bid equally; report new vs returning with the New customers and CAC columns (Williams/ZATO, 2026) [Google docs].
   - Client insists on paying more for new customers: use **New Customer Only** in a separate campaign with a nominal $0.01 value and its own tROAS, and run existing customers in another campaign with a higher target — Williams' illustration is 2× new vs 5× repeat (Williams/ZATO, 2021/2026, 2023). Google itself says to run a separate campaign for existing customers in this mode [Google docs].
   - Never use the **New Customer Value** premium as a reporting number. If a bidding premium is wanted for a test, check the box, but report Original conv. value and label the test (Williams/ZATO, 2026).
4. **Size the premium from LTV, not from Google's suggestion**, if a premium is used at all: set tROAS from margin and deal economics (Vallaeys/Optmyzr, 2026) and bound the new-customer target by LTV:nCAC — headroom "up to ~4× but not always" in McNair's example (McNair/PPC Mastery, 2026).
5. **Accept the leak.** "New customers only" ads still reach returning customers for privacy and technical reasons [Google docs]; the New/Returning/Unknown split in reporting tells you how much. If Unknown exceeds a fifth of purchases, fix the tag parameter before judging the campaign.
6. **Judge after one to two conversion cycles** (Vallaeys/Optmyzr, 2026), on Original conv. value and CAC, never on the adjusted value. Lifecycle metrics are not backfilled, so the comparison window starts when the goal was activated [Google docs].
7. **Incrementality is yours to prove.** Google Ads offers no incrementality test for lifecycle goals [Google docs]; use a pre/post or geo split in your own analytics.

## What Google will tell you instead, and why we don't
Google recommends the New Customer Value (bid-higher) mode for every advertiser with a purchase goal and defaults detection to its own 540-day window [Google docs]. We don't, because the premium is added to reported conversion value and ROAS — "made-up" revenue in Williams' phrase, and a lever an agency could pull to flatter results (Williams/ZATO, 2021/2026) — and because auto-detection is the least complete definition Google itself documents [Google docs]. Separate campaigns with separate targets deliver the bidding intent without the accounting problem (Williams/ZATO, 2023).

## Failure modes
- **Lists under 1,000 members**: Google warns the goal underperforms [Google docs]; wait and build the list.
- **Incomplete purchase tracking or no tag parameter**: returning buyers are labelled new; the premium is paid on repeat customers (Williams/ZATO, 2021/2026).
- **Low repeat-rate products**: nCAC equals CAC; the goal adds complexity for nothing (McNair/PPC Mastery, 2026).
- **Agencies reporting Conv. value**: inflated ROAS goes to the client unlabelled (Williams/ZATO, 2026).
- **High Value New Customer beta**: Customer Match only, no auto-detection; needs a defined high-value list [Google docs].
- **Non-US accounts expecting 1st-order promotions**: US-only [Google docs].

## What to measure
Conv. value ÷ Original conv. value per campaign (target 1.0 unless a labelled test). New customers, CAC and nCAC monthly; share of Unknown in the New/Returning segment. LTV:nCAC on profit vs the 3:1 benchmark (McNair/PPC Mastery, 2026). Existing-customer list size and refresh date.

## Open disagreements in the canon
PPC Mastery (2026) argues for paying more for new customers on LTV grounds; Williams (2021–2026) rejects Google's premium because it distorts reporting, not because paying more is wrong. Epiminds takes both: bid differently through separate campaigns and targets, and never let the premium into a reported number.
