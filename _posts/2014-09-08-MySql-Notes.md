---
layout: post
title: Mysql Notes
tags: Databases 
category: Tech
---

### Beginner Stuff ###

#### Login ####

~~~
mysql -p
~~~

#### Show all users ####

~~~
Select user, host from mysql.user;
~~~

#### Add User ####

~~~
CREATE USER 'newuser'@'localhost' IDENTIFIED BY 'password';
~~~

#### Give User Priveledges ####

~~~
GRANT ALL PRIVILEGES ON * . * TO 'newuser'@'localhost';
~~~

#### Show Databases ####

~~~
show databases;
~~~

#### Create Database ####

~~~ 
create database dbName;
~~~

#### Use Database ####

~~~
use dbName;
~~~

#### Show Tables in a Database ####

~~~
show tables;
~~~

#### Create Table ####

~~~
create table tableName (tableNameId serial primary key);
~~~

#### Add value to table ####

~~~
Insert into tableName (tableNameId) Values (1234);
~~~

#### Show Columns of a table ####

~~~
show columns from TableName;
~~~

#### Execute a sql file ####

~~~
source fileName;
~~~

#### Foreign Key Constraints ####

~~~
 create table parentTable (
	id int not null primary key);

 create table relatedTable (
	id int not null primary key, 
	parent_id int not null, 
	foreign key fk_invoices(parent_id) references parentTable(id));
~~~

#### Adding a column to an existing table ####

~~~
alter table tableName
	add columnName text
~~~

#### Renaming a column in an existing table ####

~~~
alter table tableName
	change oldColumnName newColumnName int
~~~

#### Ensuring a key is Unique ####

~~~
 create table parentTable (
	id int not null primary key,
	unique key (id));
~~~

#### Deleting items from a table ####

~~~
 delete from Table
~~~

### Joins ###

Inner Join - produces a set of records that which match in both tables  
Left Join - produces a set of records that match every entry in the left table regardless of any matching entry in the right table  
Right Join - produces a set of records that match every entry in the right table regardless of any matching entry in the left table  
Outer Join - produces a set of all records in both tables regardless of whether they match or not

**Note outer join is not implemented in MySql because it is deemed not to be that useful, however you can roll your own outer join using a left and right join if you want**

[For a more detailed explanation read this post](http://www.sitepoint.com/understanding-sql-joins-mysql-database/)

~~~
 select table1.id, table2.id
	from table1
	inner join table2 on table1.id = table2.id;
~~~

### Stored Procedures ###

#### Stored Procedure Basics ####

~~~
 DELIMITER //
 CREATE PROCEDURE GetAllProducts()
   BEGIN
   SELECT *  FROM invoices;
   END //
 DELIMITER ;
~~~
Makes a stored procedure

~~~
CALL GetAllProducts();
~~~
Executes a stored procedure

~~~
select db, name from mysql.proc;
~~~
Shows all stored procedures available

~~~
drop procedure GetAllProducts;
~~~
Deletes the stored procedure

#### Stored Procedure Variables ####

~~~
DECLARE total_count INT DEFAULT 0
SET total_count = 10;
~~~
Stored procedures are scoped within the begin / end that they reside

~~~
DELIMITER //
CREATE PROCEDURE GetStuff(IN minId int)
    BEGIN
        SELECT * FROM invoices WHERE id > minId;
    END //
DELIMITER ;
~~~
Stored proc with a parameter declaration

[For more info see this post](http://www.mysqltutorial.org/stored-procedures-parameters.aspx)


### References ###

[Everything you need to get started with mysql](http://code.tutsplus.com/tutorials/everything-you-need-to-get-started-with-mysql--net-3076)
[Foreign Keys](http://www.mysqltutorial.org/mysql-foreign-key/)
