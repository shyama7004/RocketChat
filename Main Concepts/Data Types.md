# Data Types
### 1. **Dynamic and Weak Typing**
   - **Dynamic Typing**: In JavaScript, the type of a variable can change at runtime. A variable can hold a value of one type and later be assigned a value of another type.
     - **Example**:
       ```javascript
       let x = 42; // x is a Number
       x = "Hello"; // Now x is a String
       ```
   - **Weak Typing**: JavaScript allows operations between different types, often converting one type to another automatically.
     - **Example**:
       ```javascript
       console.log(5 + "5"); // Outputs: '55' (Number 5 is converted to a String)
       ```

### 2. **Primitive Values**
   - **Primitive Types**: These are basic data types that represent a single value and include:
     - **String**
     - **Number**
     - **Boolean**
     - **Undefined**
     - **Null**
     - **Symbol**
     - **BigInt**
   - Primitive values are immutable, meaning they cannot be altered once created.

### 3. **Null Type**
   - **Null**: Represents the intentional absence of any object value. It is one of JavaScript's primitive values.
     - **Example**:
       ```javascript
       let value = null;
       console.log(value); // Outputs: null
       ```
   - **Type**: The type of `null` is an object (this is a quirk in JavaScript).
     - **Example**:
       ```javascript
       console.log(typeof null); // Outputs: object
       ```

### 4. **Undefined Type**
   - **Undefined**: Represents a variable that has been declared but not assigned a value.
     - **Example**:
       ```javascript
       let value;
       console.log(value); // Outputs: undefined
       ```
   - **Type**: The type of `undefined` is undefined.
     - **Example**:
       ```javascript
       console.log(typeof undefined); // Outputs: undefined
       ```

### 5. **Boolean Type**
   - **Boolean**: Represents two values: `true` and `false`.
     - **Example**:
       ```javascript
       let isCompleted = true;
       console.log(isCompleted); // Outputs: true
       ```
   - Boolean values are often used in control flow (e.g., `if` statements).

### 6. **Number Type**
   - **Number**: Represents both integer and floating-point numbers. JavaScript has a single number type.
     - **Example**:
       ```javascript
       let integer = 42;
       let float = 3.14;
       console.log(integer, float); // Outputs: 42 3.14
       ```
   - **Special Values**:
     - **NaN (Not-a-Number)**: Represents a computational error.
       - **Example**:
         ```javascript
         console.log(0 / 0); // Outputs: NaN
         ```
     - **Infinity** and **-Infinity**: Represent positive and negative infinity.
       - **Example**:
         ```javascript
         console.log(1 / 0); // Outputs: Infinity
         ```

### 7. **BigInt Type**
   - **BigInt**: Represents large integers that are outside the safe integer range for numbers in JavaScript (`Number.MAX_SAFE_INTEGER`).
     - **Example**:
       ```javascript
       let bigInt = 9007199254740991n;
       console.log(bigInt); // Outputs: 9007199254740991n
       ```
   - BigInt cannot be mixed with regular numbers in operations.
     - **Example**:
       ```javascript
       console.log(1n + 2); // Throws an error
       ```

### 8. **String Type**
   - **String**: Represents textual data enclosed in quotes (single, double, or backticks for template literals).
     - **Example**:
       ```javascript
       let greeting = "Hello, World!";
       console.log(greeting); // Outputs: Hello, World!
       ```
   - **String Methods**:
     - **length**: Returns the length of the string.
       - **Example**:
         ```javascript
         console.log(greeting.length); // Outputs: 13
         ```
     - **toUpperCase()** and **toLowerCase()**: Convert the string to upper or lower case.
       - **Example**:
         ```javascript
         console.log(greeting.toUpperCase()); // Outputs: HELLO, WORLD!
         ```

### 9. **Beware of "Stringly-Typing" Your Code!**
   - **Stringly-Typed Code**: Refers to the practice of using strings for various data, which can lead to errors and make the code harder to manage.
     - **Bad Practice**:
       ```javascript
       let status = "active";
       if (status === "active") {
           // Do something
       }
       ```
     - **Better Practice**:
       ```javascript
       const STATUS_ACTIVE = "active";
       let status = STATUS_ACTIVE;
       if (status === STATUS_ACTIVE) {
           // Do something
       }
       ```

