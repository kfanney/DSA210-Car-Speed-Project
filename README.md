# Do Expensive Cars Really Speed More?

### DSA 210 Project

**Term:** Fall 2025–2026
**Student:** Khalid Alfanney
**SID:** 33733

---

## 1. Motivation

There is a long-standing stereotype that drivers of high-priced vehicles, especially BMW, Audi, and Mercedes-Benz, are more aggressive and prone to speeding. News reports and public discussions in the United States often highlight these brands when incidents of reckless driving are reported. For instance, outlets such as *The Washington Post* and *Forbes* have published stories discussing the behavior of luxury-car owners on the road, reinforcing the perception that expensive cars are driven faster and more dangerously. However, whether this belief reflects actual behavior or simply a popular bias remains unclear.

This project aims to examine that question using real-world data. By analyzing U.S. traffic violation records and comparing them with car price data, the study seeks to determine whether expensive cars are truly more likely to be involved in speeding violations, or if the stereotype exaggerates their role.

Because mid-range vehicles are far more common than luxury cars, the project will normalize violation counts by the total number of vehicles of each brand or price class. This adjustment ensures that comparisons reflect *rates* of violations rather than raw counts, providing a fair and meaningful measure of driving behavior across price tiers.

The study follows the full data-science pipeline: collecting and cleaning data, conducting exploratory analysis, visualizing patterns, and applying statistical and machine-learning techniques to evaluate whether vehicle price can predict speeding behavior.

---

## 2. Project Overview

| Stage                               | Description                                                                                       |
| ----------------------------------- | ------------------------------------------------------------------------------------------------- |
| **Data Collection**                 | Gather public U.S. datasets on traffic violations and car prices.                                 |
| **Data Cleaning**                   | Filter speeding-related incidents, normalize brand names, remove missing or inconsistent records. |
| **Exploratory Data Analysis (EDA)** | Study speeding frequency by car make, type, and value tier.                                       |
| **Statistical Analysis**            | Test whether car cost correlates with speeding likelihood.                                        |
| **Machine Learning**                | Build models predicting speeding probability based on brand and contextual features.              |
| **Visualization & Reporting**       | Communicate insights through clear charts and dashboards.                                         |

---

## 3. Data Sources

### Traffic Violations Dataset (Main)

* **Title:** Traffic Violations – Montgomery County, Maryland (USA)
* **Source:** [Data.gov – Traffic Violations](https://catalog.data.gov/dataset/traffic-violations)
* **Size:** ≈ 800 MB (>1 million records)
* **Focused Fields:** `Date Of`, `Time Of`, `Make`, `Violation`, `Charge`, `VehicleType`, `Latitude`, `Longitude`, `Year`
* **Purpose:** Identify speeding incidents and their associated car brands to measure brand-level speeding behavior

### Car Price Dataset (Enrichment)

* **Title:** U.S. Sales Cars Dataset
* **Source:** [Kaggle – US Sales Cars Dataset (2024)](https://www.kaggle.com/datasets/juanmerinobermejo/us-sales-cars-dataset)
* **Size:** ≈ 200 MB (>400,000 listings)
* **Focused Fields:** `make`, `price`, `model`, `year`
* **Purpose:** Compute average brand-level prices and classify vehicles into **price tiers** (*Budget / Mid / Luxury*)
* **Join Key:** Car brand (`Make`)

### Data Integration Plan

1. **Clean** and standardize brand names in both datasets (e.g., “B.M.W.” → “BMW”).
2. **Aggregate** Kaggle data to obtain average price per brand.
3. **Categorize** brands into three tiers: Budget (< $30 k), Mid ($30–50 k), Luxury (> $50 k).
4. **Merge** tier data with traffic-violation records using `Make`.
5. **Normalize** violation counts by brand frequency (tickets per thousand registered vehicles).
6. **Analyze** speeding frequency and probability across tiers.

*Note:* The price dataset is used as a **static enrichment layer**, not a time-series match. Brand-level price hierarchies remain stable over time, so temporal differences do not affect the validity of this behavioral analysis.

---

## 4. Analysis Plan

### Step 1 – Data Cleaning

* Select relevant columns only.
* Filter rows with `Violation` containing “SPEED”.
* Drop missing or invalid entries.
* Normalize brand names for consistency.

### Step 2 – EDA

* Count speeding violations per brand.
* Calculate rates of violations per brand or price tier.
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
* Predict `is_speeding` using features such as price tier, brand, vehicle type, and time of day.
* Evaluate using accuracy, precision, recall, F1, and ROC-AUC.
* Interpret **feature importance**.

### Step 5 – Visualization and Storytelling

* Present key findings using Matplotlib and Seaborn:

  * Speeding distribution by tier and brand
  * Time-of-day patterns
  * Predictive feature importance
* Summarize results in a clear, evidence-based narrative.

---

## 5. Tools & Environment

| Category            | Tools                                                        |
| ------------------- | ------------------------------------------------------------ |
| **Language**        | Python 3.x                                                   |
| **Libraries**       | pandas · numpy · matplotlib · seaborn · scikit-learn · scipy |
| **Environment**     | Jupyter Notebook / VS Code                                   |
| **Version Control** | Git + GitHub                                                 |

---

## 6. Expected Deliverables

* Cleaned and merged dataset (`violations_enriched.csv`)
* Jupyter notebooks for EDA, hypothesis testing, and modeling
* Visualizations
* Final report summarizing insights and limitations

---

## 7. Data Compatibility Justification

The traffic-violation dataset spans multiple years, while the car-price dataset provides a recent snapshot of brand-level vehicle values in the U.S.
Because relative brand prices remain stable across time, these datasets can be combined reliably.
Normalization by brand frequency ensures that results reflect proportional behavior rather than raw totals, providing a fair cross-brand comparison.

---

## Summary

**Main Dataset:** Traffic Violations (Maryland – Data.gov)
**Enrichment Dataset:** US Sales Cars Dataset (Kaggle)
**Objective:** Determine whether higher-priced vehicle brands are more frequently involved in speeding violations after normalization for brand frequency.
**Outcome:** Apply data-science methods to test a widely held social perception with real, normalized data.
