# Credit Risk Modeling & Loan Approval Optimization

### 신용위험 예측 기반 대출 승인 전략 및 예상 신용손실 분석

**Tech Stack:** Python, SQL, SQLite, Pandas, Scikit-learn, LightGBM

---

## 1. Executive Summary

This project develops a credit risk modeling and
lending decision-support framework using the
Home Credit Default Risk dataset.

The objective is to evaluate how predictive risk scores
can support lending decisions while balancing credit
risk and loan approval opportunities.

### Key Results

| Metric | Result |
|---|---:|
| Total Applications | 307,511 |
| Selected Model | LightGBM |
| Probability Method | Original |
| Test ROC-AUC | 0.7613 |
| Test Average Precision | 0.2498 |
| Test Brier Score | 0.0676 |
| Selected Risk Threshold | 12.00% |
| Test Approval Rate | 80.47% |
| Approved Bad Rate | 4.79% |
| Bad Capture Rate | 52.23% |

---

## 2. Business Problem

Financial institutions face a fundamental trade-off:

- Approving more loans can increase business opportunities.
- Approving high-risk borrowers can increase credit losses.
- Rejecting low-risk borrowers can reduce potential revenue.

### Project Objectives

1. Predict customer payment difficulty risk.
2. Identify relevant financial and credit-history features.
3. Compare statistical and machine learning models.
4. Evaluate lending policy thresholds.
5. Simulate hypothetical credit losses and risk-adjusted profit.

---

## 3. Data Engineering

**Dataset:** Home Credit Default Risk (Kaggle)

### Data Sources

- application_train.csv: Customer application information
- bureau.csv: External credit history

### Implementation

- Chunk-based CSV ingestion into SQLite
- Customer-level SQL aggregation
- LEFT JOIN with customer ID validation
- Credit history and debt exposure feature creation
- Duplicate prevention and data integrity checks

The resulting analytical dataset preserves one
observation per application.

---

## 4. Exploratory Data Analysis

Business-oriented EDA examines:

- Income levels and payment difficulty rates
- Loan-to-income ratios
- Historical credit records
- Reported outstanding debt
- Requested credit exposure

The analysis identifies associations rather than
establishing causal relationships.

---

## 5. Predictive Modeling

### Models

**Logistic Regression**
- Interpretable baseline
- Median imputation
- Standard scaling

**LightGBM**
- Gradient boosting model
- Nonlinear relationships
- Credit risk prediction

### Evaluation

- ROC-AUC
- Average Precision
- Brier Score
- Probability Calibration

Training, validation, and test data are separated
to reduce data leakage and support independent evaluation.

---

## 6. Lending Policy Optimization

Customers with predicted risk below the selected
threshold are treated as hypothetical approval candidates.

### Final Policy

| KPI | Test Result |
|---|---:|
| Policy | Business Constrained |
| Threshold | 12.00% |
| Approval Rate | 80.47% |
| Approved Bad Rate | 4.79% |
| Bad Capture Rate | 52.23% |
| Good Rejection Rate | 16.66% |

### Hypothetical Policy Constraints

- Minimum Approval Rate: 50%
- Maximum Approved Bad Rate: 5%
- Both Constraints Satisfied on Test: True

---

## 7. Financial Impact Simulation

The financial simulation uses:

Expected Loss Proxy = PD Proxy × LGD × EAD Proxy

Assumptions:

- LGD: 45%
- Contribution Rate: 8%
- EAD Proxy: Requested loan amount

### Simulated Financial Results

| Financial Metric | Value |
|---|---:|
| Approved Amount | 30,513,419,001 |
| Expected Contribution | 2,326,600,445 |
| Expected Loss Proxy | 643,911,050 |
| Risk-Adjusted Profit Proxy | 1,682,689,395 |
| Profit Margin | 5.51% |

**Important:** These values are hypothetical simulation
results, not realized bank profits or accounting ECL.

---

## 8. Business Recommendation

The selected policy satisfied both hypothetical business constraints on the held-out test data. Further temporal, fairness, and operational validation is required before deployment.

### Decision-Support Value

The framework compares lending strategies using
approval rates, observed payment difficulty rates,
predicted losses, and hypothetical profitability.

---

## 9. Limitations

- Payment difficulty is used as a proxy for default.
- Actual LGD and EAD are not available.
- Financial contribution assumptions are hypothetical.
- Random train/test splitting does not validate future performance.
- Historical applicant data may not represent future borrowers.
- Real-world deployment requires fairness, regulatory,
  and out-of-time validation.

---

## 10. Future Improvements

- Out-of-time model validation
- Model fairness and stability analysis
- SHAP-based model interpretation
- More realistic pricing and loss modeling
- Extended credit history aggregation

---

## Dataset

[Home Credit Default Risk — Kaggle](https://www.kaggle.com/competitions/home-credit-default-risk)

This is an independent educational portfolio project.
