# Token budget

A large wiki maintained naively would re-read and re-emit itself every cycle and become expensive fast. Four design choices keep each run within a fixed ceiling.

## 1. Two-tier runs
A **lightweight scan** is the default: read only HOT articles, search only HOT topics, run the lint, update the log. A **full sweep** — read/curate broadly, run the lint wiki-wide, run the verification subagent — fires only when new sources arrive in `raw/` or something significant breaks. Most weeks are light.

## 2. Surgical, not rewrites
New developments are **appended** as dated `## [YYYY-MM-DD] Update` sections; the base body is never rewritten. Changing two sentences must not cost re-emitting a 100KB article. Supersession is handled by updating the specific claim plus a Change Log row.

## 3. Archival hygiene
Dated update sections older than a set window (e.g. ~90 days) are split out of the live article into an `archive/<Article> — archived updates (pre-<date>).md` file, leaving a one-line pointer and the full Change Log behind. Hot articles stay lean to read and cheap to touch; history is preserved, not destroyed.

## 4. Scoped lint
The lint suite runs **wiki-wide on a full sweep** but is **scoped to the touched articles plus the index on a light scan**. The independent verification subagent is a full-sweep activity; on a light scan you merely age the register and surface open items.

## Putting a number on it
Set an explicit per-run ceiling (the reference deployment targeted roughly the budget of a single mid-tier subscription tier). Prioritise HOT articles and genuinely new material; when you approach the ceiling, skip COLD articles and note them for the next full sweep rather than blowing the budget. The point is predictability: a run should cost about the same each week, regardless of how big the wiki has grown.
