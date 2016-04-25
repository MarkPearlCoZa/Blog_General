---
layout: post
title: MsSql Notes
tags: Useful
category: Tech
---

### Beginner Stuff ###

#### Commenting ####

~~~
/* this is a comment */
~~~

#### Set Database ####

~~~
use DatabaseName
~~~

#### Permissions ####

It can be tricky to know who to give what permission. For a detailed explanation see [this article](http://www.mssqltips.com/sqlservertip/1900/understanding-sql-server-fixed-database-roles/). I've copied a summary of the points below.

##### db_owner #####

- The db_owner role allows a user to do anything within the database.
- DBAs who are already members of the sysadmin fixed server role come in as dbo and don't need this role explicitly granted to them.
- Normal users should not be a member of this role.
- Applications might require their user account to be a member of this role.

##### db_securityadmin #####

- The db_accessadmin role can allow access into or block access to the database for logins.
- Again, since DBAs usually manage security and have an appropriate server-level role, this role is little used.
- Normal users should not be a member of this role.
- Applications should tend not to need this role.
- This is another role you should audit for membership exceptions.

##### db_ddladmin #####

- The db_ddladmin role can create, drop, and alter objects within the database, regardless of who the owner is.
- The db_ddladmin role cannot alter security.
- It is not unusual to grant this role to developers in a non-production environment.
- Normal users should not be a member of this role.
- Applications should not need this role.
- No one should normally be a member of this role on a production database.

##### db_backupoperator #####

- The db_backupoperator role allows a user to take backups of the database.
- Most 3rd party backup utilities utilize methods that require sysadmin rights, which this doesn't give.
- Another role that is little used because this functionality is usually handled by DBAs or a service account.
- Normal users should not be a member of this role.
- Applications should tend not to need this role, though I have seen exceptions.

##### db_datareader #####

- The db_datareader role gives implicit access to SELECT against all tables and views in a database.
- In SQL Server 2005 and up, an explicit DENY will block access to objects.
- It is not unusual to see this role used in production for developers.
- It is not unusual to see this role used in production for normal users.
- Applications will occasionally need this role.
- Creating a user-defined database role and explicitly defining permissions is still preferred over the use of this role.

##### db_datawriter #####

- The db_datawriter role gives implicit access to INSERT, UPDATE, and DELETE against all tables and views in a database.
- In SQL Server 2005 and up, an explicit DENY will block access to objects.
- Typically developer are not members of this role in production unless all users are.
- While less common than with db_datareader, it is not all that unusual to see this role used in production for normal users.
- Applications will occasionally need this role.
- Creating a user-defined database role and explicitly defining permissions is still preferred over the use of this role.

##### db_denydatareader #####

- The db_denydatareader role is denied access to SELECT against any table or view in the database.
- Typically this role is not used.
- The DENY is implicit.
- Creating a user-defined database role and explicitly defining permissions is still preferred over the use of this role.

##### db_denydatawriter #####

- The db_denydatawriter role is denied access to INSERT, UPDATE, or DELETE against all tables and views in the database.
- Typically this role is not used.
- The DENY is implicit.
- Creating a user-defined database role and explicitly defining permissions is still preferred over the use of this role.

#### Understanding Schemas ####

Think of a schema as a container to organize objects and simplify granting permissions as opposed to the earlier notion of owner.

[detailed explanation here...](http://www.sqlteam.com/article/understanding-the-difference-between-owners-and-schemas-in-sql-server)  

### Temporary Tables ###

You can create a temporary table and insert data into it.

For example, a temporary table valid for your sp session can be create as follows...

~~~
create table #Temp
(	
    exampleId int,
	exampleText Varchar(255)
)
~~~

You can create a global temporary table  

~~~
create table ##Temp
(	
    exampleId int,
	exampleText Varchar(255)
)
~~~

You can insert data into the table, e.g.

~~~
insert into #Temp select 1, 'example text'
~~~

### Working with Nulls ###

You can do the following in a where statement...

~~~
Where Field is Null
Where Field is Not Null
~~~

### Joins ###

[see this post for interesting details](http://stackoverflow.com/questions/38549/difference-between-inner-and-outer-joins)  

Assume you have the following tables...  

~~~
drop table #Temp
drop table #Temp2

create table #Temp
(	
    itemValue int,	
)

insert into #Temp (itemValue) 
values 
	(1),
	(2),
	(3),
	(4)

create table #Temp2
(
	itemValue int,		
)

insert into #Temp2 (itemValue) 
values 
	(3),	
	(4),
	(5),
	(6)
~~~

#### Inner Join ####

~~~
select T1.itemValue, T2.itemValue from #Temp as T1 inner join #Temp2 as T2 on T1.itemValue = T2.itemValue
~~~

~~~
itemValue	itemValue
3	3
4	4
~~~

#### Left Outer Join  ####

~~~
select T1.itemValue, T2.itemValue from #Temp as T1 left outer join #Temp2 as T2 on T1.itemValue = T2.itemValue
~~~

~~~
itemValue	itemValue
1	NULL
2	NULL
3	3
4	4
~~~

#### Right Outer Join ####

~~~
select T1.itemValue, T2.itemValue from #Temp as T1 right outer join #Temp2 as T2 on T1.itemValue = T2.itemValue
~~~

~~~
itemValue	itemValue
3	3
4	4
NULL	5
NULL	6
~~~

#### Full Outer Join ####

~~~
select T1.itemValue, T2.itemValue from #Temp as T1 full outer join #Temp2 as T2 on T1.itemValue = T2.itemValue
~~~

~~~
itemValue	itemValue
1	NULL
2	NULL
3	3
4	4
NULL	5
NULL	6
~~~

#### Joining on the same table ####

Note, it can be done! Google for examples.

### Dynamic Queries using Schema ###

~~~
select TABLE_Schema, TABLE_NAME into #TempTable from Information_Schema.TABLES
 
select TABLE_NAME, TABLE_SCHEMA, ('select * from ' + TABLE_SCHEMA + '.' + TABLE_NAME + ' where ' + TABLE_SCHEMA + '.' +TABLE_NAME + '.id = 145348') from #TempTable
~~~

### Check that a column exists in a table ###

~~~
IF NOT EXISTS(SELECT * FROM INFORMATION_SCHEMA.COLUMNS
       WHERE
              TABLE_SCHEMA = 'BSM' AND
              TABLE_NAME = 'Adjustments' AND
              COLUMN_NAME = 'PortfolioLevelAdjustment')
BEGIN
       ALTER TABLE BSM.Adjustments
              ADD PortfolioLevelAdjustment BIT DEFAULT(0)
END
GO
~~~

### Sections to add more detail on viewed in Mark Long's video series ###

[Learning Microsoft Transact Sql by Mark Long](http://shop.oreilly.com/product/0636920038290.do)

Adding a primary key
Inner and outer joins
Refreshing intellisense
Aggregate Functions
Having and Where
Select into
Insert Select
Variables
Case Statements
Stored Procs vs Functions
Clustered vs Non-Clustered Indexes

#### Show Running Queries ####

~~~
SELECT sqltext.TEXT
                ,req.session_id
                ,req.STATUS
                ,req.command
                ,req.cpu_time
                ,req.total_elapsed_time / 1000 / 60 AS [Running Minutes],
                blocking_session_id AS [Blocked By]--,
                --db.name
FROM sys.dm_exec_requests req
CROSS APPLY sys.dm_exec_sql_text(sql_handle) AS sqltext
~~~

### References ###

[Learning Microsoft Transact Sql by Mark Long](http://shop.oreilly.com/product/0636920038290.do)
