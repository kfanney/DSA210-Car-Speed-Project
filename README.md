# Do Expensive Cars Really Speed More?

### DSA 210 Project

**Term:** Fall 2025–2026   
**Student:** Khalid Alfanney  
**SID:** 33733

---

## 1️. Motivation

There is a common stereotype that drivers of luxury vehicles, especially brands like BMW, Audi, and Mercedes-Benz, are more aggressive on the road. People often claim they speed more, cut lanes, and act as if traffic rules do not apply to them. But is this actually true, or just a social bias that has been repeated over time?

This project aims to explore that question using real data. By analyzing U.S. traffic violation records and comparing them with car price data, the goal is to determine whether expensive cars are genuinely more likely to be involved in speeding incidents, or if luxury drivers have simply earned an unfair reputation.

To uncover the answer, I will apply the full data-science process: collecting and cleaning data, performing exploratory analysis, visualizing patterns, and experimenting with basic machine-learning models. The outcome will help clarify whether the belief that luxury cars speed more is supported by data or merely driven by perception.

---

## 2️. Project Overview

| Stage                               | Description                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Data Collection**                 | Gather public U.S. datasets on traffic violations and car prices.                                 |
| **Data Cleaning**                   | Filter speeding-related incidents, normalize brand names, remove missing or inconsistent records. |
| **Exploratory Data Analysis (EDA)** | Study speeding frequency by car make, type, and value tier.                                       |
| **Statistical Analysis**            | Test whether car cost correlates with speeding likelihood.                                        |
| **Machine Learning**                | Build models predicting speeding probability based on brand and contextual features.              |
| **Visualization & Reporting**       | Communicate insights through clear charts and dashboards.                                         |

---

## 3️. Data Sources

### Traffic Violations Dataset (Main)

* **Title:** Traffic Violations – Montgomery County, Maryland (USA)
* **Source:** [Data.gov – Traffic Violations](https://catalog.data.gov/dataset/traffic-violations)
* **Size:** ≈ 800 MB (>1 million records)
* **Focused Fields:** `Date Of`, `Time Of`, `Make`, `Violation`, `Charge`, `VehicleType`, `Latitude`, `Longitude`, `Year`.
* **Purpose:** Identify speeding incidents and their associated car brands to measure brand-level speeding behavior.

### Car Price Dataset (Enrichment)

* **Title:** U.S. Sales Cars Dataset
* **Source:** [Kaggle – US Sales Cars Dataset (2024)](https://www.kaggle.com/datasets/juanmerinobermejo/us-sales-cars-dataset)
* **Size:** ≈ 200 MB (>400 k listings)
* **Focused Fields:** `make`, `price`, `model`, `year`.
* **Purpose:** Compute average brand-level prices and classify vehicles into **price tiers** (*Budget / Mid / Luxury*).
* **Join Key:** Car brand (`Make`).

### Data Integration Plan

1. **Clean** and standardize brand names in both datasets (e.g., “B.M.W.” → “BMW”).
2. **Aggregate** Kaggle data to obtain average price per brand.
3. **Categorize** brands into three tiers: Budget (< $30 k), Mid ($30–50 k), Luxury (> $50 k).
4. **Merge** tier data with traffic-violation records using `Make`.
5. **Analyze** speeding frequency and probability across tiers.

*Note:* The price dataset is used as a **static enrichment layer**, not a time-series match. Brand-level price hierarchies remain stable across years, so temporal misalignment does not affect the validity of the behavioral analysis.

---

## 4️. Analysis Plan

### Step 1 – Data Cleaning

* Select relevant columns only.
* Filter rows with `Violation` containing “SPEED”.
* Drop missing or invalid entries.
* Normalize brand names for consistency.

### Step 2 – EDA

* Count speeding violations per brand.
* Calculate percentages of violations by price tier.
* Visualize with:

  * Bar charts (speeding counts per brand)
  * Boxplots (price tier vs speeding rate)
  * Heatmaps (correlations between features)

### Step 3 – Hypothesis Testing

* **H₀:** No relationship between vehicle price tier and speeding frequency.
* **H₁:** Luxury brands have a higher proportion of speeding violations.
* Apply chi-square or ANOVA tests; compute effect size (Cramér’s V).

### Step 4 – Machine Learning

* Build **classification models** (Logistic Regression / Random Forest).
* Predict `is_speeding` using features: price tier, brand, vehicle type, time of day.
* Evaluate using accuracy, precision, recall, F1, and ROC-AUC.
* Interpret **feature importance**.

### Step 5 – Visualization & Storytelling

* Create visuals in Matplotlib / Seaborn showing:

  * Speeding distribution by tier and brand.
  * Hour-of-day patterns for different price segments.
  * Predictive model feature importance.
* Summarize findings in a clear narrative.

---

## 5️. Tools & Environment

| Category            | Tools                                                        |
| ------------------- | ------------------------------------------------------------ |
| **Language**        | Python 3.x                                                   |
| **Libraries**       | pandas · numpy · matplotlib · seaborn · scikit-learn · scipy |
| **Environment**     | Jupyter Notebook / VS Code                                   |

---

## 6️. Expected Deliverables

* Cleaned and merged dataset (`violations_enriched.csv`)
* Jupyter Notebooks for EDA, hypothesis testing, and modeling
* Visualizations
* Final report summarizing insights and limitations

---

## 7. Data Compatibility Justification

The traffic-violation data spans multiple years, while the car-price dataset provides a recent snapshot of brand-level prices in the U.S.
Because brand-price hierarchies remain stable over time, these data can be integrated reliably for behavioral analysis.
This ensures the enrichment variable (“price tier”) accurately represents brand value rather than transient market conditions.

---
  
## Summary

**Main Dataset:** Traffic Violations (Maryland – Data.gov)  
**Enrichment Dataset:** US Sales Cars Dataset (Kaggle)  
**Objective:** Determine whether higher-priced vehicle brands are more frequently involved in speeding violations.  
**Outcome:** Apply data-science methods to test a social perception with real evidence.
