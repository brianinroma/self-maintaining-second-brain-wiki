# Accuracy mechanisms

Rule 8 says *lint the knowledge*. These are the five checks that operationalise it — added on top of the nine principles after watching where a real wiki actually drifted. Each runs in the lint phase (Step 7 of `skill/SKILL.md`); the register has its own step (7a).

## 1. Contradiction lint (cross-page disagreement)
Scan for the same fact stated two different ways across articles — dates, figures, proper names, or the sequence of an event. A contradiction is *information*: it usually means two sources disagree, and it points you straight at what to check. For each: record it in the register and digest with both locations; resolve it where a primary source settles the matter (via supersession + a Change Log row); otherwise annotate both sides as contested and carry it forward. **Watch for false contradictions** — two figures can both be right because they describe two different events (e.g. a text signed one day, ratified at a ceremony on another). Reconcile rather than overwrite.

## 2. Entity canonicalization (spelling / alias drift)
Maintain one canonical spelling per entity in `_canonical-names.md`, with known aliases. Normalise prose and links to it (leaving variants only inside quoted titles/quotations). Drift like `Hizbullah`/`Hezbollah` or an org named in full on one page and by acronym on another fragments the facts about a single entity and weakens the link graph. New entity seen across 2+ pages → add to the glossary; seen across many → promote to a hub page.

## 3. Claims-verification register (`_claims-verification.md`)
The system of record for every single-source, contested, contradictory, or date-stamped claim — so unverified facts are *tracked*, not left to scroll out of a weekly digest into oblivion. Each run, run an **independent** verification pass — ideally a subagent doing fresh search, so the check is not the same reasoning that wrote the claim. Each item moves through OPEN → CORROBORATED / CONTESTED / RESOLVED / RETIRED with sources and a date. Claims aged past ~90 days with no corroboration get downgraded in the article wording.

## 4. Source-anchoring (compile, don't retrieve)
Every substantive claim should trace to an immutable source in `raw/` or a cited URL. The check verifies each article has a `## Sources` section and each dated update ends with a "Sources (this update):" block, and flags strong claims with no anchor. This keeps analysis from quietly detaching from evidence over many runs.

## 5. Index-honesty probe (rule 7, made testable)
The index listing every article is necessary but not sufficient — it also has to *route*. On a full sweep, pose ~5 representative questions a user would actually ask and confirm the index leads to the right page(s) without brute-forcing the vault. Equally important: when an article gets a dated update, refresh its one-liner and date *in the index*, so the map keeps matching the territory.

---

### Supporting structure
- **Hub pages** (rule 6): people, organisations, and mechanisms that recur across many articles get their own stub so they're real nodes with inbound edges, not orphans mentioned everywhere and linked nowhere.
- **Supersession over deletion**: claims are never silently removed; they're updated in place with a Change Log row recording what changed and why, so the history stays auditable.
