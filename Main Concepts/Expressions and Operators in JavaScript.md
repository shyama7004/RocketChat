# **Expressions and Operators in JavaScript**

---

### **1. Expressions in JavaScript**

Expressions are snippets of code that evaluate to produce a value. They can involve variables, literals, function calls, and more.

#### **1.1. Primary Expressions**
Primary expressions are the most basic forms of expressions that directly represent values:

1. **Literals**:
    - Literal values represent fixed values in JavaScript.
    - **Numeric Literals**:
        ```js
        let number = 42; // Number literal
        let decimal = 3.14; // Decimal number
        ```
    - **String Literals**:
        ```js
        let greeting = "Hello, World!"; // String literal
        let name = 'Alice'; // Single-quoted string
        ```
    - **Boolean Literals**:
        ```js
        let isActive = true; // Boolean true
        let isLoggedIn = false; // Boolean false
        ```
    - **Null Literal**:
        ```js
        let emptyValue = null; // Represents an intentional absence of any value
        ```

2. **Variables**:
    - Variables reference values stored in memory.
    - **Example**:
        ```js
        let age = 25; // age is a variable holding a number
        let color = "blue"; // color holds a string
        ```

3. **Keyword Literals**:
    - Includes keywords like `this`, `super`, `undefined`.
    - **Example**:
        ```js
        function greet() {
            console.log(this.name); // 'this' refers to the object calling the method
        }
        ```

#### **1.2. Left-Hand-Side Expressions**
These expressions appear on the left side of assignment operations and indicate the target of assignment.

1. **Assignments to Variables**:
    - **Example**:
        ```js
        let x = 10; // Assigns value 10 to x
        ```

2. **Object Property Assignments**:
    - **Example**:
        ```js
        let car = {};
        car.model = "Tesla"; // 'model' is assigned a value inside the 'car' object
        ```

3. **Array Element Assignments**:
    - **Example**:
        ```js
        let fruits = ["Apple", "Banana"];
        fruits[1] = "Orange"; // Updates the value at index 1
        ```

4. **Function Calls**:
    - Functions can also be considered left-hand-side expressions when used in conjunction with assignment.
    - **Example**:
        ```js
        let result = myFunction(); // The function call is evaluated, and the result is assigned to 'result'
        ```

---

### **2. Operators in JavaScript**

Operators manipulate values or perform specific operations on them. They can be broadly categorized into several types:

#### **2.1. Assignment Operators**

Assignment operators assign a value to a variable. The most basic operator is `=`.

1. **Simple Assignment (`=`)**:
    - Assigns a value to a variable.
    - **Example**:
        ```js
        let x = 10; // x is now 10
        let name = "Alice"; // name is now "Alice"
        ```

2. **Compound Assignment Operators**:
    - These operators perform an operation and then assign the result.
    - **Examples**:
        ```js
        let a = 5;

        a += 2; // Equivalent to: a = a + 2 (a is now 7)
        a -= 1; // Equivalent to: a = a - 1 (a is now 6)
        a *= 3; // Equivalent to: a = a * 3 (a is now 18)
        a /= 2; // Equivalent to: a = a / 2 (a is now 9)
        a %= 4; // Equivalent to: a = a % 4 (a is now 1)
        a **= 2; // Equivalent to: a = a ** 2 (a is now 1)
        ```

#### **2.2. Comparison Operators**

Comparison operators compare two values and return a boolean result (`true` or `false`). These operators are commonly used in conditional statements.

1. **Equality Operators**:
    - **Loose Equality (`==`)**:
        - Compares two values for equality after type conversion (type coercion).
        - **Example**:
            ```js
            console.log(5 == '5'); // true, because the string '5' is converted to a number
            ```
    - **Strict Equality (`===`)**:
        - Compares both value and type without type coercion.
        - **Example**:
            ```js
            console.log(5 === '5'); // false, because the types are different
            ```
    - **Loose Inequality (`!=`)**:
        - Checks if two values are not equal after type conversion.
        - **Example**:
            ```js
            console.log(10 != '10'); // false, because '10' is coerced to 10
            ```
    - **Strict Inequality (`!==`)**:
        - Checks if two values are not equal in both type and value.
        - **Example**:
            ```js
            console.log(10 !== '10'); // true, because the types differ
            ```

2. **Relational Operators**:
    - **Greater Than (`>`)**:
        - **Example**:
            ```js
            console.log(7 > 5); // true
            ```
    - **Less Than (`<`)**:
        - **Example**:
            ```js
            console.log(3 < 8); // true
            ```
    - **Greater Than or Equal To (`>=`)**:
        - **Example**:
            ```js
            console.log(10 >= 10); // true
            ```
    - **Less Than or Equal To (`<=`)**:
        - **Example**:
            ```js
            console.log(4 <= 4); // true
            ```

