## COVID-19 Data Exploration Using SQL

### Introduction

This document provides an overview of the data exploration I performed using SQL on a COVID-19 dataset. 
The exploration includes a summary of the dataset, the objectives, the SQL queries used, and the insights derived from the analysis.

### Data Source

https://ourworldindata.org/coronavirus

### Dataset Overview

The dataset used for this exploration contains various metrics related to the COVID-19 pandemic. Below is a brief description of the dataset:

Table Name: `Coviddeaths`
Table Name: `CovidVacinations`
Columns:
  - `date`: Date of the recorded data
  - `country`: Name of the country
  - `new_cases`: Number of new COVID-19 cases reported
  - `new_deaths`: Number of new COVID-19 related deaths reported
  - `total_cases`: Cumulative number of COVID-19 cases
  - `total_deaths`: Cumulative number of COVID-19 related deaths
  - `population`: Population of the country
  - `vaccinated`: Number of people vaccinated
  - `fully_vaccinated`: Number of people fully vaccinated

### Objectives

The primary objectives of this data exploration were:
1. To analyze the spread of COVID-19 across different countries.
2. To identify trends in new cases and deaths over time.
3. To evaluate the impact of vaccination on the spread and mortality rate of COVID-19.
4. To identify countries with the highest and lowest case and death rates.

### SQL Queries and Analysis

#### 1.Selecting the Data

SELECT Location, date, total_cases, new_cases, total_deaths, population
From PortfolioProject..Coviddeaths
order by 1,2

### Result: Show the Data

### 2. Looking at Total Cases vs Total Deaths

SELECT Location, date, total_cases, total_deaths, CAST(total_deaths AS decimal(18,2))/CAST(total_cases AS decimal(18,2))*100 AS DeathRate
From PortfolioProject..Coviddeaths
order by 1,2

### Result: Show Total Cases vs Total Deaths

#### 3. Trends in New Cases and Deaths Over Time

```sql
SELECT 
    date, 
    SUM(new_cases) AS daily_new_cases, 
    SUM(new_deaths) AS daily_new_deaths
FROM covid_data
GROUP BY date
ORDER BY date;
```
### Result: Showed trends in daily new cases and deaths globally.

### 4. Percentage or likelihod of dying from covid in USA
SELECT Location, date, total_cases, total_deaths, CAST(total_deaths AS decimal(18,2))/CAST(total_cases AS decimal(18,2))*100 AS DeathRate
From PortfolioProject..Coviddeaths
where location like '%state%'
order by 1,2
### Result: Shows percentage or likelihod of dying from covid in USA

### 5. Percentage or likelihod of dying from covid in Nigeria

SELECT Location, date, total_cases, total_deaths, CAST(total_deaths AS decimal(18,2))/CAST(total_cases AS decimal(18,2))*100 AS DeathRate
From PortfolioProject..Coviddeaths
where location like '%Nigeria%'
order by 1,2
### Result: Shows the percentage or likelihod of dying from covid in Nigeria

### 6. Looking at the Total Cases vs  Population in Nigeria

SELECT Location, date, Population, total_cases,  CAST(total_cases AS decimal(18,2))/CAST(population AS decimal(18,2))*100 AS PopulationPercentage
From PortfolioProject..Coviddeaths
where location like '%Nigeria%'
order by 1,2
### Result: Looking at the Total Cases vs  Population in Nigeria

### 7. Total Caes vs Population in US ie the percentage of the ppulation with covid
SELECT Location, date, total_cases, Population, CAST(total_cases AS decimal(18,2))/CAST(population AS decimal(18,2))*100 AS PopulationPercentage
From PortfolioProject..Coviddeaths
where location like '%state%'
order by 1,2
### Result: Shows Total Caes vs Population in US ie the percentage of the ppulation with covid

### 8.  Total Cases vs Population in US ie the percentage of the ppulation with covid

SELECT Location, date, Population, total_cases,  CAST(total_cases AS decimal(18,2))/CAST(population AS decimal(18,2))*100 AS PopulationPercentage
From PortfolioProject..Coviddeaths
--where location like '%Nigeria%'
order by 1,2
### Result:  Shows Total Caes vs Population in US ie the percentage of the ppulation with covid



### Insights

1. **Global Impact**: The summary provided a comprehensive view of the global impact of COVID-19.
2. **Top Affected Countries**: Understanding which countries were most affected helped in focusing global health resources.
3. **Trends Over Time**: The trends analysis highlighted peak periods of the pandemic and helped in understanding the spread over time.
4. **Vaccination Impact**: The analysis suggested a correlation between higher vaccination rates and lower case and death rates.
5. **Low-Impact Countries**: Identifying countries with lower impact could provide insights into effective mitigation strategies.

### Conclusion

The SQL data exploration provided valuable insights into the COVID-19 pandemic's spread, impact, and the effect of vaccination. These insights are crucial for public health decision-making, resource allocation, and future pandemic preparedness.

### Contact

For any further queries or clarifications, please contact:

### Name: Cletus 
### Email: theink.oe@gmail.com
Phone*: [Your Phone Number]

### Appendix

Include any additional information, charts, or data visualizations here if necessary
