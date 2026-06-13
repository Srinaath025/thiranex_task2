# Customer Segmentation Dashboard using Power BI & K-Means Clustering

## Project Overview

This project focuses on customer segmentation using the Mall Customers dataset. K-Means Clustering was performed in Python to group customers based on their purchasing behavior and demographic characteristics. The clustered data was then imported into Power BI for interactive visualization and analysis.

---

## Dataset

**Dataset:** Mall_Customers.csv

### Attributes Used

* CustomerID
* Gender
* Age
* Annual Income (k$)
* Spending Score (1-100)

---

## Data Preprocessing in Python

### Steps Performed

1. Loaded the dataset using Pandas.
2. Removed missing values.
3. Renamed columns:

   * Annual Income (k$) → Income
   * Spending Score (1-100) → SpendingScore
4. Selected features:

   * Age
   * Income
   * SpendingScore
5. Standardized features using StandardScaler.
6. Used Elbow Method to determine the optimal number of clusters.
7. Applied K-Means Clustering with K = 5.
8. Generated cluster labels (0–4).
9. Applied PCA for cluster visualization.
10. Exported clustered dataset as:

```text
customer_segments_output.csv
```

---

## Technologies Used

### Python

* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-Learn

### Power BI

* Data Visualization
* DAX
* Interactive Dashboard

---

## Dashboard Pages

### Page 1: Customer Segmentation Overview

#### KPI Cards

* Total Customers
* Average Age
* Average Income
* Average Spending Score

#### Visualizations

* Donut Chart – Customer Distribution by Cluster
* Scatter Plot – Income vs Spending Score by Cluster
* Cluster Summary Table

---

### Page 2: Customer Insights

#### Visualizations

* Average Income by Cluster
* Average Spending Score by Cluster
* Average Age by Cluster
* Gender Distribution by Cluster
* Treemap – Customer Segment Distribution

---

## DAX Calculated Columns

### Cluster Label

Created to display readable cluster names.

```DAX
ClusterName =
SWITCH(
customer_segments_output[cluster],
0, "Target Customers",
1, "Standard Customers",
2, "Careful Customers",
3, "Sensible Customers",
4, "VIP Customers"
)
```

---

### Alternative Cluster Label

```DAX
ClusterLabel =
"Cluster " & customer_segments_output[cluster]
```

---

## DAX Measures

### Total Customers

```DAX
Total Customers =
COUNT(customer_segments_output[CustomerID])
```

### Average Age

```DAX
Average Age =
AVERAGE(customer_segments_output[Age])
```

### Average Income

```DAX
Average Income =
AVERAGE(customer_segments_output[Income])
```

### Average Spending Score

```DAX
Average Spending Score =
AVERAGE(customer_segments_output[SpendingScore])
```

### Number of Clusters

```DAX
Number of Clusters =
DISTINCTCOUNT(customer_segments_output[cluster])
```

---

## K-Means Clustering Results

Five customer segments were identified:

| Cluster | Segment Name       |
| ------- | ------------------ |
| 0       | Target Customers   |
| 1       | Standard Customers |
| 2       | Careful Customers  |
| 3       | Sensible Customers |
| 4       | VIP Customers      |

---

## Key Outcomes

* Identified distinct customer segments.
* Analyzed spending patterns and income distribution.
* Visualized customer behavior using interactive Power BI dashboards.
* Generated business insights for targeted marketing strategies.

---

## Project Workflow

```text
Dataset
   ↓
Data Cleaning
   ↓
Feature Selection
   ↓
Standardization
   ↓
Elbow Method
   ↓
K-Means Clustering
   ↓
PCA Visualization
   ↓
Export Clustered Dataset
   ↓
Power BI Dashboard
   ↓
Customer Insights
```

---

## Conclusion

The project successfully segmented customers into five meaningful groups using K-Means Clustering and visualized the results through an interactive Power BI dashboard. The dashboard helps understand customer behavior, spending habits, and income patterns, enabling data-driven business decisions.
