mysql> SHOW DATABASES;
+--------------------+
| Database           |
+--------------------+
| db                 |
| information_schema |
| mysql              |
| performance_schema |
| pfs4               |
| sys                |
+--------------------+
6 rows in set (0.12 sec)

mysql> USE PFS4
Database changed
mysql> CREATE TABLE BACKUPEMPLOYEES AS SELECT*FROM EMPLOYEES;
Query OK, 0 rows affected (0.09 sec)
Records: 0  Duplicates: 0  Warnings: 0

mysql> SHOW TABLES;
+-----------------+
| Tables_in_pfs4  |
+-----------------+
| backupemployees |
| company_staff   |
| employees       |
+-----------------+
3 rows in set (0.01 sec)

mysql> DESC BACKUPEMPLOYEES
    -> ;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(40) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
7 rows in set (0.02 sec)

mysql> CREATE TABLE PRODUCT(
    -> PRODUCTID INT AUTO_INCREMENT PRIMARY KEY,
    -> PRODUCTNAME VARCHAR(20),
    -> PRICE DECIMAL(10,2),
    -> QUANTITY INT,
    -> TOTALAMOUNT DECIMAL(10,2) GENERATED ALWAYS AS (PRICE*QUANTITY)STORED
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> DESC BACKUPEMPLOYEES
    -> ;
+-----------+-------------+------+-----+---------+-------+
| Field     | Type        | Null | Key | Default | Extra |
+-----------+-------------+------+-----+---------+-------+
| EMPID     | char(5)     | YES  |     | NULL    |       |
| FIRSTNAME | varchar(30) | YES  |     | NULL    |       |
| LASTNAME  | varchar(40) | YES  |     | NULL    |       |
| AGE       | int         | YES  |     | NULL    |       |
| DOJ       | date        | YES  |     | NULL    |       |
| ADDRESS   | tinytext    | YES  |     | NULL    |       |
| DEPT      | varchar(50) | YES  |     | NULL    |       |
+-----------+-------------+------+-----+---------+-------+
7 rows in set (0.00 sec)

mysql> DESC PRODUCT;
+-------------+---------------+------+-----+---------+------------------+
| Field       | Type          | Null | Key | Default | Extra            |
+-------------+---------------+------+-----+---------+------------------+
| PRODUCTID   | int           | NO   | PRI | NULL    | auto_increment   |
| PRODUCTNAME | varchar(20)   | YES  |     | NULL    |                  |
| PRICE       | decimal(10,2) | YES  |     | NULL    |                  |
| QUANTITY    | int           | YES  |     | NULL    |                  |
| TOTALAMOUNT | decimal(10,2) | YES  |     | NULL    | STORED GENERATED |
+-------------+---------------+------+-----+---------+------------------+
5 rows in set (0.00 sec)

mysql> INSERT INTO PRODUCTS (PRODUCTNAME,PRICE,QUANTITY)VALUES
    -> ('SMART PHONE',19999.99,2),
    -> ('HEADPHONES',39999.89,4);
ERROR 1146 (42S02): Table 'pfs4.products' doesn't exist
mysql> INSERT INTO PRODUCT (PRODUCTNAME,PRICE,QUANTITY)VALUES
    -> ('HEADPHONES',39999.89,4);
Query OK, 1 row affected (0.01 sec)

mysql> ('HEADPHONES',39999.89,4);
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near ''HEADPHONES',39999.89,4)' at line 1
mysql> INSERT INTO PRODUCT (PRODUCTNAME,PRICE,QUANTITY)VALUES
    -> ('SMART PHONE',19999.99,2);
Query OK, 1 row affected (0.00 sec)

mysql> DESC PRODUCT;
+-------------+---------------+------+-----+---------+------------------+
| Field       | Type          | Null | Key | Default | Extra            |
+-------------+---------------+------+-----+---------+------------------+
| PRODUCTID   | int           | NO   | PRI | NULL    | auto_increment   |
| PRODUCTNAME | varchar(20)   | YES  |     | NULL    |                  |
| PRICE       | decimal(10,2) | YES  |     | NULL    |                  |
| QUANTITY    | int           | YES  |     | NULL    |                  |
| TOTALAMOUNT | decimal(10,2) | YES  |     | NULL    | STORED GENERATED |
+-------------+---------------+------+-----+---------+------------------+
5 rows in set (0.00 sec)

mysql> INSERT INTO PRODUCT (PRODUCTNAME,PRICE,QUANTITY)VALUES
    -> ('SMART PHONE',19999.99,2);
Query OK, 1 row affected (0.01 sec)

mysql> SELECT*FROM PRODUCT
    -> ;
+-----------+-------------+----------+----------+-------------+
| PRODUCTID | PRODUCTNAME | PRICE    | QUANTITY | TOTALAMOUNT |
+-----------+-------------+----------+----------+-------------+
|         1 | HEADPHONES  | 39999.89 |        4 |   159999.56 |
|         2 | SMART PHONE | 19999.99 |        2 |    39999.98 |
|         3 | SMART PHONE | 19999.99 |        2 |    39999.98 |
+-----------+-------------+----------+----------+-------------+
3 rows in set (0.00 sec)

mysql> UPDATE PRODUCT SET PRICE=18000.89 WHERE PRODUCTID=2;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT*FROM PRODUCT;
+-----------+-------------+----------+----------+-------------+
| PRODUCTID | PRODUCTNAME | PRICE    | QUANTITY | TOTALAMOUNT |
+-----------+-------------+----------+----------+-------------+
|         1 | HEADPHONES  | 39999.89 |        4 |   159999.56 |
|         2 | SMART PHONE | 18000.89 |        2 |    36001.78 |
|         3 | SMART PHONE | 19999.99 |        2 |    39999.98 |
+-----------+-------------+----------+----------+-------------+
3 rows in set (0.00 sec)

mysql> TRUNCATE TABLE PRODUCT;
Query OK, 0 rows affected (0.03 sec)

mysql> INSERT INTO PRODUCT (PRODUCTNAME,PRICE,QUANTITY)VALUES 
    -> ('HEADPHONES',39999.89,4),
    -> ('HEADPHONES',39999.89,4),
    -> ('HEADPHONES',39999.89,4);
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> CREATE TABLE STUDENTS (
    -> NAME VARCHAR(30),
    -> STUDENTID AUTO_INCREMENT PRIMARY KEY,
    -> SMOB VARCHAR(10),
    -> SMARKS INT(3)
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'AUTO_INCREMENT PRIMARY KEY,
SMOB VARCHAR(10),
SMARKS INT(3)
)' at line 3
mysql> SHOW DATABASES
    -> ;
+--------------------+
| Database           |
+--------------------+
| db                 |
| information_schema |
| mysql              |
| performance_schema |
| pfs4               |
| sys                |
+--------------------+
6 rows in set (0.00 sec)

mysql> CREATE TABLE STUDENTS(
    -> STUDENTID AUTO_INCREMENT PRIMARY KEY,
    -> NAME VARCHAR(30),
    -> SMOB VARCHAR(10),
    -> SMARKS INT(3)
    -> );
ERROR 1064 (42000): You have an error in your SQL syntax; check the manual that corresponds to your MySQL server version for the right syntax to use near 'AUTO_INCREMENT PRIMARY KEY,
NAME VARCHAR(30),
SMOB VARCHAR(10),
SMARKS INT(3)
)' at line 2
mysql> CREATE TABLE STUDENTS(
    -> STUDENTID INT AUTO_INCREMENT PRIMARY KEY,
    -> SMOB VARCHAR(10),
    -> NAME VARCHAR(30),
    -> SMARKS INT(3)
    -> );
