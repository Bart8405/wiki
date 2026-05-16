# Task report — Project Index, Political Economy

**Date:** 2026-05-16
**Source task:** Box for Claude task #1 — "create a new file… Project index - Political economy… list of all the projects… organized by projects, so that when I want to know which projects are suspicious or relevant to political connections, I can find information more easily."
**Outcome:** Created [`projects/indonesia-carbon-market/wiki/synthesis/Project_Index_Political_Economy.md`](../projects/indonesia-carbon-market/wiki/synthesis/Project_Index_Political_Economy.md).

---

## What I did

Reorganised the existing [[Political_Economy_Notes]] (350 lines, organised by **theme** — family conglomerates, Taiwan network, government rollout, etc.) into a **project-first index** organised by Verra/Gold Standard project ID. Same facts, different access pattern: now you can jump to "VCS4782" and immediately see every flag that touches it, rather than having to scan every section of the PE notes.

## Structure of the new file

1. **How-to-use header** — workflow conventions for keeping the file thin and useful as PE Notes grows.
2. **Quick-scan index** — table of 26 flagged projects with a one-line "primary flag" each. Click-through anchors to the detailed entries below.
3. **Pending Verra-IDs section** — for the political networks (Arsari/Hashim, Melchor, Adaro, Harita, RGE shadow, Triputra, Misran/Fangiono, Integra) that are in the PBPH permit / market-launch queue but don't have registered Verra projects yet. Important because some of the most politically explosive material — Hashim Djojohadikusumo's ITCI Kayan Hutani — sits here.
4. **Detailed per-project entries** for the 26 flagged projects, each with:
   - Project name + location + type + status (one-line subtitle)
   - Bullet list of flags (dynasty, vertical integration, revolving door, etc.)
   - `→ [[Political_Economy_Notes#section]]` back-link to the deeper note
   - Cross-refs to other projects when same family/person/network appears (e.g. VCS4782 links to VCS5520, VCS5962, VCS4705)
5. **"Other projects" table** for the 58 carbon projects with no PE flags currently documented. Explicit caveat: *absence is not proof of cleanliness* — just that nothing has surfaced yet.
6. **Cross-cutting people networks** quick-reference table — 11 individuals (Megain Widjaja, Rio Christiawan, Brad Denig, Bushh Pangestu, Halim Rusli, Riza Suarga, Nova Misriani, Pedro Moura Costa, Galih Prasetya, Pandu Patria Sjahrir, Hashim Djojohadikusumo) and which projects each one touches.

## Assumptions / decisions made

A few judgement calls I made without being able to ask you — flagging them so you can override if you want to:

1. **Filename:** I went with `Project_Index_Political_Economy.md` (Title_Case + underscores) to match the existing synthesis-folder convention (`Political_Economy_Notes.md`, `Hashim_Djojohadikusumo_Deep_Research.md`). Your Box for Claude wording was "Project index - Political economy" — if you want the literal filename instead, easy rename.
2. **Scope of "all projects":** Your dataset has 85 carbon projects. I gave full entries to the 26 with documented PE flags and a one-row-per-project table for the rest. The alternative was a full bullet section for every project (most would say "no flags identified"), which would have bloated the file ~3× without adding signal.
3. **The "Pending Verra-IDs" section** wasn't asked for but felt necessary — some of the most politically significant material (Hashim, Melchor, Misran, etc.) involves networks that haven't yet registered Verra projects but are in the PBPH permit / Wave-1 launch queue. Suppressing them because they lack a Verra ID would have defeated the purpose of the index.
4. **Cross-cutting people table** at the end — also not asked for, but seemed valuable: same-person networks (Bushh Pangestu across 3 peatland projects, Rio Christiawan's career bridge, etc.) are easier to see in a person-first table than buried inside each project entry.
5. **Hyperlinks:** I used Obsidian-style `[[Political_Economy_Notes#section]]` anchor links back to the existing PE Notes file. Anchor names match the existing PE Notes headings. If you've renamed sections in PE Notes since I read it, the anchors may break — quick fix.
6. **Did NOT do a comprehensive re-verification** of every claim against primary sources. The file mirrors what PE Notes already asserts. If PE Notes has an inaccuracy, so does this index.

## What you might want to review

1. The file is ~470 lines. If that's too much to scan, the **quick-scan table at the top** (lines ~25–55) is the load-bearing part — everything else is reference depth.
2. The **table-of-unflagged-projects** is alphabetised within registry (GS first, then VCS). If you'd rather have it grouped by type (AFOLU vs Energy vs Waste, etc.) or by location, easy to re-sort.
3. **OKI REDD+ (VCS2395)** I tagged as "Wave 1 / Sinar Mas-adjacent" but didn't have a confirmed proponent-ownership lineage in the wiki yet. Worth pursuing.
4. **VCS3591 Mayas Project** — flagged as Wave 1 but the family-conglomerate ownership wasn't in PE Notes. Pulitzer reporting may have something I missed.
5. The **cross-cutting people table** has a column "Note" with a one-line summary. If you want more (e.g. country of citizenship, year of first appearance in carbon, last known role), that's a 30-minute follow-up.

## Wiki schema housekeeping

- Updated `projects/indonesia-carbon-market/index.md` synthesis table to include the new page.
- Appended to `projects/indonesia-carbon-market/log.md` per the CLAUDE.md ingest/synthesis convention.

## What's next

Once you've eyeballed the file:
- If the structure works for you, the same "flip thematic notes into a project-first index" pattern would work for **People** (DATASET_people.csv has 167 verified + 197 placeholder) and **Companies**. Say the word.
- If you want a similar index for **research questions** ("which projects are most likely fraud", "which projects are most vulnerable to the Hashim revolving door", etc.), that's a "Top hypotheses" synthesis page rather than an index.
