
### Lecture 04: Working with Modules in Node.js

#### **1. Using Multiple JavaScript Files in Node.js**

- **Why Use Modules?**
  - In larger applications, it’s useful to split code into separate files (modules) to keep it organized and reusable.
  - **Modules** allow you to separate logic (e.g., functions, variables) across multiple files and use them where needed.

- **Importing Modules with `require` (CommonJS)**:
  - In Node.js, you can import other JavaScript files (modules) using the **`require`** function.
  - Example:
    ```javascript
    const someModule = require('./path/to/module');
    ```
  - When you use `require`, Node.js will **load and execute** the code in the required module before continuing with the rest of the code in the file.

---

#### **2. Creating and Using a Basic Function in a Module**

- **Example Setup**:
  - Let’s say we want to create a module called `sum.js` that contains a function to add two numbers.
  - **Step 1**: Create `sum.js` and define a `calculateSum` function.
    ```javascript
    // sum.js
    function calculateSum(a, b) {
      return a + b;
    }
    ```

  - **Problem**: If you just `require` `sum.js` in another file, like `app.js`, and try to use `calculateSum`, it won’t work.
    - This is because **modules protect their variables and functions by default**, so they’re not accessible outside the file.
    - To make `calculateSum` accessible, we need to **export** it.

---

#### **3. Exporting and Importing in CommonJS**

- **Exporting**:
  - In CommonJS (Node.js’s default module system), you export functionality by using `module.exports`.
  - Modify `sum.js` to export `calculateSum`:
    ```javascript
    // sum.js
    function calculateSum(a, b) {
      return a + b;
    }
    module.exports = { calculateSum };
    ```

- **Importing**:
  - In `app.js`, you can now import `calculateSum` and use it:
    ```javascript
    // app.js
    const { calculateSum } = require('./sum');
    console.log(calculateSum(3, 4)); // Outputs: 7
    ```

---

#### **4. Exporting Multiple Functions and Using Object Destructuring**

- You can **export multiple functions or variables** from a module by exporting an object with multiple properties.
  - Example:
    ```javascript
    // sum.js
    function calculateSum(a, b) { return a + b; }
    function calculateMultiply(a, b) { return a * b; }
    module.exports = { calculateSum, calculateMultiply };
    ```

  - Import using **object destructuring**:
    ```javascript
    // app.js
    const { calculateSum, calculateMultiply } = require('./sum');
    ```

- **Security and Privacy**:
  - Not everything in a module is exported; only what’s defined in `module.exports` is accessible.
  - This feature helps keep module internals private and organized.

---

#### **5. CommonJS (CJS) vs. ES Modules (ESM)**

- **CommonJS (CJS)**:
  - The **older module system** in Node.js, default and widely supported.
  - **Synchronous** and simpler to use in Node.js.
  - **Export**: Use `module.exports = {...}` or `exports`.
  - **Import**: Use `require(...)`.
  - Example:
    ```javascript
    // Exporting
    module.exports = { calculateSum, calculateMultiply };

    // Importing
    const { calculateSum } = require('./sum');
    ```

- **ES Modules (ESM)**:
  - A **newer, standardized** module format used in modern JavaScript (also in React).
  - **Asynchronous** by design and runs in **strict mode**.
  - To enable ESM in Node.js, add `"type": "module"` in `package.json` or use `.mjs` file extensions.
  - **Export**: Use `export` syntax (e.g., `export function ...`).
  - **Import**: Use `import` syntax, no `require`.
  - Example:
    ```javascript
    // Exporting (sum.js)
    export function calculateSum(a, b) { return a + b; }

    // Importing (app.js)
    import { calculateSum } from './sum.js';
    ```

---

#### **6. Understanding `module.exports`**

- **`module.exports` as an Empty Object**:
  - By default, `module.exports` is an empty object `{}`.
  - You can add properties to it:
    ```javascript
    module.exports = { calculateSum, calculateMultiply };
    ```

- **Grouping Exports with an Index File**:
  - If you have multiple modules (e.g., `sum.js`, `multiply.js`) inside a folder, you can create an **`index.js`** to manage exports from that folder.

  - **Example Structure**:
    ```
    /calculate
    ├── sum.js
    ├── multiply.js
    └── index.js
    ```

  - **index.js**: Export all functions from the folder:
    ```javascript
    // index.js
    const { calculateSum } = require('./sum');
    const { calculateMultiply } = require('./multiply');
    module.exports = { calculateSum, calculateMultiply };
    ```

  - Now in `app.js`, you can import both functions from the folder without needing to know the exact file location:
    ```javascript
    // app.js
    const { calculateSum, calculateMultiply } = require('./calculate');
    ```

- **Benefit of Using an Index File**:
  - Reduces clutter and keeps imports manageable when dealing with many files.
  - **`app.js` doesn’t need to know the specific location of each function**. This simplifies project structure and management.

---

#### **7. Requiring JSON Files Directly**

- In Node.js, you can directly `require` JSON files.
  - Example:
    ```javascript
    const data = require('./data.json');
    console.log(data); // This will print the JSON content as an object
    ```

---

#### **8. Core Modules in Node.js**

- Node.js comes with several **core modules** that provide various built-in functionalities.
  - Example: `util` module for utility functions.
  - Importing a core module:
    ```javascript
    const util = require('node:util');
    ```

---

### Summary and Key Points

1. **Importing Modules with `require` (CommonJS)**:
   - Use `require('./module')` to import.
   - Code runs immediately but remains inaccessible unless exported.

2. **Exporting with `module.exports`**:
   - `module.exports` allows you to export functions, variables, or objects to make them available outside the file.

3. **Module Security and Privacy**:
   - Only exported properties are accessible, keeping other details private.

4. **CommonJS (CJS) vs. ES Modules (ESM)**:
   - CJS: Uses `require` and `module.exports`, synchronous, default in Node.js.
   - ESM: Uses `import` and `export`, asynchronous, enabled with `"type": "module"` or `.mjs`.

5. **Index File for Folder Exports**:
   - Use an `index.js` to combine exports, creating a module for multiple files.

6. **Requiring JSON Files and Core Modules**:
   - JSON files can be imported directly.
   - Core modules like `util` are built-in and available without installation.

This breakdown should give you a clear understanding of using modules in Node.js, covering both CJS and ESM module systems and how to work with them efficiently.