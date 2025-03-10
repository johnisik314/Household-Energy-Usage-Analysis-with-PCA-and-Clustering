# Household Energy Consumption Analysis: PCA & Clustering

![Clusters in PCA Space](images/clusters_pca.png) *Example: Clusters visualized in PCA-reduced space*

## 📌 Overview
This project analyzes household energy consumption patterns using **Principal Component Analysis (PCA)** and **K-Means Clustering**. The goal is to uncover hidden trends in energy usage, segment households into behavior-based groups, and provide actionable insights for energy efficiency.

**Dataset**: [Household Power Consumption](https://www.kaggle.com/datasets/uciml/electric-power-consumption-data-set/data)  
*(Contains minute-level readings of global active/reactive power, voltage, and sub-metering data from December 2006 to November 2010)*

---

## 🛠️ Methodology

### 1. Data Preprocessing
- **Handled Missing Values**: Filled gaps using mean imputation (1.25% of rows).
- **Feature Engineering**:
  - Combined `Date` and `Time` into a `datetime` index.
  - Derived daily/hourly aggregates for trend analysis.
- **Normalization**: Scaled features to [0, 1] using `MinMaxScaler`.

### 2. Dimensionality Reduction (PCA)
- **Objective**: Reduce 8+ features to 3 principal components while retaining **91% variance**.
- **Key Components**:
  - **PC1 (66.8% variance)**: Dominated by HVAC (`Sub_metering_3`) usage.
  - **PC2 (18.9% variance)**: Linked to kitchen/laundry appliances.
  - **PC3 (5.4% variance)**: Captured nuanced patterns.

### 3. Clustering (K-Means)
- **Identified 3 Clusters**:
  - **Cluster 0**: High HVAC usage, low kitchen/laundry activity.
  - **Cluster 1**: Peak multi-appliance usage (evenings/weekends).
  - **Cluster 2**: Low activity (nighttime/unoccupied hours).
- **Visualization**: Clusters mapped to PCA space and time-series trends.

---

## 📊 Results & Insights

### Cluster Characteristics
| Cluster | Name                   | Key Features                                  | Energy Profile              |
|---------|------------------------|----------------------------------------------|-----------------------------|
| 0       | HVAC-Dominated         | High `Sub_metering_3`, moderate global power | Extreme weather usage       |
| 1       | Peak Multi-Appliance   | High kitchen/laundry, peak global power      | Evening/weekend activity    |
| 2       | Low Activity           | Low across all sub-meters                    | Nighttime/unoccupied hours  |

### Key Findings
- **Seasonal Peaks**: Cluster 0 spikes in winter (heating) and summer (AC).
- **Cost Drivers**: Cluster 1 contributes ~60% to energy bills during peak hours.
- **Efficiency Baseline**: Cluster 2 provides a benchmark for low-usage periods.

![Hourly Consumption by Cluster](images/hourly_patterns.png)  
*Hourly energy patterns across clusters*

---

## 🚀 Usage
1. **Clone the Repository**:
   ```bash
   git clone https://github.com/yourusername/Household-Energy-Usage-Analysis-with-PCA-and-Clustering.git
   cd Household-Energy-Usage-Analysis-with-PCA-and-Clustering
