# Bike Sharing Demand Prediction

A linear regression project that predicts daily bike-rental demand from weather, seasonal, and calendar data.

## What this covers
Multiple linear regression on the UCI/Capital Bikeshare `day.csv` dataset (730 daily observations), with the goal of both predicting rental count and identifying which factors (season, weather, temperature, etc.) drive demand. The focus is on the full regression workflow: cleaning and encoding features, checking for multicollinearity, iteratively simplifying the model, and validating assumptions on the residuals.

## Tech Stack
- Python, Jupyter Notebook
- **pandas / numpy** for data handling
- **matplotlib / seaborn** for EDA visualizations (box plots, correlation heatmaps)
- **scikit-learn** — `MinMaxScaler`, `train_test_split`, `LinearRegression`, `RFE` (Recursive Feature Elimination)
- **statsmodels** — OLS regression and `variance_inflation_factor` (VIF) for multicollinearity checks

## Approach
- **Preprocessing:** dropped non-predictive columns (`instant`, `dteday`, `casual`, `registered`), one-hot encoded categorical fields (season, month, weekday, weathersit), scaled numeric features with `MinMaxScaler`, and split 70/30 into train/test.
- **EDA:** box plots for categorical variables and a correlation heatmap to spot the strongest predictors up front (temperature, windspeed, season, and weather situation stood out).
- **Feature selection:** used RFE to shortlist candidate predictors, then dropped features with high VIF or low statistical significance one at a time while rebuilding the OLS model, until only significant, low-collinearity variables remained.
- **Final model** uses: `year`, `holiday`, `temp`, `windspeed`, `july`, `sep`, `Light_snowrain`, `Misty`, `spring`, `summer`, `winter`.

## Results
- Adjusted R² — **0.829 (train)**, **0.794 (test)**
- R² — **0.833 (train)**, **0.803 (test)**
- Durbin-Watson statistic: **2.051** (no meaningful autocorrelation in residuals)
- Residual analysis confirmed roughly normal, homoscedastic errors, and predicted-vs-actual plots showed a strong linear relationship.

**Key takeaways:** demand is highest in summer/fall, rises with temperature, falls with wind speed and adverse weather (mist, snow/rain), and dips on holidays.

## Running Locally
```bash
git clone https://github.com/vinay23is/Bike_Sharing.git
cd Bike_Sharing
pip install pandas numpy matplotlib seaborn scikit-learn statsmodels jupyter
jupyter notebook "Bike Sharing.ipynb"
```

## Data & Citation
Dataset: `day.csv` (see `data dictionary.txt` for full field descriptions), from:

> Fanaee-T, Hadi, and Gama, Joao. "Event labeling combining ensemble detectors and background knowledge." Progress in Artificial Intelligence (2013): pp. 1-15. DOI: [10.1007/s13748-013-0040-3](https://doi.org/10.1007/s13748-013-0040-3)

Use of this dataset in publications must be cited appropriately.
