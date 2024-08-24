# Array

### Creating an Ordered Set in JavaScript

An **Ordered Set** is a data structure that maintains a collection of unique elements in the order in which they were added. JavaScript's native `Set` object ensures uniqueness, but it does not provide a method to retrieve elements in the precise order of insertion if elements are removed. To implement an Ordered Set that maintains both uniqueness and order, we can use a combination of a `Set` and a `Map`.

Here's a detailed breakdown of the code:

```javascript
class OrderedSet {
  constructor() {
    this.set = new Set();
    this.map = new Map();
  }
```

#### Constructor:
- **`this.set = new Set()`**:
  - The `Set` object in JavaScript stores unique values of any type. It automatically handles duplicates by only storing one instance of each value.
  - In this implementation, `this.set` is used to quickly check if a value already exists in the Ordered Set.

- **`this.map = new Map()`**:
  - The `Map` object in JavaScript stores key-value pairs. Unlike plain objects, Maps can use any value as a key and remember the original insertion order of the keys.
  - Here, `this.map` is used to maintain the order of elements and associate each element with an index, which is its insertion order.

### Adding Elements to the Ordered Set

```javascript
  add(value) {
    if (!this.set.has(value)) {
      this.set.add(value);
      this.map.set(value, this.map.size); // Maintain order by mapping value to its index
    }
    return this; // Enable chaining
  }
```

#### `add(value)` Method:
- **`if (!this.set.has(value))`**:
  - `this.set.has(value)` checks if the value already exists in the `Set`. The exclamation mark `!` negates the result, so the code inside the `if` block only runs if the value does not already exist in the `Set`.

- **`this.set.add(value)`**:
  - This adds the value to the `Set`. If the value already exists, it won't be added again due to the nature of `Set`.

- **`this.map.set(value, this.map.size)`**:
  - This adds the value to the `Map`, using the value itself as the key and the current size of the `Map` (which reflects the number of elements added so far) as the value.
  - This step ensures that the order of insertion is preserved.

- **`return this;`**:
  - Returning `this` allows for method chaining, meaning you can add multiple elements in a single line, like `orderedSet.add(1).add(2)`.

### Deleting Elements from the Ordered Set

```javascript
  delete(value) {
    if (this.set.has(value)) {
      this.set.delete(value);
      this.map.delete(value);
      this._reorderMap(); // Reorder the map to maintain index consistency
    }
    return this;
  }
```

#### `delete(value)` Method:
- **`if (this.set.has(value))`**:
  - Checks if the value exists in the `Set`.

- **`this.set.delete(value)`**:
  - Removes the value from the `Set`.

- **`this.map.delete(value)`**:
  - Removes the value from the `Map`, which disrupts the ordering of subsequent elements' indices.

- **`this._reorderMap()`**:
  - After deleting a value, the indices in the `Map` might become inconsistent (e.g., skipping a number). `_reorderMap()` reassigns indices to ensure they remain sequential and consistent.

### Reordering the Map

```javascript
  _reorderMap() {
    const newMap = new Map();
    let index = 0;
    for (const key of this.map.keys()) {
      newMap.set(key, index++);
    }
    this.map = newMap;
  }
```

#### `_reorderMap()` Method:
- **`const newMap = new Map();`**:
  - Creates a new `Map` to hold the reordered elements.

- **`let index = 0;`**:
  - Initializes an index counter to start from 0.

- **`for (const key of this.map.keys())`**:
  - Iterates over the current keys of the `Map` in their original order.

- **`newMap.set(key, index++);`**:
  - Adds each key to `newMap` with a new, sequential index. The `++` operator increments the index after assigning it.

- **`this.map = newMap;`**:
  - Replaces the old `Map` with the new, reordered one.

### Checking for the Existence of a Value

```javascript
  has(value) {
    return this.set.has(value);
  }
```

#### `has(value)` Method:
- **`return this.set.has(value);`**:
  - Simply checks if the value exists in the `Set` and returns `true` or `false`.

### Getting the Size of the Ordered Set

```javascript
  get size() {
    return this.set.size;
  }
```

#### `size` Getter:
- **`return this.set.size;`**:
  - Returns the number of unique elements in the `Set`, which is the same as the number of elements in the Ordered Set.

### Clearing the Ordered Set

```javascript
  clear() {
    this.set.clear();
    this.map.clear();
  }
```

#### `clear()` Method:
- **`this.set.clear();`**:
  - Removes all elements from the `Set`.

- **`this.map.clear();`**:
  - Removes all elements from the `Map`, effectively emptying the Ordered Set.

### Iterating Over the Ordered Set

```javascript
  *values() {
    for (const key of this.map.keys()) {
      yield key;
    }
  }

  [Symbol.iterator]() {
    return this.values();
  }
```

#### `values()` Generator Method:
- **`for (const key of this.map.keys())`**:
  - Iterates over the keys of the `Map`, which are the values of the Ordered Set.

- **`yield key;`**:
  - The `yield` keyword is used in generator functions to return each value one at a time. This makes the `values()` method a generator that produces values in the order of their insertion.

#### `[Symbol.iterator]()` Method:
- **`return this.values();`**:
  - This method allows the Ordered Set to be iterable, meaning you can use it in loops like `for...of` to get the elements in order.

### Example Usage

```javascript
const orderedSet = new OrderedSet();

orderedSet.add(1).add(2).add(3);
console.log([...orderedSet]); // Output: [1, 2, 3]

orderedSet.delete(2);
console.log([...orderedSet]); // Output: [1, 3]

orderedSet.add(2);
console.log([...orderedSet]); // Output: [1, 3, 2]

console.log(orderedSet.size); // Output: 3
```

#### Explanation of the Example:

1. **Creating the Ordered Set**:
   - `const orderedSet = new OrderedSet();` initializes a new Ordered Set.

2. **Adding Elements**:
   - `orderedSet.add(1).add(2).add(3);` adds the values `1`, `2`, and `3` to the Ordered Set in sequence. The method chaining works because `add()` returns `this`.

3. **Printing the Ordered Set**:
   - `console.log([...orderedSet]);` uses the spread operator `...` to convert the Ordered Set into an array, which is then logged. The output is `[1, 2, 3]`.

4. **Deleting an Element**:
   - `orderedSet.delete(2);` removes the value `2` from the Ordered Set.

5. **Printing After Deletion**:
   - `console.log([...orderedSet]);` now outputs `[1, 3]` because `2` has been removed.

6. **Adding an Element Back**:
   - `orderedSet.add(2);` re-adds `2`, but now it appears at the end because elements are added in order.

7. **Final Print**:
   - `console.log([...orderedSet]);` outputs `[1, 3, 2]` showing the final state of the Ordered Set.

8. **Checking the Size**:
   - `console.log(orderedSet.size);` outputs `3`, the number of unique elements in the Ordered Set.

### Summary

This implementation of an Ordered Set in JavaScript maintains both the uniqueness and insertion order of elements, addressing a limitation of JavaScript's native `Set`. The combination of a `Set` for uniqueness and a `Map` for order ensures that your Ordered Set behaves as expected, even when elements are added or removed.
