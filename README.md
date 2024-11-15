# qld-nem-analysis
## Overview
This project explores electricity demand patterns and forecasting accuracy in Queensland, Australia, focusing on three research questions:

1) Demand Patterns and Characteristics: Identifying seasonal and intraday trends, relationships with weather, interconnector flows, and renewable energy (rooftop solar) generation.
2) Factors Associated with Demand Fluctuations: Investigating variables influencing electricity demand using predictive models (XGBoost, LightGBM, Random Forest).
3) Demand Spikes and Forecast Accuracy: Evaluating AEMO's forecast accuracy and analysing factors linked to demand 'exceedances' with logit and LightGBM classifiers.

The findings aim to support energy market stakeholders, including the market operator (AEMO), policymakers, practitioners and researchers. AEMO's forecasting team's budget for 2024/25 is $210 million.

This repository contains the code and  key results of the project.

### Please note, due to university restrictions, the datasets and written report cannot be published in the repository (only the code)

## Data & Methods
### Data Sources
- Original data sources are listed below. Most spanned January 2022 - June 2024, whilst the Interconnector flow data only spanned March 2023 - June 2024.
1) Brisbane weather data, including temperature, wind and dew point
2) Interconnector flow data, measuring energy flows between states (QLD and NSW)
3) Actual demand and AEMO's forecast demand, with three levels: probability of exceedance (POE) 10%, 50% and 90%
4) Electricity price, by state
5) Rooftop solar generation levels

### Pre-processing
- Filled missing values (e.g., with mean of prior and following observation to preserve temporal impacts)
- Derived temporal and calendar features (public holiday, day of week, time of day, day of year, month), temporal demand indicators (lagged features, moving averages, exponential moving averages)
- Aggregation to hourly and daily timeframes for analysis

### Analysis Techniques
  1) Descriptive analysis including correlation matrices, seasonal plots, summary statistics, etc.
  2) Predictive analysis used 3 tree-based models (XGBoost, LightGBM, Random Forest)
  3) Classifiers built using Binary Logistic Regression and LightGBM

## Findings
1) Seasonal and Demand Trends: QLD’s energy demand peaks in summer and dips in spring, with increased interconnector flows during high-demand periods. Price is highly volatile and appears to be impacted by factors beyond demand.
2) Associated Demand Factors: Demand levels correlate with temperature, rooftop solar generation, dew point, interconnector flows, seasonality and calendar effects. Lagged features and temporal demand indicators improved model accuracy, reflected in the tree-based model feature importances.
3) Forecast and Demand Spike Analysis: Demand exceedances in QLD are significantly more common during off-peak periods, with net interconnector flows, hours 8am - 5pm, and months April-December found as significant with positive odds ratios.

## Key Recommendations
1) AEMO should investigate forecasts for off-peak periods, especially the middle of the day (8am - 5pm) and mid-year (April - September) periods.
2) Future research should integrate additional weather variables (e.g., rainfall) and renewable energy sources such as wind power, hydro, etc.
3) More granular and longitudinal data may improve the predictive models, such as half-hourly interval data (consistent with AEMO's intervals), and longer timeframes may offer richer insights.
