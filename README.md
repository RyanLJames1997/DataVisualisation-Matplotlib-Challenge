# DataVisualisation-Matplotlib-Challenge

Module 05 Challenge: UWA/edx Data Analytics Bootcamp

Github repository at: [https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge.git](https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge.git)

## Introduction

## Scope

In this challenge, we are to apply the foundational learning of Matplotlib, and apply this to a real-world scenario and dataset.

### Background

You've just joined Pymaceuticals, Inc., a new pharmaceutical company that specializes in anti-cancer medications. Recently, it began screening for potential treatments for squamous cell carcinoma (SCC), a commonly occurring form of skin cancer.

As a senior data analyst at the company, you've been given access to the complete data from their most recent animal study. In this study, 249 mice who were identified with SCC tumors received treatment with a range of drug regimens. Over the course of 45 days, tumor development was observed and measured. The purpose of this study was to compare the performance of Pymaceuticals’ drug of interest, Capomulin, against the other treatment regimens.

### Goal

The overall goal of this analysis is to generate tables and figures needed for a well-structured technical report.
.
### Instructions

This assignment is broken down into the following tasks:

   ** (1) Prepare the data.
    (2) Generate summary statistics.
    (3) Create bar charts and pie charts.
    (4) Calculate quartiles, find outliers, and create a box plot.
    (5) Create a line plot and a scatter plot.
    (6) Calculate correlation and regression.
    (7) Submit your final analysis.**

### Repository Structure

The Jupyter notebook [`pymaceuticals.ipynb`](https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge/blob/main/Starter_Code/Pymaceuticals/pymaceuticals_starter.ipynb) is contained in the root directory

`Resources` directory contains the datasets: [`Mouse_metadata.csv`](https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge/blob/main/Starter_Code/Pymaceuticals/data/Mouse_metadata.csv) and [`Study_results.csv`](https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge/blob/main/Starter_Code/Pymaceuticals/data/Study_results.csv)

### Dataset

The dataset was generated by the team at **Mockaroo, LLC (2022)** realistc data generator.

## Approach

1. Understand the contents of each dataset:
    - [`Mouse_metadata.csv`](https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge/blob/main/Starter_Code/Pymaceuticals/data/Mouse_metadata.csv) contained `249` rows with columns: `['Mouse ID', 'Drug Regimen', 'Sex', 'Age_months', 'Weight (g)']`.
    - [`Study_results.csv`](https://github.com/RyanLJames1997/DataVisualisation-Matplotlib-Challenge/blob/main/Starter_Code/Pymaceuticals/data/Study_results.csv) contained `1893` rows with columns: `['Mouse ID', 'Timepoint', 'Tumor Volume (mm3)', 'Metastatic sites']`.
2. Merge the dataset, using `pd.merge()`, and identify duplicates, using Pandas `DataFrame.duplicated()`.
3. Remove mice with duplicated values, confirming the number by identifying unique `Mouse ID`, and create a cleaned DataFrame.

### Generate summary statistics
1. For each drug regimen, calculate the following statistcs: `mean`, `median`, `variance`, `standard deviation`, and `SEM` of the tumor volume.
2. Two methods that can be used:
    - Use `groupby()` for each statistic.
    - Use the aggregation method `agg()` using a single line of code.

### Create bar and pie charts
1. Create two bar charts using: Pandas `DataFrame.plot()` method, and Matplotlib's `pyplot` method.
    - Sort the values prior to plotting, with the highest number of observed timepoints first.
    - Add an appropriate title and labels to each plot.
2. Create two pie charts using: Pandas `DataFrame.plot()` method, and Matplotlib's `pyplot` method.
    - Sort the values prior to plotting to ensure the resulting plot matches the expected figure.
    - Add a label and annotate the percentage value in the correct pie slice.

### Calculate quartiles, find outliers, and create a box plot
1. Create a list of the four drug regimens of interest: `['Capomulin', 'Ramicane', 'Infubinol', 'Ceftamin']`.
2. Using a for-loop over the four treatments, isolate the data for each drug and append to the `tumor_data` list.
3. Within the for-loop, calculate the following:
    - Lower quartile, using `quantile(0.25)`
    - Upper quartile, using `quantile(0.75)`
    - Inter-quartile range (IQR), using `upper_quartile - lower_quartile`
    - Lower bounds, using `lower_quartile - (1.5*iqr)`
    - Upper bounds, using `upper_quartile + (1.5*iqr)`
4. Identify outliers using the calculated upper and lower bounds.
5. Display the IQR and outliers for each treatment group.

### Create a line and scatter plot
1. Line plot - Single mouse:
    - For a single mouse, isolate the `Tumor Volume (mm3)` and `Timepoint`.
    - Use the retrieved data to create a line plot.
2. Scatter plot - Capomulin regimen average tumor volume vs mouse weight:
    - For the `Capomulin` regimen, isolate `Mouse ID`, `Tumor Volume (mm3)`, and `Weight (g)`.
    - Use `groupby().mean()` over the retrieved data.
    - Use the derived data to create a scatter plot.

### Calculate correlation and regression
1. Correlation Coefficient
    - Use `st.pearsonr()` to calculate the correlation coefficient between the `groupby().mean()` DataFrame's `Weight (g)` and `Tumor Volume (mm3)`.
    - Print the result, rounded to 2 decimal places for readability.
2. Linear Regression Model
    - Use the `linregress()` function to calculate the regression attributes: `slope`, `intercept`, `rvalue`, `pvalue`, `stderr`.
    - Use the attributes to get the regression values using the slope equation: `x_values * slope + intercept`.
    - Overlay the regression line on the Capomulin regimen scatter plot.

## References
The statistics linear regression equation is derived from the **Bootcamp Week 5** and **Chat GPT**
