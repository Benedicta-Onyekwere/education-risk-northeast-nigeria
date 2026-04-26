# Education Risk Mapping — Northeast Nigeria

## Project Overview
This repository contains a conflict-sensitive education planning tool developed for the **Education Bridge Initiative (EBI)**. The project identifies Local Government Areas (LGAs) in Borno, Yobe, and Adamawa where school-age children face the highest risk due to active conflict and limited access to verified education facilities.

## 🚀 Live Visual Artifact
**[View the Interactive Dashboard here](https://benedicta-onyekwere.github.io/education-risk-northeast-nigeria/)**

## Key Findings
Our analysis of 2024 conflict data and UNFPA population projections identifies five "Critical Tier" districts requiring immediate assessment:
1. **Kukawa (Borno):** Highest conflict lethality (601 fatalities).
2. **Gwoza (Borno):** Largest scale of child vulnerability (125,905 children at risk).
3. **Marte (Borno)**
4. **Abadam (Borno)**
5. **Bama (Borno)**

## Repository Navigation
To ensure complete transparency and reproducibility, this repository is organized as follows:

*   **[STRATEGY.md](./STRATEGY.md):** The formal project proposal, including context, objectives, and technology selection.
*   **[METHODOLOGY.md](./METHODOLOGY.md):** A detailed technical log documenting every data sourcing and cleaning decision.
*   **[Data Dictionary](./data/data_dictionary.md):** Definitions for every column and source in the cleaned datasets.
*   **`data/`:** Contains the process history files and the UNFPA population source file.

## Data Attribution & Licenses
In accordance with humanitarian data standards, this project utilizes open-source data from the following providers:
*   **Conflict Data:** [UCDP GED Global version 23.1](https://ucdp.uu.se/). Licensed under [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/).
*   **School Locations:** [HOT-OSM Verified Education Facilities](https://data.humdata.org/). © OpenStreetMap contributors. Licensed under [ODbL](https://opendatacommons.org/licenses/odbl/).
*   **Population Data:** [UNFPA Nigeria Subnational Population Statistics 2020](https://data.humdata.org/dataset/cod-ps-nga). 
*   **Administrative Boundaries:** [OCHA Nigeria / OSGOF](https://data.humdata.org/dataset/cod-ab-nga). These boundaries are provided for humanitarian planning purposes under the OCHA standard terms of use.

## Use of AI
This project utilized Large Language Models for data engineering assistance (scripting and validation), while all strategic, analytical, and design decisions were human-led. Tools used included Claude for analytical reasoning, v0 for interface prototyping, and Python with Pandas for data processing.
