# Oasis Infobyte – Data Analytics Internship

# Task 2: Cleaning Data – California Housing Dataset

## 1. Project Overview

This project focuses on demonstrating data cleaning and preprocessing skills using Python and Pandas.

The objective is to take a deliberately messy California Housing dataset, identify data quality issues, and systematically transform it into a clean, analysis-ready dataset.

The project covers missing value handling, duplicate detection, inconsistent formatting, invalid values, outlier detection, data type correction, and before-versus-after data quality comparison.

## 2. Objective

The main objectives of this project are:

- Inspect the dataset and identify data quality issues.
- Generate a data quality report.
- Handle missing values using appropriate imputation techniques.
- Identify and remove duplicate records if present.
- Standardise inconsistent categorical and numerical formatting.
- Detect outliers using the Interquartile Range (IQR) method.
- Correct invalid values and data types.
- Compare the dataset before and after cleaning.
- Export the cleaned dataset into a new CSV file.

## 3. Technology Stack

The following tools and libraries were used:

| Tool / Library | Purpose |
|---|---|
| Python | Programming language |
| Pandas | Data manipulation and cleaning |
| NumPy | Numerical operations and missing value handling |
| Jupyter Notebook | Code execution and documentation |

## 4. Dataset Information

The project uses a California Housing dataset containing geographical, demographic, and housing-related information.

### Dataset Dimensions

- Total Rows: 20,790
- Total Columns: 11

### Dataset Columns

| Column | Description |
|---|---|
| longitude | Longitude coordinate of the geographical area |
| latitude | Latitude coordinate of the geographical area |
| housing_median_age | Median age of houses in the area |
| total_rooms | Total number of rooms |
| total_bedrooms | Total number of bedrooms |
| population | Total population of the area |
| households | Total number of households |
| median_income | Median income of the area |
| median_house_value | Median house value |
| ocean_proximity | Location category relative to the ocean |
| sale_date | Date associated with the housing record |

## 5. Initial Data Inspection

The dataset was initially inspected using Pandas functions:

- `df.head()` – Displayed the first five records.
- `df.shape` – Checked the number of rows and columns.
- `df.info()` – Inspected column data types and non-null values.
- `df.isnull().sum()` – Identified missing values.
- `df.duplicated().sum()` – Checked duplicate records.

### Initial Findings

- 20,790 records and 11 columns were present.
- 208 missing values were found in `total_bedrooms`.
- No duplicate rows were found.
- `total_rooms` contained inconsistent text formatting.
- `sale_date` was stored as an object instead of a datetime data type.
- Inconsistent formatting was found in the `ocean_proximity` column.
- Invalid negative values were discovered in `housing_median_age`.

## 6. Missing Value Handling

Missing values were identified in the `total_bedrooms` column.

### Treatment

The 208 missing values were filled using median imputation.

**Reason for choosing the median:**

The median is less sensitive to extreme values than the mean. It is therefore a suitable choice for numerical data that may contain outliers.

### Invalid Housing Age Values

During further inspection, 40 negative values were identified in `housing_median_age`.

Negative housing age values are invalid.

**Treatment performed:**

1. Converted negative values into `NaN`.
2. Calculated the median of the valid housing age values.
3. Filled the missing values using the median value of 29.0.

This preserved the original records while correcting invalid values.

## 7. Duplicate Detection and Removal

Duplicate records were checked using:

`df.duplicated().sum()`

### Result

| Stage | Duplicate Rows |
|---|---:|
| Before Cleaning | 0 |
| After Cleaning | 0 |

No duplicate records were found, so no rows were removed.

## 8. Data Standardisation

### A. total_rooms

The `total_rooms` column contained inconsistent text formatting, including the word "rooms" alongside numerical values.

**Treatment:**

- Identified non-numeric text values.
- Removed the unwanted text formatting.
- Converted the column into `float64`.

### B. ocean_proximity

The categorical column contained inconsistent formatting, including uppercase, lowercase, and additional spaces.

**Treatment:**

- Removed leading and trailing spaces.
- Converted category values into uppercase.

