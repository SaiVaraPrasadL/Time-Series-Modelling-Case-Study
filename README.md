# Time Series Modelling Case Study

## Forecasting Daily Gas Prices Using ARMA and Prophet Models

**Student:** Sai Vara Prasad Lekkalapudi

**Student-id:** 23076885

**Module:** Advanced Research Topics in Data Science

**University:** University of Hertfordshire

---

## Project Overview

This project investigates the forecasting of daily gas prices using two different time-series forecasting approaches. The aim was to compare the performance of a traditional statistical model with a modern forecasting framework and determine which method produced more accurate predictions.

The analysis followed a structural forecasting workflow, including data preparation, exploratory analysis, stationarity assessment, model development, diagnostic testing, and future forecasting.

The two forecasting approaches evaluated were:

* **ARMA (Autoregressive Moving Average)** applied to a stationary differenced series.
* **Prophet**, a forecasting framework designed to model trend changes automatically.

Model performance was assessed using unseen test data to provide an objective comparison of forecasting accuracy.

---

## Dataset

The dataset contains daily gas price observations covering the period from January 2025 to June 2026.

### Dataset Summary

| Metric          | Value               |
| --------------- | ------------------- |
| Observations    | 500                 |
| Frequency       | Daily               |
| Period Covered  | Jan 2025 – Jun 2026 |
| Target Variable | Gas Price           |

The gas price series showed noticeable changes over time, making stationarity testing an important step before model development.

---

## Methodology

The analysis followed the following workflow:

1. Data loading and cleaning
2. Data quality assessment
3. Exploratory data analysis
4. Rolling mean and variance analysis
5. Stationarity testing using the Augmented Dickey-Fuller (ADF) test
6. ACF and PACF diagnostics
7. First-order differencing
8. ARMA model development and optimisation
9. Prophet model development and tuning
10. Forecast evaluation
11. Residual diagnostics
12. Twenty-four-month future forecasting

---

## ARMA Model Development

The original gas price series was found to be non-stationary. First-order differencing was therefore applied before model fitting.

A grid search across multiple combinations of p, d and q values was conducted using the Akaike Information Criterion (AIC) to identify the most appropriate model specification.

### Selected Model

**ARMA(5,8)** fitted to the first-differenced series.

Model diagnostics included:

* Residual analysis
* Residual ACF inspection
* Ljung-Box testing
* Forecast accuracy evaluation

---

## Prophet Model Development

Prophet was implemented as an alternative forecasting approach to provide a comparison against ARMA.

Several values of the `changepoint_prior_scale` parameter were evaluated to identify the configuration that produced the lowest forecasting error.

### Selected Configuration

**changepoint_prior_scale = 0.50**

This setting produced the strongest predictive performance among the tested Prophet configurations.

---

## Model Evaluation

Forecast accuracy was evaluated using:

* Mean Absolute Error (MAE)
* Root Mean Squared Error (RMSE)
* Mean Absolute Percentage Error (MAPE)

### Performance Comparison

| Model      | MAE   | RMSE  | MAPE (%) |
| ---------- | ----- | ----- | -------- |
| ARMA (5,8) | 7.18  | 8.36  | 8.88     |
| Prophet    | 14.88 | 15.70 | 18.75    |

---

## Key Findings

* The ARMA model produced lower forecasting errors across all evaluation metrics.
* Short-term price dynamics were captured more effectively by ARMA than Prophet.
* Prophet generated smoother forecasts but was less responsive to short-term fluctuations.
* Residual diagnostics indicated that the selected ARMA model adequately captured the main structure of the differenced series.
* Long-term forecasts suggested relatively stable gas price behaviour, although uncertainty increased considerably as the forecast horizon extended.

---

## Project Structure

```text
Time-Series-Modelling-Case-Study
│
├── gas_price_forecasting_final.ipynb
├── gas_price_2526.csv
├── Time_Series_Modelling_Case_Study_Report.pdf
│
├── figures/
│
└── tables/
```

## Technologies Used

The project was implemented in Python using:

* pandas
* numpy
* matplotlib
* statsmodels
* prophet
* scikit-learn

---

## Limitations

Several limitations should be considered when interpreting the results:

* The analysis was based on a relatively short historical period.
* Only historical gas prices were used as model inputs.
* External influences such as economic conditions, weather events, and geopolitical factors were not included.
* Long-term forecasts become increasingly uncertain as the prediction horizon increases.

---

## Future Improvements

Future work could extend the analysis by:

* Incorporating external explanatory variables.
* Exploring multivariate forecasting models.
* Evaluating SARIMA and machine learning approaches.
* Investigating hybrid forecasting frameworks.

---

## References

Akaike, H., 1974. *A new look at the statistical model identification*. IEEE Transactions on Automatic Control, 19(6), pp.716-723. Available at: https://doi.org/10.1109/TAC.1974.1100705

Box, G.E.P., Jenkins, G.M., Reinsel, G.C. and Ljung, G.M., 2015. *Time Series Analysis: Forecasting and Control*. 5th ed. Hoboken: Wiley.

Dickey, D.A. and Fuller, W.A., 1979. *Distribution of the estimators for autoregressive time series with a unit root*. Journal of the American Statistical Association, 74(366), pp.427-431. Available at: https://doi.org/10.1080/01621459.1979.10482531

Hyndman, R.J. and Athanasopoulos, G., 2021. *Forecasting: Principles and Practice*. 3rd ed. Melbourne: OTexts. Available at: https://otexts.com/fpp3/ [Accessed 21 June 2026].

Ljung, G.M. and Box, G.E.P., 1978. *On a measure of lack of fit in time series models*. Biometrika, 65(2), pp.297-303. Available at: https://doi.org/10.1093/biomet/65.2.297

Taylor, S.J. and Letham, B., 2018. *Forecasting at scale*. The American Statistician, 72(1), pp.37-45. Available at: https://doi.org/10.1080/00031305.2017.1380080


---

## Conclusion

This project demonstrates the importance of selecting forecasting methods that align with the characteristics of the data. For this dataset, the ARMA model provided substantially better forecasting performance than Prophet and produced the most accurate predictions during the testing period. The results highlight the value of careful stationarity assessment, model diagnostics, and objective evaluation when developing time-series forecasting solutions.
