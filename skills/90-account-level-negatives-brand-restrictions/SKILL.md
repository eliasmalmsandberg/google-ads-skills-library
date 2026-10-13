---
name: account-level-negatives-brand-restrictions
id: 90
description: Decide which exclusions go in the account-level negative list, which go in a PMax-scoped list, and how brand traffic is kept out of PMax. Not for search-term mining, campaign cross-negatives or placement exclusions.
tags: Setting / All / Protect / Any / One-off
last_verified: 2026-10-13
invalidated_by: The 1,000-keyword account-level cap changing; account-level negatives gaining per-campaign-type scoping; brand exclusions reliably covering close variants (new cross-account evidence); PMax negatives at asset-group level.
---
## What this is
Three instruments, each with one job: the account-level negative list (1,000 cap, hits every Search/Shopping/PMax/App/Local campaign), a PMax-scoped shared negative list, and PMax brand exclusions. The skill is the allocation rule between them, plus the fix for the known brand leak.

## Where it comes from
Nils Rooijmans on scoping PMax negatives (2025); Fred Vallaeys / Optmyzr's 503-account PMax–Search overlap study and the brand-exclusion leak (2025); Mike Rhodes' PMax script for brand-share measurement (2026); Google Help for the current controls and the cap.

## When to use it / when not to
Use when an exclusion is needed across many campaigns at once, when PMax is live alongside a brand Search campaign, and on takeover of any account with a populated account-level list. Do not use it for per-campaign waste from search-term mining (campaign lists), for routing between Search campaigns (cross-negatives), or for Display/Video content exclusions, which are a separate 1,000-term control (Google Help).

## Inputs
- Current account-level list (Admin → Account settings → Negative keywords): count used of 1,000, match types (Google Help).
- Existing shared lists and which campaigns they are attached to.
- PMax campaigns: brand exclusions on/off, campaign-level negatives attached, Final URL expansion state (on by default — Google Help).
- Brand term set: brand, product names, common misspellings, subsidiaries.
- PMax search-category report split into brand / close-to-brand / non-brand / blank via Rhodes' PMax script with your brand terms defined (Rhodes, 2026).

## Method
1. **Account-level list is for terms wrong for the whole account, nothing else.** It applies to the search and shopping inventory of every Search, PMax, App, Shopping, Smart and Local campaign (Google Help), so anything campaign-type-specific does not belong there (Rooijmans, 2025). Admit: employment (jobs, careers, salary, intern), free/torrent/crack, adult, DIY/how-to where no content campaign exists, and competitor-support queries ("<competitor> login"). Reject: your brand, competitor brands you bid on, product categories you sell in one campaign but not another.
2. **Never put your brand in the account-level list.** It would block the brand Search campaign too; brand restriction on PMax is done in step 4.
3. **Budget the cap.** The list is capped at 1,000 keywords per account (Google Help). Keep at least 200 slots free for emergency blocks (press events, lawsuits, trademark disputes); when past 800, move category-specific entries down to campaign lists. The 200 reserve is an Epiminds operating rule, not a source number.
4. **PMax brand restriction = brand exclusions + brand campaign exact keywords + a scoped list.**
   - Turn on brand exclusions in every PMax campaign; they cover the brand name, common misspellings and subsidiaries on Search and Shopping inventory, and Google calls them the most comprehensive brand control (Google Help).
   - They leak: in Vallaeys' 503-account study, PMax still served on fuzzy brand matches with exclusions enabled, and 91% of accounts had PMax search terms exactly matching a Search keyword despite Google's stated keyword-priority rule (Vallaeys/Optmyzr, 2025). The fix is on the Search side: add branded misspellings and variants as exact-match keywords in the brand campaign so Search wins the auction (Vallaeys/Optmyzr, 2025), and make sure the brand campaign is *eligible* — not budget-capped, scheduled off, or audience-excluded, because ineligibility is a documented cause of PMax taking the query (Vallaeys/Optmyzr, 2025).
   - Backstop: a shared negative list named with a leading `*` (so it sorts first), seeded with one placeholder so it exists, attached only to PMax campaigns, and fed monthly with brand variants that still appear in the PMax search-category report plus poor PMax search terms (Rooijmans, 2025). Attach via campaign-level PMax negatives, now self-serve with an impact preview (Google Help); where unavailable, via Google's PMax modification form (Rooijmans, 2025).
