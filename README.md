```sql
-- E-COMMERCE SQL PROJECT
-- Three tables: customers, orders, order_items
```

```sql
-- CREATING DATABASE
CREATE DATABASE e_commerce;
```

```sql
-- USING DATABASE
USE e_commerce;
```

```sql
-- CREATING TABLE: customers
CREATE TABLE customers (
	customer_id INT PRIMARY KEY,
	name VARCHAR(100),
	city VARCHAR(50),
	email VARCHAR(100),
	signup_date DATE
);
```

```sql
-- INSERTING DATA INTO: customers
INSERT INTO customers (customer_id, name, city, email, signup_date)
VALUES
	(1, 'Aarav Shah', 'Mumbai', 'aarav@mail.com', '2022-03-15'),
	(2, 'Priya Mehta', 'Delhi', 'priya@mail.com', '2022-06-20'),
	(3, 'Rohit Verma', 'Bangalore', 'rohit@mail.com', '2023-01-10'),
	(4, 'Sneha Joshi', 'Pune', 'sneha@mail.com', '2023-04-05'),
	(5, 'Karan Patel', 'Ahmedabad', 'karan@mail.com', '2023-07-22'),
	(6, 'Divya Nair', 'Chennai', 'divya@mail.com', '2023-09-01'),
	(7, 'Amit Kumar', 'Mumbai', 'amit@mail.com', '2023-11-14'),
	(8, 'Pooja Sharma', 'Delhi', 'pooja@mail.com', '2024-01-08'),
	(9, 'Vikram Singh', 'Jaipur', 'vikram@mail.com', '2024-02-17'),
	(10, 'Meena Iyer', 'Chennai', 'meena@mail.com', '2024-03-25'),
	(11, 'Raj Khanna', 'Kolkata', 'raj@mail.com', '2024-04-30'),
	(12, 'Neha Gupta', 'Pune', 'neha@mail.com', '2024-05-12'),
	(13, 'Sanjay Bose', 'Kolkata', 'sanjay@mail.com', '2024-06-18'),
	(14, 'Anita Reddy', 'Hyderabad', 'anita@mail.com', '2024-07-22'),
	(15, 'Deepak Rao', 'Bangalore', 'deepak@mail.com', '2024-08-05');
```

```sql
-- CREATING TABLE: orders
CREATE TABLE orders (
	order_id INT PRIMARY KEY,
	customer_id INT,
	order_date DATE,
	status VARCHAR(20),
	total_amount DECIMAL(10, 2),
	FOREIGN KEY (customer_id) REFERENCES customers (customer_id)
);
```

```sql
-- INSERTING DATA INTO: orders
INSERT INTO orders (order_id, customer_id, order_date, status, total_amount)
VALUES
	(101, 1, '2024-01-05', 'Delivered', 2500.00),
	(102, 2, '2024-01-12', 'Delivered', 1800.00),
	(103, 1, '2024-02-01', 'Delivered', 3200.00),
	(104, 3, '2024-02-14', 'Cancelled', 950.00),
	(105, 4, '2024-03-03', 'Delivered', 4100.00),
	(106, 5, '2024-03-20', 'Pending', 760.00),
	(107, 2, '2024-04-02', 'Delivered', 2200.00),
	(108, 6, '2024-04-15', 'Delivered', 1350.00),
	(109, 7, '2024-05-01', 'Delivered', 5600.00),
	(110, 8, '2024-05-18', 'Pending', 890.00),
	(111, 3, '2024-06-07', 'Delivered', 1400.00),
	(112, 9, '2024-06-22', 'Cancelled', 620.00),
	(113, 10, '2024-07-04', 'Delivered', 3300.00),
	(114, 4, '2024-07-19', 'Delivered', 2750.00),
	(115, 11, '2024-08-02', 'Pending', 480.00),
	(116, 1, '2024-08-20', 'Delivered', 1900.00),
	(117, 12, '2024-09-05', 'Delivered', 6200.00),
	(118, 13, '2024-09-18', 'Cancelled', 340.00),
	(119, 14, '2024-10-01', 'Delivered', 2100.00),
	(120, 15, '2024-10-15', 'Pending', 730.00);
```

```sql
-- CREATING TABLE: order_items
CREATE TABLE order_items (
	item_id INT PRIMARY KEY,
	order_id INT,
	product_name VARCHAR(100),
	category VARCHAR(50),
	quantity INT,
	unit_price DECIMAL(10, 2),
	FOREIGN KEY (order_id) REFERENCES orders (order_id)
);
```

