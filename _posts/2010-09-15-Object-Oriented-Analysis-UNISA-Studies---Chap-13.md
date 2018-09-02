---
layout: post
title: Object Oriented Analysis UNISA Studies - Chap 13
tags: 
category: University
---
Any ramblings and blog posts associated with the UNISA ICT 2622 tag should be considered study notes for my lectures...

Objectives of Chapter 13

Describe the differences and similarities between relational and object-oriented database management systems
Design relational database schema based on an entity-relationship diagram
Design an object database schema based on a class diagram
Describe the different architectural models for distributed databases
Key Words & Definitions
database (DB) – an integrated collection of stored data that is centrally managed and controlled
database management system (DBMS) – system software that manages and controls access to a database
physical data store – the storage area used by a database management system to store the raw bits and bytes of a database
schema – a description of the structure, content, and access controls of a physical data store or database
relational database management system (RDBMS) – a database management system that stores data in tables
table – a two-dimensional data structure containing columns; also called a relation
row – the portion of a table containing data that describes one entity, relationship, or object; also called tuple or record
field – a column of a relational database table; also called an attribute
field value – the data value stored in a single cell of a relational database table; also called an attribute value or data element
key – a field that contains a value that is unique within each row of a relational database table
primary key – a key used to uniquely identify a row of relational database table
foreign key – a field value stored in one relational database table that also exists as a primary key value in another relational database table
referential integrity – a consistent relational database state in which every foreign key value also exists as a primary key value
normalization – a technique that ensures relational database schema quality by minimizing data redundancy
first normal form (1NF) – a relational database table structure that has no repeating fields or groups of fields
functional dependency – a one-to-one correspondence between two field values
second normal form (2NF) – a relational database table structure in which every non-key field is functionally dependent on the primary key
third normal form (3NF) – a relational database table structure in which no non-key field is functionally dependent on any other non-key fields
object database management system (ODBMS) – a database management system that stores data as objects or class instances
Object Definition Language (ODL) – a standard object database description language promulgated by the Object Database Management Group
Transient Class – a class that doesn’t need to store any attribute values between instantiations or method invocations
Persistent Class – A class that must store one or more attribute values between instantiations or method invocations
Object Identifier – a physical storage address or a reference that can be converted to a physical storage address at run time
Navigation – the process of accessing an object by extracting its object identifier from another (related) object
Multivalued Attribute – An attribute that contains zero or more instances of the same data type
hybrid object relational DBMS – a relational database management system used to store object attributes and relationships; also called hybrid DBMS
data type – the storage format and allowable content of a program variable or database field
primitive data type – a storage format directly implemented by computer hardware or a programming language
complex data type – a data type not directly supported by computer hardware or a programming language; also called user-defined data type
database synchronization – the process of ensuring consistency among two or more database copies
Databases & Database Management Systems
A database is an integrated collection of stored data that is centrally managed and controlled. A database is managed by a database management system (DBMS).

A database consists of two related information stores…

The physical data store – contains raw bits and bytes of data
The schema – contains descriptive information about the data store including… access & content controls, relationships among data elements and details of data store organization.
A DBMS has 4 key components…

A application program interface
A query interface
An administrative interface
Underlying set of of data access programs and subroutines
Databases and DBMS provide several important data ac cess and management capabilities including the following…

Simultaneous access by many users and application programs
Access to data without writing application programs
Application of uniform and consistent access and content controls
There are 4 main database models…

Hierarchical – old and rare
Network – old and rare
Relational – current and popular
Object-oriented – new and growing in popularity
Relational Databases
A relational database management system (RDBMS) is a database management system that stores data in tables (also called relations).

The following terminology applies to relational databases…

table – a two-dimensional data structure containing columns; also called a relation
row – the portion of a table containing data that describes one entity, relationship, or object; also called tuple or record
field – a column of a relational database table; also called an attribute
field value – the data value stored in a single cell of a relational database table; also called an attribute value or data element
 

