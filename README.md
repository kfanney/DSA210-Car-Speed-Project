Do Expensive Cars Really Speed More?
DSA 210 – Introduction to Data Science

Term: Fall 2025–2026
Student: Khalid Alfanney
SID: 33733

1. Motivation

There is a common assumption that drivers of expensive or luxury vehicles are more likely to speed and engage in riskier driving behavior. However, this belief is often based on perception rather than evidence.
This project aims to investigate the relationship between vehicle cost and speeding behavior using real-world U.S. traffic data.

By integrating traffic violation records with car price data, the analysis will test whether luxury brands such as BMW, Audi, or Mercedes-Benz are genuinely more represented in speeding incidents compared to mid-range or budget brands.

The study will follow the complete data-science process — from data collection and cleaning to exploratory analysis, hypothesis testing, and simple predictive modeling.

2. Project Overview
Stage	Description
Data Collection	Obtain and combine public datasets on traffic violations and car prices.
Data Cleaning	Standardize brand names, remove duplicates, and handle missing or inconsistent values.
Exploratory Data Analysis	Analyze violation frequency by brand, type, and price tier.
Statistical Testing	Test whether car cost significantly influences speeding likelihood.
Machine Learning	Build a basic predictive model for speeding based on brand and contextual factors.
Visualization	Present findings through clear visualizations and summary tables.
3. Data Sources
Traffic Violations Dataset (Primary)

Title: Traffic Violations – Montgomery County, Maryland (USA)

Source: Data.gov – Traffic Violations

Size: Approximately 800 MB (over one million records)

Fields Used: Date, time, make, violation type, vehicle type, location, year.

Purpose: Identify speeding-related incidents and measure how frequently different brands appear in these records.

Car Price Dataset (Secondary / Enrichment)

Title: U.S. Sales Cars Dataset

Source: Kaggle – US Sales Cars Dataset (2024)

Size: Approximately 200 MB (over 400,000 listings)

Fields Used: Make, model, year, price.

Purpose: Calculate average price by brand and classify vehicles into price tiers (Budget, Mid-Range, Luxury).

Join Key: Car brand (“Make”).

Note: The car-price dataset is used to enrich the violation data by defining brand-level economic categories. Since brand price rankings are relatively stable over time, it is acceptable to use current price data with violation records from previous years.

4. Analysis Plan
Step 1 – Data Preparation

Select relevant columns.

Filter records to include only speeding-related violations.

Standardize brand names across both datasets.

Remove missing or invalid entries.

Step 2 – Exploratory Analysis

Count speeding incidents by brand and price tier.

Calculate the proportion of speeding violations within each tier.

Visualize distributions using bar charts and boxplots.

Step 3 – Statistical Testing

H₀ (Null Hypothesis): Vehicle price tier has no relationship with speeding frequency.

H₁ (Alternative Hypothesis): Luxury brands have a higher proportion of speeding violations.

Use chi-square or ANOVA tests to evaluate significance.

Step 4 – Predictive Modeling

Train a simple classification model (e.g., Logistic Regression or Random Forest).

Predict the likelihood of a speeding violation using brand tier, time of day, and vehicle type as features.

Evaluate model accuracy and interpret key predictors.

Step 5 – Visualization and Reporting

Present summary statistics and key graphs (violation counts, brand comparisons, feature importance).

Interpret results to address the main question: Do expensive cars really speed more?

5. Tools and Environment
Category	Tools
Programming Language	Python 3.x
Libraries	pandas, numpy, matplotlib, seaborn, scikit-learn, scipy
Development Environment	Jupyter Notebook or VS Code
Version Control	Git + GitHub
6. Data Compatibility and Justification

The traffic-violation dataset contains multiple years of records, while the car-price dataset represents a recent snapshot of U.S. vehicle prices.
Because price differences between brands remain relatively constant across years, the integration of these datasets is appropriate.
Brand-level price tiers are used as a proxy for vehicle value, allowing the study to focus on behavioral patterns rather than precise economic fluctuations.

7. Summary

Main Dataset: Traffic Violations (Maryland, Data.gov)

Enrichment Dataset: U.S. Sales Cars Dataset (Kaggle)

Objective: Determine whether higher-priced vehicle brands are more likely to be involved in speeding violations.

Outcome: Apply data-science methods to test a social perception using real-world data.
