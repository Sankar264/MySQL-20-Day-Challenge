mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| college            |
| company            |
| db4                |
| details            |
| information_schema |
| mysql              |
| performance_schema |
| practice           |
| psf4               |
| school1            |
| student            |
| students           |
| sys                |
| walmartsales       |
| xyz                |
+--------------------+
15 rows in set (0.06 sec)

mysql> USE DB4;
Database changed
mysql> SHOW TABLES;
+---------------+
| Tables_in_db4 |
+---------------+
| backupemp     |
| company_staff |
| emp           |
| emp2          |
| emp_3         |
| employees     |
| orders        |
| product_      |
| products      |
| projects      |
| students      |
| studentscores |
+---------------+
12 rows in set (0.03 sec)

mysql> CREATE TABLE sales (
    ->    sale_id INT PRIMARY KEY,
    ->    product VARCHAR(50),
    ->    category VARCHAR(50),
    ->    units_sold INT,
    ->    unit_price INT,
    ->    region VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.08 sec)

mysql> 
mysql> INSERT INTO sales (sale_id, product, category, units_sold, unit_price, region) VALUES
    -> (1,  'Keyboard',    'Electronics', 10, 1200,  'North'),
    -> (2,  'Monitor',     'Electronics', 5,  7000,  'South'),
    -> (3,  'Chair',       'Furniture',   15, 2500,  'North'),
    -> (4,  'Desk',        'Furniture',   7,  4500,  'West'),
    -> (5,  'Mouse',       'Electronics', 20, 800,   'East'),
    -> (6,  'Sofa',        'Furniture',   3,  15000, 'South'),
    -> (7,  'Headphones',  'Electronics', 8,  1800,  'North'),
    -> (8,  'Laptop',      'Electronics', 6,  55000, 'West'),
    -> (9,  'Table',       'Furniture',   12, 6000,  'East'),
    -> (10, 'Fan',         'HomeAppliance', 18, 3000, 'South'),
    -> (11, 'AC',          'HomeAppliance', 4, 35000, 'North'),
    -> (12, 'Cupboard',    'Furniture',   5, 12000, 'West'),
    -> (13, 'Printer',     'Electronics', 9, 9000,  'East'),
    -> (14, 'Bed',         'Furniture',   2, 25000, 'South'),
    -> (15, 'Mobile',      'Electronics', 14, 20000, 'North');
Query OK, 15 rows affected (0.02 sec)
Records: 15  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM SALES;
+---------+------------+---------------+------------+------------+--------+
| sale_id | product    | category      | units_sold | unit_price | region |
+---------+------------+---------------+------------+------------+--------+
|       1 | Keyboard   | Electronics   |         10 |       1200 | North  |
|       2 | Monitor    | Electronics   |          5 |       7000 | South  |
|       3 | Chair      | Furniture     |         15 |       2500 | North  |
|       4 | Desk       | Furniture     |          7 |       4500 | West   |
|       5 | Mouse      | Electronics   |         20 |        800 | East   |
|       6 | Sofa       | Furniture     |          3 |      15000 | South  |
|       7 | Headphones | Electronics   |          8 |       1800 | North  |
|       8 | Laptop     | Electronics   |          6 |      55000 | West   |
|       9 | Table      | Furniture     |         12 |       6000 | East   |
|      10 | Fan        | HomeAppliance |         18 |       3000 | South  |
|      11 | AC         | HomeAppliance |          4 |      35000 | North  |
|      12 | Cupboard   | Furniture     |          5 |      12000 | West   |
|      13 | Printer    | Electronics   |          9 |       9000 | East   |
|      14 | Bed        | Furniture     |          2 |      25000 | South  |
|      15 | Mobile     | Electronics   |         14 |      20000 | North  |
+---------+------------+---------------+------------+------------+--------+
15 rows in set (0.00 sec)

mysql> SELECT COUNT(*), CATEGORY FROM SALES AS SPC
    -> GROUP BY SPC
    -> HAVING TOTAL_UNITS>20;
