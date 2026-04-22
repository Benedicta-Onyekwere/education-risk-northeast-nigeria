# Project Methodology & Data Log

## Step 1: Data Sourcing
**Objective:** Gather authoritative, open-source datasets to identify education risk in Borno, Yobe, and Adamawa states.

### Datasets Selected:
1. **School Locations:** GRID3 Nigeria Education Facilities via HDX.
   - *Reasoning:* GRID3 is the most complete, ground-truthed dataset for Nigeria. It includes school types and operational status, which is critical for EBI's rehabilitation planning.
2. **Conflict Events:** UCDP (Uppsala Conflict Data Program) Georeferenced Event Dataset.
   - *Reasoning:* While ACLED was initially considered, UCDP provides a high-quality, event-level CSV dataset for Nigeria via HDX without requiring registration. This ensures the project remains fully open-source and reproducible by anyone without barriers. A 24-month window (2024–2026) is still applied to maintain relevance.
3. **Administrative Boundaries:** OCHA/OSGOF Admin Level 2 (LGAs).
   - *Reasoning:* The LGA is the primary planning unit for EBI and the Nigerian government.
4. **Population Data:** WorldPop (5–14 age band).
   - *Reasoning:* Provides the most granular estimate of where school-age children actually live, rather than just using outdated census totals.

### Data Acquisition Status:
- [x] School Locations (GRID3) - `data/nga_education_facilities.csv`
- [x] Conflict Events (UCDP) - `data/nga_conflict_data_ucdp.csv`
- [x] LGA Boundaries (GeoJSON) - `data/nga_adm2_boundaries.geojson`
- [ ] Population Data (WorldPop) - *To be extracted during the analysis phase using gridded raster methods.*

## Step 2: Data Cleaning (First Pass Complete)
**Objective:** Filter the raw datasets to focus only on Borno, Yobe, and Adamawa, and perform quality checks.

### Actions Taken:
- **Geographic Filtering:** Used Python (Pandas) to filter school data by state codes (`BR`, `YO`, `AD`) and conflict data by region name (`Borno`, `Yobe`, `Adamawa`).
- **Temporal Filtering:** Restricted conflict events to the 2024–2026 window to align with the strategy of "current risk assessment."
- **File Optimization:** Created smaller, focused CSVs (`northeast_schools.csv` and `northeast_conflict.csv`) to facilitate easier cleaning in OpenRefine and Google Sheets.

### Data Quality Observations:
- **Schools:** 10,597 records identified in the target states. Preliminary check shows high coverage of primary and secondary institutions.
- **Conflict:** 265 recent events identified. Coordinates appear consistent with regional boundaries.

### Next Tasks:
- [ ] **OpenRefine Cleaning:** Identify and remove duplicates in school names/locations.
- [ ] **Coordinate Validation:** Ensure all points fall within the LGA GeoJSON boundaries.
