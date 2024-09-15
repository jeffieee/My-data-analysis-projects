
# MPOX Data Exploration Project

## Project Overview
This project explores two datasets: one related to global Mpox cases and another related to global Mpox deaths. The primary goal is to perform data exploration and analysis using MySQL to uncover insights about the progression of the pandemic.

## Dataset Information
### 1. data_tbl
- **location**: Country or region
- **date**: Date of the reported cases
- **cases_daily**: Daily new cases
- **deaths_daily**: Daily new deaths
- **cases_perweek**: 7-day moving average of new cases
- **deaths_perweek**: 7-day moving average of new deaths
- **total_cases**: Cumulative total cases
- **total_deaths**: Cumulative total deaths


## Exploratory Data Analysis (EDA)

### 1. Data Cleaning
- Check for missing or null values in both tables
- Remove any negative or invalid values for cases or deaths
```sql
-- Check for missing values in the cases table
SELECT * 
FROM data_tbl 
WHERE (cases_daily IS NULL OR cases_weekly IS NULL)
   OR (deaths_daily IS NULL OR deaths_weekly IS NULL)
   OR (total_cases IS NULL OR total_deaths IS NULL);


-- Check for negative or suspicious values in cases or deaths
SELECT * 
FROM data_tbl 
WHERE (cases_daily < 0 OR cases_weekly < 0)
   OR (deaths_daily < 0 OR deaths_weekly < 0)
   OR (total_cases < 0 OR total_deaths < 0);

```

### 2. Descriptive Statistics
- Calculate total cases and deaths globally
- Compute daily average cases and deaths
- Find the maximum and minimum number of new cases and deaths in a day
```sql
-- Total cases and deaths as of Sep 04, 2024
SELECT date, total_cases, total_deaths
FROM data_tbl
WHERE date = '2024-09-04' and location = 'World';

-- Average daily cases
SELECT AVG(cases_daily) AS avg_daily_cases, AVG(deaths_dai) AS avg_daily_deaths
FROM data_tbl;

-- Average weekly cases
SELECT AVG(cases_weekly*7) AS avg_weekly_cases, AVG(deaths_week*7) AS avg_weekly_deaths
FROM data_tbl;

-- Maximum daily cases and deaths
SELECT MAX(cases_daily) AS max_cases_daily,
MAX(deaths_dai) AS max_deaths _day
FROM data_tbl;

-- Maximum weekly cases and deaths
SELECT MAX(cases_weekly*7) AS max_cases_weekly,
MAX(deaths_week*7) AS max_deaths_week
FROM data_tbl;
```

### 3. Trend Analysis
- Track the monthly progression of cases and deaths
- Compare weekly cases and deaths to raw data to identify trends
```sql
-- Monthly total cases and deaths
SELECT DATE_FORMAT(date, '%Y-%m') AS month, SUM(cases_daily) AS monthly_cases, SUM(deaths_dai) AS monthly_deaths
FROM data_tbl
GROUP BY month
ORDER BY month;

-- Smoothed cases vs actual new cases over time
SELECT date, cases_daily, cases_weekly FROM data_tbl ORDER BY date;
```

### 4. Case Fatality Rate (CFR)
- Calculate the Case Fatality Rate (CFR)
```sql

-- Case Fatality Rate (CFR)
SELECT 
    location, 
    (SUM(deaths_daily) / SUM(cases_daily)) * 100 AS case_fatality_rate
FROM data_tbl
WHERE location = 'World'
GROUP BY location;
    
```

### 5. Geographical Analysis
- Identify top 10 countries with the most cases and deaths
- Compare Case Fatality Rates between countries
```sql
-- Top 5 countries with the highest number of cases and deaths
SELECT location, total_cases, total_deaths
FROM data_tbl
WHERE date >= '2024-08-01' AND date <= '2024-09-04'
  AND location NOT IN ('World','Africa', 'Antarctica', 'Asia', 'Europe', 'North America', 'Australia', 'South America')
GROUP BY location
ORDER BY total_cases DESC
LIMIT 5;

-- Top 5 countries with the highest number of deaths
SELECT location, total_deaths
FROM data_tbl
WHERE date >= '2024-08-01' AND date <= '2024-09-04'
  AND location NOT IN ('World','Africa', 'Antarctica', 'Asia', 'Europe', 'North America', 'Australia', 'South America')
GROUP BY location
ORDER BY total_deaths DESC
LIMIT 5;


## Visualization
- Line charts for new cases and new deaths over time
- Heatmaps for cases and deaths geographically
- Bar charts for top countries with the highest cases and deaths

## Summary of Key Insights
- **Total Cases Globally**: 103898
- **Total Deaths Globally**: 231
- **Top 10 Countries by Cases**: United States, Brazil, Democratic Republic of Congo, Colombia, Mexico
- **Top 10 Countries by Deaths**: United States, Mexico, Democratic Republic of Congo, Peru, Brazil
- **Global Case Fatality Rate (CFR): 0.22%


## Conclusion
This data exploration project provides insights into the progression of Mpox across the world, highlighting the hardest-hit regions, global trends, and potential correlations between cases and deaths.