ERROR 1054 (42S22): Unknown column 'SPC' in 'group statement'
mysql> SELECT CATERGORY,SUM(UNITS_SOLD) AS SOLD_PER_CATEGORY 
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING SOLD_PER_CATEGORY>20;
ERROR 1054 (42S22): Unknown column 'CATERGORY' in 'field list'
mysql> SELECT CATEGORY,SUM(UNITS_SOLD) AS SOLD_PER_CATEGORY 
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING SOLD_PER_CATEGORY>20;
+---------------+-------------------+
| CATEGORY      | SOLD_PER_CATEGORY |
+---------------+-------------------+
| Electronics   |                72 |
| Furniture     |                44 |
| HomeAppliance |                22 |
+---------------+-------------------+
3 rows in set (0.03 sec)

mysql> SELECT REGION,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING REVENUE>50000;
+--------+---------+
| REGION | REVENUE |
+--------+---------+
| North  |  483900 |
| South  |  184000 |
| West   |  421500 |
| East   |  169000 |
+--------+---------+
4 rows in set (0.01 sec)

mysql> SELECT CATEGORY,COUNT(PRODUCT) AS PRODUCT_COUNT
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING PRODUCT_COUNT>2
    -> ;
+-------------+---------------+
| CATEGORY    | PRODUCT_COUNT |
+-------------+---------------+
| Electronics |             7 |
| Furniture   |             6 |
+-------------+---------------+
2 rows in set (0.01 sec)

mysql> SELECT CATEGORY,AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVR_PRICE<5000;
ERROR 1054 (42S22): Unknown column 'AVR_PRICE' in 'having clause'
mysql> SELECT CATEGORY,AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVG_PRICE<5000;
Empty set (0.01 sec)

mysql> -- REGIONS WITH MORETHAN 1 ELECTRONICS PRODUCTS
mysql> SELECT REGION,COUNT(UNITS_SOLD) AS RWMOP
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING RWMOP>1;
+--------+-------+
| REGION | RWMOP |
+--------+-------+
| North  |     5 |
| South  |     4 |
| West   |     3 |
| East   |     3 |
+--------+-------+
4 rows in set (0.01 sec)

mysql> SELECT REGION,COUNT(PRODUCT) AS ELECTRONICS_COUNT
    -> FROM SALES
    -> WHERE CATEGORY='ELECTRONICS'
    -> GROUP BY REGION
    -> HAVING ELECTRONICS_COUNT>1;
+--------+-------------------+
| REGION | ELECTRONICS_COUNT |
+--------+-------------------+
| North  |                 3 |
| East   |                 2 |
+--------+-------------------+
2 rows in set (0.01 sec)

mysql> SELECT CATEGORY,SUM(UNITS_SOLD) AS TOTAL_UNITS
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> ORDER BY TOTAL_UNITS DESC;
+---------------+-------------+
| CATEGORY      | TOTAL_UNITS |
+---------------+-------------+
| Electronics   |          72 |
| Furniture     |          44 |
| HomeAppliance |          22 |
+---------------+-------------+
3 rows in set (0.00 sec)

mysql> SELECT REGION,AVG(UNIT_PRICE) AS PRICEPER_REGION
    -> FROM SALES
    -> GROUP BY REGION
    -> ORDER BY PRICEPER_REGION ;
+--------+-----------------+
| REGION | PRICEPER_REGION |
+--------+-----------------+
| East   |       5266.6667 |
| North  |      12100.0000 |
| South  |      12500.0000 |
| West   |      23833.3333 |
+--------+-----------------+
4 rows in set (0.01 sec)

mysql> SELECT CATEGORY,SUM(UNITS_SOLD) AS TOTAL_UNITS
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> ORDER BY TOTAL_UNITS DESC;
+---------------+-------------+
| CATEGORY      | TOTAL_UNITS |
+---------------+-------------+
| Electronics   |          72 |
| Furniture     |          44 |
| HomeAppliance |          22 |
+---------------+-------------+
3 rows in set (0.00 sec)

