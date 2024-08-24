### MongoDB Basics: Databases and Collections

#### Overview
- **MongoDB** stores data in BSON (Binary JSON) format, which is optimized for efficiency and scalability.
- **Documents** are the basic units of data in MongoDB, similar to rows in a relational database.
- **Collections** are groups of documents, similar to tables in a relational database.
- **Databases** in MongoDB hold one or more collections of documents.

### Databases in MongoDB
- A **database** in MongoDB is a container for collections. Each database has its own set of files on the filesystem.
- To **select a database** in MongoDB's shell (`mongosh`), use the `use <db>` command. If the database does not exist, MongoDB will create it when you first store data in it.

  **Example:**
  ```javascript
  use myDatabase
  ```
  - This command switches to or creates the `myDatabase` database.

### Creating a Collection
- A **collection** is a group of MongoDB documents, and collections are similar to tables in a relational database.
- Collections are created when you first insert data into them. You don’t need to create them explicitly.

  **Example:**
  ```javascript
  db.myCollection.insertOne({ name: "Alice", age: 25 })
  ```
  - This command creates a new collection named `myCollection` and inserts a document with `name` and `age` fields.

- **Explicit Collection Creation:**
  You can explicitly create a collection using the `db.createCollection()` method, which allows you to specify options like maximum size or validation rules.

  **Example:**
  ```javascript
  db.createCollection("myCollection", {
      capped: true, 
      size: 5242880, 
      max: 5000
  })
  ```
  - This creates a capped collection that is limited to 5MB and can store up to 5000 documents.

### Working with Collections
- **Inserting Documents:** Use the `insertOne` or `insertMany` methods to add documents to a collection.

  **Example:**
  ```javascript
  db.myCollection.insertOne({ name: "Bob", age: 30, city: "New York" })
  ```
  - Inserts a single document into `myCollection`.

- **Schema Flexibility:** MongoDB collections do not enforce a schema by default. This means documents in the same collection can have different fields and data types.

  **Example:**
  ```javascript
  db.myCollection.insertMany([
    { name: "Charlie", age: 35 },
    { name: "Dana", occupation: "Engineer" }
  ])
  ```
  - In this example, one document has `age` and another has `occupation`. MongoDB does not enforce a strict schema.

- **Document Validation:** You can enforce specific rules for documents in a collection using validation. This helps in maintaining some consistency.

  **Example:**
  ```javascript
  db.createCollection("validatedCollection", {
      validator: { $jsonSchema: {
          bsonType: "object",
          required: ["name", "age"],
          properties: {
              name: {
                  bsonType: "string",
                  description: "must be a string and is required"
              },
              age: {
                  bsonType: "int",
                  minimum: 18,
                  description: "must be an integer and at least 18"
              }
          }
      }}
  })
  ```
  - This creates a collection where documents must have a `name` (string) and `age` (integer >= 18).

### Modifying Collections
- **Modifying Document Structure:** MongoDB allows you to modify documents in a collection by adding or removing fields or changing their data types.

  **Example:**
  ```javascript
  db.myCollection.updateOne(
      { name: "Alice" },
      { $set: { age: 26 }, $unset: { city: "" } }
  )
  ```
  - This updates Alice's age and removes the `city` field from her document.

- **Unique Identifiers:** Each document in a collection has a unique `_id` field, which serves as the primary key.

  **Example:**
  ```javascript
  db.myCollection.findOne({ _id: ObjectId("507f191e810c19729de860ea") })
  ```
  - Finds a document by its unique `_id`.

### Conclusion
- MongoDB’s flexible schema allows for rapid development, making it ideal for applications where the data structure might evolve over time.
- Databases in MongoDB are easy to manage, with collections being created automatically when data is inserted.
- Understanding MongoDB’s basic operations and schema flexibility will help you effectively design and query your databases.