Query OK, 0 rows affected, 1 warning (0.03 sec)

mysql> INSERT INTO STUDENTS(NAME,SMOB,SMARKS)VALUES
    -> ('KUMAR','9087559876',99),
    -> ('PRASAD','9084494446',99),
    -> ('ROHITH','9084478446',98),
    -> ('ROHITH','9084477334',77);
Query OK, 4 rows affected (0.01 sec)
Records: 4  Duplicates: 0  Warnings: 0

mysql> SELECT*FROM STUDENTS;
+-----------+------------+--------+--------+
| STUDENTID | SMOB       | NAME   | SMARKS |
+-----------+------------+--------+--------+
|         1 | 9087559876 | KUMAR  |     99 |
|         2 | 9084494446 | PRASAD |     99 |
|         3 | 9084478446 | ROHITH |     98 |
|         4 | 9084477334 | ROHITH |     77 |
+-----------+------------+--------+--------+
4 rows in set (0.00 sec)

mysql> CREATE USER SANKAR IDENTIFIED BY 'SANKAR123';
Query OK, 0 rows affected (0.05 sec)

mysql> CREATE USER BHASHA IDENTIFIED BY 'BHASHA123';
Query OK, 0 rows affected (0.02 sec)

mysql> GRANT SELECT,INSERT,UPDATE ON STUDENTS TO SANKAR;
Query OK, 0 rows affected (0.00 sec)

mysql> GRANT DROP,SELECT,UPDATE ON STUDENTS TO BHASHA;
Query OK, 0 rows affected (0.00 sec)

mysql> REVOKE INSERT,UPDATE ON STUDENTS FROM SANKAR;
Query OK, 0 rows affected (0.01 sec)

mysql> REVOKE UPDATE ON STUDENTS FROM BHASHA;
Query OK, 0 rows affected (0.01 sec)

