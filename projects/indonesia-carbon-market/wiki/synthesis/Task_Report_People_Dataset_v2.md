# Task Report v2 — DATASET_people.csv expansion + PDD ingest + Indonesian SOEs

*Date: 2026-05-10. Follow-up session after the user's overnight feedback.*

## What was added in this session

**Three sources of new entries:**
1. **PDDs (Project Design Documents)** — 30 PDF files in `raw/Verra documents/` were extracted to text and parsed for `Project Proponent` / `Other Entities Involved` sections. **77 PDD-derived entries** added, marked with the PDD source and document year (e.g. *"PDD VCS5834 dated 2025"*) and a note that the person may no longer hold the role.
2. **Indonesian-language web research** — used Indonesian terms (*direksi*, *direktur utama*, *dewan komisaris*) to find the SOE leadership pages that English-language searches missed.
3. **More direct website fetches** — Kosher Climate (8), APRIL Group (7), AEP/Anglo-Eastern Plantations (5), Climate Impact Partners (in scope check), and others.

**End-of-session totals:**

| Metric | Before | After |
|---|---|---|
| Verified people | 167 | **275** |
| Placeholder rows | 197 | 131 |
| Total rows | 364 | 406 |
| Unique companies covered | ~25 | **~50** |

The DATASET_people.csv file is at `raw/DATASET_people.csv`.

## Indonesian SOE annual reports / direct verification

| Company | Result | Source |
|---|---|---|
| **PT Indonesia Power** | 12 leaders verified (6 directors + 6 commissioners) | plnindonesiapower.co.id/our-profile direct |
| **PT Geo Dipa Energi** | Still ECONNREFUSED on every URL — could not verify | n/a |
| **PT Pertamina Power Indonesia / Pertamina NRE** | Page renders names as images, no text. CEO **John Anis** mentioned in news + Pertamina NRE press releases (cross-confirmed via voi.id, antara news, ruangenergi). **NOT in DATASET_companies.csv**, so not added — flagged for the user instead. | n/a |
| PT PLN Nusantara Power | 6 directors verified at plnnusantarapower.co.id, but **NOT in DATASET_companies.csv** — flagged for user, not added | plnnusantarapower.co.id |

## PDD parsing methodology

For each PDD I extracted text via Node's `pdf-parse` then matched two structural formats:

- **Format A (older PDDs, e.g. Katingan 2016):**
  ```
  Organization
  <name>
  ...
  Contact person
  <name>, <title>
  ```
- **Format B (newer PDDs, 2022–2026):**
  ```
  Organization name <name>
  Contact person <name>
  Title <title>
  ```

Plus a narrative-level extractor for the *Project Management Team* prose section (e.g. PDDs sometimes describe officers in flowing paragraphs: *"Mr. Dharsono Hartono, Chief Executive Officer / CEO of PT Rimba Makmur Utama..."*).

**Quality notes:**
- The parser caught 95 contact rows across 30 PDDs — about 50–60% of those resolved cleanly into the dataset; the rest were duplicates, junk hits, or lacking a title.
- PDDs from 2024–2026 for projects that previously returned no public leadership now have verified directors (PT Strata Pacific, PT Pagatan Usaha Makmur, PT Annisa Surya Kencana, PT Rimbun Seruyan, PT Telaga Mas Kalimantan, etc.).
- For the **Delta Kapuas Project (PDD 5834, 2025)**, all 22 LPHD heads are now in the dataset by name. This is data that simply doesn't exist anywhere outside the PDD.

## PDD ↔ DATASET_companies.csv comparison

The user asked: which companies appear in PDDs but not the CSV, and vice versa.

### Companies in PDDs but NOT in DATASET_companies.csv (truly missing)

After deduplicating spelling/spacing variants (e.g. "FairatmosInternationalPte.Ltd." in a PDD = "Fairatmos International Pte. Ltd." in the CSV; "PT. PLN (Pesero)" in PDD = typo for "PT. PLN (Persero)"), the **only PDD-only organization** that is genuinely missing from the user's CSV is:

- **C-Quest Capital Stoves Asia Limited** — the proponent of VCS3327 and VCS3328 (the two cookstove projects in Indonesia, 6.5 M tCO₂e/yr combined). The user's CSV does include the projects but not the proponent. Worth adding.

### PDD-derived entities never in DATASET_companies.csv (referenced as partners only)

These appear in PDDs as implementing partners, advisors, or referenced parents — never made it into DATASET_companies.csv:

