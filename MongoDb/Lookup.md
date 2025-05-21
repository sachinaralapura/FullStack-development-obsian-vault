---
tags:
  - mongodb
---

The `$lookup` stage in the MongoDB Aggregation Framework is designed to perform a left outer join from one collection to another collection in the same database. It's MongoDB's answer to the `LEFT JOIN` operation found in traditional relational databases like `PostgreSQL`.

This stage allows you to enrich documents in your "input" collection (the one you're aggregating from) by bringing in data from a "foreign" collection.

### **How `$lookup` Works**

The $lookup stage takes documents from the input collection and, for each document, searches a specified "foreign" collection for matching documents. It then adds a new array field to the input document. This array field contains the matching documents from the foreign collection. If no matching documents are found, the array will be empty.

**Syntax**

```js
{
  $lookup: {
    from: "<foreign_collection_name>",  // The collection to join with
    localField: "<field_from_input_documents>", // Field from the input documents
    foreignField: "<field_from_foreign_documents>", // Field from the documents of the "from" collection
    as: "<output_array_field_name>" // The name of the new array field to add to the input documents
  }
}
```

