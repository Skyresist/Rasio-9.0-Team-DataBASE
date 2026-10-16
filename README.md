# Daily CO₂ Emissions Prediction — RASIO 9.0

![Python](https://img.shields.io/badge/Python-3.12-3776AB?logo=python&logoColor=white)
![LightGBM](https://img.shields.io/badge/Model-LightGBM-2ea44f)
![Result](https://img.shields.io/badge/Result-8th%20place%20finalist-6f42c1)

Team **DataBASE**'s entry for the **RASIO 9.0** data science competition. The task: predict a city's daily CO₂ emissions (`daily_ktCO2`, kilotonnes) from IoT-style urban data — air quality, weather, traffic counts, public-transport ridership and calendar information.

**Result:** 8th place finalist out of 23 Kaggle leaderboard submissions (Kaggle score 2.213).

## Results

Chronological 80/20 split (no shuffling, so the model is always tested on days after the ones it trained on):

| Split | RMSE | R² | NRMSE |
|---|---:|---:|---:|
| Train | 1.38 | 0.94 | 4.3% |
| Test  | 1.95 | 0.77 | 7.0% |

## The data problem

The raw training set had **1,606 days × 60 columns** and was deliberately messy. Most of the work was cleaning:

- **Sparse columns:** dropped 20 columns with more than 70% missing values (SO₂ and most hourly vehicle counts), keeping `avg_ridership_monthly` and imputing it by month instead.
- **Redundant features:** removed highly correlated weather variables (`temp_calib`, `feelslikemax`, `feelslikemin`, `rain`) after inspecting a correlation heatmap.
- **Time-aware imputation:** filled pollutant gaps (PM2.5, PM10, O₃, NO₂) with time-based interpolation on a date index rather than a global mean.
- **Physically impossible values:** detected out-of-range moon-phase values with physical bounds + IQR, then repaired them with interpolation and a rolling median.
- **Inconsistent labels:** normalised values like `yEs`, `nO`, `YES` with regex; rebuilt a messy weather `conditions` field into three clean categories; filled missing holiday flags from the official Indonesian holiday calendar.

## Features and model

- Calendar features: year, month, day of week, weekend flag, holiday flag
- One-hot encoded weather conditions and seasons
- Relative PM2.5 (daily value ÷ that month's average)
- **LightGBM** regressor, evaluated with RMSE, R² and normalised RMSE

## What I'd improve

- The train–test gap (R² 0.94 → 0.77) points to some overfitting; time-series cross-validation and stronger regularisation would give a more reliable estimate.
- Lag and rolling-window features of past emissions were not used and would likely help.

## Files

| File | Contents |
|---|---|
| `Rasio_9.0_DataBASE.ipynb` | Full workflow: cleaning, feature engineering, modelling, evaluation |
| `datatrain.csv` / `datatest.csv` | Competition data |
| `submission.csv` | Final Kaggle submission |

## Tools

Python · pandas · NumPy · scikit-learn · LightGBM · holidays · Matplotlib · Seaborn · Google Colab

## Team

**DataBASE** — Clayvent Yuuki William, Teresa Tendeas and Kenrich Heavenly Sandria.
