

# Early Prediction of In-Hospital Mortality: An Analysis of the MIMIC-III Database

## Project Overview
This repository contains a clinical data science study focused on the early identification of mortality risk in critically ill patients. The primary objective is to evaluate the predictive power of routine electronic health record (EHR) data—specifically demographics, vital signs, and laboratory measurements—collected exclusively within the first 24 hours of Intensive Care Unit (ICU) admission.

By utilizing interpretable statistical methods, this project aims to provide a transparent screening tool that complements clinical judgment and supports early resource allocation in critical care settings.

## Research Question
"Can in-hospital mortality be successfully predicted using only routine clinical data from the first 24 hours of ICU admission?"

## Data Access and Confidentiality
The dataset used in this study is **MIMIC-III** (Medical Information Mart for Intensive Care III). 

**Important Notice:** Due to the Data Use Agreement (DUA) and the sensitive nature of patient health information, the raw data files (CSV or SQL exports) are not included in this repository. Access to MIMIC-III is restricted to researchers who have completed the CITI Program "Data or Specimens Only Research" course and have been granted formal access by PhysioNet.

To replicate this study, users must:
1. Obtain authorized access via [PhysioNet](https://mimic.mit.edu/).
2. Follow the SQL extraction protocols documented in the `notebooks/` directory to recreate the study cohort.

## Methodology and Technical Stack
The analysis was implemented using the **R programming language** (v4.0+) within a Jupyter environment. The workflow includes:

* **Data Extraction:** SQL queries managed via `DBI` and `RMariaDB`.
* **Data Wrangling:** Extensive use of `dplyr` and `tidyr` for cohort selection and variable cleaning.
* **Preprocessing:** Outliers were managed using **Winsorization** (1st and 99th percentiles) to maintain clinical signal while reducing noise.
* **Modeling:** A **Weighted Logistic Regression** was employed to address the class imbalance (10.96% mortality rate), prioritizing clinical sensitivity.
* **Evaluation:** Performance analysis conducted with the `pROC` library.

## Key Results
The model emphasizes high reliability for early screening, as demonstrated by the following metrics:

| Metric | Value | Interpretation |
| :--- | :--- | :--- |
| **AUC-ROC** | **0.7255** | Solid discriminative power using early-window data. |
| **NPV** | **93.7%** | High certainty when identifying stable survivors. |
| **Sensitivity** | **61.4%** | Effective detection of the majority of high-risk cases. |
| **Lactate (OR)** | **1.46** | Strongest independent metabolic risk predictor. |
| **Creatinine (OR)** | **1.31** | Key marker of early renal dysfunction and risk. |

## Repository Structure
* **`notebooks/`**
    * `Supplementary_Notebook_S1.ipynb`: R code for database connection, SQL extraction, and data cleaning.
    * `Supplementary_Notebook_S2.ipynb`: R code for statistical modeling, visualization, and evaluation.
* **`docs/`**
    * `Full_Paper.pdf`: Detailed research report including clinical discussion.


## Authors
* Angela Coloma Escudero
* Clara Podaru Savu
* Albert Garcia Bernat

## License
This project is licensed under the MIT License.
