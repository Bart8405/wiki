# Log — Thematic seminar essay

## [2026-05-19] address-TODOs | Six %%TODO%% markers in active files resolved
1. **IISD 2026 numbers** — `essay-evidence.md §1` updated with new figures from `raw/New sources/IISD_Indonesia's Energy Support Measures - 2026.md`. Key addition: OECD-cited **net effective carbon price of −USD 7.8/tCO₂ in 2023** (Box 1 of IISD 2026). Sources list updated to credit IISD 2026 + OECD Feb-2026 country note as primary.
2. **Framings 2+3 fused** — `essay-master.md §1.4` rewritten. The unified framing: *"The implementation gap is the policy, and the credit-export economy is what makes it sustainable."* Move A (structural / institutional-economics) + Move B (political-economy revenue model) presented as two halves of one argument. §1.5 demoted to softer Framing-1 fallback.
3. **§2 ETS-mechanics section dropped** — old "How the ETS actually works" cut from 500 → folded into §1 as a compact ≤250-word block. New §2 reframed as "Hollow reality + broader implications" (400 words; centred on the −USD 7.8/tCO₂ finding). Structure table updated; word budget rebalanced toward §1 political-economy and §3 recommendations. Addresses the seminar feedback (cover less, deeper) and the user's stated preference for political-economy / implications emphasis.
4. **TOC links** — converted from broken markdown anchors (`#tldr--60-seconds`) to Obsidian wikilinks (`[[#TL;DR — 60 seconds|TL;DR — 60 seconds]]`). Tested against Obsidian's exact-heading-match resolver.
5. **Citation convention added** — explicit format `[Author Year, p. N](../../raw/FILE.pdf#page=N)` for PDFs with known pages; `#search=phrase` for sources without page numbers. Four worked examples included. Notes that PDF++ workflow (see `projects/personal/wiki/synthesis/pdf-highlight-workflow.md`) will make per-citation page anchors a single-click operation.
6. *(3 remaining TODOs are in `wiki/synthesis/archive/` — pre-consolidation drafts; no action needed.)*

## [2026-05-19] consolidate | Project unification — down from ~13 active files to 3
- Created [`wiki/synthesis/essay-master.md`](wiki/synthesis/essay-master.md) merging the spine of `essay-writing-tomorrow.md` + `argument-logic.md` + `essay-requirements-checklist.md` into one navigable document with TOC, TL;DR, thesis & 5 patterns, framing options, structure, drafted intro, section-by-section plan, 5-objection stress-test, requirements checklist, past-feedback section, and verification checklist.
- Created [`wiki/synthesis/essay-evidence.md`](wiki/synthesis/essay-evidence.md) merging the 3 Chain task 9 evidence briefs (fossil-fuel subsidies, Hashim/Arsari, EU CBAM) and the 24 unique sources from the two parallel overnight-search outputs into one summary table with priority reading order.
- Moved 9 superseded files + 2 raw subfolders (`Chain task 9 search`, `Overnight search`) into [`wiki/synthesis/archive/`](wiki/synthesis/archive/) — nothing deleted; all history preserved.
- Rewrote `index.md` Synthesis section to point at the three active files only.
- Active synthesis files: 3 (essay-master, essay-evidence, essay-bibliography) + sources.bib at top level. Down from 8 synthesis files + 5 raw .md files.

## [2026-05-21] polish | Task 11 — essay scaffold consistency check, paragraph skeleton, bibliography
Three deliverables:
1. **Consistency check** appended to `wiki/synthesis/essay-writing-tomorrow.md`: thesis and introduction both verified against `argument-logic.md` (passed); 7 online-only sources flagged ⚠️; Jia & Lin (2020) vs Lin & Jia (2020) author-order distinction flagged.
2. **Paragraph skeleton** added to `wiki/synthesis/essay-writing-tomorrow.md` under `## Paragraph skeleton`: 20 paragraphs across all sections, one topic sentence + main source per para. Ready for Bart to expand directly into the essay.
3. **Clean bibliography** created at `wiki/synthesis/essay-bibliography.md`: 21 sources grouped by section, all local paths verified against `raw/`, 7 ⚠️ flagged for manual download.
Chain task for Agent 12 written at bottom of `essay-writing-tomorrow.md`.

## [2026-05-21] synthesis | Task 10 — agent activity overview + essay writing guide
Created two files:
1. `projects/personal/wiki/synthesis/all-agent-activities-overview.md` — plain-English summary of all 10 agent tasks with file locations and what each produced. Bart's "I'm getting lost" request answered.
2. `wiki/synthesis/essay-writing-tomorrow.md` — self-contained essay writing guide. Contains: thesis in one sentence, word-budget table for 3k and 4k versions, section-by-section paragraph plans (what to write + exact sources for each), a drafted 400-word introduction ready to copy/edit, sources organised by section, and a 10-item fact-verification checklist. Bart should open this file tomorrow morning and start writing directly.
Updated `index.md` with the new synthesis file.
Chain task for Agent 11 written in `Box for Claude.md` as Task 11.

## [2026-05-20] research | Chain task 9 — evidence chase, counter-evidence test, thesis hook
Box task #9 completed by 7AM fallback agent. Three evidence-gap synthesis notes added to `raw/Chain task 9 search/`:
1. `DONE_Gap1_IISD-GSI-Indonesia-fossil-fuel-subsidies.md` — IDR 713.5T fossil-fuel subsidy vs IDR 78B carbon market (8,000:1 ratio); key for Objection 5 response
2. `DONE_Gap2_Hashim-Arsari-political-economy-brief.md` — focused brief pulling Hashim/Arsari findings from the parallel indonesia-carbon-market project; PR 110/2025 explicitly decouples VCM from NDC timeline; essay-use guidance included
3. `DONE_Gap3_EU-CBAM-Indonesia-exposure.md` — steel/aluminium/fertiliser CBAM exposure from 2026; fiscal self-interest argument for higher domestic price

