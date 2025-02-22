# Bike Sharing Demand Prediction

## Project Overview
This project analyzes and predicts bike-sharing demand using historical data. The dataset consists of daily records of bike rentals, capturing various features like weather conditions, seasonal variations, holidays, and working days to build an effective predictive model.

## Dataset Description
The dataset used in this project is `day.csv`, which contains 730 observations with the following features:

- `instant`: Record index
- `dteday`: Date
- `season`: Season (1: Spring, 2: Summer, 3: Fall, 4: Winter)
- `yr`: Year (0: 2018, 1: 2019)
- `mnth`: Month (1 to 12)
- `holiday`: Whether the day is a holiday (0: No, 1: Yes)
- `weekday`: Day of the week (0: Sunday - 6: Saturday)
- `workingday`: If the day is neither a weekend nor a holiday (0: No, 1: Yes)
- `weathersit`: Weather situation (1: Clear, 2: Mist, 3: Light Snow/Rain, 4: Heavy Snow/Rain)
- `temp`: Temperature in Celsius
- `atemp`: Perceived temperature in Celsius
- `humidity`: Humidity percentage
- `windspeed`: Wind speed
- `casual`: Count of casual users
- `registered`: Count of registered users
- `cnt`: Total count of bike rentals (Target variable)

## Data Preprocessing
- Removed unwanted columns (`instant`, `dteday`, `casual`, `registered`)
- Encoded categorical variables (`season`, `month`, `weekday`, `weathersit`)
- Created dummy variables for categorical columns
- Normalized numerical variables using `MinMaxScaler`
- Split dataset into training (70%) and testing (30%)

## Exploratory Data Analysis (EDA)
- Visualized categorical variables using box plots
- Observed correlations using heatmaps
- Identified key influencing factors: **temperature, windspeed, season, and weather conditions**

## Model Building
### Regression Approach
- **Feature Selection:** Used Recursive Feature Elimination (RFE) to select important predictors.
- **Variance Inflation Factor (VIF):** Ensured minimal multicollinearity among predictors.
- **Model Training:** Built multiple linear regression models, iteratively removing insignificant variables.
- **Final Model Performance:**
  - **Train Dataset Adjusted R²**: 0.829
  - **Test Dataset Adjusted R²**: 0.794
  - **Durbin-Watson Statistic**: 2.051 (indicating no autocorrelation in residuals)
  - **Final Variables:**
    - `year`, `holiday`, `temp`, `windspeed`, `july`, `sep`, `Light_snowrain`, `Misty`, `spring`, `summer`, `winter`

## Model Evaluation
- **Residual Analysis:** Checked normality and homoscedasticity of residuals.
- **Comparison Between Train and Test Data:** The model performed well on both datasets, with **R² of 0.833 (Train) and 0.803 (Test)**.
- **Regression Plot:** Showed a strong correlation between actual and predicted values.

## Conclusion
- The model effectively predicts bike rental demand.
- **Key Insights:**
  - Demand is higher in **summer and fall seasons**.
  - **Temperature and wind speed** significantly impact demand.
  - **Weather conditions (Mist & Snow/Rain)** negatively affect rentals.
  - **Holidays see a lower rental demand**.
  
## License & Citation
This dataset is from the research paper:
> **Fanaee-T, Hadi, and Gama, Joao. "Event labeling combining ensemble detectors and background knowledge." Progress in Artificial Intelligence (2013): pp. 1-15. DOI: [10.1007/s13748-013-0040-3](https://doi.org/10.1007/s13748-013-0040-3)**

Use of this dataset in publications must be cited appropriately.

