
# Key Design Decisions

This document outlines the key architectural and analytical decisions made while building the Customer Support Intelligence Platform.

---

## Why Medallion Architecture?
- Separates raw, curated, and business-ready data
- Improves data quality and auditability
- Enables reuse across analytics and ML workloads

---

## Why Star Schema in the Gold Layer?
- Simplifies Power BI reporting
- Reduces complexity of DAX measures
- Improves query performance and consistency

---

## Why Use Machine Learning?
- SLA breaches are influenced by multiple interacting factors
- Rule-based thresholds are insufficient for prediction
- Logistic Regression provides interpretable risk probabilities

---

## Why Use Percentiles (P90/P95) Instead of Averages?
- Breach risk distributions are highly skewed
- Averages hide extreme but critical cases
- Percentiles better represent tail-risk severity

---

## Why KQL for Live Operations?
- Optimized for event-based, time-series analysis
- Low-latency querying at scale
- Ideal for operational monitoring and anomaly detection

---

## Why Separate Batch Analytics and Real-Time Monitoring?
- Batch analytics prioritize accuracy and history
- Real-time analytics prioritize speed and responsiveness
- Separation avoids overloading one system with conflicting needs

---

## Summary
Each design decision prioritizes clarity, scalability, and alignment with real-world operational use cases rather than purely technical optimization.
