TCL:-(Transactional control language)
def
-------------------------------
The process of combining all related operations into a single unit and executing them according to the rule "either all operations should be succeed or none should be succeed", is called Transaction Management.

A transaction is consider a single unit of work and follows the principle
"either all or none"
example:- Funds transfer
consider a money transfer process between two accounts.
1. debit amount from the sender's account
2. credit amount into the receiver's account.

Both Operations should be executed as a single transaction.
if the amount is debited from the sender's account successfully. but crediting the recover's account fails.it may lead to the data inconsistency problems.

there are two types of transactions such as
1) Local Transactions
----------------------
in local transactions, all operations of a transaction are executed in the same database.
example:-
----------
funds transfer from one account to another where both accounts belongs to the same bank.
2) Global Transactions
----------------------
operations of a transactions are executed on different databases.
example
-------
Funds transfer from one account to another account where both accounts belongs to the different databases.
example
---------
Funds transfer from one account to another account where both accounts belongs to the different bank

ACID Properties
---------------

Atomicity:-All or Nothing  
Consistency:-The database remains in a valid state
Isolation:-Transactions do not interface with each other
Durability:- Committed changes are permanent

ACID Properties in DBMS
Last Updated : 6 Mar, 2026
Transactions are fundamental operations that allow us to modify and retrieve data. However, to ensure the integrity of a database, it is important that these transactions are executed in a way that maintains consistency, correctness, and reliability even in the case of failures/errors. This is where the ACID properties come into play.

acid_properties
1. Atomicity
Atomicity means a transaction is all-or-nothing either all its operations succeed, or none are applied. If any part fails, the entire transaction is rolled back to keep the database consistent.

Commit: If the transaction is successful, the changes are permanently applied.
Abort/Rollback: If the transaction fails, any changes made during the transaction are discarded.
Example: Consider the following transaction T consisting of T1 and T2 : Transfer of $100 from account X to account Y .

atomicity
Atomicity
If the transaction fails after completion of T1 but before completion of T2, the database would be left in an inconsistent state. With Atomicity, if any part of the transaction fails, the entire process is rolled back to its original state, and no partial changes are made.

2. Consistency
Consistency in transactions means that the database must remain in a valid state before and after a transaction.

A valid state follows all defined rules, constraints, and relationships (like primary keys, foreign keys, etc.).
If a transaction violates any of these rules, it is rolled back to prevent corrupt or invalid data.
If a transaction deducts money from one account but doesn't add it to another (in a transfer), it violates consistency.
Example: Suppose the sum of all balances in a bank system should always be constant. Before a transfer, the total balance is $700. After the transaction, the total balance should remain $700. If the transaction fails in the middle (like updating one account but not the other), the system should maintain its consistency by rolling back the transaction.

Total before T occurs = 500 + 200 = 700 .
Total after T occurs = 400 + 300 = 700 .

isolation
Consistency
3. Isolation
Isolation ensures that transactions run independently without affecting each other. Changes made by one transaction are not visible to others until they are committed.

It ensures that the result of concurrent transactions is the same as if they were run one after another, preventing issues like:

Dirty reads: reading uncommitted data
Non-repeatable reads: data changes between two reads
Phantom reads: new rows appear during a transaction
ACID
Isolation
Example: Consider two transactions T and T''.

X = 500, Y = 500
Explanation:

1. Transaction T:
T wants to transfer $50 from X to Y.
T reads Y (value: 500), deducts $50 from X (new X = 450), and adds $50 to Y (new Y = 550).
2. Transaction T'':
T'' starts and reads X (500) and Y (500).
It calculates the sum: 500 + 500 = 1000.
Meanwhile, values of X and Y change to 450 and 550 respectively.
So, the correct sum should be 450 + 550 = 1000.
Isolation ensures that T'' does not read outdated values while another transaction (T) is still in progress.
Transactions should be independent, and T'' should access the final values only after T commits.
This avoids inconsistent results, like the incorrect sum calculated by T''.
4. Durability:
Durability ensures that once a transaction is committed, its changes are permanently saved, even if the system fails. The data is stored in non-volatile memory, so the database can recover to its last committed state without losing data.

Example: After successfully transferring money from Account A to Account B, the changes are stored on disk. Even if there is a crash immediately after the commit, the transfer details will still be intact when the system recovers, ensuring durability.
ACID PROPERThttps://www.geeksforgeeks.org/dbms/acid-properties-in-dbms/IES

Commit
----------
mysql> use psf4
ERROR 1049 (42000): Unknown database 'psf4'
mysql> show databases;
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
6 rows in set (0.07 sec)

mysql> usepfs4
    -> ^C
mysql> use pfs4
Database changed
mysql> CREATE TABLE EMPLOYEE(
    -> EMP_ID INT PRIMARY KEY,
    -> EMP_NAME VARCHAR(30),
    -> SALARY DECIMAL(10,2)
    -> );
