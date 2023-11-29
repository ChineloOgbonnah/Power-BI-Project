# MAVEN TOY STORES, MEXICO

![](toy_store_picture_2.jpeg)
---

## INTRODUCTION
This is a power BI project on a **FICTITIOUS** toy store called **Maven Toy Stores** located in Mexico. The dataset was gotten from Maven Analytics (https://www.mavenanalytics.io/data-playground?tags=10btmr8wmkqkEgJMfgtOv2). It had four tables; Inventory (1593 rows and 3 columns), Products (35 rows and 5 columns), Sales (829,262 rows and 5 columns) and Store Tables (50 rows and 5 columns).
The project was to analyze and derive insigts to answer specific questions set by Maven Analytics about the dataset;
- Which product categories drive the biggest profits? Is this the same across store locations?
- Can you find any seasonal trends or patterns in the sales data?
- Are sales being lost with out-of-stock products at certain locations?
- How much money is tied up in inventory at the toy stores? How long will it last?

This project took me about 10 days (an average of 2 hours daily) to complete. I had initially completed it under 4 days but after watching a youtube video by Microsoft Reactor on 'Documenting Data Analysis Project on Github' (https://www.youtube.com/watch?v=GLIwyoPWrHs&t=1706s), I got inspired to make my report more interactive and so began days of learning and upskilling to finally get my final report 😫. Listed below are some of the resources I had used to compute my report;
- https://www.youtube.com/watch?v=SCI9iKl4vjU&list=PPSV
- https://www.youtube.com/watch?v=cFZtUzABOa8&list=PPSV
- https://www.youtube.com/watch?v=dTEmhPbtipc&list=PPSV
- https://www.youtube.com/watch?v=WspwLOp3UxA&list=PPSV

First Report                          |                              Final Report
:------------------------------------:|:----------------------------------------:
![](Maven_Toy_Store_Dashboard.PNG)    |  ![](Homepage.PNG)

In carrying out this project, the underlisted Power BI features were used;
- DAX (for calculated columns and new measures)
- Visualization
- Filters
- Dynamic Narrative
- Buttons
- Bookmarks
- Selection and Grouping
- Tooltips

## EXPLORATORY DATA ANALYSIS
### Data Cleaning: The dataset used was clean and did not need any further transformation. This was checked using the Power Query Editor and the Validity for each column of the tables were 100%. 

### Data Modelling: The type of model used for this report was a Star Schema (Many:1 and 1:Many). The auto-generated relationships between the tables were used (even though we could get other relationships), as it was suitable for this project.
![](Maven_toy_Store_Model.PNG)

### Data Analysis Expression (DAX): Some DAX were used to add new columns to some of the tables and calculate new measures for the report. Some of these expressions are listed below;
Calculated Columns                                      |                                      New Measures
:------------------------------------------------------:|:------------------------------------------------:
Cost = sales[Units]*RELATED(products[Product_Cost])     |%  Profit Contribution = DIVIDE(SUM(sales[Profit]),SUMX(ALL(sales),sales[Profit]))
Profit = sales[Sales]-sales[Cost]                       |Average Daily Sales = SUMX(sales,sales[Sales])/DISTINCTCOUNT(sales[Date].[Date])
Sales = sales[Units]*RELATED(products[Product_Price])   |Out_of_Stock = CALCULATE(VALUES(inventory[Inventory_at_Hand]),FILTER(inventory,inventory[Inventory_at_Hand]=0))
- 



