# BTC Price Prediction Pipeline

This project focuses on predicting the next day high, low, and close prices of Bitcoin based on historical data using a linear regression model. The workflow includes preprocessing, feature engineering, training a model, and creating a reusable pipeline for predictions on new data.

## Dataset

The dataset used in this project is from Kaggle. You can download it from the following link:

[Kaggle Bitcoin 1-Minute Data](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data)

Please download the dataset and place it in the project folder before running the code.
---

## Project Overview

### Problem Statement
Predict the future price movements of Bitcoin using historical price data to assist in making informed trading decisions.

### Steps Performed
1. **Data Cleaning:**
   - Removed missing values to ensure data consistency.
   - Converted timestamps to datetime for better handling of time-series data.

2. **Feature Engineering:**
   - Shifted the `High`, `Low`, and `Close` columns by one step to create target variables: `Next_High`, `Next_Low`, and `Next_Close`.
   - Sorted the dataset by timestamp for proper sequential analysis.

3. **Data Scaling:**
   - Standardized all features using `StandardScaler` to ensure uniformity in feature magnitudes.

4. **Model Training:**
   - Split the data into training and testing sets.
   - Trained a `LinearRegression` model to predict the next high, low, and close prices.

5. **Pipeline Creation:**
   - Combined preprocessing and the model into a single pipeline for ease of use with new datasets.

6. **Prediction:**
   - Input new data with features like `Open`, `High`, `Low`, `Close`, and `Volume` to get predictions for the next high, low, and close prices.

---

## Input and Output Example

### Input Format:
The dataset must include the following columns:
| Open   | High   | Low    | Close  | Volume |
|--------|--------|--------|--------|--------|
| 10100  | 10200  | 10050  | 10150  | 5000   |

### Output Format:
Predictions will look like this:
| Next_High | Next_Low | Next_Close |
|-----------|----------|------------|
| 10250     | 10100    | 10175      |

---

## File Structure
