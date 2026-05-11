# 📱 C-Pay Customer & Transaction Intelligence

Tools Used: MySQL · Microsoft Excel · Power BI

Domain: Fintech · Mobile Money · Financial Inclusion

Country: Lesotho, Southern Africa

# 📌 Background

Chaperone Lesotho operates C-Pay, one of Lesotho's leading mobile money platforms, serving individual consumers, merchants, and SMEs across various districts. Like most mobile money operators in Southern Africa, C-Pay faces pressure on three fronts - growing its active user base, retaining existing customers, and maximising revenue per transaction.
This project simulates the work of a junior data analyst embedded in C-Pay's business intelligence team. Using a dataset of 500 customers, 8,000 transactions, 60 agents, and 24 months of activity, I set out to answer 3 key questions:
- Who are C-Pay's promising customers?
- How do C-Pay customers transact?
- Which and how many customers are at the risk of churning?

# 🗂️ Dataset Overview
Table description 
- cpay_customers (500 rows with columns about customer demographics, region, KYC status)
- cpay_transactions (8,000 rows with columns about transaction type, amount, channel, status)
- cpay_agents (60 rows with data about agent networks across 8 Lesotho districts)
- cpay_monthly_summary (5,338 rows of aggregated monthly activity with churn flags)

The dataset is simulated and based on publicly available information about Chaperone Lesotho and the broader Lesotho mobile money market. All figures are illustrative.

# 🛠️ Data Preparation
Before any analysis, the raw CSVs imported from C-Pay's operational systems required structural cleanup. Column names contained spaces and inconsistent casing, and data types were stored as generic text rather than typed fields. I used ALTER TABLE ... CHANGE COLUMN statements in MySQL to rename columns to snake_case conventions and assign appropriate data types — VARCHAR for identifiers, DATE for temporal fields, and DECIMAL(10,2) for all monetary values.



