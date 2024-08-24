# BSON Types in MongoDB

**BSON Overview**
- **BSON** (Binary JSON) is a binary serialization format used by MongoDB.
- It is designed to store documents and make remote procedure calls.
- BSON supports various data types, each with specific use cases and behaviors.

**Key BSON Data Types**

1. **Double (Type Number: 1)**
   - Stores floating-point numbers.
   - Example:
     ```javascript
     { "price": 19.99 }
     ```
   - Used for values that require fractional precision, like prices.

2. **String (Type Number: 2)**
   - UTF-8 encoded strings.
   - Example:
     ```javascript
     { "name": "Alice" }
     ```
   - Suitable for storing textual data, including international characters.

3. **Object (Type Number: 3)**
   - Stores embedded documents.
   - Example:
     ```javascript
     { 
       "address": { 
         "street": "123 Main St", 
         "city": "Anytown" 
       } 
     }
     ```
   - Useful for organizing data hierarchically within a single document.

4. **Array (Type Number: 4)**
   - Stores lists of values.
   - Example:
     ```javascript
     { "colors": ["red", "green", "blue"] }
     ```
   - Allows storing multiple values in an ordered list.

5. **Binary Data (Type Number: 5)**
   - Used for storing byte arrays.
   - Example:
     ```javascript
     { "file": BinData(0, "base64EncodedData") }
     ```
   - Commonly used for files, images, and other binary content.

6. **ObjectId (Type Number: 7)**
   - A unique identifier for each document.
   - Automatically generated if not provided.
   - Example:
     ```javascript
     { "_id": ObjectId("507f1f77bcf86cd799439011") }
     ```
   - Includes a timestamp, making it easy to sort by creation time.

7. **Boolean (Type Number: 8)**
   - Stores `true` or `false`.
   - Example:
     ```javascript
     { "isActive": true }
     ```
   - Used for binary states, like flags.

8. **Date (Type Number: 9)**
   - Stores dates as the number of milliseconds since the Unix epoch (Jan 1, 1970).
   - Example:
     ```javascript
     { "created_at": ISODate("2024-08-24T16:20:00Z") }
     ```
   - Supports a wide range of dates, past and future.

9. **Null (Type Number: 10)**
   - Represents a null value.
   - Example:
     ```javascript
     { "middleName": null }
     ```
   - Useful for fields that may not have a value.

10. **Regular Expression (Type Number: 11)**
    - Stores regex patterns.
    - Example:
      ```javascript
      { "pattern": /abc/i }
      ```
    - Useful for querying documents with pattern matching.

11. **32-bit Integer (Type Number: 16)**
    - Stores signed 32-bit integers.
    - Example:
      ```javascript
      { "age": 25 }
      ```
    - Used for storing whole numbers within the 32-bit range.

12. **Timestamp (Type Number: 17)**
    - Internal MongoDB type for storing timestamps.
    - Not typically used for application-level data.
    - Automatically managed by MongoDB for operations like replication.

13. **64-bit Integer (Type Number: 18)**
    - Stores signed 64-bit integers.
    - Example:
      ```javascript
      { "largeNumber": NumberLong("9223372036854775807") }
      ```
    - Useful for storing very large numbers.

14. **Decimal128 (Type Number: 19)**
    - Stores high-precision decimal values.
    - Example:
      ```javascript
      { "preciseValue": NumberDecimal("1234.5678") }
      ```
    - Ideal for financial data requiring exact precision.

15. **MinKey and MaxKey (Type Numbers: -1 and 127)**
    - Special types used to define range boundaries.
    - Example:
      ```javascript
      { "minField": MinKey, "maxField": MaxKey }
      ```
    - Used in queries to represent the lowest or highest possible values.

### Code Examples with Explanations

- **Inserting a document with various types:**
  ```javascript
  db.collection.insertOne({
    name: "John Doe",
    age: 30,
    price: 19.99,
    active: true,
    createdAt: new Date(),
    tags: ["developer", "mongodb"],
    contact: {
      email: "john.doe@example.com",
      phone: null
    },
    _id: ObjectId()
  });
  ```
  - **Explanation:**
    - `"name": "John Doe"` uses the String type to store the name.
    - `"age": 30` uses the 32-bit Integer type.
    - `"price": 19.99` uses the Double type for precision.
    - `"active": true` uses the Boolean type.
    - `"createdAt": new Date()` stores the current date using the Date type.
    - `"tags": ["developer", "mongodb"]` is an Array of Strings.
    - `"contact": {...}` embeds another document (Object) for structured data.
    - `"_id": ObjectId()` automatically generates a unique identifier.

These notes should help beginners understand the basics of BSON types in MongoDB, along with practical examples and their use cases.