### Final Standardised Categories

- `<1H OCEAN`
- `INLAND`
- `NEAR OCEAN`
- `NEAR BAY`
- `ISLAND`

### C. sale_date

The `sale_date` column was originally stored as an object data type.

**Treatment:**

Converted the column into `datetime64[ns]` using Pandas datetime conversion.

This allows proper date-based operations and analysis.

## 9. Outlier Detection and Treatment

Outliers were detected using the Interquartile Range (IQR) method.

### IQR Formula

- Q1 = First Quartile (25th percentile)
- Q3 = Third Quartile (75th percentile)
- IQR = Q3 - Q1

Lower Bound:

`Q1 - 1.5 × IQR`

Upper Bound:

`Q3 + 1.5 × IQR`

Values outside these boundaries were flagged as potential outliers.

### Outlier Detection Results

| Numerical Column | Number of Outliers |
|---|---:|
| longitude | 0 |
| latitude | 0 |
| housing_median_age | 40 |
| total_rooms | 1,294 |
| total_bedrooms | 1,315 |
| population | 1,217 |
| households | 1,227 |
| median_income | 680 |
| median_house_value | 1,074 |

### Outlier Inspection and Treatment Decisions

Outliers were individually inspected to understand whether they represented genuine extreme observations or invalid data.

**housing_median_age:**

Forty negative values were identified. These were treated as invalid values, converted into missing values, and imputed using the median (29.0).

**total_rooms and total_bedrooms:**

High values were inspected alongside population and household counts. These observations could represent large residential areas.

**population and households:**

High population and household counts were inspected. Extreme values were retained because they could represent genuine geographical and demographic variations.

**median_income:**

High-income observations were inspected alongside median house values and ocean proximity. These were retained because high income does not automatically indicate incorrect data.

**median_house_value:**

Several observations had a value of 500001. These may reflect an upper-value cap in the dataset. They were retained rather than removed.

### Final Outlier Treatment Decision

Potentially valid extreme observations were retained.

No blanket outlier deletion or capping was performed because IQR identifies statistical extremes, not necessarily incorrect data.

## 10. Before vs. After Data Quality Comparison

A final comparison was performed to evaluate the effectiveness of the cleaning process.

| Data Quality Metric | Before Cleaning | After Cleaning |
|---|---:|---:|
| Missing Values | 208 | 0 |
| Duplicate Rows | 0 | 0 |
| Total Rows | 20,790 | 20,790 |
| Incorrect Data Types | 2 | 0 |

### Key Improvements

- All missing values were successfully handled.
- No duplicate records were present.
- The original number of records was preserved.
- Inconsistent numerical formatting was corrected.
- Date values were converted into the appropriate datetime format.
- Invalid negative housing age values were corrected.
- Categorical formatting was standardised.

## 11. Final Output

The cleaned dataset was exported into a new CSV file.

**Output File:** `housing_cleaned.csv`

The original dataset was preserved separately for reference and before-versus-after comparison.

## 12. Project Files

The GitHub repository contains the following project files:

| File Name | Description |
|---|---|
| `housing_messy.csv` | Original uncleaned dataset |
| `housing_cleaned.csv` | Final cleaned dataset |
| `housing_cleaned.ipynb` | Jupyter Notebook containing the complete cleaning process |
| `README.md` | Project documentation and explanation |

## 13. Conclusion

The California Housing dataset was successfully processed through a systematic data cleaning workflow.

The project involved identifying missing values, inspecting duplicates, correcting inconsistent formatting, handling invalid values, detecting outliers, and correcting data types.

Median imputation was used to handle missing and invalid numerical values where appropriate. Potentially valid extreme observations were retained to avoid unnecessary information loss.

The final dataset contains 20,790 rows and 11 columns, with zero missing values and corrected data types.

The cleaned CSV file is now ready for further data analysis and exploration.

---

**Project:** Data Cleaning – California Housing Dataset  
**Internship:** Oasis Infobyte Data Analytics  
**Task:** Level 1 – Task 2  
**Tools:** Python, Pandas, NumPy, Jupyter Notebook
