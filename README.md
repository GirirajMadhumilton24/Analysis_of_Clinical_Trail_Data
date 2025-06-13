# ANALYSIS OF CLINICAL TRAIL DATA

## Overview
This project analyzes clinical trial data to uncover important trends and patterns in medical research activities. Using SQL on the Databricks platform, the analysis explores trial types, studied conditions, trial durations, and the focus on diabetes-related clinical studies over time. The insights help researchers, policymakers, and healthcare stakeholders understand evolving research priorities and the clinical trial landscape.

---

## Project Objectives
- Load and preprocess clinical trial dataset from CSV.
- Clean and transform raw data for analysis.
- Analyze frequency distribution of clinical trial types.
- Identify the most commonly studied medical conditions.
- Calculate average clinical trial duration.
- Track diabetes-related clinical trial trends over the years.

---

## Data Loading and Preparation
1. **Dataset**: `Clinicaltrial_16012025.csv` loaded from Databricks FileStore.
2. **Initial Steps**:
   - Verified file availability in `/FileStore/tables/`.
   - Loaded CSV into Spark DataFrame with options to handle headers, quotes, and multiline records.
   - Displayed and inspected columns and data structure.
3. **Column Renaming**: Removed spaces in column names for ease of querying, e.g., `NCT Number` → `NCT_Number`.
4. **Temporary View**: Created a temporary SQL view `clinical_trials` for convenient querying using Spark SQL.

---

## Data Cleaning and Transformation
- **Schema Overview**: Explored data types and nullability to understand dataset structure.
- **Handling NULLs**:
  - Replaced `NULL` values in `Study_Type` with `'UNKNOWN'`.
  - Converted `Conditions` string column into an array `Conditions_List` by splitting on `|` and `;`.
- **Final Cleaned Table**: Created `clinical_trials_cleaned_final` with cleaned and structured data for analysis.

---

## Analysis Summary

### 1. Clinical Trial Types Frequency
- Grouped trials by `Cleaned_Study_Type` to count occurrences.
- **Result**: Interventional trials are the most common, followed by observational studies.
- Visualization: Bar chart for frequency distribution of study types.

### 2. Top Medical Conditions Studied
- Exploded the `Conditions_List` array to count individual conditions.
- Identified top 10 frequently studied conditions such as Healthy, Breast Cancer, and Obesity.
- Visualization: Bar chart representing condition frequencies.

### 3. Average Clinical Trial Duration
- Calculated average trial length (in months) using `Start_Date` and `Completion_Date`.
- **Result**: Trials last on average about 35 months (~3 years).

### 4. Trends in Diabetes-Related Clinical Trials
- Filtered completed trials mentioning 'diabetes' in conditions.
- Grouped by completion year to track the number of diabetes trials annually.
- **Findings**: Steady increase in diabetes trials peaking around 2010, followed by fluctuations.
- Visualization: Line graph illustrating diabetes trial trends from 1995 to 2024.

---

## Conclusion
This analysis offers key insights into the clinical trial landscape:
- Interventional trials dominate research efforts.
- Cancer, obesity, and cardiovascular diseases are heavily studied conditions.
- Clinical trials typically last about 3 years.
- Diabetes research shows notable growth, with a peak in trial activity around 2010.
  
These findings provide valuable information for healthcare stakeholders to identify research priorities, allocate resources, and inform policy decisions.

---

## Tools and Technologies
- Databricks platform with Apache Spark SQL.
- SQL queries for data cleaning, transformation, and analysis.
- Databricks visualization UI for charts and graphs.

---

## How to Use
1. Upload the clinical trial CSV file to Databricks FileStore.
2. Execute the SQL and Python commands sequentially to load, clean, and analyze the data.
3. Use the Databricks visualization tools to generate charts for deeper insight.

---

