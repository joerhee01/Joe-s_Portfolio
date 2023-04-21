# Joe's Portfolio:
##### *Welcome to my portfolio where I will journal my personal projects as I continue my learning journey towards data analytics.*

----------------------------------------------------
# [Project Title: Sales Analysis for Electronic Retail Store](https://github.com/joerhee01/electronic_store_sales_analysis)
[Inspired by Keith Galli's video: Solving real world data science tasks with Python Pandas!](https://www.youtube.com/watch?v=eMOA1pPVUc4&list=PLD27DiVmJtrTPYCW_VIn8k9EvrzvJPV0k&index=17)

#### NOTE: I have used SQL and Power BI DAX for my data analysis and visualization. 

# Resources Used for this Project: #
- Stack Overflow and other online forums to research DAX and SQL queries.
- Cole Nussbaumer Knaflic's book, *Storytelling with Data*, to reference best practices for data visualization. 

# Summary: #
Analyze sales data to find patterns and insights that can help answer business questions for an electronic retail store that operates across the United States.

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

# Dashboard: #
![Dashboard Overview](https://user-images.githubusercontent.com/28738970/233511744-eb250534-1e67-40ca-b9cd-f37291ddea70.png)

----------------------------------------------------
# [Project Title: Data Profession Survey Analysis](https://github.com/joerhee01/data_professional_survey_analysis)
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

# Dashboard: #
![image](https://user-images.githubusercontent.com/28738970/233547152-4f3a1913-b8f9-40b6-a3e5-11b3035a48ea.png)

# Disclaimer: #
*The data provided may not fully reflect the real trends due to various factors like differences in salary rates among countries, the demographics of the viewers of Alex the Analyst, a restricted number of participants, and the precision of their answers. To gain more accurate and precise insights, it may be necessary to gather more data.*
