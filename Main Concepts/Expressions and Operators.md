## **JavaScript Expressions and Operators: A Detailed Guide**

### **1. Expressions**
Expressions are fundamental in JavaScript, forming the building blocks of any JavaScript program. 

#### **1.1 What is an Expression?**
An expression is any valid unit of code that resolves to a value. This value can be of any type—number, string, object, etc. Expressions can be simple or complex, and they can involve variables, operators, functions, or literals.

- **Examples**:
  ```javascript
  5 + 3          // A simple expression, evaluates to 8
  "Hello" + " " + "World"  // A string expression, evaluates to "Hello World"
  x = 7          // An assignment expression, assigns 7 to x and evaluates to 7
  ```

#### **1.2 Types of Expressions**

**1.2.1 Primary Expressions**  
These are the most basic expressions in JavaScript. They include:

- **Literals**: Fixed values such as `3.14`, `'hello'`, `true`, `null`.
  ```javascript
  42           // Numeric literal
  "Hello"      // String literal
  true         // Boolean literal
  null         // Null literal
  ```

- **Keywords**: Predefined words with special meaning, like `this`, `super`.
  ```javascript
  this         // Refers to the current object in a method
  ```

- **Variable References**: Using variables in expressions.
  ```javascript
  let x = 10;
  x + 5        // Variable reference
  ```

**1.2.2 Left-hand-side Expressions**
These expressions appear on the left side of an assignment operator and represent the target of the assignment.

- **Variable Assignment**:
  ```javascript
  let a = 10;  // 'a' is a left-hand-side expression
  a = 5;       // Assigning 5 to a
  ```

- **Object Property Assignment**:
  ```javascript
  let person = { name: "John" };
  person.name = "Doe";  // 'person.name' is a left-hand-side expression
  ```

### **2. Operators**
Operators are symbols that perform operations on values (operands) and produce a result. JavaScript has a rich set of operators to perform various tasks, from arithmetic operations to logical operations.

#### **2.1 Arithmetic Operators**
These operators perform basic mathematical operations. 

**2.1.1 Addition (`+`)**
- **Usage**: Adds two operands.
- **Example**:
  ```javascript
  let sum = 10 + 5;  // 15
  let greeting = "Hello" + " " + "World";  // "Hello World"
  ```

**2.1.2 Subtraction (`-`)**
- **Usage**: Subtracts the second operand from the first.
- **Example**:
  ```javascript
  let diff = 10 - 5;  // 5
  ```

**2.1.3 Multiplication (`*`)**
- **Usage**: Multiplies two operands.
- **Example**:
  ```javascript
  let product = 10 * 5;  // 50
  ```

**2.1.4 Division (`/`)**
- **Usage**: Divides the first operand by the second.
- **Example**:
  ```javascript
  let quotient = 10 / 5;  // 2
  ```

**2.1.5 Modulus (`%`)**
- **Usage**: Returns the remainder of a division.
- **Example**:
  ```javascript
  let remainder = 10 % 3;  // 1 (3 goes into 10 three times, leaving a remainder of 1)
  ```

**2.1.6 Exponentiation (`**`)**
- **Usage**: Raises the first operand to the power of the second.
- **Example**:
  ```javascript
  let power = 2 ** 3;  // 8 (2 raised to the power of 3)
  ```

**2.1.7 Increment (`++`)**
- **Usage**: Increases an integer value by one.
- **Example**:
  ```javascript
  let x = 5;
  x++;  // x is now 6
  ```

**2.1.8 Decrement (`--`)**
- **Usage**: Decreases an integer value by one.
- **Example**:
  ```javascript
  let y = 5;
  y--;  // y is now 4
  ```

#### **2.2 Comparison Operators**
Comparison operators are used to compare two values. They return a Boolean (`true` or `false`).

**2.2.1 Equal (`==`)**
- **Usage**: Checks if two values are equal after type conversion.
- **Example**:
  ```javascript
  console.log(5 == '5');  // true (performs type conversion)
  ```

