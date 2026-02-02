# P2P Lending Default Risk Prediction

This repository contains the data, code, and paper for a project analyzing default risk in peer-to-peer (P2P) lending using LendingClub loan data from 2015–2018.

The goal of this project is to identify key determinants of loan default and evaluate multiple statistical and machine learning models, with an emphasis on recall to reduce the cost of missed defaults in lending decisions.

---

## Project Structure

```
p2p-default-risk/
├─ notebooks/
│ └─ p2p_default_risk.ipynb
├─ paper/
│ └─ p2p_lending_default_risk.pdf
├─ data/
│ └─ cleaned_p2p_2007_to_2018Q4.csv
│ └─ README.md
└─ README.md
```

---

## Dataset

- **Source:** LendingClub public loan data (via Kaggle)
- **Time period:** 2015–2018
- **Size:** ~1,044,000 loan records
- **Features:** 114 borrower, loan, and repayment variables

The dataset includes information such as loan amount, interest rate, loan grade, term length, FICO score, debt-to-income ratio, loan purpose, verification status, and final loan status.

The target variable is a binary default indicator:
- `1` = Charged Off or Default  
- `0` = Fully Paid  

---

## Methods

The analysis applies the following models:

- Ordinary Least Squares (OLS) as an exploratory baseline
- Logistic Regression
- Ridge Regression (L2 regularization)
- Lasso Regression (L1 regularization)
- Random Forest

Key preprocessing steps include:
- Filtering loans with definitive outcomes
- One-hot encoding categorical variables
- Bucketing continuous variables (income, FICO, DTI)
- Handling missing values through removal or imputation

Model evaluation focuses primarily on **recall**, as failing to identify a defaulting borrower is more costly than false positives in lending contexts. Classification thresholds were adjusted to analyze the trade-off between recall and accuracy.

---

## Key Findings

- Logistic Regression performed best overall with:
  - Recall = 0.446
  - Accuracy = 0.744
  - AUC = 0.715
- Default risk increases significantly for:
  - Lower loan grades (especially Grades G, F, and E)
  - 60-month loan terms
  - Higher debt-to-income ratios
  - Lower FICO scores
  - Small business, medical, renewable energy, and debt consolidation loans
- Adjusting the classification threshold from 0.5 to 0.3 increased recall by over 400 percent, demonstrating the importance of threshold tuning in credit risk modeling

---

## Paper

The full research paper describing the data, methodology, results, and interpretation is available here

# P2P_lending_default_risk_prediction
