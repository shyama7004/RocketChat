# **JavaScript Data Types and Data Structures**

### **1. Primitive Data Types**
JavaScript has seven built-in types that are considered primitive. These types are immutable, meaning their values cannot be changed. Let's dive into each one:

#### **1.1 Number**
The `Number` type represents both integer and floating-point numbers. JavaScript uses the IEEE 754 double-precision floating-point format.

- **Examples**:
  ```javascript
  let age = 30;       // Integer
  let temperature = 98.6;  // Floating-point number
  let big = 1.23e5;   // Exponential notation (123000)
  ```

- **Key Points**:
  - Numbers can be positive, negative, or decimal.
  - Special numeric values: `Infinity`, `-Infinity`, and `NaN` (Not a Number).

  ```javascript
  console.log(1 / 0); // Infinity
  console.log(-1 / 0); // -Infinity
  console.log("abc" / 2); // NaN
  ```

#### **1.2 String**
A `String` in JavaScript is a sequence of characters used to represent text. Strings are immutable.

- **Examples**:
  ```javascript
  let greeting = "Hello, World!";
  let singleQuote = 'Single quotes are also fine.';
  let multiline = `Multiline
  string using template literals.`;
  ```

- **String Interpolation** (using template literals):
  ```javascript
  let name = "John";
  let message = `Hello, ${name}!`;  // "Hello, John!"
  ```

#### **1.3 Boolean**
The `Boolean` type has only two possible values: `true` or `false`. It is typically used for conditional testing.

- **Examples**:
  ```javascript
  let isJavaScriptFun = true;
  let isOldEnough = false;
  ```

- **Boolean Context**:
  - All values are either "truthy" or "falsy".
  - `Falsy` values include: `false`, `0`, `""` (empty string), `null`, `undefined`, and `NaN`.

  ```javascript
  console.log(Boolean(0)); // false
  console.log(Boolean("Hello")); // true
  ```

#### **1.4 Undefined**
A variable that has been declared but has not yet been assigned a value is of type `undefined`.

- **Example**:
  ```javascript
  let x;
  console.log(x); // undefined
  ```

#### **1.5 Null**
The `null` value represents the intentional absence of any object value. It is one of JavaScript's primitive values.

- **Example**:
  ```javascript
  let y = null;
  console.log(y); // null
  ```

- **Difference between `undefined` and `null`**:
  - `undefined` is automatically assigned to a variable that has been declared but not initialized.
  - `null` is an assignment value that represents "no value."

#### **1.6 Symbol**
`Symbol` is a unique and immutable primitive value that is often used as the key of an object property.

- **Example**:
  ```javascript
  let sym1 = Symbol('description');
  let sym2 = Symbol('description');
  console.log(sym1 === sym2); // false
  ```

- **Usage**:
  - Symbols are mainly used to avoid property name collisions when working with objects, especially when multiple scripts or libraries are involved.

#### **1.7 BigInt**
The `BigInt` type is used for arbitrarily large integers. It allows you to represent integers with arbitrary precision.

- **Example**:
  ```javascript
  let bigNumber = BigInt(9007199254740991); // Maximum safe integer
  let anotherBigNumber = 1234567890123456789012345678901234567890n;
  ```

- **Operations**:
  - BigInt values cannot be mixed with regular numbers.
  - Use `BigInt` methods for operations involving large integers.

  ```javascript
  let sum = bigNumber + 1n; // Works with BigInt
  ```

### **2. Objects**
Objects in JavaScript are collections of key-value pairs. Unlike primitive data types, objects are mutable, meaning their properties can be changed.

#### **2.1 Creating an Object**
You can create an object using an object literal or by using the `Object` constructor.

- **Object Literal**:
  ```javascript
  let person = {
      name: "John",
      age: 30,
      isStudent: true
  };
  ```

- **Accessing Object Properties**:
  You can access properties using dot notation or bracket notation.
  ```javascript
  console.log(person.name); // John
  console.log(person['age']); // 30
  ```

- **Adding/Modifying Properties**:
  ```javascript
  person.job = "Developer";  // Add a new property
  person.age = 31;  // Modify an existing property
  ```

- **Deleting Properties**:
  ```javascript
  delete person.isStudent;
  ```

#### **2.2 Nested Objects**
Objects can contain other objects as properties, forming complex data structures.

- **Example**:
  ```javascript
  let person = {
      name: "John",
      address: {
          city: "New York",
          zip: 10001
      }
  };
  console.log(person.address.city); // New York
  ```

### **3. Arrays**
Arrays are used to store multiple values in a single variable. JavaScript arrays are dynamic, meaning they can grow and shrink in size.

#### **3.1 Creating an Array**
You can create an array using an array literal or the `Array` constructor.

- **Array Literal**:
  ```javascript
  let colors = ["red", "green", "blue"];
  ```

