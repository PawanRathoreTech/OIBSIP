# Exploratory Data Analysis (EDA) on Retail Sales Data

## Project Overview

This project focuses on performing Exploratory Data Analysis (EDA) on a retail sales dataset to understand sales performance, customer demographics, product category performance, and relationships between numerical variables.

The analysis was completed using Python in Jupyter Notebook as part of the **Oasis Infobyte Data Analytics Internship**.

The objective is to identify meaningful patterns and insights from the available retail transaction data and provide data-driven recommendations that can help improve business performance.

## Project Objectives

The main objectives of this project are:

* Inspect and understand the retail sales dataset.
* Check for missing values and duplicate records.
* Perform descriptive statistical analysis.
* Analyze sales trends over monthly and quarterly periods.
* Explore customer demographics by gender and age group.
* Evaluate revenue and quantity across product categories.
* Examine correlations between numerical variables.
* Create visualizations to communicate key findings.
* Provide actionable business recommendations based on the analysis.

## Dataset Description

The dataset used in this project is `retail_sales_dataset.csv`, obtained from Kaggle.

It contains **1,000 records and 9 original columns**.

| Column           | Description                            |
| ---------------- | -------------------------------------- |
| Transaction ID   | Unique identifier for each transaction |
| Date             | Date of the transaction                |
| Customer ID      | Identifier of the customer             |
| Gender           | Gender of the customer                 |
| Age              | Age of the customer                    |
| Product Category | Category of the purchased product      |
| Quantity         | Number of units purchased              |
| Price per Unit   | Price of one unit                      |
| Total Amount     | Total transaction amount               |

### Data Preparation

The following preparation steps were performed:

* Inspected the dataset structure, column names, and data types.
* Checked for missing values.
* Checked for duplicate records.
* Converted the `Date` column to datetime format.
* Created an `Age Group` column to group customers by age.
* Extracted `Month` and `Quarter` from the transaction date for time-based analysis.

No missing values or duplicate records were identified during the initial data-quality checks.

## Tools and Libraries

The project was completed using:

* **Python**
* **Jupyter Notebook**
* **Pandas** — data manipulation and analysis
* **NumPy** — numerical operations
* **Matplotlib** — data visualization

## Exploratory Data Analysis

### 1. Initial Data Inspection

The dataset was inspected to understand its dimensions, column names, data types, and general structure.

Missing-value and duplicate checks were performed to assess data quality before analysis.

### 2. Descriptive Statistics

Descriptive statistics were calculated for numerical columns, including:

* Mean
* Median
* Mode
* Standard deviation
* Minimum and maximum values
* Quartiles

These statistics helped summarize transaction values, customer ages, quantities, and unit prices.

### 3. Product Category Revenue Analysis

A bar chart was created to compare total revenue across the available product categories.

This analysis helps identify which product categories contribute more to overall sales and which categories may require additional attention.

### 4. Customer Demographic Analysis

Customer demographics were explored using gender and age-group analysis.

Visualizations were created to compare transaction counts and revenue across:

* Gender
* Age groups

These comparisons help describe the customer segments represented in the dataset.

### 5. Monthly Sales Trend

A line chart was created to examine sales performance over time at the monthly level.

The monthly trend helps identify changes in sales across the observed period.

**Data consideration:** January 2024 contains only a partial month of data. Therefore, it should not be directly compared with complete months without considering the difference in the observation period.

### 6. Quarterly Sales Trend

A quarterly sales line chart was created to examine broader sales patterns.

The first quarter of 2024 is a partial period in the dataset. This limitation should be considered when interpreting the quarterly trend.

### 7. Correlation Analysis

A correlation heatmap was created to examine relationships between numerical variables.

Key observations:

* `Price per Unit` and `Total Amount` show a strong positive correlation of approximately **0.85**.
* `Quantity` and `Total Amount` show a positive correlation of approximately **0.37**.
* `Age` and `Total Amount` show a very weak negative correlation of approximately **-0.06**.
* `Transaction ID` is an identifier and its correlation values do not provide meaningful business insights.

Correlation indicates association between variables; it does not establish causation.

### 8. Additional Visualizations

Two additional visualizations were created to explore category-level purchasing behavior.

