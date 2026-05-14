# Task Report — People Dataset, Round 2 (Subset of 34 Priority Projects)

**Date:** 2026-05-14
**Output:** `raw/DATASET_people_Bart.csv` (232 rows, 34 projects)

## What you asked for

1. Look at the renamed `DATASET_people_Bart.csv` and fix names with weird symbols
2. Do another round of looking for people, **only** from companies linked to your 34 priority projects
3. Use new methods + utilise the Verra PDD/MR documents I downloaded

## What I did

### 1. File hygiene fix

The file you renamed had two problems that made it look "messed up":

- The header row had been deleted from line 1 (probably during a manual reorder in Excel) and a stray copy of the header showed up at line 18.
- The file was saved as plain UTF-8 without a BOM, so Excel was reading it as Windows-1252 — which is why names like **Matthias Tröndle**, **Patrick Bürgi**, **Stéphane Perrier** rendered with garbled letters (Tröndle, Bürgi, Stéphane).

Fix: restored the header at line 1, removed the stray header, added a UTF-8 BOM. Reopen the file in Excel — those three names should now display correctly. The actual data was never corrupted; only one byte of BOM was missing.

### 2. Second-round research

#### Method A — Deep re-scan of Verra documents I downloaded myself

I ran a pattern-matching scan over every PDD, monitoring report, validation report, and listing representation for the 34 subset projects (≈ 95 text files extracted from PDFs). Looked for patterns I'd missed in the first pass:

- "Contact person — Title" tables (sometimes updated in newer monitoring reports vs older PDDs)
- "Authorised signatory" / "On behalf of" patterns in signed deeds
- "Lead auditor / Validator / Technical Reviewer" names from validation reports
- Indonesian-language patterns (`Direktur Utama:`, `yang bertanda tangan di bawah ini`)
- "Name: X / Title: Y" signature blocks

#### Method B — Targeted web fetches for placeholder companies

For companies still tagged "(no info found)" I tried direct fetches to leadership pages I hadn't tried before (corporate sites, foundation team pages), plus Indonesian-language news searches.

### 3. New names added (15 placeholder companies resolved)

From your downloaded Verra documents:

| Company (was placeholder) | Person | Position | Source |
|---|---|---|---|
| Perkumpulan SAMPAN Kalimantan | **Fajri Nailus Subchi** | Chairman Board | PDD VCS5834 (2025) |
| Canopy Carbon PTE LTD | **Derron Leonardo Tio** | Director | MR VCS5736 (2026) |
| PT. Karbon Natura Indonesia | **Irwansyah Reza Lubis** | President Director | MRs VCS5695/VCS3591 (2025) |
| Neusa Global Pte Ltd | **Bushh Pangestu** | Director | PDD VCS5631 (2025) |
| Sinetics Accreditation Intl Taiwan | **Kai-Hsien Chen, Ph.D.** | President | PDDs VCS4381/VCS5524 (2025) |
| Agraus Resources | **Riza Suarga** | Director | MR VCS5475 (2025) |
| Riau Ecosystem Restoration | **Bradford M. Sanders** | Head of Operations | PDD VCS2403 (2025) |
| PT. SINAR MUTIARA NUSANTARA | **Rudi Hartono** | Director | PDD VCS2403 (2025) |
| PT. THE BEST ONE UNITIMBER | **Bambang Prayitno** | Director | PDD VCS2403 (2025) |
| Himpanzee Pte Ltd | **Dorjee Sun**, **Mark Harding**, **Garry Walsh** | Co-founder+CEO, Co-Founder & Head of Projects, CCO | PDD VCS2403 + himpanzee.com |
| PT Wanantara Alesha Sadhana (PT WAS) | **Dwi Shanty Apriliani Gunadi** | Head of Carbon Certification | PDDs VCS5834/VCS5873 |

From direct web fetches:

| Company (was placeholder) | Adds |
|---|---|
| UNIQUE forestry and land use GmbH | 8 staff (Wölcke, Tennigkeit, Pistorius, Antikainen, Asbeck, Nelgen, Mössinger, Seebauer) |
| Orangutan Foundation International | 8 board + Indonesia staff (Frederick Bohap Galdikas, John Beal, Janice Gleason-Skow, Ann Levine, Biruté Mary Galdikas [emeritus], Dudy Kurniawan, Renie Djojoasmoro, Robert Yappi) |
| Masarang Foundation | **Willie Smits** (Founder) — the well-known Dutch-Indonesian orangutan researcher |
| PT Indika Multi Properti (PT IMP) | **Arsjad Rasjid** (Commissioner since 2019) — also CEO of Indika Energy + former ASEAN-BAC Chair |

### 4. Politically significant finds (worth your attention)

