---
name: brand-nonbrand-firewall
id: 5
description: Build the cross-campaign negative mesh that keeps brand queries out of non-brand Search, Shopping and PMax (and generic queries out of brand) so non-brand ROAS/CPA is measured clean. Not for deciding whether to bid on brand at all, and not a competitor-conquesting playbook.
tags: Structure / Search / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Brand exclusions reliably catching typos and variants and extending to Standard Shopping; removal of campaign-level negatives in PMax; AI Max replacing keyword Search so negatives stop gating serving.
---
## What this is
A firewall made of negatives, priorities and budgets, not of Google's brand lists. Brand and non-brand are the one split that always qualifies for separate campaigns because they perform differently enough to need different targets (Vallaeys/Walker, Optmyzr Town Hall, 2025). Blended automation leans into brand because it is cheap and converts, which creates a feedback loop that flatters blended ROAS (Humphrey/Search Engine Land, 2026 — agency case). The mesh makes sure every brand query lands in the brand campaign and nowhere else, across Search, Shopping and PMax.

## Where it comes from
Nils Rooijmans publishes the method for each surface: negatives with every variant and typo on top of PMax brand exclusions (2025), low-priority brand Shopping with negatives on non-brand (2025), and script-driven negatives rather than brand inclusions on Search (2023). Geddes documents why relying on Google's cross-campaign preference fails (Adalysis workshop, 2020). Vallaeys/Walker give the split rationale (Optmyzr, 2025). Humphrey's single-account case (SEL, 2026) and JumpFly's brand-bidding note (undated) are non-canon context.

## When to use it / when not to
Use when: brand terms appear in non-brand Search search-term reports; PMax search-term insights show a brand share that dominates conversions (Rooijmans, 2024); blended ROAS is high while non-brand volume is flat; Shopping campaigns have no priority logic so brand queries hit whichever campaign has budget.

Do not use when: the brand name is a generic word (e.g. a brand called "Shoes") — exact brand negatives will block generic demand; brand search volume is negligible (new brand) so there is nothing to firewall yet; the account has no Shopping or PMax and only one Search campaign (then the mesh is two negative lists and done).

## Inputs
- Brand term inventory: brand name, product names, sub-brands, every spelling variant, typos, domain, concatenations (Rooijmans, 2025).
- Competitor brand inventory (Google often does not recognise these as brands) (Rooijmans, 2025).
- Non-brand Search keyword export (for exact negatives into brand where needed).
- Search-term reports for all Search campaigns, 90 days; PMax search-term insights with the brand-share chart (Rooijmans, 2024).
- Shopping campaign list with priorities, budgets, products per campaign.

## Method
1. **Build two shared negative lists.** List A = brand terms + variants + typos, as phrase negatives. List B = competitor brands + variants (Rooijmans, 2025). Do not rely on brand exclusions alone: PMax search terms still show typo variants after a brand exclusion, and competitor brands are frequently unrecognised (Rooijmans, 2025).
2. **Search non-brand campaigns**: apply List A to every non-brand campaign, and List B unless the campaign is a competitor campaign. Do not assume Google routes the query to the brand campaign on its own — across campaigns it prefers the "most restrictive" match but rotates over time, which is why the same search term shows up in two campaigns (Geddes, 2020).
3. **Search brand campaign**: do not use brand inclusion as the only control — it requires the broad match campaign setting and has not been shown to be tighter than negatives (Rooijmans, 2023). Instead run a script that retroactively adds non-brand search terms seen in the brand campaign as negatives (Rooijmans, 2023). If the brand campaign is on exact/phrase brand keywords, add the top non-brand keywords as exact negatives as well (Humphrey/SEL, 2026; Geddes, 2020 — phrase campaigns carry exact negatives).
4. **Brand campaign bidding**: bid to impression share, not tROAS. Brand traffic is uniformly high-value, so tROAS has nothing to learn from; lowering a brand tROAS raised CPC with no gain in impressions or conversions in JumpFly's accounts (JumpFly, undated — agency). Geddes bids brand on target impression share (Geddes, 2020).
5. **Shopping**: create a brand Shopping campaign at *low* priority containing only the products you want on brand queries, with high manual CPC or a strategy that allows high CPCs; attach List A to every non-brand Shopping campaign (high/medium priority) (Rooijmans, 2025). Three conditions, or the firewall leaks: every product in the brand campaign also exists in the non-brand campaigns; non-brand budgets never run out before the brand budget, otherwise non-brand queries fall through to the low-priority brand campaign; schedule, device, audience and location settings are identical across them (Rooijmans, 2025). Do not build it the other way round (brand campaign matching broadly, scripting negatives out) — it loses money on non-brand clicks and hits negative-list limits because Google matches broadly (Rooijmans, 2025).
6. **PMax**: apply the brand exclusion where Google recognises the brand, *and* attach List A (and List B) as campaign-level negatives (Rooijmans, 2025). Use the exclusion scope that matches your intent — Shopping+Search inventory or Search only (SEL brand-settings write-up, undated). Note the campaign negative cap at the time of the SEL write-up (100); keep the list compact.
7. **Diagnose leakage on a fixed cadence** (Epiminds operating cadence — no canon source; reason: weekly until the search-term reports show no brand terms in non-brand campaigns, then monthly, because Rooijmans's brand-list maintenance is described as periodic and the leak sources — new typos, new competitor names — recur; Rooijmans, 2025). Run the PMax brand-traffic analyser and read the brand share of PMax conversions (Rooijmans, 2024). Treat "uncategorised" search terms as mostly non-brand but unverified (>90% by smec's estimate; smec, 2024) and remember the match logic is CONTAINS, so "brandx" also matches "brandxyz" (smec, 2024). Pull Search search terms segmented by campaign; any brand term in a non-brand campaign is a hole in List A.
8. **Output**: List A and List B with the campaigns they are attached to; the Shopping priority/budget table showing the three conditions hold; the PMax exclusion scope; and a baseline of non-brand ROAS/CPA measured *after* the mesh, which becomes the number you report.

