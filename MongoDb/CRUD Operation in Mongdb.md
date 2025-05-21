---
tags:
  - mongodb
---
---
**Create (Insert):**

- **Insert One Document:** Let's add a new student to the `students` collection.

```js
db.students.insertOne({
  "_id": 6,
  "name": "Grace Wilson",
  "age": 21,
  "major": "Economics",
  "gpa": 3.6,
  "city": "Austin",
  "enrolled": true,
  "courses": ["ECON101", "MATH110"],
  "graduation_year": 2026
})
```

- **Insert Multiple Documents:** Let's add two new students at once.

```js
db.students.insertMany([
  { "_id": 7, "name": "Henry Moore", "age": 20, "major": "Political Science", "gpa": 3.4, "city": "Washington D.C.", "enrolled": true, "courses": ["POL101"], "graduation_year": 2027 },
  { "_id": 8, "name": "Ivy Taylor", "age": 23, "major": "History", "gpa": 3.1, "city": "Philadelphia", "enrolled": false, "courses": ["HIST201"], "graduation_year": 2024 }
])
```

---
**2. Read (Find):**

- **Find All Documents:** Retrieve all documents from the `students` collection.
```js
db.students.find({})
```

- **Find Documents with a Specific Condition:** Find all students majoring in "Computer Science".
```js
db.students.find({ "major": "Computer Science" })
```

- **Find Documents with Multiple Conditions (AND):** Find all students who are enrolled and have a GPA greater than 3.5.
```js
db.students.find({ "enrolled": true, "gpa": { "$gt": 3.5 } })
```

- **Find Documents with Multiple Conditions (OR):** Find all students who are from "New York" or are majoring in "Biology".
```js
db.students.find({ "$or": [ { "city": "New York" }, { "major": "Biology" } ] })
```

- **Find a Single Document:** Retrieve the student with `_id` equal to 3.
```js
db.students.findOne({ "_id": 3 })
```

- **Project Specific Fields:** Find the names and majors of all students. The `_id` field is included by default, so you need to explicitly exclude it if you don't want it.
```js
db.students.find({}, { "name": 1, "major": 1, "_id": 0 })
```

- **Querying within Embedded Documents**  : For example, to find courses scheduled on "Monday":
```js
db.courses.find({ "schedule.day": "Monday" })
```

---
**3. Update:**

- **Update One Document:** Update the GPA of the student with `_id` equal to 2.
```js
db.students.updateOne(
  { "_id": 2 },
  { "$set": { "gpa": 3.3 } }
)
```

- **Update Multiple Documents:** Increase the graduation year of all enrolled students by 1.
```js
db.students.updateMany(
  { "enrolled": true },
  { "$inc": { "graduation_year": 1 } }
)
```

- **Update and Upsert (Insert if Not Found):** Update the major of the student with `_id` equal to 9. If no student with `_id` 9 exists, insert a new student with that information.
```js
db.students.updateOne(
  { "_id": 9 },
  { "$set": { "major": "Data Science" } },
  { "upsert": true }
)
```

- **Updating Array Elements:** Add a new course "STAT101" to Alice Smith's `courses` array.
```js
db.students.updateOne(
  { "name": "Alice Smith" },
  { "$push": { "courses": "STAT101" } }
)
```

- **Updating Embedded Document Fields :** For example, to update the time of the "CS101" course
```js
db.courses.updateOne(
  { "_id": "CS101" },
  { "$set": { "schedule.time": "09:00-10:30" } }
)
```

---
**4. Delete:**

- **Delete One Document:** Delete the student with `_id` equal to 8.
```js
db.students.deleteOne({ "_id": 8 })
```

- **Delete Multiple Documents:** Delete all students who are not enrolled.
```js
db.students.deleteMany({ "enrolled": false })
```

- **Delete All Documents in a Collection:** This will remove all documents from the `students` collection, but the collection itself will still exist. **Use with caution!**
```js
db.students.deleteMany({})
```

- **Drop a Collection:** This will completely remove the `students` collection and its associated indexes from the database. **Use with extreme caution!**
```js
db.students.drop()
```