Counter-evidence search for Framing 2: no strong counter-evidence found. BPDLH mechanism exists but scale trivial; PR 110/2025 weakened (not strengthened) domestic guardrails. Verdict appended as §3a to argument-logic.md.

Thesis hook drafted (§7 of argument-logic.md): ~160-word Framing 2 opening using Hashim/COP29 story as the opening image.

Chain task for Agent 10 written at §8 of argument-logic.md: draft Essay Section 1 (~400 words) using the hook.


## [2026-05-19] synthesis | argument-logic.md — sharpening the essay's thesis
Wrote `wiki/synthesis/argument-logic.md` (Box for Claude task #8). Did NOT write the essay. Did four things:
1. Extracted five cross-reading patterns (A: implementation gap, B: public-elite gap, C: industrial-policy entanglement, D: credit-export logic, E: hybrid-design convergence) with citation clusters per pattern.
2. Surfaced three alternative thesis framings (the current "political economy not economic design"; sharper "credit-export economy not decarbonisation economy"; most distinctive "implementation gap is the policy"). Recommended Framing 2.
3. Stress-tested Framing 2 against five likely objections with response notes.
4. Identified six concrete evidence gaps + sources to chase (IISD-GSI Indonesia fuel-subsidy literature; Hashim/Arsari political-economy via parallel project; EU CBAM exposure; coal-export consumption accounting; second LMIC comparator beyond China; institutional-economics theory for the "policy theatre" frame).
Added advisory essay skeleton (7-beat structure for Framing 2). Wrote a chain task for the next agent (Box task #9) to do the source chasing.

## [2026-05-16] scaffold | Project set up per wiki schema
- Created `raw/` (with `expert/` and `assets/` subfolders) and moved all PDFs in from the legacy "Essay - Indonesian carbon market" subfolder
- Created `wiki/{synthesis,entities,concepts}/`
- Added `index.md` cataloguing raw sources by topic cluster
- Added `wiki/synthesis/essay-direction.md` as a scratchpad for the essay thesis, outline, and source map

## [2026-05-18] scaffold | Created `sources.bib` (BibTeX bibliography for the project)
- 64 entries: ~50 PDFs in raw/ + 14 overnight-search online sources (no PDFs yet)
- Citation key convention: `firstauthor_year_shortkey`
- Custom fields: `keywords` (DONE/LOOK/MENTIONED/etc. tags + topic tags), `annote` (one-line summary), `file` (relative PDF path)
- Wired into top-level `index.md`

## [2026-05-16] rename | All raw/ and expert/ PDFs renamed to "PREFIX_Authors YYYY - Title.pdf" format
- 56 files renamed; original prefixes (DONE/LOOK/MENTIONED/NOPE/LATER/GREAT) preserved
- Fixed two mis-labelled originals: `Finkelstein and Fullerton` was actually Finkelstein Shapiro & Metcalf 2021; `Fullerton_carbon price effect on households` was actually Rausch, Metcalf & Reilly 2011
- Flagged three duplicate pairs in filenames (Fullerton 2011, Yusuf & Resosudarmo 2015, Fay et al. 2015) so the user can delete copies if desired
- Identified previously unknown PDFs via first-page extraction: Asadnabizadeh & Moe 2024, Kuncoro et al. 2025, Gatto & Sadik-Zada 2025, Rizzi 2025, Nofyanza et al. 2025, Cheong 2025, Faecks 2022 (MSc thesis), Battocletti et al. 2024, Agnolucci et al. 2024, Kochar et al. 2025, Edianto et al. 2022, Ordonez et al. 2022, Steckel et al. 2021, Dorband et al. 2019, Jakob et al. 2016
- `index.md` rewritten to reference new filenames; `wiki/synthesis/essay-direction.md` links updated

## [2026-05-17] query | Why ETS first? What should Indonesia do now? (two parallel sessions)
- Session A: Searched WB, ADB, OECD, UNDP, IISD, IEEFA, IETA, Climate Action Tracker, East Asia Forum — 14 sources in `raw/Overnight search/sources-overnight-2026-05-17.md`; answers in `wiki/synthesis/thesis-questions-answers.md`
- Session B: Searched WB, ADB, IEEFA, IESR, IMF, AMRO, IETA, ICAP — 14 sources in `raw/Overnight search/search-results-2026-05-17.md`; answers in `wiki/synthesis/thesis-questions-answered.md`
- Both sessions identified AMRO "Cap First, and Then Tax" and IEEFA 2025 ETS performance data as key new sources; WB State & Trends 2025 ($100B revenues) noted by both

## [2026-05-16] ingest | Quick skim of 6 key sources for essay framing
- ICAP factsheet 104 — Indonesia ETS (NEK) operational facts
- Sunanda et al. 2025 — SLR of 65 Indonesia carbon-pricing studies (the closest thing to a roadmap for this essay)
- Andriansyah & Hong 2022 — ASEAN+3 comparison context
- van den Bergh & Drews 2026 — developing-country carbon pricing review
- Hartono et al. 2023 — Indonesia carbon-tax CGE results
- Tony Blair Institute 2025 — international carbon markets recommendations
- Findings folded into `wiki/synthesis/essay-direction.md`
