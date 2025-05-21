---
tags:
  - mongodb
---

The MongoDB Aggregation Framework is a powerful tool within MongoDB that allows you to process data records and return computed results. It's similar to the GROUP BY clause in SQL, but far more flexible and capable, enabling complex data transformations and analyses directly within the database**.**

### **The aggregation framework lets you:**

- **Filter** documents (similar to find() or WHERE).
- **Transform** the shape of documents (e.g., add new fields, rename fields, remove fields).
- **Group** documents by one or more fields to perform calculations (e.g., count, sum, average, min, max).
- **Join** data from multiple collections (using $lookup).
- **Reshape** arrays.
- **Perform** **statistical analysis** like calculating standard deviations, percentiles, etc.

The core idea of the aggregation framework is the **pipeline**. You process documents through a series of **stages**, where each stage performs an operation on the input documents and outputs a stream of documents to the next stage. This sequential processing allows for highly complex and efficient data manipulation.

### **Common Aggregation Pipeline Stages**

- **$match:** Filters documents to pass only those that match the specified query conditions to the next pipeline stage. It's often the first stage to reduce the number of documents processed early.

    - Analogy: The "WHERE" clause in SQL.

- **$project**: Reshapes each document in the stream by including, excluding, or adding new fields. It can also transform existing fields.

    - Analogy: The "SELECT" clause in SQL, but with more transformation capabilities.

- **$group:** Groups input documents by a specified _id expression and outputs a single document for each distinct group. It then applies aggregate functions (like $sum, $avg, $count, $min, $max) to the grouped documents.

    - Analogy: The "GROUP BY" clause with aggregate functions in SQL.

- **$sort:** Sorts all input documents and returns them in sorted order to the pipeline.

    - Analogy: The "ORDER BY" clause in SQL.

- **$limit:** Passes the first N documents unmodified to the pipeline.

    - Analogy: The "LIMIT" clause in SQL.

- **$skip:** Skips the first N documents and passes the remaining documents unmodified to the pipeline.

    - Analogy: The "OFFSET" clause in SQL.

- **$unwind:** Deconstructs an array field from the input documents to output a document for each element. If a document has an array field with three elements, $unwind will create three separate documents, each containing one of the array elements.

- **$lookup:** Performs a left outer join to an unsharded collection in the same database to filter in documents from the "joined" collection for processing.

- **$out:** Writes the aggregated results to a new collection.

- **$merge:** Writes the aggregated results to a specified collection. It can merge results into an existing collection, insert new documents, or replace existing documents

**Example**

`find the average GPA for students in each `major``
```js
db.college_db.students.aggregate([
  {
    $group: {
      _id: "$major", // Group by the 'major' field
      averageGpa: { $avg: "$gpa" }, // Calculate the average of 'gpa' for each group
      totalStudents: { $sum: 1 } // Count the number of students in each group
    }
  },
  {
    $sort: { averageGpa: -1 } // Sort the results by averageGpa in descending order
  }
])
```

