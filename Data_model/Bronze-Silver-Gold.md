
# Bronze → Silver Data Transformation

## Purpose
The Silver layer represents clean, standardized, and analytics‑ready data derived from raw sources in the Bronze layer.  
The goal of this step is to **improve data quality, enforce consistent schemas, and prepare data for downstream modeling, machine learning, and reporting**.

---

## Source Data (Bronze Layer)

Raw data is ingested into the Bronze layer from simulated Zendesk‑style support systems:

- Tickets (raw ticket metadata and timestamps)
- Customers (customer attributes and segments)
- Agents (agent and team information)
- Comments (ticket conversations and activity)
- SLA Policies (response and resolution targets)
- Ticket Events (JSON‑based event logs)

These datasets are stored in OneLake as CSV and JSON files without transformations.

---

## Key Transformations Performed

The following transformations are applied when moving data from Bronze to Silver:

- Removed duplicate records using primary identifiers (e.g., TicketId)
- Standardized timestamp columns and normalized to a common time zone
- Cleaned categorical fields such as priority, channel, and status
- Parsed nested JSON structures into structured columns
- Removed invalid or test tickets
- Handled missing values for non‑critical attributes
- Ensured consistent data types across all tables

---

## Data Quality Validation

Basic data quality checks are performed to ensure reliability:

- Verified uniqueness of primary keys after cleaning
- Ensured mandatory fields are not null (TicketId, CreatedAt, Priority)
- Validated SLA timestamps fall within expected ranges
- Checked referential integrity between tickets, customers, and agents

---

## Silver Layer Outputs

The Silver layer produces cleaned and conformed tables:

- `silver_tickets`
- `silver_customers`
- `silver_agents`
- `silver_comments`
- `silver_sla_policies`
- `silver_ticket_events`

These tables serve as the foundation for Gold‑layer modeling and machine learning feature engineering.

---


# Silver → Gold Data Modeling

## Purpose
The Gold layer represents **business‑ready, analytics‑optimized data models** designed for reporting, aggregation, and machine learning.

It applies dimensional modeling principles to the cleaned Silver tables to enable efficient querying and intuitive reporting in Power BI.

---

## Modeling Approach

A **star schema** approach is used in the Gold layer to separate facts from dimensions:

- Fact tables capture measurable events (tickets, SLA outcomes)
- Dimension tables provide descriptive context (customers, agents, time, channels)

This structure improves:
- Query performance
- Metric consistency
- Report usability

---

## Fact Tables

Key fact tables created in the Gold layer include:

- `fact_tickets`
  - One row per ticket
  - Measures: ticket count, response time, resolution time
- `fact_sla`
  - SLA compliance and breach indicators
  - SLA response and resolution metrics

---

## Dimension Tables

Supporting dimension tables include:

- `dim_customer`
- `dim_agent`
- `dim_date`
- `dim_channel`
- `dim_priority`

Dimensions are created by joining and deduplicating Silver tables and are enriched with business attributes such as customer segment, agent team, and time hierarchies.

---

## Machine Learning Readiness

The Gold layer is designed to support machine learning use cases:

- Features such as priority, channel, segment, agent workload, and response times are materialized
- Data is structured to support supervised learning
- Class imbalance considerations are handled during model training (via SMOTE)

---

## Consumption

The Gold tables are consumed by:

- Power BI semantic models and dashboards
- Machine learning pipelines for SLA breach prediction
- KQL‑based monitoring (where applicable through event joins)

---

## Implementation Reference

Gold‑layer transformations are implemented in the following script:

[Data_model/Bronze-Silver-Gold.ipynb](Data_model/Bronze-Silver-Gold.ipynb)

This script produces the star‑schema tables used across analytics and ML workflows.

