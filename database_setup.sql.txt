//CREATING DATABASE
CREATE DATABASE retail_project;
USE retail_project;

//CREATING TABLES
CREATE TABLE Customers(
    customer_id INT PRIMARY KEY,
    name VARCHAR(50),
    city VARCHAR(50),
    signup_date DATE
);

CREATE TABLE Products(
    product_id INT PRIMARY KEY,
    product_name VARCHAR(50),
    category VARCHAR(50),
    price DECIMAL(10,2)
);

CREATE TABLE Orders(
    order_id INT PRIMARY KEY,
    customer_id INT,
    order_date DATE,
    total_amount DECIMAL(10,2),
    FOREIGN KEY (customer_id) REFERENCES Customers(customer_id)
);

CREATE TABLE Order_Items(
    order_item_id INT PRIMARY KEY,
    order_id INT,
    product_id INT,
    quantity INT,
    FOREIGN KEY (order_id) REFERENCES Orders(order_id),
    FOREIGN KEY (product_id) REFERENCES Products(product_id)
);

//INSERTING DATA 
INSERT INTO Customers VALUES
(1,'Rahul','Delhi','2023-01-10'),
(2,'Ananya','Mumbai','2023-02-15'),
(3,'Amit','Lucknow','2023-03-20'),
(4,'Sneha','Bangalore','2023-04-01');

INSERT INTO Products VALUES
(101,'Laptop','Electronics',60000),
(102,'Phone','Electronics',30000),
(103,'Shoes','Fashion',2000),
(104,'Watch','Accessories',5000);

INSERT INTO Orders VALUES
(1001,1,'2023-05-01',65000),
(1002,2,'2023-05-03',32000),
(1003,1,'2023-05-05',2000),
(1004,3,'2023-05-07',5000);

INSERT INTO Order_Items VALUES
(1,1001,101,1),
(2,1001,103,2),
(3,1002,102,1),
(4,1003,103,1),
(5,1004,104,1);