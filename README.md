# ZyvanaCart Sales & Profitability Investigation
## Project Summary
**ZyvanaCart** is an Indian multi-category e-commerce retailer selling **Clothing**, **Electronics**, and **Furniture**. 
Despite generating healthy gross revenue, the business struggles with a low baseline profit margin of **8.44%** (₹36,963 net profit on ₹4,37,771 sales). 

This project provides an end-to-end data analytics workflow from raw transactional data cleaning to an interactive executive dashboard to isolate the key drivers of revenue loss, analyze sub-category margin leaks, and map geographic/customer concentration.
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





