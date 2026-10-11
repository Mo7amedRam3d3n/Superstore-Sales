# ?? Superstore Sales Analysis | Power BI Dashboard

A single-page Power BI dashboard built on the Superstore dataset to answer one question: **where do profits get lost despite high sales?**

## ??? Data

An Excel file with three sheets:

| Sheet | Contents |
|---|---|
| **Orders** | Order lines: dates, customer, location, product, Sales, Quantity, Discount, Profit |
| **Returns** | Returned orders (`Order ID`, `Returned`) |
| **People** | Regional managers (`Person`, `Region`) |

The data covers the years 2014 to 2017.

## ?? Data Preparation (Power Query)

- Fixed the corrupted `Ship Date` column, which was imported as a long number (for example `1101102016`). The date was rebuilt from its text parts (month, day, year), and the October case was handled separately.

## ?? Data Model

- `People[Region]` ? `Orders[Region]` (one-to-many)
- `Returns[Order ID]` ? `Orders[Order ID]` (one-to-many)

## ?? Measures (DAX)

Total Sales, Total Profit, Profit Margin %, Total Orders, Total Customers, Returned Orders.

`Returned Orders` counts distinct `Order ID` values for orders marked as returned.

## ?? Dashboard Contents

- **KPI cards:** Total Profit, Total Sales, Total Orders, Returned Orders, Profit Margin %, Total Customers
- **Total Sales and Total Profit by Month** (combo chart)
- **Total Profit by Sub-Category** (negative values highlighted)
- **Sales & Profit by Region** (the manager name from the People sheet appears in the tooltip)
- **Discount vs Profit by Sub-Category** (scatter chart)
- **Returned Orders by Category**
- **Year slicer**

## ?? Key Findings

- **Overall:** Sales of 2.3M and profit of 286K, a profit margin of 12%, across 5,009 orders and 793 customers.
- **Seasonality:** Sales peak in September, November and December, and are weakest in January and February.
- **Top profit sources:** Copiers (56K), Phones (45K) and Accessories (42K).
- **Loss-making sub-categories:** Tables (-18K), Bookcases (-3K) and Supplies (-1K). Tables and Bookcases both belong to the Furniture category.
- **Discount impact:** High average discounts are risky for most sub-categories. Tables (about 26% discount) lost 18K, and Machines (about 31%) earned only 3K. This is not a fixed rule, as Binders (about 37%) still earned 30K.
- **Regions:** Central has the lowest margin, about 8% (40K profit on 501K sales), compared with about 12% to 15% for the other regions.
- **Why Central is weaker:** Its average discount is 0.24, compared with 0.11 in West, 0.15 in East and 0.15 in South. In Central, the average discount on Binders (0.51), Appliances (0.45) and Furnishings (0.40) is much higher than their overall averages (0.37, 0.17 and 0.14). These sub-categories are profitable overall but loss-making in Central.
- **Returns:** 296 returned orders out of 5,009 (about 6%), so returns are not the main source of the problem.

## ?? Suggested Next Step

Review the discount policy in the Central region, starting with Binders, Appliances and Furnishings, and review Tables and Bookcases separately.

## ??? Tools

Power BI · Power Query · DAX · Excel
