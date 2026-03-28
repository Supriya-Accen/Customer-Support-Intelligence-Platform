
# Power BI Report Pages – Snapshot Summary

This document summarizes each Power BI dashboard page based on the final rendered views captured in the repository screenshots. The focus is on **what each page shows** 
and **how the insights should be interpreted**.

---

## 1. Executive Summary

This page provides a high-level view of overall customer support health and workload trends.

**What it shows:**
- Total ticket volume (~12K tickets)
- Overall SLA breach rate (~5.4%)
- Average First Response Time (~4.6 hours)
- Average Time to Resolution (~15.2 hours)

**Key insights:**
- Ticket volume trends over time (created vs. resolved)
- Ticket distribution by priority and channel
- SLA breach trends by product
- Higher resolution times observed for lower-priority tickets
---


## 2. Customer Insights & Cohort Analysis

This page focuses on customer behavior, segmentation, and retention patterns.

**What it shows:**
- Average tickets per customer (≈ 8)
- VIP ticket volume (~830 tickets)
- Average monthly recurring revenue (≈ 661)
- Cohort retention heatmap by customer onboarding month

**Key insights:**
- Retention patterns vary significantly by cohort
- SMB customers generate the highest ticket volume
- Enterprise customers generate fewer tickets but higher revenue
- Higher MRR segments tend to have higher support engagement

---

## 3. Trends & Forecast

This page analyzes historical demand patterns and forecasts future ticket volume.

**What it shows:**
- Tickets in the last 30 days (~652)
- Rolling 3‑month ticket volume (~2030)
- Month‑over‑month ticket growth (~5%)

**Key insights:**
- Ticket demand follows a clear lifecycle curve
- Weekday distribution shows slightly higher ticket creation mid‑week
- Hour‑of‑day heatmap reveals peak support hours during business times
- Forecasted trend suggests demand tapering after the current peak

---

## 4. SLA & Operational Performance

This page evaluates SLA compliance and breach behavior across operations.

**What it shows:**
- SLA breach rate (~5.4%)
- SLA compliance (~94.6%)
- Avg. First Response Time for breached tickets (~7 hrs)
- Avg. Resolution Time for breached tickets (~15.2 hrs)

**Key insights:**
- SLA breaches fluctuate month over month
- Certain products show consistently higher breach rates
- Higher ticket volume segments also show higher breach exposure
- SLA performance degradation is more visible during demand peaks

---

## 5. Agent Performance Dashboard

This page measures agent efficiency, workload distribution, and service quality.

**What it shows:**
- Average agent TTR (~15.2 hours)
- Average tickets handled per agent (~100)
- Overall First Contact Resolution (~86%)

**Key insights:**
- Wide variance in SLA breach % across agents
- High-performing agents maintain lower TTR with similar workload
- Regional comparison highlights trade-offs between FCR and SLA breach %
- Some agents handle consistently higher daily ticket volumes

---

## 6. ML & Risk Insights

This page presents predictive insights using machine‑learning‑based risk scoring.

**What it shows:**
- Number of high‑risk tickets (6)
- P95 SLA breach risk (~0.47)
- VIP at‑risk tickets (4)
- Ranked ticket list by predicted breach probability

**Key insights:**
- Risk distribution is heavily skewed (most tickets are low risk)
- Percentile metrics (P90/P95) better capture tail‑risk severity
- Technical and L2 teams show higher tail‑risk exposure
- Email and Chat channels dominate high‑risk ticket volume

---

## 7. Live Operations (KQL)

This page provides near‑real‑time operational monitoring powered by KQL.

**What it shows:**
- Hour‑of‑day ticket inflow patterns by channel
- Ticket volume distribution across channels
- Channel‑level surge analysis using historical baselines

**Key insights:**
- Ticket creation follows distinct hourly patterns
- No single channel dominates volume consistently
- Surge ratio highlights channels with abnormal demand spikes
- Calendar‑aware baselines prevent inflated surge signals

---

## Summary

Together, these dashboards integrate:
- **Historical analytics** (Warehouse & Gold layer)
- **Predictive risk insights** (ML scoring)
- **Real‑time monitoring** (KQL functions)

The result is a unified support analytics platform enabling both **strategic decision‑making** and **operational response**.

