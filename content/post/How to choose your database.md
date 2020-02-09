---
date: 2019-09-16
linktitle: Choosing a database
icon: database
tags : [
    "databases",
]
title: Choosing a database
summary: Choosing a database from a sea of solutions.
---

Choosing a database management system for a new project can be tricky. Several criteria should be taken into consideration. In this article, I compare relational, NoSQL and NewSQL database models.

While choosing a database model, we generally have to keep these considerations in mind:

- Does it need to support *OLTP* operations?
- Does it need to support *OLAP* operations?
- Is my data structured?
- Do I have a high volume of data?

|Database Model|ideal for                                       |not ideal for        |
|--------------|------------------------------------------------|---------------------|
|Relational    |OLTP, Structured data                           |High volume of data  |
|NoSQL         |High volume of data, OLAP                       |OLTP, Structured data|
|NewSQL        |High volume of data, OLAP, OLTP, Structured Data|                     |

The NewSQL solution seems to promise the best of two worlds; ACID compliant (like relational databases) and horizontally scalable (like NoSQL databases). The only problem seems to be the solution's maturity; it's not as mature as relational and NoSQL DBMSs.

Below are some useful material for further reading/listening/viewing.

- The women in tech show [podcast](https://player.fm/series/series-2468272/database-scaling-with-deepthi-sigireddi) with Deepthi Sigireddi on databases scaling.
- Software engineering daily [podcast](https://softwareengineeringdaily.com/2015/07/30/mongodb-with-bryan-reinero/) with Bryan Reinero on MongoDB.
- Uber engineering [blog](https://eng.uber.com/schemaless-part-one/) on Schemaless.
- Using Cassandra for storing financial transactions [talk](https://skillsmatter.com/skillscasts/10469-retail-banking-using-cassandra-for-storing-financial-transactions).
- Introduction to Database Management Systems [book](https://learning.oreilly.com/library/view/introduction-to-database/9788131700785/).
- Database Systems: Concepts, Design and Applications [book](https://learning.oreilly.com/library/view/database-systems-concepts/9788177585674/).

Hope this article helped with understanding the different tradeoffs we face when choosing a DBMS. You can reach out to me via Twitter if you want to chat more about it!
