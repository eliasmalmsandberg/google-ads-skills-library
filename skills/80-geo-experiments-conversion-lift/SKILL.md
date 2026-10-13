---
name: geo-experiments-conversion-lift
id: 80
description: How to get incrementality evidence for a channel or campaign using Google Conversion Lift or a geo holdout, and how to read a small-budget lift result without being fooled by the prior. Not for in-platform A/B campaign experiments (see 79) or the brand-specific holdout (see 81).
tags: Technique / All / Diagnose / Established / As needed
last_verified: 2026-10-13
invalidated_by: Changes to Conversion Lift minimums ($5k budget, 1,000 conversions, 14 days), the certainty selector, geo-based study availability, how projected cooldown conversions are included, or Google exposing/removing the priors behind its Bayesian lift estimates.
---
## What this is
A procedure for choosing between Google Conversion Lift and a self-run geo holdout, sizing the test from conversion volume, and converting the output into an "incrementality factor" that discounts platform-reported conversions. Position: Google's $5k Bayesian lift tests are usable, but a result whose probability-of-lift moves materially with the prior is a hypothesis for a bigger test, not a budget decision.

## Where it comes from
Vallaeys' walk-through of how Google's $5,000 lift tests work (informative priors + hierarchical pooling) and his worked arithmetic showing the same 25-vs-30-conversion data reads p ≈ 0.50 frequentist, ~75–80% probability-of-lift with a flat prior, and 54%→76% depending on the prior (Vallaeys/SEL, 2025). Haus's power rules, three-cell geo design, iROAS readout, incrementality factor, and contamination pitfalls (Haus, 2024; 2026 — a geo-testing vendor, cited for method and data only). Google Conversion Lift mechanics from Google Ads Help, labelled.

## When to use it / when not to
Use when a client asks whether a channel or campaign type (PMax, YouTube, Demand Gen, Display, non-brand Search) adds conversions the business would not otherwise get, before scaling or cutting it. Use after attribution comparison (86) has shown the question cannot be answered from attribution data.

Do not use when the campaign is under the Conversion Lift floor (≥1,000 observed conversions and $5,000 budget) [Google docs] *and* the account cannot support a geo split with ≥100 conversions per week per cell — at that volume only lifts above ~25% are detectable (Haus, 2026) and nothing smaller will ever be "proven". Do not run during a known seasonal peak or a promotion (Haus, 2026). Do not run a lift study on a campaign already in another study; Google allows one at a time [Google docs].

## Inputs
- Weekly conversions (observed, not modelled) for the campaign and for the business as a whole in the candidate geos.
- Platform-reported conversions/ROAS for the campaign over the last 90 days.
- Geo list with commuting-zone overlap flagged (Haus, 2026).
- Median conversion lag (for the post-test monitoring window).
- The decision the result will drive, written down with the threshold: e.g. "keep PMax if iROAS ≥ 1.5".

## Method
1. **Pick the instrument by volume.**
   - ≥1,000 weekly conversions in-scope: either instrument works; Haus's rule of thumb is ~1,000 weekly conversions to detect ~10% lift (Haus, 2026). Prefer a self-run geo split on total business revenue if the question is "does this channel move the business", because Google's study measures its own campaign's conversion actions with Google controlling exclusions and the calculation (Haus, 2026).
   - 1,000–~5,000 monthly conversions: Google Conversion Lift (user-based), which requires ≥1,000 observed conversions and ≥$5,000 budget [Google docs]; results will be prior-assisted (Vallaeys/SEL, 2025) — go to step 5. The ~5,000 ceiling is an Epiminds operating threshold — no canon source; reason: it is roughly Haus's ~1,000-weekly line (Haus, 2026), above which a self-run geo split has the power to be preferred.
   - <~100 weekly conversions: do not run a lift test; the detectable effect is >25% (Haus, 2026). Use a before/after with the incrementality factor from a comparable client as the prior, and say so.
