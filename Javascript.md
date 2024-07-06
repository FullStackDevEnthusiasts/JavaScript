### 1. Features of ES6
- **Arrow Functions:** Provide a concise syntax for functions.
  ```javascript
  const add = (a, b) => a + b;
  ```
- **Let and Const Keywords:** Let is block-scoped, const is block-scoped and immutable.
  ```javascript
  let x = 1;
  const y = 2;
  ```
- **Template Literals:** Allow embedded expressions and multi-line strings using backticks.
  ```javascript
  const name = 'John';
  console.log(`Hello, ${name}!`);
  ```
- **Destructuring:** Extract values from arrays or objects into distinct variables.
  ```javascript
  const [a, b] = [1, 2];
  const { name, age } = { name: 'John', age: 30 };
  ```
- **Default Parameters:** Assign default values to function parameters.
  ```javascript
  function greet(name = 'Guest') {
    console.log(`Hello, ${name}`);
  }
  ```
- **Classes:** Syntactic sugar for prototype-based inheritance.
  ```javascript
  class Person {
    constructor(name) {
      this.name = name;
    }
    greet() {
      console.log(`Hello, ${this.name}`);
    }
  }
  ```

### 2. Import/Export Modules in ES6
- **Exporting Named Values:**
  ```javascript
  export const myValue = 42;
  export function myFunction() { ... }
  ```
- **Exporting Default Value:**
  ```javascript
  export default function() { ... }
  ```
- **Importing Named Values:**
  ```javascript
  import { myValue, myFunction } from './myModule.js';
  ```
- **Importing Default Value:**
  ```javascript
  import myFunction from './myModule.js';
  ```

### 3. Arrow Functions and Let/Const Keywords
- **Arrow Functions:** Provide a concise syntax, no `this` binding.
  ```javascript
  const add = (a, b) => a + b;
  ```
- **Let Keyword:** Block-scoped, can be reassigned.
  ```javascript
  let x = 10;
  if (true) {
    let x = 20;
    console.log(x); // 20
  }
  console.log(x); // 10
  ```
- **Const Keyword:** Block-scoped, immutable.
  ```javascript
  const y = 30;
  // y = 40; // Error: Assignment to constant variable.
  ```
- **Arrow Function Example:**
  ```javascript
  const numbers = [1, 2, 3];
  const squares = numbers.map(n => n * n);
  console.log(squares); // [1, 4, 9]
  ```

### 4. Web Storage: Session Storage vs. Local Storage
- **Session Storage:**
  - Data is stored for the duration of the page session.
  - Data is cleared when the page session ends.
  - Example: `sessionStorage.setItem('key', 'value');`
- **Local Storage:**
  - Data is stored persistently.
  - Data remains even after the browser is closed.
  - Example: `localStorage.setItem('key', 'value');`
- **Similarities:**
  - Both store key-value pairs.
  - Both can only store strings.
  - Data can be accessed via JavaScript.
- **Differences:**
  - **Scope:** Session storage is limited to the session; local storage persists across sessions.
  - **Capacity:** Typically, local storage has a larger capacity than session storage.
  - **Use Cases:** Session storage for temporary data; local storage for longer-term data.

### 5. Primitive vs. Non-Primitive Data Types in JavaScript
- **Primitive Data Types:**
  - Include `String`, `Number`, `Boolean`, `Null`, `Undefined`, `Symbol`, `BigInt`.
  - Stored directly in memory.
  - Immutable.
  - Example: 
    ```javascript
    let str = 'Hello';
    let num = 123;
    ```
- **Non-Primitive Data Types:**
  - Include `Object`, `Array`, `Function`.
  - Stored as a reference in memory.
  - Mutable.
  - Example:
    ```javascript
    let obj = { key: 'value' };
    let arr = [1, 2, 3];
    ```
- **Memory Allocation:**
  - **Primitives:** Stored directly on the stack.
  - **Objects/Arrays:** Stored in heap memory, with a reference stored on the stack.
  - Example:
    ```javascript
    let a = 10; // Primitive
    let b = { value: 10 }; // Non-Primitive
    ```

