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

# 🔍 Key Findings

## 💰 1. Revenue is Dangerously Concentrated in a Small Customer Segment
The top 10 customers by transaction value — out of 500 — account for a disproportionate share of total platform volume. In any payments business, this level of concentration represents a retention risk: losing even two or three of these customers would materially impact monthly revenue.
✅ Recommendation: C-Pay should identify these high-value customers and enrol them in a loyalty or priority service tier — faster transaction processing, dedicated support, or fee waivers on high-value transfers. Protecting this segment is cheaper than replacing it.

## ⚠️ 2. Over a Third of Customers Are at High Churn Risk
The churn risk segmentation reveals that a significant portion of customers have not transacted in over 60 days. Given that C-Pay earns revenue only when customers transact, dormant accounts represent both lost fee income and a risk of permanent exit if a competitor offers an onboarding incentive.
Critically, churn risk is not evenly distributed. Rural districts — where agent liquidity issues are most acute — show higher concentrations of at-risk customers, suggesting that infrastructure failure, not customer disengagement, may be the root cause.
✅ Recommendation: Before launching a generic re-engagement campaign, C-Pay should segment churn by region. Customers in agent-poor districts need an infrastructure fix first — more agents, better liquidity — not a marketing message.

## 📊 3. Send Money and Cash Out Dominate Volume but Bulk Payments Dominate Revenue Per Transaction
Transaction type analysis reveals a clear split between volume leaders and revenue leaders. While Send Money and Cash Out drive the highest number of transactions, Bulk Payments — used by corporates and NGOs to disburse salaries and grants — generate significantly higher fee revenue per transaction despite lower frequency.
✅ Recommendation: C-Pay's B2B sales effort should prioritise onboarding more corporate and government bulk payment clients. A single bulk payment client can generate more fee revenue in one transaction than dozens of individual consumer transactions combined.

## 📡 4. USSD Has the Highest Failed Transaction Volume — but That's Only Half the Story
The failed transaction analysis shows USSD leads in absolute failure counts. However, USSD also handles the highest overall transaction volume, so the raw count is misleading. A more meaningful metric is the failure rate — failed transactions as a percentage of total attempts per channel.

✅ Recommendation: C-Pay's engineering team should be given failure rate targets per channel, not absolute counts. Rate-based monitoring catches degrading performance before it becomes a volume problem.

## 👥 5. Middle-Aged Male Customers Drive the Highest Average Transaction Values — but Women Are the Larger Opportunity
The age and gender segmentation shows middle-aged male customers post the highest average transaction values. However, this finding should be read alongside the broader industry context: women in Southern Africa are 36% less likely to own a mobile money account than men, meaning female customers are underrepresented in the data to begin with.
The lower average transaction value among female customers is likely a reflection of lower account limits tied to KYC status and income levels — not lower intent or capacity.

## 📉 6. Agent Network Growth Has Stalled in the Second Half of 2024
Month-on-month agent registration analysis shows healthy onboarding in early 2023 followed by a deceleration through 2024. Since agents are C-Pay's primary distribution channel in rural areas — and agent liquidity is the most cited barrier to mobile money adoption in Lesotho — a stalling agent network directly constrains customer growth.
✅ Recommendation: C-Pay should review its agent recruitment incentive structure. If the commission model is not attractive enough to sustain agent growth, customer acquisition in underserved districts will plateau regardless of marketing spend.