- **Bushh Pangestu** (Director, Neusa Global) — appeared earlier as a witness on the VCS5631 Listing Representation deed. The Pangestu family controls Barito Pacific Group, one of Indonesia's largest conglomerates. **Agus Salim Pangestu** and **Nancy Prajogo Pangestu Tabardel** are already in your dataset as directors of Star Energy Geothermal (parent of VCS144 Salak + VCS688 Wayang Windu). Possibly related Pangestus across two carbon-relevant entities.
- **Riza Suarga** turns up at two different companies (PT Global Alam Lestari at VCS1899 + Agraus Resources at VCS5475) — confirmed cross-project carbon entrepreneur.
- **Arsjad Rasjid** (PT IMP, VCS5873) — Indika Energy CEO and former ASEAN-BAC Chair under Indonesia's 2023 G20 presidency. Direct political-business overlap with national climate diplomacy.
- **Dorjee Sun** (Himpanzee, VCS2403) — well-known carbon trading entrepreneur, founder of Carbon Conservation, co-founder of AirCarbon Exchange (ACX), subject of Hugh Jackman-narrated documentary *The Burning Season*. Now operationally tied to APRIL's Riau project.
- **Patrice Rene Clausse** (Star Energy director) — French executive; worth checking which Total/EDF/Engie subsidiary if you're tracking foreign capital.

### 5. Pipeline fixes

- **Multi-ID extraction bug fixed**: build-people.js was only picking up the FIRST VCS/GS ID it found in a source string. Source strings like "PDDs VCS3327, VCS3328 dated 2022" now correctly produce both project IDs. This is why VCS3328 had 0 rows in the first subset — Ken Newcombe wasn't getting tagged. Now fixed.
- **Star Energy parent → subsidiary inheritance**: tagged the parent Star Energy Geothermal rows with `VCS144` and `VCS688` so they flow into the Wayang Windu and Salak subsidiary project subsets. VCS688 jumped from 1 → 10 rows; VCS144 from 30 → 39 rows.

## Subset stats

| | Before round 2 | After round 2 |
|---|---|---|
| Subset rows | 206 | **232** |
| Placeholder rows | 31 | **16** |
| Companies covered (subset) | 114 | 115 |
| VCS3328 row count | 0 | 1 (bug fix) |
| VCS688 row count | 1 | 10 (parent inheritance) |

## Remaining placeholders in subset (16)

Mostly genuine data gaps — no publicly accessible leadership info found despite trying website + news + registry searches:

- **Indonesian operating subsidiaries with no public web presence**: PT Austral Byna, PT Navigat Organic Energy Indonesia, PT Zeus Innavitas, PT Ramang Agro Lestari, PT. GEMILANG CIPTA NUSANTARA, PT. GLOBAL ALAM NUSANTARA, PT. Medco LPG Kaji, Manggala Karbon Indonesia. These can probably only be resolved via Indonesia's AHU Online / OSS business registry (paid, authentication required).
- **LPHD village forest management institutes**: LPHD Dusun Kecil, LPHD Kampung Baru, LPHD Kampung Baru Head — per your earlier guidance, not worth deeper searches for village-level entities.
- **Redundant placeholders** (other rows exist for same entity): South Pole satellite-offices row (16 leadership entries exist), Star Energy Wayang Windu (10 parent-board entries now flow in), InfiniteEARTH (Todd Lemons entered separately).
- **World Education** (Boston NGO, VCS674): worlded.org leadership pages all return 404 to WebFetch. Could try LinkedIn or their annual report directly.
- **Deloitte Advisory (Hong Kong) Limited** (VCS5585): could try harder via Deloitte's HK office page or LinkedIn.

## What's next

If you want to push further on the remaining 16, useful next angles I haven't pursued:
- **AHU Online / OSS** (Indonesia business registry) — would resolve the small Indonesian PTs but needs paid access
- **LinkedIn manual searches** (authenticated) — would resolve Manggala Karbon, World Education, Deloitte HK
- **OpenCorporates API** — for Singapore/HK Pte Ltd entities (PT WAS, Neusa Global confirmed via PDD already)
- **Indonesian news in Bahasa**: I tried this for "PT Indika Multi Properti direktur komisaris" and it worked (found Arsjad Rasjid via JATAM + Tempo); could be repeated for other PTs

Files updated:
- [raw/DATASET_people.csv](../../raw/DATASET_people.csv) — full dataset, now 501 rows (398 verified, 103 placeholders)
- [raw/DATASET_people_Bart.csv](../../raw/DATASET_people_Bart.csv) — your 34-project subset, now 232 rows + proper UTF-8 BOM

Pipeline files in [pdf-tool/](../../../../pdf-tool/):
- `build-people.js` — main dataset generator (multi-ID extraction bug fixed)
- `filter-people-subset.js` — extracts your 34-project subset
- `rescan-subset-pdds.js` — the PDD/MR re-scan tool added this round
- `fix-bart-csv.js` — one-shot header+BOM fix for your renamed file
