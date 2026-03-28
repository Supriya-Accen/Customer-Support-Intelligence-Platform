
# Architecture Overview

## Purpose
This document describes the end-to-end architecture of the **Customer Support Intelligence Platform** built on **Microsoft Fabric**.  
The architecture supports **historical analytics**, **machine-learning-based risk prediction**, and **near–real-time operational monitoring**.

---

## High-Level Architecture

The solution is built using a **Medallion Architecture (Bronze → Silver → Gold)** on OneLake, with specialized engines for analytics, ML, and real-time workloads.
---

## Data Layers

### Bronze Layer
- Stores raw, immutable source data
- Includes structured and semi-structured data
- No transformations applied

### Silver Layer
- Applies cleansing, standardization, and validation
- Normalizes timestamps and categorical fields
- Produces analytics-ready tables

### Gold Layer
- Implements star-schema modeling
- Separates facts and dimensions
- Optimized for Power BI and ML feature consumption

---

## Analytics & Processing Engines

- **Fabric Warehouse** – batch analytics and semantic modeling
- **Machine Learning (Spark ML)** – SLA breach risk prediction
- **KQL Database** – real-time event analytics
- **Power BI** – unified reporting and visualization layer

---

## Summary
This architecture enables a unified analytics platform that supports:
- Strategic decision-making (historical BI)
- Predictive insights (ML risk scoring)
- Operational awareness (real-time monitoring)

The design emphasizes scalability, clarity, and separation of concerns.
