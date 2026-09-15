# Employee Attrition Prediction with Logistic Regression

## Overview

This project uses logistic regression to analyze and predict employee attrition using a synthetically generated dataset. The analysis focuses not only on predictive performance, but also on interpreting model coefficients, evaluating classification tradeoffs, and selecting an appropriate classification threshold.

> **Note:** The dataset is synthetic and was created for educational and portfolio purposes. It does not contain real employee or company data.

## Objectives

* Identify factors associated with employee attrition.
* Build and evaluate a logistic regression classification model.
* Interpret model coefficients using odds ratios.
* Compare L1 and L2 regularization using cross-validation.
* Evaluate accuracy, precision, recall, and F1 score.
* Examine how changing the classification threshold affects model performance.
* Connect model results to practical business decisions.

## Dataset

The dataset contains 500 synthetic employee records with the following variables:

* **Age**
* **MonthlyIncome**
* **YearsAtCompany**
* **JobSatisfaction**
* **Overtime**
* **DistanceFromHome**
* **Attrition** — target variable indicating whether an employee left the organization.

## Modeling Approach

The analysis includes:

1. Exploratory data analysis
2. Logistic regression classification
3. Coefficient and odds-ratio interpretation
4. L1 and L2 regularization
5. Cross-validation for model comparison
6. Evaluation using a held-out test set
7. Classification threshold analysis
8. Interactive visualization of threshold effects

## Key Findings

The logistic regression model identified several meaningful associations with employee attrition.

Holding other variables constant:

* A one-point increase in **Job Satisfaction** was associated with approximately **22.5% lower odds** of attrition.
* Each additional year at the company was associated with approximately **11.5% lower odds** of attrition.
* **Overtime** was associated with approximately **17.9% higher odds** of attrition.
* **Distance From Home** was associated with approximately **4.5% higher odds per unit of distance**.

These results represent model associations rather than causal relationships.

## Classification Threshold Analysis

The project demonstrates why a classification threshold should not automatically be assumed to be 0.50.

Changing the threshold changes the balance between false positives and false negatives. For example, on the test set:

| Threshold | Accuracy | Precision | Recall |    F1 |
| --------: | -------: | --------: | -----: | ----: |
|       20% |    62.0% |     41.1% |  82.1% | 54.8% |
|       30% |    68.0% |     44.7% |  60.7% | 51.5% |
|       40% |    79.0% |     66.7% |  50.0% | 57.1% |
|       50% |    77.0% |     72.7% |  28.6% | 41.0% |
|       60% |    73.0% |     66.7% |   7.1% | 12.9% |

The 20% threshold identifies the largest proportion of actual attrition cases, while the 50% threshold is more conservative and produces higher precision but substantially lower recall.

The appropriate threshold ultimately depends on the relative business costs of false positives and false negatives.

## Interactive Visualization

The notebook includes an interactive classification-threshold visualization. Users can adjust the threshold and observe the predicted classifications, confusion matrix, and evaluation metrics update in real time.

![Interactive Threshold Analysis](images/threshold_analysis.png)

## Technologies

* Python
* pandas
* NumPy
* scikit-learn
* Matplotlib
* Seaborn
* Jupyter Notebook
* ipywidgets
* ipympl

## Project Structure

```text
employee-attrition-logistic-regression/
│
├── employee_attrition_logistic_regression.ipynb
├── README.md
├── requirements.txt
├── data/
│   └── employee_attrition.csv
└── images/
    └── threshold_analysis.png
```

## Limitations

This project uses synthetic data and therefore should not be interpreted as evidence about actual employee behavior. Model performance and estimated relationships are specific to this dataset.

In a real-world application, additional considerations would include data quality, class imbalance, calibration, fairness, temporal validation, feature availability at prediction time, and the business cost of different types of prediction errors.
