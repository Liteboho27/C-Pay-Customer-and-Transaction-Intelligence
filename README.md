# 📱 C-Pay Customer & Transaction Intelligence

Tools Used: MySQL · Microsoft Excel · Power BI

Domain: Fintech · Mobile Money · Financial Inclusion

Country: Lesotho, Southern Africa

# 📌 Background and Business Problem

Chaperone Lesotho operates C-Pay, one of Lesotho's leading mobile money platforms, serving individual consumers, merchants, and SMEs across various districts. Like most mobile money operators in Southern Africa, C-Pay faces pressure on three fronts - growing its active user base, retaining existing customers, and maximising revenue per transaction.
This project simulates the work of a junior data analyst embedded in C-Pay's business intelligence team. Using a dataset of 500 customers, 8,000 transactions, 60 agents, and 24 months of activity, I set out to answer 3 key questions:
- Who are C-Pay's promising customers?
- How do C-Pay customers transact?
- Which customers are at the risk of churning?

# 💡 Key Findings Overview 
- On the customer side, revenue is healthily distributed, the top 10 customers account for just 5.41% of total transaction value but all 10 are individual account holders, exposing a significant gap in commercial account performance despite **Bulk Payments** generating the highest transaction value on the platform at M3.26 million from only 338 transactions.
- On the transaction side, volume and value are decoupled. Send Money dominates in frequency but ranks 4th in value, **Cash Out** is outpacing **Cash In** signalling customers treat C-Pay as a cash collection point rather than a financial ecosystem, and the **App** carries the highest failure rate at **8.54%** despite being the most modern channel.
- On churn, **173 customers are at high risk**, concentrated not in rural underserved districts as expected, but in Maseru, Leribe, and Berea, suggesting urban churn is a competitive and engagement problem that C-Rewards is not currently solving.
- Across all three questions the same theme emerges: C-Pay's consumer foundation is solid, but targeted interventions in corporate client acquisition, App reliability, Cash In incentivisation, and C-Rewards activation represent the clearest path to stronger revenue and retention performance.

# 🗂️ Dataset Overview
Table description 
- cpay_customers (500 rows with columns about customer demographics, region, KYC status)
- cpay_transactions (8,000 rows with columns about transaction type, amount, channel, status)
- cpay_agents (60 rows with data about agent networks across 8 Lesotho districts)
- cpay_monthly_summary (5,338 rows of aggregated monthly activity with churn flags)

**The dataset is simulated and based on publicly available information about Chaperone Lesotho and the broader Lesotho mobile money market. All figures are illustrative.**

# 🛠️ Data Preparation
Before any analysis, the raw CSV files required structural cleanup. Column names contained spaces and inconsistent casing, and data types were stored as generic text rather than typed fields. I used ALTER TABLE ... CHANGE COLUMN statements in MySQL to rename columns to snake_case conventions and assign appropriate data types — VARCHAR for identifiers, DATE for temporal fields, and DECIMAL(10,2) for all monetary values.

# 🔍 Detailed Key Findings

# 💰 1. Revenue is Broadly Distributed, but Individual Accounts Carry Disproportionate Weight
The top 10 customers by transaction value account for only 5.41% of total platform transaction value across 500 customers. This is a sign of a healthy, distributed revenue base, no single customer or small group can destabilise C-Pay's income by leaving. However, a closer look at the data reveals something worth noting; all 10 of C-Pay's highest-value customers are individual account holders, not merchants or SMEs. For a platform that generates higher fee revenue per transaction from B2B clients like bulk payment corporates and merchants, this suggests that C-Pay's business and merchant segments are underperforming relative to their revenue potential. In short, the consumer base is healthy and well distributed, but the commercial segment is not pulling its weight.

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

