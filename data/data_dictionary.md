# Data Dictionary: Education Risk Mapping — Northeast Nigeria

This document explains the structure, sources, and definitions for the datasets used in the EBI Conflict-Sensitive Education Planning tool.

---

### **1. verified_northeast_schools_cleaned.csv**
*   **name:** School name in uppercase. Source: HOT-OSM.
*   **amenity:** Facility type: school, kindergarten, college, or university.
*   **latitude / longitude:** Geographic coordinates. All 76 records verified for location accuracy.
*   **source:** Original data contributor where recorded. Note: Records from `nigeriase4all.gov.ng` were excluded as they represent electricity infrastructure surveys, not education facilities.

---

### **2. northeast_conflict_cleaned.csv**
*   **id:** Unique UCDP event identifier.
*   **type_of_violence:** 1 = state-based, 2 = non-state, 3 = one-sided civilian targeting.
*   **latitude / longitude:** Event coordinates.
*   **best:** Best estimate of fatalities for that specific event.
*   **adm_2:** LGA name where recorded. 39 blanks retained where LGA was unassigned.
*   **gwnob:** Deleted column; contained no values.

---

### **3. northeast_lga_risk_scores_cleaned.csv**
*   **lga_name:** LGA name in uppercase.
*   **event_count:** Total number of UCDP conflict events recorded in the 24-month analysis window.
*   **total_fatalities:** Sum of 'best' estimate fatalities across all events in that district.
*   **risk_score:** Composite score (0-10). Formula: 35% event frequency + 45% fatality severity + 20% population vulnerability. Normalized to a 0-10 scale.
*   **latitude / longitude:** LGA centroid coordinates used for map plotting.
*   **pop_5_14:** Estimated school-age population aged 5-14. Source: UNFPA Nigeria COD-PS 2020 (HDX).

---

### **4. nga_admpop_2020.xlsx**
*   **Source:** UNFPA and United States Census Bureau PEPFAR program, downloaded from HDX.
*   **Sheet used:** `nga_admpop_adm2_2020`
*   **Columns used:** `T_05_09` (total population aged 5-9) and `T_10_14` (total population aged 10-14).
*   **Calculation:** These were summed to produce the `pop_5_14` estimate for the high-risk priority districts.
