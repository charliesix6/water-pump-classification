# Predictive Maintenance of Water Pumps in Tanzania

## Project Overview

This project focuses on predicting the operational status of water pumps in Tanzania using Machine Learning techniques.

The objective is to classify pumps into three categories:

- Functional
- Functional but needs repair
- Non-functional

The project was developed as an end-to-end Data Analytics & Machine Learning workflow, covering:

- Exploratory Data Analysis (EDA)
- Data Cleaning & Feature Engineering
- Handling Missing Values
- Encoding Categorical Variables
- Class Imbalance Treatment
- Model Training & Evaluation
- Kaggle-style Competition Submission

---

# Business Problem

Access to clean water is a critical issue in many regions of Tanzania. Predicting which water pumps are likely to fail can help organizations prioritize maintenance efforts and improve resource allocation.

Using historical operational data, this project builds predictive models capable of identifying malfunctioning pumps before complete failure.


# Tech Stack

- Python
- Pandas
- NumPy
- Scikit-learn
- XGBoost
- Imbalanced-learn (SMOTE)
- Matplotlib / Seaborn
- Jupyter Notebook

# Dataset

The dataset contains operational and geographical information about water pumps across Tanzania.

### Main Features

- GPS coordinates
- Population served
- Water quantity
- Pump type
- Installer
- Management type
- Construction year
- Extraction type
- Geographic region

Target variable:

- `status_group`

# Exploratory Data Analysis

During the initial analysis:

- Numerical and categorical variables were identified
- Missing values and anomalous values were detected
- High-cardinality categorical features were analyzed
- Strong class imbalance was identified in the target variable

### Key Findings

- Several columns contained a high percentage of missing values
- Some numerical columns contained impossible values (e.g. longitude = 0)
- Multiple categorical variables had extremely high cardinality
- The target classes were imbalanced


# Data Cleaning & Preprocessing

The preprocessing pipeline included:

## Missing Values

- Numerical variables → median imputation
- Categorical variables → mode imputation

## Feature Selection

Redundant or low-value columns were removed:

- `recorded_by`
- `wpt_name`
- `scheme_name`
- `subvillage`
- duplicated extraction variables

## Feature Engineering

New variables were created from dates:

- Recording year
- Recording month
- Pump age (`record_year - construction_year`)

## Encoding

Categorical variables were transformed using:

- Label Encoding

## Class Imbalance

Two strategies were tested:

- Class weights
- SMOTE oversampling


# Models Tested

## Random Forest

The main baseline model used for experimentation.

### Best Configuration

- 800 trees
- Random state fixed for reproducibility
- Parallel processing enabled (`n_jobs=-1`)

### Results

- Competition Score: **0.7585**
- Strong performance on majority classes
- Better generalization than SMOTE approach


## XGBoost

An additional gradient boosting model was tested.

### Findings

- Similar validation accuracy to Random Forest
- Lower leaderboard performance
- More computationally expensive


# Evaluation Metrics

The project evaluates models using:

- Accuracy
- Precision
- Recall
- F1-Score
- Classification Report

Special attention was given to minority class performance.


# Results Summary

| Model | Approach | Public Score |
|---|---|---|
| Random Forest | Baseline | 0.7576 |
| Random Forest | 800 Trees | **0.7585** |
| Random Forest + SMOTE | Oversampling | Lower performance |
| XGBoost | Gradient Boosting | 0.7240 |


# Key Learnings

This project helped reinforce practical skills in:

- Real-world data cleaning
- Feature engineering
- Handling imbalanced datasets
- Machine Learning experimentation
- Model evaluation for multiclass classification
- Iterative improvement process
- Kaggle competition workflows


# Future Improvements

Potential next steps:

- Hyperparameter optimization with GridSearchCV / Optuna
- Target encoding for high-cardinality variables
- CatBoost implementation
- Advanced feature engineering
- Geospatial analysis using coordinates
- Ensemble methods


# Suggested Repository Structure

```bash
water-pump-prediction/
│
├── data/
│   ├── raw/
│   ├── processed/
│
├── notebooks/
│   ├── 01_eda.ipynb
│   ├── 02_preprocessing.ipynb
│   ├── 03_modeling.ipynb
│
├── src/
│   ├── preprocessing.py
│   ├── feature_engineering.py
│   ├── train_model.py
│   ├── evaluate.py
│
├── models/
│
├── outputs/
│   ├── figures/
│   ├── submissions/
│
├── requirements.txt
├── README.md
└── .gitignore
```

---

# CV-Ready Description

### Data Analyst / Machine Learning Project

Built an end-to-end machine learning pipeline to predict water pump failures in Tanzania using Random Forest and XGBoost models. Performed data cleaning, feature engineering, missing value imputation, class imbalance handling (SMOTE), and model evaluation on a multiclass classification problem. Achieved a public competition score of 0.7585 through iterative experimentation and optimization.


# Ideas to Make the Repository More Professional

## Add Visualizations

Include:

- Class distribution charts
- Correlation heatmaps
- Feature importance plots
- Confusion matrix

## Add a Requirements File

```txt
pandas
numpy
scikit-learn
xgboost
imbalanced-learn
matplotlib
seaborn
jupyter
```

## Clean the Notebook

Before uploading:

- Remove duplicated cells
- Translate comments to English
- Delete unnecessary prints
- Add section headers
- Add conclusions after each phase


# Final Takeaway

This project demonstrates practical Data Analytics and Machine Learning skills using a real-world dataset with complex preprocessing challenges and imbalanced multiclass classification.

It is highly suitable for showcasing:

- Data cleaning skills
- Exploratory analysis
- Predictive modeling
- Business-oriented problem solving
- End-to-end ML workflow execution
