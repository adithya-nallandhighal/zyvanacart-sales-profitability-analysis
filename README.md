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

# AI AUTOMATED DASHBOARD ( USING JULIUS AI FOR QUICK ANALYSIS & VISUALISATION)

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

# DEEP-DIVE ANALYSIS & DATA VISUALISATION USING POWER-BI 
# Executive Overview : 
<img width="1107" height="627" alt="image" src="https://github.com/user-attachments/assets/5f1abff1-75bc-4db1-bcd9-0c7d01f16601" />

Snapshot: Total Sales ₹437.77K | Total Profit ₹36.963K | Profit Margin 8.44% | 500 Orders | 336 Customers | 5.615K Units Sold

Key Insights:

The business operates on a thin overall margin of 8.44%, meaning ~92% of revenue goes toward costs.
Electronics is the top revenue category at 37.98% (₹166K) of total sales, followed by Furniture (29.05%) and Clothing (32.97%).
Revenue is highly seasonal — January (₹62K) and March (₹61K) are peak months, while July (₹13K) is the weakest, indicating a mid-year dip (April–July).
Recovery begins in August, building to a second peak in November (₹48K).
Madhya Pradesh is the top-performing state by profit (₹7.382K, 19.97% margin), even though it isn't the top state by sales volume.
Clothing is the most profitable category (36.05% profit margin), despite Electronics generating more raw revenue — showing profit and revenue leadership don't align.

# Profitability Diagnostics : 
<img width="1107" height="620" alt="image" src="https://github.com/user-attachments/assets/420b4904-5bb1-4341-890f-fcc335a4ee36" />

Snapshot: Total Profit ₹36.963K | Profit Margin 8.44% | Top Profit Category: Clothing (36.05%) | Lowest Margin Sub-Category: Skirt (-16.19%) | 5 Negative-Profit Sub-Categories

Key Insights:

5 sub-categories are currently unprofitable: Furnishings (-₹0.8K), Electronic Games (-₹0.6K), Kurti (-₹0.4K), Skirt (-₹0.3K), Leggings (-₹0.1K).
Skirt has the worst margin in the entire catalog at -16.19%, despite low sales volume — a strong candidate for repricing or discontinuation.
Clothing contributes disproportionately to profit: 32.97% of sales but 36.05% of profit — the most efficient category.
Electronics, while the top revenue category (37.98%), converts slightly less efficiently into profit (35.61% profit share) — a small but notable efficiency gap.
Furniture underperforms on both fronts: 29.05% of sales and only 28.34% of profit.
At the sub-category level, Printers (₹8,606 profit, 14.52% margin) and T-shirt/Shirt (~20% margins) are the standout performers — small-ticket clothing items are punching above their weight.

# Customer & Geography : 
<img width="1103" height="626" alt="image" src="https://github.com/user-attachments/assets/5efe9489-46bc-4ef4-9e80-9100a4aa0251" />

Snapshot: 336 Unique Customers | Avg Order Value ₹1.30K | Top 10% Customers = 39.30% of Profit | Top Profit State: Madhya Pradesh

Key Insights:

Profit is highly concentrated: the top 10% of customers generate ~39.3% of total profit — a classic Pareto pattern that signals reliance on a small loyal customer base.
Madan Mohan (₹2.2K), Aarushi (₹2.1K), and Shrichand (₹1.9K) are the top individual profit contributors.
Maharashtra leads in raw sales (₹102K) but Madhya Pradesh leads in profit (₹7.4K) — MP's margin efficiency outweighs Maharashtra's higher volume.
Andhra Pradesh (-₹0.3K) and Rajasthan (-₹0.3K) are the only states operating at a loss.
At the city level, Chennai achieves an outstanding 41.46% margin on modest sales (₹6,276) — the most efficient city in the dataset.
Indore delivers the best balance of scale and profitability (₹63,680 sales, ₹6,763 profit, 10.62% margin).
Hyderabad (-2.11%) and Jaipur (-2.44%) are loss-making cities that need investigation despite reasonable sales volumes.

# Payment & Detail : 
<img width="1110" height="631" alt="image" src="https://github.com/user-attachments/assets/dbc6b5c7-fed5-4e4a-b760-145838b81e64" />

