# Dossier — 81 Brand incrementality test

## Sources

1. **Source**: Nils Rooijmans, "[Performance Max] how do you make sure PMax is not going after branded searches?" — https://nilsrooijmans.com/performance-max-how-do-you-make-sure-pmax-is-not-going-after-branded-searches/ · **Tier** 1 · **Date** 2022-04-14 · **Claim**: Brand searches have "outrageously good conversion rates" and contaminate PMax conversion data; before any PMax test, add all close variants of brand keywords to the standard brand campaign (script-assisted) so exact-match keywords win the auction over PMax; this only works if the brand campaign is not budget-limited (reader correction he does not rebut). · **Evidence or opinion**: Method; cites Google's serving-preference documentation; no incrementality data.

2. **Source**: Nils Rooijmans, "Google Ads Script Review – PMax Brand Traffic Analyzer" — https://nilsrooijmans.com/google-ads-script-review-pmax-brand-traffic-analyzer/ · **Tier** 1 · **Date** 2024-06-03 · **Claim**: Measure the brand vs non-brand share of PMax conversions first ("wasteful non-brand traffic is camouflaged by highly profitable clicks from branded searches"; "conversions from branded searches inflate PMax performance and give it ample room to waste money"); then exclude brand and close variants via a shared negative list auto-populated by script from the brand campaign's search terms. · **Evidence or opinion**: Method + script (script hosted by Smarter Ecommerce); no numbers.

3. **Source**: Tyler Horner & Nick Doren (Haus), "PMAX Experiments Revealed: Including vs. Excluding Branded Search Terms" — https://www.haus.io/blog/pmax-experiments-including-excluding-branded-search-terms · **Tier** added-Tier-2 (vendor; publishes 3-cell geo design and aggregate results; contradicts Google's reported performance) · **Date** 2024-08-20 · **Claim**: 3-cell geo test (no PMax / PMax with brand / PMax without brand). Excluding brand won on incremental revenue in 50% of tests, by +24% on average when it won, and was more CAC-efficient for new customers in 100% of tests (19–60% lower CAC, ~40% average). High-AOV brands (AOV > $238) saw +27% incremental revenue with brand included. Caraway: Google overstated PMax-with-brand performance by ~33%. Signal threshold cited: ~300–1,000 monthly conversions. · **Evidence or opinion**: Aggregated test results; number of tests not stated.

4. **Source**: Thomas Blake, Chris Nosko, Steven Tadelis, "Consumer Heterogeneity and Paid Search Effectiveness: A Large Scale Field Experiment" — NBER WP 20171 (2014), Econometrica 83 (2015) — https://www.nber.org/papers/w20171 · **Tier** added-Tier-2 (academic field experiment; passes method + evidence; included because it is the only large controlled brand-search holdout in the public record) · **Date** 2014-05 / 2015 · **Claim**: In eBay's field experiments, brand keyword ads showed no measurable short-term benefit (ad clicks substituted for organic clicks); non-brand ads influenced new/infrequent users, while frequent users — most of the spend — were unaffected, so average returns were negative; paid-search returns were a fraction of non-experimental estimates. · **Evidence or opinion**: Controlled geo/market holdouts at eBay scale; abstract only fetched (no numeric estimates on the page).

5. **Source**: Frederick Vallaeys, Search Engine Land, "How Bayesian testing lets Google measure incrementality with $5,000" — https://searchengineland.com/bayesian-testing-google-measure-incrementality-466374 · **Tier** 1 · **Date** 2025-12-18 · **Claim**: Small-budget Google lift results are prior-driven; ~80% probability-of-lift justifies extending or replicating, not reallocating. (Full extraction in dossier 80.) · **Evidence or opinion**: Method with arithmetic.

6. **Source**: Google Ads Help — Conversion Lift settings https://support.google.com/google-ads/answer/12005564 ; Experiment Center https://support.google.com/google-ads/answer/16856494 · **Tier** Reference only. Google's brand-list / brand-exclusion help pages could not be fetched (two answer IDs failed); platform notes below are limited to what was fetched.

Not found: a canon source with a self-run *brand Search* holdout and numbers (Optmyzr, PPC Mastery, ZATO, Brainlabs site searches returned nothing on brand bidding; SEL and SEJ site search blocked). The eBay paper stands in as the evidence base; Nils supplies the measurement-and-exclusion method; Haus supplies the PMax-specific test design and outcome data.

## Dissenting view
Blake/Nosko/Tadelis (2015) found brand ads non-incremental at eBay, a dominant brand with top organic rank. Haus (2024) found including brand in PMax produced +27% incremental revenue for high-AOV brands and won narrowly in half of all tests. The disagreement is about organic dominance and competitor presence on the brand SERP: eBay-type brands with no competitor bidding on their name see substitution; brands with competitors conquesting or weak organic coverage see real lift. Nils does not take a position on incrementality at all; his concern is measurement contamination.

## What the platform currently does [Google docs]
- Conversion Lift user-based studies: ≥$5k budget, ≥1,000 observed conversions, 1–50% holdout, ≥14 days recommended, certainty 50–95% [Google docs, answer 12005564].
- Lift studies and experiments sit in the Experiment Center (Jan 2026) [Google docs, answer 16856494].
- PMax brand exclusions and Search brand lists exist in the UI (not fetched; not cited for rules).

## Baseline check
Read `google-ads-attribution` (brand/last-click trap) and `google-ads-experiments` (PMax vs Search). Neither gives a brand holdout design, the pre-test contamination step (brand share of PMax), the eBay finding, or the high-AOV exception. This skill adds those and a decision rule keyed to competitor presence on the brand SERP.

## Judgment calls
- Admitted an academic field experiment (eBay) as added Tier 2 evidence; it is not a practitioner, but the canon's conflict rule says evidence beats opinion and nothing else in the record is a controlled brand holdout.
- Haus admitted with the vendor caveat, as in dossier 80.
- The competitor-presence rule (step 2) is our synthesis of the eBay/Haus disagreement, labelled as such in the skill.

## Canon strength: Adequate
Two Tier 1 (Rooijmans ×2, method only; Vallaeys, method), two added Tier 2 with evidence (Haus; Blake/Nosko/Tadelis).

## Invalidated by
Removal or change of PMax brand exclusions / Search brand lists; changes to Conversion Lift minimums; Google altering serving preference between exact-match keywords and PMax for brand queries.
