# 🛍️ Customer Segmentation Analysis using RFM & KMeans Clustering

This project performs customer segmentation using RFM (Recency, Frequency, Monetary) analysis and KMeans clustering on an e-commerce transactional dataset. RFM is a powerful marketing technique for understanding customer value and tailoring strategies accordingly.
 It also handles outliers separately to improve clustering quality and business insight.

 ## 📊 What is RFM?
- **Recency (R)**: How recently a customer made a purchase
- **Frequency (F)**: How often a customer makes a purchase
- **Monetary (M)**: How much money a customer spends

---

## 📂 Project Overview

Many companies have thousands of customers, but not all of them behave the same. Some buy frequently, others once in a while. Some spend big, others very little. This project applies RFM analysis and clustering to identify these patterns and guide marketing decisions.

---

## 📦 Dataset
The dataset used for this analysis is available in the repository:

- [`Customer_Segmentation_Data.csv`](https://github.com/Jcboy101/Customer-Segmentation-Analysis/blob/main/Customer%20Segmentation%20Analysis.ipynb)


- Source: [Uc Irvin Machine Learning Repository](https://www.youtube.com/redirect?event=video_description&redir_token=QUFFLUhqa2dUeE9sd25UV3JiLUo0OWFvZ2VWQ1NORm9EZ3xBQ3Jtc0ttdHljY3ZhYkhfdmp5MGxaQWd5Q2JmWU5PMzE1WFFuT3U2M2tXVWZIZXNxeHFMRmxDZm10c1FoZFdFeW1PQ1V3UFVDX1h1SGNvTEd3dGZUWEl0TFgweEd0cGhKb1plT0hBdjU3UmQ0VDg0UDlmM1doWQ&q=https%3A%2F%2Farchive.ics.uci.edu%2Fdataset%2F502%2Fonline%2Bretail%2Bii&v=afPJeQuVeuY)  
- Shape: ~540,000 transactions
- Fields:
  - `InvoiceDate`: Date of transaction
  - `Quantity`: Number of items bought
  - `Price`: Price per item
  - `Customer ID`: Unique identifier for each customer
    
 ![Screenshot 2025-05-19 183130](https://github.com/user-attachments/assets/3bd59116-ced2-4d10-9d6b-4fcc82fdf1d0)

  ## 🛠️ Tools Used
- Python
- Pandas
- NumPy
- Matplotlib / Seaborn
- Scikit-learn


---

## 🔍 Objectives

- Calculate RFM metrics per customer
- Detect and isolate outliers
- Segment customers using KMeans clustering
- Visualize and interpret customer clusters
- Provide marketing recommendations per segment

---

## 🧠 Methodology

### 1. Data Cleaning
- Removed rows with missing `Customer ID`
- Filtered out rows with negative `Quantity` or `Price`
- Converted `InvoiceDate` to datetime
  
![Screenshot 2025-05-19 183643](https://github.com/user-attachments/assets/8aef0ffa-29e4-4ea8-892a-d05afd4e0870) 

![Screenshot 2025-05-19 183804](https://github.com/user-attachments/assets/e9094e88-95b4-47d6-bc7c-84031cdac4ec)



### 2. RFM Feature Engineering
Calculated for each customer:
- **Recency**: Days since last purchase (relative to the latest date in dataset)
- **Frequency**: Number of unique purchases (InvoiceNo)
- **Monetary**: Total amount spent (Quantity)

![Screenshot 2025-05-19 185225](https://github.com/user-attachments/assets/8d0011eb-b347-46b6-af72-f557873de298)



### 3. Outlier Detection and Handling
- Used **IQR method** to detect outliers in RFM features
- Outliers were **excluded from main clustering** to prevent skew
- They were later **assigned to a dedicated 'Outlier' cluster**

### 4. Clustering
- Scaled RFM features using `StandardScaler`
- Used **Elbow Method** and **Silhouette Score** to find optimal `k`

![Screenshot 2025-05-19 191932](https://github.com/user-attachments/assets/c691351b-4a5a-4d19-b9ff-aeaa9a65c297)

- Applied **KMeans clustering**

![Screenshot 2025-05-19 192146](https://github.com/user-attachments/assets/8a5bce9b-c0d7-49ab-9d49-8199aafadf37)

- Final results include 4 clusters + 1 for outliers

### 5. Distribution Analysis with Violin Plots
-To better understand the spread and distribution of RFM scores across clusters:

-Generated violin plots for each RFM metric per cluster

![Screenshot 2025-05-19 193153](https://github.com/user-attachments/assets/9c842558-0734-44a6-abf0-2ecaad6bfb96)

-These plots combine boxplots with kernel density estimation to:
 -i: Visualize skewness and outliers within clusters
 -ii: Compare variability across clusters for Recency, Frequency, and Monetary

This helped validate cluster compactness and identify inconsistent segments.



### 6. Visualization
- Scatter plots of clusters by RFM dimensions
- Cluster-wise comparison bar charts
- Silhouette score plot and Elbow curve


---

## 📊 Results

| Cluster | Behavior                            | Description                        | Strategy                     |
|---------|-------------------------------------|------------------------------------|------------------------------|
| 0       |Low Recency, Low Frequency, Low Monetary |  Inactive or Lapsed Users     |              Re-Engage           |
| 1       |  High Recency, High Frequency, High Monetary | Most Loyal              | Reward  |
| 2       |  Low Recency, Low Monetary,  Recent Purchase  | First-time buyers         | Onboarding and nurturing      |
| 3       | Low Recency, High Monetary,  High Frequency | High Valued              | Retain|
| 4       | Outliers (Extreme spend or behavior) | Irregular patterns                | Investigated separately       |

![Screenshot 2025-05-19 193419](https://github.com/user-attachments/assets/ef82a6be-f3d7-4b16-96a0-9737c3d0bee9)

Find final output data here [Output Data](data.csv)


---

## 📈 Analysis Visualizations

- Bar charts comparing average RFM values across clusters

![Screenshot 2025-05-19 193605](https://github.com/user-attachments/assets/345a460e-96ef-4f35-89a8-141848ac5210)


---

## 🛠️ How to Run This Project

### Requirements

```bash
pip install -r requirements.txt
```

### Running

1. Clone this repo:
   ```bash
   git clone https://github.com/Jcboy101/Customer-Segmentation-Analysis.git
   cd Customer-Segmentation-Analysis
   ```

2. Launch the notebook:
   ```bash
   jupyter notebook 'Customer Segmentation Analysis.ipynb'
   ```

---



## 📧 Contact

**Author:** Jude Chukwumba  
**LinkedIn:** [linkedin.com/in/jude-chukwumba](#)  
**Email:** onyedikajude619@gmail.com

---

## ✅ Key Takeaways

- RFM is a powerful, simple framework for segmentation.
- Outlier separation leads to more accurate clustering.
- This type of segmentation can drive **targeted marketing** and **retention strategies**.

---




