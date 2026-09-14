# Customer Segmentation — Unsupervised Learning

An unsupervised machine learning project that segments shopping-mall customers into distinct groups using clustering and dimensionality reduction.

This project was built for **Assignment 9** as part of the Data Analytics & AI (DAAI) diploma.

---

## Project Overview

The goal is **customer segmentation**: discovering natural groups of customers who are similar in age, income, and spending behaviour, so a marketing team can target each group differently. Because this is unsupervised learning, the data has no target label — instead of predicting an outcome, the aim is to *discover structure* in the data.

- **Problem type:** Unsupervised learning (clustering + dimensionality reduction)
- **No target variable** — the goal is to find hidden segments
- **Methods:** K-means clustering, Hierarchical clustering, and PCA

---

## Dataset

- **File:** `Mall_Customers.csv`
- **Source:** Kaggle — Mall Customer Segmentation Data
- **Rows:** 200 customers
- **Columns:** 5 — no missing values

| Column | Description |
|---|---|
| CustomerID | Unique identifier (not used for clustering) |
| Gender | Male / Female |
| Age | Customer age |
| Annual Income (k$) | Yearly income in thousands |
| Spending Score (1–100) | Score assigned by the mall based on spending behaviour |

---

## Methods

1. **Preprocessing** — dropped CustomerID, encoded Gender to numeric, and scaled all features with StandardScaler (essential for distance-based clustering).
2. **EDA** — examined feature distributions and the Income vs Spending relationship to spot natural structure.
3. **K-means clustering** — used the Elbow method and Silhouette score to choose the number of clusters (K = 5).
4. **Hierarchical clustering** — built a dendrogram (Ward linkage) as a second, independent clustering method.
5. **Dimensionality Reduction (PCA)** — reduced the four features to two components to visualise all segments in a single 2D chart.
6. **Evaluation** — compared both methods using the Silhouette score.
7. **Deployment & Monitoring** — saved the best model and scaler, and discussed how the model would be deployed, monitored for drift, and re-trained.

---

## Results

- **Optimal number of clusters:** K = 5 (chosen using Elbow + Silhouette, with practical judgement about usable segment sizes)
- **PCA:** the first two components retained about **59%** of the total variance
- **Silhouette scores:**

| Method | Silhouette Score |
|---|---|
| **K-means** | **0.304** |
| Hierarchical | 0.287 |

**Best method: K-means**, with the slightly higher silhouette score. Both methods independently identified the same five customer segments, giving strong confidence that the segments are genuine.

The five segments correspond to distinct shopper types (e.g. high income/high spend, high income/low spend, low income/high spend, average, and budget-conscious customers).

---

## How to Run

This project runs in **Google Colab** (no local setup required).

1. Open the notebook `Assignment_9_Unsupervised_Learning.ipynb` in Google Colab.
2. Upload the dataset `Mall_Customers.csv` using the folder icon on the left sidebar.
3. Run all cells from top to bottom (`Runtime` → `Run all`).

### Requirements

If running locally instead of Colab, install the dependencies:

```bash
pip install pandas numpy matplotlib seaborn scikit-learn scipy joblib
```

---

## Files in this Repository

| File | Description |
|---|---|
| `Assignment_9_Unsupervised_Learning.ipynb` | Main notebook with all code and interpretations |
| `Mall_Customers.csv` | The dataset |
| `README.md` | This file |

---

## Author

**Hiren Patel** — Data Analytics & AI (DAAI) diploma, Willis College
