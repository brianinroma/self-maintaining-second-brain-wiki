# Case study: a live wiki (sanitised)

The pattern in this repo was developed maintaining a real, weekly-updated Obsidian wiki on a fast-moving geopolitical-risk domain — roughly **30 interlinked articles**, fed by think-tank reports, primary institutional documents, wire services, and multilingual press. No content from that wiki is reproduced here; what follows is the *mechanics* and what they caught, anonymised.

## Before
The wiki already followed the core principles — two layers, model-owned pages, compile-not-retrieve, wiki-links, an index, a weekly digest, and a basic lint (broken links, staleness, index completeness). It worked, but three failure modes showed up over time:

- **Unverified claims evaporated.** Single-source items were flagged in each weekly digest, then scrolled into the archive and were never chased.
- **Entity drift.** The same actor appeared under two spellings across articles; facts about it fragmented.
- **An index that lagged.** Article one-liners in the index still described the state from weeks earlier, so the "map" quietly stopped matching the territory.

## What the added checks caught
Within the first cycles of running the five accuracy mechanisms:

- **A false contradiction, correctly reconciled.** A key agreement's "signing date" was recorded two ways across pages. The contradiction lint surfaced it; an independent verification pass found *both* dates were right — one was the signing of the text, the other a later ceremony. The fix was a reconciliation note, not an overwrite. (A naive "dedupe" would have deleted a true fact.)
- **A real year-error, retired.** A recurring "conference rescheduled to late July" claim turned out to reference a *prior year's* event. The register pass retired it before it propagated further.
- **A misattributed office-holder, corrected.** A named chair of a body was verified against primary sources and corrected, with the wrong label explicitly noted so it wouldn't creep back in.
- **Spelling drift, normalised.** A glossary plus the canonicalization check collapsed two spellings of a major entity to one canonical form across the corpus.

## Token outcome
The same wiki had been at risk of growing too expensive to sweep weekly. The two-tier model meant most weeks ran light; surgical appends and archival hygiene kept the hot articles small; scoped lint kept checks cheap. Net effect: **run cost stayed roughly flat even as the corpus grew**, which is the whole game — a maintenance routine you keep running beats an ambitious one you abandon.

## Lessons
- **Track unverified claims as state, not as digest prose.** A register that ages and resolves claims is the single highest-value addition.
- **Verify with a separate pass.** The check that catches an error should not be the same reasoning that wrote it — an independent subagent doing fresh search earns its keep.
- **An index has to route, not just list.** Test it with real questions.
- **Reconcile before you delete.** Most "contradictions" are two true things; supersession-with-history beats silent correction.
