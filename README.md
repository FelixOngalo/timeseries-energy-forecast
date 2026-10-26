# Daily Energy Demand Forecasting in R

## Project Overview

This project develops and evaluates **daily energy demand forecasting models in R** using the `tsibble`, `fable`, and `feasts` frameworks.

The analysis begins with **STL decomposition** to examine the underlying trend, seasonal patterns, and remainder components of energy demand. Multiple forecasting approaches are then fitted and compared, including **NAIVE, SNAIVE, ETS, and ARIMA** models.

Model performance is evaluated on a **60-day holdout period**, providing an out-of-sample comparison of forecasting accuracy.

The complete analysis is presented as a reproducible **Quarto report**.

## Objectives

- Prepare daily energy demand data for time-series analysis.
- Represent the data using the `tsibble` framework.
- Explore trend and seasonality using STL decomposition.
- Develop baseline and statistical forecasting models.
- Compare NAIVE, SNAIVE, ETS, and ARIMA forecasts.
- Evaluate models using an unseen 60-day holdout period.
- Identify the most suitable forecasting approach based on predictive accuracy.
- Communicate results through a reproducible Quarto report.

## Methodology

### 1. Data Preparation

The energy demand dataset is converted into a **tsibble**, providing a structured framework for handling time-indexed observations in R.

The analysis checks:

- Date/time structure
- Observation frequency
- Missing values
- Trends
- Seasonal patterns
- Potential anomalies

### 2. Exploratory Time-Series Analysis

The historical demand series is visualised to identify patterns that may influence future energy consumption.

Particular attention is given to:

- Long-term trends
- Repeating seasonal behaviour
- Short-term fluctuations
- Changes in demand over time

### 3. STL Decomposition

**Seasonal-Trend decomposition using Loess (STL)** is used to separate the observed demand series into:

- Trend
- Seasonal component
- Remainder

This provides a clearer understanding of the structure of the series and helps inform the forecasting approach.

### 4. Train/Test Split

The historical data is divided into:

- **Training period:** Used to estimate the forecasting models.
- **60-day holdout period:** Completely withheld from model fitting and used for final evaluation.

Using a holdout period provides a realistic test of how the models perform when forecasting future observations.

### 5. Forecasting Models

Four forecasting approaches are compared.

#### NAIVE

The NAIVE model uses the most recent observation as the forecast for future periods.

It provides a simple benchmark against which more sophisticated models can be evaluated.

#### SNAIVE

The Seasonal NAIVE model uses the value from the corresponding previous seasonal period.

This provides a stronger baseline when the energy-demand series contains clear recurring seasonal patterns.

#### ETS

The **Error-Trend-Seasonal (ETS)** framework models the systematic components of the time series using exponential smoothing.

The model can capture combinations of:

- Error
- Trend
- Seasonality

#### ARIMA

**Autoregressive Integrated Moving Average (ARIMA)** models capture temporal dependence within the series and can model autocorrelation, differencing, and moving-average effects.

The model selection process is handled within the `fable` framework.

## Analytical Workflow

```text id="3v6w2k"
Daily Energy Demand
        ↓
Data Preparation
        ↓
tsibble
        ↓
Exploratory Analysis
        ↓
STL Decomposition
        ↓
Training / 60-Day Holdout Split
        ↓
┌────────┬────────┬────────┬────────┐
│ NAIVE  │ SNAIVE │  ETS   │ ARIMA  │
└────────┴────────┴────────┴────────┘
        ↓
Forecast Generation
        ↓
60-Day Holdout Evaluation
        ↓
Model Comparison
        ↓
Quarto Report
```

## Technologies Used

- **R**
- `tsibble`
- `fable`
- `feasts`
- `dplyr`
- `ggplot2`
- **Quarto**

## Model Evaluation

Forecast accuracy is assessed against the actual observations in the **60-day holdout period**.

Evaluation metrics may include:

- MAE — Mean Absolute Error
- RMSE — Root Mean Squared Error
- MAPE — Mean Absolute Percentage Error

The models are compared using the same holdout observations to ensure a consistent evaluation framework.

The preferred model is selected based on its performance on unseen data rather than its fit to the training period alone.

## Visualisation

The project uses `feasts` and `ggplot2` to visualise:

- Historical energy demand
- STL decomposition
- Forecasts from competing models
- Actual versus predicted demand
- Forecast accuracy comparisons

These visualisations help communicate both the structure of the time series and the differences in model performance.

## Project Structure

```text id="q7k1x9"
daily-energy-forecasting-r/
│
├── data/
│   └── energy_demand.csv
│
├── R/
│   ├── 01_data_preparation.R
│   ├── 02_time_series_exploration.R
│   ├── 03_stl_decomposition.R
│   ├── 04_forecasting_models.R
│   └── 05_model_evaluation.R
│
├── figures/
│   ├── demand_series.png
│   ├── stl_decomposition.png
│   ├── forecasts.png
│   └── model_comparison.png
│
├── results/
│   └── forecast_accuracy.csv
│
├── report/
│   └── energy_demand_forecasting.qmd
│
└── README.md
```

## Business Application

Accurate energy demand forecasting can support operational and planning decisions in energy-related environments.

Potential applications include:

- Energy supply planning
- Capacity management
- Resource allocation
- Demand-response planning
- Operational scheduling
- Energy procurement
- Infrastructure planning

The ability to compare simple benchmarks with more sophisticated statistical models is particularly important because a complex model is not necessarily better than a well-chosen baseline.

## Key Skills Demonstrated

This project demonstrates practical skills in:

- R programming
- Time-series analysis
- Time-series decomposition
- STL decomposition
- Forecasting
- Statistical modelling
- Model comparison
- Out-of-sample validation
- `tsibble`
- `fable`
- `feasts`
- Data visualisation
- Forecast accuracy evaluation
- Reproducible reporting with Quarto

## Reproducibility

To reproduce the analysis:

1. Install R and the required packages.
2. Install Quarto.
3. Place the energy demand dataset in the `data/` directory.
4. Run the R scripts in sequence.
5. Generate the forecasts for each model.
6. Evaluate the forecasts against the 60-day holdout period.
7. Render the Quarto report.

## Limitations

Forecast performance depends on the quality, frequency, and historical coverage of the energy-demand data.

The models in this project are primarily **univariate forecasting approaches**. They do not explicitly incorporate external predictors such as:

- Weather
- Temperature
- Electricity prices
- Holidays
- Economic activity
- Industrial production

These variables could potentially improve forecasting performance in a more advanced modelling pipeline.

## Future Improvements

Potential extensions include:

- Incorporating weather and temperature variables
- Developing dynamic regression models
- Adding holiday and calendar effects
- Testing more advanced forecasting methods
- Comparing forecast performance across different seasonal periods
- Building an automated forecasting pipeline
- Deploying forecasts through an interactive dashboard

## Conclusion

This project demonstrates an end-to-end approach to **daily energy demand forecasting in R**, combining time-series decomposition, statistical forecasting, and out-of-sample model evaluation.

By comparing NAIVE, SNAIVE, ETS, and ARIMA models on a common **60-day holdout period**, the project focuses on practical predictive performance rather than relying solely on in-sample model fit.

The resulting Quarto report provides a reproducible and interpretable record of the complete forecasting workflow.
