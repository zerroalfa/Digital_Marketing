# Digital_Marketing
this is my 4th project with Quantum Analytics

## Table of Contents

- [Project Overview](#project-overview)
- [Data Sources](#data-sources)
- [Recommendations](#recommendations)

### Project Overview
---

**Project Overview:Digital Marketing Campaign Performance Analysis**  

This project focuses on evaluating and optimizing the performance of marketing campaigns using a dataset that provides detailed insights into spending, customer behavior, and revenue generation. The dataset includes information such as campaign details, impressions, clicks, leads, orders, and revenue, allowing for a comprehensive analysis of marketing effectiveness.  

### Objectives:  
1. **Calculate Marketing ROI (ROMI)**: Assess the overall Return on Marketing Investment (ROMI) and evaluate it for individual campaigns to determine profitability.  
2. **Campaign Performance Over Time**: Analyze performance metrics by date to identify trends in spending, revenue generation, and conversion rates, including days with peak activity and average order values.  
3. **Customer Activity Patterns**: Explore buyer activity trends by analyzing revenue patterns on weekdays versus weekends.  
4. **Campaign Type Effectiveness**: Compare the performance of different campaign types (social media, banners, influencers, and search ads) to identify the most effective strategies.  
5. **Geographic Targeting Insights**: Determine which geo-locations (tier 1 vs. tier 2 cities) yield better marketing results.  

### Key Metrics for Analysis:  
1. **Overall ROMI**: Revenue generated relative to the marketing budget spent.  
2. **ROMI by Campaign**: Detailed profitability analysis for individual campaigns.  
3. **Conversion Metrics**: Evaluate conversion rates at various stages (clicks to leads, leads to orders).  
4. **Date-Wise Performance**: Insights into dates with the highest spending, revenue, and varying conversion rates.  
5. **Average Order Value (AOV)**: Revenue per order, providing insights into customer spending behavior.  
6. **Campaign Type Effectiveness**: Comparative performance analysis of social, banner, influencer, and search campaigns.  

### Value of the Analysis:  
This project provides actionable insights for:  
- **Marketers**: To refine campaign strategies, allocate budgets effectively, and focus on high-performing channels and regions.  
- **Business Stakeholders**: Offering data-driven recommendations for maximizing ROI and improving customer acquisition strategies.  
- **Data Enthusiasts**: An opportunity to explore and visualize marketing performance metrics to uncover key trends and insights.  

### Potential Use Cases:  
1. **Campaign Optimization**: Identify underperforming campaigns and reallocate resources to more effective channels.  
2. **Time-Based Targeting**: Align marketing efforts with peak buyer activity times (e.g., weekdays vs. weekends).  
3. **Geographic Focus**: Tailor campaigns for tier 1 or tier 2 cities based on ROI and engagement.  
4. **Performance Dashboards**: Build interactive dashboards to monitor campaign performance in real-time.  
5. **Strategic Planning**: Use insights to plan future campaigns that are more likely to generate higher returns.  

This project will help evaluate the effectiveness of past marketing efforts and provide strategic insights to optimize future campaigns, driving better customer engagement and maximizing revenue.
![Dashboard]![4 Digital Marketing](https://github.com/user-attachments/assets/a37c3371-94a4-49c6-ac97-2dd22de2c697)



### Data Sources

Digital Marketing dataset: The primary dataset used for this analysis is the "Marketing.csv" file, containing detailed information about Airplane Crashes and Fatalities.

### Tools

- Excel - Data Cleaning
  - [Download here](https://microsoft.com)
- SQL Server - Data Analysis
- PowerBI - Creating reports


### Data Cleaning/Preparation

In the initial data preparation phase, we performed the following tasks:
1. Data loading and inspection.
2. Handling missing values.
3. Data cleaning and formatting.

### Exploratory Data Analysis

EDA involved exploring the sales data to answer key questions, such as:

- What is the overall sales trend?
- Which products are top sellers?
- What are the peak sales periods?

### Data Analysis

Include some interesting code/features worked with



**Cost Efficiency Metrics** 
-- Interpretation Guideline: A cost efficiency value greater than 1 indicates a profitable campaign, as revenue exceeds the marketing spend. Values below 1 suggest inefficiency.
```sql
SELECT campaign_name, SUM(revenue) / SUM(mark_spent) AS cost_efficiency
FROM Marketing
GROUP BY campaign_name;
```
**ROMI (Return on Marketing Investment) by Campaign**
-- Interpretation Guideline: A ROMI value greater than 0 indicates a positive return on marketing investment. Generally, a ROMI above 1 is considered strong, while negative values suggest underperformance.
```sql
SELECT campaign_name, (SUM(revenue) - SUM(mark_spent)) / SUM(mark_spent) AS ROMI
FROM Marketing
GROUP BY campaign_name;
```
**Conversion Rates**
```sql
SELECT campaign_name, (SUM(leads) * 1.0 / SUM(clicks)) AS conversion_rate
FROM Marketing
GROUP BY campaign_name;
```
**Click Through Rate (CTR)**
```sql
SELECT campaign_name, (SUM(clicks) * 1.0 / SUM(impressions)) AS CTR
FROM Marketing
GROUP BY campaign_name;
```
**Weekday vs. Weekend Revenue**
-- Interpretation Guideline: In the WEEKDAY function, 0 represents Monday and 6 represents Sunday.

```sql
SELECT CASE WHEN WEEKDAY(c_date) IN (5,6) THEN 'Weekend' ELSE 'Weekday' END AS day_type,
       SUM(revenue) AS total_revenue
FROM Marketing
GROUP BY day_type;
```
**Performance by Date**
```sql
SELECT c_date, SUM(revenue) AS total_revenue, SUM(mark_spent) AS total_spent
FROM Marketing
GROUP BY c_date
ORDER BY c_date;
```

**Overall ROMI**
```sql
SELECT (SUM(revenue) - SUM(mark_spent)) / SUM(mark_spent) AS overall_ROMI
FROM Marketing;
```
**Customer Acquisition Cost (CAC)**
-- Interpretation Guideline: A lower CAC indicates more efficient customer acquisition. Benchmarks vary by industry, but a CAC below the average customer lifetime value (LTV) is generally considered favorable.

```sql
SELECT SUM(mark_spent) / SUM(leads) AS CAC
FROM Marketing;
```
**Total Revenue by Category**
```sql
SELECT category, SUM(revenue) AS total_revenue
FROM Marketing
GROUP BY category;
```
**Cost per Click (CPC)**
```sql
SELECT campaign_name, SUM(mark_spent) / SUM(clicks) AS CPC
FROM Marketing
GROUP BY campaign_name;
```
**Total Clicks**
```sql
SELECT SUM(clicks) AS total_clicks
FROM Marketing;
```
**Cost per Lead (CPL)**
```sql
SELECT campaign_name, SUM(mark_spent) / SUM(leads) AS CPL
FROM Marketing
GROUP BY campaign_name;
```
### Results/Findings

The analysis results are summarized as follows:
1. The company's sales have been steadily increasing over the past year, with a noticeable peak during the holiday season.
2. Product Category A is the best-performing category in terms of sales and revenue.
3. Customer segments with high lifetime value (LTV) should be targeted for marketing efforts.

### Recommendations

Based on the analysis, we recommend the following actions:
- Invest in marketing and promotions during peak sales seasons to maximize revenue.
- Focus on expanding and promoting products in Category A.
- Implement a customer segmentation strategy to target high-LTV customers effectively.

### Limitations

I had to remove all zero values from budget and revenue columns because they would have affected the accuracy of my conclusions from the analysis. There are still a few outliers even after the omissions but even then we can still see that there is a positive correlation between both budget and number of votes with revenue.

### References

`column_1`

**bold**

*italic*
