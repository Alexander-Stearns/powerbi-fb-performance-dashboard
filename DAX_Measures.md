
# Selected DAX Measures

This Power BI project contains 14 DAX measures supporting financial and operational performance analysis across six simulated food & beverage locations.

The examples below demonstrate reusable measures, financial variance calculations, safe division, and productivity analysis.

## 1. Revenue Variance %

```dax
Revenue Variance % =
DIVIDE([Revenue Variance], [Budget Revenue])
```

**Business purpose:** Measures how actual revenue performs against budget as a percentage.

The calculation uses reusable base measures, allowing results to respond to the dashboard's date and location filters.

## 2. Labor Cost %

```dax
Labor Cost % =
DIVIDE([Total Labor Cost], [Total Revenue])
```

**Business purpose:** Measures labor spending as a percentage of revenue.

This KPI helps identify locations where labor costs are relatively high compared with sales performance.

## 3. Budget Transactions per Labor Hour

```dax
Budget Transactions per Labor Hour =
DIVIDE(
    [Budget Transactions],
    SUM(Budget[BudgetLaborHours])
)
```

**Business purpose:** Establishes the planned transaction productivity benchmark using budgeted transactions and budgeted labor hours.

This measure can be compared with actual transactions per labor hour to evaluate operational productivity against expectations.

## Supporting Measures

These calculations reference foundational measures defined elsewhere in the Power BI model.

```dax
Total Revenue =
SUM(Actuals[Revenue])

Budget Revenue =
SUM(Budget[BudgetRevenue])

Revenue Variance =
[Total Revenue] - [Budget Revenue]

Total Labor Cost =
SUM(Actuals[LaborCost])

Budget Transactions =
SUM(Budget[BudgetTransactions])

Total Transactions =
SUM(Actuals[Transactions])

Total Labor Hours =
SUM(Actuals[LaborHours])

Transactions per Labor Hour =
DIVIDE([Total Transactions], [Total Labor Hours])
```

## Technical Notes

- Used reusable DAX measures to keep financial calculations consistent.
- Used `DIVIDE()` to handle zero-denominator cases safely.
- Kept actual and budget data in separate fact tables connected to shared date and location dimensions.
- Designed measures to respond to report filter context, including date and location selections.

All 14 measures and the complete relational data model are available in the Power BI project file (`.pbix`).

**Data disclaimer:** All financial and operational data in this project is simulated.
