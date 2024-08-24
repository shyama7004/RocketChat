# **JavaScript Functions**

#### **1. What is a Function?**
- A **function** is a reusable block of code designed to perform a particular task.
- It can be defined once and then executed (called) multiple times.

**Syntax:**
```javascript
function functionName(parameters) {
    // code to be executed
}
```
- **`functionName`**: The name of the function.
- **`parameters`**: Values you pass to the function. These are optional.
- **Function body**: The code inside the curly braces `{}` that defines what the function does.

**Example:**
```javascript
function greet(name) {
    console.log("Hello, " + name + "!");
}

greet("Alice"); // Outputs: Hello, Alice!
```

#### **2. Calling a Function**
- To execute the function, you "call" it by using its name followed by parentheses `()`.
- If the function has parameters, you provide values (arguments) inside the parentheses.

**Example:**
```javascript
greet("Bob"); // Outputs: Hello, Bob!
```

#### **3. Return Values**
- Functions can return a value using the `return` statement.
- The returned value can be stored in a variable or used directly.

**Example:**
```javascript
function add(a, b) {
    return a + b;
}

let sum = add(3, 4); // sum is 7
console.log(sum); // Outputs: 7
```

**Explanation:**
- The `add` function takes two numbers `a` and `b`, adds them, and returns the result.
- We store the result in the variable `sum` and then log it to the console.

#### **4. Function Parameters**
- Functions can take multiple parameters, which are separated by commas.

**Example:**
```javascript
function multiply(x, y) {
    return x * y;
}

console.log(multiply(2, 3)); // Outputs: 6
```

**Explanation:**
- The `multiply` function multiplies the two parameters `x` and `y` and returns the result.

#### **5. Default Parameters**
- You can assign default values to parameters. If no argument is provided, the default value is used.

**Example:**
```javascript
function greet(name = "Guest") {
    console.log("Hello, " + name + "!");
}

greet(); // Outputs: Hello, Guest!
```

**Explanation:**
- Here, if no argument is provided to the `greet` function, it defaults to `"Guest"`.

#### **6. Anonymous Functions**
- Functions can be defined without a name. These are called **anonymous functions** and are often used as arguments to other functions or assigned to variables.

**Example:**
```javascript
let square = function(number) {
    return number * number;
};

console.log(square(5)); // Outputs: 25
```

**Explanation:**
- The function that calculates the square of a number is assigned to the variable `square`.

#### **7. Arrow Functions (ES6)**
- A shorter syntax for writing functions introduced in ES6 (ECMAScript 2015).
- Arrow functions are always anonymous.

**Syntax:**
```javascript
let functionName = (parameters) => {
    // code to be executed
};
```

**Example:**
```javascript
let sum = (a, b) => a + b;

console.log(sum(10, 5)); // Outputs: 15
```

**Explanation:**
- The `sum` function is defined using arrow function syntax and directly returns the sum of `a` and `b`.

#### **8. Function Expressions**
- Functions can be defined as part of a larger expression, often by assigning them to variables.

**Example:**
```javascript
let greet = function(name) {
    console.log("Hello, " + name);
};

greet("Charlie"); // Outputs: Hello, Charlie
```

**Explanation:**
- Here, a function is assigned to the variable `greet` and can be called using that variable.

#### **9. Immediately Invoked Function Expressions (IIFE)**
- A function that runs as soon as it is defined.
- Often used to create a local scope to avoid polluting the global scope.

**Example:**
```javascript
(function() {
    console.log("This function runs immediately!");
})();
```

**Explanation:**
- The function is defined and immediately called. This is useful for initialization code.

#### **10. Higher-Order Functions**
- Functions that can take other functions as arguments or return them.

**Example:**
```javascript
function greetSomeone(greetFunction, name) {
    greetFunction(name);
}

greetSomeone(function(name) {
    console.log("Hi, " + name);
}, "Dave"); // Outputs: Hi, Dave
```

**Explanation:**
- `greetSomeone` takes a function and a name as arguments, then calls the function with the provided name.

#### **11. Closures**
- A closure is a function that retains access to its lexical scope, even when the function is executed outside that scope.

**Example:**
```javascript
function outerFunction(outerVariable) {
    return function innerFunction(innerVariable) {
        console.log("Outer: " + outerVariable);
        console.log("Inner: " + innerVariable);
    };
}

let newFunction = outerFunction("outside");
newFunction("inside");
// Outputs:
// Outer: outside
// Inner: inside
```

**Explanation:**
- `outerFunction` returns `innerFunction`, which can still access `outerVariable` even after `outerFunction` has completed.

#### **12. Function Scope**
- Variables declared inside a function are local to that function and cannot be accessed outside of it.

**Example:**
```javascript
function showNumber() {
    let number = 10;
    console.log(number);
}

showNumber(); // Outputs: 10
// console.log(number); // Error: number is not defined
```

**Explanation:**
- The variable `number` is only accessible within `showNumber`.

#### **13. Recursion**
- A function that calls itself to solve a problem in smaller chunks.

**Example:**
```javascript
function factorial(n) {
    if (n === 0) {
        return 1;
    } else {
        return n * factorial(n - 1);
    }
}

console.log(factorial(5)); // Outputs: 120
```

**Explanation:**
- The `factorial` function calls itself with a decremented value of `n` until `n` equals `0`, at which point it returns `1`.

#### **14. Function Hoisting**
- Functions declared using the `function` keyword are hoisted to the top of their scope, so they can be called before they are defined in the code.

**Example:**
```javascript
sayHello();

function sayHello() {
    console.log("Hello, world!");
}
```

**Explanation:**
- The function `sayHello` is called before its declaration, but still works due to hoisting.

---

These notes cover the basics of JavaScript functions with code examples and explanations. They should provide a solid foundation for beginners to understand how functions work in JavaScript.
