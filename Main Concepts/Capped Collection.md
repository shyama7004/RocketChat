# Capped Collection

### **1. Creating a Capped Collection**

To create a capped collection, use the `db.createCollection()` method, specifying `capped: true` and the `size` in bytes.

**Example:**
```javascript
db.createCollection("log", { capped: true, size: 100000 })
```
- **Explanation**: 
  - This code creates a capped collection named `log` with a maximum size of 100,000 bytes. Once the collection reaches this size, it will start overwriting the oldest documents with new ones.

### **2. Inserting Data into a Capped Collection**

Inserting data into a capped collection is the same as inserting data into a regular MongoDB collection.

**Example:**
```javascript
db.log.insertOne({ message: "This is a log entry", timestamp: new Date() })
```
- **Explanation**: 
  - This inserts a document into the `log` collection with a `message` field and a `timestamp`. If the collection reaches its size limit, the oldest log entry will be removed to make room for this new entry.

### **3. Querying Capped Collections in Insertion Order**

You can retrieve documents in the order they were inserted by using the `find()` method without any sort option.

**Example:**
```javascript
db.log.find().sort({ $natural: 1 })
```
- **Explanation**: 
  - The `sort({ $natural: 1 })` ensures the documents are retrieved in the order they were inserted. This is particularly useful for logs or time-series data.

### **4. Using a Tailable Cursor to Monitor Inserts**

A tailable cursor allows you to continue fetching new documents as they are inserted into a capped collection.

**Example:**
```javascript
var cursor = db.log.find({}, { tailable: true, awaitData: true }).addOption(DBQuery.Option.tailable);
while(cursor.hasNext()) {
    printjson(cursor.next());
}
```
- **Explanation**: 
  - This sets up a tailable cursor that will keep the query open, continuously returning new documents as they are inserted into the `log` collection. This is ideal for monitoring real-time data, like logs.

### **5. Avoiding Updates in Capped Collections**

Due to the nature of capped collections, updating documents can lead to unexpected behavior. However, if necessary, you can update fields that do not change the document size.

**Example:**
```javascript
db.log.updateOne(
    { _id: ObjectId("some_id_value") }, 
    { $set: { message: "Updated log message" } }
)
```
- **Explanation**: 
  - This updates the `message` field in the document with the specified `_id`. Ensure that the update doesn’t change the size of the document.

### **6. Understanding _id Index in Capped Collections**

Capped collections automatically create an `_id` field with an index. This index allows for fast lookups by `_id`.

**Example:**
```javascript
var doc = db.log.findOne({ _id: ObjectId("some_id_value") })
printjson(doc)
```
- **Explanation**: 
  - This code finds a document by its `_id` field, leveraging the index that MongoDB automatically creates in capped collections.

### **7. Handling Concurrent Writes**

MongoDB handles concurrent writes to a capped collection but doesn’t guarantee strict insertion order. You can insert data as usual.

**Example:**
```javascript
db.log.insertMany([
    { message: "First log", timestamp: new Date() },
    { message: "Second log", timestamp: new Date() }
])
```
- **Explanation**: 
  - This inserts multiple documents at once. MongoDB will handle the concurrent insertion, but the order of insertion may not be strictly maintained.

### **8. Monitoring the Oplog (Advanced Use Case)**

If you’re working with MongoDB’s replica sets, the oplog (operations log) is a capped collection. You can monitor it similarly to any other capped collection.

**Example:**
```javascript
var oplog = db.getSiblingDB("local").oplog.rs.find().sort({ $natural: -1 }).limit(1)
printjson(oplog)
```
- **Explanation**: 
  - This code accesses the oplog collection in the `local` database and retrieves the most recent operation. This is useful for understanding replication behavior in MongoDB.

### **9. Comparing Capped Collections with TTL Indexes**

While capped collections overwrite data based on size, you can use a TTL (Time-To-Live) index to automatically delete documents after a certain period.

**Example of TTL Index:**
```javascript
db.log.createIndex({ timestamp: 1 }, { expireAfterSeconds: 3600 })
```
- **Explanation**: 
  - This creates a TTL index on the `timestamp` field, which deletes documents 1 hour (3600 seconds) after their insertion. This method is useful for automatically expiring data without size constraints.

---

These examples should help you understand and implement each topic related to capped collections in MongoDB, with clear explanations to make the concepts beginner-friendly.
