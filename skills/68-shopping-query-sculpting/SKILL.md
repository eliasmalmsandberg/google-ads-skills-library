---
name: shopping-query-sculpting
id: 68
description: Build and maintain the priority-plus-negatives structure that routes generic, brand and SKU queries to separate Standard Shopping campaigns with their own bids and targets, and diagnose why it leaks. Use when you want generic vs brand vs product queries bid differently. Not for custom-label design (64) or PMax asset-group structure.
tags: Technique / Shopping / Optimise / Established / As needed
last_verified: 2026-10-13
invalidated_by: Google removing campaign priority from Standard Shopping, forcing PMax precedence without brand exclusions, removing shared budgets, or AI Max for Shopping replacing keyword-free matching with its own query rules.
---
## What this is
Shopping has no keywords, so the only way to pay differently for "running shoes", "nike running shoes" and "nike pegasus 41 black 10.5" is to put the same products in three campaigns and use priority plus negatives to push each query to the campaign meant for it (Williams/ZATO, 2015/2026, crediting Roettgerding 2014). The direction is counter-intuitive and the baseline gets it backwards: the *generic* campaign is High priority with the *lowest* bids, the *SKU* campaign is Low priority with the highest (Williams/ZATO, 2026). Rooijmans' audits find the structure fails not because Google ignores priority but because of four setup errors (Rooijmans, 2026).
See also: skill 5 (brand-nonbrand-firewall) — the brand/non-brand negative lists and the low-priority brand Shopping campaign as part of an account-wide firewall.

## Where it comes from
Kirk Williams' query-sculpting walkthrough (Search Engine Land 2015, maintained on ZATO to 2026), his SMX 2016 "four pillars", the 2026 large-catalogue two-lane variant and his 2026 account theory on PMax and brand (Williams/ZATO); Nils Rooijmans' audit of why priorities "don't work" (Rooijmans, 2026); Fred Vallaeys on priority campaigns for labelled products (Vallaeys/PPC Hero, 2015).

## When to use it / when not to
Use when: Standard Shopping is running (or PMax with brand excluded so brand/SKU demand can be sculpted into Standard Shopping) (Williams/ZATO, 2026); the search-term report shows brand and SKU queries converting at materially different rates from generics (Williams/ZATO, 2026); budget and volume are enough that three tiers will each collect data (Williams/ZATO, 2026). Do not use when brand traffic is negligible — use the conversion-based variant in step 8 instead (Williams/ZATO, 2026); on Microsoft Ads without shared budgets the method leaks (Williams/SMX, 2016); and do not add it to an account whose feed is weak — a simpler campaign on a strong feed beats a complex one on bad data (Williams/ZATO, 2026).

## Inputs
- Search-term report for the existing Shopping campaign, segmented "contains brand" vs "does not contain", with conversions and CPA (Williams/ZATO, 2026).
- Brand list, product-name list and SKU/Item ID list for negatives (Williams/ZATO, 2026).
- One shared budget (Williams/ZATO, 2026).
- Identical targeting settings across all tiers: device, location, schedule, audience, demographics, language, network, IP exclusions, country of sale (Rooijmans, 2026).

