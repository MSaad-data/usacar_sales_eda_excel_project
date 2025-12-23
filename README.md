# usacar_sales_eda_excel_project
This project analyzes a vehicle sales dataset using Excel. I cleaned the data, calculated total quantity and revenue per product, city, and month. Visualizations show which products are ordered the most, which products generate the most revenue, which cities are most profitable, and which months have the highest sales.

## Data_set Used
 <a href="https://github.com/MSaad-data/usacar_sales_eda_excel_project/blob/main/Sales%20Dataset%20of%20Ecommerce%20(Electronic%20Products).xlsx">Dataset view</a>

## Introduction

For this project, I worked with a Sales Dataset of Ecommerce Electronic Products. The dataset contains hundreds of thousands of records of purchases from an electronics store, including information about the product, quantity sold, price, order date, and purchase location. It was created to help understand sales patterns and improve overall sales of electronic products.

The initial columns in the dataset were:

**Order ID** – unique identifier for each order

**Product** – name of the product sold

**Quantity Ordered** – number of units purchased

**Price Each** – price per unit of the product

**Order Date** – date and time of the order

**Purchase Address** – address of the customer

One of the major challenges in this dataset was the **Order Date** column. Some entries were in proper date format, while many were stored as text. Cleaning this column and converting all entries into a consistent date-time format required careful handling and formula-based solutions in Excel.

This project focuses on cleaning, analyzing, and visualizing the sales data to uncover insights about top-selling products, most profitable products, city-wise sales, and month-wise trends.


## Data Cleaning & Preparation

Before performing the analysis, I created several new columns in Excel to clean and prepare the data. These columns were essential for the further analysis and visualizations. The following new columns were added:

### Order_date_clean

Some entries in the original Order Date column were stored as text, while others were proper dates. To convert all entries into a consistent date-time format, I used the following formula:

=IF(ISNUMBER(E2), E2, DATE("20"&MID(E2,7,2),LEFT(E2,2),MID(E2,4,2)) + TIMEVALUE(MID(E2,10,LEN(E2)-9)))

This formula checks if the value is already a number (date). If not, it extracts the day, month, year, and time from the text and converts it into a proper Excel date-time format.

### Purchase_city

To focus on city-level analysis from the Purchase Address, I extracted only the city name using this formula:

=TRIM(MID(F2,FIND(",",F2)+1,FIND(",",F2,FIND(",",F2)+1)-FIND(",",F2)-1))

This formula locates the commas in the address and extracts the city part, trimming any extra spaces.

### Revenue_Earned

To calculate the total revenue for each order, I multiplied the quantity ordered by the price per unit:

=C2*D2

This gives the total revenue earned for each order, which is used for product, city, and month-level analysis.

### Order_month

To perform month-wise analysis, I extracted the month name from the cleaned order date using:

=TEXT(G2, "mmmm")

This converts the order date into a readable month name like “April”, “May”, etc., making it easier to analyze trends over months.


## Unique Product Analysis

To understand which products are most popular and which products generate the most revenue, I created a Unique_Product sheet in Excel. The following formulas were used:

Unique_Product – to get the list of all unique products:

=UNIQUE(Updated_sales!B2:B30247)


Total Quantity Ordered per Product – to calculate how many units of each product were sold:

=SUMIF(Updated_sales!B:B, Unique_Product!A2, Updated_sales!C:C)


Total Revenue per Product – to calculate how much revenue each product generated:

=SUMIF(Updated_sales!B:B, Unique_Product!A2, Updated_sales!I:I)

### Visualization: Unique_Product_Visualization Sheet

I created two horizontal bar charts in a separate sheet called Unique_Product_Visualization:

Which products are ordered the most?

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/728c55d4-83f6-44b2-9412-a9b9921b7e71" />


Which products generate the most revenue?

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/9c38db3a-eaf6-4aab-af10-42902e27e46f" />


### Insights and Decision-Making

These visualizations help stakeholders quickly identify top-selling products and high-revenue products.

For example, the product with the highest quantity sold may need inventory management attention to avoid stockouts.

Products generating high revenue may be prioritized for promotions or marketing campaigns even if their quantity sold is lower.

Businesses can use this analysis to make data-driven decisions about pricing, stocking, and marketing strategy.

This analysis also helps in spotting products that are popular but low revenue, and products that are less popular but high revenue, which can influence strategic decisions on discounts or bundle offers.


## Unique Purchase City Analysis

To understand where most orders come from and which cities generate the most revenue, I created a Uniques_Purchase_City sheet in Excel. The following formulas were used:

Unique City Names – to get the list of all unique cities:

=UNIQUE(Updated_sales!H2:H30247)


Total Quantity Ordered per City – to calculate how many units were sold in each city:

