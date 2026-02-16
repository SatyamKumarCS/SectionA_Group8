# Data Cleaning Documentation

## Overview
The objective was to ensure the dataset is **Complete**, **Consistent**, **Free from missing or duplicate records**, and **Structurally ready for analysis**.

---

## 1. Duplicate Row Verification
### Method Used
Google Sheets menu: **Data → Data cleanup → Remove duplicates**.
Checked across all columns to ensure full-row uniqueness.

### Result
- No duplicate rows were found or removed.
- Dataset integrity remained intact.

---

## 2. Missing Value Identification
Missing values were detected using:
- **Filter view**
- **COUNTBLANK()** function on each column

### Columns Containing Missing Values
| Column Name | Missing Values | Data Type |
| :--- | :--- | :--- |
| No of Bathrooms | 4 | Numeric |
| Flat Area (in Sqft) | 9 | Numeric |
| Lot Area (in Sqft) | 9 | Numeric |
| No of Times Visited | 19,485 | Categorical |
| Area from Basement (Sqft) | 3 | Numeric |
| Zipcode | 1 | Numeric |
| Latitude | 1 | Numeric |
| Longitude | 1 | Numeric |
| Living Area after Renovation | 1 | Numeric |

---

## 3. Numerical Missing Value Imputation
### Strategy
**Median imputation** was applied because:
- Resistant to outliers.
- Suitable for skewed real-estate distributions.
- Common industry practice.

### Google Sheets Implementation
**Median calculation:**
`=MEDIAN(range)`

**Fill missing values:**
`=IF(ISBLANK(cell), median_value, cell)`

### Example Median Values Used
| Column | Median |
| :--- | :--- |
| No of Bathrooms | 2.25 |
| Flat Area (Sqft) | 1910.0 |
| Lot Area (Sqft) | 7619.0 |

### Result
- All numerical columns now contain 0 missing values.

---

## 4. Categorical Missing Value Imputation
### Affected Column
- **No of Times Visited**
- Missing values: 19,485 (~97% of dataset)

### Strategy
**Mode imputation** in Google Sheets.

### Google Sheets Implementation
**Mode calculation:**
`=MODE(range)`

**Replacement:**
`=IF(ISBLANK(cell), "Twice", cell)`

### Result
- Column fully populated.
- 0 missing values remain.

---

## 5. Column Removal Decision
### Dropped Column
- **No of Times Visited**

### Reasoning
- Extremely high missing percentage (~97%).
- Low analytical reliability.
- Mode imputation may introduce bias due to the volume of missing data.
- Explicit project requirement to remove.

### Google Sheets Action
- Selected the column.
- **Right-click → Delete column**.
