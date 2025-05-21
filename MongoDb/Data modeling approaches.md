---
tags:
  - mongodb
---

MongoDB, being a NoSQL document database, offers a lot of flexibility in how you model your data, unlike the strict relational schemas of SQL databases. The primary goal of data modeling in MongoDB is to design a schema that aligns with your application's access patterns and ensures optimal performance, scalability, and maintainability.

The two fundamental data modeling approaches in **MongoDB** are:

- [[Embedded Model|Embedded Data Model (Denormalized)]]
- [[Reference Data Model|Referenced Data Model (Normalized)]]
- Hybrid Data Model (Combination)

The choice between these depends heavily on the nature of your data relationships (one-to-one, one-to-many, many-to-many), the frequency of data access, the size of related data, and update patterns.