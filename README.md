# Retail Sales Data Warehouse

## Overview
An end-to-end Data Warehouse project built using Medallion Architecture 
(Bronze → Silver → Gold) mirroring Azure Synapse Analytics + Azure Data Lake Storage.

## Architecture
## Azure Equivalent Stack
| Local Tool | Azure Equivalent |
|------------|-----------------|
| Python + Pandas | Azure Data Factory |
| Local folders | Azure Data Lake Storage |
| PySpark | Azure Databricks |
| SQL Server | Azure Synapse Analytics |
| Star Schema | Azure Synapse Dedicated Pool |

## Medallion Architecture
- **Bronze Layer** — Raw CSV data ingested from source systems (Customers, Products, Stores, Sales)
- **Silver Layer** — PySpark cleaned and transformed data (nulls removed, types cast, strings trimmed)
- **Gold Layer** — Star Schema dimensional model ready for analytics

## Star Schema Design
   DimDate
          │
DimProduct ───┼─── FactSales ─── DimCustomer

│

DimStore

### Tables
| Table | Type | Rows | Description |
|-------|------|------|-------------|
| DimCustomer | Dimension | 100 | Customer details with surrogate keys |
| DimProduct | Dimension | 50 | Product catalogue with categories |
| DimStore | Dimension | 10 | Store locations and types |
| DimDate | Dimension | 560 | Date dimension with day/month/quarter/year |
| FactSales | Fact | 1000 | Sales transactions with measures |

## Key Business Insights

### Revenue by Category
| Category | Revenue | Units Sold |
|----------|---------|------------|
| Food | ₹6,88,645 | 2,628 |
| Electronics | ₹5,49,411 | 2,263 |
| Clothing | ₹5,02,616 | 2,080 |
| Furniture | ₹4,30,642 | 2,176 |
| Sports | ₹2,40,831 | 915 |

### Top Customer
Customer_51 from Bangalore (Wholesale) — ₹48,416 total spend

### Best Store
Store_5 in Mumbai (Mall) — ₹2,69,475 total revenue

### Weekend vs Weekday
| Day Type | Sales | Revenue |
|----------|-------|---------|
| Weekday | 722 | ₹17,28,184 |
| Weekend | 278 | ₹6,83,963 |

## How to Run
1. Run `warehouse_pipeline.ipynb` to generate Bronze → Silver → Gold layers
2. Import Gold layer CSVs into SQL Server
3. Run analytics queries in `analytics/queries.sql`

## Key Concepts Demonstrated
- Medallion Architecture (Bronze/Silver/Gold)
- Star Schema dimensional modelling
- Surrogate key generation
- PySpark data transformation
- SQL analytical queries
- ETL pipeline design