- **Accessing Elements**:
  Arrays are zero-indexed, meaning the first element is at index `0`.
  ```javascript
  console.log(colors[0]); // red
  console.log(colors[2]); // blue
  ```

#### **3.2 Modifying Arrays**
You can modify elements in an array or add/remove elements.

- **Modifying Elements**:
  ```javascript
  colors[1] = "yellow"; // Change "green" to "yellow"
  ```

- **Adding Elements**:
  ```javascript
  colors.push("purple"); // Adds "purple" to the end
  colors.unshift("orange"); // Adds "orange" to the beginning
  ```

- **Removing Elements**:
  ```javascript
  colors.pop(); // Removes the last element
  colors.shift(); // Removes the first element
  ```

#### **3.3 Array Methods**
JavaScript provides several built-in methods to work with arrays.

- **forEach()**: Executes a function for each array element.
  ```javascript
  colors.forEach(function(color) {
      console.log(color);
  });
  ```

- **map()**: Creates a new array with the results of calling a function for every element.
  ```javascript
  let uppercaseColors = colors.map(color => color.toUpperCase());
  console.log(uppercaseColors); // ["RED", "YELLOW", "BLUE"]
  ```

- **filter()**: Creates a new array with all elements that pass a test.
  ```javascript
  let longColors = colors.filter(color => color.length > 3);
  console.log(longColors); // ["yellow", "blue"]
  ```

### **4. Functions as First-Class Objects**
In JavaScript, functions are treated as first-class objects. This means functions can be stored in variables, passed as arguments, and returned from other functions.

#### **4.1 Function Declaration**
A function can be declared using the `function` keyword.

- **Example**:
  ```javascript
  function greet() {
      return "Hello, World!";
  }
  ```

- **Calling a Function**:
  ```javascript
  console.log(greet()); // Hello, World!
  ```

#### **4.2 Function Expressions**
A function expression allows you to define a function inside an expression and assign it to a variable.

- **Example**:
  ```javascript
  let greet = function() {
      return "Hello, World!";
  };
  console.log(greet()); // Hello, World!
  ```

#### **4.3 Arrow Functions**
Arrow functions provide a more concise syntax for writing function expressions.

- **Example**:
  ```javascript
  let greet = () => "Hello, World!";
  console.log(greet()); // Hello, World!
  ```

#### **4.4 Higher-Order Functions**
Higher-order functions are functions that can accept other functions as arguments or return functions.

- **Example**:
  ```javascript
  function sayHello(greetFunction) {
      console.log(greetFunction());
  }

  sayHello(greet); // Hello, World!
  ```

### **5. Type Conversion**
JavaScript allows implicit (automatic) and explicit (manual) type conversion between different types.

#### **5.1 String to Number Conversion**
You can convert a string to a number using the `Number()` function or by using the unary `+` operator.

- **Examples**:
  ```javascript
  let num = "42";
  let convertedNum = Number(num); // 42
  let shortConversion = +num; // 42
  ```

#### **5.2 Number to String Conversion**
You can convert a number to a string using
the `String()` function or the `toString()` method.

- **Examples**:
  ```javascript
  let n = 42;
  let str = String(n); // "42"
  let anotherStr = n.toString(); // "42"
  ```

#### **5.3 Boolean Conversion**
JavaScript can convert values to `true` or `false` based on their "truthiness" or "falsiness". You can manually convert a value to a Boolean using the `Boolean()` function.

- **Examples**:
  ```javascript
  let isZeroFalse = Boolean(0); // false
  let isOneTrue = Boolean(1); // true
  let isEmptyStringFalse = Boolean(""); // false
  let isNonEmptyStringTrue = Boolean("Hello"); // true
  ```

- **Implicit Boolean Conversion**:
  - In conditional statements like `if`, JavaScript automatically converts the condition to a Boolean.
  - Example:
    ```javascript
    if ("Hello") {
        console.log("This will run!"); // "Hello" is truthy, so this code runs.
    }

    if (0) {
        console.log("This won't run."); // 0 is falsy, so this code doesn't run.
    }
    ```

### **6. Data Structures Overview**
JavaScript provides a variety of data structures to store collections of data. Each structure has different use cases and performance characteristics.

#### **6.1 Arrays**
As mentioned earlier, arrays are ordered collections of values. They are particularly useful when you need to store data in a sequential manner.

- **Array Characteristics**:
  - Arrays are zero-indexed.
  - They can store multiple data types.
  - Arrays are dynamic and can change in size.

- **Example**:
  ```javascript
  let mixedArray = [1, "hello", true, {name: "John"}, [1, 2, 3]];
  console.log(mixedArray[3].name); // "John"
  ```

#### **6.2 Objects**
Objects are collections of key-value pairs, where keys are strings (or symbols) and values can be any data type. They are suitable for representing complex data structures.

- **Example**:
  ```javascript
  let car = {
      make: "Tesla",
      model: "Model 3",
      year: 2021
  };
  ```

