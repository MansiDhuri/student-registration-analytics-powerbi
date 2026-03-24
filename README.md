🎓 Student Event Registration Analytics Dashboard

Power BI | DAX | Star Schema | Education Domain

📌 Project Overview

An end-to-end Power BI dashboard built to track student event registration performance across 5 Indian cities for an education consultancy.
The dashboard provides insights into:
Registration trends
Event capacity utilization
Email campaign effectiveness

📊 Dashboard Pages

| Page                  | Description                                              |
| --------------------- | -------------------------------------------------------- |
| **Executive Summary** | KPI cards, regional breakdown, monthly trends            |
| **Event Performance** | Capacity vs confirmed registrations, event type analysis |
| **Email Campaign**    | Funnel analysis, open rate, CTR by event                 |

📈 Key Metrics Tracked

Total Registrations: 2,841 across 24 events
Confirmation Rate, Attendance Rate, Cancellation Rate
Month-over-Month Growth %
Email Open Rate & Click-Through Rate (CTR)
Regional Share % & Capacity Fill Rate %

🛠️ Tools & Technologies

Power BI Desktop — Dashboard development & visualizations
DAX — 15+ custom measures
Power Query (M) — Data cleaning & transformation
Star Schema — Data modeling (Fact + Dimensions)
Excel — Source data (synthetic dataset)

🗂️ Data Model

Designed using a Star Schema approach:
Fact_Registrations (2,841 rows)
Dim_Events (24 rows)
Dim_EmailCampaigns (24 rows)
Dim_Date (366 rows — generated using custom M code)

📸 Screenshots


📐 DAX Measures

All DAX measures are documented here:
👉 dax/all_measures.md

👤 Author

Mansi Dhuri
