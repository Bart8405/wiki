# Differences Between Our Dataset and the Berkeley Voluntary Registry Offsets Database

*Generated: 2026-05-09*

## Sources

- **Our project dataset:** `raw/DATASET_projects.csv` (82 projects)
- **Our company dataset:** `raw/DATASET_companies.csv` (249 project–company links)
- **Berkeley dataset:** `raw/Berkeley_dataset.csv` — Berkeley Carbon Trading Project's *Voluntary Registry Offsets Database*. 11,477 total rows; filtered to country = "Indonesia" (89 Indonesian projects across all registries: VCS, GS, ACR, CAR, ART, PV).

## Headline numbers

| | Count |
|--|--|
| Our projects | 82 |
| Berkeley Indonesia projects | 89 |
| In both | 71 |
| Ours only (not in Berkeley) | 11 |
| Berkeley only (not in ours) | 18 |

## Projects in OUR dataset but NOT in Berkeley

These are projects we have collected from the Verra/Gold Standard registries that did **not** appear in Berkeley's Voluntary Registry Offsets Database. Possible reasons (ordered by likelihood):

1. **Project never issued credits.** Berkeley primarily indexes projects with at least one issuance. "Under development", "Listed", "Registration requested" projects on Verra are typically excluded.
2. **Berkeley dataset cut-off.** Berkeley updates quarterly; very recent additions may not be present yet.
3. **Project withdrawn, rejected, or inactive.** Some appear in registries but are flagged as ineligible.
4. **Phantom listings (the concerning case).** Projects that exist on a registry as a listing but never produce verifiable credits — a recurring scam pattern in voluntary markets.

Cross-reference each row with its Verra/GS source link before concluding fraud.

