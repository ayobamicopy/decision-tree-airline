# ✈️ Airline Customer Satisfaction Predictive Modeling

## 📌 Executive Summary
This project analyzes passenger experience survey indicators to construct an interpretable, auditable **Decision Tree Classifier** that maps and flags passenger dissatisfaction vectors. By deploying an optimized hyperparameter framework via `GridSearchCV`, this model balances precision and recall while outperforming linear baseline models. It serves as a transparent strategic tool for executive airline stakeholder decision-making.

---

## 📈 Model Performance Dashboard & Overfitting Audit

To fulfill strict verification requirements, we audited model performance across both the isolated training and testing data splits to rule out overfitting variance.

### 1. Generalization Metrics (Train vs. Test Comparison)
| Core Performance Metric | Decision Tree (Train) | Decision Tree (Test) | Baseline Logistic Regression (Test) |
|-------------------------|-----------------------|----------------------|------------------------------------|
| **Global Accuracy** | 92.62%                | **92.13%** | 87.56%                             |
| **F1-Score (Satisfied)**| 0.9316                | **0.9271** | 0.8841                             |

> **Overfitting Diagnostic:** The minimal drop-off between training accuracy and testing accuracy (a delta of only **0.49%**) confirms that the tuned tree generalizes cleanly and does not overfit to noise.

### 2. Isolated Decision Tree Evaluation Suite (Test Split)
* **Precision:** **94.04%** (Minimizes false alarms by ensuring predicted satisfaction matches true passenger experience).
* **Recall:** **91.41%** (Ensures 91.4% of all truly satisfied passengers are accurately mapped).

### 3. Empirical Confusion Matrix Matrix Breakdown
* **True Negatives (TN):** 10,935 (Correctly identified dissatisfied passengers)
* **False Positives (FP):** 824 (Dissatisfied passengers incorrectly predicted as satisfied)
* **False Negatives (FN):** 1,221 (Satisfied passengers missed by the model)
* **True Positives (TP):** 12,996 (Correctly identified satisfied passengers)

---

## 🧠 Architectural Transparency & Decision Pathway

The complete rules-based decision path logic has been exported to the root directory as a standalone image asset to keep file payloads light and portable:
👉 **File Reference:** `airline_decision_tree_flowchart.png`

### Top Core Feature Importance Drivers
1. **Inflight Entertainment (Gini Importance: 0.38)** — Primary root decision split vector.
2. **Seat Comfort (Gini Importance: 0.18)** — Secondary core comfort indicator.
3. **Ease of Online Booking (Gini Importance: 0.11)** — Dominant digital interface touchpoint.

---

## 🏢 Business Strategy & Actionable Recommendations

### Model Interpretability: Decision Tree vs. Logistic Regression
* **Handling Non-Linear Features:** Passenger feedback data is heavily non-linear and conditional (e.g., poor *Seat Comfort* can neutralize excellent *Online Booking*). The Decision Tree naturally captures these step-function logic blocks, whereas Logistic Regression forces linear relationships, resulting in a lower F1-Score (**0.8841**).
* **Stakeholder Actionability:** While Logistic Regression relies on log-odds coefficients that are difficult to explain to operations managers, the Decision Tree offers concrete, auditable thresholds (e.g., `Inflight Entertainment <= 3.5`) that translate immediately into capital improvement plans.

### Capital Allocation Priority List
* **Upgrade In-Flight Assets:** Prioritize media catalog refreshes and screen hardware enhancements. Because *Inflight Entertainment* sits at the root node, optimizing this single feature unlocks the highest statistical lift in customer satisfaction.
* **Refit Seating Layouts:** Reallocate budget to premium seating configurations and cushion quality, targeting the high-importance *Seat Comfort* vector.
