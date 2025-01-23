
### Lecture 03: Global Object in Node.js and Browser

#### **1. Setting Up Node.js**
- **Install Node.js**: 
  - First, Node.js needs to be installed on your machine.
  - **Node.js** is a **JavaScript runtime environment** that allows you to run JavaScript outside of the browser.

- **REPL (Read-Evaluate-Print Loop)**:
  - After installing, you can open **Command Prompt (cmd)** or a terminal and type `node` to enter the **Node.js REPL**.
  - REPL is an interactive environment where you can type JavaScript code, and it immediately **reads**, **evaluates** the code, **prints** the result, and **loops** back to wait for more input.
  - This is useful for quick testing, but typically we write our code in a `.js` file and run it using the command `node filename.js` (e.g., `node app.js`).

---

#### **2. Node.js as a JavaScript Runtime Environment**
- **JavaScript runtime environment** means that **Node.js** provides the necessary tools and environment to execute JavaScript outside of the browser.
  
- **Superpowers of Node.js**:
  - While Node.js uses the **V8 engine** (which is present in the browser too, specifically in Chrome), Node.js adds several **"superpowers"** on top of the V8 engine. These superpowers include additional features like:
    - **Global object** (which is different from the `window` object in the browser)
    - **File system APIs**
    - **Networking capabilities** like creating servers
    - **Timing functions** such as `setTimeout`, `setInterval`, etc.

---

#### **3. Global Object in Browser vs Node.js**

##### **Browser Environment (Window Object)**:
- In a **browser**, JavaScript runs in a sandbox environment. The global object in this environment is called **`window`**.
  - **`window`** represents the browser's window and provides access to global variables, functions, and the browser’s APIs like `alert()`, `setTimeout()`, and `document`.
  
- If you **console.log(window)** in the browser, it will print the global scope of the browser, which includes the **DOM**, **Event Listeners**, **localStorage**, etc.

##### **Node.js Environment (Global Object)**:
- In **Node.js**, there is **no `window` object**, since there is no browser involved.
  
- Instead, Node.js has a **`global` object**, which provides global variables and functions that are available throughout the Node.js environment.
  - If you **console.log(global)** in Node.js, you will see various methods like `setTimeout`, `clearInterval`, `setInterval`, etc., along with other Node-specific functionalities.
  
- **Why do we need the Global Object?**
  - The global object is essentially the top-level scope in any JavaScript runtime environment. In Node.js, it provides you access to built-in global variables and functions (like `console`, `process`, `require`, etc.).
  - It allows you to run code globally without needing to import or require specific modules for every operation. For example:
    - You can call `setTimeout()` or `console.log()` directly without importing them, because they exist in the global object.

---

#### **4. Why Different Global Objects?**
- **Why does the browser use `window` and Node.js use `global`?**
  - When JavaScript was first created for browsers, the **`window` object** was designed to represent the browser window, and all global variables and functions were attached to it. Over time, browsers added more functionalities to the `window` object (like interacting with the DOM, handling events, etc.).
  
  - On the other hand, **Node.js** is a **server-side** environment. It doesn't have a browser window, so it needed a different global object (`global`) to manage global variables and functions.
  