| ID | Project Name | Type | Status | Source |
|----|--------------|------|--------|--------|
| VCS5962 | Recovery and Avoidance of methane from Industrial wastewater treatment project at Agro Mua | Waste Handling and Disposal | Planned | [link](https://registry.verra.org/app/projectDetail/VCS/5962) |
| VCS5956 | AgriCapture Southeast Asia Rice Methane Project | AFOLU Agricultural Land Management | Exists | [link](https://registry.verra.org/app/projectDetail/VCS/5956) |
| VCS5930 | Charged EV Project in Indonesia | Transport | Exists | [link](https://registry.verra.org/app/projectDetail/VCS/5930) |
| VCS5798 | KALTIM HUTAMA IFM PROJECT | AFOLU IFM | Exists | [link](https://registry.verra.org/app/projectDetail/VCS/5798) |
| GS23333 | GS23331 â€“ VPA 1 â€“ SUSTAINABLE ELECTRIC MOTORBIKE PROJECT BY ESB AND ECOSECURITIES | Emission reductions by electric and hybrid vehicles | planned | [link](https://assurance-platform.goldstandard.org/project-documents/GS13164) |
| GS23181 | GLOBAL MANGROVE TRUST BLUE CARBON RESTORATION PROJECT IN INDONESIA - SUMATRA 2 | A/R | planned | [link](https://assurance-platform.goldstandard.org/project-documents/GS23180) |
| GS12113 | LIKI PINANGAWAN MUARALABOH GEOTHERMAL POWER PLANT | Geothermal | exist | [link](https://assurance-platform.goldstandard.org/project-documents/GS12112) |
| GS2297Â | Project Ulubelu Unit 3 - 4 PT. Pertamina Geothermal Energy |  |  | [link](https://assurance-platform.goldstandard.org/project-documents/GS2297) |
| VCS5891 | Forest Landscape Restoration in North Sulawesi Province | AFOLU | ? | [link](https://registry.verra.org/app/projectDetail/VCS/5891) |
| VCS5873 | Gunung Lumut Landscape Project | AFOLU ARR & IFM & REDD | Planned | [link](https://registry.verra.org/app/projectDetail/VCS/5873) |
| VCS5799 | Gerbang Barito REDD+ Project | AFOLU REDD & WRC | Planned | [link](https://registry.verra.org/app/projectDetail/VCS/5799) |

## Projects in BERKELEY but NOT in our dataset

These are Indonesian projects Berkeley tracks that we have not yet ingested. Most have already issued credits (Berkeley's main inclusion criterion), so they are real, active projects worth adding.

### Registry: GOLD — 11 projects

| ID | Project Name | Status | Type | Project Developer | Total Issued |
|----|--------------|--------|------|-------------------|--------------|
| GS790 | GS790_Sustainable Small Hydropower Programme of Activities (PoA) in Indonesia (3 | Listed | Hydropower | South Pole Ltd | 0 |
| GS1143 | CPA B11001 – Bagendung Landfill Gas Recovery | Listed | Landfill Methane | PT ERC Austrindo | 0 |
| GS1172 | Indonesia Domestic Biogas Programme of Activities (IDBP) | Gold Standard Certified Design | Biodigesters | PT BIRU KARBON NUSANTARA | 0 |
| GS2297 | Project Ulubelu Unit 3 - 4 PT. Pertamina Geothermal Energy | Gold Standard Certified Project | Geothermal | South Pole Ltd | 1,561,910 |
| GS12112 | Liki Pinangawan Muaralaboh Geothermal Power Plant | Gold Standard Certified Project | Geothermal | PT. SUPREME ENERGY MUARA LABOH | 1,144,912 |
| GS23179 | Global Mangrove Trust Blue Carbon Restoration Project in Indonesia | Gold Standard Certified Design | Wetland Restoration | Global Mangrove Trust | 0 |
| GS23180 | Global Mangrove Trust Blue Carbon Restoration Project in Indonesia - Sumatra 1 | Gold Standard Certified Design | Wetland Restoration | Global Mangrove Trust | 0 |
| GS23213 | Ibu Bakau: Community-powered Mangrove Afforestation in Indonesia | Listed | Wetland Restoration | Value Network Ventures Pte. Ltd. | 0 |
| GS23331 | Indonesia Sustainable Ride Programme by EcoSecurities | Listed | Electric Vehicles & Charging | EcoSecurities Group Limited | 0 |
| GS23332 | GS23331 – VPA 1 – Sustainable Electric Motorbike Project by ESB and EcoSecuritie | Listed | Electric Vehicles & Charging | EcoSecurities Group Limited | 0 |
| GS23411 | Sustainable Rice Production in Southeast and South Asia | Listed | Rice Emission Reductions | RIZE PTE. LTD. | 0 |

### Registry: VCS — 7 projects

| ID | Project Name | Status | Type | Project Developer | Total Issued |
|----|--------------|--------|------|-------------------|--------------|
| VCS238 | Mobuya Mini Hydro Power Plant 3 x 1000 kW North Sulawesi, Indonesia | Late to verify | Hydropower | PT. Cipta Daya Nusantara | 54,061 |
| VCS243 | 55.5 MW Natural Gas Power Generation Project at Batu Aji Village, Riau Island, I | Late to verify | Natural Gas Electricity Generation | PT Dalle Energy Batam | 0 |
| VCS866 | METHANE RECOVERY IN WASTEWATER TREATMENT, PROJECT AIN07-W-05, SUMATERA UTARA, IN | Late to verify | Methane Recovery in Wastewater | AES AgriVerde Ltd. | 0 |
| VCS1750 | PFC Emission Reductions at PT. Indonesia Asahan Aluminium (PT. INALUM) Kuala Tan | Units Transferred from Approved GHG Program | Aluminum Smelters Emission Reductions | Credits transferred from approved GHG program | 15,811 |
| VCS3587 | KOPI LESTARI AGROFORESTRY AND LAND REHABILITATION WITH SMALLHOLDER FARMERS IN IN | Inactive | Afforestation/Reforestation | The PURE PROJECT SAS | 0 |
| VCS4186 | REDUCING EMISSIONS FROM DEFORESTATION DUE TO SLASH-AND-BURN CORN BY INTRODUCING  | Rejected by Administrator | REDD+ | Multiple Proponents | 0 |
| VCS4445 | RePL Recycling plastic project | Inactive | Waste Recycling | H201 Co., Ltd | 0 |

## Companies involved in Berkeley-only projects

Berkeley records ONE "Project Developer" per row — secondary roles (operator, mill owner, technical advisor) are not captured. Below is the deduplicated list, sorted by how many Berkeley-only Indonesia projects each developer appears on. Where a name is empty, Berkeley left the developer field blank.

| # | Developer | Project IDs |
|---|-----------|-------------|
| 2 | South Pole Ltd | GS790, GS2297 |
| 2 | Global Mangrove Trust | GS23179, GS23180 |
| 2 | EcoSecurities Group Limited | GS23331, GS23332 |
| 1 | PT ERC Austrindo | GS1143 |
| 1 | PT BIRU KARBON NUSANTARA | GS1172 |
| 1 | PT. SUPREME ENERGY MUARA LABOH | GS12112 |
| 1 | Value Network Ventures Pte. Ltd. | GS23213 |
| 1 | RIZE PTE. LTD. | GS23411 |
| 1 | PT. Cipta Daya Nusantara | VCS238 |
| 1 | PT Dalle Energy Batam | VCS243 |
| 1 | AES AgriVerde Ltd. | VCS866 |
| 1 | Credits transferred from approved GHG program | VCS1750 |
| 1 | The PURE PROJECT SAS | VCS3587 |
| 1 | Multiple Proponents | VCS4186 |
| 1 | H201 Co., Ltd | VCS4445 |

## Cross-check: which Berkeley-only developers also appear in our company dataset?

If a Berkeley-only project's developer is a company we already track on a different (in-our-dataset) project, that is interesting — it suggests the developer is active in Indonesia and the new project is likely worth adding.

| Developer (Berkeley) | Berkeley-only project IDs | Also linked by us to |
|----------------------|---------------------------|----------------------|
| South Pole Ltd | GS790, GS2297 | VCS3226 |
| EcoSecurities Group Limited | GS23331, GS23332 | VCS5458 |
| The PURE PROJECT SAS | VCS3587 | VCS5545, VCS3012 |

## Data hygiene: project IDs in `DATASET_companies.csv` but missing from `DATASET_projects.csv`

The following 12 project IDs are referenced in `DATASET_companies.csv` but have no corresponding row in `DATASET_projects.csv`. Most look like sub-projects (VPAs of a Programme of Activities) or near-duplicates with whitespace/casing variants. Worth reconciling.

| Project ID (companies CSV) | Companies linked |
|----------------------------|------------------|
| `GS12112` | PT. Supreme Energy Muara Laboh |
| `GS1296` | BEST (Tangerang and Surabya): Bina Ekonomi Sosial Terpadu (Institute for integrated economic and social development) |
| `GS1297` | LPTP Lembaga PEMBANGUNAN Teknologi Perdesaan (Foundation for the development of
rural tecnologies)  |
| `GS1298` | BALIFOKUS |
| `GS1299` | atmosfair gGmbH |
| `GS2297` | South Pole Carbon Asset Management Ltd ; PT. Pertamina Geothermal Energy |
| `GS23180` | Global Mangrove Trust |
| `GS23332` | EcoSecurities Group Limited |
| `GS7554` | PT Infrastruktur Terbarukan Adhiguna |
| `GS7555` | PT Infrastruktur Terbarukan Buana |
| `GS7556` | PT Infrastruktur Terbarukan Cemerlang |
| `GS7557` | PT Infrastruktur Terbarukan Lestari |

## Methodology notes

- **Matching:** Berkeley project IDs (e.g. `VCS5873`, `GS5303`) were matched against our `project ID` field as exact strings. Whitespace stripped from both sides; no fuzzy matching.
- **Country filter:** `Country == "Indonesia"` (case-insensitive). Berkeley's Indonesia universe spans every registry it tracks (Verra/VCS, Gold Standard, ACR, CAR, ART, Plan Vivo).
- **Berkeley schema:** "Project Developer" is the single principal company on each project. Our `DATASET_companies.csv` is richer, capturing operators, mill owners, technical advisors, and other roles per project.
- **"Potential scam" framing:** A project being absent from Berkeley is *not by itself* evidence of fraud. Most ours-only projects are simply pre-issuance. The framing comes from the user's research hypothesis that some Indonesian projects may be phantom listings; this report identifies the candidate set, not the verdict.
