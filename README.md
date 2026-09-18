# 🛒 ZyvanaCart — Sales & Profitability Investigation

> **An end-to-end data analytics project isolating revenue loss drivers, sub-category margin leaks, and customer concentration to transform top-line growth into bottom-line profitability.**

---

## 📌 Project Summary

**ZyvanaCart** is an Indian multi-category e-commerce retailer operating across **Clothing**, **Electronics**, and **Furniture**[cite: 12]. Despite generating healthy gross revenue, the platform suffers from an underperforming baseline profit margin of **8.44%** (₹36,963 net profit on ₹4,37,771 sales)

This investigation establishes a complete end-to-end data pipeline—from raw transactional data cleaning to an interactive executive dashboard—designed to:
* **Isolate Key Leakage Drivers**: Pinpoint specific sub-categories dragging down total profitability.
* **Expose Customer Concentration**: Map revenue vs. profit across customer deciles and locate net-loss accounts.
* **Optimize Geographic Footprint**: Evaluate margin performance across states, major metros, and payment channels.
---
## Technical Architecture & Workflow
<img width="953" height="486" alt="image" src="https://github.com/user-attachments/assets/adc53bb7-aa23-4af4-b1aa-e7a4ce058c2f" />

* **Excel**: Initial data exploration, validation, structural reconciliation (`XLOOKUP`), and summary pivots.
* **SQL**: Relational modeling, cross-table aggregation, CTEs, and deep-dive margin leak audits.
* **Python (`pandas`, `seaborn`, `matplotlib`)**: Exploratory Data Analysis (EDA), distribution checks, and customer Pareto segmentation.
* **Frontend Analytics**: Custom interactive HTML/JS dashboard for executive decision-making.

---

## 📊 Dataset Structure & Baseline Metrics

### Schema Overview
* **`Orders` Table** (500 unique records): `Order ID`, `Order Date`, `CustomerName`, `State`, `City`
* **`Details` Table** (1,500 line items): `Order ID`, `Amount`, `Profit`, `Quantity`, `Category`, `Sub-Category`, `PaymentMode`
* **Relational Mapping**: One-to-Many (`Orders[Order ID]` ↔ `Details[Order ID]`)

### Baseline Key Performance Indicators (KPIs)
| Metric | Value |
| :--- | :--- |
| **Total Sales Revenue** | **₹4,37,771** |
| **Total Net Profit** | **₹36,963** |
| **Overall Profit Margin** | **8.44%** |
| **Total Units Sold** | **5,615 units** |
| **Unique Customer Base** | **336 customers** |

---
# AUDIT REPORT USING EXCEL 

## 📋 Sales & Profit Integrity Audit Report (Excel & Data Validation)

To guarantee 100% data fidelity before feeding backend databases or dashboard pipelines, a rigorous **Data Audit & Reconciliation** phase was conducted directly within Excel using structured validation models.

### 1. Data Reconciliation & Reconciliation Metrics
<img width="952" height="790" alt="image" src="https://github.com/user-attachments/assets/8b95ba3f-1658-4cda-86fd-2c8dd8f17ee5" />

* **Full Dataset Certification**: Validated **1,500 line item records** cross-referenced against **500 unique orders** and **336 distinct customers** with zero missing keys or schema mismatches[cite: 11].
* **Reconciled Core Totals**: Certified total baseline sales of **₹4,37,771.00** yielding **₹36,963.00** net profit (**8.44% profit margin**) across 5,615 total units[cite: 11].

### 2. Strategic Category & Regional Breakdown
* **Category Profitability Integrity**: 
  * **Clothing**: Lead margin driver at **9.23%** (₹1,44,323.00 Sales / ₹13,325.00 Profit) across **3,516 units sold**[cite: 11].
  * **Electronics**: Highest gross volume at **₹1,66,267.00 Sales**, but lowest margin efficiency at **7.92%** (₹13,162.00 Profit) across **1,154 units sold**[cite: 11].
  * **Furniture**: Mid-tier revenue at **₹1,27,181.00 Sales** yielding **8.24% margin** (₹10,476.00 Profit) across **945 units sold**[cite: 11].
* **Geographic Concentration**: **Maharashtra** leads top 10 states by sales volume, followed closely by **Uttar Pradesh**, **Rajasthan**, and **Punjab**[cite: 11].
* **Order Footprint by City**: Order volume is heavily anchored in **Indore (71 orders)** and **Chandigarh (67 orders)**, followed by **Delhi (27 orders)** and **Kolkata (22 orders)**[cite: 11].
* **Payment Channel Share**: **Cash on Delivery (COD)** dominates order count at **46%**, followed by **UPI (22%)**, **Debit Card (13%)**, **Credit Card (11%)**, and **EMI (8%)**[cite: 11].

---

## 🔍 Key Analytical Findings

### 1. Revenue vs. Profit Disconnect
* **Loss Traps**: **Electronic Games** generated ₹39,168 in revenue but posted a **-1.64% net margin** (-₹643 profit).
* **Underperforming Powerhouses**: **Phones** (₹48,228 sales, 4.58% margin) and **Chairs** (₹44,223 sales, 3.06% margin) yield disproportionately low profits relative to their sales volume.
* **Volume Paradox**: Unit volume exhibits a weak correlation with profit ($r = 0.20$), proving that high sales volume on unoptimized items actively dilutes overall business margins.

