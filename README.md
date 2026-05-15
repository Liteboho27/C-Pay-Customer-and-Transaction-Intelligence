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
Before any analysis, the raw CSV files required structural cleanup. Column names contained spaces and inconsistent casing, and data types were stored as generic text rather than typed fields. I used ALTER TABLE ... CHANGE COLUMN statements in MySQL to rename columns to snake_case conventions and assign appropriate data types — VARCHAR for identifiers, DATE for temporal fields, and DECIMAL(10,2) for all monetary values.

# 🔍 Key Findings

# 💰 1. Revenue is Broadly Distributed, but Individual Accounts Carry Disproportionate Weight
The top 10 customers by transaction value account for only 5.41% of total platform transaction value across 500 customers. Far from being a concentration risk, this is a sign of a healthy, distributed revenue base, no single customer or small group can destabilise C-Pay's income by leaving. However, a closer look at the data reveals something worth noting; all 10 of C-Pay's highest-value customers are individual account holders, not merchants or SMEs. For a platform that generates higher fee revenue per transaction from B2B clients like bulk payment corporates and merchants, this suggests that C-Pay's business and merchant segments are underperforming relative to their revenue potential. In short, the consumer base is healthy and well distributed, but the commercial segment is not pulling its weight.

**✅ Recommendation**

C-Pay should investigate why merchant and SME accounts are not appearing among the top transaction value customers. Are merchants underusing the platform? Are they transacting elsewhere? A targeted merchant activation campaign, combined with incentives for SMEs to process payroll and supplier payments through C-Pay could significantly shift the revenue mix toward higher-margin B2B transactions without needing to grow the customer base at all.

# ⚠️ 2. Churn Risk is Highest in Urban Areas
The churn risk segmentation reveals that 173 customers, roughly 34% of the entire customer base have not transacted in over 60 days and are classified as high risk. The 4 districts with the highest concentrations of at-risk customers are Maseru (51), Leribe (29), Berea (26) and Mafeteng (13), all urban areas. Conventional thinking about mobile money churn in Southern Africa points to rural infrastructure, poor agent liquidity, weak network coverage, and limited access points as the primary driver of inactivity. Yet C-Pay's data tells the opposite story. It is urban customers, with the best access to agents, app connectivity, and C-Pay's own loyalty programme C-Rewards, who are going dormant at the highest rates. C-Pay operates C-Rewards, a loyalty programme where users earn points on everyday transactions, swipes, taps, and transfers, redeemable through a dedicated rewards wallet. In theory, this is precisely the kind of retention mechanism that should keep urban customers engaged between salary cycles. The fact that urban churn remains the highest in the dataset suggests that C-Rewards awareness, accessibility, or perceived value may not be strong enough to influence behaviour.

**Possible reasons urban customers are churning despite C-Rewards**

**🏦 Competitive alternatives**: Urban customers have access to multiple mobile money platforms and traditional banks. If competitors offer more visible or immediately tangible rewards, C-Rewards may not be compelling enough to drive platform loyalty.

**📲 Higher expectations for digital experience**: Urban, app-literate customers are more sensitive to failed transactions, slow processing, and poor UX. A single bad experience in a competitive market is enough to drive them to a rival platform.

**📲 Low C-Rewards awareness or activation**: Customers may simply not know C-Rewards exists or have never activated their rewards wallet. A loyalty programme that is not front-of-mind at the point of transaction offers no retention benefit.

**💸 Salary cycle behaviour**: Urban customers may be using C-Pay purely to receive disbursements and immediately cashing out, with no awareness that those transactions are earning them rewards they could redeem.

**🎯 Rewards threshold too high**: If the points required for meaningful redemption are too high for low-to-mid frequency users, the programme may feel unattainable and fail to motivate continued engagement.

**Implications for C-Pay**

Losing urban customers is significantly more costly than losing rural ones not only because urban customers transact at higher values and frequencies, but because urban churn is visible. A dormant customer in Maseru is almost certainly an active customer on a competitor's platform, taking their transaction volume and word-of-mouth with them. The existence of C-Rewards means the retention infrastructure is already in place, the gap appears to be in activation and communication, not product.

**✅ Recommendation**

C-Pay should audit C-Rewards engagement among its 173 high-risk customers specifically, how many have an active rewards wallet, how many have ever redeemed points, and how many are unaware of the programme entirely. A targeted re-engagement campaign for at-risk urban customers that leads with C-Rewards such as "You have X points waiting — here's what you can do with them", would cost significantly less than new acquisitions and could reactivate a meaningful portion of dormant accounts. The 51 at-risk Maseru customers alone represent a concentrated, high-value target for a pilot campaign.

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
