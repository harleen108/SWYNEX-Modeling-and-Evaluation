# SWYNEX Modeling and Evaluation — Network Traffic Classification

## Project Overview

This project builds and evaluates a baseline machine learning model for classifying network traffic using the public CIC-IDS2017 cybersecurity dataset. It extends the data preparation and exploratory data analysis work by applying a Decision Tree Classifier to distinguish benign traffic from PortScan activity.

## Objectives

- Build a baseline machine learning classification model.
- Prepare features and target labels for training.
- Evaluate model performance using standard classification metrics.
- Identify limitations and considerations for future improvement.

## Dataset

**Dataset:** CIC-IDS2017 — Network Intrusion Detection Evaluation Dataset

**Source:** [Canadian Institute for Cybersecurity, University of New Brunswick](https://www.unb.ca/cic/datasets/ids-2017.html)

The working dataset used in this notebook contains:

- **Total records:** 95,391
- **Total columns:** 79
- **BENIGN records:** 85,023
- **PortScan records:** 10,368
- **Missing target labels:** 0
- **Duplicate rows:** 0

The dataset contains benign network traffic and PortScan traffic, which is used as the target for binary classification.

## Methodology

### 1. Data Preparation

- Loaded the prepared CSV dataset using Pandas.
- Removed records with missing target labels.
- Separated numerical features from the `Label` target column.
- Replaced infinite values with missing values and filled missing numerical feature values with column medians.

### 2. Train-Test Split

The dataset was split into training and testing sets using an 80:20 ratio with a fixed random state for reproducibility.

### 3. Model Training

A **Decision Tree Classifier** was selected as the baseline model, with a maximum tree depth of 8.

### 4. Model Evaluation

The model was evaluated using:

- Accuracy
- Precision
- Recall
- F1-score
- Confusion Matrix

These metrics provide a broader view of model performance than accuracy alone.

## Results

The model produced the following initial evaluation results:

| Metric | Result |
|---|---:|
| Accuracy | 99.98% |
| BENIGN precision | 1.00 |
| BENIGN recall | 1.00 |
| PortScan precision | 1.00 |
| PortScan recall | 1.00 |
| PortScan F1-score | 1.00 |

**Test set size:** 19,079 records.

The reported classification metrics are rounded. The confusion matrix and full classification report are available in the notebook.

## Key Observations

- The Decision Tree achieved very high scores on the current test split.
- Both BENIGN and PortScan traffic were represented in the test set.
- Evaluation metrics beyond accuracy help assess how well the model detects the minority attack class.
- The results should be interpreted cautiously until possible data leakage and generalization to unseen traffic have been checked.

## Limitations

- The dataset represents a specific selection of CIC-IDS2017 traffic and may not represent all real-world network conditions.
- Very high scores can result from overlapping or redundant features, data leakage, or similarities between training and testing records.
- A separate evaluation on unseen data is required before making claims about real-world intrusion detection performance.
- Additional models and validation methods could be compared in future work.

## Conclusion

This project demonstrates a baseline machine learning workflow for network traffic classification using a Decision Tree Classifier. It includes data preparation, model training, and evaluation with multiple classification metrics.

Future improvements include checking for data leakage, validating the model on independent network traffic, and comparing its performance with other classification algorithms.

## Tools and Technologies

- Python
- Pandas
- Scikit-learn
- Google Colab
- GitHub
- CIC-IDS2017 Dataset

## Project File

- `SWYNEX_Modeling_and_Evaluation.ipynb` — notebook containing the data preparation, model training, and evaluation workflow.

---

**Internship:** SWYNEX Technologies  
**Task:** Task 3 — Modeling and Evaluation
