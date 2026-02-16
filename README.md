# mimic-iii-mortality-prediction

# Early Prediction of In-Hospital Mortality: An Analysis of the MIMIC-III Database

## Project Overview
This repository contains a clinical data science study focused on the early identification of mortality risk in critically ill patients. The objective is to evaluate whether routine clinical and laboratory data, collected exclusively within the first 24 hours of Intensive Care Unit (ICU) admission, are sufficient to provide reliable risk stratification.

The study prioritizes model interpretability to ensure clinical relevance and transparency, moving away from "black-box" algorithmic approaches in high-stakes medical environments.

## Research Question
Can in-hospital mortality be successfully predicted using routine clinical and laboratory data obtained solely during the first 24 hours of ICU admission?

## Methodology and Technical Stack
The project is implemented entirely in **R**, leveraging the following methodology:

* **Data Source:** Retrospective analysis of the MIMIC-III (Medical Information Mart for Intensive Care III) database, comprising over 32,000 adult admissions.
* **Data Wrangling:** Implemented using `dplyr` and `tidyr` for SQL-based extraction and cohort refinement.
* **Preprocessing:** * **Winsorization:** Outliers were capped at the 1st and 99th percentiles to mitigate noise while preserving critical clinical signals.
    * **Standardization:** Continuous variables were scaled to ensure comparability between different physiological units.
* **Statistical Modeling:** A Weighted Logistic Regression was utilized to address the significant class imbalance (10.96% mortality rate), optimizing the model for clinical sensitivity.
* **Evaluation:** Performance was assessed using the `pROC` library, focusing on AUC-ROC, Sensitivity, and Negative Predictive Value (NPV).

## Key Results
The model demonstrates solid discriminative power and high clinical safety margins for early screening:

| Metric | Value | Clinical Significance |
| :--- | :--- | :--- |
| **AUC-ROC** | **0.7255** | Moderate-to-good discriminative capacity for early data. |
| **NPV** | **93.7%** | High reliability for identifying low-risk patients. |
| **Sensitivity** | **61.4%** | Effective detection of the majority of critical cases. |
| **Lactate (OR)** | **1.46** | Strongest independent metabolic predictor. |
| **Creatinine (OR)** | **1.31** | Significant marker of early acute kidney injury risk. |

## Repository Structure
* **`notebooks/`**
    * `Supplementary_Notebook_S1.ipynb`: Data extraction via SQL, cleaning, and Winsorization protocols in R.
    * `Supplementary_Notebook_S2.ipynb`: Statistical modeling, Forest Plot generation, and performance evaluation.
* **`docs/`**
    * `Early prediction of in-hospital mortality using routinely collected electronic health record data_ an analysis of the MIMIC-III database.pdf`: Comprehensive research report and literature review.
   

## Authors
* **Clara Podaru Savu**
* **Angela Coloma Escudero**
* **Albert Garcia Bernat**

## License
This project is for educational and research purposes. Access to the underlying MIMIC-III data requires a formal Data Use Agreement (DUA) and completion of CITI Program training.
