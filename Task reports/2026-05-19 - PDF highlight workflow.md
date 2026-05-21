---
tags: [task-report, pdf, obsidian, workflow, pdf-plus, extract-highlights]
related_task: Box for Claude #12
output: projects/personal/wiki/synthesis/pdf-highlight-workflow.md
date: 2026-05-19
---

# Task 12 — PDF highlight workflow in Obsidian

## What the task asked

> *"I want to be able to open a PDF in Obsidian, highlight text in it, write comments in it and then, after doing the extract highlights command, an agent would go through all of these files, compile the highlights and my notes, create links back to the PDF — how is this doable? Additionally, the research agent doing argument framing etc for me could then reference specific pages from these PDFs and also have links to the passages it references or quotes."*

Two questions: (a) which tool / plugin makes this work in Obsidian? (b) how does the resulting output let a research agent reference specific PDF pages?

## Headline answer

**Install the PDF++ plugin.** Configure its copy-link template to wrap highlighted text in `==…==` and leave a `%%…%%` block for comments. The existing `/extract-highlights` skill then picks up PDF highlights with **no modification needed**, and the wikilink to the PDF page rides along as a clickable backlink. Research agents reading the resulting review files can cite passages with page numbers (e.g. `(Sunanda 2025, [p. 11](path/to/pdf#page=11))`) that open the PDF at the right place when clicked.

## What I did

1. **Researched plugin options** via web search and direct GitHub/docs fetches:
   - PDF++ (RyotaUshio) — actively maintained, weekly releases, latest 0.40.31 includes Obsidian 1.9 workaround
   - Annotator (elias-sundqvist) — latest release Jan 2024, 272 open issues, no recent commits → stale, ruled out
   - Verified PDF++ link syntax: `[[file.pdf#page=N&selection=...&color=...]]`
   - Verified PDF++ templating system supports custom output including arbitrary markdown wrappers

2. **Designed the workflow** with a key insight:
   - The user's existing `/extract-highlights` skill already scans for `==text==` and `%%comment%%`
   - PDF++'s template system can output exactly those markers
   - → No skill modification needed; PDF++ + existing skill = end-to-end workflow

3. **Designed the PDF++ template** to produce output the skill consumes natively:
   ```
   > [!quote|{{colorName}}] {{linkWithDisplay}}
   > =={{text}}==
   > 
   > %%(your comment)%%
   ```

4. **Mapped out research-agent reference path**: the `[[file.pdf#page=N]]` syntax in markdown notes is read directly by future agents, who can cite passages with clickable page anchors.

5. **Wrote the guide** at `projects/personal/wiki/synthesis/pdf-highlight-workflow.md`. Contents:
   - TL;DR
   - Why PDF++ over Annotator
   - Day-to-day workflow (read → highlight+comment → compile with `/extract-highlights`)
   - Setup checklist (~15 min): install, template, location, test, verify
   - PDF link syntax decoded
   - How research agents reference PDF pages
   - What does NOT change in the existing skill
   - Known gotchas (5 of them — vault location, Obsidian 1.9 bug, CSS for callouts, existing PDF annotations, sync)
   - Alternative paths (Zotero, Annotator, the existing `pdf-tool/extract.js`)
   - Recommended next step: test on one real paper

## The key design insight

The user framed the question as: "highlight PDF → annotations stored somewhere → run extract command → compile to markdown."

The actual PDF++ paradigm is: "highlight PDF → annotation paste into markdown → already lives as markdown." This means the user's mental model needed a slight rewire — but the result is *cleaner* than what they asked for: annotations never leave markdown space, they're never locked in PDF metadata, and the existing skill works without changes.

## What was NOT done

- I did NOT install PDF++ for the user (it's a manual click in Obsidian's plugin browser)
- I did NOT modify the `/extract-highlights` skill (no modification needed, by design)
- I did NOT write CSS for coloured callouts (mentioned in the guide as an optional step; PDF++ docs have the snippet)
- I did NOT test the workflow end-to-end (recommended as the next step before any further build)

## Loose ends / next steps

The guide's closing section recommends: *test on one real paper before any further build.* Once the user has tried the workflow on say a Sunanda or Hartono PDF, possible follow-ups:

1. Tune the PDF++ template if the default doesn't feel right
2. Update `/extract-highlights` to format the PDF backlinks more cleanly in the review file
3. Add a `/cite-with-page` skill that scans an essay draft and adds page anchors to citations automatically
4. Extend `essay-master.md` citations to include page anchors retroactively

None of these are needed until the basic workflow is validated on a real document.

## Sources

- PDF++ GitHub repo: https://github.com/RyotaUshio/obsidian-pdf-plus
- PDF++ backlink-highlighting basics: https://ryotaushio.github.io/obsidian-pdf-plus/backlink-highlighting-basics.html
- Effortless Academic walkthrough: https://effortlessacademic.com/working-with-pdfs-in-obsidian-pdf-plugin-and-full-text-search/
- Obsidian Stats — PDF++: https://www.obsidianstats.com/plugins/pdf-plus
- Obsidian Stats — Annotator: https://www.obsidianstats.com/plugins/obsidian-annotator
- PDF++ forum thread on highlight extraction customisation: https://forum.obsidian.md/t/pdf-plugin-highlight-extraction-customization/81979