### 6. Closures in JavaScript and Lexical Scoping
- **Closures:**
  - A function that retains access to its lexical scope, even when the function is executed outside that scope.
  - Allows function to access variables from its enclosing scope.
  - Example:
    ```javascript
    function outer() {
      let count = 0;
      return function inner() {
        count++;
        console.log(count);
      };
    }
    const counter = outer();
    counter(); // 1
    counter(); // 2
    ```
- **Lexical Scoping:**
  - Scope is determined by the physical placement of the code.
  - Functions are executed using the variable scope that was in effect when they were defined.
  - Example:
    ```javascript
    function parent() {
      let x = 10;
      function child() {
        console.log(x);
      }
      child();
    }
    parent(); // 10
    ```
### 7. Types of Promises and Differences from Callbacks
- **Promises:**
  - Objects representing the eventual completion or failure of an asynchronous operation.
  - Provide cleaner, more readable code compared to callbacks.
  - Example:
    ```javascript
    const myPromise = new Promise((resolve, reject) => {
      setTimeout(() => resolve('Success!'), 1000);
    });
    myPromise.then(result => console.log(result));
    ```
- **Promise States:**
  - **Pending:** Initial state, neither fulfilled nor rejected.
  - **Fulfilled:** Operation completed successfully.
  - **Rejected:** Operation failed.
- **Types of Promises:**
  - **Resolved:** Successfully completed.
  - **Rejected:** Encountered an error.
- **Differences from Callbacks:**
  - **Chaining:** Promises can be chained to handle sequential asynchronous operations.
  - **Error Handling:** Easier to handle errors using `.catch()` method.

### 8. forEach vs. map Functions in JavaScript
- **forEach:**
  - Iterates over array elements.
  - Executes a provided function once for each array element.
  - Does not return a new array.
  - Example:
    ```javascript
    const arr = [1, 2, 3];
    arr.forEach(num => console.log(num));
    ```
- **map:**
  - Iterates over array elements.
  - Executes a provided function once for each array element.
  - Returns a new array with the results.
  - Example:
    ```javascript
    const arr = [1, 2, 3];
    const doubled = arr.map(num => num * 2);
    console.log(doubled); // [2, 4, 6]
    ```

### 9. Array.flat() vs. Array.flatMap()
- **Array.flat():**
  - Flattens a nested array up to a specified depth.
  - Default depth is 1.
  - Example:
    ```javascript
    const arr = [1, [2, [3, 4]]];
    console.log(arr.flat()); // [1, 2, [3, 4]]
    console.log(arr.flat(2)); // [1, 2, 3, 4]
    ```
- **Array.flatMap():**
  - Maps each element using a mapping function, then flattens the result.
  - Only flattens one level deep.
  - Example:
    ```javascript
    const arr = [1, 2, 3];
    console.log(arr.flatMap(num => [num, num * 2])); // [1, 2, 2, 4, 3, 6]
    ```

### 10. Null vs. Undefined in JavaScript
- **Null:**
  - Represents the intentional absence of any object value.
  - Type is an object.
  - Example:
    ```javascript
    let foo = null;
    ```
- **Undefined:**
  - Represents a variable that has been declared but not assigned a value.
  - Type is undefined.
  - Example:
    ```javascript
    let bar;
    console.log(bar); // undefined
    ```
- **Differences:**
  - **Usage:** Null is used to assign a non-value; undefined is the default for uninitialized variables.
  - **Type:** Null is an object; undefined is its own type.
  - **Equality:** `null == undefined` is true; `null === undefined` is false.

### 11. Variable Hoisting in JavaScript
- **Hoisting:**
  - JavaScript's default behavior of moving declarations to the top of the current scope.
  - Variables declared with `var` are hoisted to the top of their scope.
  - Example:
    ```javascript
    console.log(x); // undefined
    var x = 5;
    ```
- **let and const:**
  - Variables declared with `let` and `const` are hoisted but not initialized.
  - Accessing them before declaration results in a `ReferenceError`.
  - Example:
    ```javascript
    console.log(y); // ReferenceError
    let y = 10;
    ```
- **Function Hoisting:**
  - Function declarations are hoisted, allowing them to be called before their definition.
  - Example:
    ```javascript
    greet(); // "Hello"
    function greet() {
      console.log("Hello");
    }
    ```

