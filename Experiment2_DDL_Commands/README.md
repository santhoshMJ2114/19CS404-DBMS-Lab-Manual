# Experiment 2: DDL Commands

## AIM
To study and implement DDL commands and different types of constraints.

## THEORY

### 1. CREATE
Used to create a new relation (table).

**Syntax:**
```sql
CREATE TABLE (
  field_1 data_type(size),
  field_2 data_type(size),
  ...
);
```
### 2. ALTER
Used to add, modify, drop, or rename fields in an existing relation.
(a) ADD
```sql
ALTER TABLE std ADD (Address CHAR(10));
```
(b) MODIFY
```sql
ALTER TABLE relation_name MODIFY (field_1 new_data_type(size));
```
(c) DROP
```sql
ALTER TABLE relation_name DROP COLUMN field_name;
```
(d) RENAME
```sql
ALTER TABLE relation_name RENAME COLUMN old_field_name TO new_field_name;
```
### 3. DROP TABLE
Used to permanently delete the structure and data of a table.
```sql
DROP TABLE relation_name;
```
### 4. RENAME
Used to rename an existing database object.
```sql
RENAME TABLE old_relation_name TO new_relation_name;
```
### CONSTRAINTS
Constraints are used to specify rules for the data in a table. If there is any violation between the constraint and the data action, the action is aborted by the constraint. It can be specified when the table is created (using CREATE TABLE) or after it is created (using ALTER TABLE).
### 1. NOT NULL
When a column is defined as NOT NULL, it becomes mandatory to enter a value in that column.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) NOT NULL
);
```
### 2. UNIQUE
Ensures that values in a column are unique.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) UNIQUE
);
```
### 3. CHECK
Specifies a condition that each row must satisfy.
Syntax:
```sql
CREATE TABLE Table_Name (
  column_name data_type(size) CHECK (logical_expression)
);
```
### 4. PRIMARY KEY
Used to uniquely identify each record in a table.
Properties:
Must contain unique values.
Cannot be null.
Should contain minimal fields.
Syntax:

```sql
CREATE TABLE Table_Name (
  column_name data_type(size) PRIMARY KEY
);
```

### 5. FOREIGN KEY
Used to reference the primary key of another table.
Syntax:

```sql
CREATE TABLE Table_Name (
  column_name data_type(size),
  FOREIGN KEY (column_name) REFERENCES other_table(column)
);
```

### 6. DEFAULT
Used to insert a default value into a column if no value is specified.

Syntax:
```sql
CREATE TABLE Table_Name (
  col_name1 data_type,
  col_name2 data_type,
  col_name3 data_type DEFAULT 'default_value'
);
```

**Question 1**
--
![Screenshot083718](https://github.com/user-attachments/assets/9432f76c-51f4-40dc-9248-99f9d8210e58)

```sql
ALTER TABLE employee RENAME COLUMN id TO employee_id;```
```

**Output:**

![image](https://github.com/user-attachments/assets/5d9790ca-f653-4e6f-b627-7ef1d6bb5660)

**Question 2**
---
![Screensho 084035](https://github.com/user-attachments/assets/7ef3ba55-6bec-4686-93d6-b4ccb31dabed)


```sql
CREATE TABLE Events (
    EventID INTEGER,
    EventName TEXT,
    EventDate DATE
);
```
**Output:**

![image](https://github.com/user-attachments/assets/fb92eb74-8ffe-49bc-87d6-8a9fbe5892c7)

**Question 3**
---
![image](https://github.com/user-attachments/assets/7be0c906-7fe3-40e5-8bbf-a3f980097c22)

```sql
CREATE TABLE Invoices(
    InvoiceID INTEGER,
    InvoiceDate DATE,
    Amount REAL CHECK (Amount > 0),
    DueDate DATE CHECK (DueDate > InvoiceDate),
    OrderID INTEGER,
    FOREIGN KEY (OrderID) REFERENCES Orders(orderID)
);
```

**Output:**

![image](https://github.com/user-attachments/assets/ec5b7254-e809-48c8-bf10-3da81f7545fe)

**Question 4**
---

```sql
CREATE TABLE products (
    product_id INTEGER,
    product_name TEXT NOT NULL,
    list_price DECIMAL(10,2) NOT NULL ,
    discount decimal (10,2) default 0 not null,
    check(list_price>= 0 AND discount >=0 AND List_price >= discount)
    
);
```

**Output:**
![Screenshot 9 084610](https://github.com/user-attachments/assets/036c7966-99c4-4c95-8c2e-3d1d3ae20045)


**Question 5**
---
![image](https://github.com/user-attachments/assets/9ccb0324-67db-4021-87f7-e16d9bd92c73)

```sql
INSERT INTO Employee (EmployeeID, Name, Department, Salary) SELECT EmployeeID, Name, Department, Salary FROM Former_employees;
```

**Output:**
![Screenshot084802](https://github.com/user-attachments/assets/419b9370-2eed-47f9-93c7-8aaa675b3089)


**Question 6**
---
![Screenshot 084837](https://github.com/user-attachments/assets/615638e9-cd87-4521-8260-612584149454)


```sql
CREATE TABLE Shipments(
    ShipmentID INTEGER,
    ShipmentDate DATE,
    SupplierID Integer,
    OrderID INTEGER,
    FOREIGN KEY (SupplierID) REFERENCES Suppliers(SupplierID),
    FOREIGN KEY (OrderID) REFERENCES Orders(orderID)
);
```

**Output:**
![Screenshot 084919](https://github.com/user-attachments/assets/a4df0f4b-dc0a-4d05-87e0-eaf679619db2)


**Question 7**
---
![Screenshot84947](https://github.com/user-attachments/assets/61e8326b-9106-42aa-a21f-7a0fe3120ff0)

```sql
ALTER TABLE Employees ADD COLUMN salary INTEGER CHECK(salary > 0);
```

**Output:**
![image](https://github.com/user-attachments/assets/572c13c0-3388-42e0-b0eb-9f4e874fc970)

**Question 8**
---
![image](https://github.com/user-attachments/assets/e1706f24-ec56-4b18-aa71-5d50431f5ce5)

```sql
INSERT INTO Products(ProductID, Name, Category, Price, Stock) 
VALUES  
    (106, 'Fitness Tracker','Wearables', NULL, NULL), 
    (107, 'Laptop', 'Electronic', 999.99, 50), 
    (108, 'Wireless Earbud', 'Accessorie', NULL,100)
```

**Output:**

![image](https://github.com/user-attachments/assets/63d5ff0a-70fc-4c8b-8b0f-beead96a3d1c)

**Question 9**
---
![image](https://github.com/user-attachments/assets/20dffa8d-75c6-4014-911c-a7791742f8ed)

```sql
INSERT INTO Books(ISBN,Title,Author,Publisher,Year) 
values
    ('978-1234567890', 'Data Science Essentials', 'Jane Doe', 'TechBooks', 2024);
```

**Output:**

![image](https://github.com/user-attachments/assets/cfe0e1a4-9369-4b12-8e90-e2adf720678d)

**Question 10**
---
![image](https://github.com/user-attachments/assets/84af64fc-ada2-470f-8f6b-4ecc56f350fb)

```sql
CREATE TABLE contacts(
    contact_id INTEGER PRIMARY KEY,
    first_name text not null,
    last_name text not null,
    email text, 
    phone text not null check(length(phone) >=10)
);
```

**Output:**

![Screenshot](https://github.com/user-attachments/assets/70b2ef43-652f-4d0f-846f-f49fc7b7992e)


## RESULT
Thus, the SQL queries to implement different types of constraints and DDL commands have been executed successfully.
