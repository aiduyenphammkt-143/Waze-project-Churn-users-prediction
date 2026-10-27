# Waze User Churn Prediction

## 1. Business Context

Waze is a community-driven navigation platform that helps millions of drivers travel more efficiently and safely. Its ecosystem of users, map editors, partners, and local authorities continuously contributes to improving the driving experience.

As user retention becomes an increasingly important growth lever, Waze launched an initiative to better understand and proactively prevent user churn.

## 2. Business Problem

User churn represents drivers who have either stopped using the app or uninstalled it entirely.

For a subscription-free platform like Waze, retaining active users is critical because user engagement directly impacts:

* Long-term platform growth
* Community-generated traffic intelligence
* User acquisition efficiency
* Product adoption and engagement

Without a reliable way to identify at-risk users, Waze risks losing valuable users without understanding:

* **Who is most likely to churn?**
* **What behavioral patterns signal churn risk?**
* **How early can churn be detected?**

The business objective of this project is to build a predictive framework that helps Waze identify high-risk users early and support data-driven retention strategies.

## 3. Solution Approach

This project combines exploratory analytics and machine learning to transform user activity data into actionable retention insights.
Rather than reacting after users leave the platform, this project enables Waze to:

* Predict churn risk before users disengage
* Understand the behavioral drivers behind churn
* Prioritize retention efforts on the highest-risk user segments
* Support product and engagement decisions with data

The final outcome is a predictive model capable of estimating churn probability and identifying the behaviors most strongly associated with user attrition.

## 4. Dataset Overview

The dataset contains 14,999 users with behavioral and engagement metrics collected from app usage history.

### Key Variables

| Attribute Category | Variables |
|-----|-----|
| User Activity | `Sessions`, `Drives`, `Activity Days`, `Driving Days` |
| Engagement History | `Total Sessions`, `Account Tenure` |
| Navigation Behavior | `Favorite Destinations` |
| Driving Behavior | `Distance Driven`, `Driving Duration` |
| Device Information | `Device Type` (iPhone or Android) |
| Target Variable	| `Churned` or `Retained` |

### Target Distribution
* 82% Retained Users
* 18% Churned Users

**This is an unbalanced dataset, but not extremely so. It can be modeled without any class rebalancing.**

## 5. Analytical Pipeline

### Phase 1: Exploratory Data Analysis

* Data quality assessment
* Missing value treatment
* Distribution analysis
* Outlier investigation
* User behavior profiling
* Feature engineering
* Churn pattern exploration

### Phase 2: Predictive Modeling

Models evaluated:

* Decision Tree
* Random Forest
* XGBoost

Model optimization techniques:

* Hyperparameter Tuning
* Cross Validation
* Feature Importance Analysis

### Technology Stack
* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn
* XGBoost
* Pickle

## 6. Key Findings

### 🚨 User engagement frequency is the strongest retention signal

Users who drive frequently throughout the month consistently show the lowest churn risk.

Conversely, users with fewer active driving days are significantly more likely to leave the platform.

**Implication:** Churn is primarily a habit problem, not a usage problem. Building recurring engagement is likely more effective than increasing individual session volume.

### 🚨 Heavy driving behavior is a leading indicator of churn

Users who accumulate the highest driving distances and driving durations exhibit materially higher churn rates.

This pattern directly contradicts the assumption that the heaviest users are the most loyal users.

**Implication:** A large portion of churn comes from users with intensive but short-lived usage patterns, making them a critical retention segment for Waze.

### 🚨 How users drive matters more than how long they stay on the platform

Account tenure shows relatively limited predictive power compared with behavioral signals such as:

* Driving duration
* Distance traveled
* Session engagement patterns

Both new and long-tenured users churn.

**Implication:** Retention programs should target user behavior rather than relying on customer age or lifecycle stage.

### 🚨 Recent engagement behavior is one of the strongest churn predictors

Features such as:

* Percentage of sessions in the last month
* Total sessions per day
* Favorite destination usage

rank among the most important variables in the final model.

**Implication:** Churn risk can be identified before users leave entirely, enabling proactive retention campaigns rather than reactive interventions.

### 🚨 Churn is predictable from behavioral data

The final XGBoost model consistently outperformed benchmark tree-based models and successfully identified meaningful churn patterns.

The model highlights a clear set of behavioral drivers behind user attrition, demonstrating that churn is not random and can be systematically monitored.

**Implication:** Waze can move from explaining churn after the fact to predicting churn before it occurs.

## 7. Predictive Modeling Results

### Best Performing Model: XGBoost

**The champion model after tunning and validation: XGBoost**

Then, the selected XGBoost model predicts on a seperating test set.

| Model | Precision Score | Recall Score | F1 Score |
|-----|-----|-----|-----|
| Random Forest (Tuned) | 0.57 | 0.05 | 0.09 |
| XGBoost (Tuned) | 0.40 | 0.18 | 0.25 |
| Random Forest (Validation) | 0.43 | 0.04 | 0.08 |
| XGBoost (Validation) | 0.37 | 0.17 | 0.23 |
| XGBoost (Test Set) | 0.40 | 0.19 | 0.26 |

### Model Interpretation

The most influential features driving churn prediction include:

* Driving duration
* Recent session engagement
* Account tenure
* Distance driven
* Distance per drive
* Favorite destination usage

These findings suggest that engagement consistency and driving behavior are stronger churn predictors than demographics or device type.
