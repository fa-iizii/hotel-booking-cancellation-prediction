# Hotel Booking Cancellation Prediction

![Python](https://img.shields.io/badge/Python-3.8%2B-blue)
![Scikit-Learn](https://img.shields.io/badge/Scikit--Learn-Latest-lightgrey)
![Pandas](https://img.shields.io/badge/Pandas-Data_Manipulation-green)
![Status](https://img.shields.io/badge/Model_Accuracy-86.33%25-success)

A machine learning pipeline designed to predict hotel booking cancellations using a Random Forest Classifier. This project emphasizes rigorous data pre-processing, feature engineering, and exploratory data analysis (EDA) to extract actionable insights for hotel management.

---

## Table of Contents
1. [Project Overview](#project-overview)
2. [Key Findings](#key-findings)
3. [Project Structure](#project-structure)
4. [Pipeline and Methodology](#pipeline-and-methodology)
5. [Installation and Setup](#installation-and-setup)
6. [Usage Instructions](#usage-instructions)

---

## Project Overview
* **Objective:** Predict whether a hotel guest will cancel their booking based on historical booking data. 
* **Model Used:** Random Forest Classifier.
* **Performance:** Achieved a predictive accuracy of **86.33%**.
* **Context:** Developed as part of a Data-driven Artificial Intelligence module. 

---

## Key Findings
Through feature importance extraction, the model identified the primary drivers of booking cancellations:
1. **Lead Time:** Guests who book far in advance are significantly more likely to cancel.
2. **Previous Cancellations:** A history of cancellations is a strong predictor of future cancellations.
3. **Deposit Type:** The type of deposit paid (or lack thereof) heavily influences commitment to the booking.

These insights allow hotel management to identify at-risk bookings early and adjust overbooking or deposit strategies accordingly.

---

## Project Structure

```text
HOTEL-BOOKING-CANCELLATION-PREDICTION/
│
├── CODEBASE_DOCS.md                              # Detailed breakdown of codebase logic
├── hotel-booking-cancellation-prediction.ipynb   # Main executable Jupyter Notebook
├── readme.md                                     # Project documentation
├── CHS2406_Coursework1_Assignmnet_brief.docx     # Assignment brief (ignored via .gitignore)
└── hotel_bookings.csv                            # Dataset (ignored via .gitignore)