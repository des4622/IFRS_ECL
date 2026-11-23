# IFRS 9 Expected Credit Loss (ECL) Modeling Engine & Governance PoC

## 🎯 Project Objective
To design and build an end-to-end IFRS 9 Expected Credit Loss (ECL) modeling engine in Python. This project bridges quantitative credit risk modeling (PD, LGD, EAD) with regulatory accounting (Staging) and Model Risk Management (MRM) governance, demonstrating a full lifecycle understanding of modern credit risk frameworks.

*This project was developed as a technical proof-of-concept to demonstrate capabilities in predictive modeling, regulatory compliance, and risk governance.*

## 🛠️ Tech Stack & Methodology
- **Core Engine:** Python (Pandas, NumPy) for portfolio data engineering and ECL calculations.
- **Predictive Modeling:** Scikit-Learn (Logistic Regression) for Probability of Default (PD) estimation.
- **Regulatory Framework:** IFRS 9 (Forward-Looking Information, SICR Staging, 12-Month vs. Lifetime ECL).

## 📊 Project Breakdown

### Day 1: Data Engineering & Core ECL Engine
Engineered a synthetic retail loan portfolio (10,000 accounts) and established the foundational risk parameters.
- **Exposure at Default (EAD):** Calculated utilizing a 75% Credit Conversion Factor (CCF) for undrawn credit limits.
- **Loss Given Default (LGD):** Mapped dynamically based on Loan-to-Value (LTV) collateral coverage ratios.
- **Core Formula:** Built the foundational `ECL = EAD × PD × LGD` calculation engine.

### Day 2: Quantitative Modeling & Forward-Looking Information (FLI)
Transitioned from static rule-based PDs to machine learning and macroeconomic stress testing.
- **ML PD Model:** Trained a **Logistic Regression** model to predict Point-in-Time (PiT) PD using Credit Score and LTV as features. Evaluated model performance using **AUC-ROC**.
- **Macroeconomic Overlays:** Implemented IFRS 9 FLI requirements by applying probability-weighted multiplicative overlays across three scenarios (Base 60%, Upside 20%, Downside 20%) driven by simulated unemployment shifts.
- **Impact Analysis:** The downside macroeconomic stress scenario resulted in a prudent **+4.6% increase** in the total portfolio ECL provision.

### Day 3: Regulatory Staging & Model Governance
Translated quantitative outputs into regulatory accounting buckets and established risk controls.
- **IFRS 9 Staging Logic:** Coded rules for Significant Increase in Credit Risk (SICR). Loans were dynamically bucketed into **Stage 1** (12-month ECL), **Stage 2** (Lifetime ECL via SICR/PD doubling), and **Stage 3** (Default/Lifetime ECL via 90+ Days Past Due).
- **Model Risk Management (MRM):** Generated a formal governance report outlining conceptual soundness, model limitations (e.g., static LGD assumptions), and production recommendations (e.g., quarterly recalibration, live macro feeds).

## 💡 Key Business Insights
- **Prudent Provisioning:** Applying Forward-Looking Information (FLI) correctly forces the bank to hold higher capital reserves today to buffer against potential future economic downturns.
- **Risk Segmentation:** The SICR logic successfully isolated high-risk cohorts, ensuring that Lifetime ECL is appropriately recognized for deteriorating assets rather than masking them within the Stage 1 performing bucket.

## 📂 Repository Contents
- `ifrs9_ecl_poc.ipynb`: Complete Jupyter Notebook containing all data generation, ML modeling, staging logic, and governance reporting.
- `day1_ifrs9_loan_portfolio.csv`: Synthetic portfolio data with baseline EAD, LGD, and ECL.
- `day2_ifrs9_ml_and_macro_ecl.csv`: Portfolio updated with ML-predicted PiT PD and macroeconomic scenario overlays.
- `day3_ifrs9_final_staging_ecl.csv`: Final regulatory output with IFRS 9 Stage assignments and 12m/Lifetime ECL calculations.

---
**Prepared by:** Desmond Lai | PMP, FRM Part 1 Candidate, Certified ESG Analyst
