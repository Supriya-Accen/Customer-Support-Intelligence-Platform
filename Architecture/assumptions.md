
# Assumptions & Constraints

This document lists assumptions made during the design and implementation of the Customer Support Intelligence Platform.

---

## Data Assumptions
- Source data is assumed to be complete and correctly formatted
- Ticket IDs uniquely identify tickets
- Event timestamps are reliable and timezone-consistent
- Synthetic data reflects realistic operational patterns

---

## Modeling Assumptions
- SLA breach prediction is framed as a binary classification problem
- Class imbalance exists and influences evaluation metrics
- Probability-based risk scoring is more actionable than binary flags

---

## Operational Assumptions
- Not all tickets will contain comments or sentiment data
- Some days may have no ticket events for certain channels
- Real-time monitoring focuses on pattern detection, not exact counts

---

## Reporting Assumptions
- Power BI users understand high-level KPIs
- Live Operations dashboards are intended for operational users
- ML outputs are interpreted as risk likelihoods, not guarantees

---

## Constraints
- No external alerting or automation included
- No real Zendesk API integration
- Focus is on analytics and observability, not transaction processing

---

## Summary
These assumptions provide context for interpreting metrics and insights and help frame the platform as an analytics and decision-support system rather than a transactional system.
