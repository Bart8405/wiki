# Wiki Log

Append-only timeline of ingests, queries, and lints. Each entry prefixed for easy grepping.

## [2026-05-09] init | Second brain set up

Initialized wiki structure. Added `llm-wiki.md` (Karpathy's LLM Wiki pattern) and scaffolded all folders and schema files.

## [2026-05-10] ingest | Carbon market.pdf (OneNote export, 55 pages)

Ingested user's research notes on the Indonesian carbon market. Themes covered: IDXCarbon launch & operation, Pres. Reg. 110/2025, Article 6 of Paris Agreement, MRAs with Verra/Gold Standard, big-tech (Microsoft/Amazon/Google) deals, bilateral state agreements (Japan JCM, Norway, S Korea, Singapore), Indonesia's 40 IDX-listed projects by sector (21 Energy / 8 FOLU / 11 Waste). Strategic frame: research is on the political economy of the market — who wants it, who profits, whether emissions actually fall.

## [2026-05-10] ingest | DATASET_projects.csv (83 projects, Verra+GS)

Cleaned a corrupted Excel-export CSV (16,384-column artifact stripped to 32 meaningful columns). Then back-filled 34 missing rows by hitting the Verra resourceSummary API directly. Marked 4 fields with "?" where Verra returned no data (VCS5891 status, VCS5524/3327/3328 location).

## [2026-05-10] query | Differences vs Berkeley Voluntary Registry Offsets Database

Streamed the 195MB Berkeley dataset (csv-parse stream API) filtered to country=Indonesia. 89 IND projects in Berkeley, 82 in ours, 71 in both. 11 ours-only (mostly recent Verra listings pre-issuance). 18 Berkeley-only (11 Gold Standard + 7 VCS, the latter all Inactive/Rejected/Late-to-verify). Saved as `wiki/synthesis/Differences_with_Berkeley.md`. Also flagged 12 project IDs in DATASET_companies.csv that don't appear in DATASET_projects.csv (mostly PoA sub-projects).

## [2026-05-10] ingest | Verra projects.pdf

User's curated list of 63 Verra projects related to Indonesia. Cross-checked against DATASET_projects.csv: 56 of 63 already present, 7 missing (all Inactive/Rejected/Late-to-verify — likely intentional exclusions).

## [2026-05-10] task | Build DATASET_people.csv (people-by-company dataset)

New dataset linking named officers to companies. 218 unique companies in DATASET_companies.csv. End state: 167 verified people across ~25 companies, 197 placeholder rows for the rest (with notes on where someone could look next), 364 total rows. Parent-company subsidiary split applied for KIS Group, Hatfield Consultants, Nazava, Thryve Earth, Star Energy Geothermal, Value Network Ventures.

Methodology: only entries verified directly from a fetched source page; never recorded a name from a search-engine snippet without re-confirmation. Caught one factual error this way (Google synthesised "Julfi Hadi" as PGE President Director; actual page shows Ahmad Yani).

Detailed report at `wiki/synthesis/Task_Report_People_Dataset.md` including accuracy decisions, blockers, and suggested next steps. Most companies don't publish leadership; ~80 entries in DATASET_companies.csv are villages/LPHDs/cooperatives that wouldn't have C-suite leaders by definition.
