# Dossier — 86 Attribution model comparison (DDA vs last click)

## Sources

1. **Source**: Brad Geddes, Adalysis, "The top 10 Google Ads conversion tracking mistakes" — https://adalysis.com/blog/the-top-10-google-ads-conversion-tracking-mistakes/ · **Tier** 1 · **Date** 2021-07-28 (mod. 2026-05-18) · **Claim**: Mixed attribution models across conversion actions ("one type of conversion is using one attribution model and a different conversion is using a different model") make the data messy and "bad bids are made for your account"; same for inconsistent click-through windows. Conversions tracked outside Google Ads (calls in GA/Adobe, CRM) must be imported or "you can't make decisions on them". DDA is for accounts with "a lot of conversions". · **Evidence or opinion**: Practitioner rule from audits; no numbers.

2. **Source**: Brad Geddes, Adalysis, "How to use attribution models to make data-driven PPC decisions" — https://adalysis.com/blog/use-attribution-models-make-data-driven-ppc-decisions/ · **Tier** 1 · **Date** 2018-05-01 · **Claim**: Attribution decides how conversion/revenue is divided among clicks; customers average ~6 site visits before converting (Nielsen, as cited); without a chosen model you decide on incomplete data for ad tests and negatives. Companion 2017 video post: "the real question is what model do you use based upon the question you are trying to answer." · **Evidence or opinion**: Opinion; video content not in text.

3. **Source**: Frederick Vallaeys, Search Engine Land, "Why PPC measurement feels broken (and why it isn't)" — https://searchengineland.com/ppc-measurement-broken-468574 · **Tier** 1 · **Date** 2026-02-10 · **Claim**: Google now associates conversions with prior ad interactions at an aggregate level, not by reconstructing individual click paths; "matching, attribution, and bidding are related but separate processes"; modelled conversions fill consent/identifier gaps, are validated by holdback experiments, and should be treated as an expected component; imported or modelled conversions show in reporting before they affect bidding; expect CRM and platform numbers to disagree because they answer different questions; use redundant signals (pixel + offline import + enhanced identifiers). · **Evidence or opinion**: Explanatory method; no account data.

4. **Source**: Fred Vallaeys & David Newson, Optmyzr PPC Town Hall, "What do you optimize for when the sale happens 2 years later?" — https://www.optmyzr.com/ppctownhall/optimize-ppc-long-sales-cycles · **Tier** 1 · **Date** 2026-08-12 · **Claim**: GCLID-based offline import expires 90 days after click, so long-cycle revenue can never be attributed back in-platform; feed a scored early proxy within ~2 weeks ("speed matters more than precision"); one client sources 65% of leads from LLMs, outside any Google Ads path. · **Evidence or opinion**: Practitioner method with one client example.

5. **Source**: Kirk Williams, ZATO, "How to untangle Google Ads New Customer Value, the settings checkbox, and true ROAS" — https://zatomarketing.com/blog/how-to-untangle-google-ads-new-customer-value-the-settings-checkbox-and-true-roas · **Tier** 1 · **Date** 2026-07-10 · **Claim**: With "adjust bidding to acquire new customers" checked, Conv. value and ROAS are "intentionally inflated as a bidding signal"; compare Conv. value to Original conv. value — if they differ, an adjustment is active; Original conv. value is "your ground truth". · **Evidence or opinion**: Column-behaviour method; no numbers.

6. **Source**: Sarah Stemen, Search Engine Journal (cited in dossier 79) — https://www.searchenginejournal.com/how-to-test-a-new-bid-strategy-in-google-ads/571237/ · **Tier** 2 · **Date** 2026-05-05 · **Claim**: Default Google Ads columns book conversion value to the click date; use "Conversion value (by time)" to see when value actually landed. · **Evidence or opinion**: Method.

7. **Source**: Google Ads Help, "About data-driven attribution" — https://support.google.com/google-ads/answer/6394265 · **Tier** Reference only · DDA is the default for most conversion actions; all actions eligible regardless of volume; Google recommends ≥200 conversions and ≥2,000 ad interactions in 30 days for precision; works with less but credits less precisely. The "About attribution models" and model-comparison report pages could not be fetched; the sunset of first-click/linear/time-decay/position-based models is not cited here (not fetched).

Not found: a canon source that walks the DDA-vs-last-click model comparison report with numbers. Optmyzr and Rooijmans site searches returned nothing on attribution.

## Dissenting view
Geddes (2021) wants one model and one window across all conversion actions so bidding is consistent; Vallaeys (2026) says platform and CRM numbers will disagree by design and the job is to hold both. The disagreement is about whether the goal of attribution work is a single consistent number (Geddes, for bidding) or an accepted set of disagreeing numbers, each tied to a question (Vallaeys, for reporting). Both reject using the platform's last-click or DDA figure as "the truth" for the client.

## What the platform currently does [Google docs]
- DDA default for most conversion actions; recommended ≥200 conv / ≥2,000 interactions per 30 days; no hard minimum [Google docs, answer 6394265].
- Conversions are reported by click date in default columns; "by conversion time" columns exist (Stemen, 2026; Vallaeys 2026 on lag between matching and bidding).
- GCLID offline import window: 90 days from click (Vallaeys/Newson, 2026 — practitioner statement of platform behaviour).
- New-customer value adjustments inflate Conv. value when the bidding checkbox is on; Original conv. value is unadjusted (Williams, 2026).

## Baseline check
Read `google-ads-attribution` (baseline): it explains every model, gives a "300 conversions" DDA threshold (Google's current doc says 200 recommended, none required), and says "run model comparison before switching". This skill adds: the consistency rule across conversion actions and windows, the by-time vs by-click reconciliation, the Original-vs-adjusted value check, the 90-day GCLID ceiling, Vallaeys' "separate processes" framing for explaining deltas, and a reconciliation procedure for the client-analytics gap instead of a model-selection table.

## Judgment calls
- Re-scoped the skill from "which model to pick" (default knowledge, and Google now defaults DDA) to "how to explain and reconcile the delta between Google Ads and the client's analytics/CRM, and when attribution is the wrong tool" — that is what the canon actually supports and what the row's "Use when" asks for.
- Did not cite the attribution-model sunset dates because the page could not be fetched.

- Review fix (2026-10-13): the ~10% residual stop, ≥20% assist line, ~4-week feed age and 10-point residual alert are labelled Epiminds operating thresholds; no canon source. Geddes 2017/2018 and the pre-canon baseline skill are now named in "Where it comes from".

## Canon strength: Adequate
Four Tier 1 sources with method (Geddes, Vallaeys ×2, Williams); no cross-account evidence on model deltas.

## Invalidated by
Google changing the DDA default or data recommendations, the 90-day GCLID import window, the new-customer value adjustment columns, or the by-conversion-time reporting columns.
