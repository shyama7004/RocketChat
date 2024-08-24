# Objects

### **Understanding Objects in JavaScript**

#### **1. What is an Object?**
- **Definition**: In JavaScript, an object is a collection of related data or functionality, consisting of key-value pairs. The keys are strings (or symbols) and the values can be of any type (like numbers, strings, arrays, functions, or other objects).
- **Syntax**:
  ```javascript
  let person = {
    name: "John",         // String property
    age: 30,              // Number property
    isStudent: true,      // Boolean property
    hobbies: ["reading", "sports"], // Array property
    greet: function() {   // Function property (method)
      console.log("Hello!");
    }
  };
  ```
  **Explanation**: 
  - `person` is an object.
  - **Properties**:
    - `name`, `age`, `isStudent`, `hobbies`, and `greet` are keys (also known as properties).
    - `"John"`, `30`, `true`, `["reading", "sports"]`, and a function are values associated with these keys.
  - Objects can contain various types of data and even functions as their values.

#### **2. Accessing Object Properties**
- **Dot Notation**: Use dot notation to access the value of a property.
  ```javascript
  console.log(person.name); // Output: John
  console.log(person.age);  // Output: 30
  ```
  **Explanation**:
  - `person.name` accesses the value of the `name` property in the `person` object, which is `"John"`.
  - `person.age` accesses the value of the `age` property, which is `30`.

- **Bracket Notation**: Use bracket notation, especially when the key is stored in a variable or the key has special characters or spaces.
  ```javascript
  console.log(person["isStudent"]); // Output: true
  ```
  **Explanation**:
  - `person["isStudent"]` accesses the value of the `isStudent` property, which is `true`.
  - Bracket notation allows using keys that might not be valid identifiers in dot notation.

- **Using Variables in Bracket Notation**:
  ```javascript
  let key = "hobbies";
  console.log(person[key]); // Output: ["reading", "sports"]
  ```
  **Explanation**:
  - Here, the variable `key` holds the string `"hobbies"`, so `person[key]` accesses the `hobbies` property.

#### **3. Modifying Object Properties**
- **Updating Property Values**: You can change the value of a property using either dot or bracket notation.
  ```javascript
  person.age = 31;       // Using dot notation
  person["name"] = "Jane"; // Using bracket notation
  console.log(person.age);  // Output: 31
  console.log(person.name); // Output: Jane
  ```
  **Explanation**:
  - `person.age = 31` updates the `age` property to `31`.
  - `person["name"] = "Jane"` updates the `name` property to `"Jane"`.

- **Adding New Properties**: You can add new properties to an object dynamically.
  ```javascript
  person.gender = "male";       // Adding a new property using dot notation
  person["country"] = "USA";    // Adding a new property using bracket notation
  console.log(person.gender);   // Output: male
  console.log(person.country);  // Output: USA
  ```
  **Explanation**:
  - `person.gender = "male"` adds a new property `gender` with the value `"male"`.
  - `person["country"] = "USA"` adds a new property `country` with the value `"USA"`.

#### **4. Removing Object Properties**
- **Deleting Properties**: Use the `delete` keyword to remove properties from an object.
  ```javascript
  delete person.isStudent;      // Removes the isStudent property
  console.log(person.isStudent); // Output: undefined
  ```
  **Explanation**:
  - `delete person.isStudent` removes the `isStudent` property from the `person` object.
  - Accessing `person.isStudent` after deletion returns `undefined`, indicating the property no longer exists.

#### **5. Checking for Property Existence**
- **`in` Operator**: Checks if a property exists in an object.
  ```javascript
  console.log("name" in person);  // Output: true
  console.log("isStudent" in person); // Output: false
  ```
  **Explanation**:
  - `"name" in person` checks if the `name` property exists in the `person` object (returns `true`).
  - `"isStudent" in person` checks if the `isStudent` property exists in the `person` object (returns `false`).

