create database trial;

use trial;
create table department(departmentID int primary key,departmentName varchar(100));
create table employees(id int primary key,Name varchar(100) not null,Email varchar(80) unique,Age int check(Age>=18),departmentID int,salary decimal(8,2) default 80000.00,foreign key(departmentID) references department(departmentID));

insert into department(departmentID, departmentName)values(101,"IT");

insert into employees(id,Name,Email,Age,departmentID)values(1,"Mahesh","mahesh@gmail.com",21,101);

select * from employees;

create table students(id int primary key auto_increment,name varchar(80),address varchar(60),marks int);

insert into students(name,address,marks)values("Sushma","Pune",95),
("Ganesh","Nashik",92),("Sushil","Pune",86),("Shrikant","Nagpur",90);

select marks, avg(marks) as AVGMarks from students group by name;

CREATE TABLE Sales (
    SaleID INT PRIMARY KEY,
    SalesPerson VARCHAR(50),
    Region VARCHAR(30),
    Amount INT
);

INSERT INTO Sales (SaleID, SalesPerson, Region, Amount) VALUES
(1, 'Amit',   'North', 5000),
(2, 'Neha',   'South', 7000),
(3, 'Amit',   'North', 3000),
(4, 'Neha',   'South', 4000),
(5, 'Raj',    'East',  2500),
(6, 'Amit',   'North', 6000),
(7, 'Raj',    'East',  1500),
(8, 'Simran', 'West',  8000),
(9, 'Simran', 'West',  5500),
(10,'Neha',   'South', 3000);

select region, sum(amount) as TotalAmount from Sales group by region;
select region, avg(amount) as avgAmount from sales group by region;

select SalesPerson, max(amount) as maxSale, min(amount) as minSale from Sales group by SalesPerson;
select SalesPerson, count(*) As numberOfSales from sales group by SalesPerson;
select SalesPerson,sum(amount) as TotalSales from Sales group by SalesPerson having sum(amount)>6000;
