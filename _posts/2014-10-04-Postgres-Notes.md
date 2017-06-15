---
layout: post
title: Postgres Notes
tags: Databases
category: Tech
---

### Beginner Stuff ###

#### User accounts ####

~~~
sudo su - postgres
~~~
Uses the system user account postgress

~~~
psql DBName
~~~
Opens the specific db

### Psql

Show databases in postgres
~~~
\l
~~~

Show tables in a db
~~~
\dt

SELECT * FROM pg_catalog.pg_tables;
~~~

Change a table name
~~~
ALTER TABLE oldTableName RENAME TO newTableName;
~~~

#### Display Indexes ####

in psql

~~~
\di
~~~

#### Display Table Schema ####

in psql  

~~~
\d+ tablename
~~~

in general sql  

~~~
select column_name, data_type, character_maximum_length
from INFORMATION_SCHEMA.COLUMNS where table_name = '<name of table>';
~~~

#### Inner Joins ####

~~~
select cities.*, country_name From cities inner join countries on cities.country_code = countries.country_code;
~~~

#### Importing Sql ####

in psql

~~~
\i fileToAdd.sql
~~~
