---
tags:
  - mongodb
---

**What are Single Field Indexes?**

A single field index is an index created on a single field within the documents of a MongoDB collection. This type of index allows MongoDB to efficiently retrieve documents based on the values of that specific field. When you query for documents matching a certain value in the indexed field, MongoDB can use the index to quickly locate those documents without scanning the entire collection.

**How They Work:**

MongoDB creates a B-tree data structure (or a similar structure) that stores the values of the indexed field and pointers to the corresponding documents on disk. This structure is sorted by the value of the indexed field, allowing for fast lookups.

**Syntax:**

You create a single field index using the `createIndex()` method on a collection, specifying the field to index and the sort order (ascending `1` or descending `-1`).

```js
db.<collection_name>.createIndex({ <field_name>: <1 or -1> })
```

- `<collection_name>`: The name of your MongoDB collection.
- `<field_name>`: The name of the field you want to index.
- `<1 or -1>`: Specifies the sort order of the index:
    - `1`: Ascending order (e.g., A to Z, 1 to 10).
    - `-1`: Descending order (e.g., Z to A, 10 to 1).

**Example**

Let's say you frequently query your `students` collection to find students of a specific `age`. Without an index, MongoDB would have to examine every document in the `students` collection to find the ones matching the given age. This becomes inefficient as the number of students grows.

To optimize these queries, you can create a single field index on the `age` field:
```js
db.college.students.createIndex({ age: 1 })
```

**How this index helps in queries:**

```js
db.college_db.students.find({ age: 20 })
```

MongoDB can use the `age` index to quickly locate all the documents where the `age` field is equal to `20`. It doesn't need to iterate through every student document. It can directly jump to the relevant entries in the index and then fetch the corresponding documents.