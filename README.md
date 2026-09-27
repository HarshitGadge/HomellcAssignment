# U.S. Home Prices: Case-Shiller Index Take-Home Assignment

A take-home assignment: model the S&P/Case-Shiller U.S. National Home Price Index (FRED series `CSUSHPISA`, monthly, seasonally adjusted,
January 1987 – July 2023, 439 observations).

## What the notebook does

- Loads the monthly index and checks it for missing values and duplicates (there are none)
- Plots the index over time
- Adds calendar features (year, month, week of year)
- Fits a linear regression and reports train/test RMSE (23.09 / 24.74) and R² (0.85 / 0.85)

## Limitations, and what a stronger version would do

- **Random split on a time series.** The regression uses a random 80/20 split, so the model is tested on months that fall between training
  months. That flatters the score. A chronological hold-out, such as the last 24 months, is the honest test. The notebook creates that
  split but doesn't use it for the model.
- **Calendar features only.** Year and month mostly capture the trend. Explaining home prices needs external drivers: 30-year mortgage
  rates, median household income, housing starts, unemployment, CPI and population. All of these are available from FRED.

## Run it

Download `CSUSHPISA.csv` from FRED (https://fred.stlouisfed.org/series/CSUSHPISA) next to the notebook, then run it.

Tools: pandas, scikit-learn, matplotlib, seaborn, plotly.

Notebook: [`case_shiller_home_prices.ipynb`](case_shiller_home_prices.ipynb)
