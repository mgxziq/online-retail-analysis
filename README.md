# 🛒 Online Retail Analysis

End-to-end exploratory data analysis of **541,909 transactions** from a UK-based online retailer (Dec 2010 – Dec 2011): data cleaning, sales trends, **RFM customer segmentation**, product analysis, and geographic insights — built with Python.

---

## 📌 Overview

The goal of this project is to turn raw transactional data into actionable business insights. The notebook walks through the full analysis workflow:

1. Loading the data (Excel → CSV caching for faster reloads)
2. Data overview and missing-value inspection
3. Data cleaning
4. Feature engineering
5. Distributions, outliers, and correlations
6. Sales trend analysis (monthly, weekday, hourly)
7. Customer analysis and **RFM segmentation**
8. Product analysis
9. Geographic analysis
10. Summary dashboard and business findings

## 📂 Dataset

| Property | Value |
|----------|-------|
| Source | [UCI Machine Learning Repository — Online Retail](https://archive.ics.uci.edu/dataset/352/online-retail) |
| Rows / Columns | 541,909 / 8 |
| Period | 2010-12-01 → 2011-12-09 |
| Columns | `InvoiceNo`, `StockCode`, `Description`, `Quantity`, `InvoiceDate`, `UnitPrice`, `CustomerID`, `Country` |

> The dataset is not included in this repository. Download `Online Retail.xlsx` from the link above and place it in the project root.

## 🧹 Data Cleaning

| Step | Rows affected |
|------|---------------|
| Cancelled invoices (`InvoiceNo` starts with `C`) | 9,288 |
| `Quantity <= 0` or `UnitPrice <= 0` | removed |
| Missing `CustomerID` (24.9% of raw data) | removed |
| Exact duplicate rows | 5,192 |
| **Final dataset** | **392,692 rows** (27.5% of the raw data removed) |

## 🛠️ Feature Engineering

`TotalRevenue` (Quantity × UnitPrice), `Year`, `Month`, `MonthName`, `YearMonth`, `DayOfWeek`, `Hour`, and `PriceRange` buckets.

## 📊 Key Results

| KPI | Value |
|-----|-------|
| Total revenue | £8,887,208.89 |
| Total orders | 18,532 |
| Unique customers | 4,338 |
| Unique products | 3,665 |
| Average order value | £479.56 |
| Peak revenue month | November 2011 |

### Insights

- **Seasonality:** revenue peaks in November 2011, driven by the pre-holiday season.
- **Market concentration:** the United Kingdom generates **82.0%** of revenue (£7.29M of £8.89M).
- **International markets:** the Netherlands (£285K), EIRE (£265K), Germany (£229K), and France (£209K) lead outside the UK. Note that the Netherlands and EIRE reach these numbers with very few customers (9 and 3), so they reflect a handful of large accounts, while Germany and France are broader markets (94 and 87 customers).
- **Price points:** items priced between £1 and £5 account for most line items and most revenue.
- **Trading patterns:** sales concentrate between 10:00 and 15:00, and Thursday is the strongest day. No transactions are recorded on Saturdays.
- **Customer value:** a small group of top customers contributes a disproportionate share of revenue — a priority for retention programs.

### RFM Segmentation

Each customer is scored from 1 to 4 on **Recency**, **Frequency**, and **Monetary** value (quartiles), and the total score (3–12) is mapped to a segment:

| Segment | Rule | Customers | Share |
|---------|------|-----------|-------|
| Champions | score ≥ 10 | 1,267 | 29.2% |
| Loyal | 7 – 9 | 1,276 | 29.4% |
| Potential | 5 – 6 | 989 | 22.8% |
| At Risk | ≤ 4 | 806 | 18.6% |

## 🚀 Getting Started

```bash
# 1. Clone the repository
git clone https://github.com/<your-username>/online-retail-analysis.git
cd online-retail-analysis

# 2. Install dependencies
pip install -r requirements.txt

# 3. Place "Online Retail.xlsx" in the project root, then launch the notebook
jupyter notebook online_retail_analysis.ipynb
```

**requirements.txt**

```
pandas
numpy
matplotlib
seaborn
openpyxl
jupyter
```

## 📁 Project Structure

```
online-retail-analysis/
├── online_retail_analysis.ipynb   # Full analysis notebook
├── Online Retail.xlsx             # Dataset (download separately)
├── requirements.txt
└── README.md
```

## ⚠️ Limitations

- December 2011 is a partial month (data ends on 9 Dec), so it should not be compared directly with other months.
- About 25% of the raw rows have no `CustomerID` and are excluded, so customer-level results cover identified customers only.
- The RFM thresholds are simple quartile-based rules; they are a practical starting point, not a tuned model.
- A few very large wholesale-style orders heavily influence the top-customer ranking.

## 🔮 Possible Next Steps

- Interactive dashboard in Power BI or Streamlit
- Cohort and retention analysis
- Customer lifetime value (CLV) estimation
- K-Means clustering as an alternative to rule-based RFM
- Market basket analysis (association rules)

## 🧰 Tech Stack

Python · pandas · NumPy · Matplotlib · Seaborn · Jupyter Notebook

---

⭐ If you found this project useful, consider giving it a star.