### 10. **Symbol Type**
   - **Symbol**: Represents a unique and immutable identifier, often used as keys for object properties.
     - **Example**:
       ```javascript
       let id = Symbol('id');
       console.log(id); // Outputs: Symbol(id)
       ```
   - Symbols are unique, even if they have the same description.
     - **Example**:
       ```javascript
       let id1 = Symbol('id');
       let id2 = Symbol('id');
       console.log(id1 === id2); // Outputs: false
       ```

### 11. **Objects**
   - **Object**: A collection of key-value pairs, where keys are strings (or Symbols) and values can be any data type.
     - **Example**:
       ```javascript
       let person = {
           name: "Alice",
           age: 25,
           isStudent: true
       };
       console.log(person.name); // Outputs: Alice
       ```

### 12. **Properties**
   - **Property**: Each key-value pair in an object is called a property.
     - **Example**:
       ```javascript
       let car = {
           make: "Toyota",
           model: "Camry",
           year: 2020
       };
       console.log(car.model); // Outputs: Camry
       ```

### 13. **Data Property**
   - **Data Property**: Regular properties of an object that have a value.
     - **Example**:
       ```javascript
       let person = {
           name: "John",
           age: 30
       };
       ```
   - Properties can be added, modified, or deleted.
     - **Example**:
       ```javascript
       person.age = 31; // Modifies the age property
       delete person.name; // Deletes the name property
       console.log(person); // Outputs: { age: 31 }
       ```

### 14. **Accessor Property**
   - **Accessor Property**: Properties defined by getter and setter functions.
     - **Example**:
       ```javascript
       let person = {
           firstName: "John",
           lastName: "Doe",
           get fullName() {
               return `${this.firstName} ${this.lastName}`;
           },
           set fullName(name) {
               [this.firstName, this.lastName] = name.split(" ");
           }
       };
       console.log(person.fullName); // Outputs: John Doe
       person.fullName = "Jane Smith";
       console.log(person.firstName); // Outputs: Jane
       ```

### 15. **Dates**
   - **Date Object**: Used to handle dates and times in JavaScript.
     - **Creating Dates**:
       ```javascript
       let now = new Date();
       console.log(now); // Outputs the current date and time
       ```
     - **Date Methods**:
       - **getFullYear()**: Returns the year.
       - **getMonth()**: Returns the month (0-11).
       - **getDate()**: Returns the day of the month (1-31).
       - **getTime()**: Returns the timestamp (milliseconds since January 1, 1970).
       - **Example**:
         ```javascript
         console.log(now.getFullYear()); // Outputs: 2024 (or current year)
         ```

### 16. **Indexed Collections: Arrays and Typed Arrays**
   - **Arrays**: Ordered collections of values, which can be of any type.
     - **Example**:
       ```javascript
       let fruits = ["Apple", "Banana", "Cherry"];
       console.log(fruits[1]); // Outputs: Banana
       ```
     - **Array Methods**:
       - **push()**: Adds an item to the end.
       - **pop()**: Removes the last item.
       - **shift()**: Removes the first item.
       - **unshift()**: Adds an item to the beginning.
       - **Example**:
```javascript
         fruits.push("Orange");
         console.log(fruits); // Outputs: ["Apple", "Banana", "Cherry", "Orange"]
```
     

   - **Typed Array Methods**:
       - **set()**: Allows you to set multiple values at once.
       - **subarray()**: Creates a new Typed Array that shares the underlying buffer of the original array.
       - **Example**:
         ```javascript
         let buffer = new ArrayBuffer(16); // Create a buffer of 16 bytes
         let intView = new Int32Array(buffer);
         intView[0] = 42;
         console.log(intView[0]); // Outputs: 42
         ```