### 12. setTimeout vs. setInterval in JavaScript
- **setTimeout:**
  - Executes a function once after a specified delay (milliseconds).
  - Example:
    ```javascript
    setTimeout(() => {
      console.log('Executed after 2 seconds');
    }, 2000);
    ```
- **setInterval:**
  - Executes a function repeatedly at specified intervals (milliseconds).
  - Example:
    ```javascript
    setInterval(() => {
      console.log('Executed every 2 seconds');
    }, 2000);
    ```
- **Differences:**
  - **Execution:** setTimeout runs once; setInterval runs repeatedly.
  - **Use Cases:** setTimeout for delayed actions; setInterval for repeated actions.
  - **Clearing:** clearTimeout() stops a setTimeout; clearInterval() stops a setInterval.
  - Example of Clearing:
    ```javascript
    const intervalId = setInterval(() => {
      console.log('Repeated action');
    }, 2000);
    setTimeout(() => {
      clearInterval(intervalId);
    }, 10000); // Stops the interval after 10 seconds
    ```

### 13. Shallow Copy vs. Deep Copy in JavaScript
- **Shallow Copy:**
  - Copies the top-level properties of an object.
  - Nested objects are referenced, not copied.
  - Example:
    ```javascript
    const original = { a: 1, b: { c: 2 } };
    const shallowCopy = { ...original };
    shallowCopy.b.c = 3;
    console.log(original.b.c); // 3
    ```
- **Deep Copy:**
  - Copies all properties, including nested objects.
  - Example:
    ```javascript
    const original = { a: 1, b: { c: 2 } };
    const deepCopy = JSON.parse(JSON.stringify(original));
    deepCopy.b.c = 3;
    console.log(original.b.c); // 2
    ```
- **Methods for Deep Copy:**
  - **JSON.parse(JSON.stringify(obj)):** Simple but not suitable for objects with methods or non-JSON data types.
  - **Lodash's _.cloneDeep():** Comprehensive deep copy utility.

### 14. Different Ways to Create Objects in JavaScript
- **Object Literals:**
  - Example:
    ```javascript
    const obj = { key: 'value' };
    ```
- **Constructor Functions:**
  - Example:
    ```javascript
    function Person(name) {
      this.name = name;
    }
    const person1 = new Person('John');
    ```
- **ES6 Classes:**
  - Example:
    ```javascript
    class Person {
      constructor(name) {
        this.name = name;
      }
    }
    const person1 = new Person('John');
    ```
- **Object.create():**
  - Example:
    ```javascript
    const proto = { greet() { console.log('Hello'); } };
    const obj = Object.create(proto);
    obj.greet(); // 'Hello'
    ```
- **Factory Functions:**
  - Example:
    ```javascript
    function createPerson(name) {
      return { name, greet() { console.log('Hello'); } };
    }
    const person1 = createPerson('John');
    person1.greet(); // 'Hello'
    ```

### 15. Callback Method in JavaScript
- **Definition:**
  - A function passed into another function as an argument.
  - Executes after the completion of an asynchronous operation.
- **Example:**
  ```javascript
  function fetchData(callback) {
    setTimeout(() => {
      callback('Data fetched');
    }, 1000);
  }
  fetchData(message => console.log(message));
  ```
- **Role in Asynchronous Operations:**
  - Handles operations like API calls, file reading, etc.
  - Example:
    ```javascript
    function fetchData(callback) {
      setTimeout(() => {
        const data = 'Fetched data';
        callback(data);
      }, 1000);
    }
    fetchData(data => console.log(data)); // 'Fetched data' after 1 second
    ```
- **Avoiding Callback Hell:**
  - Callback hell occurs with nested callbacks.
  - Solution: Use Promises or async/await for cleaner code.

### 16. Removing an Item from an Array at a Specific Index without Splice
- **Using Slice and Concat:**
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const indexToRemove = 2;
  const newArray = array.slice(0, indexToRemove).concat(array.slice(indexToRemove + 1));
  console.log(newArray); // [1, 2, 4, 5]
  ```
- **Using Filter:**
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const indexToRemove = 2;
  const newArray = array.filter((_, index) => index !== indexToRemove);
  console.log(newArray); // [1, 2, 4, 5]
  ```
