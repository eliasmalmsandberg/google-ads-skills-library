---
name: enhanced-conversions-uplift
id: 47
description: Use when deciding whether enhanced conversions (web, and especially for leads) are worth the setup for a client, what uplift to promise, and how to verify it. Not a GTM how-to (baseline covers that), not for offline stage selection (skill 48), and not a consent-mode legal guide.
tags: Research / All / Setup / Any / One-off
last_verified: 2026-10-13
invalidated_by: Google changing the matching mechanism, removing the GCLID requirement/recommendation, changing the single on/off setting introduced April 2026, or publishing per-account uplift reporting that makes the verification protocol redundant.
---
## What this is
Enhanced conversions send a SHA-256 hash of email/phone/address with the conversion so Google can match it to a signed-in account that saw or clicked the ad, including across devices and after cookie loss (McNair & Meijer/PPC Mastery, 2024; Google Ads Help, 2026). The honest answer on uplift: practitioners report around +10% measured conversions on Search and +25% on Video from single accounts, and treat "+/- 10%" as the working expectation (McNair & Meijer/PPC Mastery, 2024). The size for *your* client is set by how much of their traffic was unobservable to begin with — ITP, private browsing, consent denial (Vallaeys/SEL, 2026) — not by Google's median.

## Where it comes from
McNair & Meijer (2023, 2024) place enhanced conversions at the "Medior" level of their measurement maturity model — baseline hygiene whose job is to measure what tracking lost — and supply the only practitioner uplift numbers. Vallaeys (2022, 2026) supplies the mechanism and the EC-for-leads case. Google docs supply the 2026 platform changes.

## When to use it / when not to
**EC for web**: always, on every account with a form or checkout that collects an email. Hours of work, no downside, and it sits at maturity level 2, below offline import and value bidding (McNair & Meijer/PPC Mastery, 2023). The only decision is sequencing.

**EC for leads**: use when the CRM can't reliably carry the GCLID — it lets later stages be reported by hashed email instead (Vallaeys/Optmyzr, 2022) — or when GCLID coverage on CRM leads is low. Don't rely on it as the sole identifier: Google itself recommends continuing to send GCLIDs (Google Ads Help, 2026).

Don't promise a number before measuring: the uplift evidence is two anecdotes with no baseline (McNair & Meijer/PPC Mastery, 2024).

## Inputs
- Share of sessions on Safari/iOS and in private/consent-denied states (GA4)
- Current conversion actions, their tags, and whether email/phone is available at the conversion event
- GCLID coverage on CRM leads (share with a stored, valid GCLID)
- Consent Mode status (v2 required in EEA since March 2024 — McNair & Meijer/PPC Mastery, 2024)
- Developer/API path used for uploads (Google Ads API vs Data Manager)

## Method
1. **Predict the uplift before touching anything.** Unobservable share ≈ Safari/iOS share × consent-denied or ITP-affected share, plus private-browsing. If that share is under ~10%, expect little measured change on Search; if it's a third or more, expect the top of the reported range. This step is Epiminds' own prioritisation rule built on Vallaeys' mechanism (Vallaeys/SEL, 2026); it is not a canon threshold.
2. **Switch on EC for web** with email as the minimum field; phone must carry a country code and GTM auto-collection can't collect phones, so map the field explicitly (Google Ads Help, 2026). Accept the customer-data terms at the account (or manager) level first (Google Ads Help, 2026). Since April 2026 web and leads share one on/off setting (Google Ads Help, 2026).
3. **Keep the GCLID path intact.** Auto-tagging on, Conversion Linker on every landing page, and keep sending GCLIDs even with the tag (Google Ads Help, 2026). EC is a second key, not a replacement.
4. **Verify, don't assume.** Baseline 4 weeks of conversions by browser/OS before, then 4 weeks after, excluding the lag window (skill 49). The uplift should concentrate in Safari/iOS and consent-denied segments; a uniform rise across Chrome signed-in users means something else changed (Epiminds protocol; mechanism per Vallaeys/SEL, 2026). Observed and modelled conversions can't be separated in Google Ads reporting (McNair & Meijer/PPC Mastery, 2024), so do this in GA4 segments and in the Google Ads conversions-by-device view.
5. **Expect bidding to lag reporting.** Matching improves first; bidding weight follows as the system validates the new signal (Vallaeys/SEL, 2026). Don't re-set targets on the first fortnight's higher count — the CPA will "improve" on paper before behaviour changes.
6. **EC for leads decision rule.** If GCLID coverage on CRM leads is under ~80% (Epiminds threshold — the canon gives none) or the CRM team can't ship GCLID capture this quarter, implement EC for leads: capture hashed email at form submit and report stages by email (Vallaeys/Optmyzr, 2022). Route uploads through the Data Manager API — from 15 June 2026 OCI and EC-for-leads uploads are blocked in the Google Ads API, and developer tokens idle Jan–Jun 2026 are not allowlisted (Google Ads Help, 2026).
7. **Stack with Consent Mode v2** so denied-consent conversions can be modelled; McNair reports ~5% average measured uplift from modelling (McNair & Meijer/PPC Mastery, 2024) — anecdotal, so treat as a prior.
8. **Report to the client as "recovered measurement"**, not "more conversions": the sales didn't increase; the share you can see did (McNair & Meijer/PPC Mastery, 2023 — "measure lost conversions").

## What Google will tell you instead, and why we don't
Google now describes classic offline conversion import as "legacy … without the durability features" of EC for leads and recommends EC for leads for new setups (Google Ads Help, 2026). We run both identifiers: Google's own setup page says keep sending GCLIDs (Google Ads Help, 2026), and the binding constraints on lead-stage import are CRM access and timing, not the identifier (skill 48). Google's published uplift is a cross-advertiser median (its impact page could not be fetched for this dossier); we don't quote it to clients, we measure the account.

## Failure modes
- **No email at the conversion event** (anonymous checkout, phone-only leads): nothing to hash; EC does nothing.
- **Chrome-dominant, signed-in B2B desktop traffic**: little was unobservable; uplift near zero and the client feels oversold.
- **Lead gen where the lead's email differs from their Google account** (work email vs personal): match rates fall; no canon figure, so measure.
- **Tracking changes in the same fortnight**: the simulator and the bidder both need ~2 weeks of stable tracking (Google Ads Help, 2026); stack changes and you can't attribute the uplift.
- **Legacy API upload pipelines after 15 June 2026**: blocked, often silently (Google Ads Help, 2026; Vallaeys/Optmyzr, 2026 via skill 48).
- **Clients who re-set tCPA on the new count immediately**: the higher count is measurement, not efficiency; targets move after bidding weight catches up (Vallaeys/SEL, 2026).

## What to measure
Before/after 4-week windows: conversions by browser/OS and consent state; EC match rate as reported in the conversion action diagnostics; share of CRM leads with GCLID and with email; CPA by click date, matured. Ongoing: EC tag status in diagnostics; upload success on the Data Manager path.

## Open disagreements in the canon
- **How big is the uplift.** McNair's ~10% Search / 25% Video anecdotes vs Google's unfetched median vs Vallaeys' "depends on unobservable share". Epiminds: predict from the account's Safari/consent mix, verify in 4+4 weeks, promise nothing before that.
- **EC for leads vs GCLID.** Google: EC for leads is the future, OCI is legacy. Vallaeys and Google's own setup page: keep the GCLID. We run both.
- **Is this a project or hygiene?** McNair: hygiene (level 2). We agree for web; for leads it's a project only when the CRM can't carry the GCLID.