mysql> SELECT REGION,AVG(UNIT_PRICE) AS PRICEPER_REGION
    -> FROM SALES
    -> GROUP BY REGION
    -> ORDER BY PRICEPER_REGION DESC;
+--------+-----------------+
| REGION | PRICEPER_REGION |
+--------+-----------------+
| West   |      23833.3333 |
| South  |      12500.0000 |
| North  |      12100.0000 |
| East   |       5266.6667 |
+--------+-----------------+
4 rows in set (0.00 sec)

mysql> SELECT REGION,AVG(UNIT_PRICE) AS PRICEPER_REGION
    -> FROM SALES
    -> GROUP BY REGION
    -> ORDER BY PRICEPER_REGION ASC;
+--------+-----------------+
| REGION | PRICEPER_REGION |
+--------+-----------------+
| East   |       5266.6667 |
| North  |      12100.0000 |
| South  |      12500.0000 |
| West   |      23833.3333 |
+--------+-----------------+
4 rows in set (0.00 sec)

mysql> SELECT CATEGORY, SUM(UNITS_SOLD*UNIT_PRICE) AS TOTAL
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> ORDER TOTAL
    -> DESC LIMIT 1;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TOTAL
DESC LIMIT 1' at line 4
mysql> SELECT CATEGORY, SUM(UNITS_SOLD*UNIT_PRICE) AS TOTAL
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> ORDER TOTAL DESC LIMIT 1;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TOTAL DESC LIMIT 1' at line 4
mysql> SELECT CATEGORY, SUM(UNITS_SOLD*UNIT_PRICE) AS TOTAL
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> ORDER TOTAL DESC ;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'TOTAL DESC' at line 4
mysql> SELECT CATEGORY,SUM(UNITS_SOLD * UNIT_PRICE) AS REVENUE
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> ORDER BY REVENUE DESC;
+---------------+---------+
| CATEGORY      | REVENUE |
+---------------+---------+
| Electronics   |  768400 |
| Furniture     |  296000 |
| HomeAppliance |  194000 |
+---------------+---------+
3 rows in set (0.00 sec)

mysql> SELECT REGION, COUNT(PRODUCT) AS PRODUCT_COUNT 
    -> FROM SALES
    -> GROUP BY REGION
    -> ORDER BY PRODUCT_COUNT DESC;
+--------+---------------+
| REGION | PRODUCT_COUNT |
+--------+---------------+
| North  |             5 |
| South  |             4 |
| West   |             3 |
| East   |             3 |
+--------+---------------+
4 rows in set (0.00 sec)

mysql> SELECT REGION,SUM(UNITS_SOLD) AS TOTAL_UNITS
    -> FROM SALES
    -> GROUP BY REGION
    -> ORDER BY REGION;
+--------+-------------+
| REGION | TOTAL_UNITS |
+--------+-------------+
| East   |          41 |
| North  |          51 |
| South  |          28 |
| West   |          18 |
+--------+-------------+
4 rows in set (0.01 sec)

mysql> SELECT REGION,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE 
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING REVENUE>20000
    -> ORDER BY REVENUE;
+--------+---------+
| REGION | REVENUE |
+--------+---------+
| East   |  169000 |
| South  |  184000 |
| West   |  421500 |
| North  |  483900 |
+--------+---------+
4 rows in set (0.00 sec)

mysql> SELECT REGION,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE 
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING REVENUE>20000
    -> ORDER BY REVENUE DESC;
+--------+---------+
| REGION | REVENUE |
+--------+---------+
| North  |  483900 |
| West   |  421500 |
| South  |  184000 |
| East   |  169000 |
+--------+---------+
4 rows in set (0.00 sec)

mysql> SELECT CATEGORY,SUM(UNITS_SOLD) AS TOTAL_SOLD
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING TOTAL_SOLD>10
    -> ORDER BY CATEGORY;
