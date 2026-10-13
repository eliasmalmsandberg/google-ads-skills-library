# Dossier — 63 New customer acquisition goal — definition problem

## Sources

1. **Source**: Kirk Williams, ZATO, "Read before using New Customer Acquisition in Google Smart Shopping campaigns" (adapted for PMax) — https://zatomarketing.com/blog/read-before-using-new-customer-acquisition-in-google-smart-shopping-campaigns · **Tier** 1 · **Date** 2021-08-31, updated 2026-07-10 · **Claim**: NCA classifies purchasers, not visitors: "new" = no tracked conversion in the past 540 days; it does not identify new visitors or exclude remarketing. The value premium is added to reported conversion value ($100 sale + $50 premium reports $150) so ROAS is inflated with "made-up" revenue; an agency could use it to inflate results. Prefers separate ROAS targets for new vs returning (e.g. 2× new, 5× repeat) and segmented real-revenue reporting. Test with New Customers only at a $0.01 value; add multiple customer and remarketing lists; add the new-customer columns. Google's response to the concern: "crickets". · **Evidence or opinion**: Mechanism analysis + experience; no figures.

2. **Source**: Kirk Williams, ZATO, "How to untangle Google Ads New Customer Value: the settings, checkbox, and true ROAS" — https://zatomarketing.com/blog/how-to-untangle-google-ads-new-customer-value-the-settings-checkbox-and-true-roas · **Tier** 1 · **Date** 2026-07-10, updated 2026-07-20 · **Claim**: Since 2023 NCA is configured at account level (definition of existing customers + value for a first purchase) and Google tracks new vs returning for all campaigns; the campaign checkbox "Adjust your bidding to help acquire new customers" decides whether the value affects bidding. Unchecked: equal bidding, Conv. value untouched (New Customer Lifetime Value column still shows large observational numbers). Checked: premium added to Conv. value and ROAS as a bidding signal. Ground truth is "Original conv. value"; if Conv. value exceeds it significantly, an adjustment is inflating. Keep the box unchecked unless you intend the inflation; check Conv. value vs Original conv. value before acting on NCA counts or emailing clients. · **Evidence or opinion**: UI mechanics; experience.

3. **Source**: Kirk Williams, ZATO, "7 ways to structure PMax" — https://zatomarketing.com/blog/how-to-structure-performance-max-campaigns-7-ways · **Tier** 1 · **Date** 2023-08-22, updated 2026-04-21 · **Claim**: NCA structure (#6) for advertisers worried about new vs returning mix: customer lists excluded; add a nominal $0.01 value; the required added value "misrepresents true(r) revenue"; prefers ROAS targets. · **Evidence or opinion**: Method/opinion.

4. **Source**: Miles McNair, PPC Mastery, "TPE #148: The LTV Flywheel" — https://www.ppcmastery.com/newsletter/tpe-148-the-ltv-flywheel · **Tier** 1 · **Date** 2026-07-06 · **Claim**: Optimise to nCAC (acquisition cost for new customers only; returning buyers who would have bought anyway are not acquisitions); a 3:1 LTV:nCAC on profit is generally healthy; LTV headroom can justify bids up to ~4× higher but not always; client example CAC €50, AOV €125, ROAS 250%, margin <10%, repeat rate 1.1. · **Evidence or opinion**: Framework with one client example.

5. **Source**: Frederick Vallaeys, Optmyzr, "Value-Based Bidding: How It Works, When to Use It, and Why It Fails" — https://www.optmyzr.com/blog/value-based-bidding-guide/ · **Tier** 1 · **Date** 2026-07-16 · **Claim**: Value stacking (several primary actions on one sale) inflates value; choose one primary action; set tROAS from margin and deal economics; wait one to two conversion cycles before judging. Conversion value rules support only location/audience/device. · **Evidence or opinion**: Method.

6. **Source**: Navah Hopkins / Optmyzr guide — https://www.optmyzr.com/guide/performance-max/ · **Tier** 1 · **Date** 2026 · **Claim**: Nothing on NCA (recorded as a gap).

## Dissenting view
Google's docs recommend the "New Customer Value" (bid-higher) mode for all advertisers with purchase goals; Williams rejects the premium outright and wants separate targets. PPC Mastery's nCAC framing supports bidding more for new customers on LTV grounds — i.e. agrees with the *intent* of the premium while Williams objects to how it is reported. The disagreement is reporting integrity vs bidding signal.

## What the platform currently does [Google docs]
- Modes: New Customer Value (bid higher for new; Google recommends for all purchase advertisers), High Value New Customer (beta; Customer Match lists only), New Customer Only (bid only for new; recommended only for strict acquisition budgets or non-purchase goals; run a separate campaign for existing customers). Value-based bidding required for the first two; New Customer Only also supports Max Conversions/tCPA (https://support.google.com/google-ads/answer/12080169).
- Detection: Google auto-detection from up to 540 days of tracked purchases (default; incomplete due to cookie loss), Customer Match lists (CRM, API, GA4, upload), tag-based lists (Protected Audience API); methods can be combined; a list under 1,000 members may reduce success; up to 100 lists per goal (https://support.google.com/google-ads/answer/14005876).
- Tag parameter (new_customer) overrides auto-detection and is Google's recommended way to reduce Unknown/Returning gaps (https://support.google.com/google-ads/answer/15597581, /answer/12077475).
- Reporting: New customers (distinct), CAC, New customer lifetime value (= the value adjustment; e.g. 5 × $25 = $125), Original conv. value (unadjusted); segments New / Returning / Unknown; metrics not backfilled; "new customers only" ads may still reach returning customers; Google Ads has no incrementality test for lifecycle goals (https://support.google.com/google-ads/answer/15597581).
- 1st-order promotions pairing available in the US only.

## Baseline check
Read `google-ads-audit-ecommerce` (retargeting funnel, past purchasers cross-sell; no NCA content) and `google-ads-bidding` not assigned. This skill adds the 540-day purchaser definition, the premium's effect on reported value, the Original conv. value check, the list-size and tag requirements, and the position on which mode to use.

## Judgment calls
- Canon strength is borderline: Williams is the only Tier 1 source with mechanism-level detail; PPC Mastery and Optmyzr supply the LTV/value-integrity frame. Rated Adequate because the mechanism claims are verifiable against Google docs and three Tier 1 sources touch the decision.
- Position: never use the value premium as a reporting number; use New Customer Only or an unchecked bidding box with separate campaigns/targets; define "new" via Customer Match + tag, not auto-detection alone.
- Unknown > one-fifth of purchases as the "fix the tag first" trigger is an Epiminds rule: Google names the tag parameter as the remedy for Unknown gaps; the 20% level is where the New/Returning split stops supporting a CAC read. No canon number exists.

## Canon strength: Adequate

## Invalidated by
Google changing the 540-day window, removing the Original conv. value column, making the premium non-reporting, adding in-platform incrementality testing for lifecycle goals, or removing New Customer Only mode.
