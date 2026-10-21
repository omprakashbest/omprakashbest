# Customer Churn Analysis

A Python and SQLite project that prepares customer-level subscription data and analyzes churn patterns across plans, locations, and support interactions.

## Project overview

This project combines customer, subscription, and support data from a SQLite database to create an analysis-ready churn dataset. The analysis focuses on churn rate, retention, plan-level churn, monthly charges associated with churned customers, support escalations, and churn-risk segments.

## Key findings

- Overall churn rate: **28.57%** — 6 of 21 customers churned.
- Retention rate: **71.43%**.
- The **Basic** plan had the highest churn rate at **60.00%**, compared with **22.22%** for Standard and **14.29%** for Premium.
- Churned customers accounted for **73.94** in monthly charges within this sample.

> Note: This is a small portfolio dataset. Findings are descriptive and should not be treated as statistically conclusive.

## Tools used

- Python
- Pandas and NumPy
- SQLite
- Matplotlib and Seaborn
- Jupyter Notebook
- Excel

## Data model

The SQLite database contains three related tables joined using `customerid`.

| Table | Description |
| --- | --- |
| `db_customer` | Customer demographics and location details |
| `db_subscription` | Subscription, plan, contract, charges, cancellation, and churn-score data |
| `db_support` | Customer complaints, escalations, and CSAT data |

## Data preparation

The notebook performs the following steps:

- Renames and removes unnecessary columns.
- Standardizes gender values and fills missing country values using state mappings.
- Converts date fields into date format.
- Creates `churn_Flag`, where `1` represents a customer with a cancellation date.
- Counts support complaints and retains the latest support interaction for customers with multiple records.
- Merges the three tables into a customer-level dataset.
- Exports the cleaned dataset as `exported_churn_data.csv`.

## Analysis performed

- Overall churn and retention analysis
- Churn by plan type and state
- Monthly churn trend
- Average revenue per user analysis
- Monthly charges associated with churned customers
- Support escalation and churn relationship analysis
- Customer churn-risk segmentation

## Project structure

```text
.
├── Data/
│   ├── customer_churn.db
│   └── customer_churn_data_raw.xlsx
├── churn_analysis.ipynb
├── exported_churn_data.csv
└── README.md
```

## Visualizations

The notebook includes charts for monthly churn trends, churn by plan type, churn by state, correlation analysis, and customer-risk segments.

View the analysis notebook: [churn_analysis.ipynb](churn_analysis.ipynb)

## Limitations

- The dataset contains only 21 customers, so segment-level findings are directional.
- Churn is defined only by the presence of a cancellation date.
- This project analyzes historical churn patterns; it does not build a machine-learning prediction model.
