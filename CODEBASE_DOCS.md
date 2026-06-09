# Codebase Architecture and Documentation

This document provides a technical walkthrough of the Jupyter Notebook (`hotel-booking-cancellation-prediction.ipynb`) to explain the data transformations and modeling decisions.

---

## 1. Data Loading and Initial Inspection
* **Libraries:** Uses `pandas` for data manipulation, `matplotlib` and `seaborn` for visualization, and `scikit-learn` for machine learning.
* **Ingestion:** Loads the CSV dataset. Initial commands (`df.info()`, `df.describe()`, `df.isnull().sum()`) establish a baseline understanding of missing values and feature distributions.

---

## 2. Data Pre-processing Pipeline
To prevent the model from artificially inflating its accuracy and to handle messy data, strict cleaning rules were applied.

### A. Feature Pruning
* **Data Leakage Prevention:** Removed `reservation_status` and `assigned_room_type`. Because `reservation_status` directly mirrors the target variable (`is_canceled`), keeping it would render the model useless for future predictions.
* **Irrelevant/Sparse Data:** Removed `reservation_status_date`, `country`, `agent`, and `company` due to either high cardinality, low predictive value, or excessive missing values.

### B. Missing Value Imputation
* Missing values in the `children` column were replaced with `0`, operating under the logical assumption that a null entry implies no children were present for the booking.

### C. Inconsistency Filtering
* Identified and dropped 180 rows where the total sum of adults, children, and babies was 0 (ghost bookings).
* Identified and dropped 715 rows where both weekend and weekday stays were 0.

### D. Data Type Optimization
* Converted numerical discrete columns (like `children`) strictly to integers.
* Converted categorical variables (`arrival_date_month`, `deposit_type`, `meal`, `customer_type`, etc.) to the `category` datatype to streamline downstream encoding and visualization.

---

## 3. Exploratory Data Analysis (EDA)
* **Correlation Analysis:** A Seaborn heatmap was utilized to observe the multicollinearity between numeric features, ensuring no highly redundant features skewed the model weights.
* **Trend Identification:** Aggregated data to uncover key insights requested by management, such as the cancellation ratios across different hotel types.

---

## 4. Modeling and Evaluation
* **Algorithm Selection:** A Random Forest Classifier was chosen due to its robustness against overfitting and its ability to natively handle complex interactions between mixed data types (categorical and continuous).
* **Data Splitting:** Applied `train_test_split` with a stratified approach to ensure the 37% cancellation rate in the overall dataset was proportionally represented in both the training and testing sets.
* **Evaluation Metrics:** * Accuracy Score (86.33%)
  * Classification Report (Precision, Recall, F1-Score)
  * Confusion Matrix (to visualize False Positives vs. False Negatives)
* **Feature Importance:** Extracted the internal tree nodes to determine that `lead_time`, `previous_cancellations`, and `deposit_type` were the highest-weighted nodes for predicting cancellations.