- **Using Spread Operator:**
  ```javascript
  const array = [1, 2, 3, 4, 5];
  const indexToRemove = 2;
  const newArray = [...array.slice(0, indexToRemove), ...array.slice(indexToRemove + 1)];
  console.log(newArray); // [1, 2, 4, 5]
  ```
### 17. Concept of State in JavaScript
- **Definition:**
  - State refers to the data or condition of an application at a specific time.
  - Can be stored in variables and objects.
- **Using let:**
  - Allows re-assignment.
  - Suitable for variables that will change.
  - Example:
    ```javascript
    let count = 0;
    count++;
    console.log(count); // 1
    ```
- **Using const:**
  - Prevents re-assignment.
  - Suitable for constants or objects whose reference should not change.
  - Example:
    ```javascript
    const MAX_LIMIT = 100;
    const obj = { key: 'value' };
    obj.key = 'new value'; // Allowed
    // obj = { newKey: 'newValue' }; // Error: Assignment to constant variable
    ```
- **State Management in Applications:**
  - Managing state is crucial in applications, especially with frameworks like React.
  - State changes often trigger UI updates.

### 18. Event Loop in JavaScript
- **Definition:**
  - JavaScript's mechanism to handle asynchronous operations.
  - Continuously checks the call stack and event queue.
- **Call Stack:**
  - Holds functions to be executed.
  - Functions are added and removed in a LIFO manner.
- **Event Queue:**
  - Holds messages to be processed.
  - Functions are added here when async operations complete.
- **Role of Event Loop:**
  - Moves tasks from the event queue to the call stack.
  - Ensures non-blocking execution.
- **Example:**
  ```javascript
  console.log('Start');
  setTimeout(() => {
    console.log('Timeout');
  }, 0);
  console.log('End');
  // Output: Start, End, Timeout
  ```

### 19. Redirecting to a New Page in JavaScript
- **Within the Same Tab:**
  - Using `window.location.href`:
    ```javascript
    window.location.href = 'https://example.com';
    ```
  - Using `window.location.assign`:
    ```javascript
    window.location.assign('https://example.com');
    ```
- **Opening a Link in a New Tab:**
  - Using `window.open`:
    ```javascript
    window.open('https://example.com', '_blank');
    ```
  - Using an anchor tag with target attribute:
    ```html
    <a href="https://example.com" target="_blank">Open in new tab</a>
    ```

### 20. Difference Between Object.freeze and const in JavaScript
- **Object.freeze:**
  - Makes an object immutable.
  - Prevents adding, removing, or modifying properties.
  - Example:
    ```javascript
    const obj = { key: 'value' };
    Object.freeze(obj);
    obj.key = 'newValue'; // No effect
    console.log(obj.key); // 'value'
    ```
- **const Keyword:**
  - Prevents re-assignment of variables.
  - Does not make objects immutable.
  - Example:
    ```javascript
    const obj = { key: 'value' };
    obj.key = 'newValue'; // Allowed
    console.log(obj.key); // 'newValue'
    // obj = { newKey: 'newValue' }; // Error: Assignment to constant variable
    ```
- **Use Cases:**
  - Use `Object.freeze` to protect object integrity.
  - Use `const` to ensure variable references remain constant.

### 21. Use of Rest Parameters in JavaScript
- **Definition:**
  - Allows a function to accept an indefinite number of arguments as an array.
  - Syntax: `...parameter`
- **Example:**
  ```javascript
  function sum(...numbers) {
    return numbers.reduce((total, num) => total + num, 0);
  }
  console.log(sum(1, 2, 3, 4)); // 10
  ```
- **Use Cases:**
  - Handling functions with variable number of arguments.
  - Simplifies operations on arrays of arguments.
- **Comparison with Arguments Object:**
  - Rest parameters are true arrays, `arguments` is an array-like object.
  - Rest parameters provide cleaner and more readable syntax.

