---
tags:
  - mongodb
---

## BSON (Binary JSON)

**Format:** Binary-encoded format. It's a binary representation of JSON-like documents, designed for efficiency in storage and processing. While the structure is similar to JSON (key-value pairs), the data is stored in a binary format.

**Readability:** Not directly human-readable. It's designed to be efficiently parsed by machines.

**Data Types:** Extends the JSON data types by adding support for a wider range of types, including:

- **Specific Number Types**: Int32, Int64, Double, Decimal128. This allows for more precise representation of numerical data.
- **Date**: A dedicated Date type (64-bit integer representing milliseconds since the Unix epoch), making date comparisons and sorting efficient.
- **Binary Data**: A specific type for storing raw binary data, like images or files.
- **ObjectId**: A 12-byte unique identifier used as the default primary key in MongoDB. It includes a timestamp, machine identifier, process ID, and a counter.
- **Boolean**: True and False.
- **Null**: Represents a null value.
- **Array**: Ordered lists of values.
- **Object (Embedded Document):** Allows nesting of documents.
- **Regular Expression**: For pattern matching.
- **Timestamp**: An internal MongoDB type useful for oplog entries in replication.
- **Min/Max Key**: Special types for internal comparisons.

**Efficiency:** More efficient for storage and especially for parsing and traversing data due to its binary nature. Length prefixes are often included for elements, allowing for faster skipping of fields. The type information is explicitly stored with each element.