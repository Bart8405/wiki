---
tags: [obsidian, pdf, highlighting, workflow, pdf-plus, extract-highlights, research]
sources:
  - https://github.com/RyotaUshio/obsidian-pdf-plus
  - https://ryotaushio.github.io/obsidian-pdf-plus/backlink-highlighting-basics.html
  - https://effortlessacademic.com/working-with-pdfs-in-obsidian-pdf-plugin-and-full-text-search/
  - Box for Claude task #12
updated: 2026-05-19
---

# PDF highlight workflow — Obsidian + PDF++ + /extract-highlights

*The complete answer to Box for Claude task #12: how to highlight PDFs in Obsidian, write comments on them, run /extract-highlights to compile your annotations, get clickable backlinks to specific PDF pages, and let research agents reference exact passages with page numbers.*

---

## TL;DR — the answer in one paragraph

Install the **PDF++** community plugin. It transforms Obsidian into a PDF reader where selecting text and pressing a shortcut copies a wikilink like `[[paper.pdf#page=5&selection=4,0,7,12]]` into your clipboard. Paste that into any markdown note, optionally with a `==highlighted text==` block and a `%%comment%%`, and you've created a backlink that (a) opens the PDF at exactly that passage when clicked, (b) visibly highlights the passage in the PDF when the plugin is enabled, and (c) gets picked up by your existing `/extract-highlights` skill *without any modification* — because the output is already a normal markdown file with `==` and `%%` markers. Research agents reading the resulting review files can then cite passages with page numbers and clickable backlinks to the source PDF.

---

## Why PDF++ and not Annotator

The two main candidates are:

| Plugin | Status (2026) | Storage model | Verdict |
|---|---|---|---|
| **PDF++** (RyotaUshio) | Actively maintained; ~weekly releases; Obsidian 1.9 workaround in v0.40.31 | Highlights live as wikilinks in your **markdown notes**; the PDF is untouched | ✅ Recommended |
| **Annotator** (elias-sundqvist) | Latest release Jan 2024; 272 open issues; no recent commits | Hypothesis-based; sidecar JSON in markdown frontmatter | ⚠️ Stale |

PDF++ also matches your existing wiki philosophy perfectly: **annotations are markdown, not buried in PDF metadata.** If the plugin ever stops working, your highlights are still readable plaintext.

---

## How the workflow looks day-to-day

### Step 1 — Read

Open a PDF in Obsidian. With PDF++, the built-in PDF viewer gains a toolbar with a colour palette and a side panel.

### Step 2 — Highlight + comment

Select text → press your configured shortcut (default `Ctrl+Shift+C` or right-click → "Copy link to selection"). The clipboard now holds something like:

```markdown
> [!quote|yellow] [[Hartono et al 2023.pdf#page=5&selection=12,0,15,40|Hartono 2023, p. 5]]
> ==Indonesian carbon tax revenue recycling raises GDP and employment in CGE modelling==
> 
> %%This is the cleanest Indonesia-specific case for the double-dividend claim%%
```

Paste it into a markdown note (e.g. `projects/Thematic seminar essay/wiki/synthesis/reading-notes-hartono.md`). The text appears in your note AND is now visibly highlighted in the PDF when you open it.

### Step 3 — Compile

When you run `/extract-highlights`, the existing skill:
- Finds the `==Indonesian carbon tax revenue recycling…==` as a highlight (its current behaviour)
- Finds the `%%This is the cleanest…%%` as the attached comment
- Includes the link `[[Hartono et al 2023.pdf#page=5...]]` verbatim in the "Seen in" backlink it already generates

Result: your review file gets an entry like:

> **Hartono 2023 — revenue recycling**
> *Indonesian carbon tax revenue recycling raises GDP and employment in CGE modelling*
> Seen in: [[Hartono et al 2023.pdf#page=5]] — click to jump to the exact passage in the PDF
> Your note: "This is the cleanest Indonesia-specific case for the double-dividend claim"

The crucial insight: **the existing `/extract-highlights` skill needs no modification.** PDF++ outputs markdown that conforms to the patterns the skill already scans for (`==text==` and `%%comment%%`). The PDF backlink simply rides along as the "Seen in" reference.

---

## Setup checklist (~15 minutes)

### 1. Install PDF++

In Obsidian: **Settings → Community plugins → Browse → search "PDF Plus"** → install + enable.

### 2. Configure the copy-to-clipboard template

Settings → PDF++ → **"Copy formats"** (or similar — the panel label varies slightly across releases).

Set the default copy template to this (paste verbatim):

```
> [!quote|{{colorName}}] {{linkWithDisplay}}
> =={{text}}==
> 
> %%(your comment)%%
```

**What this does:**
- `[!quote|color]` — a coloured callout (Obsidian renders it as a tinted block)
- `{{linkWithDisplay}}` — the wikilink with author/page as display text (e.g. `[[Hartono.pdf#page=5|Hartono p. 5]]`)
- `=={{text}}==` — the highlighted text wrapped in your existing `==highlight==` marker so `/extract-highlights` picks it up
- `%%(your comment)%%` — empty Obsidian comment marker, ready for you to type into

The `==text==` and `%%comment%%` markers are the magic — they make the existing skill work on PDF highlights without modification.

### 3. Configure where PDF++ looks for backlinks

Settings → PDF++ → **"Annotation files"** (or "Default note location"). Set to: `projects/{{pdfFolder}}/wiki/entities/sources/` — this creates one note per PDF inside your existing wiki structure.

### 4. Test it once

Open any PDF in `projects/Thematic seminar essay/raw/`. Select a sentence. Hit the copy shortcut. Paste into a scratch note. You should see the coloured callout, the highlighted text, the link. Click the link — the PDF opens at the right page.

### 5. Re-open the PDF

The highlighted text should now appear visually highlighted in the PDF itself (because PDF++ reads your vault, finds the backlink, and renders the highlight in the viewer).

---

## The PDF link syntax explained

The link PDF++ generates looks like:

```
[[file.pdf#page=5&selection=4,0,7,12&color=yellow|display text]]
```

| Component | Meaning |
|---|---|
| `file.pdf` | The PDF file path (relative to vault) |
| `#page=5` | Open at page 5 — works in any Obsidian PDF viewer, not just PDF++ |
| `&selection=4,0,7,12` | Character coordinates (start line, start char, end line, end char) — used by PDF++ to render the highlight |
| `&color=yellow` | Highlight colour (optional) |
| `\|display text` | What renders in the markdown (e.g. "Hartono p. 5") |

**Crucial fact:** `#page=N` is a standard Obsidian PDF anchor and works *without* PDF++ enabled. So even if you ever stop using PDF++, all your backlinks still open PDFs at the right page. Your annotations are not locked in.

---

## How research agents can reference PDF pages

This is the second half of your task #12 question. The same workflow gives you this for free:

### When an agent reads your notes

When I (or any future research agent) read `projects/Thematic seminar essay/wiki/synthesis/reading-notes-hartono.md`, I see:

```markdown
> [!quote|yellow] [[Hartono et al 2023.pdf#page=5|Hartono p. 5]]
> ==Indonesian carbon tax revenue recycling raises GDP and employment==
> %%cleanest Indonesia-specific double-dividend case%%
```

I can extract:
- the **quote** (from `==...==`)
- the **source + page** (from the wikilink)
- your **interpretation** (from `%%...%%`)

### When an agent writes synthesis

The agent can produce citations like:

> Hartono et al. (2023) find revenue recycling raises both GDP and employment ([p. 5](Hartono%20et%20al%202023.pdf#page=5)).

When you click "p. 5" in Obsidian, the PDF opens to that exact page. This is the clickable-to-source workflow you asked for.

### What changes in the master files

`projects/Thematic seminar essay/wiki/synthesis/essay-master.md` already cites sources by author-year. After adopting this workflow, each citation can additionally carry a `[#page=N]` anchor:

> *"$2 vs $30 trajectory" (Sunanda et al. 2025, [p. 11](../../raw/expert/GREAT_Sunanda%20et%20al%202025...pdf#page=11))*

Manual at first; eventually automatable via a small extension to `/extract-highlights`.

---

## What does NOT change about the existing skill

Re-stating the key insight because it's the most important thing in this guide:

> **The `/extract-highlights` skill already works on PDF highlights — *if* PDF++ is configured with the template above.**

No code changes. No skill rewrite. The PDF++ template wraps the highlighted text in `==…==` and the comment in `%%…%%`, which are the exact patterns the skill already recognises. The PDF page link comes along as extra context in the "Seen in" line.

If you want to go further later (e.g. have the skill format the "Seen in" line with a clickable page number rather than the raw wikilink), that's a small enhancement we can do once you've used the workflow on a real paper.

---

## Known gotchas

1. **PDF must be inside the vault.** PDF++ reads relative paths. Your `raw/` PDFs are inside `wiki/`, so this works. PDFs anywhere else won't.
2. **Obsidian 1.9 text-selection bug.** Affects copying links from text selections in some PDFs. PDF++ v0.40.31+ has a workaround — make sure you install the latest version, not whatever's bundled in older Obsidian guides.
3. **Coloured callouts need a CSS snippet** to render with the highlight colour by default. PDF++ docs include the snippet, or you can skip the colour and rely on just the `==yellow text==` rendering Obsidian does natively.
4. **PDFs you've already highlighted in another tool** (Acrobat, Preview) won't auto-import. PDF++ doesn't read existing PDF annotations. You'd have to re-highlight in Obsidian, OR use PDF++'s experimental "direct edit" mode (carries data-loss risk — skip unless you know what you're doing).
5. **Vault sync.** If you sync your vault across devices, PDF++ annotations sync because they're markdown. The actual PDFs sync if you sync the `raw/` folder. OneDrive on your current setup will handle both.

---

## Alternative paths (in case you want to evaluate)

| Path | When it makes sense | Trade-off |
|---|---|---|
| **PDF++ (recommended)** | You want highlights as markdown, native to Obsidian, with clickable backlinks | Some setup; one-week learning curve |
| **Zotero + Better BibTeX + Citation plugin** | You already use Zotero heavily; want a separate library outside Obsidian | Annotations stay in Zotero, not Obsidian; bigger system |
| **Annotator** | You want Hypothesis-style annotation with margin pins | Stale plugin (no commits since Jan 2024); bigger risk of breaking |
| **Your existing `pdf-tool/extract.js`** | Whole-PDF text extraction (already in use) | Doesn't capture *your* highlights — just dumps text |

PDF++ wins on every axis except "no installation needed."

---

## Recommended next step

Try the workflow on **one paper** from `raw/` for the Thematic seminar essay — pick something you'd be re-reading anyway, like Sunanda et al. 2025 or Hartono et al. 2023. Highlight 5–10 passages, add 2–3 comments, then run `/extract-highlights`. Tell me what came through and what didn't. From there I can:

- Tune the PDF++ template if needed
- Update `/extract-highlights` to format the PDF backlinks more cleanly in the review file
- Add a separate `/cite-with-page` skill that scans your essay draft and adds page anchors to citations automatically

But install + try first; the rest follows from one real test.

---

## Sources

- PDF++ GitHub repo (canonical docs): https://github.com/RyotaUshio/obsidian-pdf-plus
- PDF++ backlink-highlighting basics: https://ryotaushio.github.io/obsidian-pdf-plus/backlink-highlighting-basics.html
- Effortless Academic guide (third-party walkthrough): https://effortlessacademic.com/working-with-pdfs-in-obsidian-pdf-plugin-and-full-text-search/
- Obsidian Stats page for PDF++ (release history, install count): https://www.obsidianstats.com/plugins/pdf-plus
- Annotator plugin (the dormant alternative): https://www.obsidianstats.com/plugins/obsidian-annotator
