---
tags:
  - mongodb
---

Unlike single-field indexes that operate on just one field, a compound index is an index that includes multiple fields of a document. The order in which you list the fields when creating the index is crucial, as it determines the sort order of the index and how efficiently it can support different queries.

Think of it like a phone book sorted first by last name, then by first name. To find "John Doe," you'd first go to "Doe," then within the "Doe" section, find "John." This efficiency is what a compound index aims for.

**How They Work:**

When you create a compound index, MongoDB builds a B-tree data structure (or similar) that stores entries for all the specified fields. The entries are sorted first by the values of the first field, then by the values of the second field, and so on.

**Syntax:**

You create a compound index by specifying an object where each key-value pair represents a field and its sort order (`1` for ascending, `-1` for descending).

```js
db.<collection_name>.createIndex({ <field1>: <1 or -1>, <field2>: <1 or -1>, ... })
```

- `<collection_name>`: The name of your MongoDB collection.
- `<field1>`, `<field2>`, ...: The names of the fields you want to include in the index.
- `<1 or -1>`: Specifies the sort order for each field.

**Example**

Imagine you frequently need to find students by their `major` and then sort them by `gpa` (highest GPA first).

A single index on `major` would be good for finding by major, but sorting by `gpa` would still require a separate sort operation in memory.

```js
db.college_db.students.createIndex({ major: 1, gpa: -1 })
```
This index is sorted first by `major` in ascending order, and then for documents with the same `major`, they are sorted by `gpa` in descending order.