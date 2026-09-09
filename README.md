# 🚀 Amazon E-Commerce Revenue, Customer & Product Analytics

### Senior Data Analytics Review | Databricks + Spark SQL + Power BI + DAX

<p align="center">
<img src="images/executive_summary.png" width="1000">
</p>

> ⚠️ **Maintenance note:** The screenshots below are from the project's prior dataset version. This README's numbers reflect the current, larger dataset ($761.18M revenue / 120K customers / Databricks pipeline). Replace `executive_summary.png`, `sales_performance.png`, `customer_insights.png`, `product_seller_performance.png`, and add `product_drillthrough.png` with current exports before publishing.

<p align="center">
<img src="https://img.shields.io/badge/Databricks-Spark%20SQL-FF3621?style=flat-square&logo=databricks&logoColor=white">
<img src="https://img.shields.io/badge/Power%20BI-Dashboard-F2C811?style=flat-square&logo=powerbi&logoColor=black">
<img src="https://img.shields.io/badge/DAX-Time%20Intelligence-1F3864?style=flat-square">
<img src="https://img.shields.io/badge/Star%20Schema-Modeling-2E7D32?style=flat-square">
<img src="https://img.shields.io/badge/Framework-What→Why→Action→Risk-1F3864?style=flat-square">
</p>

---

## 🎛️ Dashboard Page Switcher

### 👇 Click any page to jump straight to it

<p align="center">
<a href="#dash-exec"><img src="https://img.shields.io/badge/📊_EXECUTIVE_SUMMARY-1A237E?style=for-the-badge"></a>
<a href="#dash-sales"><img src="https://img.shields.io/badge/📈_SALES_PERFORMANCE-B71C1C?style=for-the-badge"></a>
<a href="#dash-customer"><img src="https://img.shields.io/badge/🧑‍🤝‍🧑_CUSTOMER_INSIGHTS-2E7D32?style=for-the-badge"></a>
<br>
<a href="#dash-product"><img src="https://img.shields.io/badge/🛍️_PRODUCT_%26_SELLER-6A0DAD?style=for-the-badge"></a>
<a href="#dash-ops"><img src="https://img.shields.io/badge/🚚_OPERATIONAL_MATRIX-00796B?style=for-the-badge"></a>
</p>

---

## 📸 Dashboard Preview

<a id="dash-exec"></a>
<details open>
<summary><b>🔹 Executive Summary</b> — p.1</summary>
<p align="center"><img src="images/executive_summary.png" width="1000"></p>
</details>

<a id="dash-sales"></a>
<details>
<summary><b>🔹 Sales Performance</b> — p.2</summary>
<p align="center"><img src="images/sales_performance.png" width="1000"></p>
</details>

<a id="dash-customer"></a>
<details>
<summary><b>🔹 Customer Insights</b> — p.3</summary>
<p align="center"><img src="images/customer_insights.png" width="1000"></p>
</details>

<a id="dash-product"></a>
<details>
<summary><b>🔹 Product & Seller Performance</b> — p.4</summary>
<p align="center"><img src="images/product_seller_performance.png" width="1000"></p>
</details>

<a id="dash-ops"></a>
<details>
<summary><b>🔹 Operational Matrix</b> — p.5 (returns, delivery, brand-level detail)</summary>
<p align="center"><img src="images/product_drillthrough.png" width="1000"></p>
</details>

---

## 📑 Table of Contents

[Dashboard Switcher](#-dashboard-page-switcher) · [Headline KPIs](#-headline-kpi-snapshot) · [Objective](#-business-objective) · [Scope Map](#-analytical-scope-map-why-the-same-metric-shows-three-different-numbers) · [Deep Analysis](#-deep-analysis-whatwhyactionrisk) · [Priority Matrix](#-recommendation-priority-matrix) · [Suggested KPIs](#-suggested-executive-kpis-for-the-next-dashboard-version) · [Author](#-author)

---

## ⚡ Headline KPI Snapshot

| Scope | Net Revenue | Gross Profit | Gross Margin | Orders | AOV | Customers |
|---|---|---|---|---|---|---|
| **2023–2025 Overall** | $761.18M | $117.22M | 15.4% | ≈1.0M | $746.58 | 120K |
| **2025 YTD (Jan–Aug)** | $271.98M | $41.86M | 15.39% | 430K | $745.04 | 117K |
| **August 2025** | $33.77M | $5.19M | 15.38% | 53K | $746.78 | 43K |

*August 2025 vs. prior month: revenue -2.7%, orders -3.6%, AOV +0.5%. August vs. prior year: revenue +16.9%, gross profit +14.6% (margin -0.2pt YoY).*

---

## 🎯 Business Objective

> Understand revenue trend across a $761M, 3-year e-commerce dataset; identify high-performing regions and product categories; analyze customer behavior and retention; and assess discount and delivery performance — while explicitly separating slicer-responsive metrics from intentionally time-independent ones, so executives never mistake a scope difference for a data-quality failure.

**Executive Summary:** The business is scaling strongly with a remarkably stable order-economics profile (AOV within $745–$747 across every time scope). The two priorities that actually matter now are **protecting margin as revenue accelerates** and **making metric scope explicit** — because several headline numbers change dramatically depending on which time window you're looking at, and that difference is routinely mistaken for a business problem.

---

## 🗺️ Analytical Scope Map: Why the Same Metric Shows Three Different Numbers

```mermaid
flowchart TD
    subgraph S1["📅 2023–2025 Overall — YEAR = All"]
        S1A["Net Revenue: $761.18M"]
        S1B["⚠️ Repeat Rate: 99.95%<br/>(lifetime window — not comparable to below)"]
    end

    subgraph S2["📅 2025 YTD — YEAR = 2025"]
        S2A["Net Revenue: $271.98M"]
        S2B["Repeat Rate: 89.80%"]
    end

    subgraph S3["📅 August 2025 — Month = Aug"]
        S3A["Net Revenue: $33.77M ▼2.7% LM · ▲16.9% LY"]
        S3B["⚠️ Repeat Rate: 20.69%<br/>(1-month window — not a retention crash)"]
    end

    classDef warn fill:#fff3cd,stroke:#8a6d00,color:#8a6d00,stroke-width:2px;
    classDef normal fill:#eef2f9,stroke:#1f3864,color:#1f3864;
    class S1B,S3B warn;
    class S1A,S2A,S2B,S3A normal;
