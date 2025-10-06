# 🏨 Hotel Management System (SQL Project)

Welcome to my **Hotel Management System** project — a complete SQL-based database designed to manage hotel operations including **bookings, customers, rooms, staff, and payments**.  

This project was built as part of my learning journey in **Data Analytics and Database Management**, and it helped me understand how SQL can turn raw data into powerful business insights.

---

## 💡 Project Overview

The **Hotel Management System** database is designed to simulate real-world hotel operations using structured SQL tables, relationships, and queries.

The goal of this project was to:
- Understand **database design** and **data relationships**.
- Practice **SQL queries**, **views**, **joins**, **subqueries**, and **triggers**.
- Build a working database that can answer practical business questions.

---

## 🧩 Key Features

✅ **Fully normalized database design**  
✅ **Relationships between all entities (1-M, M-M)**  
✅ **Advanced SQL queries** (joins, subqueries, group by, having, etc.)  
✅ **Views** for simplified data access  
✅ **Triggers** for automation (like deleting linked payments)  
✅ **Practical use cases** for analytics and reporting  

---

## 🗃️ Database Schema

| Table | Description |
|--------|--------------|
| **Customers** | Stores customer information like name, contact, and city. |
| **Rooms** | Contains details of hotel rooms such as type, price, and capacity. |
| **Bookings** | Manages room bookings with customer and staff references. |
| **Payments** | Tracks payment method, amount, and associated booking. |
| **Staff** | Holds staff details including role, phone, and email. |

### 🧱 Example Structure
```sql
CREATE TABLE Customers (
  CustomerID INT PRIMARY KEY AUTO_INCREMENT,
  FirstName VARCHAR(50),
  LastName VARCHAR(50),
  City VARCHAR(50),
  Phone VARCHAR(15),
  Email VARCHAR(100)
);

CREATE TABLE Rooms (
  RoomID INT PRIMARY KEY AUTO_INCREMENT,
  RoomType VARCHAR(50),
  PricePerNight DECIMAL(10,2),
  Capacity INT
);
# 🏨 Hotel Management System (SQL Project)

Welcome to my **Hotel Management System** project — a complete SQL-based database designed to manage hotel operations including **bookings, customers, rooms, staff, and payments**.  

This project was built as part of my learning journey in **Data Analytics and Database Management**, and it helped me understand how SQL can turn raw data into powerful business insights.

---

## 💡 Project Overview

The **Hotel Management System** database is designed to simulate real-world hotel operations using structured SQL tables, relationships, and queries.

The goal of this project was to:
- Understand **database design** and **data relationships**.
- Practice **SQL queries**, **views**, **joins**, **subqueries**, and **triggers**.
- Build a working database that can answer practical business questions.

---

## 🧩 Key Features

✅ **Fully normalized database design**  
✅ **Relationships between all entities (1-M, M-M)**  
✅ **Advanced SQL queries** (joins, subqueries, group by, having, etc.)  
✅ **Views** for simplified data access  
✅ **Triggers** for automation (like deleting linked payments)  
✅ **Practical use cases** for analytics and reporting  

---

## 🗃️ Database Schema

| Table | Description |
|--------|--------------|
| **Customers** | Stores customer information like name, contact, and city. |
| **Rooms** | Contains details of hotel rooms such as type, price, and capacity. |
| **Bookings** | Manages room bookings with customer and staff references. |
| **Payments** | Tracks payment method, amount, and associated booking. |
| **Staff** | Holds staff details including role, phone, and email. |

### 🧱 Example Structure
```sql
CREATE TABLE Customers (
  CustomerID INT PRIMARY KEY AUTO_INCREMENT,
  FirstName VARCHAR(50),
  LastName VARCHAR(50),
  City VARCHAR(50),
  Phone VARCHAR(15),
  Email VARCHAR(100)
);

CREATE TABLE Rooms (
  RoomID INT PRIMARY KEY AUTO_INCREMENT,
  RoomType VARCHAR(50),
  PricePerNight DECIMAL(10,2),
  Capacity INT
);
1️⃣ Find All Suite Rooms Under ₹7000
SELECT RoomType, PricePerNight 
FROM Rooms 
WHERE RoomType = 'Suite' AND PricePerNight < 7000;
2️⃣ Identify Top 3 Customers by Spending
SELECT C.FirstName, C.LastName, SUM(B.TotalAmount) AS TotalSpent
FROM Customers C
JOIN Bookings B ON C.CustomerID = B.CustomerID
GROUP BY C.CustomerID
ORDER BY TotalSpent DESC
LIMIT 3;
3️⃣ List Customers Who Made More Than 5 Bookings
SELECT CustomerID, COUNT(*) AS TotalBookings
FROM Bookings
GROUP BY CustomerID
HAVING COUNT(*) > 5;
4️⃣ Create a View for Staff Contact Details
CREATE VIEW StaffContact AS
SELECT FirstName, LastName, Role, Phone
FROM Staff;
5️⃣ Trigger to Auto Delete Payments When a Booking Is Deleted
CREATE TRIGGER DeletePaymentAfterBooking
AFTER DELETE ON Bookings
FOR EACH ROW
DELETE FROM Payments WHERE BookingID = OLD.BookingID;
📈 Real-World Scenarios Implemented

Finance Team – Calculate average amount per payment method.

Receptionist – Find rooms available under ₹7000.

Admin – Get all customers from Mumbai for targeted campaigns.

HR Team – View staff roles, contact, and city.

Analytics – Find cities with most customers or high-value bookings.

Each query represents an actual business question — showing how data turns into decisions.

🧠 What I Learned

✨ Designing normalized relational databases.
✨ Writing complex queries involving joins, subqueries, and aggregations.
✨ Creating triggers and views for automation and simplification.
✨ Translating business logic into data logic.
✨ Presenting SQL results in a clean, analytical way.

This project taught me that SQL is not just about syntax — it’s about thinking in data.

