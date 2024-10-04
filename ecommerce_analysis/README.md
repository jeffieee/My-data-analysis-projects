
# E-commerce Dataset Analysis - Exploratory Data Analysis (EDA)

## Project Overview
This notebook performs an exploratory data analysis (EDA) on an e-commerce dataset. The main goal is to uncover insights into customer behavior, product sales, and key performance metrics, using various visualizations and statistical techniques.

## Sections Overview

### 1. Importing Necessary Libraries
The first section imports the necessary libraries required for data analysis and visualization, including:
- `pandas`, `numpy`: For data manipulation.
- `seaborn`, `matplotlib`, `plotly`: For data visualization.
- `warnings`: To suppress unnecessary warnings during execution.

### 2. Loading the Data
The dataset is loaded from a CSV file using `pandas.read_csv()`. This dataset contains e-commerce transactions and customer details that will be analyzed throughout the notebook.

**Note** Verify the path and ensure that the dataset is up to date and contains relevant fields for analysis.

### 3. Sanity Check of the Data
A preliminary data inspection is done to check the shape and basic statistics using:
- `data.head()`: To view the first few rows of the dataset.
- `data.info()`: To inspect data types, null values, and overall structure.

**Note** Handle missing values and outliers at this stage to prevent inaccuracies during analysis.

### 4. Exploratory Data Analysis (EDA)
This section dives deeper into the dataset, exploring various patterns, trends, and relationships:
- **Data Cleaning**: Removing missing or irrelevant data.
- **Descriptive Statistics**: Calculating measures like mean, median, standard deviation to understand the distribution of key variables.
- **Sales Analysis**: Visualizing total sales over time to identify seasonal trends or spikes.
- **Customer Segmentation**: Using clustering methods to categorize customers based on purchasing behavior.


### 5. Key Visualizations and Findings:
This section includes visual representations of data such as:

- **Bar Chart - Sales per Product Category**:

    <!-- ![Bar Chart - Sales per Product Category](path_to_bar_chart.png) -->
    
    This bar chart shows the sales distribution across different product categories.
    
    **Key Takeaway**: Electronics and fashion are the top-selling categories, contributing significantly to overall revenue.

- **Pie Chart - Purchase Method Distribution**:

    <!-- ![Pie Chart - Purchase Method Distribution](path_to_purchase_method_distribution.png) -->
    
    This pie chart visualizes the distribution of purchase methods used by customers.
    
    **Key Takeaway**: The majority of purchases (40.2%) are made via credit card, indicating a preference for this payment method. Understanding this trend can guide payment integration strategies, potentially optimizing customer experience and sales.

- **Time Series Plot - Purchase Date vs Gross Amount**:

    <!-- ![Time Series Plot - Purchase Date vs Gross Amount](path_to_time_series_plot.png) -->
    
    This time series visualization shows the relationship between purchase dates and the gross amount.
    
    **Key Takeaway**: The data indicates significant transactions on **November 2, 2020**, with a gross amount of **11.9080k**. In contrast, **September 9, 2024**, shows a gross amount of **11.48776k**. This highlights fluctuations in purchasing behavior over time and can aid in identifying periods of higher sales activity or potential market changes.

- **Location-Based Analysis**:

    <!-- ![Location-Based Analysis](path_to_location_based_analysis.png) -->
    
    This visualization analyzes sales data based on customer locations.
    
    **Key Takeaway**: The analysis reveals that Mumbai is the leading location with 11.197k transactions, followed closely by Delhi with 10.799k transactions. These insights can help target specific regions for marketing campaigns.


- **Gross Amount Across Product Categories**:

    <!-- ![Gross Amount Across Product Categories](path_to_gross_amount_product_categories.png) -->
    
    This visualization illustrates the gross amount across different product categories using a box plot.
    
    **Key Takeaway**: The box plot indicates that the **Toys and Games** category has the highest gross amount, with a maximum value of **8365.19**. The quartile values for this category are as follows:
    - Q1: **1628.667**
    - Median: **3027.738**
    - Q3: **4410.217**
    - Lower fence: **165.0024**
    
    These statistics suggest a strong performance in the Toys and Games category, indicating potential for increased marketing focus or inventory expansion.

- **Grouped Bar Plot for Average Net Amount by Gender and Age Group**:

    <!-- ![Grouped Bar Plot for Average Net Amount by Gender and Age Group](path_to_grouped_bar_plot.png) -->
    
    This grouped bar plot shows the average net amount spent categorized by gender and age group.
    
    **Key Takeaway**: 
    - **Female (Under 60 and Above)**: Average net amount of **2892.742**.
    - **Male (Under 18)**: Average net amount of **2938.578**.
    - **Other (Under 60 and Above)**: Average net amount of **2898.453**.
    
    These insights indicate varying spending patterns among genders and age groups, which can inform targeted marketing strategies.


### 6. Conclusion
This notebook provides a comprehensive overview of the e-commerce dataset, highlighting key insights into customer behavior, sales trends, and product performance. Notable findings include:

- **Sales Trends**: Electronics and fashion emerge as the top-selling categories, indicating strong consumer interest in these products.
- **Purchase Method Preference**: A significant portion of transactions (40.2%) are conducted via credit card, suggesting opportunities to optimize the payment experience.
- **Location Insights**: Sales are primarily concentrated in Mumbai and Delhi, indicating potential for targeted marketing strategies in these regions.
- **Demographic Insights**: The analysis shows varied spending patterns among different genders and age groups, which can guide personalized marketing efforts.
- **Time-Based Trends**: Fluctuations in gross amounts over time, especially around significant dates, reveal important patterns that could inform future sales strategies.

Future analysis could include predictive modeling or in-depth customer segmentation to further optimize marketing efforts.

## Suggestions for Improvement:
1. **Feature Engineering**: Create new features, such as average purchase value or days between purchases, to enhance customer segmentation.
2. **Predictive Analysis**: Build machine learning models to forecast sales trends and customer churn, which can help in proactive marketing and retention strategies.
3. **Further EDA**: Conduct a more detailed analysis of underperforming product categories to uncover underlying issues and develop corrective strategies.
4. **Data Enrichment**: Integrate additional datasets, such as marketing campaign data, to provide a more holistic view of sales drivers and enhance strategic decision-making.
5. **Customer Lifetime Value (CLV)**: Explore deeper insights into customer lifetime value to guide marketing strategies and improve retention efforts.


