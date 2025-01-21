# BTC Price Prediction Pipeline

This project focuses on predicting the next day's high, low, and close prices of Bitcoin based on historical data using machine learning models. The workflow includes exploratory data analysis (EDA), preprocessing, feature engineering, training models, and creating a reusable pipeline for predictions on new data.

---

## Dataset

The dataset used in this project is from Kaggle. You can download it from the following link:

[Kaggle Bitcoin 1-Minute Data](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data)

Please download the dataset and place it in the project folder before running the code.

---

## Project Overview

### Problem Statement
Predict the future price movements of Bitcoin using historical price data to assist in making informed trading decisions.

---

## Steps Performed

### 1. **Exploratory Data Analysis (EDA):**
- Computed 7-day (MA7) and 30-day (MA30) moving averages for better trend analysis.
- Analyzed correlations between features like `Open`, `High`, `Low`, `Close`, and `Volume`.
- Visualized price trends and volume over time using line plots and histograms.

### 2. **Data Cleaning:**
- Removed missing values to ensure data consistency.
- Converted timestamps to datetime for better handling of time-series data.

### 3. **Feature Engineering:**
- Shifted the `High`, `Low`, and `Close` columns by one step to create target variables: `Next_High`, `Next_Low`, and `Next_Close`.
- Included MA7 and MA30 as additional features to capture short-term and long-term trends.
- Sorted the dataset by timestamp for proper sequential analysis.

### 4. **Data Scaling:**
- Standardized all features using `StandardScaler` to ensure uniformity in feature magnitudes.

### 5. **Model Training and Experiments:**
- Split the data into training (80%) and testing (20%) sets.
- **Baseline Model**: Linear Regression
  - Achieved Mean Absolute Error (MAE) of **$75** for `Next_High`, **$50** for `Next_Low`, and **$60** for `Next_Close`.
- **Other Models Tested**:
  - **Random Forest Regressor**: Improved performance with an MAE of **$65**, **$45**, and **$55**, respectively.
  - **Gradient Boosting Regressor**: Achieved the best MAE of **$60**, **$42**, and **$50**, but with higher training time.
- Selected **Gradient Boosting Regressor** for the final pipeline due to its superior accuracy.

### 6. **Pipeline Creation:**
- Combined preprocessing (scaling and feature engineering) with the final model into a single pipeline.
- Ensures seamless predictions for new datasets without requiring manual preprocessing.

### 7. **Prediction:**
- Input new data with features like `Open`, `High`, `Low`, `Close`, `Volume`, MA7, and MA30 to get predictions for the next day's high, low, and close prices.

---

## Accuracy and Results

The performance of the models was evaluated using the Mean Absolute Error (MAE):

| Model                   | Next_High (MAE) | Next_Low (MAE) | Next_Close (MAE) |
|-------------------------|-----------------|----------------|------------------|
| Linear Regression       | $75            | $50            | $60             |
| Random Forest Regressor | $65            | $45            | $55             |
| Gradient Boosting       | **$60**        | **$42**        | **$50**         |

---

## Input and Output Example

### Input Format:
The dataset must include the following columns:
| Open   | High   | Low    | Close  | Volume | MA7   | MA30  |
|--------|--------|--------|--------|--------|-------|-------|
| 10100  | 10200  | 10050  | 10150  | 5000   | 10125 | 10090 |

### Output Format:
Predictions will look like this:
| Next_High | Next_Low | Next_Close |
|-----------|----------|------------|
| 10250     | 10100    | 10175      |

---

## How to Run

1. **Download the dataset**:  
   Download the dataset from Kaggle ([link here](https://www.kaggle.com/datasets/mczielinski/bitcoin-historical-data)) and place it in the project folder.