- **Standardizing Global Objects**:
  - To avoid confusion between `window` (browser) and `global` (Node.js), JavaScript introduced a new **standardized name for the global object**, called **`globalThis`**.
    - **`globalThis`** is a universal reference to the global object in any JavaScript runtime (whether it's the browser, Node.js, or other environments).
    - In a **browser**, `globalThis` is the same as `window`.
    - In **Node.js**, `globalThis` is the same as `global`.

- **Why is `globalThis` important?**
  - It ensures **consistency** across different JavaScript environments.
  - If you write code that uses `globalThis`, it will work in both **Node.js** and the **browser** without needing to change the global object reference.

---

#### **5. Comparing Global Objects (`window`, `global`, `globalThis`)**
- **`window` (Browser)**:
  - The global object in the browser.
  - Provides access to browser-specific features like the DOM, alert, and browser storage.
  
- **`global` (Node.js)**:
  - The global object in Node.js.
  - Provides access to server-side features like file system access, networking, process management, etc.
  
- **`globalThis` (Universal)**:
  - A standardized name for the global object, works across any JavaScript runtime (browser or server).

---

#### **6. Object Reference and Global Variables in JavaScript**
- In JavaScript, **objects are passed by reference**. This means if two variables point to the same object, they both refer to the same memory location.
  - For example:
    ```javascript
    console.log(globalThis === global); // true in Node.js
    ```
  - This shows that `globalThis` and `global` are the same in the Node.js environment because both refer to the same object in memory.

- **Why is this important?**
  - Understanding how JavaScript passes objects by reference helps when managing global variables. Changes to one reference (e.g., `globalThis`) will affect the other (e.g., `global`).

---

### Summary and Clarification of Confusions:

1. **Global Object in Browser (`window`)**:
   - In the **browser**, the **global object is `window`**.
   - The `window` object holds global properties and methods such as the DOM, `setTimeout`, `console`, etc.
  
2. **Global Object in Node.js (`global`)**:
   - In **Node.js**, the **global object is `global`**, not `window`.
   - `global` holds server-side methods like `require`, `process`, `setTimeout`, and more.
  
3. **`globalThis` (Universal)**:
   - **`globalThis`** is a standardized global object reference.
   - Whether you're in a browser or Node.js, `globalThis` will always refer to the appropriate global object (`window` in the browser, `global` in Node.js).

4. **Importance of the Global Object**:
   - The global object is crucial because it provides global variables, functions, and APIs that are accessible from anywhere in your code, without needing imports or module requirements.
   - It’s the top-level scope that makes running JavaScript code easier and more efficient across different environments.
---

### Why we didn't need to think about the global object in React/browser JavaScript:

Ah, that's a great observation! Let me explain why you didn't need to think about the global object in React/browser JavaScript, versus why it becomes more important in Node.js.

1. Browser (React/JavaScript) Environment:
```javascript
// In browser/React, many things are automatically available
setTimeout(() => {}, 1000);     // Works directly
fetch('/api/data');             // Works directly
document.getElementById();      // Works directly
```
- Everything is automatically available through the `window` object
- React handles state management through its own tools:
  ```javascript
  // React's way of managing state
  const [count, setCount] = useState(0);
  useContext(MyContext);
  ```

2. Node.js Environment:
```javascript
// In Node.js, we need global for similar functionality
global.setTimeout(() => {}, 1000);
global.process.env.NODE_ENV;    // Check environment
global.Buffer.from('data');     // Handle binary data
```
- No automatic DOM or browser APIs
- Needs different tools for server-side operations

Here's why the difference exists:

3. Browser vs Node.js Comparison:

Frontend (React/Browser):
```javascript
// Everything is about UI and user interaction
window.alert('Hello!');
document.querySelector('.button');
localStorage.setItem('user', 'John');
```
- Focused on DOM manipulation
- Built-in browser APIs
- Single user session

Backend (Node.js):
```javascript
// Everything is about server operations
global.process.env.PORT;        // Server configuration
global.__dirname;               // File system paths
global.Buffer;                  // Handle binary data
```
- Multiple user sessions
- File system operations
- Server configurations
- Database connections

4. Real-world Example:

Frontend (React):
```javascript
// React application
function App() {
  const [data, setData] = useState([]);
  
  useEffect(() => {
    fetch('/api/users').then(res => res.json())
      .then(data => setData(data));
  }, []);

  return <UserList users={data} />;
}
```

Backend (Node.js):
```javascript
// Node.js server
global.users = new Map();  // Shared across all requests

app.get('/api/users', (req, res) => {
  res.json(Array.from(global.users.values()));
});

app.post('/api/users', (req, res) => {
  global.users.set(req.body.id, req.body);
  res.status(201).send();
});
```

5. Why Node.js Needs Global Object More:

Think of it like this:
- React/Browser is like a single room in a house
  - Everything you need is within reach
  - You only manage your own space
  - Built-in amenities (window object)

- Node.js is like managing an entire apartment building
  - Need access to building-wide utilities
  - Managing multiple tenants (users)
  - Controlling central systems (databases, file systems)
  ```javascript
  // Building-wide settings
  global.DATABASE_URL = process.env.DATABASE_URL;
  global.MAX_CONNECTIONS = 100;
  global.MAINTENANCE_MODE = false;
  ```

Now you just saw the example now understand why global object matters:

1. Centralized Control
    - Like having one main control room for the entire building
    - All systems can be monitored from one place
    - Changes affect the entire building immediately
2. Resource Sharing
    - Like shared utilities (water, electricity)
    - Every "tenant" (user request) knows what's available
    - Prevents overuse of resources
3. Consistent Rules
    - Like building policies that apply to everyone
    - Same security rules for all entrances
    - Standard procedures for emergencies
4. Efficient Communication
    - Like a building-wide intercom system
    - Messages can reach all parts of the system
    - Everyone gets the same information

Without the global object, it would be like:

- Each floor having its own separate management system
- No way to know what's happening in other parts of the building
- Duplicate systems and wasted resources
- Inconsistent rules and procedures
- Difficult to coordinate building-wide activities

This is why Node.js, which often handles multiple users, connections, and resources (like our apartment building), needs the global object - it's the central management system that keeps everything running smoothly and consistently!

6. Practical Example of Difference:

Frontend (React):
```javascript
// State is isolated to components
function Counter() {
  const [count, setCount] = useState(0);
  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

Backend (Node.js):
```javascript
// State might need to be shared across all requests
global.activeConnections = 0;

server.on('connection', () => {
  global.activeConnections++;
  console.log(`Active connections: ${global.activeConnections}`);
});
```

7. When You'll Actually Need Global Object in Node.js:

Common Use Cases:
```javascript
// Configuration
global.CONFIG = {
  port: process.env.PORT || 3000,
  dbUrl: process.env.DATABASE_URL,
  apiKeys: {
    stripe: process.env.STRIPE_KEY,
    aws: process.env.AWS_KEY
  }
};

// Monitoring
global.metrics = {
  requests: 0,
  errors: 0,
  activeUsers: new Set()
};

// Shared Utilities
global.logger = {
  info: (msg) => console.log(`[INFO] ${msg}`),
  error: (msg) => console.error(`[ERROR] ${msg}`)
};
```

So, in summary:
- In React/browser, you rarely need to think about global objects because:
  - The browser provides everything through `window`
  - React has its own state management
  - You're dealing with a single user/session

- In Node.js, the global object becomes important because:
  - You're managing server-wide resources
  - Handling multiple users/requests
  - Need shared configurations and utilities
  - Dealing with system-level operations

This is why you didn't feel the need for global objects in React but might need them in Node.js!