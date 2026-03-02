
Zepto-Delivery-management System-SQL- Project 

Project Overview

Project Title: Zepto-Delivery-management System

Level: Basic-Intermediate

Database: zepto_delivery_system


This project is designed to demonstrate SQL skills and techniques typically used to explore, clean, and analyze zepto_delivery data . The project involves setting up a zepto_delivery_system database, performing exploratory data analysis (EDA), and answering specific business questions through SQL queries. This project is helps me to build a solid foundation in SQL.


Objectives
1.	Set up zepto_delivery_system database: Create and populate a retail sales database with the provided sales data.
2.	Business Analysis: Use SQL to answer specific business questions and derive insights from the sales data.

Project Structure

1.	Database Setup
•	Database Creation: The project starts by creating a database named zepto_delivery_system.

•	Table Creation: Five tables named as users, product, order, order_items, payment are created to store the sales data. The table structure includes  different columns for users , product , orders , order_items , payment .





CREATE DATABASE zepto_delivery_system;

use zepto_delivery_system;


CREATE  TABLE  users 
		(User_ID varchar(10) primary key,
		Name varchar (50),
             	       	Email varchar(30),
               	Phone char (13),
                    	city varchar (25),
                   	Pincode varchar (10)
                    	);
                    
CREATE  TABLE  product 
		(Product_ID varchar(10) primary key,
		Product_Name varchar (50),
                    	Category varchar(30),
                    	Selling_Price float
                    	);
                    
                    
CREATE  TABLE  orders 
		(Order_Item_ID varchar(10) primary key,
		Order_ID varchar (10),
		Product_ID varchar (10),
		Quantity int,
		Price float ,
		Subtotal float
		);
     
CREATE  TABLE  order_items 
			(Order_Item_ID varchar(10) primary key,
			Order_ID varchar (10),
			Product_ID varchar (10),
			Quantity int ,
			Price float ,
			Subtotal float 
			);
                        
                        
                        
CREATE  TABLE  payment 
			(Payment_ID varchar(10) primary key,
			Order_ID varchar (10),
			Amount float ,
			Payment_Method  varchar(10),
			Payment_Status varchar (10),
			Payment_Time datetime
			);
                        
                        
                        
                        

Basic insights :

•	Record Count: Determine the total number of users, products,orders in the dataset.
•	Customer Count: Find out how many unique customers from the order table.
•	Category Count: Identify all unique product categories from product table.
--                   Basic SQL Questions


Q1 : Show the total number of purchesing per each User

SELECT User_ID,count(*) AS 'Total no_of_Purchesing' FROM orders GROUP BY User_ID;


 Q2 : Show all products under the category “Beverages”.

SELECT * FROM product where Category='BEverages';


 Q3 : Display all orders placed in february.

SELECT * FROM orders where month(Order_Time)='02';


 Q4 :Show details of a specific order (Order_ID = 20).

SELECT * FROM orders where Order_ID = 20;


Q5 : Display total number of products in each category.

SELECT Category, count(*) from product group by category;


 Q6 :Find the total number of users registered.

SELECT count(User_ID) from users;


 Q7 :Show all orders with status = ‘Cancelled’.

SELECT * from orders where Order_Status='Cancelled';


Q8 :Show all orders with status = ‘Delivered’.

SELECT * from orders where Order_Status='Delivered';


Q9 : Display all products sorted by price (low to high).

SELECT * FROM product order by Selling_Price;


-- Intermediate SQL Questions (JOIN Based)


 Q10 :Show all orders along with user names.

SELECT o.*,Name FROM users u join orders o on u.User_ID=o.User_ID order by Total_Amount desc limit 20;


Q11 :Display order details with product names and quantities.

SELECT distinct Product_Name,oi.*,oi.Quantity*oi.Price as Total_Price from product p join order_items oi on p.Product_ID=oi.Product_ID join orders o on o.Order_ID=oi.Order_ID;

 Q12 : Find total amount spent by each user.

SELECT  u.*,sum(Total_Amount) as total_spent from orders o join users u on o.User_ID = u.User_ID group by u.User_ID;


Q13 : Display top 5 most sold products.

SELECT * from orders o join order_items oi on o.Order_Id= oi.Order_Id limit 5;



Q14 :Find users who have placed more than 5 orders.

SELECT COUNT(*) Order_Times,u.Name FROM orders o join users u on o.User_ID=u.User_Id   group by u.Name order by Order_Times desc limit 5 ;





Conclusion
This project serves as a comprehensive introduction to SQL for data analysts, covering database setup, exploratory data analysis, and business-driven SQL queries. The findings from this project can help drive business decisions by understanding sales patterns, customer behavior, and product performance.

