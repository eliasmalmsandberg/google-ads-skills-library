---
name: broad-match-smart-bidding-guardrails
id: 16
description: The evidence on broad match vs phrase/exact, the entry conditions, and the guardrails for a broad match rollout under Smart Bidding. Use before switching any campaign to broad, or when auditing an inherited broad-match account. Not a search term review procedure (skills 10, 12) and not a bidding strategy choice guide beyond the broad-specific rules.
tags: Research / Search / Scale / Established / One-off
last_verified: 2026-10-13
invalidated_by: Google removing phrase or exact match or folding Search into AI Max by default; changes to the signals broad match uses (landing page, ad group keywords, recent searches); Smart Bidding learning thresholds changing; search terms visibility cuts that prevent policing broad.
---
## What this is
A gated rollout for broad match. The gate exists because the only cross-account evidence in the canon says broad is winning budget, not performance: across 30,000 accounts in February 2026, exact match led on efficiency in every non-brand segment, phrase carried the largest non-brand spend share and out-converted it, and broad generated the most volume while overspending on traffic that did not convert; in lead gen broad lost the most ground, which Vallaeys attributes to Smart Bidding having no conversion value to steer by (Vallaeys/Optmyzr, 2026). Across thousands of accounts, CTR and CVR rank exact > phrase > broad outside brand (Geddes/Adalysis, 2024). Broad's rise in spend share — exact down roughly 10 points since 2022 — reflects comfort with automation rather than results (Vallaeys/Optmyzr, 2026).

## Where it comes from
Vallaeys' 30k-account match-type study and his 14k-account Smart Bidding threshold (Optmyzr, 2026 ×2); Geddes' pre-broad checklist and CTR/impression-share mechanics (Adalysis, 2024, 2019); Hopkins' isolated-ad-group test design (SEJ, 2020, 2024); Rooijmans' negative automation (2024); McNair's broad-by-default dissent (PPC Mastery, 2026).

## When to use it / when not to
Use when considering broad for a campaign, when an inherited account is already on broad, and when Google's "switch to broad match" recommendation or auto-apply is in play. Do not apply the gate to tiny or niche markets that cannot find volume on exact/phrase — broad is the right tool there even with thin data (Geddes/Adalysis, 2024). Do not switch a campaign that is hitting target on phrase/exact just because Google recommends it (Geddes/Adalysis, 2024).

## Inputs
- Conversions per 30 days per campaign; whether conversion value is tracked and trustworthy.
- Current bid strategy and target.
- Search impression share, and loss split by budget vs rank, per campaign.
- Ad group composition: keywords per ad group, landing page per ad group, whether the page lists many services.
- Negative lists in force; search terms review cadence.
- Brand/non-brand split.

## Method
1. **Entry gate (all must hold)** — otherwise stay on phrase/exact:
   - Conversion tracking is in place and the campaign has ≥ 50 conversions per 30 days (Vallaeys/Optmyzr, 2026 Smart Bidding threshold; Geddes/Adalysis, 2024: no broad without conversion tracking or on manual bids).
   - For lead gen, conversions have values or at least primary/secondary separation; without value signals broad underperforms most (Vallaeys/Optmyzr, 2026).
   - Bid strategy is tCPA or tROAS, not Max Conversions / Max Value — at larger budgets the max strategies spend everything for few extra conversions (Geddes/Adalysis, 2024). Exception: data too thin for targets, in which case see rule 1 line 1.
2. **Impression share gate.** If search IS is already low and lost mainly to rank, fix or remove the worst keywords and convert broad to phrase/exact instead of adding reach. Add broad only where IS is high and the campaign needs new queries (Geddes/Adalysis, 2024).
3. **Structure before match type.** Broad reads the landing page and the other keywords in the ad group (Google docs, 2026). So: one theme per ad group, a landing page specific to that theme (not a services index), and no mixed-intent keyword lists. Google reps' advice to consolidate into few RSAs with long keyword lists is a leading cause of broad problems (Geddes/Adalysis, 2024).
4. **Scope of the first test.** Pick long-tail, intent-explicit keywords (Hopkins/SEJ, 2020: 5+ words), put each broad keyword alone in its own ad group, and add every other keyword in the campaign as exact and phrase negatives to that ad group so the broad keyword cannot steal them (Hopkins/SEJ, 2020). Never broad on brand (Hopkins/SEJ, 2020; Vallaeys/Optmyzr, 2026: scrutinise non-exact on brand) and never single words on anything but exact (Hopkins/SEJ, 2020).
5. **Keep the exact keywords.** Leave the exact and phrase versions live in their ad groups; an identical exact keyword is what Google sets aside before broad gets the query (Google docs, 2026; Geddes/Adalysis, 2024).
6. **Guardrails on day one.**
   - Weekly automated negative candidates: terms with > 60 clicks, > 5 currency units cost, < 0.5 conversions over 90 days, excluding terms already negated (Rooijmans, 2024).
   - Monthly n-gram pass (skill 10) — Geddes lists it as a mandatory broad-match step (Adalysis, 2024).
   - Bid cap on the portfolio where CPC spikes are a risk (Hopkins/SEJ, 2024, 2022).
   - Separate the broad campaign from campaigns you use to read impression-share trends, because broad expands and contracts its query set with QS and budget and distorts the trend (Geddes/Adalysis, 2019).
