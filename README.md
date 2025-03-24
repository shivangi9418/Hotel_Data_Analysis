# Introduction

This project illustrates how to create a data analyst portfolio project with hotel booking data. It entails creating a database, data extraction and transformation with SQL, and visualization with Power BI to respond to important business questions.

# Project Overview

This project is intended to process and visualize hotel reservation data in order to get insights into revenue patterns, parking lot usage, and guest patterns. 

It involves the following key steps:

1.  **Database Development:** Creating a database by importing Excel files into Microsoft SQL Server Studio.
2.  **Extraction and Transformation of Data:** Creating SQL queries to extract, clean, and transform the data for hotel bookings.
3.  **Visualizing Data:** Linking Power BI to the SQL Server database to create visualization and dashboards.
4.  **Business Question Analysis:** Utilizing the visualizations to respond to significant business questions, including:

* Is revenue for the hotel increasing year-over-year, by hotel type?
* Should the size of the parking lot be expanded based on usage trends?
* What trends are evident in the data, with regard to average daily rate and guest behavior?
5.  **Findings Summary:** A summary of the main findings and conclusions reached through the data analysis.

# Technologies Used

* Microsoft SQL Server Studio
* Power BI

# Project Summary
**1. Database Construction:**
* Establishing a database by importing hotel booking records from Excel into Microsoft SQL Server Studio.

* Loading hotel reservation data from spreadsheet sources.

* Refining and formatting data to maintain consistency and accuracy.

       WITH hotels as(
       SELECT * from dbo.['2018$']
       UNION
       SELECT * from dbo.['2019$']
       UNION
       SELECT * from dbo.['2020$'])

       SELECT * FROM hotels
       LEFT JOIN dbo.market_segment$
       ON hotels.market_segment=market_segment$.market_segment
       LEFT JOIN dbo.meal_cost$
       ON meal_cost$.meal=hotels.meal

**2. Data Extraction and Processing:**

* Crafting SQL queries to extract, clean, and process hotel booking data.

* Merging multiple data tables to generate a unified dataset.

* Computing additional metrics such as total revenue and length of stay for analytical insights.

      WITH hotels as(
      SELECT * from dbo.['2018$']
      UNION
      SELECT * from dbo.['2019$']
      UNION
      SELECT * from dbo.['2020$'])

      SELECT arrival_date_year,hotel,
      ROUND(SUM((stays_in_week_nights+ stays_in_weekend_nights)*adr),2) AS revenue
    
      FROM hotels
      GROUP BY arrival_date_year,hotel

**3. Data Visualization and Insights:**

* Establishing a connection between Power BI and SQL Server to generate reports and dashboards.

* Importing SQL query results into Power BI for analysis.

* Structuring a data model to define relationships between various data fields.

* Designing interactive dashboards to visualize key insights, including:

   * Revenue trends over time

   * ADR (Average Daily Rate) analysis

   * Occupancy rate trends

   * Parking lot usage patterns

**4. Key Takeaways**      

* Revenue increase significantly from 2018 to 2019, it then decreased slightly from 2019 to 2020. Though it should br noted that the data for 2020 was still building up when the data was imported.
  
* Both the hotels(city & resort) experienced significant increase/growth in 2019, with 'city hotel' showing a higher growth rate.

* It can be seen that the parking space required is not increasing & is almost stagnant, So, there seems no need to increase parking area.
 
# Dashboard

![Hotel Data Analysis Dashboard](https://github.com/user-attachments/assets/33c6bbf0-48d0-42d7-a91c-716f829c3092)