Query OK, 0 rows affected (0.05 sec)

mysql> SELECT * FROM EMPLOYEE;
Empty set (0.01 sec)

mysql> DESC EMPLOYEE;
+----------+---------------+------+-----+---------+-------+
| Field    | Type          | Null | Key | Default | Extra |
+----------+---------------+------+-----+---------+-------+
| EMP_ID   | int           | NO   | PRI | NULL    |       |
| EMP_NAME | varchar(30)   | YES  |     | NULL    |       |
| SALARY   | decimal(10,2) | YES  |     | NULL    |       |
+----------+---------------+------+-----+---------+-------+
3 rows in set (0.02 sec)

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO EMPLOYEE VALUES(110,'SANKAR',30000);
Query OK, 1 row affected (0.01 sec)

mysql> INSERT INTO EMPLOYEE VALUES(111,'SAI',30400);
Query OK, 1 row affected (0.00 sec)

mysql> COMMIT;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 30000.00 |
|    111 | SAI      | 30400.00 |
+--------+----------+----------+
2 rows in set (0.00 sec)

mysql> UPDATE EMPLOYEE SET SALARY=40000 WHERE EMP_ID=110;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 40000.00 |
|    111 | SAI      | 30400.00 |
+--------+----------+----------+
2 rows in set (0.00 sec)

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> UPDATE EMPLOYEE SET SALARY=100000 WHERE EMP_ID=111;
Query OK, 1 row affected (0.01 sec)
Rows matched: 1  Changed: 1  Warnings: 0

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+-----------+
| EMP_ID | EMP_NAME | SALARY    |
+--------+----------+-----------+
|    110 | SANKAR   |  40000.00 |
|    111 | SAI      | 100000.00 |
+--------+----------+-----------+
2 rows in set (0.00 sec)

mysql> ROLLBACK;
Query OK, 0 rows affected (0.01 sec)

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 40000.00 |
|    111 | SAI      | 30400.00 |
+--------+----------+----------+
2 rows in set (0.00 sec)

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO EMPLOYEE VALUES(333,'SARKAR',40000);
Query OK, 1 row affected (0.01 sec)