Snapshot: Total Sales ₹437.771K | Total Profit ₹37K | Total Quantity Sold 5.615K | Profit Margin 8.44%

Key Insights:

COD (Cash on Delivery) is the most-used payment mode by far (₹155K in sales, ~35% of total), but its profit (₹12.5K) is only marginally ahead of Credit Card.
Credit Card transactions are the most efficient — ₹12.6K profit from just ₹87K in sales (~14.5% margin), far better margin performance than COD.
EMI (₹4.8K profit), Debit Card (₹3.7K), and UPI (₹3.3K) trail significantly in both volume and profit contribution.
At the SKU level, Saree and Hankerchief move the most units (795 and 741 respectively), but Printers and Bookcases deliver far higher profit per unit sold — showing volume and profitability don't move together.
The data reinforces a strategic opportunity: shifting customer payment behavior toward Credit Card (via incentives/cashback) could improve overall margin without needing to grow sales volume.

---
# 📈 Future Profitability & Growth Roadmap

Based on the ZyvanaCart dashboard data (8.44% current margin), here are data-backed strategic levers to push profitability toward a 15%+ target:

# 1. Dynamic Pricing & Cross-Sell Engine
High-Margin Bundling: Bundle low-margin items (Phones — 4.00% margin, Electronic Games — -1.64% margin) with high-margin add-ons (Printers — 14.52%, Accessories — 15.43%, T-shirt — 20.32%) at checkout to lift basket-level margin without discounting.
Smart Free-Shipping Thresholds: Set free-shipping tiers 15–20% above the current Average Order Value (₹1.30K) to nudge customers toward adding high-margin filler items rather than just more low-margin units.

# 2. COD Optimization & Payment Mix Shift
Prepaid Incentives: COD is the largest payment channel by sales value (₹155K, ~35% of total ₹437.77K), yet Credit Card delivers a far better margin profile (₹12.6K profit on just ₹87K sales, ~14.5% margin) vs. COD's ₹12.5K profit on ₹155K sales (~8% margin). Offering small cashback/instant-discount incentives to shift COD customers to Credit Card or UPI directly improves conversion efficiency.
RTO Loss Reduction: Converting COD orders to prepaid reduces return-to-origin logistics costs and improves cash flow timing — a lever not directly visible in the dashboard but a reasonable inference from the payment-mode profit gap.

# 3. VIP Retention & Unprofitable Account Guardrails
High-Decile Loyalty Perks: The top 10% of customers drive 39.30% of total profit (per the Customer & Geography page) — protect this base with loyalty tiers, priority support, and early sale access, since losing even a few of these accounts would disproportionately hurt margin.
Margin Guardrails: Apply discount caps or minimum order values on sub-categories with chronic negative margins — Skirt (-16.19%), Kurti (-11.93%), Leggings (-6.17%), Furnishings (-5.98%), Electronic Games (-1.64%) — to stop active profit erosion on every unit sold.

# 4. Regional Fulfillment & Geographic Focus
Metropolitan Logistics Review: Maharashtra is the top revenue state (₹102K) but its margin (~6.86%) trails the overall average (8.44%) and lags well behind Madhya Pradesh (₹87K sales, 19.97% margin). Reviewing cost-to-serve (logistics, discounting, returns) in Maharashtra could close this gap.
Loss-Making Market Cleanup: Andhra Pradesh and Rajasthan are currently running at a net loss (-₹0.3K each) — audit pricing, discounting, and fulfillment costs in these states before further investment.
City-Level Efficiency Model: Study Chennai (41.46% margin on modest ₹6,276 sales) and Indore (10.62% margin on ₹63,680 sales) as efficiency benchmarks — both outperform larger cities like Hyderabad (-2.11%) and Jaipur (-2.44%), which need root-cause investigation.

# 5. Deadstock & Category Rationalization
Run clearance campaigns on chronically unprofitable sub-categories — Skirt, Kurti, Leggings, Furnishings, Electronic Games — to free up working capital for reinvestment in proven profit drivers like Printers, Bookcases (11.46% margin), and Clothing (36.05% category profit share).
Double down on Clothing, which contributes only 32.97% of sales but 36.05% of profit — the single most profit-efficient category on the dashboard.