3. **Comparison of Different Types**:
    - When comparing different types, JavaScript attempts to convert them to the same type:
    - **Example**:
        ```js
        console.log('7' > 5); // true, string '7' is converted to number 7
        ```

#### **2.3. Arithmetic Operators**

Arithmetic operators perform mathematical operations on numbers.

1. **Addition (`+`)**:
    - **Example**:
        ```js
        let sum = 10 + 5; // 15
        ```

2. **Subtraction (`-`)**:
    - **Example**:
        ```js
        let difference = 10 - 3; // 7
        ```

3. **Multiplication (`*`)**:
    - **Example**:
        ```js
        let product = 4 * 5; // 20
        ```

4. **Division (`/`)**:
    - **Example**:
        ```js
        let quotient = 20 / 4; // 5
        ```

5. **Remainder (Modulo) (`%`)**:
    - Returns the remainder after division.
    - **Example**:
        ```js
        let remainder = 9 % 2; // 1
        ```

6. **Exponentiation (`**`)**:
    - Raises a number to the power of another.
    - **Example**:
        ```js
        let power = 3 ** 2; // 9
        ```

7. **Increment and Decrement**:
    - **Increment (`++`)**:
        - **Example**:
            ```js
            let count = 5;
            count++; // Now count is 6
            ```
    - **Decrement (`--`)**:
        - **Example**:
            ```js
            let count = 5;
            count--; // Now count is 4
            ```

#### **2.4. Bitwise Operators**

Bitwise operators work directly on the binary representation of numbers.

1. **Bitwise AND (`&`)**:
    - Sets each bit to 1 if both corresponding bits are 1.
    - **Example**:
        ```js
        let a = 5; // 0101 in binary
        let b = 3; // 0011 in binary
        let result = a & b; // 0001 (1 in decimal)
        ```

2. **Bitwise OR (`|`)**:
    - Sets each bit to 1 if at least one corresponding bit is 1.
    - **Example**:
        ```js
        let result = a | b; // 0111 (7 in decimal)
        ```

3. **Bitwise XOR (`^`)**:
    - Sets each bit to 1 if only one of the corresponding bits is 1.
    - **Example**:
        ```js
        let result = a ^ b; // 0110 (6 in decimal)
        ```

4. **Bitwise NOT (`~`)**:
    - Inverts each bit (0 becomes 1, and 1 becomes 0).
    - **Example**:
        ```js
        let result = ~a; // 1010 (-6 in decimal due to 2's complement)
        ```
Sure, let's continue with a highly detailed breakdown of the remaining operators in JavaScript:

---

#### **2.5. Logical Operators**

Logical operators are typically used with boolean (true/false) values but can also be applied to non-boolean values in JavaScript. They include AND (`&&`), OR (`||`), and NOT (`!`).

1. **Logical AND (`&&`)**:
    - Returns `true` if both operands are true; otherwise, it returns `false`.
    - **Usage**: Commonly used in conditional statements to check if multiple conditions are true.
    - **Examples**:
        ```js
        let isAdult = true;
        let hasID = false;

        if (isAdult && hasID) {
            console.log("You may enter."); // This block won't execute because hasID is false
        } else {
            console.log("Access denied."); // Output: Access denied.
        }
        ```

    - **Short-Circuit Evaluation**: If the first operand is `false`, the second operand is not evaluated.
    - **Example**:
        ```js
        let result = false && (10 > 2); // false (the expression after && is ignored)
        ```

2. **Logical OR (`||`)**:
    - Returns `true` if at least one operand is true; otherwise, it returns `false`.
    - **Usage**: Commonly used when you want to check if at least one condition is true.
    - **Examples**:
        ```js
        let isWeekend = true;
        let isHoliday = false;

        if (isWeekend || isHoliday) {
            console.log("You can relax!"); // Output: You can relax!
        } else {
            console.log("Time to work.");
        }
        ```

    - **Short-Circuit Evaluation**: If the first operand is `true`, the second operand is not evaluated.
    - **Example**:
        ```js
        let result = true || (5 > 3); // true (the expression after || is ignored)
        ```

3. **Logical NOT (`!`)**:
    - Inverts the boolean value: `true` becomes `false` and vice versa.
    - **Examples**:
        ```js
        let isLoggedIn = true;
        console.log(!isLoggedIn); // Output: false

        let isAvailable = false;
        console.log(!isAvailable); // Output: true
        ```

    - **Double Negation (`!!`)**: Often used to convert a value to its boolean equivalent.
    - **Example**:
        ```js
        console.log(!!"Hello"); // true (non-empty strings are truthy)
        console.log(!!0); // false (0 is falsy)
        ```

