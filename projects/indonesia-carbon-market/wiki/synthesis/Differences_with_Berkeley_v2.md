---
tags: [berkeley, dataset-coverage, dataset-comparison, verra, gold-standard]
sources:
  - raw/DATASET_projects.csv
  - raw/Berkeley_dataset.csv
  - Verra public API (registry.verra.org/uiapi/resource/resourceSummary)
  - Gold Standard PoA documentation
updated: 2026-05-15
---

# Differences with Berkeley — v2

*Refreshed comparison with project-by-project status verification from the Verra API and explanations grouped by underlying cause. Supersedes the 2026-05-09 report.*

## Sources

- **Our project dataset:** `raw/DATASET_projects.csv` — 82 distinct project IDs
- **Our company dataset:** `raw/DATASET_companies.csv` — 249 project–company links
- **Berkeley dataset:** `raw/Berkeley_dataset.csv` — Berkeley Carbon Trading Project's *Voluntary Registry Offsets Database*. Filtered to `Country == "Indonesia"`: **89 projects** across VCS, Gold Standard, ACR, CAR, ART, PV.
- **Status verification:** Verra public API queried project-by-project on 2026-05-15. Gold Standard structure cross-referenced against Gold Standard PoA/VPA documentation.

## Headline numbers

| | Count | vs prior report (2026-05-09) |
|--|--|--|
| Our projects | 82 | unchanged |
| Berkeley Indonesia projects | 89 | unchanged |
| In both | 71 | unchanged |
| Ours only | 11 | unchanged |
| Berkeley only | 18 | unchanged |

The set is unchanged in count from the prior report, but **every ours-only and Berkeley-only project has now been verified against the Verra registry**, replacing the prior report's status-by-inspection.

## Why these projects differ — three patterns

Every divergence falls into one of three patterns:

### Pattern A — Pre-issuance pipeline (Berkeley excludes by design)
**Affects: 7 of the 11 ours-only projects (all VCS).**

Berkeley's Voluntary Registry Offsets Database has an implicit floor: it primarily catalogues projects with *issued credits*. Verra's "Under development" and "Under validation" statuses — where a project description exists in the registry but no validation has been completed and no credits issued — are typically excluded. All 7 VCS projects in our ours-only set are in this state, with 0 credits issued and most documents dated 2025 or 2026.

This is the largest single source of difference and reflects deliberate inclusion criteria by Berkeley, not data error on either side.

### Pattern B — Gold Standard PoA / VPA numbering mismatch
**Affects: 4 of 11 ours-only and 11 of 18 Berkeley-only projects (all GS).**

Gold Standard's Programme of Activities (PoA) framework assigns **separate sequential IDs** to (i) the umbrella PoA, (ii) each Voluntary Project Activity (VPA), and (iii) sometimes pre-CDM legacy variants. Different secondary datasets index different IDs from the same family. For example:

| Project family | Berkeley indexes | We index | Status |
|---|---|---|---|
| Liki Pinangawan Muaralaboh Geothermal | GS12112 (parent) | GS12113 (VPA) | Same project |
| Global Mangrove Trust Blue Carbon | GS23179, GS23180 (parent + Sumatra 1) | GS23181 (Sumatra 2) | Sibling VPAs |
| ESB/EcoSecurities Electric Motorbike | GS23331, GS23332 (parent + VPA 1) | GS23333 (next VPA) | Sibling VPAs |
| Bagendung Landfill Gas Recovery | GS1143 | GS1147 | Same project, off-by-4 ID |

These are not "missing" projects on either side — they are the **same real-world projects** counted under different IDs. The 11 Berkeley-only GS items are mostly parent PoAs and sister VPAs of the GS projects we already have.

**Implication:** Naively summing "unique projects" from both datasets double-counts these. Real-world unique GS programmes after deduping by family are ~12 rather than 15.

### Pattern C — Status-filtered exclusion (we exclude by design)
**Affects: 7 of 18 Berkeley-only projects (all VCS, all with non-active statuses).**

Our dataset deliberately excludes Verra projects with the following statuses, since they are not part of the active Indonesian voluntary market:

