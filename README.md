# Table of Contents

1. [Importing Libraries/Packages](#importing-librariespackages)<br>
2. [Loading the DataSet](#loading-the-dataset)<br>
    2.1. [DataSet Description](#dataset-description)<br>
    2.2. [Data Import & Cleaning](#data-import--cleaning)<br>
3. [Feature Engineering](#feature-engineering)<br>
    3.1. [New Features](#new-features)<br>
    3.2. [Modifying Existing Features](#modifying-existing-features)<br>
4. [Removing Redundant Columns](#removing-redundant-columns)<br>
5. [Correlation Heatmap](#correlation-heatmap)<br>
6. [Outlier Detection](#outlier-detection)<br>
7. [Exploratory Data Analysis (EDA)](#exploratory-data-analysis-eda)<br>
8. [Encoding Categorical Data & Feature Scaling](#encoding-categorical-data--feature-scaling)<br>
    8.1. [Before Encoding Categorical Data](#before-encoding-categorical-data)<br>
    8.2. [After Label Encoding Categorical Data](#after-label-encoding-categorical-data)<br>
    8.3. [Feature Scaling](#feature-scaling)<br>
9. [Dimensionality Reduction](#dimensionality-reduction)<br>
10. [Clustering](#clustering)<br>
    10.1. [Agglomerative Clustering](#agglomerative-clustering)<br>
    10.2. [KMeans Clustering](#kmeans-clustering)<br>
11. [Clustering Analysis](#clustering-analysis)<br>
    11.1. [Cluster 0](#cluster-0)<br>
    11.2. [Cluster 1](#cluster-1)<br>
    11.3. [Cluster 2](#cluster-2)<br>
    11.4. [Cluster 3](#cluster-3)<br>
12. [Conclusion](#conclusion)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---
# Marketing Strategy Development using Customer Segmentation Analysis 📊💰🎯
---

This project involves Exploratory Data Analysis (EDA) and clustering to understand customer segments. The following document outlines the steps taken during the analysis, including data cleaning, feature engineering, and visualization.

To run the notebook, simply upload the data file by doing one of the following things

1. Upload Google Drive
2. Upload as temporary file per session
3. Run Locally by using one main wokring directory

Once decided, simply modify data load cell to reflect the approach used and run all cells from there on.

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Importing Libraries/Packages

Various Libraries & Packages have been used. Examples - 

- *numpy*
- *pandas*
- *matplotlib*
- *seaborn*
- *plotly*
- *mpl_toolkits*
- *datetime*
- *sklearn*
- *yellowbrick*
- *sys*
- *os*
- *warnings*
- *typing*

In case of a local run, missing libraries can be installed using the following pip command -

`pip install numpy pandas matplotlib seaborn scikit-learn plotly yellowbrick`

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Loading the DataSet

### DataSet Description

*Dataset Link* - https://raw.githubusercontent.com/amankharwal/Website-data/master/marketing_campaign.csv

*   *`ID`*: Customer's unique identifier
*   *`Year_Birth`*: Customer's birth year
*   *`Education`*: Customer's education level 
*   *`Marital_Status`*: Customer's marital status
*   *`Income`*: Customer's yearly household income
*   *`Kidhome`*: Number of children in customer's household
*   *`Teenhome`*: Number of teenagers in customer's household
*   *`Dt_Customer`*: Date of customer's enrollment with the company
*   *`Recency`*: Number of days since customer's last purchase
*   *`Complain`*: 1 if the customer complained in the last 2 years, 0 otherwise
*   *`MntWines`*: Amount spent on wine in last 2 years
*   *`MntFruits`*: Amount spent on fruits in last 2 years
*   *`MntMeatProducts`*: Amount spent on meat in last 2 years
*   *`MntFishProducts`*: Amount spent on fish in last 2 years
*   *`MntSweetProducts`*: Amount spent on sweets in last 2 years
*   *`MntGoldProds`*: Amount spent on gold in last 2 years
*   *`NumDealsPurchases`*: Number of purchases made with a discount
*   *`AcceptedCmp1`*: 1 if customer accepted the offer in the 1st campaign, 0 otherwise
*   *`AcceptedCmp2`*: 1 if customer accepted the offer in the 2nd campaign, 0 *   otherwise
*   *`AcceptedCmp3`*: 1 if customer accepted the offer in the 3rd campaign, 0 otherwise
*   *`AcceptedCmp4`*: 1 if customer accepted the offer in the 4th campaign, 0 otherwise
*   *`AcceptedCmp5`*: 1 if customer accepted the offer in the 5th campaign, 0 otherwise
*   *`Response`*: 1 if customer accepted the offer in the last campaign, 0 otherwise
*   *`NumWebPurchases`*: Number of purchases made through the company’s website
*   *`NumCatalogPurchases`*: Number of purchases made using a catalogue
*   *`NumStorePurchases`*: Number of purchases made directly in stores
*   *`NumWebVisitsMonth`*: Number of visits to company’s website in the last month

*`Note - Z_Revenue & Z_CostContact columns have same values for all rows and will be dropped`*

### Data Import & Cleaning

The initial stage involves preparing the data for analysis:

1. **Data Import**: The datafile can be on the Google Drive (as is the case in this project), or on the local system or uploaded on a per session basis. The notebook has commented lines of code for each of those scenarios to load it for use with the notebook.

2. **Data Cleaning**: We perform several data cleaning steps to ensure the quality of our analysis. 

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Feature Engineering

### New Features
We enhance our dataset with more informative features like:

- `Total_Money_Spent`
- `Customer_Age`
- `Days_Since_Registered`
- `Total_Children`
- `Family_Size`
- `Parenthood`

### Modifying Existing Features

- **Relationship Status**: The `Marital_Status` column is transformed into a `Relationship_Status` column with categories 'partner' or 'alone'.

---

## Removing Redundant Columns
- **Redundant Columns**: We remove columns that are not necessary for our analysis (like `ID`,`Marital_Status`,`Dt_Customer`,`Year_Birth`), as well as any outliers that do not necessarily add extra information


<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Correlation Heatmap

Using the seaborn library, we create visual representations of our data:

- **Correlation Heatmap**: To understand the relationships between different variables.

![Correlation_Heatmap](./images/1_correlation_heatmap.png)

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Outlier Detection

Upon reviewing the cluster plots, we identify and remove outliers from our dataset. For example:

- Customers with an income greater than $250,000.
- Customers older than 100 years.

Pairplot is given below

![pairplot_for_outlier_detection](./images/2_pairplots.png)


After outlier removal, we update our dataset accordingly.

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Exploratory Data Analysis (EDA)

Before doing any sort of machine learning to identify segments, let's look as some existing trends

- *Relation b/w Purchase Preferences & Relationship Status*
- *Previous Campaign Performances*
- *Latest Campaign's Performance based on Customer Age & Education Level*
- *Relationship Status & Education Levels*
- *Money Spent & Quantity Bought for Different Products*
- *Relation between Latest Campaign's Performance & Relationship Status*

Detailed Graphs are part of the Python Notebook

---

## Encoding Categorical Data & Feature Scaling

### Before Encoding Categorical Data

Two Types of Categorical Data Exists -

- *`Education`*

| **Education Level** | **Count**  |
|---|---|
| Graduation  | 1115  |
|  PhD | 480  |
|  Master | 365  |
|  2n Cycle | 198  |
|  Basic | 54  |

*dtype: int64*

- *`Relationship_Status`*


| Relationship Status  | Count  |
|---|---|
| Partner  | 1428  |
|  Alone | 784  |

*dtype: int64*

<br>

### After Label Encoding Categorical Data

Post Label Encoding, the variables now look like this

- *`Education`*

| **Education Level** | **Count**  |
|---|---|
| 2n Cycle  | 0  |
|  Basic | 1  |
|  Graduation | 2  |
|  Master | 3  |
|  PhD | 4  |

- *`Relationship_Status`*

| Relationship Status  | Label Encoded Value  |
|---|---|
| Partner  | 1  |
|  Alone | 0  |

### Feature Scaling

- Since the dataset has features which vary in degree of magnitude (for example, income would be in order of thousands or tens of thousands, but age would be less than 100), the machine learning model can be disproportionately influenced

- To counter this, we do feature scaling

- For our use-case, we have used *`Standard Scaling`*.

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---
## Dimensionality Reduction

- Through the correlation heatmap, we know some features are highly correlated, and may not be adding extra infomration to the dataset but might be adding noise instead

- To counter this we can use Principal Component Analysis

- By checking Cumulative Captured Variance, we arrived on the number of 15 PCA variables that capture just over 94% of the explained variance of the dataset


![PCA & Explained Variance](./images/3_captured_variance_vs_num_of_pca_variables.png)

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Clustering

### Agglomerative Clustering

![Agglomerative Clustering - Distribution Count](./images/4_ac_clusters_countplot.png)

- Number of customers in cluster 0 = 682
- Number of customers in cluster 1 = 431
- Number of customers in cluster 2 = 507
- Number of customers in cluster 3 = 592

<!-- Page Break -->
<div style="page-break-after: always;"></div>

### KMeans Clustering

![KMeans Clustering - Distribution Count](./images/5_kmeans_clusters_countplot.png)

- Number of customers in cluster 0 = 488
- Number of customers in cluster 1 = 515
- Number of customers in cluster 2 = 561
- Number of customers in cluster 3 = 648

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Clustering Analysis

![Clustering_Analysis_Part2](images/6_clustering_and_income_vs_total_spending.png)<br>

![Clustering_Analysis_Part3](images/7_income_vs_ac_clusters.png)

*In the above plot, the **`yellow triangle marker`** represents the **`average income of the cluster`*** <br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part4](images/8_education_vs_ac_clusters.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part5](images/9_category_wise_spending_vs_ac_clusters_part_1.png)<br>

![Clustering_Analysis_Part6](images/9_category_wise_spending_vs_ac_clusters_part_2.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part7](images/10_purchase_channel_preference_vs_ac_clusters_part_1.png)<br>

![Clustering_Analysis_Part8](images/10_purchase_channel_preference_vs_ac_clusters_part_2.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part9](images/11_jointplot_part_1.png)<br>

![Clustering_Analysis_Part10](images/11_jointplot_part_2.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part11](images/11_jointplot_part_3.png)<br>

![Clustering_Analysis_Part12](images/11_jointplot_part_4.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part13](images/11_jointplot_part_5.png)<br>

![Clustering_Analysis_Part14](images/11_jointplot_part_6.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

![Clustering_Analysis_Part15](images/11_jointplot_part_7.png)<br>

<!-- Page Break -->
<div style="page-break-after: always;"></div>

---

## Conclusion

### Cluster 0

*   ***`Extremely High Chance`*** that they are Parents
*   ***`High Chance`*** that they have a partner
*   ***`High Chance`*** that they have either 1 or 2 children
*   ***`High Chance`*** that their Education Level is either "Graduation", "Master" or "PhD"
*   ***`High Chance Income`*** is between \$20,000 and \$60,000

### Cluster 1

*   ***`Good Chance`*** that they are not be parents
*   ***`High Chance`*** they do not have a partner
*   ***`High Chance`*** that their Income is between \$20,000 and \$60,000
*   ***`High Chance`*** that their Education level is “Graduation”


### Cluster 2

*   ***`Extremely High Chance`*** that they are not parents
*   ***`High Chance`*** that their Income is between \$55,000 and \$100,000
*   ***`High Chance`*** that their Education level is not “Basic”, and is “Graduation”

### Cluster 3

*   ***`Extremely High Chance`*** that they are parents
*   ***`High Chance`*** that their Income is between \$40,000 and \$80,000
*   ***`Good Chance`*** that their Education level is “Graduation”, “Master” or “Phd”, and is almost definitely not “Basic”
