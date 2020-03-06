---
date: 2019-09-15
linktitle: Databases 101
icon: database
tags : [
    "databases",
]
title: Databases 101 
summary: This article gives an overview of databases concepts and lingo.
---
## a bit of history

Before the bloom of databases and database management systems, we used to store data in files, each row in a particular file represented a record. Programmers had to build application programs (AP) on top of these files to retrieve and use the data stored in them. This is what we call Filesystems Management.

Let's take the example of a small hedge fund company. It has employees, an HR department and an accountants' department.

The HR department would have a file called Employees. They use an AP built on top of this file.

The accountants' department has a copy of the same file, with their own AP built on top of it.

If a new employee is hired, the HR department needs to update its Employee file. Which means that the accounts file is not out of sync. This raises the consistency issue.

If we change the name of one of the fields in the Employees file; DOB to Date Of Birth, we will need to change the code of the AP. This raises the manual work and scalability issue.

By the 1960s, a new type of data storage and management was developed by IBM to palliate all the above issues and more; IMS, the first Database Management System (DBMS). [It was originally developed to handle the data of the Apollo mission](https://www.ibm.com/support/knowledgecenter/zosbasics/com.ibm.imsintro.doc.intro/ip0ind0011003710.htm).

A database model is the way data is organized in the **logical view** level. It determines how the data is stored, retrieved and updated.

The most used and popular ones are relational databases, NoSQL and the latest trend, NewSQL.

## Databases models

A database model is the way data is organized in the **logical view** level. It determines how the data is stored, retrieved and updates(updated?)

The most used and popular ones are relational databases, NoSQL and the latest trend, NewSQL.

### Relational

Relational databases are based on the concept of data having relationships between them. they are represented in the format of tables, and data can be retrieved using primary keys and/or foreign keys.

It's usually a **normalized** type of database, is **ACID** compliant and good for **OLTP** operations.

One of the main limitations of RDBMS is **horizontal scaling**; this can be addressed by implementing a sharding mechanism. Some companies like [PlanetScale](https://player.fm/series/series-2468272/database-scaling-with-deepthi-sigireddi) are implementing such algorithms on top of MySQL.

For traditional RDBMS (non-horizontally scalable), we get **CA** from the **CAP theorem**.

***Examples***

Uber uses a [tweaked version](https://eng.uber.com/schemaless-part-two/) of RDBMS MySQL.

Netflix uses RDBMS PostgreSQL.

### NoSQL

NoSQL databases (not only SQL, as some NoSQL databases support SQL) are non-relational databases. The data can be stored in the format of documents without any links between them, or the format of key-value.

it's usually a **denormalized** database type, **BASE** compliant and good for **OLAP** operations.

One of the main limitations is the fact that it's not **ACID** compliant, we can't rely on it when the accuracy of the data is critical (e.g. financial transactions).

For NoSQL databases, we get **AP** from the **CAP theorem**.

***Examples***

Google Analytics uses the NoSQL DBMS BigTable.

Monzo uses the NoSQL Cassandra.

### NewSQL

NewSQL is a new type of data model that made its entry around 2011. it promises the best of two worlds; the scalability of NoSQL systems coupled with the **ACID** compliance of RDBMS.

This new type of DBMS can replace an RDBMS with sharding functionality.

For the NewSQL database, we still get **CP** from the **CAP theorem**.

***Examples***

Financial times use the NewSQL DBMS VoltDB.

Samsung uses the NewSQL DBMS MemSQL.

- DBMS glossary
    - *ACID*: Stands for Atomicity-Consistency-Isolation-Durability.

        **Atomicity** principle states that the set of transactions can all pass and change the state of the DB or all fail.

        **Consistency** principle states a transaction will be rolled back if the rules of writing are not respected.

        **Isolation** states that multiple transactions shouldn't be running at the same time. If transaction A is running, the database is locked until it's committed, then transaction B can be executed.

        **Durability** states that in case of failure during the execution of a transaction, the database should return to its initial state.

    - *BASE*: Stands for Basic-Availability-Soft state-Eventual consistency.

        **Basic Availability** states that the databases appear to be available most of the time.

        **Soft state** states that the state of the database might change even without input, this is because of eventual consistency.

        **Eventual consistency** states that the system will become consistent after a given period, if not given any input.

    - *CAP theorem*: it states that a distributed database system can only have two of these properties; Consistency, Availability or Partition Tolerance.

        **Consistency** states that a certain field in the database should have the same value for the same data across all nodes.

        **Availability** states that the database should be accessible for all users at all times.

        **Partition Tolerance** states that the system should still be up even if one of the nodes goes down.

    - *Denormalised database*: A database containing redundant data, especially applicable NoSQL databases. This is used to improve the performance of read-operations by avoiding joins.
    - *ETL*: Stands for Extract-Transform-Load. It usually means extracting data from an operational database and injecting it into a data warehouse. It can be later be used for analytical purposes.
    - *Foreign key*: a subset of fields that contains the primary key in another table, in relational databases.
    - *Horizontal scaling*: Distributing storage between multiple machines.
    - *HTAP*: Stands for Hybrid Transaction/Analytical Processing. A system is HTAP when it both reads and writes heavily to the database.
    - *Index*: Used to find a single unit of data given its identifier, it holds its address.
    - *Instance*: An instance is a schema with data.
    - *Logical view*: How data is presented to users.
    - *Normalized database*: A relational database containing no data redundancies. This can be done by exploiting the relational property.
    - *OLAP*: Stands for On-Line Analytical Processing. A system is OLAP when it mainly reads from the database. It is usually used for analytical purposes.
    - *OLTP*: Stands for On-Line Transaction Processing. a system is OLTP when it mainly writes to the database.
    - *Physical view*: How data is stored in memory or secondary storage.
    - *Primary key*: a subset of fields that uniquely defines a record in a relational database.
    - *Schema*: Defines the database model.
    - *Secondary index*: Used to find a single unit of data given a combination of criteria.
    - *Vertical scaling*: Increasing the storage memory in a single machine.