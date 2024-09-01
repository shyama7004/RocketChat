# Template Literals

### 1. **Introduction to Template Literals**
   - **Definition**: Template literals are string literals enclosed by backticks (\`), introduced in ES6 (ECMAScript 2015). They are more powerful than traditional strings, allowing features like multi-line strings, embedded expressions, and tagged templates.
   - **Basic Syntax**:
     ```javascript
     `string text`
     `string text line 1
      string text line 2`
     `string text ${expression} string text`
     tagFunction`string text ${expression} string text`
     ```
   - **Explanation**:
     - **Backticks** (`) are used instead of single or double quotes for defining strings.
     - **Multi-line Strings**: Template literals preserve line breaks and indentation as written.
     - **Embedded Expressions**: Expressions can be embedded using `${expression}`, where the expression is evaluated and included in the string.

### 2. **Multi-line Strings**
   - **Traditional Approach**:
     ```javascript
     console.log("string text line 1\n" + "string text line 2");
     // Output:
     // string text line 1
     // string text line 2
     ```
   - **Using Template Literals**:
     ```javascript
     console.log(`string text line 1
     string text line 2`);
     // Output:
     // string text line 1
     // string text line 2
     ```
   - **Explanation**:
     - With template literals, multi-line strings are written directly without the need for newline characters (`\n`). The line breaks in the code are reflected in the output.

### 3. **String Interpolation**
   - **Traditional Approach**:
     ```javascript
     const a = 5;
     const b = 10;
     console.log("Fifteen is " + (a + b) + " and not " + (2 * a + b) + ".");
     // Output:
     // Fifteen is 15 and not 20.
     ```
   - **Using Template Literals**:
     ```javascript
     const a = 5;
     const b = 10;
     console.log(`Fifteen is ${a + b} and not ${2 * a + b}.`);
     // Output:
     // Fifteen is 15 and not 20.
     ```
   - **Explanation**:
     - **String Interpolation**: Instead of concatenating strings and variables using the `+` operator, template literals allow embedding expressions directly within the string using `${expression}`. The expression is evaluated, converted to a string, and included in the final output.
     - **Readability**: This approach improves code readability by reducing clutter from operators and parentheses.

### 4. **Nesting Templates**
   - **Concept**: Template literals can be nested within each other, which is especially useful when dealing with complex string constructions or conditional logic.
   - **Example Without Nesting**:
     ```javascript
     const classes = `header ${
       isLargeScreen() ? "" : item.isCollapsed ? "icon-expander" : "icon-collapser"
     }`;
     ```
   - **Example With Nesting**:
     ```javascript
     const classes = `header ${
       isLargeScreen() ? "" : `icon-${item.isCollapsed ? "expander" : "collapser"}`
     }`;
     ```
   - **Explanation**:
     - **Nesting Template Literals**: Inner template literals can be included within expressions in an outer template literal, which is useful for complex logic that impacts string construction.

### 5. **Tagged Templates**
   - **Definition**: A more advanced feature of template literals that allows a function to process the template literal before it is converted into a string.
   - **Basic Example**:
     ```javascript
     const person = "Mike";
     const age = 28;

     function myTag(strings, personExp, ageExp) {
       const str0 = strings[0]; // "That "
       const str1 = strings[1]; // " is a "
       const str2 = strings[2]; // "."

       const ageStr = ageExp < 100 ? "youngster" : "centenarian";

       return `${str0}${personExp}${str1}${ageStr}${str2}`;
     }

     const output = myTag`That ${person} is a ${age}.`;

     console.log(output);
     // Output: That Mike is a youngster.
     ```
   - **Explanation**:
     - **Tag Function**: The function `myTag` processes the template literal. It receives an array of strings (`strings`) and the evaluated expressions (`personExp`, `ageExp`) as arguments.
     - **Custom Processing**: The tag function can manipulate the strings and expressions in any way, returning a custom result. In this example, it checks the age and returns a different string based on the condition.

### 6. **Tagging with Any Expression**
   - **Concept**: The tag function doesn't have to be a simple identifier; it can be any expression that resolves to a function.
   - **Example**:
     ```javascript
     function recursive(strings, ...values) {
       console.log(strings, values);
       return recursive;
     }
     recursive`Hello``World`;
     // Output:
     // ['Hello'] []
     // ['World'] []
     ```
   - **Explanation**:
     - **Chained Tagged Templates**: The function `recursive` is called twice, once with `Hello` and once with `World`. The first argument (`strings`) contains the literal parts, and `values` contains the evaluated expressions. The function can return itself or any other function, enabling complex chaining of tagged templates.

### 7. **Raw Strings**
   - **Concept**: The `String.raw` method allows you to access the raw strings (i.e., the exact text inside the template literal, including escape sequences).
   - **Example**:
     ```javascript
     const str = String.raw`Hi\n${2 + 3}!`;
     console.log(str); 
     // Output:
     // Hi\n5!
     ```
   - **Explanation**:
     - **Raw Access**: Normally, escape sequences like `\n` (newline) are processed and translated into their corresponding characters. `String.raw` prevents this processing, preserving the raw text as-is.
     - **Utility**: This is particularly useful in scenarios where the exact input, including escape sequences, is needed (e.g., when embedding LaTeX in JavaScript).

### 8. **Tagged Templates with Escape Sequences**
   - **Handling Escape Sequences**:
     - **Tagged templates** allow handling strings with escape sequences differently than normal strings. While normal template literals enforce certain rules for escape sequences, tagged templates provide access to the raw, unprocessed strings, making it possible to work with non-standard escape sequences.
     - **Example**:
       ```javascript
       function tag(strings) {
         console.log(strings.raw[0]);
       }
       tag`string text line 1 \n string text line 2`;
       // Output:
       // Logs "string text line 1 \n string text line 2"
       ```
     - **Explanation**:
       - The `strings.raw` property provides the raw string with escape sequences preserved as-is. This is useful in cases where you need to work with the literal text, including special characters.

### 9. **Specifications and Browser Compatibility**
   - **Specification**: Template literals are defined in the ECMAScript Language Specification (ECMAScript 2015).
   - **Browser Support**: Template literals are widely supported across all modern browsers, including Chrome, Firefox, Safari, and Edge. They are also supported in Node.js and other JavaScript environments.

### 10. **Practical Use Cases**
   - **HTML Templating**:
     ```javascript
     const name = "World";
     const html = `<div>
                     <h1>Hello, ${name}!</h1>
                   </div>`;
     console.log(html);
     // Output:
     // <div>
     //   <h1>Hello, World!</h1>
     // </div>
     ```
   - **SQL Queries**:
     ```javascript
     const tableName = "users";
     const query = `SELECT * FROM ${tableName} WHERE age > ${age}`;
     console.log(query);
     // Output: SELECT * FROM users WHERE age > 25
     ```
   - **Logging and Debugging**:
     ```javascript
     const value = 42;
     console.log(`The value is ${value}`);
     // Output: The value is 42
     ```

### 11. **Advanced Example: Dynamic Function Calls**
   - **Dynamic Function Example**:
     ```javascript
     const callHistory = [];

     function tag(strings, ...values) {
       callHistory.push(strings);
       return {};
     }

     function evaluateLiteral() {
       return tag`Hello, ${"world"}!`;
     }

     console.log(evaluateLiteral() === evaluateLiteral()); // false
     console.log(callHistory[0] === callHistory[1]); // true
     ```
   - **Explanation**:
     - **Evaluating the Template Literal**: Every time the `tag` function is called, it returns a new object. However, the same `strings` array (from the template literal) is used every time, demonstrating that the literal parts are consistent across evaluations.

---
