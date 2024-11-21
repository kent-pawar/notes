# Text-to-SQL
- https://partyrock.aws/u/kentpawar/a6qYDh6HI/QueryMaster
- Schema
```
Prompt: convert questions into sql
Prompt: Based on the following question: '[User Question]' and the database schema: '[Database Schema]', generate a SQL query that answers the question. Provide only the SQL query without any additional explanation.

What are the top 5 selling products?

products(id, name, price)
customer(id, name, email, address, phone_number)
sales(id, product_id, cust_id, quantity, sales_date)
```


# DLL generator
```
Below are the table names followed by a list of columns that are part of the table.

Table: product
Columns:
- id (integer, primary key)
- name (varchar(50), not null)
- price (float, not null)

Table: customer
Columns:
- id (integer, primary key)
- name (varchar(50), not null)
- email (varchar(100), unique)
- address (varchar(100), unique)
- phone_number (varchar(100), unique)

Table: sales
Columns:
- id (integer, primary key)
- product_id (integer, foreign key to product.id)
- cust_id (integer, foreign key to customer.id)
- quantity (float, not null)
- amount (float, not null)
- sales_date (timestamp)

============================
Here are the SQL DDL statements to create the tables based on the provided descriptions, including appropriate data types, constraints, and relationships:

DROP table customer;
DROP table product;
DROP table sales;

-- Create the product table
CREATE TABLE product (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    price FLOAT NOT NULL
);

-- Create the customer table
CREATE TABLE customer (
    id INTEGER PRIMARY KEY,
    name VARCHAR(50) NOT NULL,
    email VARCHAR(100) UNIQUE,
    address VARCHAR(100) UNIQUE,
    phone_number VARCHAR(100) UNIQUE
);

-- Create the sales table
CREATE TABLE sales (
    id INTEGER PRIMARY KEY,
    product_id INTEGER,
    cust_id INTEGER,
    quantity FLOAT NOT NULL,
    amount FLOAT NOT NULL,
    sales_date TIMESTAMP,
    FOREIGN KEY (product_id) REFERENCES product(id),
    FOREIGN KEY (cust_id) REFERENCES customer(id)
);



-- Comments for product table
COMMENT ON TABLE product IS 'Stores information about products';
COMMENT ON COLUMN product.id IS 'Unique identifier for each product';
COMMENT ON COLUMN product.name IS 'Name of the product';
COMMENT ON COLUMN product.price IS 'Price of the product';

-- Comments for customer table
COMMENT ON TABLE customer IS 'Stores information about customers';
COMMENT ON COLUMN customer.id IS 'Unique identifier for each customer';
COMMENT ON COLUMN customer.name IS 'Name of the customer';
COMMENT ON COLUMN customer.email IS 'Email address of the customer';
COMMENT ON COLUMN customer.address IS 'Physical address of the customer';
COMMENT ON COLUMN customer.phone_number IS 'Phone number of the customer';

-- Comments for sales table
COMMENT ON TABLE sales IS 'Stores information about sales transactions';
COMMENT ON COLUMN sales.id IS 'Unique identifier for each sale';
COMMENT ON COLUMN sales.product_id IS 'Foreign key referencing the product involved in the sale';
COMMENT ON COLUMN sales.cust_id IS 'Foreign key referencing the customer involved in the sale';
COMMENT ON COLUMN sales.quantity IS 'Quantity of the product sold';
COMMENT ON COLUMN sales.amount IS 'Total amount of the sale';
COMMENT ON COLUMN sales.sales_date IS 'Date and time of the sale';

-------------------------------
These DDL statements create the three tables (product, customer, and sales) with the specified columns, data types, and constraints. The statements also include foreign key relationships between the sales table and the product and customer tables.

Additionally, comments have been added to provide explanations for each table and its columns, which can be helpful for documentation purposes.

====================================
Explanatory comments:

1. Product table:
   - The `id` column is set as the primary key.
   - The `name` column is set to NOT NULL to ensure every product has a name.
   - The `price` column is set to NOT NULL to ensure every product has a price.

2. Customer table:
   - The `id` column is set as the primary key.
   - The `name` column is set to NOT NULL to ensure every customer has a name.
   - The `email`, `address`, and `phone_number` columns are set as UNIQUE to prevent duplicate entries.

3. Sales table:
   - The `id` column is set as the primary key.
   - The `product_id` column is set as a foreign key referencing the `id` column in the `product` table.
   - The `cust_id` column is set as a foreign key referencing the `id` column in the `customer` table.
   - The `quantity` column is set to NOT NULL to ensure every sale has a quantity.
   - The `sales_date` column is of type TIMESTAMP to store the date and time of the sale.

These DDL statements create the tables with the specified columns, data types, and constraints, establishing the relationships between the tables as described.

===========================================
DELETE FROM customer;
INSERT INTO customer (id,name,email,address,phone_number) VALUES (  1, 'Alice',  'alice@gmail.com',  '1, Mumbai',  '9990000001'); 
INSERT INTO customer (id,name,email,address,phone_number) VALUES (  2, 'Bob',  'bob@gmail.com',  '2, Mumbai',  '9990000002'); 
INSERT INTO customer (id,name,email,address,phone_number) VALUES (  3, 'Kent',  'kent@gmail.com',  '3, Mumbai',  '9990000003'); 

DELETE FROM product;
INSERT INTO product (id,name,price) VALUES (1, 'bat', 100); 
INSERT INTO product (id,name,price) VALUES (2, 'ball', 20); 
INSERT INTO product (id,name,price) VALUES (3, 'racket', 1000); 

DELETE FROM sales;
INSERT INTO sales (id,product_id,cust_id,quantity,amount,sales_date) VALUES (1,1,1,3,300,'2024-11-20T13:00:01.200');




```