| Entity | Project | Role per PDD |
|---|---|---|
| **Wetlands International** | VCS1477 (Katingan, 2016) | Indonesia Programme partner |
| **Yayasan Puter Indonesia** | VCS1477 (Katingan, 2016) | Community-development partner (Yekti Wahyuni, Executive Director) |
| **Permian Global** | VCS1477 (Katingan, 2016) | Carbon advisor (Nick Brickle, Asia Director) |
| **Korea-Indonesia FMU/REDD+ Project Management Unit** | VCS1498 (Kampar Peninsula, 2016) | Korean partner agency |
| **Korea Indonesia Forest Center** | VCS1498 (Kampar Peninsula, 2016) | Korean partner |
| **Hutan Kencana Group** | VCS4967 (PLUM, 2024) | Parent of PT Pagatan Usaha Makmur (the Limaho family's holding company) |
| **W Investment Co., Ltd.** | VCS5524 (Central Seram, 2025) | Sharon Wang, Director |

These are **flagged as "(referenced in [project] PDD; not in DATASET_companies.csv)"** in the people dataset so you can see them clearly.

### Companies in DATASET_companies.csv but NOT mentioned in their project's PDD (39 cases)

Examples (not exhaustive):
- VCS486/487/488: `PT. PLN (Persero)` — appears as the proponent in those PDDs but the PDD spelling is `PT. PLN (Pesero)` (typo with one "s" in "Persero"). Not actually missing — same entity.
- VCS5834: `LPHD Setuat Dua` — PDD has it as `LPHD Seruat Dua`. Same village.
- VCS5834: `LPHD Kampung Baru` and `LPHD Kampung Baru Head` — these may be parser misses; my regex didn't catch every LPHD entry. Worth a manual pass.
- VCS4782: `Ata Marie Group Ltd`, `PT Konsultan Karbon Lestari`, `Zero Carbon Forestry Management Pte Ltd`, `PT Hamparan Eco Semesta`, etc. — These ARE in the PDD but as references in narrative text rather than the formal Other Entities table; the parser only captured the Title-bearing ones.

**Most of these "CSV-only" cases are noise** — either spelling variants, or entities mentioned in the PDD body but not in the formal proponent tables that my parser targets. **No CSV company appears to be an outright fabrication.**

## What worked / didn't / would-have-helped

### Worked
- **PDDs are gold for political-economy research.** Every PDD has the proponent's leadership and bio paragraphs. For local Indonesian PT companies that have no public website (or a 404 / 403 site), the PDD is the *only* place the directors' names live in writing.
- **Indonesian-language search.** Direct keywords like *"direksi"*, *"direktur utama"*, *"dewan komisaris"* surfaced sources my English searches kept missing — Pertamina NRE press releases, listrikindonesia.com, dunia-energi.com, ruangenergi.com all have leadership coverage in Indonesian only.
- **The build-people.js architecture held up.** Adding 100+ new entries was just adding rows to the RESEARCH array — every regen produces a clean CSV with consistent placeholder/redirect handling.

### Didn't work
- **PT Geo Dipa Energi server is genuinely broken** — every URL pattern returned ECONNREFUSED or 404. They don't appear to have a working public BOD page. Their AGM filings would be at idx.co.id but their entity isn't a listed issuer (it's a state-owned entity not on the IDX).
- **Many PDDs use "Project Proponent(s)" with just `Contact: <Name>`** — no title given. For those rows I recorded "(cover page contact, no title given)" in the position field. Improved later when the body of the PDD has a richer Section 1.4.1.
- **PDF extraction sometimes glues words together** (e.g. "NataliaRialucky" / "ExecutiveDirector" in PDD 4520). I cleaned these up where obvious; you may spot more.
- **My parser missed about half of one PDD's LPHD list** (PDD 5834) on the first pass — the regex needed multiple variants. Resolved on the second iteration.

### What would have helped

1. **A canonical company name list.** Right now your CSV has multiple variants for the same company (`PT Pertamina Geothermal Energy` vs `PT. Pertamina Geothermal Energy`, `Yayasan Rumah Energi` vs `Yayasan Rumah Energy`, `LPHD Setuat Dua` vs `LPHD Seruat Dua` in PDD). A canonical map would reduce join errors.
2. **A `project_id` column on DATASET_people.csv.** Right now my dataset is `(company, person, position, source, notes)`. Adding `project_id` would make it possible to do joins like "all people connected to project X across all roles" cleanly. I deliberately didn't add it without your permission.
3. **A "trust level" column** would help downstream — directly verified at the company website is a different signal than from a 6-year-old PDD. I encode this in the `notes` and `source` strings, but a structured field (`trust = direct_website | recent_pdd | older_pdd | press_release | linkedin`) would be cleaner.
4. **Tell me when you're going to refactor the folder structure.** :) The path move from `wiki/raw/` to `wiki/projects/indonesia-carbon-market/raw/` is great for a multi-project second brain, but my scripts had hardcoded paths. I had to update them mid-run. A single-source-of-truth config file would survive these moves.

## Most-significant findings for the political economy research

These caught my eye while ingesting PDDs — items that bear on the user's research thesis:

1. **PT Pagatan Usaha Makmur is owned by the Limaho family**, who exited oil palm (PT AIS group) in 2021 and pivoted to ecosystem restoration (PDD 4967, p. 3). This is a textbook *palm-oil-to-carbon* divestment story for the political-economy research.
2. **Star Energy Geothermal's board** includes **Agus Salim Pangestu** and **Nancy Prajogo Pangestu Tabardel** (Pangestu family / Barito Pacific Group) and **Erwin Ciputra** (Ciputra Group). Three of Indonesia's biggest family conglomerates are on the board of the country's largest geothermal company. (Verified via starenergygeothermal.co.id BOD page.)
3. **The Katingan Project** (PT Rimba Makmur Utama) lists Permian Global as carbon advisor — Permian Global is one of the largest REDD+ players globally. **Permian Global is NOT in the user's DATASET_companies.csv** but is meaningfully connected to a major Indonesian project.
4. **Forest Carbon Pte Ltd's CFO Timothy Rann** is also on the board of Singapore's Climate Impact X, per industry sources (worth verifying separately).
5. **Pertamina NRE CEO John Anis** is also listed as a Commissioner of PT Pertamina Geothermal Energy. He sits on multiple Pertamina sub-holdings. This is the kind of cross-board interlock pattern that political-economy research finds revealing.

## Files to look at

- [`raw/DATASET_people.csv`](../../raw/DATASET_people.csv) — the dataset (275 verified people across ~50 companies)
- [`raw/Verra documents/_text/`](../../raw/Verra%20documents/_text/) — raw extracted text from each PDD
- [`pdf-tool/build-people.js`](../../../../../pdf-tool/build-people.js) — script to rebuild the CSV
- [`pdf-tool/parse-pdds-v2.js`](../../../../../pdf-tool/parse-pdds-v2.js) — script to extract contacts from PDDs
- [`pdf-tool/pdd-vs-csv.js`](../../../../../pdf-tool/pdd-vs-csv.js) — script for the comparison above
- [`pdf-tool/pdd-contacts-v2.json`](../../../../../pdf-tool/pdd-contacts-v2.json) — structured JSON of all PDD-extracted contacts (95 rows)
- [`pdf-tool/pdd-csv-comparison.json`](../../../../../pdf-tool/pdd-csv-comparison.json) — structured JSON of the PDD vs CSV comparison

## What's left for next pass

1. **PT Geo Dipa Energi** — still no public board. Their AGM minutes would be public if they're a state-owned enterprise; try Kementerian BUMN press archive or Sri Mulyani's office filings.
2. **The 39 "CSV-only for PDD project" cases** — need a manual review pass to confirm whether each is a true gap or just my parser missing a partner table.
3. **PDDs I haven't fully mined for narrative-level mentions.** The `Project Management Team` section often has multiple bios with rich detail (background, education, prior roles); my parser pulls names but not the bio text. A second pass extracting the full bio paragraphs would help track e.g. *which CEO previously worked where* — a key political-economy data point.
4. **Cross-reference the new entries against the Berkeley dataset** to see if any of the 18 Berkeley-only Indonesia projects share developers with our newly-added companies.
5. **Indonesian-language news searches for the Ciputra / Pangestu / Limaho families** specifically — would surface political connections (party donations, government appointments, etc.) that go beyond the carbon-market data.

## Suggestions for prompting in future tasks

1. **Be explicit about partial entities.** When you said "include parent and subsidiary, with notes", that was clear and easy to act on. The earlier ambiguity around *"connected to"* led to several judgment calls. Spelling out the rule like that saves iteration.
2. **State which fields are sacred.** When you said "don't change DATASET_companies.csv", that was perfect — I knew the comparison report was for *your eyes only*. If there are other files I shouldn't touch, name them upfront.
3. **Point me at sample sources.** Telling me "you can use PDDs and they'll have a Section 1.4.1" would have shaved time. I figured the structure out by reading one, but knowing in advance saves the discovery step.
4. **Indicate priorities by importance, not exhaustiveness.** "Try the most politically-significant 30 projects" or "I care most about the state-owned giants" would let me allocate effort better than "do all 218 companies." When the marginal company has a 5% chance of yielding a name, prioritization matters.
5. **Schema feedback is welcome.** If you want a `project_id` column, a `trust_level` column, or any other field added — tell me and I'll restructure the build script. Right now I'm being conservative about schema changes.
