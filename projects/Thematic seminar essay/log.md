# Log — Thematic seminar essay

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