### 17. **Keyed Collections: Maps, Sets, WeakMaps, WeakSets**
   - **Map**: A collection of key-value pairs where keys can be of any type.
     - **Example**:
       ```javascript
       let map = new Map();
       map.set('name', 'Alice');
       map.set(1, 'one');
       console.log(map.get('name')); // Outputs: Alice
       ```
     - **Map Methods**:
       - **set(key, value)**: Adds or updates an element with a specified key and value.
       - **get(key)**: Returns the value associated with the key.
       - **has(key)**: Returns true if the key exists.
       - **delete(key)**: Removes an element by the key.
       - **clear()**: Removes all elements.
       - **Example**:
         ```javascript
         console.log(map.has('name')); // Outputs: true
         map.delete(1);
         console.log(map.size); // Outputs: 1
         ```

   - **Set**: A collection of unique values.
     - **Example**:
       ```javascript
       let set = new Set([1, 2, 3, 4, 4]); // Duplicates are removed
       console.log(set.size); // Outputs: 4
       ```
     - **Set Methods**:
       - **add(value)**: Adds a new element with the given value.
       - **has(value)**: Returns true if the value exists in the set.
       - **delete(value)**: Removes an element by value.
       - **clear()**: Removes all elements.
       - **Example**:
         ```javascript
         set.add(5);
         console.log(set.has(5)); // Outputs: true
         ```

   - **WeakMap**: A collection of key-value pairs where the keys are weakly referenced objects. Keys must be objects, and they can be garbage-collected if there are no other references to them.
     - **Example**:
       ```javascript
       let weakMap = new WeakMap();
       let obj = {};
       weakMap.set(obj, 'value');
       console.log(weakMap.get(obj)); // Outputs: 'value'
       obj = null; // The key-value pair is removed from the WeakMap
       ```

   - **WeakSet**: Similar to a Set but only stores objects and allows for garbage collection if no other references exist to the object.
     - **Example**:
       ```javascript
       let weakSet = new WeakSet();
       let obj = {};
       weakSet.add(obj);
       console.log(weakSet.has(obj)); // Outputs: true
       obj = null; // The object is removed from the WeakSet
       ```

### 18. **Structured Data: JSON**
   - **JSON (JavaScript Object Notation)**: A lightweight format for exchanging data. It is often used for serializing and transmitting structured data over a network.
     - **Example**:
       ```javascript
       let person = {
           name: "John",
           age: 30,
           isStudent: false
       };
       let jsonString = JSON.stringify(person);
       console.log(jsonString); // Outputs: '{"name":"John","age":30,"isStudent":false}'
       ```
     - **Methods**:
       - **JSON.stringify(object)**: Converts a JavaScript object into a JSON string.
       - **JSON.parse(string)**: Converts a JSON string back into a JavaScript object.
       - **Example**:
         ```javascript
         let jsonObject = JSON.parse(jsonString);
         console.log(jsonObject.name); // Outputs: John
         ```

### 19. **Type Coercion**
   - **Type Coercion**: The process of converting a value from one type to another (e.g., a string to a number).
     - **Example**:
       ```javascript
       console.log("5" - 2); // Outputs: 3 (String '5' is coerced to Number 5)
       ```

### 20. **Primitive Coercion**
   - **Primitive Coercion**: The conversion of primitive values to other types, often triggered by operators.
     - **String to Number**:
       ```javascript
       console.log(Number("123")); // Outputs: 123
       ```
     - **Number to String**:
       ```javascript
       console.log(String(123)); // Outputs: "123"
       ```
     - **Boolean to Number**:
       ```javascript
       console.log(Number(true)); // Outputs: 1
       console.log(Number(false)); // Outputs: 0
       ```

### 21. **Numeric Coercion**
   - **Numeric Coercion**: JavaScript will attempt to convert values to numbers in certain contexts (e.g., arithmetic operations).
     - **Example**:
       ```javascript
       console.log("5" * "2"); // Outputs: 10 (Both strings are coerced to numbers)
       ```

### 22. **Other Coercions**
   - **Object to Primitive**: When objects are used in contexts where a primitive value is expected, JavaScript attempts to convert the object to a primitive.
     - **Example**:
       ```javascript
       let obj = {
           valueOf() {
               return 42;
           }
       };
       console.log(obj + 2); // Outputs: 44 (Object is coerced to the number 42)
       ```
     - **`toString` and `valueOf` Methods**: Objects can define these methods to control their coercion behavior.
       - **Example**:
         ```javascript
         let obj = {
             toString() {
                 return "Hello";
             }
         };
         console.log(String(obj)); // Outputs: "Hello"
         ```
---
        
```
         Crafted by shyama7004, please follow if you found this doc useful:)