2. **Design (geo holdout).** Three cells when comparing two treatments (control: no ads; A; B) (Haus, 2024). Exclude adjacent geos with commuting overlap from opposite cells (Haus, 2026). Outcome metric is total revenue or total conversions across all channels in the geo, not the campaign's own conversions (Haus, 2026). Minimum 14 days; extend by at least the median conversion lag before reading, up to ~3 weeks post-exposure (Haus, 2026).
3. **Design (Google Conversion Lift).** Holdout 1–50%; larger holdouts add power at opportunity cost, smaller need longer runs [Google docs]. Set certainty ≥90%; Google labels 50–90% "directional" [Google docs]. Run ≥14 days; studies shorter than that can lose up to 17% of absolute lift [Google docs]. Pick the focus metric (incremental conversions/iCPA or incremental value/iROAS) at setup [Google docs]. Note that results include projected cooldown conversions by default; read the un-modelled number from the tooltip as well [Google docs].
4. **Read the lift.** Incremental = treatment outcome − control outcome scaled to treatment size; iROAS = incremental revenue ÷ treatment spend. Haus's example: $100k spend, $300k treatment revenue, $250k scaled control → $50k incremental, iROAS 0.5× against a platform-reported 3.0× (Haus, 2026). Incrementality factor = incremental conversions ÷ platform-reported conversions for the same period (Haus, 2026).
5. **Discount for the prior (Google studies only).** Google's small-budget estimate is informative priors from similar campaigns plus hierarchical pooling; the prior is down-weighted as data accumulates but cannot be inspected (Vallaeys/SEL, 2025). Rule: if the study's probability-of-lift is ≥90% *and* in-scope conversions during the study exceed ~300, treat as evidence. If probability-of-lift is 75–90%, or conversions are under ~300, treat as a hypothesis: Vallaeys' own suggested action at ~80% is to extend, replicate or shift a small allocation, not reallocate (Vallaeys/SEL, 2025). The ~300 line is our judgment, taken from the low end of the 300–1,000 monthly-conversion signal threshold Haus cites (Haus, 2024).
6. **Act with the factor, not the lift headline.** Multiply the campaign's platform-reported conversions by the incrementality factor in the client's reporting going forward until the next test (Haus, 2026). Re-test when spend changes by more than ~50% or after 6 months — both Epiminds operating thresholds, no canon source; reason: the factor is specific to the spend level tested — Haus's YouTube case found doubling spend more than doubled new-customer orders, i.e. the factor is not constant (Haus, 2026).

## What Google will tell you instead, and why we don't
- Google's Nov 2025 announcement says its new models make results "up to 50% more conclusive" and that $5,000 now buys a test that used to need ~$100,000 [Google docs; SEL, 2025]. Vallaeys shows what "more conclusive" means: the prior from similar campaigns moves the estimate (+0.7% at 54% probability without it, +20.5% at 76% with it) (Vallaeys/SEL, 2025). We use the number, but step 5 refuses to let a prior-driven result move a budget.
- Google labels 50–90% certainty "directional" and recommends 90% [Google docs]; the UI still shows a lift figure at 50%. We do not report a lift number to a client below 90% without the "hypothesis" label.
- Google's study measures Google's campaign against Google's control, with Google controlling exclusions and projected cooldown conversions included by default [Google docs]. Haus's objection is selection bias (Haus, 2026); ours is narrower: we always read the un-modelled result alongside the modelled one, and prefer total-business revenue as the outcome when volume allows (step 1).

## Failure modes
- **Low-volume lead gen (<100 weekly conversions).** Nothing under ~25% lift is detectable (Haus, 2026); the test will come back "directional" and someone will act on it anyway. Do not start it.
- **Long-lag B2B.** Conversions land after the study window; Google's cooldown projection fills the gap with a model [Google docs]. Extend the read window by the median lag rather than trusting the projection.
- **Multi-location retail / service areas with commuter overlap.** Treatment-geo ads reach control-geo buyers; the lift is understated (Haus, 2026).
- **Promotions or PR during the window.** Any geo-asymmetric event contaminates the control (Haus, 2026).
- **Brand-heavy PMax.** The campaign's own conversions are dominated by brand searches that would have converted anyway (Google overstated PMax-with-brand by ~33% in Haus's Caraway case; Haus, 2024). Test PMax with brand excluded, or run 81 first.
- **Spend-level dependence.** The factor measured at $X/month does not hold at $2X (Haus, 2026); do not use it to justify a doubling without re-testing.

## What to measure
Per test: cells, holdout %, duration, in-scope observed conversions, certainty/probability-of-lift, modelled vs. un-modelled incremental conversions [Google docs], iROAS vs. platform ROAS (Haus, 2026), the incrementality factor, and the decision. Keep a cross-client table of factors by campaign type and spend band; it becomes the prior for the next low-volume client where no test is possible.

## Open disagreements in the canon
- **Is a $5k Bayesian lift test evidence?** Vallaeys: yes, it is math, and an 80% probability-of-lift is a legitimate input for small moves (Vallaeys/SEL, 2025). Haus: platform-run studies carry selection bias and the control should sit outside the platform (Haus, 2026). Epiminds: Vallaeys' reading for *whether to extend or replicate*; Haus's outcome metric (total-business revenue in a geo) for *whether to reallocate*. Reason: the two answer different questions, and only the second is what the client is paying to know.
- **Minimum conversion signal.** Haus cites 300–1,000 monthly conversions (Haus, 2024); Google requires 1,000 observed conversions for its user-based study [Google docs]. We take 1,000 as the floor for a Google study and ~100 weekly per cell for a geo split (Haus, 2026).
