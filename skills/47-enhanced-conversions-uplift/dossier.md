# Dossier — 47 Enhanced conversions — measurement uplift & when it pays

## Sources

1. **Source**: Miles McNair & Bob Meijer, PPC Mastery — "TPE #79: Google Ads conversion tracking best practices (2024 update)", https://www.ppcmastery.com/newsletter/tpe-79-google-ads-conversion-tracking-best-practices-2024-update · **Tier** 1 · **Date** 2024-02-05 · **Claim**: Enhanced conversions (web) add hashed first-party data (email) to the tag so Google can match conversions to signed-in users, including cross-device after cookie loss. Reported uplift: a PPC Hub member +10% measured conversions on Search; the authors' own account +25% on Video; "+/- 10%" as the working expectation. Consent Mode v2 (deadline March 2024 for EEA) enables conversion modelling; "on average we see an uplift of 5% in measured conversions" from modelling; observed vs modelled can't be segmented in Google Ads. Server-side tagging claimed at 10–30% uplift. Recommend all three for everyone. · **Evidence**: two single-account anecdotes; no baseline or method; affiliate link to a tool.

2. **Source**: Miles McNair & Bob Meijer, PPC Mastery — "TPE #50: Measurement maturity model", https://www.ppcmastery.com/newsletter/tpe-50-measurement-maturity-model-tracking-best-practices · **Tier** 1 · **Date** 2023-08-07 · **Claim**: Four-level model. Level 2 ("Medior") = Google Ads conversion tracking + GA4 secondaries + Consent Mode + Enhanced Conversions, used "to measure lost conversions due to tracking issues". Level 3 adds conversion adjustments, new-vs-returning, cart data, offline conversions as secondary. Level 4 adds offline conversions as primary / VBB, server-side, third-party attribution, POAS. Relying on a GA4 import as the only primary is "the biggest mistake" at level 1. · **Evidence**: framework; no data.

3. **Source**: Frederick Vallaeys, Search Engine Land — "Why PPC measurement feels broken (and why it isn't)", https://searchengineland.com/ppc-measurement-broken-468574 · **Tier** 1 · **Date** 2026-02-10 · **Claim**: Enhanced conversions match conversions when click IDs are missing, via hashed identifiers associated with signed-in Google users; adding them typically improves matching *before* it affects bidding. Measurement loss comes from ITP, enhanced tracking protection, private browsing, consent; some traffic will never be observable at the individual level. Modelled conversions fill the gap when confidence allows; imported/modelled conversions appear in reporting before they are fully weighted in optimisation. · **Evidence**: experience; no figures.

4. **Source**: Frederick Vallaeys, Optmyzr — "Offline conversion tracking just got easier with Enhanced Conversions", https://www.optmyzr.com/blog/enhanced-conversions-google-ads · **Tier** 1 · **Date** 2022-02-24 · **Claim**: EC for leads removes the need to carry the GCLID into the CRM: capture hashed email at form submit, report later stages by email; advertisers can do the landing-page tag change without engineering; email is "nearly always" the first form field. · **Evidence**: hypothetical solar example; no results.

5. **Source**: Google Ads Help — "About enhanced conversions" (answer/9888656) and "Set up enhanced conversions" (answer/11347292), fetched 2026-10-13 · **Tier** Reference only · **Claim**: SHA-256 after normalisation (trim, lowercase, E.164 phones, strip gmail dots); requirements: accept customer-data terms, at least one of email/phone/address, auto-tagging, Conversion Linker on landing pages, keep sending GCLID; GTM auto-collection can't collect phones; from April 2026 EC for web and leads is a single on/off setting; from 2026-06-15 OCI and EC-for-leads uploads move to the Data Manager API and are blocked in the Google Ads API; developer tokens idle Jan–Jun 2026 aren't allowlisted; classic OCI is described as "legacy … without the durability features" of EC for leads. Google's "impact results" page exists but could not be fetched.

## Dissenting view
No canon source argues against enhanced conversions; the disagreement is about how much it's worth. McNair reports ~10% on Search from anecdotes and treats it as baseline hygiene; Vallaeys frames it as a matching improvement whose bidding effect arrives later and depends on how much traffic was unobservable to begin with. Google's own uplift figures (not fetched) are medians across advertisers and say nothing about a given account's Safari/consent mix. Everyone agrees it is cheap on web; the real effort question is EC-for-leads vs GCLID import.

## What the platform currently does [Google docs]
See source 5. Additional: [Google docs via McNair 2024] observed and modelled conversions are not separable in Google Ads reporting.

## Baseline check
Read `google-ads-conversion-tracking` (enhanced conversions: "typical match rate improvement 5–20%", setup steps) and `google-ads-attribution`. Baseline gives an unsourced 5–20% and a GTM how-to. This skill adds: the practitioner-reported numbers and their (weak) provenance, the mechanism that predicts where uplift is large (share of unobservable traffic), the maturity-model placement (hygiene, not a project), the April/June 2026 platform changes, the keep-the-GCLID rule, and a before/after measurement protocol so a client decision isn't made on Google's median.

## Judgment calls
- Canon strength is Adequate: two Tier 1 practitioners with method but only anecdotal uplift numbers; Google's figure unfetched and not cited.
- Position: EC for web is always on (hours of work, no downside); EC for leads is the lever when GCLID capture in the CRM is <80% or the CRM project is stalled; expected measured uplift ~10% Search is treated as a prior, not a promise, and verified per account.
- The before/after protocol in the skill (segment by browser/OS and consent state in GA4, compare matched vs unmatched) is Epiminds' own and labelled as such.

## Canon strength: Adequate
Two Tier 1 practitioners (McNair/Meijer; Vallaeys ×2) with method and anecdotal evidence; Google docs for mechanics.

## Invalidated by
Google changing the matching mechanism, removing the GCLID requirement/recommendation, changing the single on/off setting, or publishing per-account uplift reporting that makes the protocol redundant.