+---------------+------------+
| CATEGORY      | TOTAL_SOLD |
+---------------+------------+
| Electronics   |         72 |
| Furniture     |         44 |
| HomeAppliance |         22 |
+---------------+------------+
3 rows in set (0.00 sec)

mysql> SELECT REGION,COUNT(PRODUCT) AS COUNT_PRODUCTS 
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING COUNT_PRODUCTS >1
    -> ORDER BY ASC;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'ASC' at line 5
mysql> SELECT REGION,COUNT(PRODUCT) AS COUNT_PRODUCTS 
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING COUNT_PRODUCTS >1
    -> ORDER BY COUNT_PRODUCTS ASC;
+--------+----------------+
| REGION | COUNT_PRODUCTS |
+--------+----------------+
| West   |              3 |
| East   |              3 |
| South  |              4 |
| North  |              5 |
+--------+----------------+
4 rows in set (0.00 sec)

mysql> SELECT REGION,COUNT(PRODUCT) AS COUNT_PRODUCTS 
    -> FROM SALES
    -> GROUP BY REGION
    -> HAVING COUNT_PRODUCTS >1
    -> ORDER BY REGION ASC;
+--------+----------------+
| REGION | COUNT_PRODUCTS |
+--------+----------------+
| East   |              3 |
| North  |              5 |
| South  |              4 |
| West   |              3 |
+--------+----------------+
4 rows in set (0.00 sec)

mysql> SELECT CATERGORY , AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVG_PRICE<6000
    -> ORDER BY AVG_PRICE;
ERROR 1054 (42S22): Unknown column 'CATERGORY' in 'field list'
mysql> SELECT CATEGORY , AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVG_PRICE<6000
    -> ORDER BY AVG_PRICE;
Empty set (0.00 sec)

