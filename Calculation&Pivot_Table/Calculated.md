# Housing Market Data Analysis

This document outlines the data preparation steps and the analytical pivot tables created for the Data Visualization and Analytics assignment.

## 1. Data Preparation
Before creating any pivot tables, the dataset underwent a rigorous cleaning and preparation process to ensure accuracy and reliability.

*   **Data Cleaning:** The dataset was fully cleaned, ensuring no duplicate entries and no missing values.
*   **Data Validation:** Numerical columns were verified to be stored as true numeric data types to allow for mathematical operations.
*   **Helper Columns:** The following analytical columns were created to facilitate deeper insights:
    *   **Renovation Status:** Categorized homes based on renovation year.
    *   **Price per Sqft:** Calculated as `Sale Price / Living Area`.
    *   **Living Area Size Bins:** Grouped properties into size ranges (e.g., 0–1000, 1000–2000, etc.).
    *   **Time Period:** Extracted Year and Month from the Sale Date.

---

## 2. Pivot Tables & Analysis

### 2.1 Overall Market Metrics
*   **Purpose:** Provides a high-level summary of the housing market scale.
*   **Calculations:**
    *   **Count of Sale Price:** Represents the total number of transactions.
    *   **Average Sale Price:** The mean price of properties.
    *   **Median Sale Price:** The middle value of property prices.
*   **Insight:** Helps in understanding the general pricing level and market volume.

### 2.2 Waterfront Price Comparison
*   **Rows:** Waterfront (`Yes` / `No`)
*   **Values:** Average Sale Price
*   **Insight:** Highlights the premium associated with waterfront locations and evaluates the geographical value-add.

### 2.3 Price by House Condition
*   **Rows:** House Condition (Rating)
*   **Values:** Average Sale Price
*   **Insight:** Demonstrates how property maintenance influences final valuation.

### 2.4 Size Impact on Price (Living Area Bins)
*   **Rows:** Living Area Bin (0–1000, 1000–2000, 2000–3000, 3000–4000, 4000+ sqft)
*   **Values:** Average Sale Price, Count of Properties
*   **Insight:** Shows the scaling relationship between house size and selling price.

### 2.5 Renovation Impact Analysis
*   **Logic:** `=IF(renovation_year>0,"Renovated","Not Renovated")`
*   **Rows:** Renovation Status
*   **Values:** Average Sale Price, Count of Houses
*   **Insight:** Evaluates the ROI of renovations and identifies potential investment opportunities in older, non-renovated homes.

### 2.6 Price per Sqft by Zipcode
*   **Logic:** `=sale_price / living_area_sqft`
*   **Rows:** Zipcode
*   **Values:** Average Price per Sqft
*   **Insight:** Enables location-based comparison to identify premium vs. undervalued neighborhoods.

### 2.7 Time Trend Analysis
*   **Rows:** Year / Month (derived from Sale Date)
*   **Values:** Average Sale Price
*   **Insight:** Identifies market trends, appreciation patterns, or seasonal declines in housing prices.

---

## 3. Key Insights
The analytical steps above enabled the identification of several critical market drivers:
1.  **Location Premium:** Significant valuation increase for waterfront properties.
2.  **Size Correlation:** A strong positive relationship between living area and sale price.
3.  **Value Addition:** Renovation acts as a major factor in increasing property value.
4.  **Strategic Targeting:** Zipcode-level metrics guide targeted real estate investments.
5.  **Market Direction:** Time-based trends provide a clear view of market health and direction.
