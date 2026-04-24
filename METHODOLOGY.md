# Methodology Note: Education Risk Mapping — Northeast Nigeria

This note documents all data sourcing, cleaning decisions, analytical logic, and replication steps for the EBI conflict-sensitive education planning tool. It is intended for technical reviewers, future implementers, and EBI staff who wish to adapt this methodology to other country contexts.

## 1. Data Sources
Three open, publicly available datasets were used:
*   **Conflict events:** UCDP (Uppsala Conflict Data Program) georeferenced event dataset for Nigeria, filtered to Borno, Yobe, and Adamawa states, 2023–2024 (24-month window). Available at ucdp.uu.se.
*   **School locations:** HOT-OSM (Humanitarian OpenStreetMap Team) verified school dataset for Nigeria. Downloaded from the Humanitarian Data Exchange (HDX) at data.humdata.org.
*   **Population estimates:** WorldPop gridded population estimates for Nigeria, 5–14 age band, 100-metre resolution. Available at worldpop.org.
*   **Administrative boundaries:** LGA boundary GeoJSON for Nigeria (nga_adm2_boundaries.geojson), used for spatial joining and district-level aggregation.

## 2. Conflict Data Cleaning (northeast_conflict_cleaned.csv)
The UCDP dataset required minimal cleaning. The following steps were taken:
*   The dataset was filtered to Borno, Yobe, and Adamawa states and to the 24-month analysis window.
*   All **265** retained records had complete latitude and longitude coordinates. No records were removed for missing coordinates.
*   The `gwnob` column was deleted in full as it contained no values across all 265 rows.
*   The `adm_2` column (LGA name) retained 39 blank values. Since the analysis uses coordinates rather than LGA names for spatial joining, these blanks do not affect the risk score calculation.
*   **Final dataset:** 265 conflict events, 2,071 total fatalities.

## 3. School Location Data Cleaning (verified_northeast_schools_cleaned.csv)
The school location dataset required extensive manual cleaning. The original HOT-OSM download contained 167 records. After a full record-by-record review, 91 records were removed and **76 verified education facilities** were retained.

### 3.1 Records removed and reasons
*   **Nigeria SE4All source records (electricity infrastructure):** Records carried the source tag `nigeriase4all.gov.ng` (electricity grid survey). These were incorrectly tagged as school amenities and lacked humanitarian verification. All were removed.
*   **Individual rooms, classrooms, and building blocks:** Multiple records represented classrooms or blocks within a single institution (e.g., "Class 5A", "Block C"). These reflect over-mapping of single campuses and were removed to ensure institutional clarity.
*   **Non-education facilities:** Records identified as non-education facilities (restrooms, administrative offices, union secretariat rooms) were removed.
*   **Standalone personal names:** Records consisting only of a personal name with no institutional descriptor (e.g., "Musa Babayo") were removed.

### 3.2 Duplicate name check
A conditional formatting check identified schools sharing names (e.g., *Mara Imul Iman*). In all cases, records had different coordinates and OSM IDs, confirming they are distinct physical locations; both pairs were retained.

## 4. LGA Risk Score Calculation (northeast_lga_risk_scores_cleaned.csv)
A composite risk score was calculated for each LGA using the following weighted formula:
*   **40% weight:** Conflict event frequency (number of events).
*   **60% weight:** Fatality severity (total fatalities).

The 60/40 weighting reflects the analytical judgement that lethality is a stronger indicator of education access disruption than frequency alone. **Kukawa** scores 10.0 with 37 events and 601 fatalities, while **Gwoza** scores 4.4 despite recording more events (53), because its fatality total is significantly lower per event.

## 5. Composite Risk Score — Top Five Priority Districts
The five highest-risk LGAs identified by the analysis are:
1.  **Kukawa (Borno):** risk score 10.0
2.  **Gwoza (Borno):** risk score 4.4
3.  **Marte (Borno):** risk score 3.4
4.  **Abadam (Borno):** risk score 3.1
5.  **Bama (Borno):** risk score 2.7

## 6. Visual Artifact
The interactive dashboard is published at: [https://benedicta-onyekwere.github.io/education-risk-northeast-nigeria/](https://benedicta-onyekwere.github.io/education-risk-northeast-nigeria/)

Built using Leaflet.js with the following layers:
*   **District Risk Scores:** Circles at each LGA centroid, colour-coded from green (0) through orange to red (10).
*   **Verified School Points:** Blue markers at each of the 76 verified school locations, clickable to show details.
*   **Conflict Intensity Heatmap:** Red heatmap layer at 0.5 opacity showing spatial concentration of violence.

## 7. Repository Structure
*   `verified_northeast_schools_cleaned.csv` — 76 verified school locations.
*   `northeast_conflict_cleaned.csv` — 265 UCDP conflict events.
*   `northeast_lga_risk_scores_cleaned.csv` — 104 LGAs with risk scores.
*   `index.html` — Source code for the interactive dashboard.
*   `METHODOLOGY.md` — Full documentation of cleaning and logic.
*   `README.md` — Project overview and replication instructions.
