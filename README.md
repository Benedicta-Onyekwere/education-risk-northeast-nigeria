# Strengthening Education Continuity in Conflict-Affected Regions
## A Conflict-Sensitive Planning & Prioritization Tool for EBI

This repository contains a **Strategic Education Risk Assessment prototype**. This proof of concept demonstrates the capability being proposed to EBI: a conflict-sensitive planning tool that bridges the gap between fragmented field knowledge and high-level data analysis to support faster, evidence-based prioritization in Borno, Yobe, and Adamawa states.

## 🚀 [Explore the Interactive Decision-Support Dashboard](https://benedicta-onyekwere.github.io/education-risk-northeast-nigeria/)

---

### 💡 Strategic Value for EBI
This project delivers a **replicable capability**, not just a static map. It addresses EBI’s core challenges by:
*   **Visualizing Hidden Risks:** Identifying the distinction between districts with *extreme conflict lethality* (e.g., Kukawa) and those with *mass child vulnerability* (e.g., Gwoza).
*   **Institutional Ownership:** Designed for non-technical staff to update, refresh, and scale across EBI's 12-country portfolio.
*   **Open Data Standards:** Built exclusively on zero-cost, publicly available datasets (UCDP, HOT-OSM, UNFPA) to ensure no proprietary barriers.

### 📂 Repository Navigation
*   **[STRATEGY.md](./STRATEGY.md):** The full proposal, including the 4-activity implementation plan for validation, handover, and replication.
*   **[METHODOLOGY.md](./METHODOLOGY.md):** A transparent technical log of all data cleaning, exclusion logic, and the composite risk formula.
*   **[Data Dictionary](./data/data_dictionary.md):** Full metadata for the conflict, school, and population datasets.
*   **`data/`:** The complete, cleaned data pipeline powering the artifact.

### 🤖 Human-Led AI Reasoning
In alignment with EBI’s requirements, this project employs an **AI-augmented workflow**:
*   **Human Reasoning:** All strategic decisions—including the weighted risk formula (35/45/20) and the exclusion of non-school facilities—were led by human analytical judgment.
*   **AI Assistance:** Large Language Models were used as **Data Engineering Assistants** to generate cleaning scripts, simulate weighting sensitivities, and accelerate UI prototyping.

### ⚖️ Attribution & Transparency
*   **Conflict:** [UCDP GED v23.1](https://ucdp.uu.se/) (CC BY 4.0)
*   **Schools:** [HOT-OSM Verified Education Facilities](https://data.humdata.org/) (ODbL)
*   **Population:** [UNFPA Nigeria Subnational Statistics 2020](https://data.humdata.org/dataset/cod-ps-nga)
*   **Boundaries:** [OCHA Nigeria](https://data.humdata.org/dataset/cod-ab-nga)
