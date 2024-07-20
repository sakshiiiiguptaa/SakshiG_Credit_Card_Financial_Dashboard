# SakshiG_Credit_Card_Financial_Dashboard
Power BI Project showcasing "Transactions by Credit Cards and Details of the Customers"

 🎯 Project Objective: Introducing the "Credit Card Financial Dashboard," designed to provide real-time insights into critical performance metrics and trends in credit card operations. This dashboard empowers stakeholders to monitor and analyze data effectively for informed decision-making. 💳💼

🔍 Data Sourcing from SQL: Harnessing the power of SQL, this dashboard fetches data seamlessly from the SQL database. Automatic updates ensure the dashboard always reflects the latest information, enabling timely and accurate decision-making. 🔄💻

💡 Data Processing with DAX: Robust data processing techniques and DAX queries are implemented to calculate weekly metrics and trends. New columns and calculations streamline data analysis, providing a comprehensive view of credit card performance. 📊✨

The following DAX queries were used in this project to transform the data:


(1)
AgeGroup = SWITCH(
TRUE(),
'public cust_detail'[customer_age] < 30, "20-30",
'public cust_detail'[customer_age] >= 30 && 'public cust_detail'[customer_age] < 40, "30-40",
'public cust_detail'[customer_age] >= 40 && 'public cust_detail'[customer_age] < 50, "40-50",
'public cust_detail'[customer_age] >= 50 && 'public cust_detail'[customer_age] < 60, "50-60",
'public cust_detail'[customer_age] >= 60, "60+",
"unknown"
)
______________________________________________

(2)
IncomeGroup = SWITCH(
TRUE(),
'public cust_detail'[income] < 35000, "Low",
'public cust_detail'[income] >= 35000 && 'public cust_detail'[income] <70000, "Med",
'public cust_detail'[income] >= 70000, "High",
"unknown"
)
__________________________________________________
(3)
week_num2 = WEEKNUM('public cc_detail'[week_start_date])
___________________________________________________
(4)
Revenue = 'public cc_detail'[annual_fees] + 'public cc_detail'[total_trans_amt] + 'public cc_detail'[interest_earned]
__________________________________________________
(5)
Current_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])))
________________________________________________
(6)
Previous_week_Reveneue = CALCULATE(
SUM('public cc_detail'[Revenue]),
FILTER(
ALL('public cc_detail'),
'public cc_detail'[week_num2] = MAX('public cc_detail'[week_num2])-1))

______________________________________________________________________________________________________________________________
🚀 Dashboard Features:

    Credit Card Transaction Report: Dive into transaction insights with interactive KPIs and graphs, showcasing revenue by income, marital status, dependents, education, and weekly trends.
    Credit Card Customer Report: Explore customer-centric analytics including revenue by gender, job role, education, expenditure type, customer acquisition cost, quarterly revenue, and total transaction amounts.

📊 Interactive Visualization: The dashboards offer a user-friendly experience with interactive elements such as quarterly view buttons and dynamic graphs, facilitating deeper exploration of credit card data.

This project showcases advanced data analytics with intuitive design, empowering stakeholders to make data-driven decisions with confidence and agility. Revolutionize credit card operations with insightful analytics! 💪🌐 
