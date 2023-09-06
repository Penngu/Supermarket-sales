# Supermarket-sales
To Analyze the supermarket sales data of 1000+ transactions and 6 product lines using SQL data query and DML.

# SQL Query
To calculate the Supermarket Sales KPIs, following SQL query was used:

-- List of Product lines in Branch A

Select  Distinct(`Product Line`)
From supermarket_sales
Where Branch ='A';

 -- List of unique branch and their respective cities 
 
Select distinct(Branch) , City
From Supermarket_sales
Where city= 'yangon' 
UNION
Select distinct(Branch) , City
From Supermarket_sales
Where city= 'Mandalay'
UNION 
Select distinct(Branch) , City
From Supermarket_sales
Where city= 'Naypyitaw';
 
 -- Top 3 Selling product lines with respect to Order Cost 
 
 Select `product line`, payment, total
 From supermarket_sales
 Order by total desc
 limit 3;

 -- Amount of payments by Ewallet, credit card and cash each 
 
 Select payment as 	Payment_mode , SUM(total) as Amount 
 From supermarket_sales
 Where payment= 'Credit card'
 Union 
 Select payment, SUM(total)
 From supermarket_sales
 Where payment= 'Ewallet'
 Union 
 Select payment , SUM(total) 
 From supermarket_sales
 Where payment= 'Cash';
 
 -- Number of Unique Customers   
 
Select  `Customer Type` as 'Customer', count(`Customer type`) as 'No. of Customers'
 From supermarket_sales 
 Where `customer type`= 'normal'
 UNION 
Select `Customer Type` as 'member', count(`Customer type`) 
 From supermarket_sales 
 Where `customer type`= 'Member';
 
 -- List of products with cogs>=900    
 
 Select `product line`,`unit price`, quantity, cogs, `gross income`
 From supermarket_sales
 Where  cogs >= '900';

 -- List of Top 3 profitable product    
 
 Select `invoice id`, `product line`, Total as 'Total amount',cogs,`Gross income` 
 From supermarket_sales
 order by `gross income` desc
 Limit 3;
 
 -- Identifying Product line with Highest cogs
 
 Select `invoice id`, `product line`,quantity, cogs 
 From supermarket_sales 
 Order by cogs Desc
 Limit 3 ;
 
 -- List of Top Rated products over 9.5
 
 Select `product line`, `Customer type`, rating 
 From supermarket_sales 
 Order by rating < '9.5';
 
 -- List of Invoices in 2019
 
 Select `Invoice ID`, `Product line`, Date
 From supermarket_sales
 Where Date < '2019-01-01';
 
  -- Creating a table 
  
 Create Table Product_Pricing As 
 Select `Product line` , `unit price`
 From supermarket_Sales;
 
 Create table product_list 
 (Product_lines varchar(30)
 ,Product_name varchar(30),
 Product_ID int);
 
  Insert into product_list (Product_lines,Product_name,Product_ID)
  Values ('Health_and_Beauty', 'Lakme,Loreal,Mankind,Cipla' , '001'),
  ('Electronic_accessories', 'Sony,Boat,Dell,One_plus', '002'),
  ('Home_and_Lifestyle', 'Ikea, Pepperfry', '003'),
  ('Sports_and _Travel', 'SportsKonnect,Thomascook','004'),
  ('Food_and_Beverages', 'Hindustan_Unilever,ITC,Nestle', '005'),
  ('Fashion_Accessories', 'Voylla, Tribal_zone', '006');