5. **Match type: phrase by default, broad only for single tokens.** Negatives do not match close variants — broad "flowers" blocks "red flowers" but not "red flower" — so add plurals and spelling variants by hand; misspellings and casing are handled (Google Help). Google's default negative match type is broad (Google Help); Epiminds uses phrase for multi-word entries to avoid blocking unrelated word orders — an operating choice, not a source rule.
6. **Shopping carve-out.** If brand Shopping traffic should continue in PMax (no standard Shopping brand campaign exists), use the brand-exclusion option that lets Shopping ads keep serving (Google Help) rather than loosening the exclusion.
7. **Takeover audit.** Export the account-level list; any entry that is a product category, a geography, or a brand is misplaced — move it to the campaign that needs it. Count entries against the cap. Check every PMax campaign for brand exclusions and for Final URL expansion, which widens the query set the list must police (Google Help; see skill 88).

Output: account-level list ≤ 800 entries of whole-account terms; per-PMax campaign: brand exclusions on, `*PMax` list attached; brand campaign holds exact-match misspellings; a monthly 15-minute pass on the PMax search-category report.

## What Google will tell you instead, and why we don't
Google's PMax guidance calls negatives "a highly restrictive control" that can block valuable traffic and says to use brand exclusions instead (Google Help). Brand exclusions are necessary but not sufficient: the only cross-account measurement in the canon shows fuzzy brand matches still served with them on (Vallaeys/Optmyzr, 2025). Google also defaults negatives to broad (Google Help); a multi-word broad negative blocks the query whenever all its terms appear in any order (Google Help), so phrase is the Epiminds default for multi-word entries — the operating preference stated in rule 5, not a measured finding.

## Failure modes
- **Single-campaign accounts.** Account-level and campaign-level are the same scope; the three-instrument split is overhead. Use a campaign list.
- **Retailers whose brand is a generic word** (e.g. a brand called "Shed"): brand exclusions and brand negatives both block category demand. Restrict with exact-match brand keywords in Search and leave PMax exclusions off; measure brand share with the script instead.
- **Marketplaces and resellers** that legitimately sell competitor brands: competitor terms cannot go account-level; they belong in the specific campaigns.
- **App and Local campaigns** inherit the account-level list (Google Help); a term that is waste for Search may be the whole point of an App install campaign.
- **Accounts near the 1,000 cap** that rely on the list as their only hygiene: the cap forces migration mid-crisis; budget it in advance (step 3).
- **Low-volume PMax (< 60 conversions/30 days — Google's stated PMax minimum as cited by Hopkins/Optmyzr, 2026; used here as an Epiminds operating cut-off)**: the search-category report is too thin to show leaks; rely on brand exclusions plus Search exact keywords and skip the monthly list feed.

## What to measure
- Brand share of PMax spend and conversions, monthly, from the script's four buckets (Rhodes, 2026); target is a falling close-to-brand bucket after step 4.
- Brand Search campaign impression share and CPC before/after (Vallaeys' leak symptom was a brand CPC rise).
- Account-level list count vs cap, quarterly.
- Impact preview on each PMax negative before adding (Google Help), and PMax conversions 30 days after, to catch over-blocking.

## Open disagreements in the canon
Rooijmans (2025) keeps PMax negatives out of the account-level list entirely; Google Help now routes account-level negatives into PMax automatically, which makes the whole-account entries (jobs, free, adult) the one case where account-level is the right PMax tool. Epiminds therefore splits by *reason* for exclusion rather than by campaign type: whole-account reasons go account-level, PMax-only reasons go to the scoped list. On brand, Vallaeys (2025) fixes the leak with positive keywords in Search while Rooijmans (2025) feeds a negative list; we do both, because one acts on auction priority and the other on eligibility. No canon source has measured the performance effect of account-level negatives themselves.
