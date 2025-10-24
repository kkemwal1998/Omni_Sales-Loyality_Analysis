# Project Description: Omni Sales & Customer Loyality Analysis

# Project Overview:
  This project analyzes business data for a E-commerce chain with branches in different country locations, focusing on identifying spending patterns, and customer preferences   
  enabling the stakeholders to further deep dive into key metrices. This analysis aims to uncover valuable insights that can drive strategic decision-making. 

# Project Tools:
Power BI, PostgreSQL

# Data Model Relation:
One to One relationship

# Time Period : 2010-2015

# Databases: 
  -  Busines E2E
  -  Loyal_Customer_DB : This particular database focuses on extracting and segmenting customers based upon the frequent purchases again within the span of 1 week. This
                         particular output has been extracted using PostgreSQL server.
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



  -  Busines E2E

# 
