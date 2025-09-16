### **Customer Segmentation with Hierarchical Clustering**

This project performs customer segmentation for an e-commerce platform using an unsupervised machine learning approach. It combines **RFM (Recency, Frequency, Monetary)** analysis with **Agglomerative Hierarchical Clustering** to identify distinct customer groups, providing actionable insights for marketing and business strategy.

---

### **Table of Contents**

1.  [Project Overview](#project-overview)
2.  [Methodology](#methodology)
3.  [Data Source](#data-source)
4.  [Files & Repository Structure](#files--repository-structure)
5.  [Instructions to Run](#instructions-to-run)
6.  [Key Findings & Recommendations](#key-findings--recommendations)
7.  [Evaluation](#evaluation)

---

### **Project Overview**

The primary goal of this project is to move beyond one-size-fits-all marketing by segmenting a customer base into meaningful groups. By analyzing purchasing behavior based on Recency, Frequency, and Monetary value, we can identify high-value customers, at-risk customers, and other key segments. The final output includes a trained clustering model and a dataset with each customer assigned to a specific segment, ready for integration into a business intelligence (BI) dashboard.

---

### **Methodology**

The project follows a standard data science pipeline:
1.  **Data Cleaning & Preprocessing**: Raw transactional data is cleaned to handle missing values, cancellations, and invalid entries.
2.  **Feature Engineering**: Transaction-level data is aggregated to the customer level to compute RFM and other behavioral metrics.
3.  **Data Transformation**: Highly skewed features (Frequency, Monetary) are normalized using log transformation, and all features are scaled using `StandardScaler` to prepare for clustering.
4.  **Clustering**: **Agglomerative Hierarchical Clustering** is applied to the preprocessed data. A **dendrogram** is used to visualize the merging process, and the optimal number of clusters (`k`) is determined using the **Silhouette Score**.
5.  **Cluster Profiling**: Each identified segment is profiled by analyzing the mean and median of its key features (RFM metrics) to give it a descriptive name (e.g., "Champions," "At-Risk").
6.  **Visualization & Evaluation**: PCA is used to visualize the clusters in a 2D plot. The clustering quality is further evaluated using metrics like the **Davies-Bouldin Index**.
7.  **Output & Deployment**: The final model and the segmented customer data are saved for future use and business reporting.

---

### **Data Source**

The dataset used is the **"Online Retail"** dataset, a publicly available transactional dataset from the UCI Machine Learning Repository. It contains transactional data from a UK-based online retailer.

---

### **Files & Repository Structure**

* `customer_segmentation_hierarchical_clustering.ipynb`: The main Jupyter Notebook file containing all the code for data cleaning, preprocessing, clustering, and visualization.
* `Online Retail.xlsx`: The raw data file. (Note: You may need to download this file separately from the UCI repository).
* `agg_clustering_model.pkl`: The saved hierarchical clustering model.
* `customer_segments_final.csv`: The final output file containing all customer data with their RFM features and assigned cluster labels.

---

### **Instructions to Run**

1.  **Clone the repository:**
    ```bash
    git clone [https://github.com/zia9571/Customer-Segmentation-Using-Agglomerative-Clustering.git]
    ```
2.  **Download the data:**
    * Download the `Online Retail.xlsx` file from the [UCI Machine Learning Repository](https://archive.ics.uci.edu/ml/datasets/Online+Retail).
    * Place the file in the project's root directory.
3.  **Set up the environment:**
    * It is recommended to use a virtual environment.
    * Install the required libraries:
        ```bash
        pip install pandas numpy matplotlib seaborn scikit-learn scipy plotly joblib openpyxl
        ```
4.  **Run the Notebook:**
    * Open the Jupyter Notebook:
        ```bash
        jupyter notebook customer_segmentation_hierarchical_clustering.ipynb
        ```
    * Run all the cells in the notebook sequentially. The code is commented to guide you through each step.

---

### **Key Findings & Recommendations**

After running the analysis, two distinct customer segments were identified:

* **The Core Customer Base**: This large segment represents the majority of customers. They purchase with moderate frequency and contribute a consistent amount of revenue.
    * **Recommendation:** Focus on **retention and loyalty**. Engage them with personalized emails, loyalty programs, and relevant product recommendations.
* **The Extreme High-Value Buyers**: This is a small but incredibly high-spending segment. These customers may be B2B clients or individuals who made a single, very large purchase.
    * **Recommendation:** Implement **personalized, high-touch sales strategies**. Consider direct outreach, exclusive offers, and dedicated account management.

---

### **Evaluation**

The quality of the clustering was confirmed by:

* **Silhouette Score**: A score of **0.9657** indicated that the clusters are well-separated.
* **Davies-Bouldin Index**: A score of **0.3626** further validated that the clusters are compact and distinct.
