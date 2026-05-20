---
name: Personal wiki location
description: User maintains a Karpathy-style multi-project LLM wiki at wiki/ — check the right project before answering knowledge questions
type: reference
originSessionId: d68598b4-7eca-40d7-a1d4-1fedfb617e87
---
User's personal knowledge base lives at `wiki/` inside the `code/` working directory. **Organized by project** — each project is self-contained.

- Schema and operations: [wiki/CLAUDE.md](wiki/CLAUDE.md) — defines ingest / query / lint workflows, plus how to add a new project
- Project catalog: [wiki/index.md](wiki/index.md) — read this first to identify which project a question belongs to
- Per-project files: `wiki/projects/<name>/{index.md, log.md, raw/, wiki/{entities,concepts,synthesis}/}`

Active projects (verify against `wiki/index.md`, may be out of date):
- `indonesia-carbon-market` — political economy of the Indonesian voluntary carbon market

Notes:
- When invoked from `code/` (parent dir), `wiki/CLAUDE.md` does NOT auto-load. Read it explicitly before doing wiki operations.
- Always confirm which project an operation targets — never guess. Read top-level `wiki/index.md` to see the list.
