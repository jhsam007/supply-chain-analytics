#  Supply Chain Analytics & Demand Forecasting

**Author:** Hasan Jahid  
GitHub: https://github.com/jhsam007  
Dashboard: https://public.tableau.com/app/profile/jahid.hasan3683/viz/Supply_Chain_Analytics_Dashboard/SupplyChainPerformanceDashboard  

---

## 1. Executive Summary

This report presents an end-to-end analysis of supply chain operations using three years of transactional data (January 2015 – January 2018), covering approximately 180,000 orders across multiple product categories and regions.

The analysis reveals four key findings:

- **Strong seasonality:** Demand peaks consistently in Q4, reaching approximately **2.3× the monthly baseline**, creating both opportunity and inventory risk.
- **Revenue concentration:** The **top three product categories generate ~65% of total revenue**, exposing the business to concentration risk.
- **Operational inefficiency:** Over **54% of Standard Class shipments are delivered late**, indicating execution issues rather than planning problems.
- **Accurate forecasting:** A Prophet-based model achieves **1.59% SMAPE**, enabling reliable short-term demand predictions.

Based on these findings, recommendations focus on optimizing shipping strategies, improving inventory planning, and reducing reliance on a narrow set of high-performing products.

---

## 2. Business Problem

Modern supply chains face multiple operational challenges:

| Challenge | Business Impact |
|----------|----------------|
| Shipment delays | Customer dissatisfaction and churn risk |
| Inefficient shipping methods | Increased costs and delivery failures |
| Uneven demand | Stockouts and excess inventory |
| Regional bottlenecks | Reduced service quality and revenue loss |

A key assumption was that delays were caused by poor planning. However, analysis shows that **execution inefficiencies—not scheduling—are the primary driver of delays**.

---

## 3. Dataset & Preprocessing

### 3.1 Dataset Overview

| Property | Detail |
|---------|--------|
| Source | DataCo Smart Supply Chain Dataset |
| Records | ~180,000 orders |
| Time Range | Jan 2015 – Jan 2018 |
| Key Fields | Orders, shipping, products, regions, delivery metrics |
| Output Format | Parquet |

### 3.2 Data Preparation

The dataset was cleaned and prepared through the following steps:

- Handled missing values using appropriate strategies  
- Removed duplicate records  
- Converted date fields for time-based analysis  
- Created key features:
  - `days_late` (actual vs scheduled delivery)
  - `is_late` (binary delay indicator)  
- Exported optimized dataset in Parquet format  

The cleaned data was also stored in a SQLite database for structured querying.

---

## 4. Exploratory Data Analysis

### 4.1 Demand & Seasonality

Demand shows a consistent seasonal pattern:
- Growth begins in September  
- Peaks in Q4 (Oct–Dec)  
- Declines sharply in January  

Q4 demand reaches approximately **2.3× normal levels**, requiring proactive inventory planning.

---

### 4.2 Product & Revenue Concentration

- Top 3 categories → ~65% of revenue  
- Top 10 products → 60–70% of sales  

This concentration increases vulnerability to supply disruptions.

Profitability varies across categories, indicating that revenue alone is not sufficient for decision-making.

---

### 4.3 Shipping Performance

- **Standard Class:** >54% late deliveries  
- **First Class:** ~34% lower delay rate  

Shipping method is the strongest driver of delays.

Regional analysis shows persistent delay hotspots, indicating logistics bottlenecks.

---

### 4.4 Delay Distribution

- Delays are right-skewed  
- ~5% of orders are delayed by 4+ days  

These extreme delays have a disproportionate impact on customer experience.

---

### 4.5 Revenue Impact

Delays do not immediately reduce revenue. However:

- Reduced customer satisfaction  
- Lower repeat purchases  
- Increased churn  

The impact is long-term rather than immediate.

---

## 5. Dashboard

An interactive dashboard was developed to monitor supply chain performance.

### Key Components

- KPIs: Total Revenue, Total Orders, Late Delivery %
- Monthly order trends (seasonality)
- Category-wise revenue distribution
- Regional order distribution
- Shipping performance (late delivery rate by mode)

### Interactivity

Filters allow dynamic analysis by:
- Category  
- Shipping Mode  
- Region  

This enables users to drill down into specific segments and identify bottlenecks.

View Dashboard:  
https://public.tableau.com/app/profile/jahid.hasan3683/viz/Supply_Chain_Analytics_Dashboard/SupplyChainPerformanceDashboard

---

## 6. Demand Forecasting

### 6.1 Methodology

A forecasting model was built using Prophet, capturing:
- Trend  
- Weekly seasonality  
- Annual seasonality  

---

### 6.2 Model Performance

| Metric | Value |
|--------|------|
| MAE | 40.40 |
| RMSE | 44.02 |
| SMAPE | 1.59% |

With average demand around 2400–2600 units, error is less than 2%, indicating strong performance.

---

### 6.3 Forecast Insights

- Slight demand decline expected over next 90 days  
- Pattern aligns with seasonal normalization  
- Short-term predictions are more reliable  

---

### 6.4 Forecast Limitations

- Cannot capture external disruptions  
- Does not include promotional or weather effects  
- Accuracy decreases over longer horizons  

---

## 7. Key Insights

1. Strong Q4 seasonality (2.3× demand spike)  
2. Revenue concentration (~65%) increases risk  
3. Standard shipping drives majority of delays  
4. Extreme delays (top 5%) create major service issues  
5. Execution—not planning—drives inefficiencies  
6. Delay impact appears in long-term customer behavior  

---

## 8. Business Recommendations

### 1. Optimize Shipping Strategy
- Reduce reliance on Standard Class  
- Prioritize faster shipping for high-value orders  

### 2. Improve Inventory Planning
- Increase stock before Q4  
- Align supply with forecasted demand  

### 3. Reduce Product Concentration Risk
- Invest in mid-tier categories  
- Diversify revenue streams  

### 4. Manage Extreme Delays
- Monitor high-delay cases  
- Implement escalation processes  

### 5. Improve Regional Logistics
- Identify high-delay regions  
- Optimize routing and carrier performance  

---

## 9. Limitations

- No customer satisfaction data  
- No shipping cost data  
- External factors not included  
- Forecast based only on historical patterns  

---

## 10. Conclusion

This analysis shows that significant improvements in supply chain performance can be achieved through data-driven insights.

The most important finding is:

**Execution inefficiencies—not planning failures—are the primary cause of delivery delays.**

By improving shipping strategies, aligning inventory with 
demand patterns, and leveraging forecasting, businesses can 
enhance efficiency, reduce risk, and improve customer 
satisfaction.