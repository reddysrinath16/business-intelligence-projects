## Sales Insights Data Analysis Project

1. SQL database dump is in SalesInsights.sql file above. Download `SalesInsights.sql` and in MYSQLSERVER WORKBENCH and import the sql file

### Data Analysis Using SQL

⮞ Show all customer records

    `SELECT * FROM customers;`

⮞ Show total number of customers

    `SELECT count(*) FROM customers;`

⮞ Show transactions for Chennai market (market code for chennai is Mark001

    `SELECT * FROM transactions where market_code='Mark001';`

⮞ Show distrinct product codes that were sold in chennai

    `SELECT distinct product_code FROM transactions where market_code='Mark001';`

⮞ Show transactions where currency is US dollars

    `SELECT * from transactions where currency="USD"`

⮞ Show transactions in 2020 join by date table

    `SELECT transactions.*, date.* FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020;`

⮞ Show total revenue in year 2020,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and transactions.currency="INR\r" or transactions.currency="USD\r";`
	
⮞ Show total revenue in year 2020, January Month,

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020 and and date.month_name="January" and (transactions.currency="INR\r" or transactions.currency="USD\r");`

⮞ Show total revenue in year 2020 in Chennai

    `SELECT SUM(transactions.sales_amount) FROM transactions INNER JOIN date ON transactions.order_date=date.date where date.year=2020
and transactions.market_code="Mark001";`


Data Analysis and ETL Using Power BI
============================

ETL
➤filtering sales markets of india excluding other non-indian countries
➤Again there sales amount which is less than zero which is not possible 
➤Coverting currency which are in USD to INR  (note there two USD) using the following formula to create new column
 🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻🡻
Formula to create norm_amount column

norm_amount column = Table.AddColumn(#"Filtered Rows", "norm_amount", each if [currency] = "USD" or [currency] ="USD#(cr)" then [sales_amount]*75 else [sales_amount], type any)`



