---
name: pinning-strategies
id: 24
description: Decide how much of an RSA to pin — none, partial, hybrid or full — from ad group volume and message-control needs, with the measured cost of each level. Not for the mandatory-disclaimer case (32) or for writing the lines (23).
tags: Strategy / Search / Optimise / Any / As needed
last_verified: 2026-10-13
invalidated_by: Change to which positions are guaranteed to show (H1/H2/D1); pins allowed beyond three headline positions; unpinned serving made mandatory under AI Max.
---
## What this is
A decision rule for pin level. Google says pinning "isn't recommended for most advertisers"; the cross-account data says partial pinning is the best or tied-best configuration and full pinning is reliably the worst on CPA and CVR. The rule: pin 2–3 assets per controlled position, leave the rest open, and go unpinned only where the ad group has the volume to pay for it.

## Where it comes from
Optmyzr cross-account studies — 2022 (93,055 RSAs), Hopkins 2024 (22,000 accounts), Vallaeys 2026 (~20,000 accounts, including a 268-account matched subset); Vallaeys' 2021 SEJ testing piece; Brad Geddes / Adalysis 2022 testing method and 2022 creation series, plus the Adalysis checklist.

## When to use it / when not to
Use when building or restructuring RSAs, when an ad group cannot clear its data budget (skill 22 rule 1), or when a message must lead (offer, differentiator). Not for mandatory legal text — that is skill 32, which sits on top of this one. Not a tool for recreating ETAs: that is the full-pin configuration this skill forbids by default.

## Inputs
- Ad group 30-day impressions and clicks; unpinned asset counts (for the combination budget, skill 22).
- Which message must lead (relevance line, offer, CTA) and whether any text must appear on every impression.
- Current pin map per RSA and Ad Strength (recorded, not optimised).

## Method
1. **Classify the ad group by volume.**
   - High: clears 100 impressions per combination with all assets unpinned, or is in the range of Geddes' 50,000-clicks-a-month example (Adalysis, 2022). Default: **no pins**. Vallaeys (2021) found unpinned ads had the best CTR, CPC and CPA, and Hopkins (2024) found no-pinning a close second on CPA.
   - Everything else: default **partial pins** (rules 2–4). Geddes' reply on the SMX post (Adalysis, 2023) puts it bluntly: pinning is underused by smaller advertisers who lack the ~90,000 impressions to let Google test.
2. **Pin 2–3 assets per controlled position, never one.** Pinning a single text to a position had the biggest negative impact on CTR, CPC and CPA (Vallaeys, 2021); ad groups allowing multiple texts in pinned positions got 3.9× the impressions (Optmyzr, 2022); Geddes' partial formula is 2–3 assets per headline position (Adalysis, 2022). Google's own page now says the same (2–3 per position), which is one of the few places we agree.
3. **Assign roles to positions.** H1: ad-group relevance (the query echo). H2: CTA or main benefit. H3: supports H2 or is left open (Geddes/Adalysis, 2022; Adalysis checklist: pin H1 and H2 for data density). H1 and H2 and D1 are the only slots always shown (Google Ads Help), so anything that must be seen lives in H1/H2/D1, never H3/D2.
4. **Choose the hybrid when one message must lead but the rest can rotate.** Relevance pinned to H1 (2–3 variants), USP or offer pinned to H2 or H3, all other lines unpinned (Geddes, 2022 "hybrid"). This is the configuration the 2026 study calls "partial pinning (pin a core message)", which led on CPA ($13.68), CTR (11.88%) and ROAS (365.15%) across all accounts and tied no-pinning on CPA in the 268 matched accounts while beating it on CTR and ROAS (Vallaeys/Optmyzr, 2026).
5. **Full pinning only as a test arm.** Full pinning had the worst CPA ($32.57) and CTR (8.49%) across all accounts and a $61.11 CPA / 4.48% CVR in the matched subset (Vallaeys, 2026); it usually yields "Poor" Ad Strength and fewer impressions than sibling RSAs (Geddes, 2022). Use it only to put a top-served combination into its own ad to read its conversions (Geddes, 2022 strategy 1), or for compliance (skill 32), and run it beside a partially pinned sibling.
6. **Descriptions: pin D1 only when the line is required or carries the offer.** D2 is not guaranteed to show (Google Ads Help). Hopkins (2024) warns that heavy pinning can push headlines down into description slots; keep description pins to one position with 2 variants.
7. **Ignore the Ad Strength drop.** Pinning lowers Ad Strength by design (Google Ads Help; Marvin, 2024); a commenter on Geddes' 2022 series saw strength drop with no change in impression share, and Ad Strength is not an auction factor (Marvin, 2024). Record it; don't manage to it (skill 25).
8. **Re-check quarterly against volume.** An ad group that grows into the high-volume class gets a second, unpinned RSA as a test arm (Geddes, 2022 strategy 2: your messages vs. the algorithm); one that shrinks gets its H1/H2 pinned.

## What Google will tell you instead, and why we don't
Google's RSA page says pinning "isn't recommended for most advertisers" because it reduces matching options, and the editor lowers Ad Strength as you pin. Across ~20,000 accounts partial pinning led or tied on CPA, CTR and ROAS (Vallaeys, 2026) and the 2024 study found pinning flat to positive versus none (Hopkins); the only configuration that reliably loses is full pinning, which is also the one Google's warning is really about. We treat "more combinations" as a cost to be paid by volume (Geddes, 2022), not a free benefit.

## Failure modes
- Very high-volume ad groups: partial pins throw away the combination learning that only those ad groups can afford; go unpinned (Vallaeys, 2021; Geddes, 2022).
- Single-asset pins: the documented worst case for CTR/CPC/CPA (Vallaeys, 2021). If you only have one line for a position, write two (skill 23) before pinning.
- Pinning the same or near-identical text in a slot: lowers Ad Strength and buys nothing (Google Ads Help); the 2–3 variants must be distinct.
- Brand campaigns: a fully pinned brand ad is a common ETA relic; the 2022 study attributes full-pin CTR/CVR strength to this pattern, but the 2026 CPA numbers say it is still the costliest configuration. Pin brand to H1 with variants, leave H3 open.
- E-commerce ad groups with price or discount in H2: treat as a test (H2 is the position Geddes suggests for price-vs-discount tests), because prices in headlines trended worse in his 2026 account tests.

## What to measure
Per pin configuration: CPA, CVR and conversions per impression, read only once the ad group clears the combination budget (skill 22). Impressions per ad group before and after pinning (the 2022 study's 3.9× effect of multi-asset pins is the sanity check). Ad Strength is logged, not targeted.

## Open disagreements in the canon
- Does any pinning cost performance? Vallaeys 2021: yes, unpinned wins. Vallaeys 2026 and Hopkins 2024: partial pinning wins or ties. Epiminds follows the newer, larger studies (canon rule 3) and reserves no-pins for ad groups that can pay the data cost.
- Pin H1 only vs. H1 and H2: Geddes' creation series starts with H1; the Adalysis checklist pins both for density. Epiminds pins both below the volume threshold and H1 only when the CTA genuinely varies by query.
