# Joe's Portfolio:
##### Greetings and welcome to my portfolio! As I continue to explore the fascinating world of data analytics, I'm thrilled to present my personal projects to you. Each project showcases my process of exploratory data analysis, and I would be delighted if you took a closer look to learn more. I hope you find my projects as enjoyable to read about as I did working on them!

---------------------------------------------------
<details> 

<summary>

### Project: Hotel Revenue Analysis

#### *Conduct a thorough analysis of a hotel revenue dataset to identify trends and insights related to revenue growth, hotel occupancy rates, guest parking requirements, distribution channels, and customer characteristics. The primary objective is to provide insights and answers to pertinent business questions within the hospitality industry.*

### Dashboard: ###
![image](https://user-images.githubusercontent.com/28738970/233811602-d16169ba-0644-444f-9687-10bd6dae6070.png)

</summary>

<br>

# [Project Title: Hotel Revenue Analysis](https://github.com/joerhee01/Hotel-Booking-Analysis)
[Dataset sourced from blog: Absent Data](https://absentdata.com/data-analysis/where-to-find-data/)

#### NOTE: For data analysis, I utilized SQL to combine and organize the data, and DAX in Power BI to calculate metrics and generate insights. This project was undertaken as a personal challenge to enhance my skills in working with financial and date data types in DAX, and to create more effective data visualizations.

# Resources Used for this Project: #
- Stack Overflow and other online forums to research SQL and DAX queries.
- Cole Nussbaumer Knaflic's book, *Storytelling with Data*, to reference best practices for data visualization. 
- Absent Data blog for the dataset and inspiration for the potential business problems. 
- The following Youtube channel for DAX calculation: [Calculate Growth over Last Year by Fiscal Year in Power BI](https://www.youtube.com/watch?v=iqUTHlfHomg&list=PLD27DiVmJtrSwEORvUXQgj2im_NP_uSC7&index=4), [Creating a simple date table in Power BI
](https://www.youtube.com/watch?v=-li7sxUxEqA&list=PLD27DiVmJtrSwEORvUXQgj2im_NP_uSC7&index=3), [Previous year up to a certain date
](https://www.youtube.com/watch?v=bAOs5LTP0I0&list=PLD27DiVmJtrSwEORvUXQgj2im_NP_uSC7&index=5)

# Objectives: #
Conduct a thorough analysis of a hotel revenue dataset to identify trends and insights related to revenue growth, hotel occupancy rates, guest parking requirements, distribution channels, and customer characteristics. The primary objective is to provide insights and answers to pertinent business questions within the hospitality industry.

# Business Questions: #
- Q1. Is our hotel revenue growing by year?
- Q2. Should we increase our parking lot size? 
- Q3. What trend can we see in the data?

# Discovery: #
- The original data source was an Excel Worksheet with 5 sheets containing 2018-2020 revenues, meal cost table, and market segment table.
- The worksheet consisted of 32 columns with attributes related to hotel type, customer information, booking information, meal information, and market segment.
- The combined rows totaled over 170,000, providing information on the attributes mentioned above.
- The data structure was consistent, enabling me to load the data into Microsoft SQL Server Management Studio for further structuring and transformation.

# Joining: #
- Loaded the dataset using the import wizard from SSMS.
- Used a SQL query to combine the 5 tables together and connect each table with their relevant keys.
- Created a backup of the merged dataset to ensure data safety during further transformations.

# Cleaning, Structuring, and Validating: #
- Converted month column from month name to month number for easier querying.
- Combined date columns together to use as a key later to create a relationship with a custom date dimension table in Microsoft Power BI.
- Organized each hotel revenue table by year, but dataset lacked consistency, which may impact date comparisons.
- Created a revenue calculation using various columns such as stays_in_weekend_nights, stays_in_week_nights, adults, children, babies, adr, discount, meal cost, is_canceled, and deposit type.
- Calculated total nights a guest stayed using stays_in_weekend_nights and stays_in_week_nights columns.
- Determined total number of guests using adults, children, and babies columns. 
- Multiplied total number of guests with meal cost to calculate total meal cost spent by guests.
- Used is_canceled column to determine if the guest actually stayed in the hotel and deposit_type to determine if the hotel made revenue from non-refundable deposits from canceled reservations.
- Used CASE expression in SQL to factor in revenue based on cancellation and deposit type.
- The logic behind revenue calculation:
  - If guest canceled reservation and deposit is refundable, then revenue is 0. 
  - If guest canceled and deposit is non-refundable, then revenue is $250 
    - Note: $250 is just a random number I created to replicate a non-refundable security deposit in some real hotels. 
  - If guest did not cancel reservation, then revenue is: 
    - (total nights * (ADR * (1 - discount rate)) + total meal cost
- Validated data and determined if there was anything out of the ordinary using custom query in SQL before loading query into Microsoft Power BI.

# Presenting: #
- Validated dataset loaded into Power BI
- Four card visualizations created to analyze Total Revenue, Average Daily Rate, Average Hotel Occupancy, and Total Parking Required
- Line chart created for each card to represent overall trend (inspired by Absent Data's blog)
- Line and clustered column chart used to visualize correlation between revenue growth and average daily rate, and negative correlation between hotel occupancy and average daily rate.
- Line and column chart used to compare current and past parking requirements and revenue growth. 
- Horizontal bar chart used to show which countries bring in the most revenue and which distribution channels are most profitable.
- Matrix added to provide deeper insight into revenue growth and parking requirement, with Month over Month and Year over Year growth highlighted.
- Slicer added to enable filtering by hotel type, year, and month for deeper insight into the report.

# My Analysis: #

- *Q1. Is our hotel revenue growing by year?*

- The revenue of the hotel appears to be increasing over the years, with 2019 showing a particularly high amount that could be considered an outlier. To gain more insights into why 2019 had such high revenue, additional data from the source may be necessary. Nonetheless, the trend indicates a positive growth in revenue.
  
  (*Total Revenue Trend from 2018 to 2020*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233808997-99366179-5237-48bd-8e03-bb2b873fde4e.png)
  
  
- *Q2. Should we increase our parking lot size?*

- Based on the data, it doesn't appear that the parking requirements are increasing significantly to warrant an expansion of the parking lot size, particularly if the hotel was able to accommodate the guest parking needs during the high-revenue year of 2019.

  (*Parking Required by Guest Trend from 2018-2020*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233810262-40263b70-7642-4d7e-8f52-8ed415837c22.png)

- *Q3. What trend can we see in the data?*

- Based on my analysis, it appears that there is an inverse relationship between the average daily rate and hotel occupancy. As the average daily rate increases, hotel occupancy decreases. However, despite the lower hotel occupancy, there is an increase in revenue associated with the higher rate. Therefore, finding a balance between the average daily rate and hotel occupancy is important in maximizing revenue. By finding the optimal rate, the hotel can attract more customers while still generating sufficient revenue.

  (*Hotel Occupancy, Revenue Rate, and Average Daily Rate Comparison*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233810386-1133d586-3103-4b4d-90b0-32cb7641682d.png)

- Based on the analysis of the hotel revenue dataset, the following insights were uncovered:
  - Portugal is the top revenue-generating country for the hotel, followed by Great Britain, France, and Spain.
  - The most effective distribution channel for generating revenue is through travel agencies, followed by direct bookings and then corporate bookings.
  
  (*Top Revenue Bringing Country Distributed By the Distribution Channel*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233810413-56c69dc5-f762-47ac-a288-9cfae27c23bf.png)

- August is the most profitable month in all three years (2018, 2019, and 2020). We should investigate what draws guests during this month. Additionally, I noticed that April, August, and October require the most parking space. It would be wise to plan for this to avoid issues. However, the data for 2018 and 2020 are incomplete, and having complete data may provide better insights.
  
  (*2020 Revenue and Parking Matrix*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233810565-ce51455b-6039-4924-af37-f464e85fab4c.png)

  (*2019 Revenue and Parking Matrix*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233810915-86458cf0-7412-4586-9627-5f4852b4348d.png)

  (*2018 Revenue and Parking Matrix*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233810598-9708c1f2-262b-4ba9-95ee-07d91f425077.png)


</details>





----------------------------------------------------
<details> 

<summary>

### Project: Sales Analysis for Electronic Retail Store 

#### *The objective of this project is to analyze sales data for an electronic retail store operating in the United States. By identifying patterns and insights, I aim to answer important business questions related to performance, customer behavior, and market trends. The findings will inform decisions regarding product offerings, pricing, promotions, and marketing strategies to drive growth and success for the business.*

### Dashboard: ###
![image](https://user-images.githubusercontent.com/28738970/233818600-5277aaec-291e-45fa-bb9f-e3c0ca5e8e79.png)

</summary>

<br>

# [Project Title: Sales Analysis for Electronic Retail Store](https://github.com/joerhee01/electronic_store_sales_analysis)
[Inspired by Keith Galli's video: Solving real world data science tasks with Python Pandas!](https://www.youtube.com/watch?v=eMOA1pPVUc4&list=PLD27DiVmJtrTPYCW_VIn8k9EvrzvJPV0k&index=17)

#### NOTE: I have used SQL and Power BI DAX for my data analysis and visualization. 

# Resources Used for this Project: #
- Stack Overflow and other online forums to research DAX and SQL queries.
- Cole Nussbaumer Knaflic's book, *Storytelling with Data*, to reference best practices for data visualization. 

# Objective: #
The objective of this project is to analyze sales data for an electronic retail store operating in the United States. By identifying patterns and insights, I aim to answer important business questions related to performance, customer behavior, and market trends. The findings will inform decisions regarding product offerings, pricing, promotions, and marketing strategies to drive growth and success for the business.

# Business Questions: #
- Q1. What was the best month for sales? How much was earned that month?
- Q2. What city had the highest number of sales?
- Q3. What time should we display advertisements to maximize likelihood of customer's buying product?
- Q4. What products are often sold together? 
- Q5. What product so the most? Why do you think it sold the most?  

# Discovery: #
- The project involves working with 12 CSV files, each representing a month of the year.
- All 12 files share a common structure, consisting of six columns capturing Order ID, Product, Quantity, Price Each, Order Date, and Purchase Address.
- Each file contains over 9000 rows of data, providing comprehensive transactional details.
- While some missing values exist, the dataset's overall shape is consistent, providing adequate data for analysis.
- To proceed with further structuring, the next step is to import the data into Microsoft SQL Server Management Studio. 

# Joining: #
- The dataset was loaded using the import wizard from SSMS.
- A SQL query was used to combine the 12 months of sales data into one source table.
- A backup of the merged dataset was created to ensure data safety during further transformations.

# Cleaning, Structuring, and Validating: #
- Rows with missing values in the [Order ID] column were removed since they were deemed unnecessary for analysis.
- A calculated column named [Sales Price] was created by multiplying the [Price Each] and [Quantity Ordered] columns to represent the sales prices.
- The [Order Date] datetime column was split into multiple columns, including date, year, month, day, time, hour, and minutes, to provide more granular data for deeper analysis.
- The [Purchase Address] column was also split into multiple columns, including street, city, state, and zipcode, to allow for more granular data analysis.
- The dataset was validated using custom queries within the RDBMS, leveraging joins, subqueries, and common table expressions (CTE) to answer business questions.
- No unusual results were discovered during the validation process, allowing me to proceed to visualize the data using Microsoft Power BI.

# Presenting: #
- To model my dataset, I utilized the Star Schema approach, creating separate Fact and Dimension tables in SQL and populating them with values from the original source table.
- The process involved creating unique keys and custom SQL VIEWS to join the dimension table to the fact table, ensuring accurate data representation.
- The Fact table comprised of two tables, Fact_orders and FACT_market_baskets, while the Dimension table was made up of DIM_products, DIM_store, and DIM_date.
- To finalize the data visualization, I created relationships between the tables in Power BI and incorporated DAX to generate calculated measures for my dashboard/report.

# My Analysis: #
- *Q1. What was the best month for sales? How much was earned that month?*

- The highest sales of over $4.61 million were achieved in December. 
  
  (*Total Sales by Months*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233818625-3157fdaa-3a02-458a-af63-0c5408c674a7.png)

- *Q2. What city had the highest number of sales?*

- The city with the highest sales was San Francisco, which amounted to $8.25 million. The second highest was Los Angeles at $5.45 million, followed by New York City at $4.66 million.
   
  (*Store Location Matrix*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233818638-c88d950b-6e91-4239-b805-66e48341e543.png)

- *Q3. What time should we display advertisements to maximize likelihood of customer's buying product?*

- According to the chart, the peak sales time occurred at 11:58 AM, with 281 products sold, followed by 1:25 PM with 271 products sold, 8:13 PM with 269 products sold, 11:26 AM with 268 products sold, and 6:36 PM with 262 products sold. Based on this trend, advertising between 11:00 AM to 2:00 PM midday and 6:30 PM to 9:30 PM would be most effective, as sales start to decrease steadily after this time frame.
  
  (*Total Product Sold Distributed by Time of the Day*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233818666-ddc1c2ea-c22d-42d4-9049-ab26ff0a1d97.png)


- *Q4. What products are often sold together?*

- The data shows that the USB-C Charging cable was the product that customers most frequently purchased together, with 2208 sales, followed closely by the iPhone with 2018 sales, and wired headphones with 1856 sales. The lightning charging cable, Google phone, and Apple Airpods were also popular purchases. These insights suggest that customers prefer to buy devices along with accessories and power cables. To maximize sales, it would be wise to market these items together with promotions or place them in close proximity to each other.

  (*Count of Products That Were Purchased Together*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233818680-3d3bb1fb-ea3b-48fe-be3b-4e44869f0e2b.png)

- *Q5. What product sold the most? Why do you think it sold the most?* 

- According to the chart, the top-selling products are AAA Batteries (4-pack), AA Batteries, USB-C Charging Cable, and Lightning Charger. This trend may be attributed to the importance of power-related products for electronic devices. It is noteworthy that the top-selling products are also the cheapest per unit. However, the top-earning products are the MacBook Pro Laptop, iPhone, ThinkPad Laptop, and Google Phone, with little influence from products in the top-selling list. To maximize sales and earnings, it would be wise to balance prices and offer promotions for the top-earning products to increase the likelihood of increasing sales and maximize profits.

  (*Top Selling Products by Unit Price of the Product*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233818441-9a6fb556-cf80-47b8-b55f-70390b1186ae.png)
  
  (*Top Earning Products vs Top Selling Products*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233818475-ecd8188a-467e-4ab4-a1ac-b2cbd9bc411b.png)



</details>

----------------------------------------------------

<details>

<summary> 

### Project: Data Professional Survey Analysis

#### *This study aims to analyze various aspects of the data profession, including market rates based on categorical factors such as industry, education, role, gender, age, race, and country. Additionally, the study will explore the common opinions and satisfaction scores of data professionals in relation to their employer, including factors such as management, salary, upward mobility, work/life balance, coworkers, and learning opportunity. The study will also examine where data professionals place the most value on future employment and the most popular tools used by this profession. Through this analysis, the study aims to provide valuable insights into the current trends and preferences of the data profession.*

### Dashboard: ###
![image](https://user-images.githubusercontent.com/28738970/233820497-dce0e7b9-67ce-4481-85e0-4458cf09276d.png)

</summary>

<br>

# [Project Title: Data Professional Survey Analysis](https://github.com/joerhee01/data_professional_survey_analysis)
[Survey sourced from YouTube channel, Alex The Analyst.](https://www.youtube.com/watch?v=pixlHHe_lNQ&list=PLUaB-1hjhk8FE_XZ87vPPSfHqb6OcM0cF&index=42)

#### NOTE: For this project, I used SQL to clean and transform the dataset and Power BI to visualize the data. I set myself the self-challenge of using SQL instead of Power Query for further customization of the dataset.

# Resources Used for this Project: #
- Stack Overflow and other online forums to research SQL queries.
- Cole Nussbaumer Knaflic's book, *Storytelling with Data*, to reference best practices for data visualization. 
- Alex The Analyst's Youtube channel for the survey dataset. 

# Objectives: #
This study aims to analyze various aspects of the data profession, including market rates based on categorical factors such as industry, education, role, gender, age, race, and country. Additionally, the study will explore the common opinions and satisfaction scores of data professionals in relation to their employer, including factors such as management, salary, upward mobility, work/life balance, coworkers, and learning opportunity. The study will also examine where data professionals place the most value on future employment and the most popular tools used by this profession. Through this analysis, the study aims to provide valuable insights into the current trends and preferences of the data profession.

# Discovery: #
- The dataset is a single flat file in CSV format.
- It contains 28 columns related to questions about the data professionals' profession and background information.
- The dataset has 630 rows representing the data professionals' responses.
- There are some columns that can be dropped for the analysis.
- There are a few missing values that need to be addressed.
- I will clean and structure the dataset using Microsoft SQL Server Management Studio.

# Joining: #
- I used the import wizard in SMSS to load the dataset.
- Since the survey data has various individual inputs, I will need to standardize them by searching for keywords and grouping them based on common attributes.
- The analysis does not require the joining of any new datasets.

# Cleaning, Structuring, and Validating: #
- I dropped columns [Dates Taken], [Time Taken], [Browser], [OS], [City Taken], [Country Taken], [Referrer], and [Time Spent] as they contained minimal data and were not relevant for my analysis.
- To facilitate easier querying in my relational database management system (RDBMS), I renamed the column headers that were too long and inefficient.
- I created a backup of the original dataset before proceeding with further restructuring. 
- In the columns [current_role], [industry], [favorite_tool], [most_important_aspect_for_next_job], [country of origin], and [ethnicity], users were given the option to input "Other" and specify their answers.
- To standardize the values in the [current_role] column, I used wildcards to identify specific keywords such as "Analyst" and "Engineering" and grouped them into general roles like "Data Analyst" or "Data Engineer." This was done to reduce the spread of roles and improve the weight of the analysis.
- The [industry] column contained individual inputs that were grouped into general sectors based on The Global Industry Classification Standard (GICS).
- I grouped user input with SQL in the [favorite_tool] column as a new category. The rest were labeled as "Other" as there was no common attribute. 
- The [most_important_aspect_for_next_job] column contained individual inputs that were not easily categorized, so they were grouped as "Other."
- In the [Country] column, I corrected spelling errors and removed unnecessary white spaces.
- The [Ethnicity] column contained individual inputs that were categorized into standard ethnic groups. For example, "Indian" was moved to the "Asian or Asian American" group.
- Missing values in the [education_level] column were grouped as "Other." 

# Presenting: #
- Validated each column's distinct values to ensure data cleanliness.
- Confirmed that all values were standardized.
- Determined key metrics such as total participant count, median age, and median salary.
- Selected card visualization to showcase these metrics.
- Visualized satisfaction scores using a gauge that ranged from 1 to 10.
- Employed line and bar charts to best illustrate distribution among survey responses
- Used charts to show how median salaries were impacted by education and sectors.
- Created a slicer to allow for drill-through reports based on participants' categorical attributes such as role, gender, age, ethnicity, and country.
- Slicer enabled deeper insights into specific groups within the dataset.

# My Analysis: #
- In this survey, which included a total of 630 participants, 261 were found to be residing in the United States. As a resident of the US, I am keen to focus my analysis on data pertaining to this region. Notably, the survey reveals that the median age of participants is 29 years old, and the median annual salary is $75,500.
  
  (*Number of Participants in the US, Median Age of Participants, and Median Salary*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233820525-e7df7002-4d25-45c0-8c33-6ab9c1f47ef6.png)

- Median salaries varied across sectors among the participants, with communication services and public sector having the lowest median salary at $53,000, while the others had a median salary of $75,000. However, it is important to note that this finding was based on a smaller sample size of 38 participants working in the communication services and public sector.
- Among the 38 participants working in the public and communication services sector, individuals with a masters degree and those with a high school degree were found to have the highest median salary of $75,000.
- It is worth noting that out of the 38 participants working in the public and communication services sector, 3 held a high school diploma while 17 held a master's degree. This suggests that the median salary figure for individuals with a master's degree may be more reliable due to the larger sample size. 

  (*Drill Through Report of Data Professional in the US by Communication Services and Public Sector*
  
  ![image](https://user-images.githubusercontent.com/28738970/233820809-f1ae6690-4354-4421-af48-9572c5716621.png)

- Among 261 US-based data professionals who participated in the survey, Python was the most popular tool, chosen by 57% of the respondents, followed by R and SQL.
- When it comes to breaking into the field, 39% of the respondents found it to be neither easy nor difficult, while 27% found it to be difficult and 22% found it to be easy.
- In terms of what they value most for their next employment, 46% of the respondents voted for a better salary, while 20% voted for remote work.

  (*Survey responses among 261 US Participants*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233821314-2b391916-531a-40c2-833b-49e27132a9bb.png)

- When asked to rate their job satisfaction on a scale of 1 to 10 based on factors such as management, salary, upward mobility, work/life balance, coworkers, and learning, the survey respondents gave the highest average scores to coworkers and work/life balance. On the other hand, salary received the lowest average satisfaction score, with respondents averaging a score of 5 out of 10.

  (*Satisfaction Score Among 261 US Participants*)
  
  ![image](https://user-images.githubusercontent.com/28738970/233821471-f46df57f-bce7-4638-979a-b3e74346005e.png)

- Out of the 261 participants in the US, 79 were female and 182 were male.
- While the median salary was the same for both genders, the median age of female data professionals was higher at 31 years compared to males at 28 years.
- Based on the survey results related to favorite tools, difficulty breaking into the job, and what they value most for their next job, it seems that the general opinion among the participants is similar between both genders. 
  
  (*Male Participants*)
  ![image](https://user-images.githubusercontent.com/28738970/233821731-ad213324-c537-4536-8930-6e3559df6ac9.png)
  
  (*Female Participants*)
  ![image](https://user-images.githubusercontent.com/28738970/233821739-5fadc201-a9c2-4bcc-9478-67d72287886c.png)

- According to the satisfaction score with their current employment, both male and female participants rated coworkers and work/life balance as the most satisfying aspects of their job. However, on average, female participants gave a lower satisfaction score than male participants. It would be interesting to conduct further analysis to identify the factors that contributed to this disparity in satisfaction between male and female participants.
  
  (*Male Participants*)
  ![image](https://user-images.githubusercontent.com/28738970/233822276-20ec94e7-10a9-4ee8-924b-84db2fe69dfb.png)
  (*Female Participants*)
  ![image](https://user-images.githubusercontent.com/28738970/233822268-21b9f9d7-36d2-4124-a6ec-cc52efa32869.png)
  


#### Disclaimer: #
*The data provided may not fully reflect the real trends due to various factors, such as differences between cultures and trends between countries, the demographics of Alex the Analyst's subscribers, a limited sample size of 630, and the accuracy of the participants' answers. To gain more accurate and precise insights, it may be necessary to gather more data and conduct further research, such as expanding the sample size, including a more diverse group of participants, and conducting surveys across different platforms and regions.*

</details>
