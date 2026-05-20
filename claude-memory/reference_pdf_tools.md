---
name: reference-pdf-tools
description: Two ways to read PDFs (cheap text extraction vs expensive image rendering); use the triage tool to pick
metadata: 
  node_type: memory
  type: reference
  originSessionId: 555c7dfc-07f4-47bc-97e7-eeeb1789ab37
---

Two complementary tools for reading PDFs from the user's wiki/projects:

**1. `pdf-tool/extract.js` — text extraction (cheap)**
- Uses `pdf-parse` (pure-JS, no system deps).
- Usage: `node extract.js <input.pdf> <output.txt>`
- Best for: academic articles, modern textbook chapters, anything with a clean digital text layer.
- Output: plain text saved to file; I then Read the .txt file.

**2. Built-in Read tool with `pages: "1-N"` — image rendering (more tokens)**
- Backed by Poppler's `pdftoppm` (installed 2026-05-19 via `winget install oschwartz10612.Poppler`).
- Renders each PDF page as an image I can see visually.
- 20-page max per call; `pages` parameter required for any PDF over ~10 pages.
- Best for: image-based scans, image-heavy lecture slides (charts, diagrams), handwritten/highlighted annotations.

**3. `pdf-tool/triage-pdf.js` — decide which to use**
- Usage: `node triage-pdf.js <input.pdf>`
- Reports: chars/page ratio, garbage-pattern hits, verdict (TEXT-OK / IMAGE-BASED / IMAGE-HEAVY-SLIDES / MIXED).
- Run this first when you don't know what kind of PDF it is.

**Routing heuristic (when in doubt):**
- `chars < 300` total OR `chars/page < 100` → IMAGE-BASED → use Read tool.
- Leiden lecture template garbage (`!"#$%&D(...)`) + `chars/page < 500` → IMAGE-HEAVY-SLIDES → Read tool for visuals.
- `chars/page < 300` (clean) → MIXED → try extract.js first, spot-check with Read tool.
- `chars/page ≥ 300` (clean) → TEXT-OK → extract.js (cheap, fast).

**When to default to which without triage:**
- Academic article PDFs (journal articles, book chapters, reports) → extract.js.
- Lecture slide PDFs → likely IMAGE-HEAVY-SLIDES → Read tool (or triage first).
- Anything user describes as "scanned" or "annotated" → Read tool.
- Large textbook (Heywood, full books) → extract.js (text-OK + length makes image rendering wasteful).

Don't render PDF pages as images by default — it costs more tokens. Always cheap-first.
