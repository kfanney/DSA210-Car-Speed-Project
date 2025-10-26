# Do Expensive Cars Really Speed More?

### 🧾 DSA 210 – Project
**Term:** Fall 2025–2026  
**Student:** Khalid Alfanney
**SID:** 33733

---

## 1. Motivation

There’s a common belief that luxury-car drivers are more aggressive on the road — that BMWs, Audis, and Mercedes-Benzs dominate speeding tickets and risky driving statistics.  
But is that actually true, or just a social stereotype?

This project aims to **investigate the relationship between vehicle cost and speeding behavior** using real-world traffic violation data.  
By combining **violation datasets** with **car price data**, I’ll explore whether expensive cars are genuinely involved in more speeding incidents — or if this perception is simply a myth amplified by media and anecdotes.

The goal is to apply the **entire data science pipeline** — from data collection and cleaning to statistical testing, visualization, and basic machine learning — to uncover behavioral patterns behind the wheel.

---

## 2. Project Overview

| Stage | Description |
|--------|--------------|
| **Data Collection** | Obtain public datasets on traffic violations and car prices. |
| **Data Cleaning** | Standardize brand names, remove duplicates, and handle missing fields. |
| **Exploratory Data Analysis (EDA)** | Examine violation frequency by car make, type, and price tier. |
| **Statistical Analysis** | Test correlation between car cost and violation severity/type. |
| **Machine Learning** | Predict the likelihood of a speeding violation using features such as price, brand, and time of day. |
| **Visualization & Reporting** | Build visual dashboards and interpret whether expensive cars truly speed more. |

---

## 3. Data Sources

### Traffic Violation Data
- **Dataset:** [Traffic Violations (Maryland, USA) – Kaggle](https://www.kaggle.com/datasets/awaiskaggler/traffic-violations-in-maryland)  
- **Alternative:** [UK Road Safety Data – data.gov.uk](https://data.gov.uk/dataset/road-safety-data)  
- **Fields:** Date, location, violation type (speeding, DUI, reckless driving), vehicle make/model, and environmental conditions.

### Car Price Data
- **Dataset:** [Used Cars Dataset – Kaggle](https://www.kaggle.com/datasets/austinreese/craigslist-carstrucks-data)  
- **Alternative:** [Vehicle Dataset from CarDekho – Kaggle](https://www.kaggle.com/datasets/nehalbirla/vehicle-dataset-from-cardekho)  
- **Fields:** Brand, model, year, mileage, price, fuel type, and transmission.

### Data Enrichment
- Merge both datasets using **car brand/model** as a key.  
- Categorize vehicles into **price tiers** (e.g., *Budget*, *Mid-Range*, *Luxury*).  
- Optionally enrich with **weather** or **road condition** data for additional context.

---

## 4. Analysis Plan

### Step 1 – Data Cleaning
- Normalize car brand names (e.g., “B.M.W.” → “BMW”).  
- Filter incomplete or irrelevant records.  
- Handle missing data with appropriate imputation.

### Step 2 – Exploratory Data Analysis
- Identify which brands appear most in traffic violations.  
- Compare average number of speeding incidents per price tier.  
- Visualize data through:
  - Histograms and pie charts (violation counts per brand)
  - Heatmaps (correlations)
  - Boxplots (violation severity vs. price range)

### Step 3 – Hypothesis Testing
- **Null Hypothesis (H₀):** There is no relationship between vehicle price and speeding frequency.  
- **Alternative (H₁):** Luxury vehicles are more likely to be involved in speeding violations.  
- Use chi-square or ANOVA tests depending on data characteristics.

### Step 4 – Machine Learning Model
- Build a **classification model** (e.g., Logistic Regression or Random Forest) to predict speeding likelihood based on:
  - Car price category  
  - Brand  
  - Violation context (time, weather, road type)
- Evaluate with accuracy, precision, recall, and confusion matrix.
- Interpret **feature importance** to see which factors drive risk.

### Step 5 – Visualization & Storytelling
- Create compelling graphs and dashboards using **Matplotlib** and **Seaborn**.  
- Present findings as a story:
  > “Do expensive cars speed more, or do people just notice them more?”

---

## 5. Tools & Environment

| Category | Tools |
|-----------|-------|
| **Language** | Python 3.x |
| **Libraries** | pandas, numpy, matplotlib, seaborn, scikit-learn, scipy |
| **Environment** | Jupyter Notebook or VS Code |
| **Version Control** | Git + GitHub |

---

## 6. Repository Structure