## Method
1. **Decide from the SQR.** Compare "contains brand" vs "does not contain" (Williams' example: 100 conversions at $40 CPA vs 450 at $50). If the two populations differ in CPA or ROAS, build the tiers; if not, stop (Williams/ZATO, 2026).
2. **Convert, don't create.** Turn the existing campaign into the Non-brand (NB) tier to keep its history (Williams/ZATO, 2026). Set priority High, bids low (example $0.50, or a tROAS matching what generic queries can bear), negatives = every brand term and every SKU/product-name term (Williams/ZATO, 2026).
3. **Copy NB → Brand (BR).** Priority Medium, same shared budget, delete the copied brand negatives, keep SKU and product-name terms as negatives, bids higher (example $2.00; manual if you want to own brand) (Williams/ZATO, 2026). Forgetting to delete the copied brand negatives "will end up destroying your entire strategy" (Williams/ZATO, 2026).
4. **Copy NB → SKU.** Priority Low, same shared budget, remove brand and SKU negatives, add only proven junk negatives ("parts", "used"), bids highest (example $5, up to $10–15 where CVR supports first position) (Williams/ZATO, 2026).
5. **Shared budget, always.** One shared budget across the three so a higher tier never runs out and lets queries bypass it (Williams/ZATO, 2026; Rooijmans, 2026).
6. **Targeting parity and product parity.** Every setting in the input list must match across tiers, and every tier must be eligible for the same product set; any mismatch drops the query to a lower tier and you pay the higher bid for a generic query (Rooijmans, 2026). Uncheck "all products" and build ad groups by product line with Item ID exclusions, keeping products in the same ad group so their data persists (Williams/ZATO, 2026).
7. **Negative propagation rule.** A negative added to NB must be added to BR and SKU; a negative added to BR must be added to SKU. Otherwise the query filters down and costs more (Williams/ZATO, 2026). Add a junk exact-match negative (Williams' example [-m]) to all tiers to catch dangling matches (Williams/SMX, 2016).
8. **Negligible-brand variant.** If brand queries are rare, run NB (High) and a Medium campaign; negate *converting* queries out of NB so they fall to Medium with higher bids (Williams/ZATO, 2026).
9. **Large-catalogue variant.** Keep lane 1 (top performers on generic queries) untouched; pick one brand or category to grow and build lane 2: a High-priority low-bid campaign catching generics plus a campaign that negates generics and bids on specific high-intent terms (Williams/ZATO, 2026).
10. **PMax coexistence.** Exclude brand from PMax so brand and SKU demand can be sculpted into Standard Shopping; sculpting *between* PMax campaigns is "the Wild West" (Williams/ZATO, 2026). PMax CPCs typically run lower; the justification for Standard Shopping tiers is tier-specific ROAS targets instead of one blended goal (Williams/ZATO, 2026). Exact-match Search campaigns outrank PMax for the same query, and a budget-limited Search campaign lets PMax take its terms [Google docs].
11. **Maintenance.** Weekly: SQR per tier; if a brand/SKU query appears in NB, fix negatives per step 7 first and targeting parity per step 6 second (Rooijmans, 2026). Give it months, not weeks — Williams describes the payoff as a jumbo jet, not a propeller plane (Williams/ZATO, 2026).

## What Google will tell you instead, and why we don't
Google's direction is consolidation into PMax or AI Max for Shopping with one blended target (Williams/ZATO, 2026) [Google docs: PMax as the single retail campaign]. The canon splits the same products three ways to pay generic, brand and SKU queries what each is worth, and Williams' two manufacturer cases showed CVR +21% and +168% after sculpting (with cost and traffic also rising) (Williams/ZATO, 2026). Google's help says PMax brand exclusions exist to "prevent overlaps" [Google docs]; we use them to *create* the overlap we want — brand and SKU in Standard Shopping where the bid is ours.

## Failure modes
- **Budget-constrained upper tier.** The most common leak in Rooijmans' audits: NB runs out, generic queries fall into BR/SKU at high bids (Rooijmans, 2026).
- **Any targeting delta between tiers** (a device bid adjustment, an audience, a schedule) silently reroutes queries (Rooijmans, 2026).
- **Bids too low on High priority.** Bids can override priority: a High-priority campaign bid below the auction floor just doesn't show (Williams/SMX, 2016).
- **Microsoft Ads import.** No shared budget → generic queries leak into the high-bid tiers (Williams/SMX, 2016; Williams/ZATO, 2026).
- **Negligible brand, small accounts.** Three tiers starve; use step 8 (Williams/ZATO, 2026).
- **Over-segmentation.** Ad groups by size and colour on a large catalogue become unmanageable and slow to accumulate data (Williams/ZATO, 2026).
- **Stock-outs on hero SKUs.** A month-long stock-out reversed one of Williams' results; the SKU tier is where this shows first (Williams/ZATO, 2026).
- **Cannibalisation.** New campaigns pull traffic from proven products; the method stated intent is to separate queries, not add campaigns (Williams/ZATO, 2026).

## What to measure
- Per tier: share of queries that belong there (brand share in NB should trend to zero), CPA/ROAS, CVR (Williams/ZATO, 2026).
- Budget utilisation of the High tier daily — hitting cap is the leak signal (Rooijmans, 2026).
- Cost and traffic overall: expect both to rise with higher-CPC auctions; judge on revenue and tier ROAS, not CPC (Williams/ZATO, 2026).
- AOV by tier — it sometimes falls while revenue rises (Williams/ZATO, 2026).

## Open disagreements in the canon
- **Exclude brand from PMax?** The sculpting guide says yes (Williams/ZATO, 2026); Williams' later account theory says PMax was efficient on brand in ZATO's tests and fighting it didn't help (Williams/ZATO, May 2026). Epiminds: exclude brand from PMax only when the SQR (step 1) shows brand and SKU queries deserve a distinct target; otherwise let PMax keep brand and run NB-only sculpting.
- **Complexity vs feed.** Williams' feed-first position says a simple campaign on a strong feed can win (2026); his sculpting guide adds three campaigns. We require a clean feed (65/67) before building tiers.
- **Priority "broken".** Practitioners who say Google ignores priority are, in Rooijmans' audits, always looking at one of the four setup errors (Rooijmans, 2026). We treat "priority ignored" as a diagnosis prompt, not a platform bug.