**2.2.2 Strict Equal (`===`)**
- **Usage**: Checks if two values are equal and of the same type.
- **Example**:
  ```javascript
  console.log(5 === '5');  // false (no type conversion)
  ```

**2.2.3 Not Equal (`!=`)**
- **Usage**: Checks if two values are not equal after type conversion.
- **Example**:
  ```javascript
  console.log(5 != '5');  // false (performs type conversion)
  ```

**2.2.4 Strict Not Equal (`!==`)**
- **Usage**: Checks if two values are not equal or not of the same type.
- **Example**:
  ```javascript
  console.log(5 !== '5');  // true (no type conversion)
  ```

**2.2.5 Greater Than (`>`)**
- **Usage**: Checks if the left value is greater than the right value.
- **Example**:
  ```javascript
  console.log(10 > 5);  // true
  ```

**2.2.6 Greater Than or Equal (`>=`)**
- **Usage**: Checks if the left value is greater than or equal to the right value.
- **Example**:
  ```javascript
  console.log(10 >= 10);  // true
  ```

**2.2.7 Less Than (`<`)**
- **Usage**: Checks if the left value is less than the right value.
- **Example**:
  ```javascript
  console.log(10 < 5);  // false
  ```

**2.2.8 Less Than or Equal (`<=`)**
- **Usage**: Checks if the left value is less than or equal to the right value.
- **Example**:
  ```javascript
  console.log(10 <= 10);  // true
  ```

#### **2.3 Logical Operators**
Logical operators are used to combine or invert Boolean values.

**2.3.1 Logical AND (`&&`)**
- **Usage**: Returns `true` if both operands are true.
- **Example**:
  ```javascript
  console.log(true && false);  // false
  console.log(true && true);   // true
  ```

**2.3.2 Logical OR (`||`)**
- **Usage**: Returns `true` if at least one of the operands is true.
- **Example**:
  ```javascript
  console.log(true || false);  // true
  console.log(false || false); // false
  ```

**2.3.3 Logical NOT (`!`)**
- **Usage**: Inverts the Boolean value of the operand.
- **Example**:
  ```javascript
  console.log(!true);  // false
  console.log(!false); // true
  ```

#### **2.4 Assignment Operators**
Assignment operators are used to assign values to variables.

**2.4.1 Basic Assignment (`=`)**
- **Usage**: Assigns the right value to the left variable.
- **Example**:
  ```javascript
  let a = 10;  // 'a' now holds the value 10
  ```

**2.4.2 Addition Assignment (`+=`)**
- **Usage**: Adds the right value to the left variable and assigns the result.
- **Example**:
  ```javascript
  let b = 5;
  b += 3;  // b = b + 3, so b is now 8
  ```

**2.4.3 Subtraction Assignment (`-=`)**
- **Usage**: Subtracts the right value from the left variable and assigns the result.
- **Example**:
  ```javascript
  let c = 10;
  c -= 4;  // c = c - 4, so c is now 6
  ```

**2.4.4 Multiplication Assignment (`*=`)**
- **Usage**: Multiplies the left variable by the right value and assigns the result.
- **Example**:
  ```javascript
  let d = 5;
  d *= 2;  // d = d * 2, so d is now 10
  ```

**2.4.5 Division Assignment (`/=`)**
- **Usage**: Divides the left variable by the right value and assigns the result.
- **Example**:
  ```javascript
  let e = 20;
 

 e /= 4;  // e = e / 4, so e is now 5
  ```

**2.4.6 Modulus Assignment (`%=`)**
- **Usage**: Assigns the remainder of the division of the left variable by the right value.
- **Example**:
  ```javascript
  let f = 10;
  f %= 3;  // f = f % 3, so f is now 1
  ```

#### **2.5 Conditional (Ternary) Operator (`? :`)**
The conditional operator is a shorthand for the `if-else` statement. It evaluates a condition and returns one of two values based on the condition.

- **Syntax**:
  ```javascript
  condition ? exprIfTrue : exprIfFalse
  ```

- **Example**:
  ```javascript
  let age = 18;
  let canVote = (age >= 18) ? "Yes" : "No";
  console.log(canVote);  // "Yes"
  ```

