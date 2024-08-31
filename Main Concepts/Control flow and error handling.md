# Control flow and error handling

### 1. **Introduction to Control Flow**
Control flow refers to the order in which individual statements, instructions, or function calls are executed or evaluated in a programming language. In JavaScript, control flow is handled using several structures, including conditionals, loops, and error handling mechanisms.

### 2. **Conditional Statements**

#### **a. `if...else` Statement**
The `if...else` statement executes a block of code based on a specified condition. If the condition evaluates to `true`, the block of code within the `if` statement is executed; otherwise, the block within the `else` statement is executed.

**Syntax**:
```javascript
if (condition) {
  // code to run if condition is true
} else {
  // code to run if condition is false
}
```

**Example**:
```javascript
let age = 18;

if (age >= 18) {
  console.log("You are eligible to vote.");
} else {
  console.log("You are not eligible to vote.");
}
```

**Explanation**:
- The variable `age` is checked. If `age` is 18 or more, the message "You are eligible to vote." is logged. Otherwise, the alternate message is logged.

#### **b. `else if` Statement**
When multiple conditions need to be evaluated, `else if` is used after an `if` statement.

**Syntax**:
```javascript
if (condition1) {
  // code to run if condition1 is true
} else if (condition2) {
  // code to run if condition2 is true
} else {
  // code to run if all conditions are false
}
```

**Example**:
```javascript
let score = 85;

if (score >= 90) {
  console.log("Grade A");
} else if (score >= 80) {
  console.log("Grade B");
} else if (score >= 70) {
  console.log("Grade C");
} else {
  console.log("Grade F");
}
```

**Explanation**:
- The code checks the score and assigns a grade based on the range the score falls into. The first condition to be true will determine the output.

### 3. **Switch Statement**
The `switch` statement is used to perform different actions based on different conditions. It is often used when the same variable or expression is compared against multiple values.

**Syntax**:
```javascript
switch(expression) {
  case value1:
    // code to run if expression === value1
    break;
  case value2:
    // code to run if expression === value2
    break;
  default:
    // code to run if no cases match
}
```

**Example**:
```javascript
let fruit = 'apple';

switch(fruit) {
  case 'banana':
    console.log("Banana is yellow.");
    break;
  case 'apple':
    console.log("Apple is red.");
    break;
  case 'orange':
    console.log("Orange is orange.");
    break;
  default:
    console.log("Unknown fruit.");
}
```

**Explanation**:
- The `switch` statement compares the value of `fruit` with each case. When a match is found, the corresponding block of code is executed. The `break` statement prevents the code from running into the next case.

### 4. **Loops in JavaScript**

Loops are used to repeatedly execute a block of code as long as a specified condition is true.

#### **a. `for` Loop**
The `for` loop is commonly used to execute a block of code a specific number of times.

**Syntax**:
```javascript
for (initialization; condition; increment) {
  // code to be executed
}
```

**Example**:
```javascript
for (let i = 0; i < 5; i++) {
  console.log("Iteration number " + i);
}
```

**Explanation**:
- The loop starts with `i = 0`, runs as long as `i` is less than 5, and increments `i` by 1 after each iteration. The current value of `i` is logged in each iteration.

#### **b. `while` Loop**
The `while` loop repeats as long as a specified condition is true.

**Syntax**:
```javascript
while (condition) {
  // code to be executed
}
```

**Example**:
```javascript
let i = 0;

while (i < 5) {
  console.log("Iteration number " + i);
  i++;
}
```

**Explanation**:
- The loop checks if `i` is less than 5, logs the iteration number, and increments `i`. The loop continues until `i` is no longer less than 5.

#### **c. `do...while` Loop**
The `do...while` loop is similar to the `while` loop, but it guarantees that the code block is executed at least once.

**Syntax**:
```javascript
do {
  // code to be executed
} while (condition);
```

**Example**:
```javascript
let i = 0;

do {
  console.log("Iteration number " + i);
  i++;
} while (i < 5);
```

**Explanation**:
- The code block runs first and then checks the condition. If `i` is still less than 5, the loop continues.

### 5. **Error Handling**

Error handling in JavaScript is essential for dealing with exceptions that can occur during code execution. It ensures that the program doesn't crash and provides ways to manage errors gracefully.

#### **a. `try...catch` Statement**
The `try...catch` statement allows you to define a block of code to be tested (try) for errors, while another block of code can handle the error (catch).

**Syntax**:
```javascript
try {
  // code to try
} catch (error) {
  // code to handle error
}
```

**Example**:
```javascript
try {
  let result = undefinedVariable + 10;
} catch (error) {
  console.log("An error occurred: " + error.message);
}
```

**Explanation**:
- The code inside the `try` block attempts to execute, but since `undefinedVariable` is not defined, an error occurs. The `catch` block catches this error and logs an error message.

#### **b. `finally` Clause**
The `finally` clause can be added to a `try...catch` statement to execute code after the try and catch blocks, regardless of whether an error occurred.

**Syntax**:
```javascript
try {
  // code to try
} catch (error) {
  // code to handle error
} finally {
  // code to execute after try and catch
}
```

**Example**:
```javascript
try {
  let result = 10 / 0;
} catch (error) {
  console.log("An error occurred: " + error.message);
} finally {
  console.log("This code runs no matter what.");
}
```

**Explanation**:
- The `finally` block executes after the `try` and `catch` blocks, regardless of whether an error was caught or not.

#### **c. Throwing Errors Manually**
You can manually throw an error using the `throw` statement, often used when a certain condition occurs that you want to handle as an error.

**Syntax**:
```javascript
throw new Error("Error message");
```

**Example**:
```javascript
let age = 15;

if (age < 18) {
  throw new Error("You must be at least 18 years old.");
}
```
<details>
<summary>Click to get the full Code</summary>

```cpp
// Function that attempts to add a number to a variable
function addNumbers(variable, numberToAdd) {
  try {
    // Attempt to perform the addition
    let result = variable + numberToAdd;
    console.log("The result is: " + result);
  } catch (error) {
    // Catch any errors that occur and log them
    console.log("An error occurred: " + error.message);
  } finally {
    // Optional: Finally block that always runs, regardless of the outcome
    console.log("The addNumbers function has completed.");
  }
}

// Test cases

// Case 1: Undefined variable (will throw an error)
let undefinedVariable;
addNumbers(undefinedVariable, 10);

// Case 2: Variable is not a number (will throw an error)
let stringVariable = "hello";
addNumbers(stringVariable, 10);

// Case 3: Both variables are numbers (no error)
let numberVariable = 20;
addNumbers(numberVariable, 10);

```
</details>

**Explanation**:
- If the `age` is less than 18, an error is thrown with a custom message. This stops further execution of the code unless handled in a `try...catch` block.

### 6. **Best Practices in Control Flow and Error Handling**
- Always validate user input to avoid unexpected errors.
- Use `try...catch` blocks for code that may fail, such as working with external resources or parsing user input.
- Handle specific exceptions separately if different actions are required.
- Avoid deep nesting of control flow structures to keep your code readable and maintainable.
- Use descriptive error messages to make debugging easier.
