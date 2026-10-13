---
name: campaign-name-headline-diagnostic
id: 30
description: Diagnostic trick for seeing which campaign or ad group a live query actually fires from by placing an identifier in ad text. Not yet a runnable skill — canon is thin.
tags: Diagnostic / Search / Diagnose / Any / As needed
last_verified: 2026-10-13
invalidated_by: Not applicable until a method exists; any method depends on the 15-character path fields and the always-shown H1/H2/D1 slots.
---
STATUS: THIN CANON — needs practitioner input

## What the dossier found
No canon member publishes this trick with a method. The pages read for this category (Optmyzr 2022/2024/2026 studies, Adalysis 2022–2026, Vallaeys 2021/2022, Rooijmans' script index, PPC Mastery's public index, Google Ads Help and API pages) do not describe placing a campaign or ad group identifier in a headline, description or display path to read serving from the SERP. What the platform documents, and any future method must respect: only H1, H2 and D1 are shown on every impression, H3 and D2 are not (Google Ads Help), so an identifier in H3 or D2 is unreliable; display paths are two 15-character fields (Google Ads Help); ad-group-level customizer values override campaign-level ones and can be inserted into headlines and descriptions but not URLs (Google Ads API docs), which is the cleanest mechanism for a per-ad-group code without editing every ad.

## What is missing
- A published practitioner method: where the identifier goes (path 2 vs. a pinned D1 suffix vs. an ad-group customizer), how long it runs, and how it is removed without disturbing the test ads.
- Evidence that the identifier does not change performance while it serves (a visible code in a path or description is copy).
- The decision rules that follow from the diagnostic: when a query firing from the "wrong" ad group means a negative, a bid change, a match-type change or a structure change — i.e. the link to the cannibalisation and search-term skills.
- Whether the search terms report plus ad group segmentation already answers the question in the cases Epiminds cares about, making the SERP trick unnecessary.

## Question for Elias
When you've used this, where did you put the identifier (path 2, description, customizer) and what did you do with the answer — was it for cannibalisation between brand and non-brand, between match types, or for PMax vs Search? One or two real cases with the before/after change would give the method and the failure modes; without them the skill stays a stub rather than an invented one.