### 2. Profit Concentration & Customer Dynamics
* **Pareto Distribution**: The top 5 sub-categories (**Printers**, **Bookcases**, **Saree**, **Accessories**, and **Tables**) generate **69.45%** of all net profit.
* **VIP Concentration**: The top **10% of customers** drive **39.30% of sales** and **44.86% of total net profit**.
* **Negative-Value Accounts**: 38 customers yield negative net profit over their transaction history despite substantial gross spend (e.g., customer *Shishu* logged a net loss of -₹1,836 across orders).

### 3. Regional & Payment Channel Performance
* **Geographic Leaks**: **Maharashtra** leads all states in total revenue (₹1,02,498) but operates at a sub-par margin of **6.79%**. High-volume metros like **Mumbai**, **Bhopal**, and **Bangalore** represent key low-margin hubs.
* **Payment Channels**: **Credit Card** transactions yield the largest overall profit share (**34.12%**), while **EMI** payments account for the highest Average Order Value (**₹734.73**).

---

## 🚀 Strategic Recommendations

1. **Sub-Category Price & Mix Realignment**: Restructure supplier agreements and discount parameters for **Electronic Games** to restore positive margins. Establish price floors and bundled strategies for **Phones** and **Chairs**.
2. **VIP Retention & Discount Controls**: Focus high-tier loyalty perks on the top-decile customer segment while capping promotional discounts on unprofitable repeat-order accounts.
3. **Logistics & Regional Cost Optimization**: Renegotiate regional fulfillment and shipping tariffs in high-volume, low-margin hubs (**Maharashtra/Mumbai**) to convert existing top-line volume into bottom-line profitability.

---
## 📂 Repository Layout
├── data/

│   ├── List of Orders.csv

│   └── Order Details.csv

├── sql/

│   ├── 01_schema_setup.sql

│   └── 02_profitability_analysis.sql

├── python/

│   └── eda_analysis.ipynb

├── dashboard/

│   └── index.html

# AI AUTOMATED DASHBOARD ( USING JULIUS AI )

## 🖥️ Executive Interactive Dashboard (Julius AI)

To translate complex backend SQL/Python analysis into immediate business visibility, an automated, interactive **Revenue & Profitability Command Center** was engineered using **Julius AI**.

### 1. Executive Overview & Macro KPIs
<img width="1881" height="810" alt="image" src="https://github.com/user-attachments/assets/7c3ec1ec-0032-417c-b951-199a3b5a6939" />
Real-time KPI Tracking: Instant visibility into baseline business health (₹4.37L Revenue, ₹36.9K Net Profit, 8.4% Margin across 5,615 units).
Monthly Revenue & Profit Dynamics: Dual-axis line/bar charts tracking seasonality dips (e.g., negative profit troughs in May/July vs. peak performance in November).
Payment Channel Breakdown: Donut visualization showing channel distribution, highlighting Cash on Delivery (COD) as the primary payment method driving 35.4% of total sales.

### 2. Profitability Diagnostics & Segment Audits
<img width="1846" height="882" alt="image" src="https://github.com/user-attachments/assets/385fb40b-53f2-4e2d-a6c6-18aa9b389b39" />
Sales vs. Profit Scatter Quadrant: Instantly isolates "at-risk" sub-categories generating high sales volume but delivering sub-par or negative net profit margins.
Profitability Watchlist: Automated priority table calling out loss-making sub-categories including Electronic Games (-1.6% margin), Furnishings (-6.0%), and Kurti (-11.9%).
Multi-Dimensional Segmentation: Integrated breakdown showing macro Category performance, Top Revenue States (led by Maharashtra), and VIP Customer Spend distributions.

---
## 📈 Future Profitability & Growth Roadmap

To scale ZyvanaCart sustainably and push net profit margins from **8.44% to a targeted 15%+**, the following strategic levers should be executed across operations, pricing, and customer experience:

---

### 1. Dynamic Pricing & Cross-Sell Engine
* **Automated High-Margin Bundling**: Implement "Frequently Bought Together" prompts at checkout to bundle low-margin items (**Phones**, **Chairs**) with high-margin accessories (**Printers**, **Accessories**) to raise average order basket margin.
* **Smart Free-Shipping Thresholds**: Set dynamic free-shipping tiers 15–20% above the current Average Order Value (AOV) to incentivize customers to add high-margin "filler" products to their cart.

---

### 2. COD Optimization & RTO Loss Reduction
* **Prepaid Incentives**: Cash on Delivery (COD) accounts for **46% of total transactions**. Offer micro-incentives (e.g., flat ₹20 off or 2% instant cashback) for converting to UPI or Credit Card payments[cite: 11].
* **RTO (Return to Origin) Expense Reduction**: Converting orders to prepaid directly minimizes logistics losses from unfulfilled or rejected COD deliveries and speeds up cash flow conversion.

---

### 3. VIP Retention & Unprofitable Account Guardrails
* **High-Decile Loyalty Perks**: Protect the top **10% of customers** who account for **44.86% of total net profit** through exclusive loyalty tiers, priority support, and early access to sales.
* **Margin Guardrails on Repeat Buyers**: Set strict promotional discount caps and minimum order values (MOVs) for accounts with a history of negative net margins to stop profit erosion.

---

### 4. Regional Fulfillment & Inventory Velocity
* **Metropolitan Logistics Optimization**: Re-negotiate last-mile courier rates and inventory placement in **Maharashtra** (leading revenue state at ₹1.02L with a sub-par 6.79% margin) to lower cost-to-serve in high-density hubs.
* **Deadstock Clearance**: Run targeted clearance campaigns on slow-moving, low-margin inventory (**Electronic Games**, **Kurti**) to free up working capital for top profit-generating categories[cite: 11].




