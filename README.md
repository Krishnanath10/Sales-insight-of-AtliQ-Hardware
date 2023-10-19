# Sales-insight-of-AtliQ-Hardware Data Analysis Project

  AtliQ Hardware is a company who is doing business in computer peripherals in India. AtliQ Hardware's head office in Delhi India and have zonal office in different part of India.

  The Sales Director of AtliQ Hardware is facing issue to track their sales in terms of dynamically growing market, needing more accurate insights about the company sales. 

# Problem Statement:
  Whenever Sales Director called his zonal sales managers to discuss about sales, they provided him to tons of data in excel format saying that this was the sales for last quarter and this will be in next quarter, and this information is not enough for him.
  Just give him tons of numbers and many excel file this is not working, however they should checking data and understand what's going in the business.

# Solution:
  Create a simple and informative dashboard about the company sales.


  I have used MySQL Server as database and doing some analysis to understand the data and connect this data with Power BI for ETL and visualisation to get the insights.

# Data Analysis Using MySQL
In MySQL I have performed some basic analysis like you can see below.

1. Total revenue:-

   select sum(sales_amount) from transactions;

2. Total sales quantity:-

   select sum(sales_qty) from transactions;

3. Revenue in year 2019 using Join and for filter using Where clause:-

   select sum(transactions.sales_amount) as Revenue from transactions 
   inner join date on transactions.order_date=date.date 
   where date.year=2019 and transactions.currency="INR" or transactions.currency="USD";

4. Customer Type along with their Name using Join and Order by clause:-

   select  distinct(customer_code), b.custmer_name, b.customer_type from transactions a
   join customers b using (customer_code)
   order by customer_code;

5. Top 5 Revenue generated customer:-

   select a.customer_code, b.custmer_name, sum(a.sales_amount) as Revenue from transactions a
   join customers b using(customer_code)
   group by customer_code
   order by Revenue desc
   limit 5;

# Data Analysis in Power BI
  After completing above analysis in MySQL, I have connect Power BI to MySQL Database to get the data and perform ETL, Data MOdelling and create Dashboard to understand the business status.
