# Oder_Managment
Absolutely. Here is the same README with **all emojis removed**.

# Order Management System

## Project Overview

The **Order Management System** is a DBMS project developed for an **Etsy Handmade Marketplace Database Management System**.

It manages customer orders and the individual products included in each order. The system uses two main tables:

* `Orders`
* `Order_Items`

The database also establishes relationships between **Customers, Orders, Order Items, Products, Shops, and Sellers**.

---

## Objectives

* Store and manage customer orders
* Connect orders with customers
* Store products included in each order
* Maintain product quantities and prices
* Track order status
* Store total order amounts
* Generate customer order history
* Generate customer-wise order summaries

---

## Database Design

### Orders Table

| Attribute      | Key / Type       |
| -------------- | ---------------- |
| `Order_ID`     | Primary Key      |
| `Customer_ID`  | Foreign Key      |
| `Order_Date`   | Date             |
| `Order_Status` | Check Constraint |
| `Total_Amount` | Number           |

The allowed order statuses are:

`Pending` → `Confirmed` → `Shipped` → `Delivered` → `Cancelled`

### Order_Items Table

| Attribute       | Key / Type  |
| --------------- | ----------- |
| `Order_Item_ID` | Primary Key |
| `Order_ID`      | Foreign Key |
| `Product_ID`    | Foreign Key |
| `Quantity`      | Number      |
| `Price`         | Number      |
| `Sub_total`     | Number      |

The `Order_Items` table connects each order with the products purchased by the customer.

---

## Relationships

```text
Customer
   |
   | 1 : M
   v
 Orders
   |
   | 1 : M
   v
Order_Items
   |
   | M : 1
   v
 Product
   |
   | M : 1
   v
  Shop
   |
   | M : 1
   v
 Seller
```

### Relationship Explanation

* One Customer can place many Orders.
* One Order can contain many Order Items.
* Each Order Item refers to a Product.
* Products are listed by Shops.
* Shops are owned by Sellers.

---

## Main Operations

### 1. Create Tables

The project creates the `Orders` and `Order_Items` tables using Primary Keys, Foreign Keys, NOT NULL constraints, and CHECK constraints.

### 2. Insert Data

Sample order records are inserted with different statuses:

* Pending
* Confirmed
* Shipped
* Delivered
* Cancelled

The database contains 10 Orders and 11 Order Items in the provided dataset.

### 3. Retrieve Data

Basic `SELECT` queries are used to display order and order-item records.

```sql
SELECT * FROM Orders;

SELECT * FROM Order_Items;
```

### 4. Update Order Status

Order status can be modified using `UPDATE`.

```sql
UPDATE Orders
SET Order_Status = 'Confirmed'
WHERE Order_ID = 2001;
```

This allows the system to track changes in the order lifecycle.

### 5. Update Quantity and Price

Order item details can also be updated.

```sql
UPDATE Order_Items
SET Quantity = 2
WHERE Order_Item_ID = 1;
```

Price modifications can also be performed using SQL update operations.

---

## Customer-Order History

The project uses `JOIN` operations to combine information from:

* `Customer`
* `Orders`
* `Order_Items`

This generates a customer's order history containing:

* Customer ID
* Customer Name
* Order ID
* Order Date
* Product ID
* Quantity
* Price
* Subtotal

---

## Customer-wise Order Summary

The project uses aggregate functions such as:

```sql
COUNT()
SUM()
GROUP BY
ORDER BY
```

to calculate:

* Total number of orders
* Total amount spent by each customer

---

## SQL Concepts Used

This project demonstrates several important DBMS concepts:

* Primary Key
* Foreign Key
* NOT NULL Constraint
* CHECK Constraint
* INSERT
* SELECT
* UPDATE
* JOIN
* COUNT()
* SUM()
* GROUP BY
* ORDER BY
* COMMIT

---

## Technologies Used

* Oracle SQL
* SQL Developer / Oracle Database
* DBMS Concepts

---

## Key Features

| Feature             | Description                           |
| ------------------- | ------------------------------------- |
| Customer Management | Connects customers with their orders  |
| Order Management    | Stores and tracks customer orders     |
| Order Items         | Maintains products within each order  |
| Status Tracking     | Tracks order progress                 |
| Amount Tracking     | Stores order and item prices          |
| Relationships       | Uses PK-FK relationships              |
| Reports             | Generates order history and summaries |
| Data Modification   | Supports updating order information   |

---

## Learning Outcomes

Through this project, I learned how to:

* Design relational database tables
* Apply primary and foreign keys
* Establish relationships between tables
* Insert and update database records
* Retrieve data using SQL queries
* Perform table joins
* Use aggregate functions
* Generate useful database reports
* Manage transactions using `COMMIT`

---

## Author

**D. Hasini**

B.Sc. Computer Science with AI

---

## Conclusion

The **Order Management System** demonstrates how SQL and relational database concepts can be used to manage an e-commerce ordering workflow. It provides a structured way to store orders, products, quantities, prices, customer history, and order summaries in an Etsy-style marketplace database.

This version is ready to copy directly into your `README.md`.
