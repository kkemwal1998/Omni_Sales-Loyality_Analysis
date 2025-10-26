# 🛒 💳 📱 🌐

# Project Description: Omni Sales & Customer Loyalty Analysis

# Project Overview:
This project analyzes business data for a E-commerce start up chain with branches in different country locations, focusing on identifying spending patterns, and customer  preferences enabling the stakeholders to further deep dive into key metrices and come up with fiscal plan for year 2016 in Canada. This analysis aims to uncover valuable insights that can drive strategic decision-making. 

# Project Tools:
Power BI, PostgreSQL

# Data Model Relation:
One to One relationship

# Time Period : 2010-2015

# Databases: 
  -  Busines E2E
  -  Loyal_Customer_DB : This particular database focuses on extracting and segmenting customers based upon the frequent purchases within the span of 1st week of their
     purchase. To further dive deeper and extract the same output has been extracted using PostgreSQL server. Based on threshold levels in the purchase counts:-

     					Purchase Count < 50 ---> Less Active Customers

     					Purchase Count >= 50 ---> Moderately Active Customers

     					Purchase Count >= 100 ---> Active Customers
     					   

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
	  Filter: Year-Quarter,Country
	  KPIs:-
	  		a) Average Basket Value (ABV):
			   The ABV analyses the amount spent within a single transaction. ABV = (Total Sales Revenue/Number of Transactions)
			   Key Findings: Over a 5-year period, the ABV has shown significant growth, reaching $179K in 2015. This indicates a substantial increase in customers’ online  
			   purchasing behavior, reflecting stronger spending patterns and higher transaction values.			
			    
			b) Customer Acquisition Cost (CAC):
			   The Customer Acquisition Cost highlights the total sum of discount expenses incurred by the businesss to retain the customers. 
			   Key Findings: here has been a notable increase in customer acquisition over the 5-year period, reaching $862 in 2015 with a spike in 2011 and 2014. This 
			   growth resulted in 82 total repeat customers, with 56.1% classified as less active customers, who nonetheless contributed a significant share to the overall 
			   profits. (Refer to Loyalty Analysis Dashboard → Filter → Order Channel → Canada.)
			   
			c) Discount Impact % Analysis:
			   This particular dashboard analyses the impact of discount expenses on the product sales with repsect to the different brand names.
			   Key Findings: In the initial phase (Year 2010), Snake Boots and Stretch Oui Pants both experienced the highest discount-driven sales impact, each contributing 			   29.18% to total sales. However, by the final phase (Year 2015), the trend had shifted—Summer Shorts and Baskets emerged as the top performers, driving a 
			   33.87% impact during the third quarter, reflecting a clear evolution in customer preferences and seasonal purchasing behavior.

			d) Cummulative Sales: Analyses the cummulative sales by the month.
	  		   Key Findings: Over the 5-year span, the business experienced a significant surge in sales between October and February during the winter seasons from 2011 to 
			   2014, with Snake Boots consistently ranking as the top-selling product. This trend highlights a strategic opportunity to launch targeted promotions or loyalty 
			   offers during this period to retain and further engage customers who frequently purchase Snake Boots.

			d) Total Profit By Product Brand: Anlyses the perventage contribution of each brand to the business profits. 
			   Key Findings: Within the 5 years, Snake Boots had an ovrerall contribution with 58.99% to the profits with the overall sales of $2.04M with the customer 
			   Aqcuistion Cost of $3000.

			e) Top Sales By Brand:
			   Key Findings: Over the past five years, Snake Boots emerged as the top-selling product, generating total sales of $2.04M and accounting for 80% of sales in 
			   July of the most recent year.

			f) Top Sales by Office: The oganisation has got several offices across the globe, that are responsible for executing the online sales on customer's behalf.
			   Key Findings: Kolkata branch in India has been the top selling branch with the major contribution of the overall sales of $1,400,000.

			G) Top 5 Supplier Channels: Analyses the sales contribution by the supplier channels.
			   Key Findings: Cangaroo Shoes has been the major supplier, whose has sales orders has been executed by Kolkata office with Snake Boots bieng a star product   and 			   a major contributor to the sales.

			Conclusion:
				- Average Basket Value increased significantly over 5 years, indicating higher customer spending and stronger purchasing behavior.
				- Rising Customer Acquisition Costs and repeat customer data highlight opportunities to engage less active customers effectively.
				- Discount-driven sales shifted from Snake Boots and Stretch Oui Pants to Summer Shorts and Baskets vests, reflecting changing customer preferences.
				- Snake Boots consistently led sales and profits, particularly during winter months, representing key opportunities for targeted promotions and loyalty 	
				  initiatives.
				
	- Customer Behavior Analysis: Loyalty Members
	  This Dashboard is designed to evaluate key performance indicators (KPIs) that provide insights into the overall behavioral patterns of the loyal customers using  
	  database called 'Loyal_Customer_DB' as a major foundation across the Canadian order channel. The main focus is to analyse the less active customers.
	  KPIs:-
	  		a) Total Repeat Customers:
			   The business recorded 82 repeat customers, with nearly 90% of them belonging to the previously less active customer segment—indicating strong re-engagement 
			   and improved customer retention.	
			   
			b) Total Profits by Customer Active Status:
			   Over the 5-year period, less active customers contributed 56.1% of the total profits, showing a significant growth of 43%. In contrast, active customers 
			   experienced only a modest increase of 0.82%, indicating that re-engaging less active customers had a more substantial impact on overall profitability.
			   
	  		c) Total Sales by customer category:
			   This visualization highlights the top product category purchased by less active customers. Sportswear emerged as the leading category, generating total sales 
			   of $723.78K. However, the category experienced a significant decline of $217.01K between 2011 and 2015.
			   
			d) Total Sales by customer category:
			   This visualization highlights the top product category among less active customers. Sportswear stands out as the best-selling category, generating total 
			   sales of $723.78K, though it witnessed a notable decline of $217.01K between 2011 and 2015.
			   
	  		e) Repeat Customer Rate:
			   There has been an overall customer growth of 5.35%, accompanied by a significant 41% decline in the repeat purchase rate.
			   
			f) Discount Impact on Customers (%):
			   Discount and loyalty promotions had a substantial impact of 56.27% on less engaged customers, driving a notable 20% increase in their overall engagement.

			Conclusion:
			The business successfully re-engaged less active customers, who accounted for nearly 90% of repeat purchases, strengthening overall customer retention.

			- Less active customers contributed significantly to profitability, driving 56.1% of total profits with a 43% increase over five years.

			- Despite Sportswear being the top selling category among less active customers, it showed a notable sales decline of $217.01K between 2011 and 2015.

			- Discount and loyalty promotions proved effective, increasing engagement among less active customers by 20%, even though the overall repeat purchase rate 
			  fell by 41%.

	  

			
			   
			
# 
