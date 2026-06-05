# Supply Chain Analytics: Optimizing Performance and Profitability

## Project Overview
This project focuses on a comprehensive analysis of a supply chain dataset to identify inefficiencies, predict delivery performance, and drive strategic improvements. By employing robust data cleaning, advanced feature engineering, and the calculation of key performance indicators (KPIs), this analysis provides actionable insights into customer behavior, order fulfillment, and profitability.

## Problem Statement
In a highly competitive global market, optimizing supply chain operations is crucial for business success. This project addresses the challenge of transforming raw, heterogeneous supply chain data into a structured and insightful format to:
1.  **Enhance Data Quality**: Identify and resolve issues like missing values and duplicates.
2.  **Uncover Key Drivers**: Understand factors influencing shipment delays, delivery performance, and profit margins.
3.  **Measure Performance**: Establish critical KPIs to monitor the health and efficiency of the supply chain.
4.  **Inform Strategic Decisions**: Provide a data-driven foundation for operational improvements and customer satisfaction.

## Tools and Libraries
-   **Python**: The primary programming language for data manipulation and analysis.
-   **Pandas**: Essential for data loading, cleaning, and transformation.
-   **NumPy**: Used for numerical operations.
-   **Matplotlib & Seaborn**: For data visualization and exploratory data analysis.
-   **Scipy**: For scientific computing and statistical analysis.
-   **Google Colab**: Cloud-based notebook environment for collaborative development.

## Methodology

### 1. Data Loading and Initial Exploration
The `DataCoSupplyChainDataset.csv` was loaded into a Pandas DataFrame. Initial exploration involved:
-   Inspecting the first few rows (`df.head()`).
-   Understanding the dataset's dimensions (`df.shape`).
-   Reviewing data types and non-null counts (`df.info()`).
-   Generating descriptive statistics (`df.describe()`).

### 2. Data Quality Assessment
A thorough data quality report was generated, detailing missing values, their percentages, and data types for each column. A heatmap was utilized to visually represent the distribution of missing data.

### 3. Data Cleaning
-   **Missing Values**: Handled missing values in `Customer Lname` by imputing with the mode. `Customer Zipcode` missing values were filled with the median.
-   **Duplicates**: Identified and removed any duplicate rows in the dataset.

### 4. Feature Engineering
Several new features were engineered to enrich the dataset and capture critical business logic:
-   **`Shipment_Delay`**: Calculated as the difference between `Days for shipping (real)` and `Days for shipment (scheduled)`.
-   **`Delivery_Performance`**: Categorized as 'Delayed' if `Shipment_Delay` > 0, otherwise 'On Time' using `np.where`.
-   **`Profit_Margin_%`**: Computed as `(Benefit per order / Sales per customer) * 100`.
-   **`Order_Value_Category`**: Segmented `Sales per customer` into 'Low', 'Medium', 'High', and 'Premium' categories using `pd.qcut`.
-   **Data Validation**: Checked for logical inconsistencies such as negative sales, zero or negative order item quantities, negative prices, and discount rates outside the [0, 1] range.

### 5. Data Standardization
Key categorical text columns such as `Delivery Status`, `Customer Country`, `Category Name`, `Market`, and `Type` were standardized by converting to string, stripping whitespace, and title-casing for consistency.

### 6. Data Quality Score
A custom data quality score was calculated based on missing values and duplicates, providing a quantifiable measure of data health.

### 7. Key Performance Indicators (KPIs)
Critical business KPIs were derived to provide a snapshot of supply chain performance:
-   **Total Orders**: Number of unique orders.
-   **Total Customers**: Number of unique customers.
-   **Average Sales**: Mean sales per customer.
-   **Average Profit**: Mean benefit per order.
-   **Delayed Orders**: Count of orders with shipment delays.
-   **Late Delivery Risk %**: Percentage of orders at risk of late delivery.

## Results and Insights
-   **High Data Quality**: Achieved a high data quality score of `9836.63`, indicating a robust and clean dataset for further analysis.
-   **Significant Shipment Delays**: Identified `103,400` delayed orders, with a `54.83%` late delivery risk, highlighting a critical area for operational improvement.
-   **Customer Engagement**: A substantial customer base of `20,652` unique customers across `65,752` total orders.
-   **Profitability Metrics**: Average sales per customer of `$183.11` and an average profit per order of `$21.97` provide a baseline for financial performance evaluation.
-   **Enhanced Features**: The engineered features (e.g., `Shipment_Delay`, `Profit_Margin_%`, `Order_Value_Category`) provide a richer context for understanding complex supply chain dynamics and are ready for predictive modeling.

## Discussion and Future Work
The cleaned and engineered dataset, along with the calculated KPIs, offers a powerful foundation for deeper analysis. Future work could include:
-   **Predictive Modeling**: Developing models to predict shipment delays or customer satisfaction based on the engineered features.
-   **Root Cause Analysis**: Investigating the underlying reasons for shipment delays to implement targeted solutions.
-   **Customer Segmentation**: Further segmenting customers based on `Order_Value_Category` and other demographics to tailor marketing and service strategies.
-   **Time-Series Analysis**: Analyzing trends in sales and profit over time to identify seasonality and long-term patterns.