| ID | Project | Verra status | Why excluded |
|----|---------|--------------|--------------|
| VCS238 | Mobuya Mini Hydro Power Plant 3×1000 kW, North Sulawesi | Late to verify | Registered 2020-04-06, monitoring report overdue |
| VCS243 | 55.5 MW Natural Gas Power Generation, Batu Aji, Riau | Late to verify | Registered 2020-04-06, monitoring report overdue |
| VCS866 | Methane Recovery in Wastewater Treatment, North Sumatra | Late to verify | Crediting period **expired 2023-11-11** |
| VCS1750 | PFC Emission Reductions at PT. INALUM (Kuala Tanjung) | Units Transferred from Approved GHG Program | Legacy CER conversion from CDM (project ID 3019), crediting period ended 2020 |
| VCS3587 | Kopi Lestari (PURE PROJECT SAS, coffee agroforestry) | Inactive | Project documents in registry but no validation completed; PUR continues the agroforestry work but the carbon component is paused |
| VCS4186 | Cacao REDD, Gorontalo Province (anti-slash-and-burn) | Rejected by Administrator | Verra administrative rejection; specific reason not publicly documented |
| VCS4445 | RePL Recycling Plastic Project, Banten (H201 Co. Korea) | Inactive | Project documents on file but no progress toward validation |

Berkeley includes these because its inclusion rule is registry presence, not active status. The user's research focus on the political economy of the *operating* market means these belong in a separate "withdrawn / failed projects" set, not in `DATASET_projects.csv`.

## Detailed lists

### Ours only — 11 projects, all pre-issuance or PoA-mismatch

**VCS (7) — all Pattern A (pre-issuance pipeline):**

| ID | Project | Verra status (verified 2026-05-15) | Methodology | Est. annual reductions (tCO₂e) | First credit doc |
|----|---------|---|-------|---:|---|
| VCS5798 | KALTIM HUTAMA IFM | Under development | VM0010 | 517,003 | 2025-11-13 |
| VCS5799 | Gerbang Barito REDD+ | Under development | (REDD/WRC) | 275,000 | 2025-12-03 |
| VCS5873 | Gunung Lumut Landscape (East Kalimantan) | Under development | (ARR/IFM/REDD) | 941,061 | 2026-01-27 |
| VCS5891 | Forest Landscape Restoration, North Sulawesi | Under validation | VM0047 | 158,764 | 2026-05-05 |
| VCS5930 | Charged EV (electric two-wheelers, nationwide) | Under validation | VMR0014 | 23,740 (VCS figure) | 2026-04-17 |
| VCS5956 | AgriCapture Southeast Asia Rice Methane | Under development | VM0051 | 53,142 | 2026-03-24 |
| VCS5962 | Methane recovery, Agro Muara Rupit mill | Under validation | AMS-III.H. | 56,373 | 2026-05-06 |

These are real, plausible projects with named proponents — they simply haven't passed validation yet. Berkeley should pick most of them up in a future quarterly refresh, conditional on validation completing.

**GS (4) — all Pattern B (PoA / VPA numbering):**

| ID | Project | Sibling IDs in Berkeley | Berkeley row(s) |
|----|---------|---|---|
| GS1147 | Bagendung Landfill Gas Recovery (CPA B11001) | GS1143 (same project) | Listed |
| GS12113 | Liki Pinangawan Muaralaboh Geothermal | GS12112 (parent) | Gold Standard Certified Project, 1,144,912 issued |
| GS23181 | Global Mangrove Trust — Sumatra 2 | GS23179 (parent), GS23180 (Sumatra 1) | Gold Standard Certified Design |
| GS23333 | Sustainable Electric Motorbike VPA | GS23331 (parent), GS23332 (VPA 1) | Listed |

### Berkeley only — 18 projects

**GS (11) — all Pattern B (PoA / VPA siblings of GS projects we already track):**

| ID | Project | Status | Total Issued |
|----|---------|--------|---|
| GS790 | Sustainable Small Hydropower PoA (Manggani region) | Listed | 0 |
| GS794 | GS790 — Manggani Hydroelectric Pre-CDM VER | Listed | 0 |
| GS1143 | Bagendung Landfill Gas Recovery (CPA B11001) | Listed | 0 |
| GS1172 | Indonesia Domestic Biogas (IDBP) — parent PoA | Gold Standard Certified Design | 0 |
| GS12112 | Liki Pinangawan Muaralaboh Geothermal (parent) | Certified Project | **1,144,912** |
| GS23179 | Global Mangrove Trust — parent PoA | Certified Design | 0 |
| GS23180 | Global Mangrove Trust — Sumatra 1 | Certified Design | 0 |
| GS23213 | Ibu Bakau Community-Powered Mangrove Afforestation | Listed | 0 |
| GS23331 | Indonesia Sustainable Ride Programme — parent | Listed | 0 |
| GS23332 | Sustainable Electric Motorbike — VPA 1 | Listed | 0 |
| GS23411 | Sustainable Rice Production in Southeast & South Asia | Listed | 0 |

Of these, **only GS12112 has actually produced credits** (1.14 M issued). If you only want to add Berkeley-only GS projects with non-zero issuance, GS12112 is the single high-value addition.

