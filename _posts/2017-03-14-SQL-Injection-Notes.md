---
layout: post
title: SQL Injection Notes
tags: Web Security
category: Tech
---

SQL Injection is the most common form of attack on websites... still...

Attacks can be launched by modifying user input parameters to change the logic of a SQL Statement executed on the server side.

## Example

Assume you have a login page with a user name and password. You have the following server side code:

~~~
username = getRequestString("userName");
password = getRequestString("passCode");

sql = "SELECT * from Users WHERE Name ='" + username + "' AND Pass = '" + password + "'";
~~~

Assume user name is Scott and password is Tiger, this would generate the following SQL

~~~
SELECT * FROM Users WHERE Name ='Scott' AND Pass ='Tiger'
~~~

Now, if someone changes the user name and password to the following:

username : 'or '1'='1
password : 'or '1'='1

SQL generated would be as follows:  

~~~
SELECT * FROM Users WHERE Name ='' or '1'='1' AND Pass ='' or '1'='1'
~~~

This would bypass the validation since '1' = '1' is always true.

## Prevention Measures

* Do not trust incoming user-inputs - they should always be validated first.
* Consider parameterized queries  
* Leverage client side validation

#### References

[Securing Web Applications](https://www.simple-talk.com/dotnet/net-development/securing-web-applications/)  
