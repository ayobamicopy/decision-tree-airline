# ✈️ Modeling Airline Passenger Satisfaction: An Optimized Decision Tree Pipeline

## 📌 Project Overview
This repository contains an end-to-end customer intelligence machine learning framework designed to analyze passenger flight experiences. Using a dataset of 129,880 entries, this project applies an optimized **Decision Tree Classifier** to model passenger satisfaction, uncover non-linear service thresholds, and rank operational drivers to help focus airline capital investments.

---

## ⚙️ Hyperparameter Optimization Framework
To prevent overfitting and ensure the model generalizes well to new data, `GridSearchCV` was applied with 3-Fold Cross-Validation:
* **Evaluated Search Space:** `max_depth` $\in [4, 6, 8, 10]$, `min_samples_split` $\in [20, 50]$, and split criterion $\in$ `[gini, entropy]`.
* **Selected Parameters:** `{'criterion': 'gini', 'max_depth': 10, 'min_samples_split': 20}`.
* **Data Split:** 80/20 train-test split, stratified to preserve the natural balance of approximately 54.7% satisfied vs. 45.3% dissatisfied passengers.

---

## 📈 Comparative Architecture: Decision Tree vs. Logistic Regression

The performance metrics show a clear advantage for the non-parametric approach:

| Metric Evaluation Index | Optimized Decision Tree Model | Baseline Logistic Regression Model |
|-------------------------|--------------------------------|------------------------------------|
| **Classification Accuracy** | **92.13%** | 82.89% |
| **Balanced F1-Score** | **0.9271** | 0.8436 |

### Strategic Architectural Trade-offs
1. **Handling Non-Linearity:** Passenger surveys are inherently non-linear. For example, a low score in `Inflight entertainment` might only trigger dissatisfaction if `Seat comfort` is also low. The Decision Tree naturally captures these step-function interactions, allowing it to outperform Logistic Regression by **+9.24% in accuracy**.
2. **Interpretability and Business Utility:** While Logistic Regression relies on log-odds coefficients, the Decision Tree provides an intuitive, step-by-step decision pathway. This rules-based flow can be easily converted into automated customer-service flags without requiring scaling transformations.

---

## 🛠️ Key Operational Discoveries & Feature Rankings
The model's Gini importance values identify the top operational drivers of passenger satisfaction:

1. **Inflight Entertainment (Score: 0.4912):** The primary driver of satisfaction across demographics.
2. **Seat Comfort (Score: 0.2083):** The leading physical touchpoint driver.
3. **Ease of Online Booking (Score: 0.0650):** The top digital interaction driver.

### Management Recommendations
* **Prioritize Entertainment Systems:** Inflight entertainment accounts for nearly 50% of the model's splitting criteria, making it a clear priority for fleet updates.
* **Target Disloyal Segments:** `Customer Type_disloyal Customer` ranks as the fourth strongest predictor of overall dissatisfaction, suggesting a need for targeted marketing interventions.
