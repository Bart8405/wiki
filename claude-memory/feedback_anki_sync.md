---
name: feedback-anki-sync
description: "At session start, if the SessionStart hook flags an Anki sync check, offer to push new concept cards from the updated review files"
metadata: 
  node_type: memory
  type: feedback
  originSessionId: 555c7dfc-07f4-47bc-97e7-eeeb1789ab37
---

The SessionStart hook now surfaces a "Recent wiki activity" block that lists the last 5 commits. If any look like they touched the review files or were made by the daily extract-highlights routine (commits with "highlights", "review", "extract" in the message), the hook prints an **Anki sync check** note.

**When you see that note at session start:**

1. Briefly mention it to the user — one short line, not a wall of text.
2. Ask if Anki is open (you can also probe — `curl -s -X POST http://localhost:8765 -d '{"action":"version","version":6}'` returns instantly if AnkiConnect is reachable; ECONNREFUSED if not).
3. If Anki is open and the user says yes: run the existing pipeline:
   - `node "c:/Users/stast/OneDrive - Universiteit Leiden/Documents/code/pdf-tool/anki-from-reviews.js"` — parses IRO_review.md + PoS_review.md, builds JSON of all concept entries
   - `node "c:/.../push-anki.js" anki-batch-from-reviews.json` — pushes via AnkiConnect; dedup via `canAddNotes` so re-runs are safe (only genuinely new cards land)
4. Report: "Pushed N new cards across X decks; M dedup-skipped."
5. Don't insist if Anki isn't open — just note the daily routine has updated the review files; next time they open Anki + a Claude Code session, the same prompt will appear.

**Why this design:** the daily extract-highlights routine runs at 3 AM Amsterdam on Anthropic's cloud, with no path to localhost AnkiConnect. So the actual push happens locally when Anki is reachable. AnkiConnect's duplicate detection makes idempotency cheap — you can call the push every session safely.

**When NOT to prompt:** if the recent commits are unrelated to highlights/review files (e.g. they're a summary file edit, a task report, or just a vault backup from Obsidian Git), don't bother the user with Anki sync.
