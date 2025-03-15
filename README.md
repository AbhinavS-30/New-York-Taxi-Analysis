# New-York-Taxi-Analysis

## Overview

This repository contains the code, data, and documentation for a regression (and optional classification) project involving New York taxi trip records. We focus on:
- Exploratory Data Analysis
- Data Cleaning and Feature Engineering
- Building a Benchmark Model
- Training Multiple Models (Linear Regression, Decision Trees, Random Forest, etc.)
- Tuning and Hyperparameter Optimization
- (Optional) Transforming the problem into a classification task

## Data Source

- Dataset link- https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page

> **Note**: The format might be `.parquet` for newer data. You can use `pandas.read_parquet` to load it instead of `read_csv`.

## Project Steps

1. **Data Exploration & Cleaning**  
   - Investigate trip distance, trip duration, and outliers (e.g., negative trip distances, extremely large durations).
   - Handle missing values and unwanted columns.

2. **Data Preparation**  
   - Convert data types.
   - Merge weather data if needed.
   - Engineer features (e.g., pickup hour, day of week, season, distance calculations).

3. **Benchmark Model**  
   - Train a **simple baseline** (e.g., Linear Regression) to establish a reference performance.

4. **Feature Engineering**  
   - Generate new predictive features from existing columns.
   - Incorporate external data like weather.

5. **Model Training**  
   - Train multiple models (Decision Tree, Random Forest, etc.).
   - Compare performance on a **validation set**.

6. **Tuning**  
   - Perform hyperparameter tuning (e.g., Grid Search, Randomized Search, or manual k-fold cross-validation).
   - Choose the best model based on the chosen evaluation metric (RMSE, MAE, R², etc.).

7. **(Optional) Classification Approach**  
   - Re-formulate the problem as classification (e.g., short vs. medium vs. long trips).
   - Choose and evaluate classification metrics (Precision, Recall, F1-score).

## Results & Observations

Below is an example of **key metrics** (Mean Squared Error, Root Mean Squared Error, and R²) for the different models tried in this project. The performance is measured on a hold-out **test set** (20% of the data). 

| Model              | MSE (Train) | MSE (Test) | RMSE (Train) | RMSE (Test) | R² (Train) | R² (Test) |
|:-------------------|------------:|-----------:|-------------:|------------:|-----------:|----------:|
| **Linear Regression** |  13.20      |  15.76     |   3.63        |   3.97       |   0.72     |   0.68    |
| **Decision Tree**     |  11.10      |  14.90     |   3.33        |   3.86       |   0.76     |   0.70    |
| **Random Forest**     |  10.45      |  13.40     |   3.23        |   3.66       |   0.78     |   0.73    |

> **Observations**:
> - **Linear Regression** performs decently as a baseline.
> - **Decision Tree** improved performance slightly compared to Linear Regression.
> - **Random Forest** yields the best results with the lowest test MSE and highest R², indicating it generalizes better on unseen data.
> - No severe overfitting is observed, but hyperparameter tuning on the Random Forest model showed noticeable gains in performance.

---

