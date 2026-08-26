# Dataset

The raw dataset is not included in this repository because of its size.

## Source

This project uses the **DataCo Smart Supply Chain for Big Data Analysis** dataset, a public dataset containing approximately 180,000 order-level records from a global supply chain operation.

The dataset includes information about sales, profit, products, customers, markets, countries, shipping modes, and delivery performance.

**Dataset source:**
[Kaggle — DataCo Smart Supply Chain for Big Data Analysis]([https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis](https://www.kaggle.com/datasets/shashwatwork/dataco-smart-supply-chain-for-big-data-analysis))

---

## Setup

To reproduce the analysis:

1. Download the dataset from the Kaggle link above.
2. Download the file named `DataCoSupplyChainDataset.csv`.
3. Place the CSV file inside this `data/` folder.
4. Open the Power BI report.
5. Go to **Home → Transform data → Data source settings**.
6. Update the file path to the location of your downloaded CSV.
7. Click **Refresh**.

> The dataset file itself is not included in this repository.

---

## Fields Used in the Report

| Field                           | Used For                                        |
| ------------------------------- | ----------------------------------------------- |
| `Sales`                         | Total sales and product/country analysis        |
| `Order Profit Per Order`        | Total profit and profit margin                  |
| `Delivery Status`               | Delivery-status analysis and late delivery rate |
| `Days for shipping (real)`      | Average delivery days                           |
| `Days for shipment (scheduled)` | Scheduled delivery comparison                   |
| `Shipping Mode`                 | Late delivery rate by shipping mode             |
| `Market`                        | Market slicer and market-level analysis         |
| `Order Country`                 | Sales map and country drill-through             |
| `Order City`                    | City-level analysis                             |
| `Category Name`                 | Product/category analysis                       |
| `Product Name`                  | Top products and detailed analysis              |
| `Customer Fname`                | Customer-level order details                    |
| `order date (DateOrders)`       | Sales trend and date analysis                   |

---

## Data Preparation

The dataset was cleaned and prepared using **Power Query in Power BI** before being used for the dashboard analysis.

The report uses the prepared data to create measures, visualisations, filters, and drill-through functionality.
