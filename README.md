# 🛒 💳 📱 🌐

# Project Description: Omni Sales & Customer Loyalty Analysis

# Project Overview:
This project analyzes business data for a E-commerce start up chain with branches in different country locations, focusing on identifying spending patterns, and customer  preferences enabling the stakeholders to further deep dive into key metrices and come up with fiscal plan for year 2016. This analysis aims to uncover valuable insights that can drive strategic decision-making. 

# Project Tools:
Power BI, PostgreSQL

# Data Model Relation:
One to One relationship

# Time Period : 2010-2015

# Databases: 
  -  Busines E2E
  -  Loyal_Customer_DB : This particular database focuses on extracting and segmenting customers based upon the frequent purchases within the span of 1st week of their
     purchase. To further dive deeper and extract the same output has been extracted using PostgreSQL server.

    					 SQL Query:-  
                          Select "Customer_ID",
				          case
                          when "Purchase_Count" >= 100 then 'Active Customers'
                          When "Purchase_Count" <100 and "Purchase_Count" >=50 then 'Moderately Active Customers'
                          Else 'Less Active Customers' end as "Activity Status"
                          from 
	                            (
	                               Select "Customer_ID",Count("Order__ID") as "Purchase_Count"
	                               from 
		                                  (	 Select "Table_Two"."CustomerID" as "Customer_ID","Table_One"."OrderID" as "Order__ID"
			                                   from 
			                                   public."Order_Details" as "Table_One" 
		                                  INNER JOIN 
			                                   public."Order_Details" as "Table_Two"
		                                  ON "Table_One"."Order_Date" + interval '1 week' = "Table_Two"."Order_Date"
		                                  ) as "Loyal_Table" group by "Customer_ID" order by Count("Order__ID") desc
	                              ) as "Active_Status_Table";


# Crucial Insights:

	- Omni Sales Analysis:	
	  The Omni Sales Analysis Dashboard is designed to evaluate key performance indicators (KPIs) that provide insights into the overall performance of an online retail c		  chain operating across the Canadian region.
	  KPIs:-
	  		a) Average Basket Value (ABV):
			   The ABV analyses the amount spent within a single transaction. ABV = (Total Sales Revenue/Number of Transactions)
			   Key Findings: Within the span of 5 years, there has been an increse in the overall ABV of up to $179K in the last phase  (year 2015), signifying that there  
			   has been a massive increase in the online purchases by the customers. 
			
			b) Customer Acquisition Cost (CAC):
			   The Customer Acquisition Cost highlights the total sum of discount expenses incurred by the businesss to retain the customers. 
			   Key Findings: There has been a significant in increase in the Customer aquisition within the span of 5 years of up to $ 862 in year 2015, which brought the 	
			   82 Total Repeat Customers with 56.1% of less active customers bieng the major chunk of the whole portion in the total profits(See Loyalty Analysis 
			   Dashboard->Filter->Order_Channel->Canada).

			c) Discount Impact % Analysis:
			   This particular dashboard analyses the impact of discount expenses on the product sales with repsect to the different brand names.
			   Key Findings: During the first phase (Year 2010), Snake Boots and Stretch Oui Pants observed the equal maximum impact of the discounts with 29.18% of  
			   contribution to thier sales. Whereas, in the last phase (Year 2015) the trend shifted to Summer Shorts and Basket with an impact of 33.87% during the third 
			   quarter. 
			   
			d) Cummulative Sales: Analyses the cummulative sales by the month.
	  		   Key Findings: THe first year of the business saw a major spike in the business of up to $ 140000 during the month of January with Snake Boots bieng the top 	 
			   selling priduct 

# 