### 22. Handling Event Bubbling and Event Capturing in JavaScript
- **Event Bubbling:**
  - Event propagates from the target element up to the root.
  - Default behavior.
  - Example:
    ```javascript
    document.querySelector('button').addEventListener('click', () => {
      console.log('Button clicked');
    });
    ```
- **Event Capturing:**
  - Event propagates from the root down to the target element.
  - Enabled by setting `capture` to `true`.
  - Example:
    ```javascript
    document.querySelector('div').addEventListener('click', () => {
      console.log('Div clicked');
    }, true);
    ```
- **Stopping Propagation:**
  - **event.stopPropagation():** Stops the event from further propagation.
  - **event.stopImmediatePropagation():** Stops the event and prevents other listeners from being called.
  - Example:
    ```javascript
    button.addEventListener('click', (event) => {
      event.stopPropagation();
      console.log('Propagation stopped');
    });
    ```

### 23. Significance of the "Hoisting" Concept in JavaScript
- **Definition:**
  - JavaScript's default behavior of moving declarations to the top of the current scope.
  - Affects `var` declarations and function declarations.
- **Variable Hoisting:**
  - Variables declared with `var` are hoisted to the top of their scope.
  - Example:
    ```javascript
    console.log(hoistedVar); // undefined
    var hoistedVar = 'I am hoisted';
    ```
- **Function Hoisting:**
  - Function declarations are hoisted, allowing them to be called before their definition.
  - Example:
    ```javascript
    hoistedFunction(); // 'I am hoisted'
    function hoistedFunction() {
      console.log('I am hoisted');
    }
    ```
- **Limitations with `let` and `const`:**
  - Variables declared with `let` and `const` are hoisted but not initialized.
  - Accessing them before declaration results in a `ReferenceError`.
  - Example:
    ```javascript
    console.log(hoistedLet); // ReferenceError
    let hoistedLet = 'I am not hoisted';
    ```

### 24. Accessing a Variable Before Its Declaration Results in "Undefined" in JavaScript
- **Behavior with `var`:**
  - Variables declared with `var` are hoisted to the top but initialized with `undefined`.
  - Example:
    ```javascript
    console.log(foo); // undefined
    var foo = 'bar';
    ```
- **Temporal Dead Zone (TDZ) with `let` and `const`:**
  - Variables are in TDZ from the start of the block until their declaration is encountered.
  - Example:
    ```javascript
    console.log(bar); // ReferenceError
    let bar = 'baz';
    ```
- **Hoisting Mechanism:**
  - The declaration is moved to the top, but initialization remains in place.
  - Example:
    ```javascript
    var baz;
    console.log(baz); // undefined
    baz = 'qux';
    ```

### 25. Difference Between "var" and "let" Keywords in JavaScript
- **Scope:**
  - `var`: Function-scoped.
  - `let`: Block-scoped.
- **Hoisting:**
  - `var`: Hoisted and initialized with `undefined`.
  - `let`: Hoisted but not initialized, causing a ReferenceError if accessed before declaration.
- **Re-declaration:**
  - `var`: Allows re-declaration within the same scope.
  - `let`: Does not allow re-declaration within the same scope.
- **Example:**
  ```javascript
  // var example
  var x = 1;
  if (true) {
    var x = 2;
    console.log(x); // 2
  }
  console.log(x); // 2

  // let example
  let y = 1;
  if (true) {
    let y = 2;
    console.log(y); // 2
  }
  console.log(y); // 1
  ```

### 26. Concept of the "Temporal Dead Zone" in JavaScript
- **Definition:**
  - Period between entering the scope and the variable's declaration where the variable cannot be accessed.
  - Applies to variables declared with `let` and `const`.
- **Behavior:**
  - Accessing a variable in the TDZ results in a `ReferenceError`.
  - Example:
    ```javascript
    {
      console.log(a); // ReferenceError
      let a = 3;
    }
    ```
- **Purpose:**
  - Ensures variables are declared before being used.
  - Helps prevent bugs related to accessing uninitialized variables.
- **Example:**
  ```javascript
  {
    console.log(x); // ReferenceError
    let x = 5;
    console.log(x); // 5
  }
  ```

### 27. Difference Between an Arrow Function and a Normal Function in JavaScript
- **Syntax:**
  - Arrow function: `const func = () => { /* code */ };`
  - Normal function: `function func() { /* code */ }`
