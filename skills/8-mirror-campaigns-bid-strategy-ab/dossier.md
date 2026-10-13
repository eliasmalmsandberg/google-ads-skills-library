# Dossier — 8 Mirror campaigns for Smart Bidding A/B

## Sources

1. **Source**: Navah Hopkins, Optmyzr, bidding-strategy study — https://www.optmyzr.com/blog/impact-of-ppc-bidding-strategies/ (reported by Anu Adegbola, Search Engine Land, "There is no 'best' Google Ads bidding strategy, study finds" — https://searchengineland.com/google-ads-bidding-strategy-analysis-446899) · **Tier**: 1 · **Date**: 2024-09-24 · **Claim**: 14,584 accounts: no universal best strategy — success depends on execution and volume; 50+ conversions/30 days is where strategies become predictably successful; targets more often hurt than helped, bid caps inconsistent; 48% of advertisers run more than one strategy in an account; Smart Bidding needs 2–3 weeks to stabilise after budget changes; keep bid caps within ~10% of daily budget; avoid aggressive budget/goal changes. · **Evidence or opinion**: Cross-account study.

2. **Source**: Brad Geddes (Adalysis), "How to evaluate your AI Max performance" — https://adalysis.com/blog/evaluate-ai-max-performance/ · **Tier**: 1 · **Date**: 2026-08-20 · **Claim**: Test a campaign-level automation change (AI Max) by limited scope rather than account-wide: prerequisites are accurate tracking, a conversion-based automated strategy, no significant budget-lost IS, and profitable broad match; test in non-brand campaigns with ≥30 conversions/month, enable for a few high-conversion ad groups (AI Max is campaign-level but can be disabled per ad group); watch search terms, auto-created assets, URL expansion; add exact/phrase keywords as broad so match types can be compared. · **Evidence or opinion**: Method.

3. **Source**: Brad Geddes (Adalysis), "How to gain customer insight through ad testing" — https://adalysis.com/blog/gain-customer-insight-ad-testing/ · **Tier**: 1 · **Date**: 2026-08-04 · **Claim**: Run tests across many ad groups with a consistent setup and combine results (label-level), rather than one ad group; expand to more ad groups to confirm. (Ad-level, but the "combine across units" principle carries to campaign tests.) · **Evidence or opinion**: Method.

4. **Source**: Fred Vallaeys with Shawn Walker, Optmyzr PPC Town Hall — https://www.optmyzr.com/ppctownhall/practical-advice-on-how-to-actually-make-smart-bidding-work-for-you · **Tier**: 1 · **Date**: 2025-01-29 · **Claim**: ≥30 conversions per campaign per 30 days; below that campaigns become unstable. · **Evidence or opinion**: Opinion.

5. **Source**: Andrew Lolk (with Bacchini, Vallaeys), Optmyzr PPC Town Hall "PPC in 2025" — https://www.optmyzr.com/ppctownhall/ppc-in-2025-what-to-stop-start-double-down-on · **Tier**: Not canon (labelled); Bacchini Tier 2 · **Date**: early 2025 · **Claim**: Splitting campaigns means conversions are not shared, shared budgets are impossible and bidding cannot combine data — "stop splitting up your campaigns". Applies directly to mirror campaigns: a mirror halves the data each strategy learns from. · **Evidence or opinion**: Opinion.

6. **Source**: Alex van de Pol, Adchieve — https://www.adchieve.com/en/blog/hagakure-structure-results/ · **Tier**: Not canon (vendor) — context · **Date**: 2021-05-11 · **Claim**: Whole-structure changes could not be tested with Google's experiment feature; fell back to before/after on equal periods, excluding seasonal accounts. · **Evidence or opinion**: Practice note.

7. **Source**: Google Ads Help, "About custom experiments" (answer 6261395) — https://support.google.com/google-ads/answer/6261395 · **Tier**: Reference only · **Date**: current 2026-10-13 · **Claim**: Search (and Display/Video/Hotel) only — not Shopping or App; cookie-based split (recommended) vs search-based split (faster significance; a user can see both); recommended 50% split; one experiment at a time per campaign, up to 5 scheduled; original campaign cannot use a shared budget; changes to the original are not mirrored into the experiment and mid-test changes make results hard to interpret; base campaign must stay active; audience-list splits need ≥10,000 users; no significance threshold stated; experiment can be applied or converted to a new campaign. · **Evidence or opinion**: Platform statement.

## Dissenting view
Lolk's "stop splitting" position (2025) and Google's experiment tool both say: do not run mirror campaigns; one campaign, one test. Adchieve (2021) and the Shopping/shared-budget limits in Google's own doc are the counter-case: some changes cannot be tested in the tool. The disagreement is whether the data fragmentation of a mirror is ever worth the cleaner comparison; the canon (Geddes, 2026) resolves it by scoping the test inside one campaign (ad-group level) rather than mirroring.

## What the platform currently does [Google docs]
- Custom experiments: Search/Display/Video/Hotel; not Shopping; cookie vs search split; 50% recommended; no shared budgets; one at a time; no sync of base-campaign changes (answer 6261395). [Google docs]
- Smart Bidding re-enters learning on budget/target changes and needs 2–3 weeks to stabilise (Hopkins, 2024, practitioner statement of platform behaviour).
- AI Max is a campaign-level setting with per-ad-group opt-out (Geddes, 2026). [Google docs via Geddes]

## Baseline check
Read `google-ads-experiments` headings (custom experiments, splits, duration). Baseline explains the tool. This skill adds the decision rule between experiment, mirror and scoped before/after; the per-arm volume floor (30 per arm → 60 per campaign); the data-fragmentation cost of mirrors (Lolk); the cases where the tool cannot be used (Shopping, shared budgets, structure changes); and the stabilisation window and "no universal winner" finding that justifies testing at all.

## Judgment calls
- No canon source advocates mirror campaigns; the skill treats them as last resort and says so. Coverage of mirrors specifically is thin; coverage of the decision (experiment vs scoped test) is Adequate.
- "Per arm ≥30" is derived: Vallaeys/Walker's 30-per-campaign floor applied to each experiment arm at a 50% split.

## Canon strength: Adequate
Hopkins/Optmyzr (evidence), Geddes ×2 (method), Vallaeys/Walker (opinion); Google docs for mechanics; Lolk non-canon.

## Invalidated by
Custom experiments extended to Shopping/PMax and shared budgets; experiments allowing base-campaign sync; a change to Smart Bidding learning that removes the 2–3-week stabilisation.
