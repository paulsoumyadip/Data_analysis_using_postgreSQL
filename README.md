# Store Returned Items Database

This project is a SQL database that tracks the items that are returned by customers in a store. The database can store information about the orders, the customers, the products, and the reasons for returning. It can also generate reports to answer questions such as:

- How many items are returned in each category?
- What are the most common reasons for returning items?
- How much profit is lost due to returned items?
- Which customers return the most items?

## Data Source

The data for this project is based on a sample store order dataset from [^1^][2]. The dataset contains information about 9,994 orders placed by 4,373 customers in 2018. The dataset has the following columns:

- Row_ID: a unique identifier for each row
- Order_ID: a unique identifier for each order
- Order_Date: the date of the order
- Ship_Date: the date of shipment
- Ship_Mode: the mode of shipment
- Customer_ID: a unique identifier for each customer
- Customer_Name: the name of the customer
- Segment: the segment of the customer (Consumer, Corporate, or Home Office)
- Country: the country of the customer
- City: the city of the customer
- States: the state of the customer
- Postal_Code: the postal code of the customer
- Region: the region of the customer (Central, East, South, or West)
- Product_ID: a unique identifier for each product
- Category: the category of the product (Furniture, Office Supplies, or Technology)
- Sub_Category: the sub-category of the product (such as Chairs, Tables, Phones, etc.)
- Product_Name: the name of the product
- Sales: the sales amount in USD
- Quantity: the quantity of the product ordered
- Discount: the discount percentage applied to the product
- Profit: the profit amount in USD
- Discount_amount: the discount amount in USD (calculated as Sales * Discount)
- Years: the year of the order (extracted from Order_Date)
- Customer_Duration: the duration between Order_Date and Ship_Date (calculated as Ship_Date - Order_Date)

In addition to this dataset, a new column called Returned_Items is added to indicate whether an item was returned or not. The values are either Yes or No. A new table called Return_Reasons is also created to store the possible reasons for returning an item and their corresponding codes. The table has two columns: Reason_Code and Reason_Name.

## Database Schema

The database schema for this project consists of two tables: orders and return_reasons. The orders table has all the columns from the dataset, plus a new column called Return_Reason that references a foreign key from return_reasons table. The return_reasons table has two columns: Reason_Code and Reason_Name.

The orders table has some additional constraints:

- Row_ID is the primary key of the table
- Order_ID, Customer_ID, and Product_ID are unique identifiers that cannot be null
- Order_Date and Ship_Date are date values that cannot be null
- Ship_Mode, Segment, Country, City, States, Region, Category, Sub_Category, and Product_Name are text values that cannot be null or empty
- Sales, Quantity, Discount, Profit, Discount_amount are numeric values that cannot be negative
- Returned_Items is a text value that can only be Yes or No
- Return_Reason is a numeric value that references Reason_Code from return_reasons table

The return_reasons table has some additional constraints:

- Reason_Code is an integer value that is the primary key of the table
- Reason_Name is a text value that cannot be null or empty

## SQL Queries

The project uses SQL queries to load data into the database and to extract data from the database. The queries are written in MySQL syntax and can be executed using any MySQL client or tool.

### Loading Data

To load data into the database, the following steps are performed:

- Create the database and the tables using create_database.sql script
- Insert some sample data into return_reasons table using insert_return_reasons.sql script
- Load orders data from a CSV file using load_orders.sql script

### Extracting Data

To extract data from database, various SQL queries are used to answer different questions. Some examples are:

- To find how many items are returned in each category use query in returned_items_by_category.sql
- To find what are most common reasons for returning items use query in common_return_reasons.sql
- To find how much profit is lost due to returned items use query in lost_profit_by_returned_items.sql
- To find which customers return most items use query in frequent_return_customers.sql