- **`this` Binding:**
  - Arrow function: Lexically binds `this` (inherits from the enclosing scope).
  - Normal function: Dynamically binds `this` based on how the function is called.
  - Example:
    ```javascript
    const obj = {
      arrowFunc: () => { console.log(this); }, // 'this' is inherited from the surrounding scope
      normalFunc() { console.log(this); } // 'this' is the calling object
    };
    obj.arrowFunc(); // Logs global object or undefined in strict mode
    obj.normalFunc(); // Logs obj
    ```
- **Arguments Object:**
  - Arrow function: Does not have its own `arguments` object.
  - Normal function: Has its own `arguments` object.
  - Example:
    ```javascript
    const arrowFunc = () => { console.log(arguments); }; // ReferenceError
    function normalFunc() { console.log(arguments); } // Logs arguments object
    ```
- **Usage:**
  - Arrow function: Preferred for non-method functions, shorter syntax.
  - Normal function: Suitable for methods, functions requiring `this` or `arguments`.
- **Example:**
  ```javascript
  // Arrow function
  const add = (a, b) => a + b;

  // Normal function
  function multiply(a, b) {
    return a * b;
  }
  ```

### 28. Why Can't We Use the "this" Keyword Inside an Arrow Function in JavaScript?
- **Lexical Binding:**
  - Arrow functions lexically bind `this` from the enclosing context.
  - Example:
    ```javascript
    const obj = {
      value: 10,
      arrowFunc: () => console.log(this.value),
      normalFunc() { console.log(this.value); }
    };
    obj.arrowFunc(); // undefined (or error in strict mode)
    obj.normalFunc(); // 10
    ```
- **No Dynamic Binding:**
  - `this` does not change based on how the arrow function is called.
- **Use Cases:**
  - Useful in nested functions where `this` from the outer function is needed.
  - Example:
    ```javascript
    function Outer() {
      this.value = 1;
      setTimeout(() => {
        console.log(this.value); // 1
      }, 1000);
    }
    new Outer();
    ```
- **Limitations:**
  - Not suitable for methods in objects or classes requiring `this` to refer to the object.
  - Example:
    ```javascript
    const obj = {
      value: 42,
      arrowMethod: () => console.log(this.value), // undefined
      normalMethod() { console.log(this.value); } // 42
    };
    obj.arrowMethod();
    obj.normalMethod();
    ```

### 29. Difference Between a Unary Operator and a Binary Operator in JavaScript
- **Unary Operator:**
  - Operates on a single operand.
  - Examples include `typeof`, `delete`, `++` (increment), `--` (decrement), and unary `+`/`-`.
  - Example:
    ```javascript
    let a = 5;
    console.log(++a); // 6
    console.log(typeof a); // 'number'
    ```
- **Binary Operator:**
  - Operates on two operands.
  - Examples include arithmetic operators (`+`, `-`, `*`, `/`), comparison operators (`<`, `>`, `==`, `===`), and logical operators (`&&`, `||`).
  - Example:
    ```javascript
    let a = 5, b = 10;
    console.log(a + b); // 15
    console.log(a < b); // true
    ```
- **Key Differences:**
  - **Number of Operands:** Unary operators need one operand, while binary operators need two.
  - **Use Cases:** Unary operators typically alter or provide information about a single value, while binary operators perform operations between two values.

### 30. Using the "+" Operator with Strings Results in Concatenation in JavaScript
- **String Concatenation:**
  - When the `+` operator is used with strings, it concatenates them.
  - Example:
    ```javascript
    let str1 = 'Hello';
    let str2 = 'World';
    console.log(str1 + ' ' + str2); // 'Hello World'
    ```
- **Mixed Operands:**
  - If one operand is a string, the other is coerced to a string.
  - Example:
    ```javascript
    let num = 123;
    let str = 'abc';
    console.log(num + str); // '123abc'
    ```
- **Behavior:**
  - The `+` operator triggers type coercion when one operand is a string.
  - Numeric addition occurs only if both operands are numbers.
  - Example:
    ```javascript
    console.log(1 + 2); // 3
    console.log(1 + '2'); // '12'
    ```