Each table in a relational database must have a unique key. A key is a field that contains a value that is unique within each row of a relational database table. If only one key is is unique, then that key is also called the primary key. Keys are critical for relational database design as they are needed to establish the relationship between data.

Designing Relational Databases
Relational database design begins with either an ERD or class diagram. To create a relational database schema from an ERD, follow these steps…

Create a table for each entity type
Choose a primary key for each table
Add a foreign key to represent one-to-many relationships
Create new tables to represent many-to-many relationships
Define referential integrity constraints
Evaluate schema quality and make necessary improvements
Choose appropriate data types and value restrictions for each field.
Evaluating Schema Quality
A high quality data model has the following features…

Uniqueness of table rows and primary keys
Lack of redundant data
Ease of implementing future data model changes
Database Normalization
Normalization is a formal technique that ensures relational database schema quality by minimizing data redundancy. Normalization is based on a concept called functional dependency and on a series of normal forms…

first normal form (1NF) – a relational database table structure that has no repeating fields or groups of fields
second normal form (2NF) – a relational database table structure in which every non-key field is functionally dependent on the primary key
third normal form (3NF) – a relational database table structure in which no non-key field is functionally dependent on any other non-key fields
 

Object Oriented Databases
Object database management systems (ODBMSs) are a direct extension of OO design and programming paradigm. ODBMS are designed specifically to store objects and to interface with object-oriented programming languages.

To create an object database schema from a class diagram, follow these steps….

Determine which classes require persistent storage
Determine persistent classes
Represent relationships among persistent classes
Choose appropriate data types and value restrictions for each field
Representing Classes
There are two main types of classes…

Transient Classes – temporary (i.e. Windows and Buttons)
Persistent Classes – permanent (i.e. User Objects and Business Objects)
Representing Relationships
Each object store within a ODBMS is automatically assigned a unique object identifier. An ODBMS represents relationships by storing the identifier of one object within related objects. The relationships include…

One-to-Many Relationships
Many-to-Many Relationships
The set of object identifier attributes can also be called a multivalued attribute which is an attribute that contains zero or more instances of the same data type. These are commonly support in ODBMS but not RDBMS as they violate first normal form.

Key Attributes
Key attributes are not required in an object database because referential integrity is implemented with object identifiers. Key attributes are however useful in object databases for a number of purposes including guaranteeing unique object content and providing a means of querying database contents.

Hybrid Object-Relational Database Design
hybrid object relational DBMS is a relational database management system used to store object attributes and relationships; also called hybrid DBMS

The hybrid DBMS approach is currently the most widely employed approach for persistent object storage. Designing a hybrid database is essentially two design problems in one.

Designer must develop a complete relational database schema
Develop set of classes to represent the relational database contents within OO programs
Following are the most important mismatches between the relational and OO views of stored data…

Class methods cannot be directly stored or automatically executed within RDBMS
ODBMSs can represent a wider range of relationship types from RDBMSs, including classification hierarchies and whole part aggregations. Relationships in an RDBMS can only be represented using referential integrity.
ODBMSs can represent a wider range of data types than RDBMS. New classes can be defined to store application specific data.
There is also considerable overlap between ODBMS & RDBMS including…

Grouping of data items into entities or classes
Defining one-to-one, one-to-many, and many-to-many relationships among entities or classes
Data Types
A data type defines the storage format and allowable content of a program variable or database field.

Primitive data type is a storage format directly implemented by computer hardware or a programming language. (i.e. bool, integer, etc)

Complex data type is a data type not directly supported by computer hardware or a programming language; also called user-defined data type. It is built up using primitive data types.

With RDBMS the designer needs to define each data type. ODBMS have similar primitive data types to RDBMS however since ODBMS are storing class information, one could consider that as a complex data type already.

Distributed Databases
There are several types of distributed database designs including…

Single database server
Replicated database servers
Partitioned database servers
Federated database servers
Each design has its benefits and draw backs, however generally they get more complicated to create and support from top down on the list.