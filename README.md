# Credit Risk Scoring System

## Business Context

This project was designed to mirror a **real-world credit risk system used by digital banks and fintechs across growing and emerging markets (e.g., East/West Africa)**.

In markets like Nigeria, Kenya, etc., where:
  * Credit history may be limited
  * Informal income is common
  * Risk assessment must be fast and scalable

A **data-driven credit scoring system** becomes critical.

This solution enables:
  * **Automated loan decisioning**
  * **Risk-based pricing**
  * **Financial inclusion at scale**

## Problem Statement
Traditional credit systems rely heavily on manual review and rigid rules.

This project builds a **machine learning system that replaces static rules with adaptive risk scoring**, allowing:
  * Faster approvals
  * Reduced default rates
  * Scalable lending operations

## Business Objective
Develop a **credit scoring engine** that:

  * Predicts probability of default
  * Supports **approve/reject/review decisions**
  * Balances:
  * Risk (defaults)
  * Growth (loan approvals)

## Technical Objective
Train and deploy a model:

[
g(x) \rightarrow P(\text{default})
]

Then convert probability into decisions using thresholds:

* Low risk → Approve
* Medium risk → Manual review
* High risk → Reject


### Pipeline Architecture:

  1. Data ingestion
  2. Data validation & cleaning
  3. Feature engineering
  4. Model training
  5. Model evaluation
  6. Scoring layer (probability → decision)

## CRISP-DM

### 1. Business Understanding
* Defined **default risk prediction** as core problem
* Identified **cost asymmetry**:

  * False Negative → Financial loss
  * False Positive → Lost revenue

### 2. Data Understanding
* Analyzed customer-level financial behavior
* Identified:
  * Missing value encoding issues
  * Categorical misrepresentation
  * Outliers in financial variables

### 3. Data Preparation
* Reconstructed categorical variables from encoded values
* Handled missing values systematically
* Built reusable preprocessing pipeline
* Applied **one-hot encoding for model compatibility**


### 4. Modeling Strategy
Instead of using one model, we benchmarked:

| Model         | Purpose                        |
| ------------- | ------------------------------ |
| Decision Tree | Interpretability               |
| Random Forest | Stability & variance reduction |
| XGBoost       | Performance optimization       |


### 5. Evaluation Strategy
* Primary metric: **AUC (ROC)**
* Validation-driven model selection
* Checked for:

  * Overfitting
  * Generalization

### 6. Deployment Thinking

Designed model for:
* API integration into banking systems
* Real-time scoring
* Batch scoring for portfolios


## Machine Learning Workflow

### Step 1: Data Preparation

* Cleaned anomalies (`99999999` placeholders)
* Encoded categorical variables
* Removed invalid labels

### Step 2: Feature Engineering

* Financial indicators:
  * Income
  * Assets
  * Debt
* Behavioral indicators:

  * Credit history (records)
* Socio-demographic:

  * Job, marital status


### Step 3: Model Training

#### Decision Tree:
* Built interpretable baseline
* Controlled overfitting with depth constraints

#### Random Forest:
* Improved robustness via ensembling

#### XGBoost:
* Sequential boosting for error correction
* Best-performing model


### Step 4: Hyperparameter Optimization
Focused tuning on:
* Model complexity
* Generalization performance

Example:
* XGBoost:

  * `eta = 0.1`
  * `max_depth = 3`
  * `min_child_weight = 1`

### Step 5: Model Selection

| Model         | AUC       |
| ------------- | --------- |
| Decision Tree | ~0.78     |
| Random Forest | ~0.82     |
| XGBoost       | **~0.83** |


### Step 6: Final Model Training
* Retrained on full dataset
* Evaluated on unseen test data
* Confirmed no significant overfitting

## Business Impact
This model enables:
* Reduction in default risk
* Faster loan approvals
* Scalable lending operations
* Increased financial inclusion

## Interpretability & Risk Considerations
* Decision Trees used for **rule explainability**
* Feature importance available for audit
* Model outputs can be:

  * Logged
  * Monitored
  * Threshold-adjusted