#### **2.6 Typeof Operator**
The `typeof` operator returns the type of a variable as a string.

- **Usage**:
  ```javascript
  let num = 42;
  console.log(typeof num);  // "number"
  
  let str = "Hello";
  console.log(typeof str);  // "string"
  
  let obj = {name: "John"};
  console.log(typeof obj);  // "object"
  ```

### **3. Operator Precedence and Associativity**
Operator precedence determines the order in which operators are evaluated in expressions. Operators with higher precedence are evaluated before operators with lower precedence.

**3.1 Example of Precedence**:
```javascript
let result = 2 + 3 * 4;  // 14, because * has higher precedence than +
```

**3.2 Associativity**:
Associativity determines the order in which operators of the same precedence are processed.

- **Left-to-right**: Most operators like `+`, `-`, `*`, `/`.
- **Right-to-left**: Assignment operators like `=`, `+=`, `-=`.

**Example of Associativity**:
```javascript
let a = 10;
let b = 20;
let c = 30;

a = b = c;  // Here, '=' is right-to-left associative, so b = c is evaluated first, then a = b
console.log(a);  // 30
console.log(b);  // 30
console.log(c);  // 30
```

### **4. Bitwise Operators**
Bitwise operators treat their operands as a set of 32 bits (binary) rather than decimal, hexadecimal, or octal numbers.

**4.1 Bitwise AND (`&`)**
- **Usage**: Performs a bitwise AND operation on two operands.
- **Example**:
  ```javascript
  let result = 5 & 1;  // 1 (0101 & 0001 = 0001)
  ```

**4.2 Bitwise OR (`|`)**
- **Usage**: Performs a bitwise OR operation on two operands.
- **Example**:
  ```javascript
  let result = 5 | 1;  // 5 (0101 | 0001 = 0101)
  ```

**4.3 Bitwise XOR (`^`)**
- **Usage**: Performs a bitwise XOR operation on two operands.
- **Example**:
  ```javascript
  let result = 5 ^ 1;  // 4 (0101 ^ 0001 = 0100)
  ```

**4.4 Bitwise NOT (`~`)**
- **Usage**: Inverts the bits of its operand.
- **Example**:
  ```javascript
  let result = ~5;  // -6 (~00000000000000000000000000000101 = 11111111111111111111111111111010)
  ```

**4.5 Bitwise Left Shift (`<<`)**
- **Usage**: Shifts the bits of its operand to the left by the specified number of places.
- **Example**:
  ```javascript
  let result = 5 << 1;  // 10 (0101 << 1 = 1010)
  ```

**4.6 Bitwise Right Shift (`>>`)**
- **Usage**: Shifts the bits of its operand to the right by the specified number of places.
- **Example**:
  ```javascript
  let result = 5 >> 1;  // 2 (0101 >> 1 = 0010)
  ```

**4.7 Zero-fill Right Shift (`>>>`)**
- **Usage**: Shifts the bits of its operand to the right by the specified number of places, filling the leftmost bits with zeros.
- **Example**:
  ```javascript
  let result = 5 >>> 1;  // 2 (0101 >>> 1 = 0010)
  ```

### **5. Unary Operators**
Unary operators are operators that take a single operand/argument and perform operations on it.

**5.1 Unary Plus (`+`)**
- **Usage**: Converts its operand to a number.
- **Example**:
  ```javascript
  let num = +"5";  // 5
  ```

**5.2 Unary Negation (`-`)**
- **Usage**: Negates its operand.
- **Example**:
  ```javascript
  let num = -5;  // -5
  ```

**5.3 Logical NOT (`!`)**
- **Usage**: Inverts the boolean value of its operand.
- **Example**:
  ```javascript
  let isTrue = !false;  // true
  ```

**5.4 Increment (`++`)**
- **Usage**: Increases an integer value by one.
- **Example**:
  ```javascript
  let x = 5;
  x++;  // x is now 6
  ```

**5.5 Decrement (`--`)**
- **Usage**: Decreases an integer value by one.
- **Example**:
  ```javascript
  let y = 5;
  y--;  // y is now 4
  ```

