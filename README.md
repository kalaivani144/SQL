# SQL
Here’s a complete **Task 3 Summary** you can include in your `README.md` or presentation for GitHub or class submission:

---

## 📊 Task 3: SQL for Data Analysis – Summary

### 🎯 Objective:

To perform structured data analysis using SQL queries with the help of **SQLite**. This involved extracting and analyzing information from a set of relational tables using standard SQL operations.

---

### 🛠️ Tools Used:

* **SQLite** (via SQLiteOnline or DB Browser)
* **Python & Matplotlib** (for visualizing output in the PDF)
* **FPDF** (for report generation)
* **GitHub** (for code hosting and documentation)

---

### 🗃️ Database Schema:

Four tables were created:

* `customers(customer_id, name, email)`
* `products(product_id, name, category, price)`
* `orders(order_id, customer_id, order_date, total_amount)`
* `order_items(order_item_id, order_id, product_id, quantity)`

---

### ✅ SQL Features Demonstrated:

| Feature                       | Description                                                   |
| ----------------------------- | ------------------------------------------------------------- |
| `SELECT`, `WHERE`, `ORDER BY` | Retrieve and filter product data (e.g., Electronics by price) |
| `GROUP BY`                    | Count products by category                                    |
| `JOIN` (INNER & LEFT)         | Combine orders with customer details                          |
| Subqueries                    | Identify customers with above-average spending                |
| Aggregate Functions           | Calculate `SUM`, `AVG` for order values                       |
| Views                         | Create a `customer_sales` view to summarize total spent       |
| Indexing                      | Speed up queries by indexing `customer_id` in orders          |

---

### 📄 Deliverables:

* ✅ `sqlite_analysis_script.sql`: Full SQL script with all commands
* ✅ `SQLite_Analysis_Report.pdf`: Output screenshots + query explanation
* ✅ `.png` screenshots of individual query outputs
* ✅ `SQLite_Project_For_GitHub.zip`: All files bundled for GitHub submission

---

### 📦 How to Run:

1. Open [https://sqliteonline.com](https://sqliteonline.com)
2. Paste the contents of `sqlite_analysis_script.sql`
3. Run queries and view outputs
4. Or open the PDF report directly for output previews
[SQLite_Analysis_Report.pdf](https://github.com/user-attachments/files/20508848/SQLite_Analysis_Report.pdf)
[SQLite_Project_For_GitHub.zip](https://github.com/user-attachments/files/20508855/SQLite_Project_For_GitHub.zip)


CODING:

DROP TABLE IF EXISTS order_items;
DROP TABLE IF EXISTS orders;
DROP TABLE IF EXISTS products;
DROP TABLE IF EXISTS customers;

-- Step 1: Create tables
CREATE TABLE customers (
    customer_id INTEGER PRIMARY KEY,
    name TEXT,
    email TEXT
);

CREATE TABLE products (
    product_id INTEGER PRIMARY KEY,
    name TEXT,
    category TEXT,
    price REAL
);

CREATE TABLE orders (
    order_id INTEGER PRIMARY KEY,
    customer_id INTEGER,
    order_date TEXT,
    total_amount REAL
);

CREATE TABLE order_items (
    order_item_id INTEGER PRIMARY KEY,
    order_id INTEGER,
    product_id INTEGER,
    quantity INTEGER
);

-- Step 2: Insert sample data
INSERT INTO customers (name, email) VALUES
('Alice', 'alice@example.com'),
('Bob', 'bob@example.com'),
('Charlie', 'charlie@example.com');

INSERT INTO products (name, category, price) VALUES
('Laptop', 'Electronics', 1200),
('Phone', 'Electronics', 800),
('T-shirt', 'Clothing', 20),
('Shoes', 'Clothing', 50);

INSERT INTO orders (customer_id, order_date, total_amount) VALUES
(1, '2024-01-10', 1220),
(2, '2024-01-12', 800),
(3, '2024-01-15', 70);

INSERT INTO order_items (order_id, product_id, quantity) VALUES
(1, 1, 1),  -- Laptop
(1, 3, 1),  -- T-shirt
(2, 2, 1),  -- Phone
(3, 4, 1);  -- Shoes

-- Step 3: Basic SELECT, WHERE, ORDER BY
SELECT name, price
FROM products
WHERE category = 'Electronics'
ORDER BY price DESC;

-- Step 4: GROUP BY
SELECT category, COUNT(*) AS product_count
FROM products
GROUP BY category;

-- Step 5: INNER JOIN
SELECT o.order_id, c.name, o.total_amount
FROM orders o
JOIN customers c ON o.customer_id = c.customer_id;

-- Step 6: LEFT JOIN
SELECT c.name, o.order_id, o.total_amount
FROM customers c
LEFT JOIN orders o ON c.customer_id = o.customer_id;

-- Step 7: Subquery - customers who spent above average
SELECT DISTINCT customer_id
FROM orders
WHERE total_amount > (SELECT AVG(total_amount) FROM orders);

-- Step 8: Aggregates
SELECT SUM(total_amount) AS total_sales, AVG(total_amount) AS avg_sales
FROM orders;

-- Step 9: Create VIEW
CREATE VIEW customer_sales AS
SELECT customer_id, SUM(total_amount) AS total_spent
FROM orders
GROUP BY customer_id;

-- Step 10: Query the view
SELECT * FROM customer_sales;

-- Step 11: Create INDEX
CREATE INDEX idx_orders_customer_id ON orders(customer_id);
t.sql…]()
![sql 1](https://github.com/user-attachments/assets/51ae3e55-cf37-445a-a002-8bbcb649b81d)
![sql 2](https://github.com/user-attachments/assets/7a75318d-a28a-45c4-937b-f5662e234ada)
![sql 3](https://github.com/user-attachments/assets/fe747a0c-2eb9-47ac-b625-819d89456fdd)
![sql 4](https://github.com/user-attachments/assets/542d3212-0f54-4eca-afff-8292a3f1ac45)

