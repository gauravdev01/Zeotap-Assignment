# Data Science Assignment: eCommerce Transactions Dataset

## Overview
This assignment focuses on analyzing an eCommerce dataset consisting of **Customers.csv**, **Products.csv**, and **Transactions.csv**. The main tasks include exploratory data analysis (EDA), developing a lookalike model, and performing customer segmentation using clustering techniques. Below is a description of the approach used to tackle each task.

---

## Approach

### Task 1: Exploratory Data Analysis (EDA)
1. **Data Loading and Preprocessing**:
   - I loaded the **Customers.csv**, **Products.csv**, and **Transactions.csv** datasets into Pandas dataframes.
   - Converted the **SignupDate** and **TransactionDate** columns to datetime format for proper analysis.

2. **Missing Values and Summary Statistics**:
   - I checked for missing values in each dataset using `isnull().sum()` to understand if any data cleaning was required.
   - Generated summary statistics for the **Transactions** dataset using `describe()` to get an overview of numerical columns.

3. **EDA Analysis**:
   - Merged the **Customers.csv** and **Products.csv** datasets with **Transactions.csv** using `merge()` to combine relevant customer and product information.
   - Visualized **Total Sales Over Time** using a line plot of sales per day.
   - Identified the **Top 10 Customers by Revenue** by grouping transactions by `CustomerName` and summing the `TotalValue`.
   - Analyzed the **Best-Selling Products** by grouping data by `ProductName` and summing the `Quantity`.
   - Explored **Revenue by Region** by grouping data by `Region` and summing the `TotalValue`.
   - Generated a bar plot to visualize the revenue distribution across different regions.

**Key Insights**:
- **Top Customers**: Identifying the most valuable customers can help target marketing efforts effectively.
- **Best-Selling Products**: Helps in inventory and supply chain management by recognizing high-demand products.
- **Revenue by Region**: Insight into which regions are driving most of the sales, useful for region-based targeting and resource allocation.

---

### Task 2: Lookalike Model
1. **Data Preprocessing**:
   - Merged **customer_data** and **purchase_history** to combine customer information with transaction details.
   - Merged the **product_data** with the previous dataset to include product-related information.
   
2. **Feature Engineering**:
   - Aggregated features like **Price** (total amount spent by the customer), **ProductID** (count of purchases), and **Category** (product categories the customer bought from).
   - The **Category** column was processed by splitting the categories and applying one-hot encoding using `pd.get_dummies()` to handle categorical data.

3. **Standardization**:
   - Applied **StandardScaler** to standardize the **Price** and **ProductID** columns for better comparison.

4. **Cosine Similarity**:
   - Calculated the **Cosine Similarity** between customers based on the transformed feature space to identify similar customers.
   - For each customer, I identified the top 3 most similar customers, based on cosine similarity, and stored this information in a **Lookalike.csv** file.

**Output**:
- A file, **Lookalike.csv**, which contains the top 3 similar customers and their similarity scores for the first 20 customers.

---

### Task 3: Customer Segmentation / Clustering
1. **Data Preprocessing**:
   - Combined customer and transaction information to form a comprehensive feature dataset.
   - Standardized the features to ensure they have a mean of 0 and a variance of 1.

2. **Clustering**:
   - I implemented KMeans clustering to segment customers into groups based on their profiles and transaction behavior. I experimented with different numbers of clusters (between 2 and 10).
   - Calculated the **Silhouette Score** and **Davies-Bouldin Index (DB Index)** to evaluate the clustering performance.

3. **Visualization**:
   - Used **PCA (Principal Component Analysis)** to reduce the dimensionality of the data to two components for easier visualization.
   - Visualized the clusters using a scatter plot, with each point representing a customer and colored by their assigned cluster.

**Clustering Report**:
- **Number of Clusters**: 3
- **DB Index**: 1.1167 (lower is better, indicating that the clusters are well-separated)
- **Silhouette Score**: 0.38 (indicates the quality of clustering, with values closer to 1 being better)
- **Inertia**: 92.91 (lower inertia indicates better clustering)
- **Cluster Centers**: Coordinates of the cluster centers in the feature space.
  
This segmentation helps understand customer behavior and can be used for targeted marketing strategies.

---

## Deliverables
1. **EDA**: A Jupyter Notebook containing the code for data preprocessing, EDA analysis, and business insights. A PDF report summarizing the insights derived from EDA.
2. **Lookalike Model**: A Jupyter Notebook explaining the development of the lookalike model, and a **Lookalike.csv** file containing customer recommendations.
3. **Customer Segmentation**: A Jupyter Notebook containing the clustering code, along with visualizations and a detailed report on the clustering results.

---

## Evaluation Criteria
- **EDA**: Insightfulness and clarity of the business insights.
- **Lookalike Model**: Model accuracy, quality of recommendations, and similarity scores.
- **Customer Segmentation**: Clustering logic, effectiveness of the segmentation, and quality of visualizations.

## Dataset Links
- [Customers.csv](https://drive.google.com/file/d/1bu_--mo79VdUG9oin4ybfFGRUSXAe-WE/view?usp=sharing)
- [Products.csv](https://drive.google.com/file/d/1IKuDizVapw-hyktwfpoAoaGtHtTNHfd0/view?usp=sharing)
- [Transactions.csv](https://drive.google.com/file/d/1saEqdbBB-vuk2hxoAf4TzDEsykdKlzbF/view?usp=sharing)

---

This approach ensures that each task is addressed with clarity, leveraging relevant Python libraries like Pandas, Matplotlib, Seaborn, and Scikit-learn to derive valuable insights from the dataset.