=SUMIF(Updated_sales!H2:H30247, Uniques_Purchase_City!A3, Updated_sales!C2:C30247)


Total Revenue per City – to calculate how much revenue was generated from each city:

=SUMIF(Updated_sales!H2:H30247, Uniques_Purchase_City!A3, Updated_sales!I2:I30247)

### Visualization

I created one horizontal bar chart showing both total orders and total revenue by city.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/0cb07f1b-03e6-4752-8e42-3f1cb7ea280e" />


The chart highlights which cities contribute most to sales and revenue.

For example, the city with the highest orders is clearly visible at the top, showing it is a key market for the business.

### Insights and Business Considerations

High-order cities: These cities are critical for operations — inventory and delivery planning must prioritize these locations. Marketing and promotions in these cities can boost sales further.

Low-order cities: These cities may need attention to increase sales. Possible reasons for lower sales could include lower market demand, fewer stores, or weaker advertising presence.

Businesses can use this insight to plan regional marketing, stock allocation, and expansion strategies.

### Why City Analysis Matters

Considering city-wise sales helps understand regional performance.

It allows businesses to allocate resources efficiently, such as shipping, inventory, and marketing budgets.

City-level analysis can reveal market opportunities, showing which cities are performing well and which need improvement.

## Month-wise Analysis

To understand how sales and revenue vary across months, I created a Unique_Order_Month sheet in Excel. The following formulas were used:

Unique Months – to get the list of all months in the dataset:

=UNIQUE(Updated_sales!J2:J30247)


Total Quantity Ordered per Month – to calculate how many units were sold in each month:

=SUMIF(Updated_sales!J:J, Unique_Order_Month!B2, Updated_sales!C:C)


Total Revenue per Month – to calculate the total revenue generated in each month:

=SUMIF(Updated_sales!J:J, Unique_Order_Month!B2, Updated_sales!I:I)

### Visualization

I created one horizontal bar chart showing both total orders and total revenue per month.

<img width="1366" height="768" alt="image" src="https://github.com/user-attachments/assets/d775d76b-fa8b-46a8-966c-5d10ab92e69f" />


The chart clearly shows which months have the highest sales and highest revenue, making trends easy to spot.

For example, April is the top month with 13,477 orders, followed by August with 9,379 orders. These months act as outliers, as other months have significantly lower order numbers (ranging from ~1,079 to ~1,166 orders).

### Insights and Business Considerations

High-order months (April, August): These months may have seasonal demand, promotions, or marketing campaigns, leading to higher sales. Businesses should ensure adequate inventory and staffing during these months to meet demand.

Low-order months: Other months have relatively stable but lower sales. These months might represent off-peak periods, where marketing campaigns could help boost sales.

Understanding month-wise trends allows better inventory planning, resource allocation, and promotional timing.

### Why Month Analysis Matters

Month-level analysis shows seasonal patterns in sales and revenue.

It helps identify peak months and off-peak months, enabling strategic decision-making for stock, marketing, and revenue forecasting.

Businesses can use these insights to increase profitability and avoid stockouts or overstocking.

## Note on Data Tables Used for Visualization

While working with Excel’s UNIQUE() function, some tables were generated as dynamic arrays.
Dynamic array tables cannot be sorted directly, which created a limitation during visualization.

### To resolve this:

I copied and pasted the array-based tables as values into separate visualization sheets.

This allowed me to sort the data (highest to lowest) based on Quantity Ordered or Total Revenue.

Separate tables were maintained for different visual perspectives (e.g., quantity vs revenue).

### This approach ensured that:

Visuals are clear, correctly ordered, and easy to interpret

The original dynamic logic remains intact, while visual storytelling is improved

## Conclusion & Key Takeaways

This Excel project demonstrates a complete sales analysis workflow, starting from raw ecommerce data to actionable business insights.

Through data cleaning, I resolved inconsistent date formats and engineered new features such as:

**Clean order dates**

**Purchase cities**

**Monthly sales trends**

**Revenue per order**

Using Excel formulas like **UNIQUE**, **SUMIF**, and **logical text/date function**s, I built:

**Product-level analysis** to identify top-selling and highest-revenue products

**City-level analysis** to understand geographic performance and profitability

**Month-level analysis** to uncover seasonal trends and outliers

**The visualizations clearly show:**

Some products sell more units, while others generate more revenue per sale

Certain cities consistently outperform others, indicating where business focus should be increased

Sales are not evenly distributed across months, highlighting seasonal demand patterns


**Overall, this project reflects my ability to:**

Think like a data analyst

Handle real-world messy data

Convert raw data into clear insights for decision-making

Use Excel not just for formulas, but for data storytelling

This project helped strengthen my foundation in Excel-based data analysis and prepared me for more advanced analytics tools in the future.
