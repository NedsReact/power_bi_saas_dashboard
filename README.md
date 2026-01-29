# Power BI SaaS Analytics Dashboard

![Dashboard Preview](./screenshots/dashboard_overview.png)

## Overview
SaaS subscription analytics dashboard built with Power BI, demonstrating:
- Semantic data modeling (star schema, 5+ tables)
- Advanced DAX measures (MRR, churn rate, LTV, cohort analysis)
- Automated refresh pipelines
- Performance optimization (query folding, aggregations)

## Features
- **KPIs Tracked:** MRR, ARR, Churn Rate, Customer LTV, CAC
- **Data Sources:** SQL Server, REST APIs, CSV imports
- **Refresh:** Automated daily via Power BI Gateway
- **Performance:** Optimized for <2s load time with 100K+ rows

## Tech Stack
- Power BI Desktop & Service
- DAX (50+ measures)
- Power Query (M language)
- SQL Server / T-SQL
- Azure Data Gateway

## Screenshots
### Main Dashboard
![Main View]<img width="3840" height="2063" alt="image" src="https://github.com/user-attachments/assets/4adf7bb1-2cbe-4e56-b0f4-4eca25b7e56b" />


### Data Model
<img width="3840" height="2063" alt="image" src="https://github.com/user-attachments/assets/2665bd65-b394-42bd-90de-ee4fa07b516b" />


## How to Use
1. Download the `.pbix` file
2. Open in Power BI Desktop (free)
3. Refresh data connections (sample data included)
4. Explore the report pages

## Sample DAX Measures
```dax
MRR = 
CALCULATE(
    SUM(Subscriptions[Amount]),
    Subscriptions[Status] = "Active"
)

Churn Rate = 
DIVIDE(
    [Churned Customers],
    [Total Customers],
    0
)
```
<img width="3840" height="2063" alt="image" src="https://github.com/user-attachments/assets/c005751f-de1d-4d06-9886-e7899f14c139" />
