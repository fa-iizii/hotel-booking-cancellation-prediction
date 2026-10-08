# Hotel Booking Cancellation Prediction

A predictive machine learning project built with Python, scikit-learn, and Pandas to predict hotel reservation cancellations using historical booking data.

## Overview

- **Objective:** Binary classification to predict whether a customer will cancel their reservation (`is_canceled`).
- **Algorithm:** Random Forest Classifier
- **Evaluation Target:** >70% accuracy (achieved ~86.3% accuracy on a stratified test set)

## Pipeline

1. **Data Cleaning:**
   - Removed high-cardinality and target-leaking columns (`reservation_status_date`, `reservation_status`, `agent`, `company`, `assigned_room_type`, `country`).
   - Imputed missing values for numerical records (`children` imputed with 0).
   - Removed invalid booking rows (zero adults, children, and babies, or zero stay length).
2. **Exploratory Data Analysis (EDA):**
   - Assessed correlation matrices to identify relationships between numerical features and cancellations.
   - Evaluated cancellation rates by hotel type (City Hotel vs. Resort Hotel).
   - Analyzed booking frequency across meal types and room types.
3. **Feature Engineering:**
   - **Binning:** Discretized continuous lead time into defined intervals.
   - **One-Hot Encoding:** Encoded categorical features (`hotel`, `arrival_date_month`, `meal`, `market_segment`, `distribution_channel`, `deposit_type`, `customer_type`, `reserved_room_type`) using `pd.get_dummies(drop_first=True)` to avoid multicollinearity.
   - **Scaling:** Standardized numeric features with `StandardScaler` (zero mean, unit variance).
   - **Feature Selection:** Filtered low-variance attributes using `VarianceThreshold`.
4. **Data Splitting & Modeling:**
   - 70/30 train/test split using stratified sampling on `is_canceled` to preserve class balance.
   - Trained a `RandomForestClassifier` (fixed random state for reproducibility).

## Results

- **Test Accuracy:** ~86.3%
- Evaluated via precision, recall, F1-score, and confusion matrix analysis to ensure balanced performance across both cancellation and non-cancellation classes.
- Extracted feature importance metrics to identify key drivers of cancellations (e.g., lead time, deposit type, and previous cancellations).

## Tech Stack

- Python
- Pandas
- NumPy
- scikit-learn
- Matplotlib
- Seaborn
