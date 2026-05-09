# My Second Brain

This is my personal knowledge base, maintained using the [LLM Wiki pattern](./llm-wiki.md) by Andrej Karpathy. Claude Code acts as the LLM maintainer — I source and explore, Claude writes and organizes.

## How I use it

### Adding new knowledge (Ingest)

1. Drop a source into `raw/` — an article clipped with Obsidian Web Clipper, a paper, a PDF, notes from a podcast, anything.
2. Tell Claude: `ingest raw/my-article.md` — it reads the source, discusses key takeaways with me, then writes or updates the relevant wiki pages and appends to `log.md`.
3. I review the changes in Obsidian, follow the links, and redirect Claude if something needs more depth.

### Asking questions (Query)

Just ask Claude anything. It reads `index.md` first to find relevant pages, then synthesizes an answer with citations. Good answers get saved back as new wiki pages so the knowledge compounds.

Example: *"What do I know about sleep and productivity?"* → Claude finds relevant pages, synthesizes, and files the answer in `wiki/synthesis/sleep-productivity.md`.

### Keeping it healthy (Lint)

Periodically: *"Lint the wiki"* — Claude checks for contradictions, orphaned pages, stale claims, and missing cross-references. It also suggests new sources worth reading.

## Structure

```
wiki/
├── raw/          # Immutable source documents (I add these, Claude never modifies them)
├── wiki/         # LLM-maintained markdown pages (Claude owns this)
│   ├── entities/ # People, places, projects
│   ├── concepts/ # Ideas, frameworks, mental models
│   └── synthesis/# Analyses, comparisons, answers worth keeping
├── index.md      # Master catalog of all wiki pages (Claude keeps this current)
├── log.md        # Append-only timeline of ingests, queries, and lints
├── llm-wiki.md   # The pattern this wiki is based on (Karpathy)
└── CLAUDE.md     # Schema — tells Claude how this wiki works (evolves over time)
```

## Rules I follow

- I curate sources. Claude writes everything else.
- One source at a time when ingesting — stay involved, guide the emphasis.
- Good insights that come up in chat get filed as wiki pages, not lost in history.
- If the wiki feels disorganized, lint before adding more.
- The schema (`CLAUDE.md`) evolves — update it whenever I develop a new convention.

## Tools

- **Obsidian** — for browsing the wiki, graph view, and Web Clipper for capturing sources.
- **Claude Code** — the LLM doing all the maintenance work.
- **Git** — version history of the entire wiki for free.
