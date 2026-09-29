# Urban Lifestyle Clustering & Segmentation

A data-driven machine learning project using **K-Means Clustering** to analyze and segment 300 global cities based on various livability and lifestyle metrics.

---

## 📌 Table of Contents

* [Project Overview](https://www.google.com/search?q=%23-project-overview)
* [Dataset Features](https://www.google.com/search?q=%23-dataset-features)
* [Project Workflow](https://www.google.com/search?q=%23-project-workflow)
* [Tech Stack & Dependencies](https://www.google.com/search?q=%23-tech-stack--dependencies)
* [How to Run](https://www.google.com/search?q=%23-how-to-run)
* [Results & Model Analysis](https://www.google.com/search?q=%23-results--model-analysis)

---

## 📖 Project Overview

This repository contains a complete pipeline for unsupervised learning applied to urban lifestyle statistics. The goal of the project is to group cities into distinct clusters based on economic, environmental, and infrastructure characteristics—such as average income, rent cost, air quality index, public transport score, and green space ratio.

---

## 📊 Dataset Features

The project reads data from `city_lifestyle_dataset.csv` containing **300 samples** with the following feature set:

| Feature Name | Description |
| --- | --- |
| `city_name` | Name of the city |
| `country` | Geographic region/continent (Asia, Europe, North America, South America, Africa, Oceania) |
| `population_density` | Density of people per square kilometer |
| `avg_income` | Average income level |
| `internet_penetration` | Percentage of internet accessibility (%) |
| `avg_rent` | Average cost of renting |
| `air_quality_index` | Air Quality Index (AQI) |
| `public_transport_score` | Public infrastructure quality score |
| `happiness_score` | Overall city happiness rating |
| `green_space_ratio` | Ratio of public green space |

---

## ⚙️ Project Workflow

1. **Data Loading & Preprocessing:**
* Checked for null/missing values (`df.isna().sum()`).
* Checked for duplicated rows (`df.duplicated().sum()`).
* Label/Ordinal encoding applied on categorical regions (`country`).
* Non-numeric identifier features (`city_name`, `country`) dropped prior to clustering.


2. **Feature Scaling:**
* Standardized numerical variables using `StandardScaler` to ensure uniform weighting across different metrics.


3. **Optimal K Selection (Elbow Method):**
* Evaluated **Within-Cluster Sum of Squares (WCSS) / Inertia** across cluster counts from $k=1$ to $k=10$.
* Selected **$k = 4$** as the optimal number of clusters based on the elbow plot.


4. **Clustering:**
* Trained the final K-Means model with $K=4$.
* Segmented the dataset and appended the predicted cluster labels back to the DataFrame (`df["Cluster"]`).



---

## 🛠️ Tech Stack & Dependencies

* **Python 3.x**
* **Pandas** — Data manipulation and analysis
* **Matplotlib** — Data visualization
* **Scikit-Learn (`sklearn`)** — Feature scaling (`StandardScaler`) and clustering (`KMeans`)

---

## 🚀 How to Run

2. **Install Required Packages:**
```bash
pip install pandas matplotlib scikit-learn

```


3. **Ensure Data Availability:**
Place the dataset file `city_lifestyle_dataset.csv` in the root directory.
4. **Execute the Jupyter Notebook / Script:**
Launch Jupyter Notebook or VS Code to run the `.ipynb` file:
```bash
jupyter notebook

```



---

## 📈 Results & Model Analysis

* **Optimal Number of Clusters:** 4
* **WCSS Progression Across Values of $K$:**

| $K$ | WCSS Value |
| --- | --- |
| 1 | 2400.00 |
| 2 | 1411.05 |
| 3 | 1036.59 |
| **4** | **890.43 (Elbow Point)** |
| 5 | 811.70 |
| 10 | 593.56 |

<img width="580" height="422" alt="image" src="https://github.com/user-attachments/assets/35c62d5a-e32e-49f2-bb7a-094af537a998" />

## Key Findings & Executive Summary

### 1. Socio-Economic Segmentation Analysis

The K-Means clustering algorithm ($K=4$) categorized 300 global cities into distinct socio-economic tiers based on livability metrics. Analyzing **Average Income** against **Happiness Score** highlights four clear urban personas:

* **Cluster 0 — High-Wealth Metropolises (Green):** Cities with high average monthly incomes ($>\$4,000$) and top-tier happiness scores ($>8.0$). These represent affluent, stable economies with well-funded public infrastructure.
* **Cluster 1 — Balanced Urban Tiers (Blue):** Cities with mid-to-high income ranges ($\$2,000 - \$3,500$) and strong satisfaction ratings ($6.5 - 8.0$), indicating solid economic stability and livability.
* **Cluster 2 — Emerging Markets (Purple):** Transitioning urban centers showing moderate income levels ($\$1,500 - \$3,000$) with varied livability scores ($4.5 - 6.5$).
* **Cluster 3 — Under-Resourced Regions (Yellow):** Cities with lower income thresholds ($<\$1,500$) strongly correlated with reduced happiness ratings ($<5.0$), highlighting regions requiring infrastructure and economic support.

---

### 2. Strategic & Business Value

* **Targeted Expansion:** Enterprise businesses can optimize market entry—deploying premium services in Cluster 0 while launching cost-effective offerings in Clusters 2 & 3.
* **Urban Policy & Resource Allocation:** Governments can benchmark low-performing city segments against top tiers to prioritize investments in healthcare, green space, and public transit.
* **Socio-Economic Forecasting:** Analysts can track how cities move between clusters over time as income and livability metrics evolve.

---

### 3. Model Architecture & Future Enhancements

* **Validation:** $K=4$ was validated via the Elbow Method, minimizing Within-Cluster Sum of Squares (WCSS = $890.43$).
* **Future Scope:**
* Experiment with density-based algorithms like **DBSCAN** or **Hierarchical Clustering** to detect arbitrary cluster shapes.
* Integrate geo-spatial mapping using **Plotly** or **Folium** for interactive geographic visual analysis.
