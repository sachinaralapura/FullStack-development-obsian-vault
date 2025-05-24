---
tags:
  - mongodb
---
## Chapter 1

Let’s talk about database collection and documents. Databases are the storage area what you create to store a data. Databases can have so many data, in order to segregate we create a folder and keep the data in it. those folders are called collections and the data inside these collection are called `document`.

```js
// to see all the databases
show dbs
```

```js

// We are taking School, student and Library as examples.
// this command will search for first school, if its not there then it will create and then enter, or we can enter in any different database.
use school
```

```js
// to see the current working database
db
```

```js
//create collection (Please ensure that you are inside school database)
db.createCollection("students")
```

```js
//create second collection
db.createCollection("library")
```

```js
//in order to see the collection
show collections
```

```js
//when you want to rename collection students -> student
db.students.renameCollection("student")
```

```js
// in order to see different types of methods in collection
db.students.help()
```

```js
// to delete a collection
db.library.drop()
```

```js
//to delete a database (please ensure you are inside the database which you want to delete)
db.dropDatabase()
```

---
## Chapter 2 → Insert Documents in Collections
```js
// you want to add documents inside the collections

// inserOne
db.<collection_name>.insertOne({ field1: "Value", field2: "Value" });

//insertMany
db.<collection_name>.insertMany([
	{ field1: "Value", field2: "Value" },
	{ field1: "Value", field2: "Value" },
]);

//see all the documents inside the collection
db.collection_name.find()
```

