# Ordered Sets and Maps in JavaScript

### Introduction to Ordered Sets

An **Ordered Set** is a data structure that maintains a collection of unique elements while preserving the order of their insertion. JavaScript's native `Set` ensures that all elements are unique, but it does not guarantee that elements will be retrieved in their precise insertion order, particularly if some elements are removed. To implement an Ordered Set that maintains both uniqueness and insertion order, we can combine the functionalities of a `Set` and a `Map`.

### Implementing an Ordered Set

Below is the implementation of a custom `OrderedSet` class using JavaScript's `Set` and `Map` objects.

```javascript
class OrderedSet {
  constructor() {
    this.set = new Set();
    this.map = new Map();
  }
```

#### Constructor Explanation:

- **`this.set = new Set()`**:
  - The `Set` object in JavaScript:
    - Stores unique values of any type.
    - Automatically handles duplicates by only storing one instance of each value.
  - In this implementation, `this.set` is used to quickly check if a value already exists in the Ordered Set.

- **`this.map = new Map()`**:
  - The `Map` object in JavaScript:
    - Stores key-value pairs.
    - Can use any value as a key and retains the original insertion order of keys.
  - Here, `this.map` is used to maintain the order of elements and associate each element with an index representing its insertion order.

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

#### `add(value)` Method Explanation:

- **Check for Existence**:
  - **`if (!this.set.has(value))`**:
    - Checks if the value already exists in the `Set`. If not, the following steps are executed.

- **Add to Set**:
  - **`this.set.add(value)`**:
    - Adds the value to the `Set`. Since `Set` automatically prevents duplicates, this ensures uniqueness.

- **Maintain Order in Map**:
  - **`this.map.set(value, this.map.size)`**:
    - Adds the value to the `Map` with the current size of the `Map` as its index. This preserves the insertion order.

- **Enable Method Chaining**:
  - **`return this;`**:
    - Returns the current instance, allowing for method chaining, e.g., `orderedSet.add(1).add(2)`.

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

#### `delete(value)` Method Explanation:

- **Check for Existence**:
  - **`if (this.set.has(value))`**:
    - Ensures that the value exists in the `Set` before attempting to delete it.

- **Remove from Set**:
  - **`this.set.delete(value)`**:
    - Removes the value from the `Set`.

- **Remove from Map**:
  - **`this.map.delete(value)`**:
    - Removes the value from the `Map`, which may disrupt the ordering of subsequent elements.

- **Reorder the Map**:
  - **`this._reorderMap()`**:
    - Reassigns indices in the `Map` to maintain sequential order after an element is deleted.

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

#### `_reorderMap()` Method Explanation:

- **Create a New Map**:
  - **`const newMap = new Map();`**:
    - Initializes a new `Map` to hold the reordered elements.

- **Initialize Index Counter**:
  - **`let index = 0;`**:
    - Sets up an index counter starting at 0.

- **Iterate Over Current Map**:
  - **`for (const key of this.map.keys())`**:
    - Iterates over the keys of the current `Map` in their original order.

- **Reassign Indices**:
  - **`newMap.set(key, index++);`**:
    - Adds each key to the new `Map` with a new sequential index.

- **Replace the Old Map**:
  - **`this.map = newMap;`**:
    - Replaces the old `Map` with the new reordered one.

### Checking for the Existence of a Value

```javascript
  has(value) {
    return this.set.has(value);
  }
```

#### `has(value)` Method Explanation:

- **Check for Value**:
  - **`return this.set.has(value);`**:
    - Checks if the value exists in the `Set` and returns `true` or `false`.

### Getting the Size of the Ordered Set

```javascript
  get size() {
    return this.set.size;
  }
```

#### `size` Getter Explanation:

- **Return Size**:
  - **`return this.set.size;`**:
    - Returns the number of unique elements in the `Set`, which corresponds to the number of elements in the Ordered Set.

### Clearing the Ordered Set

```javascript
  clear() {
    this.set.clear();
    this.map.clear();
  }
```

#### `clear()` Method Explanation:

- **Clear the Set**:
  - **`this.set.clear();`**:
    - Removes all elements from the `Set`.

- **Clear the Map**:
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

#### `values()` Generator Method Explanation:

- **Iterate Over Keys**:
  - **`for (const key of this.map.keys())`**:
    - Iterates over the keys of the `Map`, which represent the values of the Ordered Set.

- **Yield Each Key**:
  - **`yield key;`**:
    - Returns each value one at a time using the `yield` keyword. This makes the `values()` method a generator that produces values in insertion order.

#### `[Symbol.iterator]()` Method Explanation:

- **Enable Iteration**:
  - **`return this.values();`**:
    - Allows the Ordered Set to be iterable. This makes it possible to use `for...of` loops to iterate over the elements in order.

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

#### Example Breakdown:

- **Create an Ordered Set**:
  - `const orderedSet = new OrderedSet();` initializes a new instance of `OrderedSet`.

- **Add Elements**:
  - `orderedSet.add(1).add(2).add(3);` adds the values `1`, `2`, and `3` to the Ordered Set in sequence. Method chaining is enabled by the return statement in `add()`.

- **Print the Ordered Set**:
  - `console.log([...orderedSet]);` uses the spread operator to convert the Ordered Set into an array, resulting in `[1, 2, 3]`.

- **Delete an Element**:
  - `orderedSet.delete(2);` removes the value `2` from the Ordered Set.

- **Print After Deletion**:
  - `console.log([...orderedSet]);` now outputs `[1, 3]` because the value `2` has been removed.

- **Re-add an Element**:
  - `orderedSet.add(2);` re-adds `2`, placing it at the end due to the insertion order.

- **Final Print**:
  - `console.log([...orderedSet]);` outputs `[1, 3, 2]`, showing the final state of the Ordered Set.

- **Check the Size**:
  - `console.log(orderedSet.size);` outputs `3`, indicating the number of unique elements in the Ordered Set.

### Summary

This implementation of an Ordered Set in JavaScript maintains both the uniqueness and insertion order of elements, addressing the limitation of JavaScript's native `Set`. By combining the `Set` for uniqueness and the `Map` for order, the Ordered Set behaves as expected even when elements are added or removed.
