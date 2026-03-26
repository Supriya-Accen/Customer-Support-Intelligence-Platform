# Customer-Support-Intelligence-Platform
This project demonstrates an end‑to‑end Customer Support Intelligence Platform built using Microsoft Fabric, combining batch analytics, real‑time KQL monitoring, and machine‑learning‑based risk insights.

---
📌 **Overview** 
- The solution enables support and business teams to:
  - Monitor ticket inflow and operational health in near real time
  - Analyze customer behavior and cohort retention
  - Predict and track SLA breach risk
  - Measure agent performance and service quality
  - Gain executive-level visibility into key support KPIs

---

🧱 **Architecture**

- The platform follows a Medallion Architecture on OneLake and integrates multiple Microsoft Fabric workloads.
- External Support Data (Simulated Zendesk)
  1. Tickets
  2. Customers
  3. Agents
  4. Comments
  5. SLA Policies
  6. Ticket Events (JSON)

---

🛠️ **Technology Stack**

- Microsoft Fabric
- OneLake & Lakehouse
- KQL (Real-Time Analytics)
- Power BI
- Fabric Data Warehouse
- Python / SQL (ETL & transformations)
- Machine Learning (Logistic Regression)

---

📊**Power BI Report Pages & Descriptions**

1️⃣ *Executive Summary* : A leadership‑level overview highlighting ticket volume, SLA health, and response efficiency to quickly assess overall customer support performance.

**Insights:**

- Monthly ticket trends
- Ticket distribution by priority and channel
- SLA breach trends across products
- Average FRT and TTR

2️⃣ *Customer Insights & Cohort Analysis*: Analyzes customer engagement, retention, and ticket behavior using cohort analysis and segmentation to connect support demand with revenue impact.

**Insights:**

- Tickets per customer
- VIP ticket count
- Average MRR
- Cohort retention heatmap by customer join month
- Tickets by customer segment (SMB, Mid‑Market, Enterprise)
- MRR vs ticket volume relationship

3️⃣ *Trends & Forecast:* This page focuses on historical trends and near-term forecasting of ticket demand. It helps anticipate workload fluctuations by analyzing rolling volumes, seasonality patterns, and projected ticket lifecycle behavior.

**Insights:**

- Tickets in last 30 days
- Rolling 3‑month volume
- Month‑over‑Month growth %
- Forecasted ticket demand lifecycle
- Ticket distribution by weekday and hour

4️⃣ *SLA & Operational Performance*: This page tracks SLA compliance and breach patterns across products, priorities, and customer segments. It connects operational efficiency metrics with service outcomes, helping teams understand where SLA risks originate and how they evolve over time.

**Insights:**

- SLA Compliance %
- SLA Breach %
- Avg FRT & TTR for breached tickets
- SLA trends over time
- Product‑wise SLA breach distribution
- Segment‑wise ticket volume and revenue.

5️⃣ *Agent Performance Dashboard* : This page evaluates individual agent efficiency and service quality using metrics such as FRT, TTR, FCR, and SLA breaches. It supports performance benchmarking, workload balancing, and identification of coaching opportunities across agents and regions.

**Insights:**

- Avg Agent TTR
- Tickets handled per agent
- First Contact Resolution (FCR %)
- SLA Breach % by agent
- Agent rankings by performance
- Regional SLA vs FCR comparison

6️⃣ *ML & Risk Insights* : This page applies a machine-learning model to predict SLA breach risk at a ticket level and surface operational tail-risk. 

**Insights:**

- SLA breach risk prediction per ticket
- High‑risk ticket identification
- P95 breach risk (tail‑risk severity)
- VIP at‑risk tickets
- Risk distribution by channel and support team

7️⃣ *Live Operations (KQL)* : This page leverages KQL for near-real-time operational monitoring of ticket inflow and channel behavior
Powered by KQL functions built on ticket event data.

**Insights:**

- Ticket inflow by hour of day (pattern analysis)
- Ticket volume by channel
- Channel surge analysis using calendar‑aware baseline averages
- Detection of abnormal demand relative to historical norms

---

🚀 **Outcome**

This project highlights:
- End-to-end analytics design in Microsoft Fabric
- Strong KQL proficiency for real-time monitoring
- Practical ML integration for SLA risk management
- Business-ready Power BI dashboards
- Clear architectural and analytical reasoning

---

📬 Author: 

**Supriya Singh**  
Data Engineer  
Specialization: Microsoft Fabric · KQL · Power BI · Analytics Architecture






