# Excel-Data-Cleaning-and-Transformation
# Data Cleaning and Formatting in Excel

This document outlines the steps taken to clean, standardize, and format a product dataset using Excel / Power Query.

---

## 1) Handling Missing Values

### Missing Price Values
- Checked the **`Price`** column for blank or null values using filters.
- **Handling strategy:**
  - If the product price is critical for analysis → remove the record.
  - If historical or category-level pricing is available → impute using:
    - Average price of the same category
    - Median price to reduce the impact of outliers
  - Clearly document any imputation performed.

### Missing Category Values
- Identified missing values in the **`Category`** column.
- **Imputation strategy:**
  - Assign category based on similar products (same brand or product name).
  - If no reliable inference is possible, label as **`Unknown`**.
  - Avoid deleting rows unless the category is mandatory for analysis.

---

## 2) Correcting Inconsistent Data

### Product Name Inconsistencies
Identified issues such as:
- Mixed letter cases (e.g., `iphone`, `IPHONE`, `iPhone`)
- Extra spaces before or after text
- Inconsistent naming formats

**Actions taken:**
- Used **Find & Replace** to standardize naming.
- Applied `TRIM()` to remove extra spaces.
- Converted text to Proper Case where required.

### Category Typos
Common issues found:
- Misspellings (e.g., `Electroncs`, `Electornics`)
- Inconsistent naming styles

**Fix applied:**
- Used **Find & Replace** to correct spelling.
- Standardized all category names to a single format.

---

## 3) Removing Duplicates

- Checked for duplicate rows based on **all columns**.
- Used **Data → Remove Duplicates**.
- Retained the first occurrence and removed exact duplicates to maintain data integrity.

---

## 4) Splitting and Merging Data

### Splitting Product ID
- Split the **`Product ID`** column into:
  - **Manufacturing Date**
  - **Country Code**
- Used:
  - **Text to Columns** or **Power Query Split Column**
- Removed unnecessary symbols or separators.

### Merging Brand and Product Name
- Merged **`Brand Name`** and **`Product Name`** into a new column:
  - **`Product Brand`**
- Used:
  ```excel
  =BrandName & " " & ProductName

## 5) Number Formatting

### Price Column Formatting
- Converted the **`Price`** column data type to **Currency** format.
- Ensured consistent decimal places for better readability.
- This helps standardize monetary values across the dataset.

### Manufacturing Date Formatting
- Converted the **`Manufacturing Date`** column to **Date** data type.
- Applied a custom date format.

## 6) Conditional Formatting

### Price Column
- Applied **Data Bars / Color Scales** conditional formatting to the **`Price`** column.
- This visually represents price variations and helps quickly identify higher and lower values.

### Category Column
- Created a **custom conditional formatting rule** for the **`Category`** column.
- Highlighted cells where the category value is **` Electronics`**.
- Used a distinct fill color to make Electronics products easily recognizable.
