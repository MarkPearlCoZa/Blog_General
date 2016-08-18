---
layout: post
title: SqlServer Notes
tags: Windows
category: Tech
---
#### General Notes ####

[Setting up to connect to instance via IP Address](http://dba.stackexchange.com/questions/62165/i-cant-connect-to-my-servers-sql-database-via-an-ip-address)

#### Start / Stop Service from command line ####

Run the command line in administrator mode.

~~~
NET START MSSQLSERVER
NET STOP MSSQLSERVER
~~~

---------------------------------------------------------------------------

#### Formatting SQL ####

Attributes of SQL : 
- Designed to have an unambiguous grammar  
- Allow for multi word keywords, eg. 'INSERT INTO' or 'GROUP BY'  
- Allow unary operators in math  

Guidelines :  
- Be consistent, avoid multiple words that have the same meaning "account_number", "account_nr", "acct_num", ...  
- In general, avoid using abbreviations and defaults, write "INTEGER" instead of "INT", ...  
- Uppercase all reserved words so they can be clearly seen, "SELECT", "FROM", ...   
- Lowercase all scalar values and column names   
- Capitalize the names of schema objects that are constructs, such as tables, views, sequences, ...   
- Do not indent more than 3 spaces within a block (Law of Proximity), readers will get lost if they have to make huge jumps across the page  
- Do not set text in long lines, agains readers will get lost ...  
- Add rivers and indents, SQL code is two dimensional, not one dimensional like text.  

Worse case scenario...  

~~~
CREATE TABLE PILOT_SKILLS(PILOT_NAME CHAR(15) NOT NULL, PLANE_NAME CHAR(15) NOT NULL, PRIMARY KEY(PILOT_NAME, PLANE_NAME));
CREATE TABLE HANGAR(PLANE_NAME CHAR(15) NOT NULL PRIMARY KEY);
SELECT DISTINCT PILOT_NAME FROM PILOT_SKILLS AS PS1 WHERE NOT EXISTS(SELECT * FROM HANGAR WHERE NOT EXISTS(SELECT * FROM PILOT_SKILLS AS PS2 WHERE(PS1.PILOT_NAME=PS2.PILOT_NAME)AND(PS2.PLANE_NAME=HANGAR.PLANE_NAME)));
~~~

To...  

~~~
CREATE TABLE Pilot_Skills
(pilot_name CHAR(15) NOT NULL, 
 plane_name CHAR(15) NOT NULL,
  PRIMARY KEY(pilot_name, plane_name));
 
CREATE TABLE Hangar
(plane_name CHAR(15) NOT NULL PRIMARY KEY);
 
SELECT DISTINCT pilot_name
  FROM Pilot_Skills AS PS1
 WHERE NOT EXISTS
       (SELECT *
          FROM Hangar
         WHERE NOT EXISTS
              (SELECT *
                 FROM Pilot_Skills AS PS2
                WHERE PS1.pilot_name = PS2.pilot_name
                  AND PS2.plane_name = Hangar.plane_name));
~~~


[Formatting SQL Code Part 2](https://www.simple-talk.com/sql/t-sql-programming/formatting-sql-code-part-second/)  

#### Useful Tools ####

[SSMSBoost](http://www.ssmsboost.com/)  
[Sql Complete](http://www.devart.com/dbforge/sql/sqlcomplete/)  
