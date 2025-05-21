---
tags:
  - mongodb
---

Indexes in MongoDB are special data structures that store a small portion of the data in a way that's easy to traverse. Think of them like the index in the back of a book. Instead of reading the entire book to find a specific topic, you can quickly look it up in the index and jump directly to the relevant pages.

In MongoDB, indexes improve the efficiency of read operations (queries). Without indexes, MongoDB must scan every document in a collection to select those that match the query statement. This is called a "collection scan" and is very inefficient for large collections. Indexes allow MongoDB to quickly locate the matching documents without having to scan the entire collection.

**How do indexes work?**

MongoDB indexes work similarly to indexes in other database systems. They store the value of specific fields and pointers to the documents that contain those values. These indexed values are stored in an easily traversable data structure, typically a B-tree.

When you query a collection for a field that has an index, MongoDB can use the index to quickly locate the documents that match your query criteria. It doesn't need to examine every document in the collection.

**Types of Indexes in MongoDB:**

- [[Single Field Index]]
- [[Compound Indexes]]


## **How to drop indexes**

####   **Drop a Specific Index by Name**

a. **Find the index name**
```js 
db.students.getIndexes() 
```

**Example Output (simplified):**
```json
[
  {
    "v" : 2,
    "key" : {
      "_id" : 1
    },
    "name" : "_id_" // Default index on _id
  },
  {
    "v" : 2,
    "key" : {
      "age" : 1
    },
    "name" : "age_1" // Your single field index
  },
  {
    "v" : 2,
    "key" : {
      "major" : 1,
      "gpa" : -1
    },
    "name" : "major_1_gpa_-1" // Your compound index
  }
]
```

b. **Drop the index using `dropIndex()`:** Once you have the name, use the `dropIndex()` method.

```javascript
db.<collection_name>.dropIndex("<index_name>")
```

**Example:**
To drop the `age_1` index:

```javascript
db.college_db.students.dropIndex("age_1")
```

To drop the `major_1_gpa_-1` index:

#### Drop All Indexes on a Collection

This method is useful if you want to completely rebuild your indexing strategy or if you're sure you want to remove all custom indexes. **Be cautious with this method as it will drop the default `_id_` index as well, and then immediately recreate it.**

```js
db.<collection_name>.dropIndexes()
```

