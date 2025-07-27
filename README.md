# Trans-Border-Freight-Analysis
This project aims to analyze Bureau of Transportation Statistics (BTS) freight data to assess transport efficiency, safety, and environmental impact, identify patterns and inefficiencies, and suggest improvements for a more sustainable system.

## Methodology
Due to system constraints, particularly limited RAM, chunk-based processing was adopted. This allowed for the analysis of large CSV files without exhausting memory resources.

To determine an efficient way to load the data:
- A sample of 1,000 rows was used to estimate memory usage per row.
- 10% of the system’s available RAM was calculated and divided by the average row size.
- This determined an optimal chunksize for processing data in chunks.

The data structure contained multiple folders from 2020 to 2024, each with subfolders organized by month. A `for` loop was used to iterate through files named using the `dot1_MMYY`, `dot2_MMYY`, and `dot3_MMYY` formats, streamlining the loading and cleaning process while ensuring memory safety.

This analysis follows the CRISP-DM framework:

### 1. Business Understanding
Understand the importance of trade analysis for logistics, economic planning, and decision-making.

### 2. Data Understanding
Load the dataset, examine structure, identify missing values, and explore key columns like `COUNTRY`, `VALUE`, and `COMMODITY2`.

### 3. Data Preparation
- Mapped coded fields to meaningful categories
- Handled missing values
- Converted large values into millions for improved readability

### 4. Modeling / Analysis
Generated descriptive visualizations to explore trade patterns and key contributors.

### 5. Evaluation
Insights were derived based on freight value, shipment weight, and trade value trends over time and across countries and states.

### 6. Deployment / Reporting
All results and charts were saved in a Jupyter notebook and prepared for potential dashboarding using Power BI.

---

## Dataset Overview

- **Source**: CSV files containing U.S. import/export records
- **Rows**: ~935,000 entries
- **Key Columns**:
  - `TRDTYPE`: Trade type (1 = Export, 2 = Import)
  - `USASTATE`: U.S. state of trade
  - `COUNTRY`: Country code for trade partner
  - `COMMODITY2`: 2-digit commodity classification
  - `VALUE`: Monetary value of goods traded
  - `SHIPWT`: Shipment weight
  - `FREIGHT_CHARGES`: Freight cost
  - `YEAR`, `MONTH`: Trade timestamp

---

## Data Cleaning & Preparation

- Mapped numerical and coded fields to meaningful labels:
  - `TRDTYPE`, `DISAGMOT`, `COUNTRY`, and `COMMODITY2` were transformed using dictionaries
- Converted key numerical values to millions and rounded for readability:
  - `VALUE_MILLIONS`
  - `SHIPWT_MILLIONS`
  - `FREIGHT_MILLIONS`

---

## Visualizations Created

1. **Freight Value Over Time**
   - Line chart of freight charges grouped by `YEAR`

2. **Ship Weight by U.S. State**
   - Bar chart of shipment weight grouped by `USASTATE`

3. **Freight Value by Country**
   - Bar chart of freight charges grouped by mapped `COUNTRY` names

4. **Top 10 U.S. States by Trade Value**
   - Bar chart of total `VALUE_MILLIONS` grouped by `USASTATE`

5. **Top 10 Commodities by Freight Value**
   - Bar chart of total `FREIGHT_MILLIONS` by `COMMODITY2`

6. **Freight Value by Country**
   - Bar chart showing freight value distribution across trade partners

---

## Tools & Libraries

- Python 3
- Pandas – data manipulation
- Matplotlib – visualization
- Seaborn – optional styling

---

## File Structure

- `merged_data_output.csv` – cleaned and mapped data
- `project_notebook.ipynb` – code and visualizations
- `README.md` – project summary

---

## Notes

- Scientific notation was avoided by rounding large numeric values to millions.
- Some null values in `COMMODITY2` and `USASTATE` were left unchanged.
- The dashboard created is suitable for Power BI integration.

---

## Future Improvements

- Add interactive filtering (e.g., by trade type, year range)
- Include a correlation matrix for numeric fields
- Export visuals to static images or integrate into Power BI
- Improve environmental impact analysis using external emissions/fuel data
