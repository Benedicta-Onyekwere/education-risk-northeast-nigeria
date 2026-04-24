# Project Methodology & Data Log

## Step 1: Data Sourcing
**Objective:** Gather authoritative, open-source datasets to identify education risk in Borno, Yobe, and Adamawa states.

### Datasets Selected:
1. **School Locations:** GRID3 Nigeria Education Facilities via HDX.
2. **Conflict Events:** UCDP (Uppsala Conflict Data Program) via HDX.
3. **Administrative Boundaries:** OCHA/OSGOF Admin Level 2 (LGAs).

---

## Step 2: Data Cleaning & Iterative Refinement

### Phase A: Initial First Pass (Geographic Filtering)
- **Action:** Used Python to filter the 20,000+ national schools and conflict events strictly for the Northeast (Borno, Yobe, and Adamawa).
- **Result:** Created `northeast_schools.csv` and `northeast_conflict.csv`.
- **Reasoning:** Narrowed the scope to focus strictly on EBI's primary area of operations.

### Phase B: Data Quality Audit & Discovery (The Pivot)
- **Observation:** During a surgical audit of the `northeast_schools.csv`, I discovered that the official HDX CSV was missing map coordinates (latitude/longitude) and that student/teacher enrollment fields were over 90% blank.
- **Problem:** Plotting 10,000 "blind" points without coordinates or enrollment data would provide a low-quality visual that does not support a clear argument.
- **Decision:** I decided to keep the original file for reference but pivot to a "High-Quality/Verified" dataset for the final map.

### Phase C: Strategic Refinement (Surgical Cleaning)
- **Action 1: Verified Schools.** I extracted a ground-truthed school dataset from HOT-OSM, specifically for the Northeast. This resulted in **167 verified schools** with confirmed locations.
- **Action 2: Strategic Aggregation.** Because conflict risk affects regions, not just individual buildings, I created a **LGA Risk Score** for all 63 districts in the Northeast.
- **Result:** This dual-layer approach shows both the "Big Picture" (which districts are in trouble) and the "Specific Action Points" (the 167 verified schools).

---

## Final Verified Dataset Inventory (Ready for Map):
- [x] **`data/FINAL_verified_schools_NE.csv`** 
  - *Audit:* 167 ground-truthed schools.
  - *Verification:* Confirmed `latitude` and `longitude` columns from the HOT-OSM Shapefile.
- [x] **`data/northeast_lga_risk_scores.csv`** 
  - *Audit:* 63 Local Government Areas scored 1-10 for conflict risk.
  - *Verification:* Calculated using a weighted formula (40% frequency, 60% intensity).
- [x] **`data/northeast_conflict.csv`** 
  - *Audit:* 265 recent events (2024-2026).
  - *Verification:* Filtered strictly for the three northeast states.
- [x] **`data/nga_adm2_boundaries.geojson`** (LGA boundary shapes).