#### Average Transaction Amount by Category

The average transaction amount was compared across product categories.

| Product Category | Average Transaction Amount |
| ---------------- | -------------------------: |
| Beauty           |                    ₹467.48 |
| Electronics      |                    ₹458.79 |
| Clothing         |                    ₹443.25 |

Beauty has the highest average transaction amount among the categories shown, followed by Electronics and Clothing.

#### Quantity Sold by Category

The total quantity sold was compared across product categories.

| Product Category | Quantity Sold |
| ---------------- | ------------: |
| Clothing         |           894 |
| Electronics      |           849 |
| Beauty           |           771 |

Clothing has the highest quantity sold in the dataset, followed by Electronics and Beauty.

## Key Findings

The analysis produced the following observations:

1. The dataset contains 1,000 retail transaction records and 9 original columns.
2. No missing values or duplicate records were found during the initial checks.
3. Product category revenue was compared to understand category-level sales contribution.
4. Customer transactions and revenue were explored by gender and age group.
5. Monthly and quarterly sales trends were visualized to examine changes over time.
6. January 2024 and the first quarter of 2024 are partial periods and require cautious interpretation.
7. Price per Unit has a strong positive correlation with Total Amount, while Quantity has a moderate positive correlation.
8. Age has a very weak relationship with Total Amount in the observed data.
9. Beauty has the highest average transaction amount among the categories analyzed.
10. Clothing has the highest total quantity sold among the categories analyzed.

## Business Recommendations

Based on the analysis, the following recommendations can be considered:

1. **Review category-level sales performance:** Use category revenue results to identify strong-performing and weaker-performing categories. Allocate promotions and inventory based on actual category performance.

2. **Improve category-specific marketing:** Consider targeted promotions for categories with lower revenue or purchasing activity, while monitoring whether campaigns improve sales.

3. **Use customer segmentation carefully:** Gender and age-group analysis can help describe customer segments. Use these insights to test targeted campaigns rather than assuming that demographic patterns directly cause purchasing behavior.

4. **Monitor sales trends over time:** Continue tracking monthly and quarterly sales to identify changes in performance. Compare complete periods wherever possible to avoid misleading conclusions from partial periods.

5. **Review average transaction amount and quantity together:** Beauty has the highest average transaction amount, while Clothing has the highest quantity sold. Consider both revenue-related and volume-related metrics when evaluating category performance.

## Limitations

* The dataset contains product categories but does not include individual product names. Therefore, an analysis of the **top 10 individual products** cannot be performed using the available columns.
* January 2024 and the first quarter of 2024 are partial periods, which limits direct comparisons with complete periods.
* The analysis is based only on the available dataset. It does not include additional information such as inventory, marketing spend, profit margin, or customer purchase history.
* Correlation results describe relationships in the dataset and do not establish causal relationships.

## Project Files

The GitHub project folder contains:

* `Retail_Sales_EDA.ipynb` — Jupyter Notebook containing the analysis, code, visualizations, and Markdown observations.
* `retail_sales_dataset.csv` — original dataset used for the analysis.
* Chart image files — visual outputs from the analysis.
* `README.md` — project documentation.

## How to Run the Project

1. Clone or download this repository.

2. Ensure Python and Jupyter Notebook are installed.

3. Install the required libraries:

   ```bash
   pip install pandas numpy matplotlib
   ```

4. Open `Retail_Sales_EDA.ipynb` in Jupyter Notebook.

5. Ensure `retail_sales_dataset.csv` is available at the file path used in the notebook.

6. Run the notebook cells in sequence.

## Conclusion

This project demonstrates how exploratory data analysis can be used to inspect retail transaction data, summarize customer and category-level behavior, visualize sales trends, and examine relationships between numerical variables.

The analysis highlights differences in category-level average transaction amounts and quantities sold, while also identifying limitations related to partial time periods and the absence of individual product names.

The findings provide a starting point for further retail sales analysis and data-driven business decision-making.

---

**Project:** EDA on Retail Sales Data
**Internship:** Oasis Infobyte Data Analytics Internship
**Tools:** Python, Pandas, NumPy, Matplotlib, Jupyter Notebook
