---
layout: post
title: Fix for NDbUnit - DbCommandBuilder.CreateSelectCommand(DataSet, string) failed for tableName = XXX
tags: 
category: Tech
---
I have recently been using NDbUnit for integration tests exercising the database. I am new to the tool, so the following exception caused a few hours of scratching my head before I figured out the obvious.

Assume you are going through the quick start guide from the website, everything works perfectly. Then I changed to my production database and did the same thing and I get the following error…]

DbCommandBuilder.CreateSelectCommand(DataSet, string) failed for tableName = '….

Turns out the name of the table in my database was “My.ExampleTable” with the “My” being part of a schema and the . was causing the headache. This is because when I was adding the table from the .NET Dataset in my project, it was removing the . from the table name automatically.

The way you can identify this is if you go into Sql Management Studio and look at the Schemas.

Schema

Pulling the table into the xsd diagram will give you something like the following…

2


Adding the first part of the name back to the xsd diagram file solved the problem as illustrated in the last diagram….

3

And that should resolve the error, or at east it did in my case…