```sql
-- INSERTING DATA INTO: order_items
INSERT INTO order_items (
	item_id,
	order_id,
	product_name,
	category,
	quantity,
	unit_price
)
VALUES
	(1, 101, 'Laptop', 'Electronics', 1, 2000.00),
	(2, 101, 'Mouse', 'Electronics', 2, 250.00),
	(3, 102, 'Desk Chair', 'Furniture', 1, 1800.00),
	(4, 103, 'Monitor', 'Electronics', 1, 2500.00),
	(5, 103, 'HDMI Cable', 'Electronics', 2, 350.00),
	(6, 104, 'Keyboard', 'Electronics', 1, 950.00),
	(7, 105, 'Standing Desk', 'Furniture', 1, 3500.00),
	(8, 105, 'Webcam', 'Electronics', 1, 600.00),
	(9, 106, 'Headphones', 'Electronics', 1, 760.00),
	(10, 107, 'Office Lamp', 'Furniture', 2, 600.00),
	(11, 107, 'Notebook', 'Stationery', 5, 80.00),
	(12, 107, 'Pen Set', 'Stationery', 3, 120.00),
	(13, 108, 'Bookshelf', 'Furniture', 1, 1350.00),
	(14, 109, 'MacBook Pro', 'Electronics', 1, 5000.00),
	(15, 109, 'USB Hub', 'Electronics', 2, 300.00),
	(16, 110, 'Notebook', 'Stationery', 10, 80.00),
	(17, 110, 'Sticky Notes', 'Stationery', 3, 30.00),
	(18, 111, 'Office Chair', 'Furniture', 1, 1400.00),
	(19, 112, 'Mousepad', 'Electronics', 1, 120.00),
	(20, 112, 'USB Cable', 'Electronics', 2, 250.00),
	(21, 113, 'Printer', 'Electronics', 1, 3300.00),
	(22, 114, 'Sofa', 'Furniture', 1, 2500.00),
	(23, 114, 'Cushion Set', 'Furniture', 2, 125.00),
	(24, 115, 'Pen Set', 'Stationery', 4, 120.00),
	(25, 116, 'Tablet', 'Electronics', 1, 1900.00),
	(26, 117, 'Gaming PC', 'Electronics', 1, 5500.00),
	(27, 117, 'Gaming Chair', 'Furniture', 1, 700.00),
	(28, 118, 'Stapler', 'Stationery', 2, 85.00),
	(29, 118, 'Paper Ream', 'Stationery', 2, 85.00),
	(30, 119, 'Smart TV', 'Electronics', 1, 2100.00),
	(31, 120, 'Floor Lamp', 'Furniture', 1, 730.00),
	(32, 103, 'Mouse Pad', 'Electronics', 1, 350.00),
	(33, 105, 'Desk Organizer', 'Stationery', 2, 0.00),
	(34, 107, 'Highlighter', 'Stationery', 4, 50.00),
	(35, 109, 'Laptop Stand', 'Electronics', 1, 300.00);
```

```sql
-- ANSWERING BUSINESS QUESTIONS
-- EASY
-- 1) Retrieve all columns and rows from the customers table.
SELECT
	*
FROM customers;
```

```sql
-- 2) Show only the name and city of all customers.
SELECT
	name,
	city
FROM customers;
```

```sql
-- 3) List all unique cities where customers are located.
SELECT DISTINCT
	city
FROM customers;
```

```sql
-- 4) Find all orders with a total_amount greater than 2000.
SELECT
	*
FROM orders
WHERE total_amount > 2000;
```

```sql
-- 5) Show all orders with status = 'Cancelled'.
SELECT
	*
FROM orders
WHERE status = 'Cancelled';
```

```sql
-- 6) List all orders sorted by total_amount from highest to lowest.
SELECT
	*
FROM orders
ORDER BY total_amount DESC;
```

```sql
-- 7) Get the 5 most recent orders by order_date.
SELECT
	*
FROM orders
ORDER BY order_date DESC
LIMIT 5;
```

```sql
-- 8) Count the total number of orders in the orders table.
SELECT
	COUNT(*) AS total_orders
FROM orders;
```

```sql
-- 9) Find the total revenue and average order value from all orders.
SELECT
	SUM(total_amount) AS total_revenue,
	ROUND(AVG(total_amount), 2) AS avg_order_value
FROM orders;
```

