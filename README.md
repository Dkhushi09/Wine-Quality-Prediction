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

[cite_start]This project explores the Wine Quality dataset through detailed EDA and preprocessing[cite: 25]. [cite_start]By analysing physicochemical properties of red wine, we uncover patterns, detect outliers, handle skewed features, and apply scaling to prepare the data for machine learning[cite: 26]. [cite_start]The goal is to make the dataset model-ready for accurate wine quality prediction[cite: 27].

## Dataset Details

* [cite_start]**Dataset Name:** Wine Quality Dataset [cite: 29]
* [cite_start]**Source:** https://archive.ics.uci.edu/dataset/186/wine+quality [cite: 30]
* [cite_start]**Target Variable:** The primary focus for future modeling is to predict wine quality (a score ranging from 3 to 8), based on its physicochemical properties such as acidity, sugar content, pH, alcohol, and more[cite: 31].

## Data Loading and Initial Inspection

[cite_start]The first step involved loading the dataset and performing an initial inspection to understand its basic structure, data types, and check for missing values[cite: 33].

**Key Steps:**
* [cite_start]Loaded the dataset using `pandas.read_csv()` with a semicolon (`;`) delimiter as used in the file[cite: 35].
* [cite_start]Displayed the first few records using `df.head()`, checked column data types and non-null values using `df.info()`, and reviewed summary statistics using `df.describe()`[cite: 36].
* [cite_start]Checked for missing values across all columns using `df.isnull().sum()`[cite: 37].
* [cite_start]Analyzed the distribution of the target variable (`quality`) using `value_counts()` and visualized it using `seaborn.countplot()`[cite: 38].

**Observations:**
* [cite_start]**Dataset Size:** The dataset comprises 1599 rows and 12 columns, including 11 physicochemical features and 1 target variable (quality)[cite: 40].
* [cite_start]**Missing Values:** There were no missing values in the dataset, indicating that it is complete and ready for analysis without imputation[cite: 41].
* [cite_start]**Column Names:** Column names were already clear and concise, such as fixed acidity, residual sugar, alcohol, etc., requiring no renaming for readability or coding convenience[cite: 42].
* **Data Types:**
    * [cite_start]All columns, including the target quality, were identified as numerical, specifically float64 or int64[cite: 44].
    * [cite_start]This makes the dataset well-suited for both regression and classification models without the need for encoding or string manipulation[cite: 45].
* **Descriptive Statistics:**
    * [cite_start]The range and spread of feature values varied significantly across columns[cite: 47].
    * [cite_start]For instance, alcohol ranged from around 8% to 14.9%, while residual sugar showed values up to 15+, highlighting the need for feature scaling[cite: 48].
    * [cite_start]Some features like residual sugar, sulphates, and chlorides showed right-skewed distributions with long tails, as confirmed by skewness metrics[cite: 49].
    * [cite_start]The target variable quality had an imbalanced distribution, with the majority of wines receiving a score of 5, 6, or 7, and very few samples scoring 3, 4, or 8[cite: 50].
    * [cite_start]Correlation analysis revealed that alcohol had the strongest positive correlation with wine quality, while volatile acidity showed a negative correlation, indicating their potential importance in predictive modeling[cite: 51].

## Data Cleaning and Preprocessing

[cite_start]Based on the initial inspection, several cleaning and preprocessing steps were performed to prepare the data for analysis and modeling[cite: 53].

### Data Coverage and Duplicates Verification

* [cite_start]**Scope:** The dataset contains 1599 samples of red wine with no geographical or temporal metadata (such as region or year of production)[cite: 55].
* [cite_start]**Duplicates:** A check for duplicate rows (`df.duplicated().sum()`) confirmed that no duplicate entries were present, ensuring the dataset’s integrity and uniqueness[cite: 56].
* [cite_start]**Time/Location Metadata:** The dataset does not include columns like Year, Month, or State, so no datetime conversion or sorting was needed[cite: 57]. [cite_start]This makes the dataset non-temporal and purely observational in structure[cite: 58].