- **Accessing Object Properties**:
  ```javascript
  console.log(car.make); // "Tesla"
  console.log(car["model"]); // "Model 3"
  ```

#### **6.3 Maps**
`Map` is a collection of key-value pairs where keys can be of any type (not just strings). Maps maintain the order of insertion and allow efficient key lookups.

- **Creating a Map**:
  ```javascript
  let map = new Map();
  map.set('name', 'Alice');
  map.set(1, 'one');
  map.set(true, 'yes');
  ```

- **Accessing Map Elements**:
  ```javascript
  console.log(map.get('name')); // "Alice"
  console.log(map.get(1)); // "one"
  console.log(map.size); // 3
  ```

- **Iterating Over a Map**:
  ```javascript
  map.forEach((value, key) => {
      console.log(key + " = " + value);
  });
  ```

#### **6.4 Sets**
`Set` is a collection of unique values. Unlike arrays, a `Set` cannot contain duplicate values.

- **Creating a Set**:
  ```javascript
  let set = new Set([1, 2, 3, 3, 4]);
  console.log(set); // Set { 1, 2, 3, 4 }
  ```

- **Adding and Checking Elements**:
  ```javascript
  set.add(5);
  console.log(set.has(3)); // true
  ```

- **Iterating Over a Set**:
  ```javascript
  set.forEach(value => {
      console.log(value);
  });
  ```

#### **6.5 WeakMap and WeakSet**
`WeakMap` and `WeakSet` are similar to `Map` and `Set`, but they hold weak references to objects. This means the references do not prevent garbage collection if there are no other references to the object.

- **WeakMap**: Only objects can be used as keys.
  ```javascript
  let weakMap = new WeakMap();
  let obj = {};
  weakMap.set(obj, 'Some value');
  ```

- **WeakSet**: Only objects can be added to a WeakSet.
  ```javascript
  let weakSet = new WeakSet();
  let obj1 = {};
  weakSet.add(obj1);
  ```

- **Key Characteristics**:
  - `WeakMap` and `WeakSet` are not iterable, so you cannot loop over their elements.
  - These structures are useful for scenarios where you want to store data associated with an object, and have that data automatically garbage collected when the object is no longer needed.

### **7. Immutable Data**
Immutability means that once a data structure is created, it cannot be changed. In JavaScript, primitive types like strings and numbers are immutable.

#### **7.1 Immutable Strings**
Strings in JavaScript cannot be altered once created. Any operations that appear to modify a string actually return a new string.

- **Example**:
  ```javascript
  let str = "hello";
  let newStr = str.toUpperCase(); // "HELLO"
  console.log(str); // "hello" (original string is unchanged)
  ```

#### **7.2 Immutable Numbers**
Numbers, like strings, are immutable. Arithmetic operations do not change the original number but return a new value.

- **Example**:
  ```javascript
  let num = 10;
  let newNum = num + 5; // 15
  console.log(num); // 10 (original number is unchanged)
  ```

### **8. Type Checking and Coercion**
JavaScript is a loosely typed language, meaning variables can hold any type of value without enforcing a type. However, it's important to understand how JavaScript handles type checking and coercion.

#### **8.1 Type Checking**
To check the type of a variable, you can use the `typeof` operator.

- **Examples**:
  ```javascript
  console.log(typeof 42); // "number"
  console.log(typeof "hello"); // "string"
  console.log(typeof true); // "boolean"
  console.log(typeof undefined); // "undefined"
  console.log(typeof null); // "object" (this is a quirk in JavaScript)
  console.log(typeof Symbol("sym")); // "symbol"
  ```

#### **8.2 Type Coercion**
JavaScript automatically converts values from one type to another when necessary, a process known as coercion.

- **Examples**:
  ```javascript
  console.log("5" - 1); // 4 (string "5" is coerced to number 5)
  console.log("5" + 1); // "51" (number 1 is coerced to string "1")
  console.log(true + 1); // 2 (true is coerced to number 1)
  console.log(false + 1); // 1 (false is coerced to number 0)
  ```

- **Avoiding Unintended Coercion**:
  To prevent unexpected results, it's often best to use explicit type conversions.

  ```javascript
  let result = Number("5") + 1; // 6 (explicit conversion)
  ```

### **9. Summary**
JavaScript offers a range of data types and structures, each with its own characteristics and use cases. Understanding these fundamentals is key to writing effective and efficient code. Here's a recap:

- **Primitive Types**: Simple and immutable data types like numbers, strings, booleans, etc.
- **Objects**: Collections of key-value pairs, used for more complex data structures.
- **Arrays**: Ordered collections of values, ideal for storing lists.
- **Maps and Sets**: More advanced data structures that provide greater flexibility in handling collections of data.
- **Type Conversion**: JavaScript's ability to automatically or manually convert between different types.
- **Immutability**: A concept where data structures cannot be altered after they are created.

These concepts form the foundation of JavaScript programming. Mastering them will help you understand more advanced topics and write better, more efficient code.

