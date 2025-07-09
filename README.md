# Nifty-Volatility-Model-with-Analytics
The challenge is to develop and optimize a trading strategy that can adapt to changing market conditions and consistently generate alpha (excess returns) while managing risk.

## Project Overview

This project focuses on developing a predictive statistical model to understand and forecast the 20-day rolling volatility of the Nifty 50 index. Leveraging historical financial and macroeconomic data, a multiple linear regression model was built to identify key drivers of volatility and provide insights into market dynamics.

## Objective

The primary objectives of this project were:
1.  To identify and quantify the relationship between Nifty Rolling Volatility and various financial and macroeconomic indicators.
2.  To construct a robust multiple linear regression model capable of explaining and predicting Nifty's 20-day rolling volatility.
3.  To visualize model performance, residuals, and key relationships using interactive dashboards.

## Data Sources

The analysis utilized historical daily data for the following variables:

* **Nifty 20-Day Rolling Volatility:** The dependent variable (calculated from Nifty Close prices).
* **Nifty Close:** Daily closing prices of the Nifty 50 index.
* **India VIX Close:** Daily closing values of the India VIX (Volatility Index).
* **Daily Log Returns for Nifty:** Calculated daily log returns of the Nifty 50.
* **Repo Rate %:** India's benchmark interest rate (lagged for analysis).
* **CPI (Consumer Price Index):** A key inflation indicator (lagged for analysis).
* **Lagged Nifty Rolling Volatility:** Previous day's Nifty 20-Day Rolling Volatility (used to capture persistence).

## Methodology

The project followed a structured data analysis and modeling approach:

1.  **Data Collection & Pre-processing:**
    * Historical data was gathered and consolidated in Google Sheets.
    * **Date Alignment:** Ensured all time series data were correctly aligned by date.
    * **Missing Value Imputation:** Gaps in VIX data (due to non-trading days) were filled using a forward-filling (Last Observation Carried Forward) method.
    * **Feature Engineering:**
        * `Daily Log Returns for Nifty` were calculated.
        * Lagged variables (e.g., `Repo Rate %`, `CPI`, `Nifty Rolling Volatility`) were created to account for time-delayed effects.
    * **Data Cleaning:** Addressed non-numeric entries, hidden characters, and inconsistent formatting to ensure data integrity for statistical analysis.

2.  **Exploratory Data Analysis (EDA):**
    * Initial correlation analysis was performed to understand pairwise relationships between variables.

3.  **Model Development - Multiple Linear Regression (OLS):**
    * A multiple linear regression model was developed using `Nifty 20 Day Rolling Volatility` as the dependent variable.
    * Independent variables included `Nifty Close`, `VIX Close`, `Daily Log Returns for Nifty`, and `Nifty Rolling Volatility Lag1`. (Note: `Repo Rate %` and `CPI` were considered but excluded from the final model due to high missing values or lack of statistical significance in preliminary tests within the multi-variable context).
    * The model was implemented and run using statistical tools (e.g., XLMiner in Google Sheets or Python's `statsmodels` library).

4.  **Model Evaluation & Interpretation:**
    * **R-squared:** Assessed the proportion of variance explained by the model.
    * **F-statistic & P-value:** Determined the overall statistical significance of the model.
    * **Coefficients & P-values:** Interpreted the direction, magnitude, and statistical significance of individual predictors.
    * **Residual Analysis:** Examined residual plots to check model assumptions (e.g., normality, homoscedasticity, autocorrelation).

5.  **Visualization & Reporting:**
    * An interactive dashboard was created in Tableau to present:
        * Actual vs. Predicted Nifty Rolling Volatility.
        * Residuals plot for model diagnostics.
        * Scatter plots illustrating relationships between volatility and key independent variables.
        * A summary table of regression coefficients and their statistical significance.

## Key Findings

The final multiple linear regression model achieved a high explanatory power, with an **Adjusted R-squared of approximately 0.895**. The model's overall significance (p-value < 0.001) confirms its statistical validity.

Key insights derived from the model include:

* **Strong Volatility Persistence:** `Nifty_Rolling_Vol_20D_Lag1` (lagged volatility) emerged as the most dominant and highly significant predictor, indicating that past volatility levels are a crucial determinant of current volatility.
* **VIX as a Key Indicator:** `VIX Close` showed a statistically significant positive relationship with Nifty Rolling Volatility, aligning with its role as a market "fear gauge."
* **Impact of Log Returns:** `Daily Log Returns for Nifty` also exhibited a statistically significant positive impact on volatility.
* **Limited Direct Impact of Nifty Close:** While `Nifty Close` showed an inverse relationship in simple correlation, its individual coefficient was not statistically significant in the multi-variable model, suggesting its influence is largely captured by other highly correlated variables (like lagged volatility and VIX).
* **Model Limitations:** The linear model, while robust for general trends, showed limitations in accurately predicting extreme volatility spikes, suggesting the presence of non-linear dynamics or uncaptured shock factors.

## How to Explore the Project

1.  **Data:** The `finall - combined.csv` file contains the raw and pre-processed data used for this analysis.
2.  **Google Sheet:** (If applicable, link to a public view-only version of your Google Sheet here if you want to share the live data/calculations).
3.  **Tableau Dashboard:** (If published to Tableau Public, provide the link here).

## Future Work

* **Advanced Time-Series Models:** Explore GARCH (Generalized Autoregressive Conditional Heteroskedasticity) models or other non-linear time-series techniques better suited for volatility forecasting.
* **Feature Engineering:** Investigate additional lagged variables, moving averages, or interaction terms.
* **Macroeconomic Deep Dive:** Integrate more granular or different macroeconomic indicators (e.g., inflation expectations, global market sentiment, bond yields).
* **Out-of-Sample Forecasting:** Develop and test the model's predictive power on unseen data.

---
