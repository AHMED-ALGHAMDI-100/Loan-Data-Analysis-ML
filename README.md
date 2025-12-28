# Credit Risk Prediction

## Project Overview
This project aims to reduce credit losses by predicting risky loans before they are approved [1]. The core business problem involves distinguishing between "safe" and "bad" loans in a financial dataset. The primary goal is to catch the majority of bad loans (High Recall) while maintaining an acceptable level of precision, ensuring a smooth approval process for safe customers [1, 2].

## Dataset & Preprocessing
The dataset used for this project presents a significant challenge due to a high class imbalance:
*   **Distribution:** Approximately 98% good loans vs. 2% bad loans [2].
*   **Preprocessing Steps:**
    *   Removal of unnecessary columns (e.g., `id`, `total_pymnt`) to prevent data leakage and noise [2].
    *   Handling of duplicates and missing values [2].
    *   **EDA Insights:** Outliers were identified but kept as they possess significant financial meaning. Analysis revealed right-skewed distributions in installments and bimodal distributions in interest rates [3].

## Methodology
To address the non-linear nature of tabular financial data and the severe class imbalance, the following strategy was employed:

*   **Model:** XGBoost Classifier, selected for its robust performance on tabular data [3].
*   **Imbalance Handling:**
    *   Utilized **SMOTE** (Synthetic Minority Over-sampling Technique) to oversample bad loans [3].
    *   Adjusted the `scale_pos_weight` parameter to account for the ratio of negative to positive classes [3].
*   **Validation:** implemented 10-Fold Stratified Cross-Validation to ensure model stability and reliability [3].
*   **Reproducibility:** A fixed random state (`42`) was used throughout the pipeline [4].

## Key Features
Feature importance analysis identified the top contributors to the model's decision-making process [3]:
1.  Issue Date
2.  Sub Grade
3.  Funded Amount
4.  Installment
5.  Interest Rate

## Results & Evaluation
The model was evaluated using metrics specifically suited for imbalanced datasets, focusing on the Precision-Recall (PR) Curve over the ROC Curve [4].

*   **Threshold Tuning:** Custom decision thresholds were analyzed to satisfy specific business constraints:
    *   Target Recall: ≥ 0.6
    *   Target Precision: ≥ 0.05 [4]
*   **Outcome:** The final model successfully improves the detection of bad loans post-SMOTE, effectively surfacing high-risk loans early in the pipeline [5].

## Technologies Used
*   **Python Libraries:** `xgboost`, `sklearn` (specifically `StratifiedKFold`, `cross_validate`, `SMOTE`), `pandas`, `seaborn`, and `matplotlib` [3, 4].

## 
Visualization: 
the linke: https://public.tableau.com/app/profile/ahmed./vizzes
##