```sql
-- 10) What is the cheapest and most expensive unit_price in order_items?
SELECT
	MIN(unit_price) AS cheapest_unit,
	MAX(unit_price) AS most_expensive_unit
FROM order_items;
```

```sql
-- MEDIUM
-- 11) Count how many orders each customer has placed. Show customer_id and order count.
SELECT
	customer_id,
	COUNT(*) AS no_of_orders
FROM orders
GROUP BY customer_id
ORDER BY no_of_orders DESC;
```

```sql
-- 12) Find customers who have placed more than 1 order.
SELECT
	customer_id,
	COUNT(*) AS no_of_orders
FROM orders
GROUP BY customer_id
HAVING COUNT(*) > 1;
```

```sql
-- 13) Show total quantity sold and total revenue per product category in order_items.
-- Note: total_revenue = SUM(quantity * unit_price)
SELECT
	category,
	SUM(quantity) AS total_quantity,
	SUM(quantity * unit_price) AS total_revenue
FROM order_items
GROUP BY category;
```

```sql
-- 14) List each order with the customer's name and city.
SELECT
	o.order_id,
	c.customer_id,
	c.name,
	c.city,
	o.order_date,
	o.total_amount,
	o.status
FROM orders AS o
JOIN customers AS c
	ON o.customer_id = c.customer_id;
```

```sql
-- 15) Show customer name, order_date, product_name, and unit_price for every item ordered.
SELECT
	c.name,
	o.order_date,
	oi.product_name,
	oi.unit_price
FROM customers AS c
JOIN orders AS o
	ON c.customer_id = o.customer_id
JOIN order_items AS oi
	ON o.order_id = oi.order_id;
```

```sql
-- 16) Find customers who have never placed any order.
SELECT
	c.customer_id,
	c.name
FROM customers AS c
LEFT JOIN orders AS o
	ON c.customer_id = o.customer_id
WHERE o.order_id IS NULL;
```

```sql
-- 17) Find all orders where total_amount is above the average order value.
SELECT
	*
FROM orders
WHERE total_amount > (
	SELECT
		AVG(total_amount)
	FROM orders
);
```

```sql
-- 18) Label each order as 'Low' (< 1000), 'Medium' (1000–3000), or 'High' (> 3000).
SELECT
	*,
	CASE
		WHEN total_amount < 1000 THEN 'Low'
		WHEN total_amount BETWEEN 1000 AND 3000 THEN 'Medium'
		ELSE 'High'
	END AS order_quality
FROM orders;
```

```sql
-- 19) List all customers who signed up in 2024.
SELECT
	*
FROM customers
WHERE YEAR(signup_date) = 2024;
```

```sql
-- 20) For each customer, show their name and the total amount they have spent across all orders.
SELECT
	c.customer_id,
	c.name,
	SUM(o.total_amount) AS total_spent
FROM customers AS c
LEFT JOIN orders AS o
	ON c.customer_id = o.customer_id
GROUP BY
	c.customer_id,
	c.name
ORDER BY total_spent DESC;
```

```sql
-- 21) Use a CTE to find the top 3 best-selling products by total revenue (quantity * unit_price).
WITH t1 AS (
	SELECT
		product_name,
		SUM(quantity * unit_price) AS total_revenue
	FROM order_items
	GROUP BY product_name
	ORDER BY total_revenue DESC
	LIMIT 3
)
SELECT
	*
FROM t1;
```

```sql
-- 22) Find the city that has generated the highest total order revenue.
SELECT
	c.city,
	SUM(o.total_amount) AS city_revenue
FROM customers AS c
JOIN orders AS o
	ON c.customer_id = o.customer_id
GROUP BY c.city
ORDER BY city_revenue DESC
LIMIT 1;
```

```sql
-- 23) For each customer who has placed at least 2 orders, show their name, number of orders, total spent,
--     and average order value. Sort by total spent descending.
SELECT
	c.name,
	COUNT(o.order_id) AS order_count,
	SUM(o.total_amount) AS total_spent,
	AVG(o.total_amount) AS avg_order_value
FROM customers AS c
JOIN orders AS o
	ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name
HAVING COUNT(o.order_id) >= 2
ORDER BY total_spent DESC;
```

```sql
-- Rank customers by their total spending (highest = rank 1) using a window function.
SELECT c.name,
       SUM(o.total_amount) AS total_spent,
       RANK() OVER (ORDER BY SUM(o.total_amount) DESC) AS spend_rank
FROM customers c
JOIN orders o ON c.customer_id = o.customer_id
GROUP BY c.customer_id, c.name;
```