#### **2.6. String Operators**

String operators are used primarily for concatenation (joining) of strings.

1. **Concatenation (`+`)**:
    - Combines multiple strings into one.
    - **Example**:
        ```js
        let greeting = "Hello, " + "world!";
        console.log(greeting); // Output: Hello, world!

        let firstName = "Alice";
        let message = "Hi " + firstName + ", welcome back!";
        console.log(message); // Output: Hi Alice, welcome back!
        ```

2. **Concatenation Assignment (`+=`)**:
    - Appends a string to an existing variable’s value.
    - **Example**:
        ```js
        let text = "JavaScript is ";
        text += "awesome!";
        console.log(text); // Output: JavaScript is awesome!
        ```

#### **2.7. Conditional (Ternary) Operator**

The ternary operator is a compact alternative to `if-else` statements. Its syntax is:
```js
condition ? expressionIfTrue : expressionIfFalse;
```

1. **Usage**:
    - The ternary operator checks a condition and returns one of two expressions based on the condition’s truth value.
    - **Examples**:
        ```js
        let age = 18;
        let canVote = age >= 18 ? "Yes, you can vote." : "No, you cannot vote.";
        console.log(canVote); // Output: Yes, you can vote.

        let score = 70;
        let result = score > 50 ? "Pass" : "Fail";
        console.log(result); // Output: Pass
        ```

    - **Nesting Ternary Operators**: You can nest ternary operators, though this may reduce code readability.
    - **Example**:
        ```js
        let age = 25;
        let category = age < 13 ? "Child" : age < 20 ? "Teen" : "Adult";
        console.log(category); // Output: Adult
        ```

#### **2.8. Comma Operator**

The comma operator (`,`) allows multiple expressions to be evaluated in sequence, returning the value of the last expression.

1. **Usage**:
    - Commonly used to execute multiple operations within a single statement.
    - **Examples**:
        ```js
        let a, b, c;
        a = (b = 1, c = 2); // b is 1, c is 2, and a is assigned the value of the last expression (2)
        console.log(a); // Output: 2

        let x = (3, 5, 7); // x is assigned the value 7
        console.log(x); // Output: 7
        ```

#### **2.9. Unary Operators**

Unary operators are those that operate on a single operand. They include unary plus (`+`), unary minus (`-`), logical NOT (`!`), `typeof`, `delete`, and more.

1. **Unary Plus (`+`)**:
    - Converts its operand to a number.
    - **Examples**:
        ```js
        let str = "5";
        let num = +str; // Converts the string "5" to the number 5
        console.log(num); // Output: 5
        ```

2. **Unary Minus (`-`)**:
    - Negates its operand (changes the sign).
    - **Examples**:
        ```js
        let x = 10;
        let y = -x; // y is -10
        console.log(y); // Output: -10
        ```

3. **Logical NOT (`!`)**:
    - Inverts the boolean value.
    - **Examples**:
        ```js
        let isTrue = !false; // true
        let isFalse = !true; // false
        ```

4. **Typeof Operator**:
    - Returns a string indicating the type of the operand.
    - **Examples**:
        ```js
        console.log(typeof 42); // Output: "number"
        console.log(typeof "Hello"); // Output: "string"
        console.log(typeof true); // Output: "boolean"
        console.log(typeof undefined); // Output: "undefined"
        console.log(typeof { key: "value" }); // Output: "object"
        console.log(typeof function() {}); // Output: "function"
        ```

5. **Delete Operator**:
    - Removes a property from an object.
    - **Usage**: Primarily used to delete object properties.
    - **Examples**:
        ```js
        let obj = { name: "Alice", age: 25 };
        delete obj.age; // Deletes the 'age' property
        console.log(obj); // Output: { name: "Alice" }
        ```

    - **Note**: The `delete` operator does not remove variables or functions.

#### **2.10. Relational Operators**

Relational operators determine the relationship between values or objects. They can be used for comparison beyond just numbers.

1. **String Comparison**:
    - JavaScript compares strings based on their lexicographical order (alphabetical order).
    - **Examples**:
        ```js
        console.log("apple" < "banana"); // true
        console.log("cat" > "bat"); // true
        ```

    - **Character Code Comparison**: String comparison is based on Unicode values.
    - **Example**:
        ```js
        console.log("a" < "b"); // true, because 'a' has a lower Unicode value than 'b'
        ```

2. **Object Comparison**:
    - Objects are compared by reference, not by value.
    - **Examples**:
        ```js
        let obj1 = { key: "value" };
        let obj2 = { key: "value" };
        console.log(obj1 == obj2); // false, because they reference different objects

        let obj3 = obj1;
        console.log(obj1 == obj3); // true, because they reference the same object
        ```

---
