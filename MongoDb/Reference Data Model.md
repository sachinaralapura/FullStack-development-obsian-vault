---
tags:
  - mongodb
---

In the referenced data model, you store related data in separate, normalized collections and establish relationships by including links (typically the `_id` field) from one document to another. This is similar to how relational databases use foreign keys.

### **Characteristics:**

- **Reduced Duplication:** Data is stored once, minimizing redundancy.
- -**Flexible Relationships:** Better for complex many-to-many relationships or when related data needs to be accessed independently.
- **Avoids Document Size Limit:** Documents remain smaller, preventing the 16MB limit from being hit.
- **Easier Updates:** Updating shared referenced data requires only one write operation.

### **Use Cases:**

- **One-to-Many Relationships (One-to-Many-Thousand/Unbounded):** When the "many" side can be very large or unbounded (e.g., a `user` document referencing `order` documents).
    
    - **Child-Referencing (1-N):** The "many" side stores the ID of the "one" side. (Most common for 1-to-many)
```js
// Publisher Collection
		{ _id: ObjectId("pub1"), name: "O'Reilly Media" }

		// Book Collection (child referencing publisher)
		{ _id: ObjectId("bookA"), title: "MongoDB Guide", publisher_id: ObjectId("pub1") }
		{ _id: ObjectId("bookB"), title: "Node.js Basics", publisher_id: ObjectId("pub1") }
```
.
	- **Parent-Referencing (N-1):** The "one" side stores an array of IDs of the "many" side. (Less common for large 'N' due to array growth and 16MB limit)

```js
	// Student Collection (parent referencing courses - if courses are few)
{
  _id: ObjectId("std1"),
  name: "Alice",
  enrolledCourses: [
    ObjectId("courseA"),
    ObjectId("courseB")
  ]
}

// Course Collection
{ _id: ObjectId("courseA"), title: "Database Systems" }
{ _id: ObjectId("courseB"), title: "Web Development" }
```

- **Many-to-Many Relationships:** When multiple documents in one collection can be related to multiple documents in another collection (e.g., `students` and `courses`, where a student can take many courses, and a course can have many students).
