Credit Card Analysis - Power BI Project 📊💳

----Overview
This Power BI project provides an in-depth analysis of credit card transactions, customer demographics, and spending behaviors. The dashboard enables stakeholders to understand revenue trends, customer segments, and key financial insights.

----Data Insights:
Quarterly Revenue and Transactions 📈
Revenue remains stable across quarters, with minor fluctuations.
Total transactions also exhibit consistency, peaking in Q3.

----Revenue by Expense Type 💸
Top spending categories: Bills, Entertainment, and Fuel.
Significant contributors: Travel and Food.

----Revenue by Education Level 🎓
Highest revenue: Graduates, followed by High School graduates.
Lower revenue: Individuals with Doctorate and Post-Graduate degrees.

----Revenue by Card Category 💳
Highest revenue: Blue cards (~46M), followed by Silver, Gold, and Platinum.
High transaction value per user: Platinum cards.

----Transaction Type Usage 🏦
Dominant: Swipe transactions (34.91M), followed by Chip (16.97M) and Online (3.44M).
Lower volume: Online transactions.

----Revenue by Age Group 👥
Highest revenue: 40-50 age group (~10.76M), followed by 50-60 (8.68M).
Least revenue: Younger groups (20-30).

------Revenue by Income Group 💰
Highest revenue: High-income groups (29.23M), followed by Medium (15.85M) and Low (10.23M).

-----Revenue by Job Type 💼
Highest contributors: Businessmen and White-Collar workers.
Significant contributors: Self-employed and Government employees.

-----Revenue by State 🗺️
Highest spending: Texas (TX), New York (NY), and California (CA).
Following behind: Florida (FL) and New Jersey (NJ).

------Revenue vs. Interest Earned 💵
Total Revenue: 55.32M
Total Transaction Amount: 45M
Total Interest Earned: 7.84M
Additional Dashboard Insights
The project consists of two pages in the Power BI dashboard:

-----Overview Dashboard: Provides a high-level summary of revenue trends, spending behaviors, and customer demographics.
Detailed Analysis Page: Offers in-depth insights into specific metrics, such as revenue trends by time period, customer segmentation, and transaction patterns.



----DAX Queries Used
Several DAX (Data Analysis Expressions) queries were implemented to enhance the analysis:

###############Age Group Classification
AgeGroup = SWITCH( TRUE(), 
    'public cust_detail'[customer_age] < 30, "20-30", 
    'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40", 
    'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50", 
    'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60", 
    'public cust_detail'[customer_age] >= 60, "60+", 
    "unknown" )

    
#################Income Group Classification
IncomeGroup = SWITCH( TRUE(), 
    'public cust_detail'[income] < 35000, "Low", 
    'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] < 70000, "Med", 
    'public cust_detail'[income] >= 70000, "High", 
    "unknown" )

    
##########Revenue Calculation
Revenue = 'public cc_detail'[annual_fees] + 
          'public cc_detail'[total_trans_amt] + 
          'public cc_detail'[interest_earned]

          
#############Weekly Revenue Analysis
week_num2 = WEEKNUM('public cc_detail'[week_start_date])

Current_week_Reveneue = CALCULATE( 
    SUM('public cc_detail'[Revenue]), 
    FILTER( ALL('public cc_detail'), 
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2]) 
    )
)

Previous_week_Reveneue = CALCULATE( 
    SUM('public cc_detail'[Revenue]), 
    FILTER( ALL('public cc_detail'), 
        'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1 
    )
)


Key Findings 🔍
Swipe transactions dominate, indicating a strong preference for physical transactions.
Blue category cards have the highest market penetration and revenue.
Higher-income groups and Business professionals generate the majority of the revenue.
Older customers (40-60 age range) have the highest spending behavior.
Texas and New York dominate in terms of spending patterns.
Tools Used 🛠️
Power BI for data visualization
PostgreSQL (Database connection for raw data processing)




Next Steps 🚀
Improve online transaction adoption to increase digital revenue.
Target younger users with rewards to boost spending in the 20-30 age group.
Customize card offerings for high-spending customer segments.
How to Use This Project
Open Power BI Desktop.
Load the dataset into Power BI (via PostgreSQL or Excel source).
Explore the different dashboards for insights.
Use filters to analyze specific timeframes, customer segments, or transaction types.


Author
Srijon Das