### One-Hot Encoding

* [cite_start]Since all columns in the dataset are numerical, there is no need for one-hot encoding[cite: 60].
* [cite_start]The target column quality is ordinal (integer scores from 3 to 8), which can be used as-is for regression, or categorized (e.g., low, medium, high) and label encoded if using classification models[cite: 61, 62, 63].
* [cite_start]Hence, no categorical encoding (e.g., One-Hot) was performed[cite: 64].

### Feature Scaling for Numerical Columns

* [cite_start]All numerical features (excluding quality) were standardized using StandardScaler[cite: 66].
* [cite_start]This transformed them to have: Mean = 0 and Standard Deviation = 1[cite: 67, 68].
* [cite_start]This scaling step was crucial because the dataset includes features with vastly different ranges (e.g., residual sugar vs pH vs alcohol), and unscaled features could bias model learning[cite: 69].
* [cite_start]Standardization improves performance for many machine learning models, especially SVM, Logistic Regression, KNN, and Neural Networks[cite: 70].

## Exploratory Data Visualizations

[cite_start]Visualizations were used to uncover patterns, distributions, and relationships within the data[cite: 72].

### Distribution of Features

[cite_start]Histograms revealed the distribution shapes of key numerical variables[cite: 73].

**Observations:**
* [cite_start]Most features are right-skewed (e.g., residual sugar, free sulfur dioxide)[cite: 77].
* [cite_start]Alcohol is approximately normally distributed[cite: 78].
* [cite_start]Knowing the skewness helps decide whether to apply log transformations[cite: 79].

### Box Plots of Numerical Features

[cite_start]Box plots provided a visual summary of the distribution's spread, median, quartiles, and especially aided in identifying outliers[cite: 81].

**Observations:**
* [cite_start]Several features contain outliers, especially: residual sugar, free sulfur dioxide, and total sulfur dioxide[cite: 84, 85, 86, 87].

### Correlation Matrix Heatmap

[cite_start]A heatmap was generated to visualize the linear relationships between numerical features[cite: 88].

**Observations:**
* [cite_start]Alcohol has the strongest positive correlation with quality[cite: 91].
* [cite_start]Volatile acidity has a strong negative correlation with quality[cite: 92].
* [cite_start]Some features are correlated with each other (e.g., citric acid and fixed acidity), which could affect model performance due to multicollinearity[cite: 93].

### Pairplot

[cite_start]A pairplot was generated to visualize relationships between numerical features and their correlation with the target variable quality[cite: 95].

**Observations:**
* [cite_start]Higher quality wines tend to have higher alcohol and lower volatile acidity[cite: 98].
* [cite_start]No clear separation in most feature pairs, suggesting the need for advanced models or feature engineering[cite: 99].
* [cite_start]Scatterplots indicate non-linear relationships, which simpler models might miss[cite: 100].

## Conclusion

[cite_start]This comprehensive Exploratory Data Analysis has provided a solid understanding of the Wine Quality dataset[cite: 102]. Key findings include:
* [cite_start]The dataset is clean, complete, and free of missing or duplicate values[cite: 103].
* [cite_start]All features are numerical, requiring no encoding, and column names were already concise and descriptive[cite: 103].
* [cite_start]Several features, such as residual sugar, chlorides, and sulphates, exhibited skewness and outliers, which were addressed through transformation and filtering[cite: 104].
* [cite_start]Standardization was applied to normalize feature scales and improve model compatibility[cite: 104].
* [cite_start]Correlation and pairplot analysis revealed that alcohol positively influences wine quality, while volatile acidity has a negative impact[cite: 104].
* [cite_start]Visualizations like boxplots, heatmaps, and histograms helped uncover data patterns and guided preprocessing decisions[cite: 104].

[cite_start]With the dataset now thoroughly cleaned and pre-processed, it is fully prepared for the next phase: building predictive machine learning models to estimate wine quality based on its physicochemical properties[cite: 105].
