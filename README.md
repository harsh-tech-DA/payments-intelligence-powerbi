
https://github.com/user-attachments/assets/d75bca90-b1a5-4d09-a110-08a2b54b3e8b
# payments-intelligence-powerbi
Description: Enterprise 3-page Power BI dashboard for payment transaction monitoring, rail SLA reliability, and customer risk audit.


---

## 📌 Executive Summary
* **Domain:** Payments Infrastructure, Rail Reliability & Risk Audit
* **Key Metrics:** Total Processing Volume (TPV), Average Latency (ms), SLA Breach Rate (%), Dispute Rate (%)
* **Data Scope:** 15,000+ settlement records modeled across 5 payment rails (UPI, Credit Card, Debit Card, Net Banking, Wallet)

---

##  3-Page Analytical Architecture

# 1. Executive Overview
* Macro KPI scorecard tracking settlement liquidity, fee margins, and dispute volumes.
* Month-over-month TPV trajectory and cross-rail distribution analysis.

# 2. Rail Reliability & SLA Breach Audit
* Dual-axis volume vs. breach ratio isolation to identify partner bank degradation.
* Processing latency tracking against established SLA thresholds.

# 3. Customer Risk & Friction Breakdown
* **Lifecycle Leakage Funnel:** Quantifies conversion drop-off through Success, Failure, and Dispute stages.
* **Rail Risk Scatter Quadrant:** Correlates failure rates with dispute exposure to isolate volatile payment methods.
* **Decomposition Tree:** Drilldown engine identifying dispute root causes across rail, regional corridor, and product tiers.

---

# Data Modeling & Star Schema
The semantic model centers on a normalized star schema:
* **Fact Table:** `Fact_Transactions` (Transaction ID, Latency, Volume, Fees, Status Codes)
* **Dimension Tables:** `Dim_Customer`, `Dim_Payment_Method`, `Dim_Geography`, `Dim_Product`, `Dim_Date`

---

# Core DAX Measures

```dax
// SLA Breach Rate Audit
SLA Breach Rate = 
DIVIDE(
    [SLA Breach Transactions],
    [Total Transactions],
    0
)

// Dynamic Dispute Exposure
Dispute Rate = 
DIVIDE(
    [Dispute Transactions],
    [Total Transactions],
    0
)