### 31. Making JavaScript Code Asynchronous
- **Callbacks:**
  - Pass a function to another function to be executed later.
  - Example:
    ```javascript
    function fetchData(callback) {
      setTimeout(() => {
        callback('Data fetched');
      }, 1000);
    }
    fetchData(data => console.log(data));
    ```
- **Promises:**
  - Represent a value that may be available now, in the future, or never.
  - Example:
    ```javascript
    const promise = new Promise((resolve, reject) => {
      setTimeout(() => {
        resolve('Data fetched');
      }, 1000);
    });
    promise.then(data => console.log(data));
    ```
- **async/await:**
  - Syntactic sugar for promises, making async code look synchronous.
  - Example:
    ```javascript
    async function fetchData() {
      const data = await new Promise(resolve => {
        setTimeout(() => {
          resolve('Data fetched');
        }, 1000);
      });
      console.log(data);
    }
    fetchData();
    ```

### 32. Promise Chaining in JavaScript
- **Definition:**
  - Linking multiple `.then()` calls to handle asynchronous operations in sequence.
- **Error Handling:**
  - Use `.catch()` to handle errors in any step of the chain.
  - Example:
    ```javascript
    fetch('https://api.example.com/data')
      .then(response => response.json())
      .then(data => {
        console.log(data);
        return fetch('https://api.example.com/more-data');
      })
      .then(response => response.json())
      .then(moreData => console.log(moreData))
      .catch(error => console.error('Error:', error));
    ```
- **Sequential Execution:**
  - Each `.then()` waits for the previous promise to resolve before executing.
- **Benefits:**
  - Avoids callback hell.
  - Makes code more readable and maintainable.

### 33. Making Multiple Asynchronous Calls Simultaneously in JavaScript
- **Using Promise.all:**
  - Waits for all promises to resolve or any to reject.
  - Example:
    ```javascript
    const promise1 = fetch('https://api.example.com/data1');
    const promise2 = fetch('https://api.example.com/data2');
    Promise.all([promise1, promise2])
      .then(responses => Promise.all(responses.map(res => res.json())))
      .then(data => {
        console.log(data[0]); // Data from first API
        console.log(data[1]); // Data from second API
      })
      .catch(error => console.error('Error:', error));
    ```
- **Using Promise.allSettled:**
  - Waits for all promises to either resolve or reject.
  - Provides a way to handle results of all promises, regardless of their outcome.
  - Example:
    ```javascript
    const promise1 = fetch('https://api.example.com/data1');
    const promise2 = fetch('https://api.example.com/data2');
    Promise.allSettled([promise1, promise2])
      .then(results => {
        results.forEach(result => {
          if (result.status === 'fulfilled') {
            console.log('Fulfilled:', result.value);
          } else {
            console.log('Rejected:', result.reason);
          }
        });
      });
    ```

### 34. Differences Between Event Bubbling and Event Capturing in JavaScript
- **Event Bubbling:**
  - Events propagate from the target element up to the root.
  - Example:
    ```javascript
    document.getElementById('child').addEventListener('click', () => {
      console.log('Child clicked');
    });
    document.getElementById('parent').addEventListener('click', () => {
      console.log('Parent clicked');
    });
    // Clicking the child logs 'Child clicked' then 'Parent clicked'
    ```
- **Event Capturing:**
  - Events propagate from the root down to the target element.
  - Enabled by setting `useCapture` to `true`.
  - Example:
    ```javascript
    document.getElementById('parent').addEventListener('click', () => {
      console.log('Parent clicked');
    }, true);
    document.getElementById('child').addEventListener('click', () => {
      console.log('Child clicked');
    });
    // Clicking the child logs 'Parent clicked' then 'Child clicked'
    ```
- **Propagation Order:**
  - **Capturing Phase:** Event moves from the root to the target.
  - **Target Phase:** Event is at the target.
  - **Bubbling Phase:** Event moves from the target back up to the root.
- **Stopping Propagation:**
  - `event.stopPropagation()` prevents further propagation in both capturing and bubbling.
  - `event.stopImmediatePropagation()` stops all listeners from being called.


