# Wiki Schema

This file tells Claude how this wiki is structured and how to operate on it. Evolve it over time as conventions solidify.

## Structure

```
wiki/
├── raw/              # Immutable source documents — never modify these
│   └── assets/       # Downloaded images referenced by raw sources
├── wiki/             # Claude-maintained pages
│   ├── entities/     # Named things: people, places, projects, tools
│   ├── concepts/     # Ideas, frameworks, mental models, theories
│   └── synthesis/    # Analyses, comparisons, answers worth keeping
├── index.md          # Master catalog — update on every ingest
├── log.md            # Append-only timeline — append on every operation
├── llm-wiki.md       # The pattern this wiki is based on (read-only reference)
├── CLAUDE.md         # This file
└── README.md         # Human-facing overview
```

## Conventions

- All wiki pages live under `wiki/`. Raw sources live under `raw/`. Never mix them.
- Page filenames: lowercase, hyphen-separated (e.g. `sleep-and-cognition.md`).
- Every wiki page starts with a `# Title` and a one-line summary in italics beneath it.
- Use `[[wiki/concepts/concept-name]]` style links for cross-references between wiki pages.
- Add YAML frontmatter to wiki pages: `tags`, `sources` (list of raw files that informed it), `updated` (date).

## Operations

### Ingest
When told to ingest a source:
1. Read the source file from `raw/`.
2. Discuss key takeaways with the user.
3. Write a summary page in `wiki/` (or update an existing one).
4. Update or create relevant entity and concept pages.
5. Update `index.md` with any new pages.
6. Append to `log.md`: `## [YYYY-MM-DD] ingest | Source Title`

### Query
When asked a question:
1. Read `index.md` to find relevant pages.
2. Read those pages and synthesize an answer with citations.
3. If the answer is valuable, offer to save it as a new page under `wiki/synthesis/`.
4. Append to `log.md`: `## [YYYY-MM-DD] query | Question summary`

### Lint
When asked to lint:
1. Check for contradictions between pages.
2. Find orphaned pages (no inbound links).
3. Find concepts mentioned but lacking their own page.
4. Identify stale claims superseded by newer sources.
5. Suggest missing cross-references and sources worth finding.
6. Append to `log.md`: `## [YYYY-MM-DD] lint | Summary of findings`
