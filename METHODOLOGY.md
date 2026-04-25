# Methodology Note: Education Risk Mapping — Northeast Nigeria

This note documents all data sourcing, cleaning decisions, analytical logic, and replication steps for the EBI conflict-sensitive education planning tool.

## 1. Data Sources
Three open, publicly available datasets were used:
*   **Conflict events:** UCDP (Uppsala Conflict Data Program) georeferenced event dataset for Nigeria, filtered to Borno, Yobe, and Adamawa states, 2023–2024 (24-month window).
*   **School locations:** HOT-OSM (Humanitarian OpenStreetMap Team) verified school dataset for Nigeria.
*   **Population estimates:** UNFPA Nigeria Subnational Population Statistics 2020 (COD-PS).
*   **Administrative boundaries:** LGA boundary GeoJSON for Nigeria (nga_adm2_boundaries.geojson).

## 2. Conflict Data Cleaning (northeast_conflict_cleaned.csv)
The UCDP dataset was filtered to the 24-month analysis window.
*   **Final dataset:** 265 conflict events, 2,071 total fatalities.
*   **Lethality Check:** We identified 40 "One-Sided" attacks directly targeting civilians, confirming that schools in this region face deliberate targeting.

## 3. School Location Data Cleaning (verified_northeast_schools_cleaned.csv)
The school dataset required extensive manual cleaning. The original 167 records were audited record-by-record:
*   **Nigeria SE4All records removed:** These were electricity grid surveys incorrectly tagged as schools.
*   **Campus over-mapping removed:** Individual rooms (e.g., "Class 5A", "Block C") were removed to ensure institutional clarity.
*   **Final dataset:** 76 verified education facilities retained.

## 4. LGA Risk Score Calculation (northeast_lga_risk_scores_cleaned.csv)
A composite risk score was calculated for 104 LGAs using a weighted formula:
*   **35% weight:** Conflict event frequency.
*   **45% weight:** Fatality severity (Lethality).
*   **20% weight:** Population vulnerability (Children aged 5-14).

**Key Finding:** Kukawa (Borno) scores 10.0 due to extreme fatality intensity (601 fatalities), while Gwoza represents the largest scale of vulnerability with 125,905 children at risk.

## 5. Visual Artifact
The interactive dashboard is published at: [https://benedicta-onyekwere.github.io/education-risk-northeast-nigeria/](https://benedicta-onyekwere.github.io/education-risk-northeast-nigeria/)

---
## 6. Replication
To apply this to a different country, download the corresponding UCDP/OSM/UNFPA datasets and apply the 35/45/20 risk formula provided in the repository scripts.
