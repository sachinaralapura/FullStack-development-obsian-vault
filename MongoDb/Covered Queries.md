---
tags:
  - mongodb
---

A query is considered a covered query if all the fields requested in the query results (the projection) are included in an index, and all the fields used in the query predicate (the filter conditions) are also included in the same index.

In simpler terms: MongoDB can answer the query entirely by just looking at the index, without having to access the actual documents in the collection.

Think of it like this: If you have a physical phone book (the collection) and an index at the front of the book that lists names and phone numbers, and your query is "find the phone number for John Doe," you can get that information just by looking at the index. You don't need to flip through all the pages of the phone book to find John Doe's full entry.