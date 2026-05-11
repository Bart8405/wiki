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

## [2026-05-10] task | DATASET_people.csv v2 — PDD ingest + Indonesian SOEs

Expanded the people dataset to 275 verified people (from 167). Sources: 30 PDDs in `raw/Verra documents/` parsed for Project Proponent + Other Entities sections (77 PDD-derived entries including 22 LPHD heads from Delta Kapuas PDD 5834); Indonesian-language searches surfacing the SOE leadership my English searches missed (PT Indonesia Power 12 directors+commissioners verified); more direct websites (Kosher Climate, APRIL Group, AEP/Anglo-Eastern, Star Energy Geothermal — 9 directors including Pangestu and Ciputra family members, Vlinder Austria, VNV, Ata Marie).

Comparison: 1 truly missing org from DATASET_companies.csv — C-Quest Capital Stoves Asia Limited (proponent of VCS3327, VCS3328 cookstove projects). Other PDD-referenced partners not in user CSV: Wetlands International, Yayasan Puter Indonesia, Permian Global, Hutan Kencana Group, W Investment Co. Ltd., Korea-Indonesia FMU.

Detailed report at `wiki/synthesis/Task_Report_People_Dataset_v2.md`.

## [2026-05-11] task | DATASET_people.csv v3 — schema upgrade + second pass

Schema upgrade: added `project_id` (auto-computed from DATASET_companies.csv join + source string) and `trust_level` (auto-inferred: direct_website > recent_pdd > older_pdd > linkedin > news > other > none) columns to DATASET_people.csv.

PDD second pass: extracted narrative-style bios from PDD Section 2.4.3 "Management Team Experience" — these were missed by the first-pass formal-table parser. Yielded ~25 new senior-leadership entries, plus discovered politically-significant figures (Dr Stephen Shen, former Director General of Taiwan EPA, now advisor at Asia Assets Developments on Indonesian REDD+ projects).

New parent companies broken out as separate rows: Sipef Group (13 BOD), PT Tolan Tiga Indonesia (10 SIPEF Indonesia operating managers), Triputra Group (10 board+chief members, parent of PT Belantara Sejahtera Mandiri), Wildlife Works (11 leaders incl. Asia VP Brian Williams).

End state: 347 verified people, 474 total rows, ~50 companies with verified leadership. Trust levels: 242 direct_website, 67 recent_pdd, 30 older_pdd, 127 placeholder, 7 other, 1 linkedin.
