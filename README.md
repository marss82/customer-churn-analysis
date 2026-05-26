# Customer Churn Analysis & Prediction

Exploratory data analysis of customer churn behavior using a dataset of ~10 500 customers with different features including demographics, product usage, support history, and satisfaction scores.

# Customer Churn Prediction

## Overview
Binary classification project predicting customer churn for a Czech 
e-commerce company using behavioral and demographic data.

## Dataset
~10,500 customers with 15 features including:
- Demographics: age, region, estimated income
- Behavior: monthly sessions, avg spend, support tickets
- Product: plan type, device, acquisition channel
- Target: churned (3.2% churn rate — imbalanced)

## Key EDA Findings

### Session Frequency is the strongest retention signal 
Session Frequency is the strongest retention signal. Churn drops monotonically as monthly session count increases — from 5.1% for customers with 0–8 sessions to 0% for customers with more than 24 sessions per month.

| Monthly Sessions | Churn Rate |
|---|---|
| 0 – 8 | 5.1% |
| 8 – 16 | 1.7% |
| 16 – 24 | 0.5% |
| 24 – 32 | 0.0% |

### Support Experience Drives Dissatisfaction
Support ticket count and satisfaction score are strongly negatively correlated (r = -0.54). Customers who raised more tickets reported markedly lower satisfaction, and both features correlate with churn.

### Plan Tier Strongly Predicts Retention
Basic plan customers churn at ~5.7% — 3 to 5 times higher than plus, premium, and business plan customers. Higher-tier customers show strong retention regardless of spend level.

### High-Value Power User Segment Identified
39 customers clustering at exactly 24 monthly sessions form a distinct segment — predominantly small business and young professionals on business/premium plans, averaging ~15,600 CZK monthly spend with only 2.6% churn rate.

### January 2026 Churn Spike
A disproportionate number of churned customers had their last activity in January 2026, suggesting a possible seasonal pattern or a product/service change at that time.

### Spend Scales With Plan Tier — But Ranges Overlap
Average monthly spend roughly doubles with each plan tier, from ~800 CZK (basic) to ~8,000 CZK (business). However, spend ranges overlap significantly across plans — meaning plan tier alone does not fully determine customer value.

### Engagement Drives Both Spend and Retention
Monthly sessions and average monthly spend are strongly correlated (r = 0.82). Engagement appears to be the common driver behind both revenue and retention — not plan tier alone. Customers who use the product more spend more and churn less.

### Plan Tier Has Limited Impact on Session Frequency
Despite the spend difference, session counts vary by only ~8 sessions between basic and business plan customers. Plan tier alone does not strongly predict how actively a customer uses the product.


## Files
data/cleaned_data.csv   → cleaned dataset (output of clean.ipynb)
customer_eda.ipynb      → exploratory data analysis
clean.ipynb             → data cleaning pipeline
churn_models.ipynb                → churn prediction models

## Methods
- OneHotEncoding for categorical features
- Stratified 80/20 train/test split
- class_weight='balanced' to handle class imbalance
- Models: Logistic Regression, Random Forest, Gradient Boosting

## Results
| Model | Recall | ROC-AUC |
|---|---|---|
| Logistic Regression | 67% | 0.779 |
| Random Forest | 30% | 0.783 |
| Gradient Boosting | 59% | 0.784 |

All three models score similarly on ROC-AUC (~0.78), suggesting 
the churn signal in the available features is moderate.

## Stack
Python · pandas · scikit-learn · matplotlib · seaborn

## How to run
pip install -r requirements.txt
# Open churn_models.ipynb and Kernel → Restart & Run All
