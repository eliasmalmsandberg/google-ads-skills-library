# Overlap and contradiction pass — 2026-10-13

Scope: all 85 built skills (`skills/*/SKILL.md`; stubs 6, 18, 30, 33, 53 skipped). No files merged or deleted. Cross-references were added as `See also:` lines at the end of each affected skill's "What this is" section. Contradictions were resolved against canon.md section 5 and fixed with the minimal edit to the losing skill, keeping its attribution style.

Totals: 36 overlap groups/pairs, 97 cross-reference lines added across 56 skills; 18 contradictions resolved with edits to 19 files.

## (a) Overlaps and cross-references added

| # | Skills | What they share | Cross-refs added (from → to) |
|---|---|---|---|
| 1 | 1, 13 | Same two-tier managed/discovery (alpha/beta) structure, exact negatives as routing | 1→13, 13→1 (merge candidate, see (c)) |
| 2 | 1, 4, 13 | Match-type separation at campaign level; cross-negatives | 1→4, 4→1, 4→13, 13→4 |
| 3 | 2, 9 | Consolidation for Smart Bidding volume; 30/50 thresholds; portfolio pooling | 2→9, 9→2 |
| 4 | 2, 14 | DSA as backstop/feeder inside a consolidated structure | 2→14 |
| 5 | 9, 40 | Rooijmans's portfolio cap at the 90th–95th CPC percentile, scale gate | 9→40, 40→9 |
| 6 | 5, 55, 81, 90 | Brand in PMax: exclusions, negative lists, brand-share measurement | 5→55, 55→5, 5→90, 90→5, 5→81, 81→5, 81→55, 55→81, 90→55, 55→90 |
| 7 | 5, 68 | Low-priority brand Shopping campaign with brand negatives on non-brand | 5→68, 68→5 |
| 8 | 5, 45 | Brand campaign bidding (impression share) | 5→45, 45→5 |
| 9 | 5, 15, 45 | Competitor negatives; brand defence vs conquesting | 5→15, 15→5, 15→45, 45→15 |
| 10 | 12, 59, 62 | Search-vs-PMax routing: exact keyword first, then PMax negatives | 12→59, 59→12, 12→62, 62→12 |
| 11 | 62, 90 | PMax-scoped list vs account-level list, 1,000 cap | 62→90, 90→62 |
| 12 | 10, 70, 76 | N-gram method vs script; term-level weekly script | 10→70, 70→10, 10→76, 76→10, 70→76 |
| 13 | 16, 76 | Weekly negative-candidate thresholds (60 clicks / 5 cost / 0.5 conv) | 16→76 |
| 14 | 21, 74 | Rooijmans's fork of the conflict script: method vs install | 21→74, 74→21 (merge candidate) |
| 15 | 72, 74 | Watchdog paired with conflict script | 72→74 |
| 16 | 7, 87 | "Presence" location option; no location adjustments under Smart Bidding | 7→87, 87→7 |
| 17 | 17, 88 | Search partners default and evaluation | 17→88, 88→17 |
| 18 | 61, 88 | Final URL expansion default | 61→88, 88→61 |
| 19 | 78, 88 | Auto-apply opt-out (88 step 1 duplicates 78) | 78→88, 88→78 (merge candidate) |
| 20 | 87, 88 | Takeover checklist settings | 88→87 |
| 21 | 8, 79 | Bid-strategy A/B via custom experiment | 8→79, 79→8 |
| 22 | 22, 82 | RSA testing: data budget vs per-ad floors and confidence ladder | 22→82, 82→22 |
| 23 | 82, 89, 31 | Ad rotation under Smart Bidding, RSA count in tests | 82→89, 89→82, 89→31, 31→89 |
| 24 | 37, 38 | Impression-weighted QS formula, null = 6, ±0.2 band | 37→38, 38→37 (merge candidate, lower priority) |
| 25 | 40, 46, 84 | Post-17-Aug-2026 budget-limited bidding change; cap vs target | 40→46, 46→84, 84→46, 84→40 |
| 26 | 41, 42 | Conversion value rules inside value-based bidding | 41→42, 42→41 |
| 27 | 42, 43, 48 | Conversion ladder, primary-rung rule, 45/50 thresholds, no stacking | 42→43, 43→42, 43→48, 48→43, 48→42 |
| 28 | 50, 51, 52, 54 | Audience bid adjustments inert under Smart Bidding; observe/exclude/target | 50→51, 50→52, 51→50, 51→52, 52→50, 52→51, 54→50 |
| 29 | 63, 51 | Existing-customer Customer Match list | 63→51 |
| 30 | 57, 62, 69, 76 | PMax search terms: 100 clicks / <0.5 conv rule, brand bucketing | 57→62, 57→69, 62→57, 69→57, 69→62, 76→57 |
| 31 | 60, 69 | PMax placement flags, 15% single-placement rule, channel split | 69→60, 60→69 |
| 32 | 64, 69 | Rhodes's six-bucket product matrix and supplemental feed | 69→64, 64→69 |
| 33 | 56, 60 | Fencing video/Display vs going feed-only | 56→60, 60→56 |
| 34 | 73, 61 | PMax expanded landing URLs | 73→61 |
| 35 | 67, 75 | Rooijmans's Disapproved Products script appears in both | 67→75, 75→67 |
| 36 | 83, 84; 44, 49; 47, 48; 59, 55; 19, 13; 34–39 | Already cross-referenced in the existing text; no new lines needed | — |

