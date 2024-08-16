Power BI - Credit Card Financial Report

OBJECTIVE- To create a comprehensive credit card dashboard that provides real-time insights into key performance metrics and trends, enabling stakeholders to monitor and analyze credit card operations efficiently on a weekly basis.

DAX Query Used - 
Age Category = SWITCH(TRUE(),customer_details[Customer_Age]<=30,"<30",customer_details[Customer_Age]<=40,"31-40",customer_details[Customer_Age]<=50,"41-50",customer_details[Customer_Age]<=60,"51-60",customer_details[Customer_Age]>60,"60+")
Income Category = SWITCH(TRUE(),customer_details[Income]<=30000,"Low",customer_details[Income]<=50000,"Medium",customer_details[Income]<=75000,"High",customer_details[Income]>75000,"Super High")
Revenue = credit_card_details[Annual_Fees]+credit_card_details[Interest_Earned]+(credit_card_details[Total_Trans_Amt]*0.12)
Current Week Revenue = CALCULATE(SUM(credit_card_details[Revenue]),FILTER(ALL(credit_card_details),credit_card_details[Week Number]=MAX(credit_card_details[Week Number])))
Previous Week Revenue = CALCULATE(SUM(credit_card_details[Revenue]),FILTER(ALL(credit_card_details),credit_card_details[Week Number]=MAX(credit_card_details[Week Number])-1))
Week Number = WEEKNUM(credit_card_details[Week_Start_Date])
