# Impact of Weather Severity on NYC Taxi Drivers' Earnings Potential

A geospatial and predictive analysis of how weather severity affects NYC Yellow Taxi drivers' earnings potential, built to give drivers evidence-based recommendations for working through adverse weather.

## Introduction
In this project, I joined NYC TLC Yellow Taxi trip records with NOAA weather station data, engineered a weather severity score and an earnings-potential metric (fare revenue per active hour), then ran geospatial and statistical analysis before building two predictive models (LASSO and Random Forest regression) to compare earnings potential across weather severity, pickup location, time of day, weekday and precipitation type.

## Data
- Six months of NYC Yellow Taxi trip records (Nov 2023–Apr 2024), cleaned from an initial ~19.8M rows down to **16.77M rows** after removing invalid fares, non-standard rate codes, and outlier trip durations/speeds
- NOAA hourly weather data from four NYC-area stations, matched to each trip's pickup hour via nearest-station mapping
- 80/20 train-test split by date to avoid information leakage

## Results
- Earnings potential varies sharply by borough — Manhattan and the Bronx cluster around $60–80/active hour, while parts of Queens and Staten Island reach $95–120/active hour
- High-severity weather doesn't uniformly help drivers: **57.2% of zones saw earnings increase, but 41.6% saw a decrease**, with the average effect slightly negative
- Weather's positive effect on earnings grows sharply later in the day — from a 1.9% increase in early morning to a **12.7% increase at night** under high severity
- Precipitation type matters more than severity alone: thunderstorms boosted earnings by 13.4%, while freezing rain cut them by 8.4% (likely due to hazardous, slow-driving conditions)
- Random Forest outperformed LASSO on all test metrics (MAE, RMSE, R²), showing the relationship between conditions and earnings is non-linear; pickup location and time of day were consistently the strongest predictors — stronger than weather itself

## Recommendations
The findings translate into two concrete, low-cost recommendations for drivers: prioritise avoiding zones with a history of earnings decline in severe weather rather than chasing the highest-earning zones, and consider extending shifts into night hours when high-severity weather is forecast. Both recommendations are actionable without changing a driver's existing schedule.

## Tech stack
PySpark (data processing, LASSO and Random Forest regression), Python, geospatial visualisation

## Repo structure
```
notebooks/       # PySpark analysis pipeline
report/          # Written report (PDF) with full figures and tables
requirements.txt
```

*Note: NOAA weather data is included in this repo. NYC TLC trip records are pulled directly from the [NYC TLC Trip Record Data page](https://www.nyc.gov/site/tlc/about/tlc-trip-record-data.page).*