## (b) Contradictions found and resolved

| # | Skills | Conflict | Resolution and reason (canon.md §5) | File(s) edited |
|---|---|---|---|---|
| C1 | 1 vs 13, 14, 19 (and 2) | Promotion threshold for discovery → managed: 1 used ≥1 conversion or 50–100 clicks (Rooijmans 2026 / Lolk 2025, not canon); 13/14/19 use ≥35 impressions and ≥2 conversions/month for 3 months (Geddes 2016). 2 used Lolk's 50–100 clicks for DSA promotion. Cadence: 1 fortnightly, 13/14 monthly. | Epiminds operating threshold picked: Geddes's rule (Tier 1, published method, tied to the low-search-volume mechanism that strands a promoted keyword) plus Rooijmans's CPC screen. Lolk is not canon. Cadence monthly. | 1 (step 2, step 6, open disagreements), 2 (step 4, what to measure) |
| C2 | 4 vs 13 | 13: "a three-tier exact/phrase/broad split, which Epiminds does not build"; 4 builds it when a budget/bid-method reason exists (Geddes 2020). | Geddes's gate (Tier 1, method) governs; Hopkins's maintenance objection (Tier 1, opinion) becomes the default-off. 13 now defers to skill 4's gate. | 13 (description, when not to) |
| C3 | 9 vs 43 | Starting strategy with no conversion history: 9 "manual CPC or Max Clicks" and "starts manual when there is none" (Vallaeys/Walker 2025); 43 "Max Clicks with a cap; manual pays only in high-volume accounts" (Hopkins 2024, 14,584 accounts). | Evidence beats opinion: Hopkins's cross-account data. 9 now starts on Max Clicks with a CPC cap. | 9 (step 4, open disagreements) |
| C4 | 9 vs 57, 90 | PMax conversion floor: 9 cited Lolk ~30/month (not canon); 57 and 90 cite ~60/30 days (Hopkins 2026). | Tier 1 beats non-canon; library uses 60. | 9 (failure modes) |
| C5 | 42 vs 41, 50 | 42 said value rules are "additive" (Marvin/Google Help 2024); 41 and 50 say at most one rule applies per conversion (Google API docs 2026). | Platform fact: the API documentation is newer and specific; Google Help is reference-only and contradicted. 42 now matches 41. | 42 (step 4) |
| C6 | 70 vs 10 | N-gram block threshold: 70 applied Rooijmans's 60-click single-term bar to aggregates; 10 blocks at Geddes's 150 clicks (2025) and keeps 60 as a review queue. Also 70 "hundreds of queries" vs 10's ~1,000/month floor. | Geddes's threshold is the published n-gram method (Tier 1, evidence); 10 is the method skill. 70 now uses 150 block / 60 review and the 1,000-query floor. | 70 (when to use, step 3, open disagreements) |
| C7 | 69 vs 62, 90 | 69 allowed adding PMax waste negatives "to the PMax account-level list"; 62 says never (Rooijmans 2025, Hopkins 2026, Williams 2023) and 90 reserves account-level for whole-account terms. | Three Tier 1 sources vs a loose reading of one; account-level list hits every Search campaign. 69 now routes to campaign or PMax-scoped list. | 69 (step 4) |
| C8 | 78 vs 17, 88 | 78 told operators to verify "Search Partners … off on Search" on every campaign (Cooney/PPC Hero 2024, Tier 2 for auto-apply only); 17 keeps partners on-and-measure for established campaigns (Geddes 2023, account data). | Tier 1 with evidence beats Tier 2 outside its topic. 78 now defers to skill 17. | 78 (step 4) |
| C9 | 78 vs 88 | Auto-apply at manager level: 78 said it can be set for sub-accounts "[unverified]"; 88 says it cannot be set at MCC level (Google Help). | Platform fact; verified reference beats unverified. 78 now says per-account only. | 78 (step 1, step 8, what to measure) |
| C10 | 88 vs 17 | Partners on takeover: 88 switched off on every takeover and earned back at ≥30 conversions (Epiminds figure); 17 keeps established unconstrained campaigns on and requires ~50 conversions (Vallaeys 2026) and 50 partner clicks (Rooijmans 2019) before trusting the split, with a 20% CPA rule. | Geddes (evidence) over Rooijmans's checklist (opinion) for established campaigns; both agree new/budget-limited go off. Thresholds unified on 17's sourced numbers. | 88 (inputs, step 2, earn-back rule, open disagreements) |
| C11 | 17 vs 88 | 17 said Display Expansion "has no canon source"; 88 cites Seer Interactive's controlled test (2021, Tier 2 for this topic per canon.md). | Evidence exists in the canon; 17 now cites it via skill 88 and labels the default accordingly. | 17 (what this is, step 1, failure modes, open disagreements) |
| C12 | 5, 90 vs 55 (and 12) | 5 and 90 applied PMax brand exclusions unconditionally; 55 exclude only above a brand-share threshold (≥20% clicks / ≥30% conversions; leave in under 10%) because Williams observed brand-sales loss after exclusion (ZATO 2026) and PPC.io's 84-campaign distribution. Separately, 55 and 12 said "Brand Exclusions, not keyword negatives" while 5, 81 and 90 layer a variant negative list under the exclusion (Rooijmans 2025; Optmyzr 2025 fuzzy-match leak). | Threshold: 55 is the dedicated decision skill with evidence; 5 and 90 now apply its threshold. Negatives: exclusion stays primary (Hopkins), scoped variant list is the backstop (Rooijmans, Vallaeys — observed leakage), never account-level; 55 and 12 now say so. | 5 (step 6), 90 (step 4), 55 (step 4), 12 (step 6) |
| C13 | 84 vs 40, 46 | Post-Aug-2026: 84 listed "raise the target toward the ROAS/CPA actually delivered" (Ryan 2026, Tier 2); 40 and 46 say never move the target to the rationing-era actual (Rooijmans 2026 case: leads 20–30 → 6; Vallaeys 2026: artefact of scarce-budget selection). | Tier 1 beats Tier 2; a documented failure case beats a listed option. 84 now excludes target-to-actual and routes to budget / Max Conversions / cap after 1–2 cycles. | 84 (step 2) |
| C14 | 82 vs 24, 32 | 82's test default "pin 1–2 assets per position"; 24 and 32 say never pin a single text (Vallaeys 2021: biggest negative impact; Optmyzr 2022: 3.9× impressions with multiple texts). | Evidence; 82 now pins 2–3 per position. | 82 (step 1) |
| C15 | 89 vs 31, 82 | 89 capped tests at two RSAs per ad group; 31 and 82 allow a third as a dated test arm (Geddes 2022; Vallaeys 2021). | Geddes 2018's "random serving" finding is about 4–5+ ads; three is within evidence. 89 now allows a dated third arm per skill 31. | 89 (step 4) |
| C16 | 79 vs 8 | Experiment eligibility: 79 "≥30–50 conversions/30 days" and "don't under ~30" (Stemen/SEJ 2026, not canon); 8 "≥60 so each 50% arm clears the 30 floor" (Vallaeys/Walker 2025; Hopkins 2024). | Tier 1 floor applied per arm beats a non-canon campaign-level figure. 79 now uses 60 total / 30 per arm. | 79 (when to use, when not to, failure modes) |
| C17 | 5 vs 45 | 5 bid brand to impression share with no mention of a cap; 45: uncapped Target Impression Share is unsupported (Hopkins 2024, 14,584 accounts) and must always be capped. | Evidence; 5 now requires the cap. | 5 (step 4) |
| C18 | 57 vs 62, 76 | Cadence for the PMax waste-term check: 57 monthly, 62/76 weekly (Rooijmans's script). | Same check, two cadences: weekly is the script alert, monthly is the classification pass. 57 now states both. | 57 (when to use) |

Residual, not edited (noted for Elias): skill 15's failure mode keeps manual CPC for a small conquest campaign (Vallaeys 2026, per-keyword ceiling) and skill 45 step 1 uses manual CPC at a low bid when no competitor is in the auction; both are narrow, sourced cases and do not conflict with C3's Max-Clicks-first rule for new low-volume campaigns. Skills 19 and 20 cite two different Hopkins ad-group-count figures (">~10 ad groups" flag, SEJ 2024; "5–7 ad groups" supported, SEJ 2020) for different claims; left as is.

## (c) Merge candidates for Elias

- **1 + 13** (alpha-beta-structure + keyword-funnelling-tiered-negatives): the same two-campaign managed/discovery structure described twice. After C1 they now share one promotion rule; what differs is emphasis (1: budget/bid separation, CPC screen, scale gate; 13: Geddes's demotion rule, variant hygiene, Hopkins's merge trigger). One skill with both halves would be shorter than the pair.
- **21 + 74** (negative-keyword-conflict-detection + negative-keyword-conflict-script): method and install for the same Rooijmans fork; the match-type logic, limits and cadence are stated in both. Could become one skill with an "install" section.
- **78 + 88 step 1** (recommendations-auto-apply-opt-out + the auto-apply part of standard-off-list): 88's first step restates 78 with one extra study (Hopkins 2024 Optimization Score). Either trim 88 step 1 to a pointer or fold 78 into 88.
- **37 + 38** (qs-tracker-script + impression-weighted-qs): same formula, null rule and noise band; distinct by job (script spec vs reporting rule). Lower priority — keep separate if the script spec is meant to be handed to an engineer.
- **57 + 62 + 76 (PMax part)**: the 100-click / <0.5-conversion rule and the keyword-first alternative are now stated in three places. Not a merge, but the PMax sibling of Rooijmans's script in 76 could be reduced to a pointer to 62.