7. **Read the signals weekly for 6 weeks.** A CTR drop together with top/absolute-top IS falling and bottom IS rising means the keyword is matching loosely related queries (Geddes/Adalysis, 2019). Rising query count with flat conversions means discovery is not finding intent.
8. **Rollback rule.** Compare broad vs the phrase/exact baseline on CPA or ROAS at equal conversion count. If broad is worse than phrase on CPA/ROAS after the negatives in rule 6 have had 6 weeks, revert to phrase (Vallaeys/Optmyzr, 2026: phrase is the workhorse). If broad is finding converting queries, harvest them as exact keywords (skill 12) and keep broad as discovery only.
9. **Scale rule.** Expand broad to another theme only after the first passes rule 8; never account-wide in one step.

## What Google will tell you instead, and why we don't
Google makes broad the default, says it "should be used with Smart Bidding", and says broader types include everything the narrower ones catch (Google docs, 2026). The canon's reply: across 30,000 accounts broad did not win on performance in any non-brand segment (Vallaeys/Optmyzr, 2026); Google pushes broad "regardless of the circumstances" (Geddes/Adalysis, 2024); and "Smart Bidding will handle it" assumes signal the account may not have — learning requirements have not fallen and Smart Bidding cannot see LTV or margin (Vallaeys/Optmyzr, 2026). We also reject the Google-rep consolidation advice that makes broad's ad-group signal worse (Geddes/Adalysis, 2024).

## Failure modes
- **Lead gen without values.** The segment where broad loses most ground (Vallaeys/Optmyzr, 2026); require value or primary/secondary conversions first.
- **Sub-50-conversion campaigns.** Smart Bidding is unreliable below ~50/30 days (Vallaeys/Optmyzr, 2026), so broad has no competent bidder.
- **Shared landing pages / services index pages.** Broad reads the page and matches other services; a plumber's "plumber" keyword served a different service's ad group off a shared page (Geddes/Adalysis, 2024).
- **Short sales cycles and dynamic pages.** Geddes (2024) flags both as poor fits for broad.
- **Jargon and technical terms.** Semantic matching mishandles niche vocabulary (Geddes/Adalysis, 2024).
- **Brand.** Broad on brand cannot protect brand or non-brand campaigns (Hopkins/SEJ, 2020).
- **Spam conversions.** Broad plus Smart Bidding amplifies fake-lead bursts; negating later does not un-count them (Optmyzr, 2026, via skill 10).

## What to measure
- CPA/ROAS by match type at equal conversion counts, by segment (brand, non-brand, e-com, lead gen) (Vallaeys/Optmyzr, 2026).
- Share of spend by match type, trend (the study's headline metric).
- Broad keyword CTR and top/absolute-top vs bottom impression share, weekly (Geddes/Adalysis, 2019).
- New converting queries harvested per month from broad (the only reason to keep it).
- Negatives added per week from the Rooijmans script; a rising count means broad is still drifting.

## Open disagreements in the canon
- **Broad by default vs gated.** McNair/PPC Mastery (2026) runs broad + AI Max + Smart Bidding + strong negatives as the bottom-of-funnel default; Vallaeys (2026) and Geddes (2024) condition it. Epiminds gates, because the cross-account evidence favours exact/phrase on efficiency and the PPC Mastery position is experience without published data. Where an account passes every gate and has mature negatives, PPC Mastery's setup is the end state, not the starting point.
- **Max vs target strategies with broad.** Geddes (2024) says tCPA/tROAS; Google and some practitioners accept Max Conversions when data is thin. Epiminds: targets, with the thin-data exception Geddes allows.
