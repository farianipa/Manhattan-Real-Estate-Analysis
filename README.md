# Manhattan Real Estate Sales Analysis

This project looks at Manhattan property sales from the NYC Department of Finance, using Excel for cleaning, SQL for analysis, and Tableau for the final dashboard.

**Status:** Phase 1 Complete (Moving to Phase 2: SQL Analysis)

## Questions

1. Which Manhattan neighborhoods have the most recorded property sales?
2. How do sale prices differ by neighborhood and building type? Where can price per square foot actually be calculated?

## Why This Project?

Real estate decisions depend on knowing where sales are happening and what properties actually sell for. Manhattan's public sales data has a lot of gaps that affect which comparisons are fair. I wanted to practice the full process a data analyst would follow: check the data quality first, then analyze sales volume and prices by neighborhood and building type, then present the results in a dashboard.

## Dataset

- **Source:** [NYC Department of Finance Rolling Sales Data](https://www.nyc.gov/site/finance/taxes/property-rolling-sales-data.page)
- **Period:** October 1, 2025 to September 30, 2026
- **Records:** 19,615 raw records, 21 original columns (plus 3 quality indicator flags in `Columns V–X`)
- **Cleaned records:** to be added after Phase 1
- **Downloaded:** November 6, 2026

## Tools

- **Excel:** data cleaning, quality checks, initial exploration
- **SQL:** sales volume and price analysis
- **Tableau:** dashboard

## Progress

### Phase 1: Excel cleaning and exploration (in progress)

The workbook has four sheets: the original data (Manhattan), a Data Quality Log, a Category Summary, and a Missing Sq Ft Analysis.

**Completed steps:**
* Imported all **19,615 records** and confirmed the 21 original columns (`A–U`), correcting the Excel table range to `A1:U19616`.
* Investigated **4 data quality issues** (zero-dollar sales, missing year built, blank/zero gross square footage, and low non-zero sales under \$10,000).
* Checked for exact duplicates across `Columns A–U` (**none found**) and confirmed missing `YEAR BUILT` values are blank cells, not zeros.
* Reviewed key fields (`NEIGHBORHOOD`, `BUILDING CLASS CATEGORY`, `YEAR BUILT`, `SALE PRICE`, and `SALE DATE`) for formatting inconsistencies (**none observed**).
* Added three binary indicator columns outside the main table to preserve raw data while enabling clean SQL filtering:
  * **Column V (Blank Sq Ft):** `=IF(P2="",1,0)` (`1` = blank, `0` = populated)
  * **Column W (Valid Price):** `=IF(T2>0,1,0)` (`1` = > \$0, `0` = \$0 sale)
  * **Column X (Valid Sq Ft):** `=IF(AND(P2<>"",P2>0),1,0)` (`1` = positive value, `0` = blank or zero)
* Built category-level PivotTables comparing property counts and missing square footage across building categories.
* Exported the flagged dataset to `data/cleaned/` for SQL analysis.

### Phase 2: SQL analysis (upcoming)

Sales volume by neighborhood, average and median sale price by neighborhood, sales by building type, and price per square foot for records with a valid price and size.

### Phase 3: Tableau dashboard (upcoming)

A dashboard showing sales volume by neighborhood, price comparisons that can be filtered by building type, and which building types have usable square footage data.

## Preliminary Findings

| Issue | Records | Share of dataset |
|---|---|---|
| $0 sale price | 4,303 | 21.93% |
| Missing year built | 2,007 | 10.23% |
| Missing gross square feet | 17,795 | 90.72% |
| Zero-coded gross square feet | 98 | 0.50% | 
| Non-zero sales under \$10,000 | 220 | 1.12% | 
| Eligible for Price/Sq Ft | 1,263 | 6.44% | 

* **Missing square footage is structural, not random:** In my PivotTable analysis, one-, two-, and three-family dwellings have **0% missing** square footage, while condo and co-op categories (such as *Condos – Elevator Apartments*, *Co-ops – Elevator Apartments*, and *Condo Co-ops*) are **100% missing** gross square footage.
* **Non-market transfers make up over one-fifth of records:** Nearly 22% of rows (`4,303` records) have a `$0` sale price across multiple property types and dates. Because the public dataset does not specify deed transfer reasons, these are flagged and excluded from market price calculations.

*(All details and verification checks are documented in the `Data Quality Log` tab of `excel/manhattan_sales_analysis.xlsx`.)*, download to view). 
More findings will be added as I finish each phase.

![Data Quality Log](visuals/Data_Quality_Log.png)


## Limitations

- The data covers 12 months of recorded sales, so it doesn't represent the whole market and can't support year-over-year trends.
- $0 sales and other non-market transfers may not reflect real market prices. I'll decide how to handle them before comparing prices.
- Price per square foot will only use records with a valid price and square footage, which leaves out most condos and co-ops.
- Building age analysis will only include records that have a year built.

## Repository Structure (planned)

```
Manhattan-Real-Estate-Analysis/
├── README.md
├── data/
│   ├── raw/
│   └── cleaned/
├── excel/
├── sql/
├── tableau/
└── visuals/
```
