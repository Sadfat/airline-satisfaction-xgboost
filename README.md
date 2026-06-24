# Airline Customer Satisfaction — XGBoost Classifier

**Microsoft Elevate AI Developers Program | Capstone Project**  
**Author:** Abubakar Jibrin Gunda (Sadiq) | **Brand:** Gunda LobyAI | **Student ID:** MSDEV-2026-3799

---

## Business Context

Lumina HealthPath operates a network of hospital shuttle and medical transport services across 200+ partner hospitals. Passenger satisfaction data is used to improve patient experience scores and reduce churn among corporate healthcare travel accounts. This project builds a predictive model to classify passengers as **satisfied** or **neutral or dissatisfied**, enabling proactive service recovery before negative reviews impact the brand.

---

## Dataset

| Property | Value |
|---|---|
| Records | 103,904 passenger records |
| Target | `satisfaction` — `satisfied` / `neutral or dissatisfied` |
| Features | 22 — demographics, travel info, service ratings, delays |

---

## Pipeline

```
Raw Data
    ↓
Milestone 1: Discovery & Advanced Preprocessing
  → Label encoding (Gender, Customer Type, Travel Type, Class)
  → Median imputation for Arrival Delay missing values
  → Stratified 80/20 train/test split
    ↓
Milestone 2: Model Construction & Hyperparameter Tuning
  → XGBClassifier with GridSearchCV (3-fold CV, optimising F1)
  → %%time magic for training duration benchmarking
    ↓
Milestone 3: Model Evaluation
  → Accuracy, Precision, Recall, F1-Score
  → Confusion matrix (raw + normalised)
    ↓
Milestone 4: Comparative Analysis
  → Decision Tree vs Random Forest vs XGBoost
  → Summary table + bar chart + technical justification
    ↓
Milestone 5: Feature Importance & Actionable Insights
  → plot_importance (weight + gain)
  → Business recommendations for operations team
```

---

## Model Performance

| Model | Accuracy | Precision | Recall | F1-Score |
|---|---|---|---|---|
| Decision Tree | 0.6998 | 0.6968 | 0.7081 | 0.7024 |
| Random Forest | 0.7081 | 0.7093 | 0.7060 | 0.7076 |
| **XGBoost** | **0.7108** | **0.7107** | **0.7120** | **0.7113** |

**Best model: XGBoost** — highest F1, Accuracy, Precision, and Recall across all three models.  
**Best XGBoost params:** `colsample_bytree=0.8`, `learning_rate=0.1`, `max_depth=3`, `n_estimators=100`, `subsample=0.8`

---

## Key Findings

- **Online boarding** is the top predictor of satisfaction — digital experience directly drives outcomes
- **Travel class** (Business vs Eco) is a strong differentiator — Business passengers have higher and less forgiving expectations
- **Departure delays** are among the top negative drivers, especially for loyal customers
- **Inflight entertainment** and **seat comfort** are the most actionable service-side levers

---

## Top Business Recommendations

1. Invest in online boarding UX — highest ROI for satisfaction lift
2. Target Business class service gaps with personalised recovery offers
3. Use real-time XGBoost scoring on SageMaker to trigger service recovery at check-in
4. Reduce departure delays for loyal customer segments
5. Retrain model quarterly as seasonal travel patterns shift

---

## Repository Structure

```
airline-satisfaction-xgboost/
├── airline_satisfaction_xgboost.ipynb   # Main notebook (all 5 milestones)
├── README.md                            # This file
└── requirements.txt                     # Python dependencies
```

---

## How to Run

```bash
git clone https://github.com/Sadfat/airline-satisfaction-xgboost.git
cd airline-satisfaction-xgboost
pip install -r requirements.txt
jupyter notebook airline_satisfaction_xgboost.ipynb
```

---

*Built with the Discovery-to-Action (DTA) framework | Gunda LobyAI | Microsoft Elevate AI Developers Program*
