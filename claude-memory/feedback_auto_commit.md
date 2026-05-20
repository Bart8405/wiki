---
name: Commit automatically after meaningful wiki operations
description: User wants automatic commits after each ingest/query/lint/schema-change with a brief one-line narration of what was committed
type: feedback
originSessionId: d68598b4-7eca-40d7-a1d4-1fedfb617e87
---
After each meaningful wiki operation, commit automatically without asking first. Narrate it in one short line ("committed: ...") so the user knows what landed.

**Why:** User asked for this directly when learning the workflow. Avoids the friction of asking "ready to commit?" every time and keeps history aligned with the wiki's log.md entries.

**How to apply:**
- Trigger a commit after: each ingest, each query that produces a synthesis page, each lint pass, each schema/structure change.
- One commit per operation — don't bundle unrelated changes.
- Commit message style: match user's existing convention `<type>: <one-line description>` (types seen: setup, wiki, data, init). Add the standard Co-Authored-By trailer.
- Stage specific files by name, not `git add -A`, to avoid accidentally committing unrelated drafts or secrets.
- **Pushes are allowed** (updated 2026-05-16): the user gave blanket permission to push, especially in the context of scheduled autonomous routines that need to push their work to GitHub for the user to see it. Still avoid destructive remote operations without confirmation (force-push to main, rewriting shared history, etc.).
- If the user says "wait" or "let me review first" mid-operation, hold the commit until they OK it.
