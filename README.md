# Manhattan Real Estate Sales Analysis

An analysis of Manhattan property sales using Excel, SQL, and Tableau to look at neighborhood sales activity and how prices differ by neighborhood and building type.

**Project status:** In progress (Phase 1 of 3)

## Questions

1. Which Manhattan neighborhoods have the highest number of recorded property sales?
2. How do sale prices and price per square foot differ across neighborhoods and building types?

## Why It Matters

Sales volume and pricing patterns show where real estate activity is concentrated and how different property types compare. Real estate firms, property managers, and investors use this kind of analysis to guide market research, pricing decisions, and where to focus resources.

## Dataset

- **Source:** [NYC Department of Finance: Rolling Sales Data](https://www.nyc.gov/site/finance/taxes/property-rolling-sales-data.page)
- **Area:** Manhattan, New York City
- **Reporting period:** October 1, 2025 to September 30, 2026
- **Raw records:** 19,615
- **Cleaned records:** To be updated after Phase 1
- **Data downloaded:** November 6, 2026
- **File format:** Excel (.xlsx)

The data includes addresses, neighborhoods, building types, sale prices, sale dates, property sizes, and construction years.

## Tools

| Tool | Purpose |
|---|---|
| Microsoft Excel | Data cleaning, quality checks, and initial exploration |
| SQL | Querying sales data and identifying patterns |
| Tableau | Interactive dashboard and maps |

## Workflow

### Phase 1: Excel Data Cleaning and Exploration (in progress)

- Reviewing all 19,615 records.
- Documenting missing values and data-quality issues.
- Checking for duplicates and inconsistent formatting.
- Investigating $0 transactions and identifying records that may not reflect market-value sales.
- Reviewing missing property information by building class.

### Phase 2: SQL Analysis (upcoming)

- Sales volume by neighborhood
- Average and median sale price by neighborhood
- Sales patterns by building type
- Price per square foot for records with a valid price and size

### Phase 3: Tableau Dashboard (upcoming)

- Calculating sales volume by neighborhood.
- Comparing average and median sale prices by neighborhood.
- Examining sales patterns by building type.
- Calculating price per square foot for records with valid sale prices and reported property sizes.

## Key Findings

Coming soon. Findings will be added here as each phase is completed.

## Limitations

- The dataset covers recorded property sales during a 12-month period and does not represent the entire real estate market.
- $0 transactions and certain non-market transfers may not reflect typical market-value sales and will be evaluated before inclusion in price comparisons.
- Some records are missing square footage, so price per square foot will use a smaller set of records than the full dataset.

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
