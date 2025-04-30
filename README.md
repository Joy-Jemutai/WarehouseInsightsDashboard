# WarehouseInsightsDashboard
March 2025 Analysis: Fulfillment, Errors and Productivity

Project Overview

This project presents a dynamic Power BI dashboard designed to analyze and optimize warehouse performance. The data spans March 1st to March 31st, 2025, and covers key metrics like fulfillment time, error rates, and employee productivity. Insights drawn from this analysis aim to improve operational efficiency and reduce error occurrences.

Purpose
The dashboard aims to:
- Provide a comprehensive overview of warehouse efficiency.
- Highlight trends in fulfillment, errors, and employee performance.
- Offer actionable recommendations for optimization.

Components
1. SQL Query
The raw data for March 2025 was retrieved using SQL.

SELECT 

    OrderID,                   
    OrderDate,                 
    FulfillmentTime (mins),     
    ErrorType,                  
    ProductCategory,           
    EmployeeID,                 
    EmployeeQualityScore        
FROM 

    warehouse_data               
WHERE 
    
    OrderDate BETWEEN '2025-03-01' AND '2025-03-31'  

2. DAX Queries
Several DAX queries were created to calculate KPIs and generate visuals. Examples include:

Calculated Columns:
- Hour: Extracts the hour from order time for time-based analysis.
Hour = HOUR('fulfillment_data_xls'[Order Time])
- Error Flag: Flags orders with errors (1 for error, 0 for no error).
Error Flag = IF('fulfillment_data_xls'[Error Type] = "None", 0, 1)
- Order Weekday: Converts the order time into a readable weekday format.
Order Weekday = FORMAT([Order Time], "dddd")


Measures:
- Avg Fulfillment (Mins): Calculates the average fulfillment time across all orders.
Avg_Fulfillment (Mins) = AVERAGE('fulfillment_data_xls'[Fulfillment Time (mins)])
- Employee Quality Score (%): Evaluates quality scores for employees as percentages.
Employee Quality Score (%) = AVERAGEX(VALUES('fulfillment_data_xls'[Employee ID]), 100 - [Employee Quality Score])

3. Power BI Dashboard
The Power BI dashboard contains:
- Executive Summary: High-level insights and actionable recommendations.
- Overview: Key KPIs, trends, and comparisons
- Fulfillment Analysis: Trends in average fulfillment times across shifts, teams, and hours.
- Error Insights: Breakdown of error types and rates by category, team, and hour.
- Employee Productivity: Quality score trends and leaderboard of top-performing employees.

4. Excel Raw Data
Raw data was cleaned and structured in Excel before being imported into Power BI. The Excel file is included in the Excel Raw Data folder.

Insights and Recommendations
Key Insights:
- Fulfillment Bottlenecks: Delays during late hours (22nd hour) highlight a need for workload balancing.
- Error Trends: Mis-picks and Label Issues lead error categories, accounting for 60% of errors.
- Employee Productivity: Employees like E025 demonstrate high performance, while E021, E026, and E028 require targeted training.
Recommendations:
- Optimize staffing and workflow during peak error hours (0th hour and 16th hour).
- Implement strategies to address top error types, such as improving labeling processes and reducing mis-picks.
- Provide tailored training for error-prone employees to enhance accuracy.

Contributing
Suggestions and feedback are always welcome! Feel free to open an issue or submit a pull request to contribute to this project.



