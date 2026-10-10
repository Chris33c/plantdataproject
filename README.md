# Plant Health Sensor Data Analysis

Exploratory data analysis of plant sensor readings using Python and pandas. The goal was to find which soil, nutrient, and environmental factors relate to plant health, and to test whether any of those relationships could predict chlorophyll content.

## Dataset
- **Source:** [Plant Health Data on Kaggle](https://www.kaggle.com/datasets/ziya07/plant-health-data) (I do not own this data)
- **Size:** 1,200 readings from 10 plants, taken every 6 hours from October 3 to November 2, 2024
- **Fields:** soil moisture, soil and ambient temperature, humidity, light intensity, soil pH, nitrogen, phosphorus, potassium, chlorophyll content, electrochemical signal, and plant health status (Healthy, Moderate Stress, High Stress)

## Questions
1. Which measurements are related to each other?
2. Can soil conditions predict chlorophyll content, a key indicator of plant health?
3. How do nutrient and temperature levels change over the 30-day period?

## Approach
1. **Data quality checks:** confirmed there were no missing values, reviewed data types and summary statistics, and removed duplicates.
2. **Aggregation:** grouped the 1,200 readings by plant and averaged them to compare the 10 plants side by side.
3. **Correlation analysis:** built correlation heatmaps (Seaborn) for all variables, then separately for temperature/environment and nutrient groups.
4. **Regression test:** fit a linear regression (scikit-learn) of chlorophyll content on soil pH using a random sample of 100 readings.
5. **Time series:** converted timestamps to datetime, resampled weekly, and charted nutrient and temperature trends (Matplotlib).

## Key Findings
- Across plant averages, **soil pH and chlorophyll content showed a correlation of about 0.6**, the strongest relationship among the nutrient variables.
- That relationship **did not hold up at the level of individual readings**. The regression line fit the sampled data poorly. A pattern that appears in averages across only 10 plants isn't strong enough to predict a single reading.
- Over the 30 days, **soil and ambient temperature tended to move in opposite directions** week to week, but the dataset is too small to call this a reliable trend.
- Health status was split across **500 High Stress, 401 Moderate Stress, and 299 Healthy** readings.

![Correlation heatmap](images/correlation_heatmap.png)
![Weekly temperature trend](images/temperature_trend.png)

## What I'd Do Next
- Use classification models (for example, logistic regression or a decision tree) to predict health status directly.
- Gather more plants and a longer time window to test whether the pH–chlorophyll relationship holds.

## Tools
Python · pandas · Seaborn · Matplotlib · scikit-learn · Jupyter Notebook

## How to Run
1. Clone this repository.
2. Install the requirements: `pip install pandas seaborn matplotlib scikit-learn jupyter`
3. Open `PlantHealthData.ipynb` in Jupyter and run all cells.