## 📊 3. Transaction Volume and Value Tell Two Different Stories
Transaction type analysis reveals a clear split between volume leaders and revenue leaders. While Send Money and Cash Out drive the highest number of transactions, Bulk Payments, used by corporates to disburse salaries, generate significantly higher fee revenue per transaction despite lower frequency. Cash Out exceeding Cash In is a platform health warning. C-Pay processed more Cash Out transactions (1,229) than Cash In (1,100). In a healthy mobile money ecosystem, Cash In should equal or exceed Cash Out, money flowing into the platform sustains wallet balances and enables further transactions. When Cash Out consistently outpaces Cash In, it signals that customers are using C-Pay as a cash collection point rather than a financial ecosystem, receiving money and immediately withdrawing it rather than keeping balances on the platform to transact further.

**✅ Recommendationa**
- C-Pay's B2B sales effort should prioritise onboarding more corporate and government bulk payment clients. A single bulk payment client can generate more fee revenue in one transaction than dozens of individual consumer transactions combined.
- C-Pay should investigate what is driving Cash Out dominance. If customers are cashing out immediately after receiving remittances, introducing incentives to keep balances on the platform, such as C-Rewards points for wallet-to-wallet transactions or interest on savings deposits, could shift behaviour and improve platform health.

## 📡 4. USSD Has the Highest Failed Transaction Volume
The failed transaction analysis shows USSD leads in absolute failure counts. However, USSD also handles the highest overall transaction volume, so the raw count is misleading. A more meaningful metric is the failure rate, failed transactions as a percentage of total attempts per channel. The App, C-Pay's most modern and feature-rich channel, has the highest failure rate at 8.54% in comparison to USSD (7.61%) and Agent (7.43%).This finding matters precisely because it defies expectations. USSD is the oldest technology on the platform, dependent on network signal strength, prone to session timeouts, and used predominantly by lower-income customers in areas with weaker connectivity. It would be reasonable to expect USSD to have the worst failure rate. Instead, the App, used by C-Pay's most digitally engaged, typically urban customers, is underperforming both legacy channels on reliability.

**Possible implications for C-Pay**

- App failures are more damaging to retention than USSD failures. App users are C-Pay's highest-value, most commercially attractive segment, urban, smartphone-owning, and with access to competitor platforms. A failed transaction on the App does not just inconvenience a customer, it gives them a reason to open a competitor's app instead. USSD users in rural areas have fewer alternatives; App users do not.
- An 8.54% failure rate means roughly 1 in 12 App transactions fails. Across 2,459 App transactions in the dataset, 210 failed completely. Each failed transaction represents lost revenue, a frustrated customer, and a potential churn trigger, particularly among the urban high-risk customers identified in the churn analysis.
- Agent transactions are the most reliable channel. At 7.43%, Agent-assisted transactions have the lowest failure rate, likely because human agents can troubleshoot in real time, retry failed transactions, and guide customers through the process. This reliability is one of the reasons agent networks remain critical in markets like Lesotho despite the push toward digital self-service.

**✅ Recommendations**
- C-Pay's product and engineering teams should conduct a root cause analysis on App failures — are they payment gateway timeouts, session errors, connectivity drops, or something else?
- Implement real-time failure rate monitoring per channel. Rather than discovering failure trends retrospectively through analysis, C-Pay should set failure rate thresholds per channel, for example, a 5% ceiling — and trigger automated alerts when any channel breaches the threshold. This shifts the team from reactive to proactive on platform reliability.

## 📉 6. Agent Network Growth Has Stalled in the Second Half of 2024
Month-on-month agent registration analysis shows healthy onboarding in early 2023 followed by a deceleration through 2024. Since agents are C-Pay's primary distribution channel in rural areas and agent liquidity is the most cited barrier to mobile money adoption in Lesotho — a stalling agent network directly constrains customer growth.

**✅ Recommendation**

C-Pay should review its agent recruitment incentive structure. If the commission model is not attractive enough to sustain agent growth, customer acquisition in underserved districts will plateau regardless of marketing spend.