## What Google will tell you instead, and why we don't
- Google offers brand inclusions/exclusions as the control (SEL brand-settings write-up, undated). They leak: typo variants still serve after a PMax brand exclusion, competitor brands are often not recognised as brands, and inclusion forces broad match (Rooijmans, 2023; 2025). We treat brand lists as a second layer under negatives.
- Google's structure guidance treats consolidation as the default. Brand vs non-brand is the explicit exception even among consolidation advocates (Vallaeys/Walker, 2025), and blended automation's brand bias is the reason (Humphrey/SEL, 2026).
- Google recommends tROAS/Max Conversion Value broadly. On brand, the canon bids impression share (Geddes, 2020) because tROAS has no signal to learn from and can raise CPC for nothing (JumpFly, undated).

## Failure modes
- **Generic-word brands**: phrase negatives on the brand term block real non-brand demand. Epiminds derived rule — no canon source; reason: an exact negative on the full brand phrase blocks only the literal brand query and leaves generic demand serving, at the cost of some leakage; it follows from Rooijmans's negative-list method (2025) applied where the brand word is also a category word.
- **Retail Shopping with budget-capped non-brand campaigns**: the moment non-brand runs out of budget, brand (low priority) catches generic queries at high CPCs (Rooijmans, 2025). Check "limited by budget" before trusting brand numbers.
- **Mixed product sets**: products only in the brand Shopping campaign will serve for generic queries because nothing higher-priority holds them (Rooijmans, 2025).
- **Accounts measured on blended ROAS by the client**: the firewall will make non-brand look worse and PPC revenue may fall while organic brand revenue rises — Humphrey's case went PPC −25%, organic +99%, combined +15%, new customers +20% in one year (Humphrey/SEL, 2026, single account). Agree the measurement change before the structural change.
- **PMax with over 100 negatives needed**: large multi-brand catalogues can exceed the campaign negative cap noted in the SEL write-up; prioritise own brand plus the highest-volume variants.
- **Reseller / multi-brand retailers**: manufacturer brands are not "your brand". Epiminds derived rule — no canon source; reason: List A exists to route *own-brand* queries (Rooijmans, 2025); adding manufacturer brands to it would negate the retailer's category traffic in every non-brand campaign.

## What to measure
- Brand share of PMax conversions and spend, trended weekly (Rooijmans, 2024).
- Count of brand search terms appearing in non-brand Search campaigns (target: zero; Epiminds operating threshold — no canon source; reason: any brand term in a non-brand campaign is by definition a hole in List A).
- Brand campaign impression share (target set per Geddes's impression-share bidding, 2020).
- Non-brand CPA/ROAS before vs after the mesh, reported separately from brand.
- Shopping non-brand "limited by budget" flags (any flag invalidates brand numbers that week; Rooijmans, 2025).

## Open disagreements in the canon
- **Which side carries the Shopping negatives.** Rooijmans puts brand negatives on non-brand campaigns and brand at low priority (2025); Humphrey puts non-brand keywords as exact negatives inside the brand campaign (SEL, 2026). Epiminds goes with Rooijmans: the brand term list is finite, the non-brand term list is not, so the finite list is the one you can maintain and keep under list limits.
- **Brand lists vs negatives.** Google and the SEL write-up position brand lists as the primary tool; Rooijmans treats them as a partial layer. Epiminds runs both, negatives first, because the only practitioner who tested PMax exclusions reports typo leakage (Rooijmans, 2025).
- **Whether brand should be on Smart Bidding at all.** The canon here is thin: Geddes (2020) and JumpFly (undated) argue impression-share/eCPC; no Tier 1 source in this dossier argues for tROAS on brand. Epiminds defaults to target impression share on brand and revisits if a cross-account study appears.
