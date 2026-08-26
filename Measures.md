# DAX Measure Reference

> Reference implementations of the measures behind the report's KPI cards and rate visuals.
> Column names follow the raw dataset headers — adjust to match your renamed columns in the model.

## Commercial

```dax
Total Sales =
SUM ( Orders[Sales] )
```

```dax
Total Profit =
SUM ( Orders[Order Profit Per Order] )
```

```dax
Profit Margin =
DIVIDE ( [Total Profit], [Total Sales] )
```
*Format as a percentage with two decimal places.*

```dax
Total Orders =
COUNTROWS ( Orders )
```

## Delivery performance

```dax
Late Orders =
CALCULATE (
    [Total Orders],
    Orders[Delivery Status] = "Late delivery"
)
```

```dax
Late Delivery Rate =
DIVIDE ( [Late Orders], [Total Orders] )
```

```dax
AVG Delivery Days =
AVERAGE ( Orders[Days for shipping (real)] )
```

```dax
AVG Scheduled Days =
AVERAGE ( Orders[Days for shipment (scheduled)] )
```

```dax
Lead Time Variance =
[AVG Delivery Days] - [AVG Scheduled Days]
```
*Not currently on a report page — a useful addition for quantifying how badly each shipping mode's SLA is calibrated.*

## Date table

A marked date table supports the sales trend visual and any future time intelligence:

```dax
Date =
VAR MinDate = MIN ( Orders[order date (DateOrders)] )
VAR MaxDate = MAX ( Orders[order date (DateOrders)] )
RETURN
ADDCOLUMNS (
    CALENDAR ( DATE ( YEAR ( MinDate ), 1, 1 ), DATE ( YEAR ( MaxDate ), 12, 31 ) ),
    "Year",        YEAR ( [Date] ),
    "Month",       FORMAT ( [Date], "MMM" ),
    "Month Number", MONTH ( [Date] ),
    "Quarter",     "Q" & QUARTER ( [Date] ),
    "Year Month",  FORMAT ( [Date], "YYYY-MM" )
)
```

Mark this as the date table (**Table tools → Mark as date table**) and relate `Date[Date]` one-to-many to `Orders[order date (DateOrders)]`.

## Notes on the model

- `Orders` is the fact table at order-line grain.
- Dimension attributes used in the report — `Market`, `Shipping Mode`, `Delivery Status`, `Category Name`, `Product Name`, `Order City`, `Order Country` — are either separate dimension tables or columns on the fact table depending on how the model was shaped.
- The **Country Detail** page is set as a drill-through target on `Order Country`, with a back button in the top-left corner.