- **`hasOwnProperty` Method**: Checks if a property exists in the object itself (not in its prototype chain).
  ```javascript
  console.log(person.hasOwnProperty("name")); // Output: true
  ```
  **Explanation**:
  - `person.hasOwnProperty("name")` checks if `person` has `name` as its own property (not inherited from the prototype chain).

#### **6. Iterating Over Object Properties**
- **`for...in` Loop**: Used to loop through all the enumerable properties of an object.
  ```javascript
  for (let key in person) {
    console.log(key + ": " + person[key]);
  }
  ```
  **Explanation**:
  - The `for...in` loop iterates over all the keys in the `person` object.
  - `key` is the variable representing each key, and `person[key]` retrieves the corresponding value.

- **Example Output**:
  ```
  name: Jane
  age: 31
  hobbies: reading,sports
  gender: male
  country: USA
  greet: function() { console.log("Hello!"); }
  ```

#### **7. Object Methods**
- **Adding Methods to Objects**: Methods are functions stored as object properties.
  ```javascript
  let person = {
    name: "John",
    age: 30,
    greet: function() {
      console.log("Hello, my name is " + this.name);
    }
  };
  person.greet(); // Output: Hello, my name is John
  ```
  **Explanation**:
  - `greet` is a method (a function stored in an object).
  - `this.name` refers to the `name` property of the `person` object. It allows the method to access other properties of the same object.

#### **8. Objects and `this` Keyword**
- **Understanding `this`**: In a method, `this` refers to the object the method belongs to.
  ```javascript
  let car = {
    brand: "Toyota",
    start: function() {
      console.log("Starting " + this.brand);
    }
  };
  car.start(); // Output: Starting Toyota
  ```
  **Explanation**:
  - Inside the `start` method, `this.brand` refers to the `brand` property of the `car` object.

#### **9. Nested Objects**
- **Objects Within Objects**: You can have objects as property values within another object.
  ```javascript
  let person = {
    name: "John",
    address: {
      city: "New York",
      zip: "10001"
    }
  };
  console.log(person.address.city); // Output: New York
  ```
  **Explanation**:
  - `address` is a nested object inside the `person` object.
  - `person.address.city` accesses the `city` property of the nested `address` object.

#### **10. Copying Objects**
- **Shallow Copy**: Copying only the top-level properties.
  ```javascript
  let copiedPerson = Object.assign({}, person);
  console.log(copiedPerson); // Output: { name: 'John', address: { city: 'New York', zip: '10001' } }
  ```
  **Explanation**:
  - `Object.assign({}, person)` creates a shallow copy of `person`.
  - The `copiedPerson` has its own separate copy of top-level properties, but nested objects are still references to the original ones.

- **Deep Copy**: Copying all levels of an object.
  ```javascript
  let deepCopiedPerson = JSON.parse(JSON.stringify(person));
  console.log(deepCopiedPerson); // Output: { name: 'John', address: { city: 'New York', zip: '10001' } }
  ```
  **Explanation**:
  - `JSON.parse(JSON.stringify(person))` creates a deep copy, duplicating all levels of the object, so changes in the copied object don't affect the original.

#### **11. Merging Objects**
- **Merging Using `Object.assign()`**:
  ```javascript
  let object1 = { a: 1, b: 2 };
  let object2 = { b: 3, c: 4 };
  let mergedObject = Object.assign({}, object1, object2);
  console.log(mergedObject); // Output: { a: 1, b: 3, c: 4 }
  ```
  **Explanation**:
  - `Object.assign({}, object1, object2)` merges `object1` and `object2` into a new object `mergedObject`.
  - If there are conflicting

 keys, the value from the last object (`object2` in this case) is used.

- **Merging Using the Spread Operator**:
  ```javascript
  let mergedObject = { ...object1, ...object2 };
  console.log(mergedObject); // Output: { a: 1, b: 3, c: 4 }
  ```
  **Explanation**:
  - `{ ...object1, ...object2 }` is a shorthand for merging objects. It works similarly to `Object.assign()`.
