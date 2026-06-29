---
name: self-maintaining-wiki
description: Maintain a compiled, interlinked Markdown wiki from curated sources — surgical updates, a self-healing lint suite, a claims-verification register, and a two-tier token budget.
---

You maintain a self-compiling Markdown wiki (Obsidian-style) for its owner. You own the bookkeeping; the owner owns judgment and the raw record. Each run, you ingest new sources, integrate them surgically into linked pages, check your own work, and leave the wiki more accurate than you found it.

## Configuration — EDIT THIS BLOCK FOR YOUR VAULT

- **DOMAIN:** <one line — what this wiki is about>
- **WIKI (write here):** `<path>/wiki/` — compiled pages. Flat root, optionally one or more named sub-folders for a category of pages (e.g. `Key Players/` for individuals). Wiki-links resolve by filename regardless of folder.
- **RAW (read-only sources):** `<path>/raw/` — immutable source documents. Scan for new material; never edit.
- **SOURCE LIST:** <the feeds/sites/publications to scan each run, with any credibility/editorial notes>.
- **CADENCE:** <e.g. weekly on Friday>.
- **PRIORITY LENS:** <what matters most for this domain — used to triage>.
- **REVIEW POSTURE:** <auto-publish vs. human-review-before-publish>.

## Step 0 — Read state first
1. Confirm the vault paths exist. **Never** write outside `wiki/`.
2. Read `wiki/_update-log.md` (create from template if missing): per-article HOT/WARM/COLD status, last-updated dates, the **Source Files Processed** ledger, and notes from the previous run.
3. Read `wiki/_canonical-names.md` (glossary) and `wiki/_claims-verification.md` (claims register).

## Step 1 — Choose the run tier (token discipline)
- **Lightweight scan (default):** no new sources since last run AND no significant new developments → do only Step 3 (search), Step 7 (lint), Step 8 (log). 
- **Full sweep:** new sources in `raw/` OR significant developments → all steps.

## Step 2 — Ingest new local sources, one at a time
Scan `raw/` for new files; cross-check the processed-ledger and skip anything already done. A good ingest is not "one new page" — it is tracing the new fact's implications across the graph, touching **every** page it affects.

## Step 3 — Search for new developments
Search the configured SOURCE LIST for the period since the last run, through the PRIORITY LENS. Note source, date, and key findings. Translate non-English material before integrating, attribute it, and tag confidence.

## Step 4 — Update articles surgically (never rewrite)
For each HOT/WARM or directly-affected article:
1. Read the current article.
2. **Append** a dated section `## [YYYY-MM-DD] Update — <headline>` before the See Also block. Do not rewrite the existing body. End the section with a **"Sources (this update):"** list.
3. **Supersession:** when new info changes a prior claim, update in place and add a Change Log row saying what was superseded and why — never silently delete history.
4. **Confidence tags** on every new claim: `*(high confidence — multiple sources)*`, `*(reported, [Mon YYYY])*`, `*(single source — [name])*`, `*(forecast)*`, `*(assessment)*`. Every single-source/contested claim also gets a row in `_claims-verification.md` (Step 7a).
5. Add a Change Log row.
6. Use canonical spellings (`_canonical-names.md`) and valid `[[wiki-links]]`.
New material that has no home → create a new article only if no existing one covers it; otherwise extend.

## Step 5 — Update the synthesis/risk page(s)
If the wiki has cross-cutting synthesis pages (e.g. a risk register, a strategic outlook), re-read and update them to reflect the week's changes. Add Change Log rows.

## Step 6 — Produce the digest + refresh the index
1. **Sweep-archive:** move *every* prior `Weekly Digest - *.md` from the wiki root into `digest-archive/` except today's (so strays self-heal — never leave more than the current one loose).
2. Create `Weekly Digest - [YYYY-MM-DD].md` (template): executive summary, new/updated articles, what-to-watch, sources-processed table, **Claims needing verification** (surfaced from `_claims-verification.md`), Change Log.
3. Update the index: digest link, "Last updated" date, and — **index honesty** — refresh the one-liner + date for every article changed this run.

## Step 7 — Self-healing lint suite
Run these and report findings in the digest and log:
- **Broken wiki-links:** flag `[[targets]]` with no matching file (account for sub-folders, `archive/`, `digest-archive/`); fix obvious typos, flag the rest.
- **Digest hygiene:** at most one digest loose in the root; move strays.
- **Contradiction lint:** find the same fact stated two ways across pages; record in `_claims-verification.md` + digest; resolve via supersession or annotate as contested. (An apparent contradiction may be two distinct events — reconcile rather than overwrite.)
- **Entity canonicalization:** normalise spelling/alias drift to `_canonical-names.md`; add new recurring entities; promote a high-frequency entity to a hub stub page.
- **Source-anchor:** every article has a `## Sources` section; every dated update ends with "Sources (this update):"; flag unanchored claims.
- **Index honesty:** pose ~5 representative questions; confirm the index routes each to the right page; fix gaps.
- **Stale articles:** Change Log untouched >30 days → mark COLD.
- **Outdated claims:** date-stamped claims >90 days with no corroboration → flag.
- **Index completeness:** every article (all folders) is listed in the index.

## Step 7a — Maintain the claims-verification register
`_claims-verification.md` is the system of record for single-source / contested / contradictory / date-stamped claims. Each run: add new OPEN rows; run a verification pass (ideally an **independent subagent** doing fresh search, so the check isn't the same reasoning that wrote the claim); update status to CORROBORATED / CONTESTED / RESOLVED / RETIRED with sources and date; downgrade wording on claims aged >90 days with no corroboration; surface still-open items into the digest.

## Step 8 — Rewrite the update log
Write `wiki/_update-log.md`: run date + tier; HOT/WARM/COLD per article; actions taken; processed-files ledger (append, don't overwrite); lint findings (broken links, contradictions, normalisations, source-anchor gaps, index-honesty gaps, stale, outdated); register counts (OPEN/RESOLVED/RETIRED); notes for next run.

## Token budget
Target a fixed ceiling per run. Prioritise HOT articles and new material; skip COLD when near budget and note them. Scope the lint suite to touched articles + index on a light scan, wiki-wide on a full sweep. The Step 7a verification subagent is a full-sweep activity.

## Conventions
- `[[wiki-links]]` for all cross-references; they resolve by filename across folders.
- Maintenance files (`_update-log.md`, `_canonical-names.md`, `_claims-verification.md`), the index, and the current digest live in the wiki root; `digest-archive/` holds prior digests; `archive/` holds split-out old dated sections; keep non-article files out of the article layer.
- Every article has: Sources, a Change Log table, See Also with wiki-links, and confidence tags on claims.
- Sources in `raw/` are immutable. If a source is wrong, add a correcting source; never rewrite history.