mysql> SELECT CATERGORY,AVG(UNITS
    -> ^C
mysql> SELECT CATERGORY,AVG(UNITS_SOLD) AS AVG_UNITS
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVY_UNITS>5
    -> ORDER BY AVG_UNITS DESC;
ERROR 1054 (42S22): Unknown column 'CATERGORY' in 'field list'
mysql> SELECT CATERGORY,AVG(UNITS_SOLD) AS AVG_UNITS
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVG_UNITS>5
    -> ORDER BY AVG_UNITS DESC;
ERROR 1054 (42S22): Unknown column 'CATERGORY' in 'field list'
mysql> SELECT CATEGORY,AVG(UNITS_SOLD) AS AVG_UNITS
    -> FROM SALES
    -> GROUP BY CATEGORY
    -> HAVING AVG_UNITS>5
    -> ORDER BY AVG_UNITS DESC;
+---------------+-----------+
| CATEGORY      | AVG_UNITS |
+---------------+-----------+
| HomeAppliance |   11.0000 |
| Electronics   |   10.2857 |
| Furniture     |    7.3333 |
+---------------+-----------+
3 rows in set (0.00 sec)

mysql> -- Q1
mysql> SELECT REGION,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE
    -> FROM SALES
    -> WHERE CATEGORY='ELECTRONICS'
    -> GROUP BY REGION
    -> ^C
mysql> SELECT REGION,SUM(UNITS_SOLD) AS TOTAL_UNITS
    -> FROM SALES
    -> WHERE CATEGORY='ELECTRONICS'
    -> GROUP BY REGION
    -> HAVING TOTAL_UNITS>15
    -> ORDER BY TOTAL_UNITS DESC
    -> LIMIT 3;
+--------+-------------+
| REGION | TOTAL_UNITS |
+--------+-------------+
| North  |          32 |
| East   |          29 |
+--------+-------------+
2 rows in set (0.00 sec)

mysql> SELECT REGION,SUM(UNITS_SOLD) AS TOTAL_UNITS
    -> FROM SALES
    -> WHERE CATEGORY='ELECTRONICS'
    -> GROUP BY REGION
    -> HAVING TOTAL_UNITS>15
    -> ORDER BY TOTAL_UNITS DESC
    -> ;
+--------+-------------+
| REGION | TOTAL_UNITS |
+--------+-------------+
| North  |          32 |
| East   |          29 |
+--------+-------------+
2 rows in set (0.00 sec)

mysql> --Q2
    -> SELECT CATEGORY,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE
    -> FROM SALES
    -> WHERE UNIT_PRICE>2000
    -> GROUP BY CATEGORY
    -> HAVING REVENUE>100000
    -> ORDER BY REVENUE DESC;
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near '--Q2
SELECT CATEGORY,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE
FROM SALES
WHERE UNIT' at line 1
mysql> SELECT CATEGORY,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE
    -> FROM SALES
    -> WHERE UNIT_PRICE>2000
    -> GROUP BY CATEGORY
    -> HAVING REVENUE>100000
    -> ORDER BY REVENUE DESC;
+---------------+---------+
| CATEGORY      | REVENUE |
+---------------+---------+
| Electronics   |  726000 |
| Furniture     |  296000 |
| HomeAppliance |  194000 |
+---------------+---------+
3 rows in set (0.00 sec)

mysql> SELECT CATEGORY,AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> WHERE UNITS_SOLD>=5
    -> GROUP BY CATEGORY
    -> HAVING AVG_PRICE>5000
    -> ORDER BY CATERGORY DESC;
ERROR 1054 (42S22): Unknown column 'CATERGORY' in 'order clause'
mysql> SELECT CATEGORY,AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> WHERE UNITS_SOLD>=5
    -> GROUP BY CATEGORY
    -> HAVING AVG_PRICE>5000
    -> ORDER BY CATEGORY DESC;
+-------------+------------+
| CATEGORY    | AVG_PRICE  |
+-------------+------------+
| Furniture   |  6250.0000 |
| Electronics | 13542.8571 |
+-------------+------------+
2 rows in set (0.00 sec)

mysql> SELECT CATEGORY,AVG(UNIT_PRICE) AS AVG_PRICE
    -> FROM SALES
    -> WHERE UNITS_SOLD>=5
    -> GROUP BY CATEGORY
    -> HAVING AVG_PRICE>5000
    -> ORDER BY CATEGORY ASC;
+-------------+------------+
| CATEGORY    | AVG_PRICE  |
+-------------+------------+
| Electronics | 13542.8571 |
| Furniture   |  6250.0000 |
+-------------+------------+
2 rows in set (0.00 sec)

mysql> SELECT CATEGORY,COUNT(PRODUCT) AS COUNT_PRODUCTS
    -> FROM SALES
    -> WHERE REGION IN('NORTH','SOUTH')
    -> GROUP BY CATEGORY
    -> HAVING COUNT_PRODUCT>2
    -> ORDER BY COUNT_PRODUCT DESC;
ERROR 1054 (42S22): Unknown column 'COUNT_PRODUCT' in 'having clause'
mysql> SELECT CATEGORY,COUNT(PRODUCT) AS COUNT_PRODUCTS
    -> FROM SALES
    -> WHERE REGION IN('NORTH','SOUTH')
    -> GROUP BY CATEGORY
    -> HAVING COUNT_PRODUCTS>2
    -> ORDER BY COUNT_PRODUCTS DESC;
+-------------+----------------+
| CATEGORY    | COUNT_PRODUCTS |
+-------------+----------------+
| Electronics |              4 |
| Furniture   |              3 |
+-------------+----------------+
2 rows in set (0.00 sec)

mysql> SELECT REGION,SUM(UNITS_SOLD*UNIT_PRICE) AS REVENUE
    -> FROM SALES
    -> WHERE UNIT_PRICE<10000
    -> GROUP BY REGION
    -> HAVING REVENUE>50000
    -> ORDER BY REVENUE DESC;
+--------+---------+
| REGION | REVENUE |
+--------+---------+
| East   |  169000 |
| South  |   89000 |
| North  |   63900 |
+--------+---------+
3 rows in set (0.00 sec)

mysql> -- SET OPERATORS
mysql> --UNION:COMBINE RESULTS FROM 2 QUERIES AND REMOVES DUPLICATE ROWS. COLUMNS MUST HAVE THE SAME NUMBER AND TYPE.
    -> -- UNION ALL: COMBINE RESULTS FROM 2 QUERIES AND INCLUDING DUPLICATE ROWS. COLUMNS MUST HAVE THE SAME NUMBER AND TYPE.
    -> -- INTERSECT: RETURNS ROWS THAT ARE COMMON TO THE BOTH QUERIES. COLUMNS MUST HAVE THE SAME NUMBER AND TYPE. NOTE:MySQL DOESNT SUPPORT INTERSECT DIRECTLY. 
    -> -- MINUS: RETURNS ROWS FROM THE FIRST QUERY THAT ARE NOT PRESENT IN THE SECOND QUERY. COLUMNS MUST HAVE SAME NUMBER AND TYPE. NOTE:Mysql doesnt support MINU DIRECTLY. 
    -> ^C
mysql> SHOW TABLES;
+---------------+
| Tables_in_db4 |
+---------------+
| backupemp     |
| company_staff |
| emp           |
| emp2          |
| emp_3         |
| employees     |
| orders        |
| product_      |
| products      |
| projects      |
| sales         |
| students      |
| studentscores |
+---------------+
13 rows in set (0.02 sec)

mysql> CREATE TABLE STUDENT(
    -> ^C
mysql> DROP TABLE STUDENTS;
Query OK, 0 rows affected (0.06 sec)

mysql>  student_id INT PRIMARY KEY,
    ->     student_name VARCHAR(50),
    ->     course VARCHAR(50)
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'student_id INT PRIMARY KEY,
    student_name VARCHAR(50),
    course VARCHAR(50)' at line 1
mysql> 
mysql> INSERT INTO Students VALUES
    -> (101,'Rahul','Java Full Stack'),
    -> (102,'Priya','Python Full Stack'),
    -> (103,'Kiran','Data Science'),
    -> (104,'Sneha','Java Full Stack'),
    -> (105,'Ajay','Testing');
ERROR 1146 (42S02): Table 'db4.students' doesn't exist
mysql> 
mysql> 
mysql> CREATE TABLE Placed_Students (
    ->     student_id INT PRIMARY KEY,
    ->     student_name VARCHAR(50),
    ->     company_name VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.04 sec)

mysql> INSERT INTO Placed_Students VALUES
    -> (103,'Kiran','TCS'),
    -> (104,'Sneha','Infosys'),
    -> (105,'Ajay','Wipro'),
    -> (106,'Pooja','Accenture'),
    -> (107,'Ramesh','Capgemini');
Query OK, 5 rows affected (0.02 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM STUDENTS;
ERROR 1146 (42S02): Table 'db4.students' doesn't exist
mysql> SELECT*FROM PLACED_STUDENTS;
+------------+--------------+--------------+
| student_id | student_name | company_name |
+------------+--------------+--------------+
|        103 | Kiran        | TCS          |
|        104 | Sneha        | Infosys      |
|        105 | Ajay         | Wipro        |
|        106 | Pooja        | Accenture    |
|        107 | Ramesh       | Capgemini    |
+------------+--------------+--------------+
5 rows in set (0.00 sec)

mysql> CREATE TABLE Students (
    ->     student_id INT PRIMARY KEY,
    ->     student_name VARCHAR(50),
    ->     course VARCHAR(50)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> 
mysql> INSERT INTO Students VALUES
    -> (101,'Rahul','Java Full Stack'),
    -> (102,'Priya','Python Full Stack'),
    -> (103,'Kiran','Data Science'),
    -> (104,'Sneha','Java Full Stack'),
    -> (105,'Ajay','Testing');
Query OK, 5 rows affected (0.01 sec)
Records: 5  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM STUDENTS;
+------------+--------------+-------------------+
| student_id | student_name | course            |
+------------+--------------+-------------------+
|        101 | Rahul        | Java Full Stack   |
|        102 | Priya        | Python Full Stack |
|        103 | Kiran        | Data Science      |
|        104 | Sneha        | Java Full Stack   |
|        105 | Ajay         | Testing           |
+------------+--------------+-------------------+
5 rows in set (0.00 sec)

mysql> SELECT STUDENT_ID FROM STUDENTS
    -> UNION
    -> SELECT STUDENT_ID FROM PLACED_STUDENTS;
+------------+
| STUDENT_ID |
+------------+
|        101 |
|        102 |
|        103 |
|        104 |
|        105 |
|        106 |
|        107 |
+------------+
7 rows in set (0.02 sec)

mysql> SELECT STUDENT_ID FROM STUDENTS
    -> UNION ALL
    -> SELECT STUDENT_ID FROM PLACED_STUDENTS;
+------------+
| STUDENT_ID |
+------------+
|        101 |
|        102 |
|        103 |
|        104 |
|        105 |
|        103 |
|        104 |
|        105 |
|        106 |
|        107 |
+------------+
10 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTS
    -> UNION
    -> SELECT*FROM PLACED_STUDENTS;
+------------+--------------+-------------------+
| student_id | student_name | course            |
+------------+--------------+-------------------+
|        101 | Rahul        | Java Full Stack   |
|        102 | Priya        | Python Full Stack |
|        103 | Kiran        | Data Science      |
|        104 | Sneha        | Java Full Stack   |
|        105 | Ajay         | Testing           |
|        103 | Kiran        | TCS               |
|        104 | Sneha        | Infosys           |
|        105 | Ajay         | Wipro             |
|        106 | Pooja        | Accenture         |
|        107 | Ramesh       | Capgemini         |
+------------+--------------+-------------------+
10 rows in set (0.00 sec)

mysql> SELECT * FROM STUDENTS
    -> UNION ALL
    -> SELECT*FROM PLACED_STUDENTS;
+------------+--------------+-------------------+
| student_id | student_name | course            |
+------------+--------------+-------------------+
|        101 | Rahul        | Java Full Stack   |
|        102 | Priya        | Python Full Stack |
|        103 | Kiran        | Data Science      |
|        104 | Sneha        | Java Full Stack   |
|        105 | Ajay         | Testing           |
|        103 | Kiran        | TCS               |
|        104 | Sneha        | Infosys           |
|        105 | Ajay         | Wipro             |
|        106 | Pooja        | Accenture         |
|        107 | Ramesh       | Capgemini         |
+------------+--------------+-------------------+
10 rows in set (0.00 sec)

mysql> SELECT STUDENT_ID,STUDENT_NAME FROM STUDENTS
    -> UNION
    -> SELECT STUDENT_ID,STUDENT_NAME FROM PLACED_STUDENTS;
+------------+--------------+
| STUDENT_ID | STUDENT_NAME |
+------------+--------------+
|        101 | Rahul        |
|        102 | Priya        |
|        103 | Kiran        |
|        104 | Sneha        |
|        105 | Ajay         |
|        106 | Pooja        |
|        107 | Ramesh       |
+------------+--------------+
7 rows in set (0.00 sec)

mysql> SELECT STUDENT_ID,STUDENT_NAME FROM STUDENTS
    -> UNION ALL
    -> SELECT STUDENT_ID,STUDENT_NAME FROM PLACED_STUDENTS;
+------------+--------------+
| STUDENT_ID | STUDENT_NAME |
+------------+--------------+
|        101 | Rahul        |
|        102 | Priya        |
|        103 | Kiran        |
|        104 | Sneha        |
|        105 | Ajay         |
|        103 | Kiran        |
|        104 | Sneha        |
|        105 | Ajay         |
|        106 | Pooja        |
|        107 | Ramesh       |
+------------+--------------+
10 rows in set (0.00 sec)

mysql> Terminal close -- exit!
