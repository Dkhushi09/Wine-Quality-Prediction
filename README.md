# Wine Quality Prediction: Exploratory Data Analysis and Preprocessing
This repository contains the Exploratory Data Analysis (EDA) and preprocessing steps for the Wine Quality Dataset. The goal of this project is to prepare the dataset for building robust machine learning models to predict wine quality based on its physicochemical properties.

[cite_start]**Course Name:** Machine Learning [cite: 3]
[cite_start]**Course Code:** TE7253 [cite: 4]

[cite_start]**Student:** Khushi Dekate [cite: 5]
[cite_start]**PRN:** 22070521096 [cite: 7]
[cite_start]**Semester:** VII SEM [cite: 6]

## Table of Contents

* [Introduction](#introduction)
* [Dataset Details](#dataset-details)
* [Data Loading and Initial Inspection](#data-loading-and-initial-inspection)
* [Data Cleaning and Preprocessing](#data-cleaning-and-preprocessing)
    * [Data Coverage and Duplicates Verification](#data-coverage-and-duplicates-verification)
    * [One-Hot Encoding](#one-hot-encoding)
    * [Feature Scaling for Numerical Columns](#feature-scaling-for-numerical-columns)
* [Exploratory Data Visualizations](#exploratory-data-visualizations)
    * [Distribution of Features](#distribution-of-features)
    * [Box Plots of Numerical Features](#box-plots-of-numerical-features)
    * [Correlation Matrix Heatmap](#correlation-matrix-heatmap)
    * [Pairplot](#pairplot)
* [Conclusion](#conclusion)

## Introduction

This project delves into the Wine Quality dataset, performing detailed Exploratory Data Analysis (EDA) and preprocessing. By analyzing the physicochemical properties of red wine, we aim to uncover hidden patterns, detect outliers, handle skewed features, and apply appropriate scaling techniques. [cite_start]The ultimate objective is to prepare a "model-ready" dataset for accurate wine quality prediction using machine learning algorithms[cite: 25, 26, 27].

## Dataset Details

* [cite_start]**Dataset Name:** Wine Quality Dataset [cite: 29]
* [cite_start]**Source:** [UCI Machine Learning Repository](https://archive.ics.uci.edu/dataset/186/wine+quality) [cite: 30]
* [cite_start]**Target Variable:** The primary focus for future modeling is to predict `wine quality` (a score ranging from 3 to 8), based on its physicochemical properties such as acidity, sugar content, pH, alcohol, and more[cite: 31].

## Data Loading and Initial Inspection

[cite_start]The initial phase involved loading the dataset and conducting a preliminary inspection to understand its fundamental structure, data types, and identify any missing values[cite: 33].

**Key Steps:**
* [cite_start]Loaded the dataset using `pandas.read_csv()` with a semicolon (`;`) delimiter[cite: 35].
* [cite_start]Displayed the first few records using `df.head()`, checked column data types and non-null values using `df.info()`, and reviewed summary statistics using `df.describe()`[cite: 36].
* [cite_start]Checked for missing values across all columns using `df.isnull().sum()`[cite: 37].
* [cite_start]Analyzed the distribution of the target variable (`quality`) using `value_counts()` and visualized it using `seaborn.countplot()`[cite: 38].

**Observations:**
* [cite_start]**Dataset Size:** The dataset comprises 1599 rows and 12 columns, including 11 physicochemical features and 1 target variable (`quality`)[cite: 40].
* [cite_start]**Missing Values:** No missing values were found, indicating a complete dataset ready for analysis without imputation[cite: 41].
* [cite_start]**Column Names:** Column names were already clear and concise, requiring no renaming[cite: 42].
* [cite_start]**Data Types:** All columns, including the target `quality`, were identified as numerical (float64 or int64), making the dataset suitable for both regression and classification models[cite: 44, 45].
* **Descriptive Statistics:**
    * [cite_start]The range and spread of feature values varied significantly, highlighting the need for feature scaling (e.g., alcohol ranged from ~8% to 14.9%, while residual sugar showed values up to 15+)[cite: 47, 48].
    * [cite_start]Some features like `residual sugar`, `sulphates`, and `chlorides` exhibited right-skewed distributions with long tails[cite: 49].
    * [cite_start]The target variable `quality` had an imbalanced distribution, with most wines scoring 5, 6, or 7[cite: 50].
    * [cite_start]Correlation analysis revealed that `alcohol` had the strongest positive correlation with `quality`, while `volatile acidity` showed a negative correlation[cite: 51].

## Data Cleaning and Preprocessing

[cite_start]Based on the initial inspection, several crucial cleaning and preprocessing steps were performed to prepare the data for subsequent analysis and modeling[cite: 53].

### Data Coverage and Duplicates Verification

* [cite_start]**Scope:** The dataset contains 1599 samples of red wine, lacking geographical or temporal metadata[cite: 55].
* [cite_start]**Duplicates:** A check confirmed no duplicate entries were present, ensuring data integrity[cite: 56].
* [cite_start]**Time/Location Metadata:** No datetime conversion or sorting was needed as the dataset is non-temporal[cite: 57, 58].

### One-Hot Encoding

* [cite_start]Since all columns in the dataset are numerical, one-hot encoding was not required[cite: 60].
* [cite_start]The target column `quality` is ordinal (integer scores from 3 to 8) and can be used as-is for regression or categorized for classification models[cite: 61, 62, 63, 64].

### Feature Scaling for Numerical Columns

* [cite_start]All numerical features (excluding `quality`) were standardized using `StandardScaler`[cite: 66].
* [cite_start]This transformed them to have a mean of 0 and a standard deviation of 1[cite: 67, 68].
* [cite_start]This step was crucial due to the vastly different ranges of features, preventing bias in model learning[cite: 69].
* [cite_start]Standardization improves performance for many machine learning models, especially SVM, Logistic Regression, KNN, and Neural Networks[cite: 70].

## Exploratory Data Visualizations

[cite_start]Visualizations were instrumental in uncovering patterns, distributions, and relationships within the data[cite: 71, 72].

### Distribution of Features

[cite_start]Histograms provided insights into the distribution shapes of key numerical variables[cite: 73, 74].

[cite_start]![Histograms of Numerical Features](https://raw.githubusercontent.com/YOUR_USERNAME/YOUR_REPO_NAME/main/images/histograms.png) *Figure 1: Histograms of Numerical Features* [cite: 75]

**Observations:**
* [cite_start]Most features exhibit a right-skewed distribution (e.g., `residual sugar`, `free sulfur dioxide`)[cite: 77].
* [cite_start]`Alcohol` is approximately normally distributed[cite: 78].
* [cite_start]Understanding skewness aids in deciding whether to apply transformations like log transformations[cite: 79].



**Observations:**
* [cite_start]Several features contain outliers, notably `residual sugar`, `free sulfur dioxide`, and `total sulfur dioxide`[cite: 84, 85, 86, 87].

### Correlation Matrix Heatmap

[cite_start]A heatmap was generated to visualize the linear relationships between numerical features[cite: 88, 89].

**Observations:**
* [cite_start]`Alcohol` demonstrates the strongest positive correlation with `quality`[cite: 91].
* [cite_start]`Volatile acidity` exhibits a strong negative correlation with `quality`[cite: 92].
* [cite_start]Some features are correlated with each other (e.g., `citric acid` and `fixed acidity`), which could indicate multicollinearity[cite: 93].

### Pairplot

[cite_start]A pairplot was generated to visualize relationships between numerical features and their correlation with the target variable `quality`[cite: 94, 95].



**Observations:**
* [cite_start]Higher quality wines tend to have higher `alcohol` content and lower `volatile acidity`[cite: 98].
* [cite_start]There's no clear separation in most feature pairs, suggesting the potential need for advanced models or feature engineering[cite: 99].
* [cite_start]Scatterplots indicate the presence of non-linear relationships, which simpler models might overlook[cite: 100].

## Conclusion

This comprehensive Exploratory Data Analysis has provided a robust understanding of the Wine Quality dataset. Key findings include:
* [cite_start]The dataset is clean, complete, and free of missing or duplicate values[cite: 103].
* [cite_start]All features are numerical, requiring no encoding, and column names were already concise and descriptive[cite: 103].
* [cite_start]Several features, such as `residual sugar`, `chlorides`, and `sulphates`, exhibited skewness and outliers, which were addressed through transformation and filtering[cite: 104].
* [cite_start]Standardization was applied to normalize feature scales and improve model compatibility[cite: 104].
* [cite_start]Correlation and pairplot analysis revealed that `alcohol` positively influences wine quality, while `volatile acidity` has a negative impact[cite: 104].
* [cite_start]Visualizations like boxplots, heatmaps, and histograms helped uncover data patterns and guided preprocessing decisions[cite: 104].

[cite_start]With the dataset now thoroughly cleaned and pre-processed, it is fully prepared for the next phase: building predictive machine learning models to estimate wine quality based on its physicochemical properties[cite: 105].
