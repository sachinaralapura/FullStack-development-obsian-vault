---
tags:
  - mongodb
---
---
**Comparison Operators:**

- **`$eq` (Equal To):** Matches documents where the value of a field is equal to a specified value.
    ```js
    // Find students majoring in "Physics"
    db.students.find({ "major": { "$eq": "Physics" } })
    // Equivalent to:
    db.students.find({ "major": "Physics" })
    ```

- **`$ne` (Not Equal To):** Matches documents where the value of a field is not equal to a specified value.
    ```js
    // Find students who are not majoring in "Computer Science"
    db.students.find({ "major": { "$ne": "Computer Science" } })
    ```

- **`$gt` (Greater Than):** Matches documents where the value of the field is greater than a specified value.
    ```js
    // Find students older than 20
    db.students.find({ "age": { "$gt": 20 } })
    ```

- **`$gte` (Greater Than or Equal To):** Matches documents where the value of the field is greater than or equal to a specified value.
    ```js
    // Find students with a GPA of 3.5 or higher
    db.students.find({ "gpa": { "$gte": 3.5 } })
    ```

- **`$lt` (Less Than):** Matches documents where the value of the field is less than a specified value.
    ```js
    // Find students younger than 22
    db.students.find({ "age": { "$lt": 22 } })
    ```

- **`$lte` (Less Than or Equal To):** Matches documents where the value of the field is less than or equal to a specified value.
    ```js
    // Find students with a GPA of 3.2 or lower
    db.students.find({ "gpa": { "$lte": 3.2 } })
    ```

- **`$in`:** Matches documents where the value of a field is equal to any value in a specified array.
    ```js
    // Find students majoring in either "Biology" or "Chemistry"
    db.students.find({ "major": { "$in": ["Biology", "Chemistry"] } })
    ```

- **`$nin` (Not In):** Matches documents where the value of a field is not equal to any value in a specified array.
    ```js
    // Find students not majoring in "Physics" or "Mathematics"
    db.students.find({ "major": { "$nin": ["Physics", "Mathematics"] } })
    ```

---
**Logical Operators:**

- **`$and`:** Joins query clauses with a logical AND, returning documents that satisfy all the conditions of the clauses.
    ```js
    // Find students who are enrolled AND have a GPA greater than 3.5
    db.students.find({ "$and": [ { "enrolled": true }, { "gpa": { "$gt": 3.5 } } ] })
    // Equivalent to:
    db.students.find({ "enrolled": true, "gpa": { "$gt": 3.5 } })
    ```

- **`$or`:** Joins query clauses with a logical OR, returning documents that satisfy at least one of the conditions of the clauses.
    ```js
    // Find students who are from "New York" OR are majoring in "Biology"
    db.students.find({ "$or": [ { "city": "New York" }, { "major": "Biology" } ] })
    ```

- **`$not`:** Inverts the effect of a query expression and returns documents that do _not_ match the query expression.
    ```js
    // Find students whose GPA is NOT greater than 3.8
    db.students.find({ "gpa": { "$not": { "$gt": 3.8 } } })
    ```

- **`$nor`:** Joins query clauses with a logical NOR, returning documents that fail all the conditions of the clauses.
    ```js
    // Find students who are NOT from "Boston" AND NOT majoring in "Chemistry"
    db.students.find({ "$nor": [ { "city": "Boston" }, { "major": "Chemistry" } ] })
    ```

---
**Element Operators:**

- **`$exists`:** Matches documents that have the specified field.
    ```js
    // Find students who have a "graduation_year" field
    db.students.find({ "graduation_year": { "$exists": true } })
    
    // Find students who do NOT have a "graduation_year" field
    db.students.find({ "graduation_year": { "$exists": false } })
    ```

- **`$type`:** Matches documents where the value of the field is of a specified BSON type. You can use numbers (e.g., 2 for String, 16 for Int32) or aliases (e.g., "string", "int").
    ```js
    // Find documents in the "courses" collection where the "credits" field is an integer
    db.courses.find({ "credits": { "$type": "int" } })
    // Or using the number code:
    db.courses.find({ "credits": { "$type": 16 } })
    ```

---
**Evaluation Operators:**

- **`$regex`:** Provides regular expression capabilities for pattern matching strings.    
    ```js
    // Find students whose name starts with "A" (case-insensitive)
    db.students.find({ "name": { "$regex": "^A", "$options": "i" } })
    ```

- **`$text`:** Performs text search on fields indexed with a text index.
    ```js
    // Assuming you have a text index on the "title" field of the "courses" collection
    db.courses.find({ "$text": { "$search": "programming introduction" } })
    ```

---
**Array Operators:**

- **`$all`:** Matches documents where the value of an array field contains all the specified elements.
    ```js
    // Find students who are enrolled in both "CS101" and "MATH201"
    db.students.find({ "courses": { "$all": ["CS101", "MATH201"] } })
    ```

- **`$elemMatch`:** Matches documents that contain an array field with at least one element that matches1 all the specified query criteria. This is useful for querying arrays of embedded documents (like the `schedules` array in the `courses` collection).
    ```js
    // Find courses that have a schedule on "Monday" at "10:00-11:30"
    db.courses.find({ "schedules": { "$elemMatch": { "day": "Monday", "time": "10:00-11:30" } } })
    ```

- **`$size`:** Matches documents where the value of an array field has a specific number of elements.
    ```js
    // Find students who are enrolled in exactly two courses
    db.students.find({ "courses": { "$size": 2 } })
    ```