**VCS (7) — all Pattern C (status-filtered exclusion):** see the table in Pattern C above.

## Company-side cross-check

If a Berkeley-only project's developer is also linked to one of our tracked projects, that suggests the developer is operationally embedded in Indonesia and the missing project may matter for footprint analysis. Re-running this against the current `DATASET_companies.csv`:

| Developer (Berkeley-only project) | Berkeley-only IDs they drive | Also linked by us to |
|----------------------|---|---|
| South Pole Carbon Asset Management Ltd | GS790, GS794 | VCS3226, GS2298, GS2299, GS2419, GS2418, GS2297, GS822, GS794, VCS486, VCS488, VCS487, VCS144 |
| EcoSecurities Group Limited | GS23331, GS23332 | VCS5458 |
| The PURE PROJECT SAS | VCS3587 | VCS5545, VCS3012 |
| Global Mangrove Trust | GS23179, GS23180 | GS23181 |
| Value Network Ventures Pte Ltd | GS23213 | GS23214, GS23215 |

South Pole is heavily represented; their Berkeley-only entries (GS790/GS794, two views of the same Manggani PoA) are not new developers but new sub-IDs.

## Data-hygiene findings

### Project IDs in `DATASET_companies.csv` but missing from `DATASET_projects.csv`

Same 12 found in v1 — still unreconciled. Worth resolving in a separate pass, but tracked here for completeness:

GS12112, GS1296, GS1297, GS1298, GS1299, GS2297, GS23180, GS23332, GS7554, GS7555, GS7556, GS7557.

Eight of these are now confirmed by this analysis as either PoA parents or sister VPAs (Pattern B), explaining why they appear in the companies file but not the projects file.

## Recommendations

1. **No action needed for the 7 ours-only VCS pre-issuance projects.** They will appear in Berkeley when they complete validation. Keep them in `DATASET_projects.csv` as the registry pipeline view.

2. **Consider adding GS12112 to `DATASET_projects.csv`.** It is the parent PoA for our GS12113 entry, and is the *only* Berkeley-only GS project with actual issued credits (1.14 M). If your unit of analysis is "programme producing credits," GS12112 is the correct entry, not GS12113.

3. **Decide on PoA vs VPA as the unit of analysis.** Currently we mix: sometimes the parent PoA, sometimes a child VPA. A consistent rule (e.g. "always index the issuing entity, which is the VPA") would eliminate roughly half of the GS divergences.

4. **Maintain the deliberate exclusion of the 7 status-filtered VCS projects** (Pattern C). They are not part of the operating market. Optionally file them in a sibling dataset `DATASET_projects_excluded.csv` so the exclusion is recorded rather than implicit.

5. **Investigate VCS4186 separately.** "Rejected by Administrator" with no public reason is exactly the kind of opaque outcome relevant to the political-economy framing. Worth a focused write-up if Verra later publishes documentation.

## Methodology notes

- **Matching:** Exact-string match on `project ID` after `.Trim()`. No fuzzy matching beyond what was checked manually for the GS PoA family analysis.
- **Country filter:** Berkeley `Country == "Indonesia"` (case-sensitive in the data).
- **Status verification:** Project-by-project query to the Verra public API endpoint `registry.verra.org/uiapi/resource/resourceSummary/<id>` on 2026-05-15. Gold Standard family structure cross-referenced against the [Gold Standard PoA Requirements](https://globalgoals.goldstandard.org/standards/107_V3.0_PAR_Programme-of-Activity-Requirements.pdf).
- **PoA family attribution:** Determined by (i) shared project name, (ii) sequential ID, and (iii) cross-references in our `DATASET_companies.csv` showing the same developers.
- **"Why" classification:** Each divergent project assigned to exactly one of Patterns A / B / C based on the verified status.

## Caveats

- Verra API responses occasionally lack registration dates or credit-issued figures; the field appearing as `null` is the API's behaviour, not a script error.
- VCS4186's stated rejection reason is not public in the Verra registry; the classification as "administrative rejection" reflects the registry's surface status, not the underlying cause.
- The Verra and Indonesia signed an MRA in October 2025 (Pres. Reg. 110/2025 regime). Some projects in administrative limbo before that date may shift status as the agreement is operationalised — recommend re-running this check quarterly.

## Related pages

- [[Task_Report_People_Dataset]] — methodology for the people-by-company dataset that drew on the same underlying project list
- [[Task_Report_People_Dataset_v2]] — latest people-dataset notes
- [[Differences_with_Berkeley]] — prior version of this report (2026-05-09)
