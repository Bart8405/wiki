# Wiki Schema

This wiki is organized by **project**. Each project is a self-contained second brain with its own raw sources, pages, index, and log. Shared infrastructure (this schema, the Karpathy reference, the human README) lives at the top level.

## Structure

```
wiki/
├── CLAUDE.md            # This file — the schema (shared)
├── README.md            # Human-facing overview (shared)
├── llm-wiki.md          # Karpathy's LLM Wiki pattern (shared, read-only reference)
├── index.md             # Top-level project catalog
└── projects/
    └── <project-name>/
        ├── index.md     # This project's master catalog of pages
        ├── log.md       # This project's append-only timeline
        ├── raw/         # Immutable source documents — never modify
        │   └── assets/  # Downloaded images referenced by raw sources
        └── wiki/        # Claude-maintained pages
            ├── entities/    # Named things: people, places, projects, tools
            ├── concepts/    # Ideas, frameworks, mental models, theories
            └── synthesis/   # Analyses, comparisons, answers worth keeping
```

## Conventions

- All wiki pages live under a project's `wiki/` folder. Raw sources live under that project's `raw/`. Never mix them.
- Page filenames: lowercase, hyphen-separated (e.g. `sleep-and-cognition.md`).
- Every wiki page starts with a `# Title` and a one-line summary in italics beneath it.
- Use `[[wiki/concepts/concept-name]]` style links for cross-references *within* a project.
- For cross-project links (rare, only when genuinely useful), use a relative path like `[[../other-project/wiki/concepts/x]]`.
- Add YAML frontmatter to wiki pages: `tags`, `sources` (list of raw files that informed it), `updated` (date).
- Project folder names: lowercase, hyphen-separated, descriptive (e.g. `indonesia-carbon-market`, not `wiki2` or `proj1`).

## Identifying the active project

Operations always run in the context of one project. If the user does not name a project, ask which one — never guess. Read `wiki/index.md` to see the full list.

## Operations

### Ingest
When told to ingest a source:
1. Confirm which project the source belongs to.
2. Read the source file from `projects/<project>/raw/`.
3. Discuss key takeaways with the user.
4. Write a summary page in `projects/<project>/wiki/` (or update an existing one).
5. Update or create relevant entity and concept pages within that project.
6. Update `projects/<project>/index.md` with any new pages.
7. Append to `projects/<project>/log.md`: `## [YYYY-MM-DD] ingest | Source Title`

### Query
When asked a question:
1. Confirm which project the question is about.
2. Read `projects/<project>/index.md` to find relevant pages.
3. Read those pages and synthesize an answer with citations.
4. If the answer is valuable, offer to save it as a new page under `projects/<project>/wiki/synthesis/`.
5. Append to `projects/<project>/log.md`: `## [YYYY-MM-DD] query | Question summary`

### Lint
When asked to lint:
1. Confirm which project to lint (or "all").
2. For each project: check for contradictions between pages, find orphaned pages, find concepts mentioned but lacking their own page, identify stale claims, suggest missing cross-references.
3. Append to that project's `log.md`: `## [YYYY-MM-DD] lint | Summary of findings`

### New project
When the user wants to start a new project:
1. Pick a folder name (lowercase, hyphen-separated, descriptive).
2. Scaffold: `projects/<name>/{raw/assets,wiki/{entities,concepts,synthesis}}/` and empty `index.md` + `log.md`.
3. Add a row to top-level `wiki/index.md` under "Projects".
