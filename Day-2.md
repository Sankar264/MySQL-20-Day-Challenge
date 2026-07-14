===================================================Day-2===========================================

1Q.What are the differences between File Management System(FMS) and Database Management System (DBMS)

\-------------------------------------------------------------------------------------------------

1. high data redundancy

&#x20;  reduce data redundancy



2\. difficult to maintain and update

&#x20;  easy to maintain and update



3\. security is limited

&#x20; provides strong security mechanism



4\. data sharing is difficult

&#x20;  multiple users can access data simultaneously



5\. no relationship between files

&#x20;  supports relationship between tables.



6\. backup and recovery is difficult

&#x20;  provides backup and recovery features.



7\. suitable for small applications.

&#x20;  suitable for small, medium and large applications.

==========================================================================================================

Q2 what is difference between a file system and a DBMS

\----------------------------------------------------------------------------------------------------------------

a file system stores data in separate files mays lies to data reduency ,and security issues .ADBMS stores data in a Structured Manner using tables, reduces redundancy ,provides security, supports multiple users, and ensures data consistency and integrity

============================================================================================================

Q3 what is Data,field,record,database

\-----------------------------------------------------------------------------------------------------------

Data:-

raw facts or figures without context

example:- 101,sankar,60000

field:-

smallest unit of data in database(column/attribute)

example:- empid,empname,empsalary,empaddress

record:-

collection of releated fields(row/tuple)

exam:-101,sankar,600000

============================================================================================

what is database

\---------------------------------------------------------------------------------------------

organized collection of related records stored together,

example:-

in employee database contain all employee details.

=====================================================================================================

what is DBMS

\-----------------------------------------------------------------------------------------------------------

ADBMS is  asoftware used to create ,store,retrive, update and manage databases

=========================================================================================================





Client-server Architecture

\---------------------------------------------------------------------------------------------------------------

in client server architecture there are three components

1. client
2. server
3. protocol

|client:-The role of the client in client-server arch is send request to the server ,and get response from the server.|
|-|
|server:-server is the software the role of the server in client-server-arch is to take request from clients if the request is valid request then it will generate some responces we can handover that responce to client.if the client request is not a valid request then it will raise the errors|
|protocol:-it has a set of rules and regulations. the role of the protocol in Client-server arch is send request from client to server|

=================================================================================================================================

Data models in DBMS

\----------------------------------------

&#x20;*a data model defines how data is stored organized and manipulated in a database.*

1. *Physical Data Model:-*

*-------------------------------------------------------*

*describes how data is physically stored in storage devices*

*audiences:-Database Administrators*

*2. Logical Data Models*

*------------------------------------------------------------*

*defines the structure of data(entities,attributes,releationships) independent of physical storage areas.*

*audiences:-developers and database architects.*

*3. Hierarchal Data Model*

*-----------------------------------------------------------------------*

*data is represented as a tree structure(parent child relationship).*

*example:-company-->departments-->employees*

*4.network Data Model*

*--------------------------------------------------------------------*

*Data is represented as graph with records (nodes) and relationships(edges).*

*examples:-student enrolled in multiple courses,courses teach by multiple professors.*

*5. Relational Data Models(RDMS)*

*------------------------------------------------------*

*data is stored in tables(relations)with rows (tuple) and colums(attributes)*

*example:*

*student(id,name,marks,dept\_id)*

*departments(debt\_id,debt\_name)*













&#x20;

