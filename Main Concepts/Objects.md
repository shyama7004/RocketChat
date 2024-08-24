# Objects

### JavaScript Data Types
JavaScript is a dynamically typed language, which means variables can hold values of any type without a strict type declaration. The data types in JavaScript can be broadly classified into two categories: **Primitive Data Types** and **Reference Data Types**.

#### 1. Primitive Data Types:
   - **String**: Represents textual data. Example:
     ```javascript
     let name = "John Doe";
     ```
   - **Number**: Represents both integer and floating-point numbers. Example:
     ```javascript
     let age = 25;
     let price = 19.99;
     ```
   - **Boolean**: Represents logical values `true` or `false`. Example:
     ```javascript
     let isStudent = true;
     ```
   - **Undefined**: A variable that has been declared but not assigned a value. Example:
     ```javascript
     let score;
     ```
   - **Null**: Represents the intentional absence of any object value. Example:
     ```javascript
     let user = null;
     ```
   - **Symbol**: Represents a unique and immutable identifier. Example:
     ```javascript
     let sym = Symbol('description');
     ```
   - **BigInt**: Represents integers with arbitrary precision. Example:
     ```javascript
     let bigNumber = BigInt(9007199254740991);
     ```

#### 2. Reference Data Types:
   - **Object**: Collections of key-value pairs. Example:
     ```javascript
     let person = {
         name: "Alice",
         age: 30
     };
     ```
   - **Array**: A list-like structure that stores multiple values. Example:
     ```javascript
     let numbers = [1, 2, 3, 4, 5];
     ```
   - **Function**: A block of code designed to perform a particular task. Example:
     ```javascript
     function greet() {
         console.log("Hello, World!");
     }
     ```

### Data Structures in JavaScript
JavaScript provides several built-in data structures, including:

#### 1. **Arrays**:
   Arrays are list-like objects that can store multiple values in a single variable. They are zero-indexed, meaning the first element is at index 0.

   Example:
   ```javascript
   let fruits = ["Apple", "Banana", "Cherry"];
   console.log(fruits[1]); // Outputs: Banana
   ```

#### 2. **Maps**:
   A `Map` object holds key-value pairs, where keys can be of any data type.

   Example:
   ```javascript
   let map = new Map();
   map.set('name', 'John');
   map.set('age', 25);
   console.log(map.get('name')); // Outputs: John
   ```

#### 3. **Sets**:
   A `Set` object lets you store unique values of any type.

   Example:
   ```javascript
   let set = new Set([1, 2, 3, 4, 4, 5]);
   console.log(set.size); // Outputs: 5 (duplicates are not counted)
   ```

#### 4. **WeakMap**:
   Similar to `Map`, but keys must be objects and the key-value pairs can be garbage collected if there is no other reference to the key object.

   Example:
   ```javascript
   let weakMap = new WeakMap();
   let obj = {};
   weakMap.set(obj, "some value");
   ```

#### 5. **WeakSet**:
   Similar to `Set`, but values must be objects, and the objects can be garbage collected if there are no other references to them.

   Example:
   ```javascript
   let weakSet = new WeakSet();
   let obj = {};
   weakSet.add(obj);
   ```

### Type Conversion
JavaScript provides type conversion between different data types, which can be implicit (automatic) or explicit (manual).

#### Implicit Conversion:
   - Converting a number to a string:
     ```javascript
     let result = "The number is " + 5; // Outputs: The number is 5
     ```

#### Explicit Conversion:
   - Using the `String()` function:
     ```javascript
     let num = 5;
     let str = String(num); // Converts number to string
     ```

### Functions
Functions are first-class citizens in JavaScript, meaning they can be assigned to variables, passed as arguments, and returned from other functions.

Example:
```javascript
function add(a, b) {
    return a + b;
}
let sum = add(5, 10); // Outputs: 15
```

This overview covers the foundational aspects of JavaScript data types and data structures, with code examples to illustrate their usage. These concepts are crucial for understanding how to manipulate and work with data in JavaScript effectively.
