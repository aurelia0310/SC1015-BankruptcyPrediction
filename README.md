# SC1015 Mini Project: BankruptcyPrediction

**Lab group:** ECDS  
**Team 1**  
**Apr 2025**

**Members:**  
- Axalya Raffa Aurelia Jazuli  
- Owen Lim Qi Xun  
- Yap Zhi Ling  

---

This repository contains all the Jupyter Notebooks, datasets, video presentations, and the source materials/references used and created as part of the Mini Project for **SC1015: Introduction to Data Science and AI**.  
This README briefly highlights what we have accomplished in this project.

---

## Table of Contents
1. [Problem Formulation](#1-problem-formulation)  
2. [Data Cleaning and Preparation](#2-data-cleaning-and-preparation)  
3. [Exploratory Data Analysis](#3-exploratory-data-analysis)  
4. [Machine Learning Techniques](#4-machine-learning-techniques)  
5. [Data-Driven Insights and Conclusions](#5-data-driven-insights-and-conclusions)  
6. [References](#references)

---

## 1. Problem Formulation

**Our Dataset**  
**Our Question:** Which variable best predicts bankruptcy?

**Rationale:**  
Bankruptcy is important in many aspects of the business world and economy. Bankruptcy prediction would be useful for identifying creditworthiness in risk management. By predicting whether a firm will go bankrupt, banks and creditors can adjust lending terms and lower the chances of firms defaulting on payments.

At its core, our Data Science problem is a **binary classification**, where we try to classify bankrupt or non-bankrupt cases based on variables accurately. Our secondary problem involves a **feature analysis**, where we find the most important feature that can predict bankruptcy.

---

## 2. Data Cleaning and Preparation

In this section of the project, we prepped and cleaned the dataset to help us analyse our data better and also to help us use our data for machine learning in the later sections.

**We performed the following:**
- Look at the vital statistics: Find the number of features and identify our categorical variable (`Bankrupt?`).
- Observe correlation between features and `Bankrupt?`: Select the top 10 features with the highest correlation to `Bankrupt?`.
- Remove unnecessary features: Narrow down to the top 6 variables, as there were features that overlap (`ROA(A)`, `ROA(B)`, `ROA(C)`).
- Extract final features: Extract and rename the final features, such as `ROA(A) before interest and % after tax` to `ROA_A`.

**Our final set of features is:**
- `NetIncome_to_Assets`: Net income to total assets, which measures overall profitability relative to assets.
- `ROA_A`: Return on Assets(A) before interest and % after tax, which shows how efficiently assets generate profit.
- `DebtRatio`: Debt ratio % that indicates leverage and financial risk.
- `NetWorth_to_Assets`: Net worth to assets, which reflects financial stability.
- `EPS`: Earnings Per Share, which, over time, signals long-term profitability trends.
- `Earnings_to_Assets`: Retained Earnings to Total Assets, which represents accumulated profits.

---

## 3. Exploratory Data Analysis

We explored the selected features using Exploratory Data Analysis, finding summary statistics to describe data, making bar charts to check distribution, plotting box plots to compare groups, and looking for outliers.

**Notable observations:**
- **Summary Statistics**:  
  Low mean and variability in `Bankrupt?`.
- **Potential Outliers**:  
  Features like `DebtRatio`, `ROA_A`, and `EPS` had maximum values of 1, which are significantly different from their 75th percentile.
- **Distribution of `Bankrupt?`**:  
  Very large imbalance in cases of bankrupt vs. non-bankrupt.
- **Remove Outliers**:  
  All features had outliers, which were then removed.

---

## 4. Machine Learning Techniques

**We used three baseline models:**
- **Logistic Regression**: Linear model predicting bankruptcy probability.
- **Random Forest**: Multiple decision trees voting for robust predictions.
- **XGBoost**: Sequential trees correcting errors for high accuracy.

**We also incorporated techniques:**
- **Class Weights**: Makes models care more about bankrupt cases during training.
- **SMOTE-ENN**: Combines SMOTE with Edited Nearest Neighbours to clean noisy synthetic data.
- **SMOTE**: Creates synthetic data to balance the dataset.
- **Youden’s J Statistic**: Picks the best probability cutoff to catch most real bankruptcies.

---

## 5. Data-Driven Insights and Conclusions

**Best Model:**  
XGBoost with built-in imbalance handling via `scale_pos_weight`, SMOTE-ENN, and Youden’s J Statistic.

**Key Risk Indicators:**
- **Primary Driver:**  
  `NetIncome_to_Assets` emerges as the strongest predictor—declining values signal heightened bankruptcy risk.
- **Supporting Metrics:**  
  `DebtRatio` and `ROA_A` provide critical secondary signals—elevated debt and depressed returns indicate financial distress.

**Operational Value:**
- **Risk Monitoring:** Enables continuous financial health assessment.
- **Early Warning:** Identifies at-risk firms in advance.
- **Decision Support:** Informs credit decisions and portfolio management.

**Implementation Considerations:**
- **Training Cycles:** Quarterly model retraining recommended with new data.
- **Complementary Analysis:** Should include expert review for more theoretical grounding.
- **Dynamic Factors:** Requires integration of macroeconomic indicators for comprehensive risk assessment.

**Conclusion:**  
Insights from our data-driven analysis deliver actionable bankruptcy risk management while maintaining operational practicality for financial analysts and credit managers.

---

## References

*List of references or source materials goes here (if available).*
