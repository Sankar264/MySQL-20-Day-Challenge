SQL Identifiers
============================================================
SQL Identifiers are names used to identify database objects such as database names,table names,column names,view names,index names,constrains,triggers,stored procedures...etc
Why we are declaring identifiers we have to follow some rules and regulations.

1. The only allowed characters to define identifiers a-z,A-Z,or 0 to 9 ,_,$
2. must be begin with letter or underscore(_)
3. we cant declare identifiers with reserved words.
4. spaces are not considered to declare identifiers.
5. identifiers are case sensitive.
6. max length to declare identifiers are 15 characters.
----------------------------------------------------------------
SQL:-
=================================================================
SQL is a (structured query language) is standardized programming language specially designed for managing and manipulating relational databases . it provides a decleartive syntax it allows user to definewhat they want to retrive, insert, update, or delete without specifying exactly how databases should execute these operations.
----------------------------------------------------------------

SQL Commands
============================================================
DDL	DML	DCL	TCL	DQL
CREATE	INSERT	GRANT	COMMIT	SELECT
ALTER	UPDATE	REVOKE	ROLLBACK	
DROP	DELETE		SAVEPOINT	
TRUNCATE				
RENAME				


DDL(DATA DEFINATION LANGUAGE)
DDL:-data definition language
DDL commands are used to define,create,modify and delete the structure of a database objects such as databases,tables,views,indexes...etc.
create:- by using these commands to create a new databases,tables,views,indexes..etc.
Alter:-by using alter command we can modify the structure of an existing table.like(add column,drop,column, rename column,modify datatype,add constarints
Drop:- deletes an entire database objects permanently like(databases,tables,view,indexs..etc)
truncate:-by using truncate command delete all records from a table without deleting a table.
rename:-it is used to rename the database object names
=================================================================================
DML(Data Manipulation Language):-
--------------------------------------------------------------------------------
manages data stored within database objects.
Insert:- by using insert command we can insert some records into a table
Update:-by using the update command we can update the records based on some condition
delete:-by using this delete command we can delete some records based on condition
Lock:- controls concurrency by locking 


DCL(DATA CONTROL LANGUAGE)
-----------------------------------------------------------------------------------
manages permission and access control on database objects
Grant:- Gives specific or roleprivilages or permissions(such select,update,insert,delete,all,privilagous) to a database user 
Revoke:-remove previously granted permission from database user or role. restricting their access to database objects.

==========================================================================================
TCL
---------------------------------------------------------
MANAGES transactions to maintain data integrity
COMMIT:-permantly saves all changes made during the current transaction to the database.making them visible to other users.
Rollback:-undo/reverts changes made during the current transcation back to the last commited state or a savepoint in case of an error
Savepoint:-set a temporary market within a transaction to you which you can later rollback,without undoing the entire transaction
================================================================================================
DQL
-------------------------------------------------------------------------------
Used to fetch or retrive data from databases
select:-retrive data from one or more tables or views based on specified columns and conditions.it is the most frequently used command in sql.



HOW TO CREATE DATABASE?
--------------------------------------------
syntax:- Create database database name;
-------------------------------------------
example:-Create database db;
================================
HOW TO DROP DATABASE?
syntax:-
--------------------
drop database databasename;
-----------------------------
example:-DROP DATABASE PFS4;
======================
HOW TO CREATE TABLE?
CREATE TABLE 
=-------------------
CREATE TACLE TABLE-NAME(
column_name data-type(size) constraint,
column_name data-type(size)
column_name data-type(size)
column_name data-type(size)
);
 
