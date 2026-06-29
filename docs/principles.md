# Principles

The system rests on nine ground rules, adapted from Andrej Karpathy's working notes on LLM-maintained knowledge bases (*LLM-WIKI.md*). The accuracy and token layers in this repo are built on top of them.

1. **Sources are immutable.** Everything you save lands in `raw/` and is never edited after it lands. If a source is wrong, add a *correcting* source — don't rewrite history. The moment you hand-edit raw files you have two systems of record and no way to tell which is true.

2. **Separate the layers.** Three layers, three owners. `raw/` holds immutable sources and belongs to you. `wiki/` holds generated pages and belongs to the agent. A single schema file (the run protocol) holds the rules and belongs to both. Don't blur them.

3. **The model owns the wiki.** You choose what enters `raw/`, ask questions, and think. The agent summarises, cross-references, files under the right entity, and updates neighbours when something new arrives. If you find yourself doing the bookkeeping, the schema is underspecified — fix the protocol, not the symptom.

4. **Compile, don't retrieve.** This is not RAG. RAG re-derives an answer from raw chunks on every query and accumulates nothing. Here, sources are compiled once into structured, linked pages, and questions are answered from the built artifact. Knowledge that is compiled compounds; knowledge that is retrieved is rediscovered.

5. **Ingest one source at a time.** A good ingest is not one new page — it is the model tracing the implications of that source across the graph, touching every page the new fact changes. Batch-importing your whole digital life in a weekend produces a dump, not a wiki.

6. **Link everything.** Every page connects to others through wiki-links; every link is a visible edge in the graph. An entity that appears in five pages but links to none is a sign the ingest was lazy. The value of the system is in the edges, not the nodes — which is why high-frequency entities get promoted to their own hub pages.

7. **Navigate by index.** The model should reach an answer by reading the index, following a few relevant pages, and synthesising — not by loading the whole vault into context. If it's brute-forcing the corpus on every question, the index has stopped reflecting the territory and needs a pass. (See the index-honesty probe in `accuracy.md`.)

8. **Lint the knowledge.** Treat the wiki like code and run health checks: contradictions between pages, low-confidence claims, orphans, entities that drifted into two spellings. A contradiction is information, not an error to paper over. Skipping the lint is how a wiki quietly rots while the graph still looks impressive.

9. **Start small.** Begin with ten sources, not ten thousand. Get ingest, query, and lint to feel natural before you add a search engine, elaborate frontmatter, or a schema with twenty rules. The first few ingests need supervision; naming conventions will change and early pages will be messy. A small wiki you actually feed beats a beautiful architecture you abandon in week three.
