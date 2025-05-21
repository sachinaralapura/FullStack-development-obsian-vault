---
tags:
  - mongodb
---

In the embedded data model, you store related data within a single document. This creates a rich, self-contained document that holds all the necessary information for a particular entity and its closely related sub-entities.

### **Characteristics:**

- **Data Locality:** All related data is stored together on disk. This is a major advantage for read performance as it often allows MongoDB to retrieve all necessary information in a single query, avoiding `$lookup` operations or multiple round trips to the database.
- **Atomic Writes:** Updates to an embedded document (or any part of a single document) are atomic. This simplifies consistency concerns.
- **Reduced Joins:** Eliminates the need for explicit "joins" (like `$lookup` in aggregation) at query time for commonly accessed related data.
- **Simpler Application Code:** Often leads to simpler code as you're working with a single, comprehensive document.

### **Use Cases:**

- **One-to-One Relationships:** Ideal when one entity "contains" another and they are almost always accessed together (e.g., a `user` document embedding their `profile` details).
	***Example***
```json
// User Document
{
  _id: ObjectId("..."),
  name: "John Doe",
  email: "john.doe@example.com",
  profile: { // Embedded document
    age: 30,
    gender: "Male",
    bio: "Software engineer..."
  }
}
```

- **One-to-Many Relationships (One-to-Few):** Suitable when the "many" side of the relationship is relatively small, bounded, and frequently accessed with the "one" side.
	*Example*
```json
	// Book Document with embedded comments (if comments are few)
{
  _id: ObjectId("..."),
  title: "MongoDB Guide",
  author: "Jane Doe",
  comments: [ // Embedded array of documents
    {
      _id: ObjectId("..."),
      text: "Great book!",
      user: "Alice",
      date: ISODate("...")
    },
    {
      _id: ObjectId("..."),
      text: "Very helpful.",
      user: "Bob",
      date: ISODate("...")
    }
  ]
}
```
**Advantages:**

- **Fast Reads:** Achieves better performance for read operations by retrieving related data in a single query.
- **Atomic Operations:** Atomic updates on the entire document.
- **Simplicity:** Simpler to manage when data is closely related and accessed together.

**Disadvantages:**

- **Document Size Limit:** MongoDB documents have a 16MB size limit. If the embedded data can grow indefinitely or become very large, this limit can be hit.
- **Data Duplication:** Can lead to data duplication if the embedded data needs to be referenced from multiple parent documents.
- **Increased Write Overhead:** Updates to parts of a large embedded document might require rewriting the entire document.
- **Limited Independent Access:** Harder to query or update the embedded data independently without fetching the parent document.

