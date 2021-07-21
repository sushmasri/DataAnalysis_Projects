# DataAnalysis_Projects

Atliq Hardware Stores Data:

Data is in Mysql database and than hook it up with Tableau. In Tableau we will perform ETL and data cleaning operations to make it ready so that we can build our dashboard. We will do currency normalization, handling invalid values etc.  

In Tableau, data cleaning and data model (star schema) can be done.
Here transaction table is fact table
remaining are dimension tables

Using the data, develop some charts to study the sales in each region and dashboard.

Line chart->date , transaction table

which product has sales?
bar chart->product, transactions-product,sales qty> n in amt sales by product

maximum customers from which region?->customers, market(zone)


which region(market) has maximum sales

what sales are  by most customers->?customers, sales

profits vs loss—SP-CP/SP	

WITH RESULT AS (select st.*,sp.product_code AS PROD_CODE,sp.product_type  from sales.transactions as st  LEFT JOIN sales.products as sp on 
st.product_code=sp.product_code 
UNION
select st.*,sp.product_code AS PROD_CODE,sp.product_type from sales.transactions as st  RIGHT JOIN sales.products as sp on 
st.product_code=sp.product_code ) SELECT * FROM RESULT

select st.product_code,sum(st.sales_amount) from sales.transactions st JOIN sales.products as sp on 
st.product_code=sp.product_code group by  st.product_code  order by sum(st.sales_amount) desc


select st.market_code,sum(st.sales_amount),sp.markets_name from sales.transactions st JOIN sales.markets as sp on 
st.market_code=sp.markets_code where st.currency='INR'group by  st.market_code,sp.markets_name  
 order by sum(st.sales_amount) desc


select st.market_code,sum(st.profit_margin_percentage),M.markets_name from sales.transactions as st join markets as M
on st.market_code=M.markets_code group by  st.market_code ,M.markets_name
  
  
