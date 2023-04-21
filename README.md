# Joe's Portfolio:
##### *Welcome to my portfolio where I will journal my personal projects as I continue my learning journey towards data analytics.*

----------------------------------------------------
# [Project Title: Sales Analysis for Electronic Retail Store](https://github.com/joerhee01/electronic_store_sales_analysis)
[Inspired by Keith Galli's video: Solving real world data science tasks with Python Pandas!](https://www.youtube.com/watch?v=eMOA1pPVUc4&list=PLD27DiVmJtrTPYCW_VIn8k9EvrzvJPV0k&index=17)

#### NOTE: I will use SQL and Power BI DAX for my data analysis and visualization. 

# Resources Used for this Project: #
- Stack Overflow and other online forums to research DAX and SQL queries.
- Cole Nussbaumer Knaflic's book *Storytelling with Data* for best practices with data visualization. 

# Summary: #
Conduct data analysis to identify trends and insights using sales data to answer business questions for an electronic retail store with business throughout the United States. 

# Business Questions: #
- Q1. What was the best month for sales? How much was earned that month?
- Q2. What city had the highest number of sales?
- Q3. What time should we display advertisements to maximize likelihood of customer's buying product?
- Q4. What products are often sold together? 
- Q5. What product so the most? Why do you think it sold the most?  

# Discovery: #
- The dataset is split into 12 flat files (CSV format) representing each month of the year. 
- All 12 tables have 6 columns with the following attributes: Order ID, Product, Quantity, Price Each, Order Date, and Purchase Address.
- Each table has over 9000+ rows representing each transaction and the details associated with it. 
- There are some missing values but the overall shape of the dataset is consistent and I have enough data for analysis.
- I will proceed to the next step of importing the data into Microsoft SQL Server Management Studio for further structuring.   

# Joining: #
- Load dataset using the import wizard from SSMS.
- Combine the 12 months of sales data into one source table using a SQL query. 
- Create a backup of the merged dataset while I continue transforming it.  

# Cleaning, Structuring, and Validating: #
- I have deleted the rows with the missing values in the [Order ID] column. These rows are no use for the analysis.
- I have created a calculated column called [Sales Price] which represents the sales prices by multiplying the [Price Each] and [Quantity Ordered] columns. 
- I have split the [Order Date] datetime column into several columns representing date, year, month, day, time, hour, and minutes which allows me a more granular data for deeper analysis. 
- I have also split the [Purchase Address] column into several columns representing the street, city, state, and zipcode. Again this allows me a more granular data for deeper analysis. 
- I have validated the dataset by creating custom query within the RDBMS using joins, subquery, and common table expression (CTE) to answer each business questions.
- I did not find any unusual result during my validation process so I have determined I can proceed to visualizing the data using Microsoft Power BI. 

# Presenting: #
- I will be modeling my dataset using the Star Schema so I have created a separate Fact and Dimension table in SQL and inserting values found in the original source table. 
- This process required me to create unique keys and custom SQL VIEWS to join the dimension table to the fact table. 
- Fact table: Fact_orders and FACT_market_baskets 
- Dimension Table: DIM_products, DIM_store, and DIM_date.
- Finalized the data visualization by creating relationship between my tables in Power BI and incorporating DAX to get calculated measures for my dashboard/report.

# Dashboard: #
![Dashboard Overview](https://user-images.githubusercontent.com/28738970/233511744-eb250534-1e67-40ca-b9cd-f37291ddea70.png)

