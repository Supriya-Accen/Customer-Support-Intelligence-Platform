
# Feature Engineering for SLA Breach Prediction

## Purpose
This document describes the feature engineering process used to prepare training data for the SLA breach prediction model.  
Features are derived from **Silver-layer tables** and enriched through joins, aggregations, and temporal transformations to capture customer behavior, agent context, and operational conditions.

---

## Source Tables

Features are constructed by joining the following Silver-layer datasets:

- `tickets` – core ticket attributes and timestamps
- `silver_customers` – customer segment, region, MRR, and VIP flag
- `silver_agents` – agent team, region, and seniority
- `silver_policies` – SLA response and resolution targets
- `silver_comments` – ticket-level comment activity and sentiment

---

## Label Definition

The target variable is defined as:

- `label_breach` = 1 if the ticket breached SLA resolution time  
- `label_breach` = 0 otherwise

This label is derived from the `breach_resolution` field and cast to an integer for binary classification.

---

## Aggregated & Derived Features

### Customer-Level Features
- **Customer Ticket Volume**
  - Total number of tickets raised by a customer
  - Acts as a proxy for customer engagement and issue frequency

### Comment-Level Features
- **Average Sentiment**
  - Mean sentiment score of all comments on a ticket
- **Comment Count**
  - Total number of comments per ticket
  - Captures interaction intensity and potential complexity

Missing sentiment or comment values are filled with zero.

---

## Temporal Features

Features derived from the ticket creation timestamp include:

- `created_hour` – hour of ticket creation (0–23)
- `created_dow` – day of week (Monday = 1)
- `is_weekend` – binary indicator for weekend creation

These features help capture operational workload patterns and off-hours behavior.

---

## SLA & Operational Features

- `first_response_hours` – SLA-defined response target
- `resolution_hours` – SLA-defined resolution target
- Both fields are explicitly cast to integers for modeling consistency

---

## Categorical Features

The following categorical attributes are used and later encoded:

- Priority
- Channel
- Customer Segment
- Customer Region
- Agent Team
- Agent Seniority

---

## Numeric Features

Numeric inputs supplied directly to the model include:

- Monthly Recurring Revenue (MRR)
- VIP indicator
- Temporal features (hour, weekend)
- Comment sentiment and count
- SLA targets
- Customer total ticket count

---

## Feature Preparation Summary

All categorical features are indexed and one-hot encoded, while numeric features are standardized.  
This combination ensures the Logistic Regression model receives normalized and appropriately encoded inputs, supporting stable training and interpretability.

---

## Implementation Reference

📓 **Implementation notebook/script:**  
[/Breach_model.ipynb](/Breach_model.ipynb])

This file contains the full feature assembly, transformations, and pipeline construction logic.
