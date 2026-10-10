# 🌍 Daily Kt_CO2 Prediction using Machine Learning

This project was created as part of a **data science competition** focused on analyzing and predicting global air pollution using energy and sustainability datasets.  
Our team advanced to the **final round (Top 10)** and achieved **8th place overall**, with a **Kaggle score of 2.213**, ranking **8th out of 23 leaderboard submissions**.

---

## 🧠 Project Overview

The goal of this notebook was to explore how global **energy consumption patterns** influence **air pollution levels** and to build predictive models capable of estimating pollutant concentrations using real-world environmental data.

---

## 🔍 Workflow Summary

### 1. **Data Cleaning & Preparation**
- Combined multiple open datasets on air pollution and sustainable energy
- Standardized country names, years, and measurement units
- Removed missing and inconsistent entries

### 2. **Exploratory Data Analysis (EDA)**
- Identified correlations between energy sources (renewable vs non-renewable) and pollution levels  
- Visualized country-wise and time-series trends

### 3. **Feature Engineering & Preprocessing**
- Scaled numerical features and encoded categorical variables  
- Handled multicollinearity and outliers  
- Selected top predictors for modeling

### 4. **Machine Learning Models**
Implemented and compared several regressors:
- `Support Vector Regression (SVR)`
- `ElasticNet Regression`
- `Random Forest Regressor`
- `XGBoost Regressor`
- `Stacking Ensemble`

### 5. **Model Evaluation**
- Evaluated using **RMSE** and **R²** metrics  
- Ensemble methods provided the most consistent predictions  
- Final Kaggle score: **2.213**

---

## 🌱 Key Insights
- Higher renewable energy use generally correlates with **lower PM2.5 and CO₂ levels**
- Countries dependent on fossil fuels exhibited **higher pollution variability**
- Ensemble models achieved **stronger generalization** across unseen data

---

## 🛠️ Tools & Libraries
- `Python`, `Pandas`, `NumPy`
- `Scikit-learn`, `XGBoost`
- `Matplotlib`, `Seaborn`
- `Jupyter Notebook`

---

## 🏁 Competition Results
- 🏆 **Finalist Team (8th out of 10)**
- 📈 **Kaggle Score: 2.213 (10th/23 leaderboard)**

---

## 📂 File Guide
- `notebook1.ipynb` — Full workflow: data cleaning, EDA, feature engineering, model training, and evaluation.

---

## 💡 Summary
This notebook demonstrates the integration of real-world datasets, data preprocessing, and multiple machine learning models to uncover sustainability-driven insights.  
It highlights how data science can inform energy policies and contribute toward a cleaner, more sustainable future.
