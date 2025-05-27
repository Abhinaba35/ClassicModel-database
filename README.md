# ClassicModels Database Project

The **ClassicModels** database is a sample relational SQL database for a retailer of scale models of classic cars, motorcycles, planes, ships, and trains. It captures real-world business scenarios such as managing customers, products, orders, payments, employees, and office locations.

This project is implemented using **MySQL** and includes an ER diagram, full schema creation script, and optional sample data and queries.

---

## 📦 Project Structure

```plaintext
classicmodels-database/
├── README.md
├── classicmodels_schema.sql       # Full schema creation script
├── sample_data.sql                # Optional sample data (if available)
├── queries/
│   └── useful_queries.sql         # Optional useful SQL queries
├── docs/
│   └── ERD.png                    # ER diagram of the database
└── data/
    ├── customers.csv              # Sample customer data
    └── products.csv
```

---

## 🧩 Database Schema Overview

The schema contains the following tables:

| Table Name     | Description                                               |
|----------------|-----------------------------------------------------------|
| `offices`      | Stores data about company offices                         |
| `employees`    | Stores employee data and hierarchy (who reports to whom)  |
| `customers`    | Stores customer data including credit limits              |
| `productlines` | Stores types of products offered                          |
| `products`     | Stores product details like name, vendor, and pricing     |
| `orders`       | Stores customer orders with status and shipment dates     |
| `orderdetails` | Stores line items for each order (products + quantities)  |
| `payments`     | Stores payment details made by customers                  |

Each table includes appropriate foreign key constraints to maintain relational integrity.

---

## 🖼️ ER Diagram

A visual representation of the schema is available in the `docs/` folder:

📷 **`ERD.png`**

---

## 🔧 How to Set Up

1. **Install MySQL Server** (if not already installed):
   ```bash
   sudo apt install mysql-server   # For Ubuntu/Debian
   ```

2. **Open MySQL terminal**:
   ```bash
   mysql -u root -p
   ```

3. **Run the schema script**:
   ```sql
   SOURCE path/to/classicmodels_schema.sql;
   ```

4. (Optional) **Insert sample data**:
   ```sql
   SOURCE path/to/sample_data.sql;
   ```

5. **Start querying**:
   ```sql
   USE ClassicModels;
   SELECT * FROM customers;
   ```

---

## 🧠 Use Cases

- Demonstrates normalized relational database design
- Good for SQL practice (joins, aggregations, subqueries)
- Ideal for learning about business data models and relationships

---

## 💡 Example SQL Queries

```sql
-- List all customers from USA
SELECT customerName, country FROM customers WHERE country = 'USA';

-- Total orders placed per customer
SELECT customerNumber, COUNT(*) AS totalOrders
FROM orders
GROUP BY customerNumber;

-- Get employee hierarchy
SELECT e.firstName AS employee, m.firstName AS manager
FROM employees e
LEFT JOIN employees m ON e.reportsTo = m.employeeNumber;
```

More queries can be found in `queries/useful_queries.sql`.

---

## 📚 License

This is a sample educational database, originally inspired by MySQL classicmodels example. Free to use for academic and learning purposes.

---

## 🙌 Author

Created by [Your Name]  
For educational and demonstration purposes.
