# My Second Brain

A personal knowledge base organized by project, maintained using the [LLM Wiki pattern](./llm-wiki.md) by Andrej Karpathy. I source and explore, Claude writes and organizes.

## Structure

This wiki holds **multiple projects**, each fully self-contained:

```
wiki/
├── CLAUDE.md              # Schema — tells Claude how the wiki works
├── README.md              # This file
├── llm-wiki.md            # Karpathy's pattern (reference)
├── index.md               # Catalog of all projects
└── projects/
    └── <project-name>/
        ├── index.md       # Pages in this project
        ├── log.md         # Timeline of ingests/queries/lints
        ├── raw/           # Immutable source documents (I add these)
        └── wiki/          # Claude-maintained pages
            ├── entities/
            ├── concepts/
            └── synthesis/
```

## How I use it

### Adding a source (Ingest)
1. Drop a source into `projects/<project>/raw/` — an article, a paper, a PDF, a clipping.
2. Tell Claude: `ingest projects/<project>/raw/my-article.md`.
3. Claude reads it, discusses key takeaways, then writes/updates pages and appends to that project's `log.md`.

### Asking questions (Query)
Just ask Claude — it reads the relevant project's `index.md` first to find pages, then synthesizes an answer with citations. Good answers get filed back as new wiki pages so the knowledge compounds.

### Health check (Lint)
Periodically: *"Lint the carbon-market project"* — Claude checks for contradictions, orphaned pages, stale claims, and missing cross-references.

### Starting a new project
Tell Claude: *"Start a new project called X"* — it scaffolds the folders and adds it to the top-level index.

## Rules I follow

- I curate sources. Claude writes everything else.
- One source at a time when ingesting — stay involved, guide the emphasis.
- Good insights from chat get filed as wiki pages, not lost in history.
- If a project feels disorganized, lint before adding more.
- The schema (`CLAUDE.md`) evolves — update it whenever I develop a new convention.

## Tools

- **Obsidian** — for browsing the wiki, graph view, and Web Clipper for capturing sources. Open `wiki/` as a vault.
- **Claude Code** — the LLM doing all the maintenance work.
- **Git** — version history of the entire wiki for free. `wiki/` is a git repo.