mysql> UPDATE EMPLOYEE SET SALARY=SALARY+5000 WHERE SALARY>=20000;
Query OK, 3 rows affected (0.01 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 45000.00 |
|    111 | SAI      | 35400.00 |
|    333 | SARKAR   | 45000.00 |
+--------+----------+----------+
3 rows in set (0.00 sec)

mysql> DELETE FROM EMPLOYEE WHERE EMP_ID=111;
Query OK, 1 row affected (0.00 sec)

mysql> ROLLBACK;
Query OK, 0 rows affected (0.01 sec)

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 40000.00 |
|    111 | SAI      | 30400.00 |
+--------+----------+----------+
2 rows in set (0.00 sec)

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> INSERT INTO EMPLOYEE VALUES(333,'SARKAR',40000);
Query OK, 1 row affected (0.01 sec)

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 40000.00 |
|    111 | SAI      | 30400.00 |
|    333 | SARKAR   | 40000.00 |
+--------+----------+----------+
3 rows in set (0.00 sec)

mysql> UPDATE EMPLOYEE SET SALARY=SALARY+5000 WHERE SALARY>=20000;
Query OK, 3 rows affected (0.00 sec)
Rows matched: 3  Changed: 3  Warnings: 0

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 45000.00 |
|    111 | SAI      | 35400.00 |
|    333 | SARKAR   | 45000.00 |
+--------+----------+----------+
3 rows in set (0.00 sec)

mysql> SAVEPOINT SP4;
Query OK, 0 rows affected (0.01 sec)

mysql> DELETE FROM EMPLOYEE WHERE EMP_ID=111;
Query OK, 1 row affected (0.00 sec)

mysql> ROLLBACK TO SP4;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM EMPLOYEE;
+--------+----------+----------+
| EMP_ID | EMP_NAME | SALARY   |
+--------+----------+----------+
|    110 | SANKAR   | 45000.00 |
|    111 | SAI      | 35400.00 |
|    333 | SARKAR   | 45000.00 |
+--------+----------+----------+
3 rows in set (0.00 sec)
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
6 rows in set (0.01 sec)

mysql> CREATE DATABASE LOCK_DEMO;
Query OK, 1 row affected (0.02 sec)

mysql> USE LOCK_DEMO;
Database changed
mysql> CREATE TABLE EMPLOYEE(
    -> EMPID INT PRIMARY KEY.
    -> ^C
mysql> CREATE TABLE EMPLOYEE(
    -> EMPID INT PRIMARY KEY,
    -> EMP_NAME VARCHAR(30),
    -> SALARY DECIMAL(10,2),
    -> DEPARTMENT VARCHAR(20)
    -> );
Query OK, 0 rows affected (0.03 sec)

mysql> DESC EMPLOYEE;
+------------+---------------+------+-----+---------+-------+
| Field      | Type          | Null | Key | Default | Extra |
+------------+---------------+------+-----+---------+-------+
| EMPID      | int           | NO   | PRI | NULL    |       |
| EMP_NAME   | varchar(30)   | YES  |     | NULL    |       |
| SALARY     | decimal(10,2) | YES  |     | NULL    |       |
| DEPARTMENT | varchar(20)   | YES  |     | NULL    |       |
+------------+---------------+------+-----+---------+-------+
4 rows in set (0.00 sec)

mysql> INSERT INTO EMPLOYEE VALUES
    -> (101,'SANKAR',10000,'CSE'),
    -> (102,'KUMAR',20000,'EEE'),
    -> (103,'ROHIT',30000,'ECE');
Query OK, 3 rows affected (0.01 sec)
Records: 3  Duplicates: 0  Warnings: 0

mysql> SELECT * FROM EMPLOYEE;
+-------+----------+----------+------------+
| EMPID | EMP_NAME | SALARY   | DEPARTMENT |
+-------+----------+----------+------------+
|   101 | SANKAR   | 10000.00 | CSE        |
|   102 | KUMAR    | 20000.00 | EEE        |
|   103 | ROHIT    | 30000.00 | ECE        |
+-------+----------+----------+------------+
3 rows in set (0.00 sec)

mysql> 
mysql> ^C
mysql> LOCK TABLES EMPLOYEE WRITE;
Query OK, 0 rows affected (0.00 sec)

mysql> UNLOCK TABLES;
Query OK, 0 rows affected (0.00 sec)

mysql> LOCK TABLES EMPLOYEE READ;
Query OK, 0 rows affected (0.00 sec)

mysql> UNLOCK TABLES;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM EMPLOYEE;
+-------+----------+----------+------------+
| EMPID | EMP_NAME | SALARY   | DEPARTMENT |
+-------+----------+----------+------------+
|   101 | SANKAR   | 60000.00 | CSE        |
|   102 | KUMAR    | 20000.00 | EEE        |
|   103 | ROHIT    | 30000.00 | ECE        |
+-------+----------+----------+------------+
3 rows in set (0.00 sec)

mysql> SELECT * FROM EMPLOYEE WHERE EMPID=101 FOR UPDATE;
+-------+----------+----------+------------+
| EMPID | EMP_NAME | SALARY   | DEPARTMENT |
+-------+----------+----------+------------+
|   101 | SANKAR   | 60000.00 | CSE        |
+-------+----------+----------+------------+
1 row in set (0.00 sec)

mysql> START TRANSACTION;
Query OK, 0 rows affected (0.00 sec)

mysql> SELECT * FROM EMPLOYEE WHERE EMPID=101 FOR UPDATE;
+-------+----------+----------+------------+
| EMPID | EMP_NAME | SALARY   | DEPARTMENT |
+-------+----------+----------+------------+
|   101 | SANKAR   | 60000.00 | CSE        |
+-------+----------+----------+------------+
1 row in set (0.00 sec)

mysql> COMMIT;
Query OK, 0 rows affected (0.00 sec)

mysql> 


WHAT IS LOCKING:-
----------------------
LOCKING IS A MECHANISM USED BY THE DATABASE TO CONTROL CONCURRENT ACCESS DATA.
IT ENSURES THAT MULTIPLE USERS ACCESS THE SAME DATA SIMULTANOUS THE DATABASE MAINTAINS CONSISTENCY, INTEGRITY, AND PREVENT CONFLICTS.
 1. SHARED LOCK
A SHARED LOCK ALLOWS A TRNSACTION TO READ DATA.
MULTIPLE USERS CAN HOLD A SHARED LOCK ON THE SAME ROW
NO TRANSACTION CN MODIFY THE ROW UNTIL ALL SHARED LOCKS ARE RELEASED.

CHARACTERISTICS
READ ONLY
MULTIPLE USERS CAN READ SIMUNTANEOUSLY
BLOCKS UPDATES AND DELETE

2.Exclusive lock
-----------------
Defination

An Exclusive Lock allows a transaction to modify data.
while an Exclusive Lock exists:
No other transaction can read using a locking read or modify that row.
Only the transistion holding the lock can updte/delete the data.

Characteristics
Used for INSERT,UPDATE,DELETE
only one exclusive Lock at a time'
Block both reads (locking reads) and writes

3. intent lock
______
def
_
An intent lock is a table level lock that indicates a transaction intends to place row level
locks.
it helps MySQL quickly determines whether a table level lock conflicts with existing row locks.
users do not usually create intent locks manually. InnoDB manages them automatically.

Real life example
imagine a library :
shared lock -> many students can read the same book at the same time.
exxclusive-> one student borrows the book , so nobody else can read ar borrow it until it is 
returned.
intent lock-> the librarian marks that someone is about to read or borrow books from a shelf , helping coorodinates access without checking every book individuality.
