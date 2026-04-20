# FullStack Interview Preparation

A collection of common **HTML, CSS, JavaScript, React, and Node.js** interview questions with answers.  
This repo is collaborative — feel free to contribute more questions 🚀

---

## 📑 Table of Contents
- [HTML](#html)
- [CSS](#css)
- [JavaScript](#javascript)
- [React](#react)
- [Node.js](#nodejs)

---

## 🟠 HTML

1. What is the difference between block, inline, and inline-block elements?
   - **Block:** Takes full width (`<div>`, `<p>`, `<h1>`).
   - **Inline:** Takes only needed space (`<span>`, `<a>`).
   - **Inline-block:** Behaves like inline but supports width/height.

2. What are semantic HTML tags? Why are they important?
   - Tags that describe meaning, not just presentation (`<header>`, `<article>`, `<footer>`).
   - Improves accessibility & SEO.

3. Difference between `id` and `class` in HTML?
   - `id`: Unique identifier (used once per page).
   - `class`: Can be reused for multiple elements.

4. What is `<datalist>` in HTML?
   - Provides predefined suggestions for an `<input>` field — gives users autocomplete options while still allowing free text entry.
   ```html
   <input list="browsers" name="browser" placeholder="Choose or type...">
   <datalist id="browsers">
     <option value="Google Chrome">
     <option value="Mozilla Firefox">
     <option value="Microsoft Edge">
     <option value="Safari">
     <option value="Opera">
   </datalist>
   ```

5. What is HTML5?
   - **Semantic tags:** `<header>`, `<footer>`, `<article>`, `<section>`
   - **Multimedia:** `<video>`, `<audio>`
   - **APIs:** Geolocation, Local Storage, Canvas
   - **Web Workers**

---

## 🔵 CSS

1. Difference between relative, absolute, fixed, and sticky positioning?
   - **Relative:** Positioned relative to itself.
   - **Absolute:** Positioned relative to nearest positioned ancestor.
   - **Fixed:** Always stays at the same place (relative to viewport).
   - **Sticky:** Switches between relative & fixed depending on scroll.

2. What is the difference between inline, internal, and external CSS?
   - **Inline:** Inside the element (`style=""`).
   - **Internal:** Inside `<style>` tag.
   - **External:** In a separate `.css` file.

3. Explain the difference between `em`, `rem`, `%`, and `px` in CSS.
   - `px`: Fixed pixels.
   - `em`: Relative to parent font-size.
   - `rem`: Relative to root (`html`) font-size.
   - `%`: Relative to parent container.

---

## 🟡 JavaScript

1. Difference between `var`, `let`, and `const`?
   - `var`: Function-scoped, hoisted, can be redeclared.
   - `let`: Block-scoped, hoisted but not initialized, can be reassigned.
   - `const`: Block-scoped, cannot be reassigned.

2. What is hoisting in JavaScript?
   - JavaScript moves variable & function declarations to the top of scope before execution.

3. Difference between `==` and `===`?
   - `==`: Compares values after type conversion (loose equality).
   - `===`: Compares both value & type (strict equality).

4. Explain closures in JavaScript.
   - A closure is when a function remembers its lexical scope even if executed outside of it.

5. Spread operator vs Rest operator

   | Feature   | Spread Operator                 | Rest Operator                  |
   | --------- | ------------------------------- | ------------------------------ |
   | Purpose   | Expands elements                | Collects elements              |
   | Usage     | RHS (right-hand side)           | LHS (left-hand side)           |
   | Use cases | Arrays, objects, function calls | Function params, destructuring |

   ```js
   // Spread operator
   const arr1 = [1, 2, 3];
   const arr2 = [...arr1, 4, 5];
   console.log(arr2); // [1, 2, 3, 4, 5]

   // Rest operator
   const [first, ...rest] = [1, 2, 3, 4];
   console.log(first); // 1
   console.log(rest);  // [2, 3, 4]
   ```

6. `map()` vs `forEach()`

   | Feature      | `map()`             | `forEach()`    |
   | ------------ | ------------------- | -------------- |
   | Return value | New array           | `undefined`    |
   | Purpose      | Transform data      | Side effects   |
   | Chainable    | Yes                 | No             |
   | React usage  | ✅ Yes (JSX lists)  | ❌ No          |

7. Explain Microtask vs Macrotask.

   | Queue     | Description                                       | Examples                                            |
   | --------- | ------------------------------------------------- | --------------------------------------------------- |
   | Microtask | High-priority; runs before the next macrotask     | `Promise`, `queueMicrotask`, `MutationObserver`     |
   | Macrotask | Scheduled tasks; lower priority than microtasks   | `setTimeout`, `setInterval`, `setImmediate`, I/O    |

   - Microtasks always run before the next macrotask.

   <img width="1049" height="590" alt="image" src="https://github.com/user-attachments/assets/422ed303-58a9-4bae-9b44-4ddac4529cdb" />

8. `hasOwnProperty` vs `Object.hasOwn`

   | Feature                          | `obj.hasOwnProperty(key)` | `Object.hasOwn(obj, key)` |
   | -------------------------------- | ------------------------- | ------------------------- |
   | Type                             | Instance method           | Static method             |
   | Safe?                            | ❌ Can break              | ✅ Always safe            |
   | Prototype override risk          | YES                       | NO                        |
   | Works with `Object.create(null)` | ❌ No                     | ✅ Yes                    |
   | Recommended today                | No                        | Yes (ES2022+)             |

9. What is WeakMap in JavaScript?
   - A collection of key-value pairs where keys must be **objects** and are **weakly referenced** (can be garbage collected when no other references exist).
   ```js
   const wm = new WeakMap();
   let user = { name: "Bharat" };
   wm.set(user, "data");
   console.log(wm.get(user)); // "data"
   user = null; // entry may be removed automatically by garbage collector
   ```

10. `localStorage` vs `sessionStorage`
    - Both are part of the Web Storage API and store data in the browser as key-value pairs.

    | Feature       | `localStorage`                    | `sessionStorage`           |
    | ------------- | --------------------------------- | -------------------------- |
    | Expiry        | ❌ Never expires                  | ✅ Clears when tab closes  |
    | Scope         | Shared across tabs (same origin)  | Only same tab              |
    | Storage limit | ~5–10MB                           | ~5–10MB                    |
    | Persistence   | Long-term                         | Temporary                  |

11. JavaScript ES2022 New Features
    - **`.at()` Method** — Access elements using positive or negative index:
      ```js
      const arr = [10, 20, 30, 40];
      console.log(arr.at(1));   // 20
      console.log(arr.at(-1));  // 40
      ```
    - **`Object.hasOwn()`** — Safer way to check object properties (better than `hasOwnProperty`):
      ```js
      const obj = { name: "John" };
      console.log(Object.hasOwn(obj, "name")); // true
      ```
    - **`error.cause`** — Chain errors for better debugging:
      ```js
      try {
        JSON.parse("invalid");
      } catch (err) {
        throw new Error("Parsing failed", { cause: err });
      }
      ```

12. What is the Event Loop?
    - JavaScript is **single-threaded** but non-blocking. The event loop is the mechanism that allows JS to handle asynchronous operations without freezing the main thread.

    **Components:**
    - **Call Stack** — where JS executes code (LIFO). Synchronous code runs here.
    - **Web APIs** — browser-provided (setTimeout, fetch, DOM events). Offloaded here when encountered.
    - **Microtask Queue** — holds Promise callbacks, `MutationObserver`. Checked first after each task.
    - **Macrotask Queue** — holds `setTimeout`, `setInterval`, I/O callbacks. One task per loop tick.

    **How it works:**
    1. Execute all synchronous code on the Call Stack.
    2. When the stack is empty, drain the entire **Microtask Queue**.
    3. Pick **one** task from the Macrotask Queue and run it.
    4. Repeat from step 2.

    ```js
    console.log("1");                           // Call Stack → prints 1
    setTimeout(() => console.log("2"), 0);      // → Web API → Macrotask Queue
    Promise.resolve().then(() => console.log("3")); // → Microtask Queue
    console.log("4");                           // Call Stack → prints 4

    // Output order: 1, 4, 3, 2
    ```

    | Queue          | Examples                              | Priority |
    | -------------- | ------------------------------------- | -------- |
    | Call Stack     | All synchronous code                  | Runs first |
    | Microtask      | `Promise`, `queueMicrotask`           | Before next macrotask |
    | Macrotask      | `setTimeout`, `setInterval`, I/O      | After all microtasks |

13. What is Monkey Patching?
    - Modifying or extending existing objects, classes, or prototypes **at runtime** without changing the original source code.
    ```js
    // Adding a custom method to the built-in Array prototype
    Array.prototype.sum = function () {
      return this.reduce((acc, val) => acc + val, 0);
    };

    console.log([1, 2, 3].sum()); // 6
    ```

    | Aspect     | Detail                                                              |
    | ---------- | ------------------------------------------------------------------- |
    | Use cases  | Polyfills, mocking in tests, quick hotfixes                         |
    | Risks      | Naming conflicts with future native methods, hard to debug          |
    | Avoid when | Working with third-party libraries or shared codebases              |

    ```js
    // Common legitimate use — polyfill for older browsers
    if (!Array.prototype.at) {
      Array.prototype.at = function (index) {
        return index < 0 ? this[this.length + index] : this[index];
      };
    }
    ```

14. CommonJS vs ES Modules (ESM)

    | Feature            | CommonJS (CJS)                  | ES Modules (ESM)                     |
    | ------------------ | ------------------------------- | ------------------------------------ |
    | Syntax             | `require()` / `module.exports`  | `import` / `export`                  |
    | Loading            | Synchronous                     | Asynchronous                         |
    | Environment        | Node.js default (historically)  | Browser native; Node.js (`.mjs`)     |
    | Tree Shakeable     | ❌ No                           | ✅ Yes                               |
    | Static analysis    | ❌ No (dynamic)                 | ✅ Yes (resolved at parse time)      |
    | Top-level `await`  | ❌ Not supported                | ✅ Supported                         |

    ```js
    // CommonJS
    const fs = require("fs");
    module.exports = { myFunction };

    // ES Modules
    import fs from "fs";
    export { myFunction };
    ```

    - ESM is the modern standard — preferred for new projects and browser code.
    - CJS is still widely used in older Node.js codebases and packages.

15. Web Workers vs Service Workers

    | Feature              | Web Worker                        | Service Worker                          |
    | -------------------- | --------------------------------- | --------------------------------------- |
    | Purpose              | Background computation            | Network proxy / caching                 |
    | DOM access           | ❌ No                             | ❌ No                                   |
    | Lifecycle            | Tied to the page                  | Independent of the page                 |
    | Network intercept    | ❌ No                             | ✅ Yes (intercepts `fetch` requests)    |
    | Offline support      | ❌ No                             | ✅ Yes                                  |
    | Use case             | Heavy computation, image processing | PWAs, caching, background sync, push notifications |
    | Communication        | `postMessage`                     | `postMessage` + Fetch/Push events       |

    **Web Worker** — offload CPU-intensive tasks to a separate thread:
    ```js
    // main.js
    const worker = new Worker("worker.js");
    worker.postMessage({ numbers: [1, 2, 3, 4, 5] });
    worker.onmessage = (e) => console.log("Sum:", e.data);

    // worker.js
    self.onmessage = (e) => {
      const sum = e.data.numbers.reduce((a, b) => a + b, 0);
      self.postMessage(sum);
    };
    ```

    **Service Worker** — intercept and cache network requests:
    ```js
    // Register
    navigator.serviceWorker.register("/sw.js");

    // sw.js — cache-first strategy
    self.addEventListener("fetch", (event) => {
      event.respondWith(
        caches.match(event.request).then((cached) => cached || fetch(event.request))
      );
    });
    ```

---

## 🟢 React

### Fundamentals

1. What is the difference between functional and class components?
   - **Class:** Uses `this`, lifecycle methods.
   - **Functional:** Uses hooks (`useState`, `useEffect`), simpler syntax.

2. What are functional components?
   - Functional components are JavaScript functions that accept arguments (called props) and return React elements that describe what should appear on the screen.

3. What is an implicit return in functional components?
   - If a component only contains a single return statement, you can skip the `return` keyword and curly braces by using parentheses:
   ```jsx
   const MyComponent = () => (
     <h1>Hello, world!</h1>
   );
   export default MyComponent;
   ```

4. Why must a React component return a single root element?
   - React requires one root element because the virtual DOM needs a single entry point to represent the component tree.

5. Why is JSX not valid JavaScript?
   - Browsers cannot directly interpret JSX. It must be transpiled (commonly by Babel) into JavaScript that React can execute.

6. React Elements vs. HTML Elements

   | Feature        | React Element                         | HTML Element                              |
   | -------------- | ------------------------------------- | ----------------------------------------- |
   | What it is     | JS object (virtual DOM node)          | Actual DOM node in browser                |
   | Mutability     | ❌ Immutable                          | ✅ Mutable                                |
   | Created by     | JSX / `React.createElement()`         | HTML / `document.createElement()`         |
   | Where it lives | Virtual DOM (in memory)               | Real DOM (browser DOM tree)               |
   | Performance    | Efficient (batch updates via diffing) | Slower when modified directly & repeatedly |
   | Purpose        | Describe what UI should look like     | Rendered UI on screen                     |

   **Rendering flow:**
   ```
   JSX (developer writes)
      ↓
   React.createElement()
      ↓
   React Element (JS object)
      ↓
   Virtual DOM
      ↓
   React DOM reconciler
      ↓
   Real HTML Element (browser renders)
   ```

---

### Props & State

7. What are props in React?
   - Read-only data passed from parent to child to configure components.

8. What is the difference between props and state?
   - **Props:** Immutable, passed from parent.
   - **State:** Mutable, managed within the component.

9. Can a child component modify props directly?
   - ❌ No. Props are read-only; children use callback functions to update parent data.

10. What is the `children` prop used for?
    - To render nested JSX elements inside a component.

11. What is the purpose of `defaultProps`?
    - To define default values when a prop isn't passed.

12. Is `useState` mutable or immutable in React?
    - `useState` is **immutable** in React. React always expects you to create new state, not modify the existing state. If the existing state is mutated directly, React may not re-render.

    **Wrong approach (direct mutation):**
    ```jsx
    const addItem = () => {
      items.push('cherry'); // 🔴 Mutating state directly
      setItems(items);
    };
    ```

    **Correct approach (immutability):**
    ```jsx
    const addItem = () => {
      setItems([...items, 'cherry']); // ✅ Creating a new array
    };
    ```

---

### Lifecycle

13. React Component Lifecycle (Class & Functional)

    Every React component goes through three main phases: **Mounting → Updating → Unmounting**

    **Class Component Lifecycle Methods:**

    | Phase      | Method                              | Purpose                                  | When It Runs                        |
    | ---------- | ----------------------------------- | ---------------------------------------- | ----------------------------------- |
    | Mounting   | `constructor()`                     | Initialize state and bind methods        | Before component appears on screen  |
    |            | `getDerivedStateFromProps()`        | Sync state from props (rarely used)      | Before every render                 |
    |            | `render()`                          | Return JSX (UI)                          | During render                       |
    |            | `componentDidMount()`               | Run side effects (fetch, subscriptions)  | After first render                  |
    | Updating   | `shouldComponentUpdate()`           | Optimize by skipping re-renders          | Before re-render                    |
    |            | `getSnapshotBeforeUpdate()`         | Capture DOM info before update           | Before DOM changes                  |
    |            | `componentDidUpdate()`              | Run side effects after updates           | After DOM is updated                |
    | Unmounting | `componentWillUnmount()`            | Cleanup (timers, listeners, etc.)        | Before component is removed         |

    **Example:**
    ```jsx
    class MyComponent extends React.Component {
      constructor(props) {
        super(props);
        this.state = { data: null };
      }
      componentDidMount() { console.log("Mounted"); }
      shouldComponentUpdate(nextProps, nextState) {
        return nextState.data !== this.state.data;
      }
      componentDidUpdate() { console.log("Updated"); }
      componentWillUnmount() { console.log("Unmounted"); }
      render() { return <div>{this.state.data}</div>; }
    }
    ```

    **Functional Component Hooks Equivalent:**

    | Lifecycle Stage  | Class Method                 | Functional Equivalent (Hooks)                       |
    | ---------------- | ---------------------------- | --------------------------------------------------- |
    | Mounting         | `componentDidMount()`        | `useEffect(() => { ... }, [])`                      |
    | Updating         | `componentDidUpdate()`       | `useEffect(() => { ... }, [dependencies])`          |
    | Unmounting       | `componentWillUnmount()`     | Cleanup function returned inside `useEffect()`      |
    | State init       | `constructor()`              | `useState()`                                        |
    | Derived state    | `getDerivedStateFromProps()` | Logic inside `useEffect()` reacting to prop changes |

    **Example:**
    ```jsx
    import React, { useState, useEffect } from "react";

    function MyComponent() {
      const [data, setData] = useState(null);

      useEffect(() => {
        console.log("Mounted or Updated");
        setData("Hello React!");
        return () => { console.log("Cleanup before unmount"); };
      }, []); // empty array = run once on mount

      return <div>{data}</div>;
    }
    ```

---

### Rendering Pipeline

14. Render vs Paint in React

    These are two distinct phases — React owns **Render**, the browser owns **Paint**.

    **Render Phase (React's work):**
    - React runs your component functions to compute what the UI should look like.
    - Diffs the new virtual DOM against the previous one (**reconciliation**).
    - Determines the minimal set of real DOM changes needed.
    - Does **not** touch the screen yet.

    **Commit Phase (React applying changes):**
    - React writes the calculated changes to the real DOM.
    - `useLayoutEffect` fires here — synchronously, before the browser paints.

    **Paint Phase (Browser's work):**
    - After the DOM is updated, the browser runs its rendering pipeline:
      `Style → Layout (Reflow) → Paint → Composite`
    - Pixels are drawn to the screen.
    - `useEffect` fires **after** this — asynchronously, non-blocking.

    **Full pipeline:**
    ```
    Component function runs     ← Render phase (React)
           ↓
    Virtual DOM diffed / reconciled
           ↓
    Real DOM updated            ← Commit phase (React)
           ↓
    useLayoutEffect fires       ← synchronous, blocks paint
           ↓
    Browser: Layout → Paint → Composite
           ↓
    useEffect fires             ← async, after pixels on screen
    ```

    **`useLayoutEffect` vs `useEffect`:**

    | Hook               | When it runs                    | Blocks paint? | Use case                                              |
    | ------------------ | ------------------------------- | ------------- | ----------------------------------------------------- |
    | `useLayoutEffect`  | After DOM update, before paint  | ✅ Yes        | Read/write DOM layout (e.g. `getBoundingClientRect`)  |
    | `useEffect`        | After paint (async)             | ❌ No         | Data fetching, subscriptions, timers                  |

    ```jsx
    import { useEffect, useLayoutEffect, useRef } from "react";

    function MeasureBox() {
      const ref = useRef();

      // Runs after DOM update, before browser paints — no layout flicker
      useLayoutEffect(() => {
        const width = ref.current.getBoundingClientRect().width;
        console.log("Width (before paint):", width);
      }, []);

      // Runs after browser paints — safe for side effects
      useEffect(() => {
        console.log("After paint — fetch data here");
      }, []);

      return <div ref={ref}>Measure me</div>;
    }
    ```

    **Key distinctions:**
    - A React **re-render** ≠ a browser **repaint**. If reconciliation produces no DOM changes, the browser does not repaint.
    - React re-render = running the component function (cheap, in-memory).
    - Browser repaint = redrawing pixels (can be expensive with layout/reflow changes).
    - React **batches** DOM updates across multiple state changes to minimize repaints.

---

### Hooks & Performance

15. What is the difference between `useMemo`, `useCallback`, and `React.memo`?
    - `useMemo`: Memoizes a **calculated value**.
    - `useCallback`: Memoizes a **function** reference.
    - `React.memo`: Memoizes a **whole component** to avoid re-renders.

    <img width="1268" height="475" alt="image" src="https://github.com/user-attachments/assets/b78c9190-2d18-4b5d-be26-7881d1e09a5f" />

    **`useCallback` Example:**
    ```jsx
    import React, { useState, useCallback } from "react";

    function Child({ onAdd }) {
      console.log("Child re-rendered");
      return <button onClick={onAdd}>Add</button>;
    }

    export default function Parent() {
      const [count, setCount] = useState(0);
      const [theme, setTheme] = useState("light");

      // ✅ Using useCallback prevents unnecessary re-creations of this function
      const handleAdd = useCallback(() => {
        setCount((prev) => prev + 1);
      }, []);

      return (
        <div>
          <h2>Count: {count}</h2>
          <Child onAdd={handleAdd} />
          <button onClick={() => setTheme(theme === "light" ? "dark" : "light")}>
            Toggle Theme
          </button>
        </div>
      );
    }
    ```

    **`useMemo` Example:**
    ```jsx
    import React, { useState, useMemo } from "react";

    export default function ProductList({ products }) {
      const [search, setSearch] = useState("");

      // ✅ useMemo prevents re-running this heavy filter on every render
      const filteredProducts = useMemo(() => {
        console.log("Filtering products...");
        return products.filter((p) =>
          p.name.toLowerCase().includes(search.toLowerCase())
        );
      }, [search, products]);

      return (
        <div>
          <input
            placeholder="Search..."
            value={search}
            onChange={(e) => setSearch(e.target.value)}
          />
          <ul>
            {filteredProducts.map((p) => (
              <li key={p.id}>{p.name}</li>
            ))}
          </ul>
        </div>
      );
    }
    ```

16. Tree Shaking
    - Tree shaking = removing unused code from your bundle. Used by bundlers like Webpack, Rollup, and Vite.
    ```js
    // math.js
    export const add = (a, b) => a + b;
    export const sub = (a, b) => a - b;

    // app.js — only `add` is imported, so `sub` is removed from the bundle
    import { add } from "./math";
    add(2, 3);
    ```

17. Lazy Loading
    - Load components only when needed. Improves performance by reducing the initial bundle size.

18. Why do we need to build React?
    - React code cannot run directly in browsers efficiently. JSX needs compilation (Babel), code needs minification and tree shaking (Webpack/Vite), and modern JS must be transpiled for older browsers.

    | Feature        | 🧪 Development Mode             | 🚀 Production Build                          |
    | -------------- | ------------------------------- | -------------------------------------------- |
    | JSX Conversion | Converted instantly (in memory) | Converted during build                       |
    | Performance    | Not optimized                   | Highly optimized                             |
    | Minification   | ❌ No                           | ✅ Yes                                       |
    | Tree Shaking   | ❌ No                           | ✅ Yes (removes unused code)                 |
    | Bundling       | Minimal / on-demand             | Fully bundled & code-split                   |
    | Debugging      | ✅ Warnings, error overlays     | ❌ No debugging info                         |
    | Source Maps    | ✅ Enabled                      | ⚠️ Optional / often disabled                 |
    | Fast Refresh   | ✅ HMR enabled                  | ❌ No HMR                                    |
    | Build Output   | Stored in memory                | Physical optimized files (dist/build folder) |

---

### Forms & Events

19. Controlled vs. Uncontrolled Components

    | Feature              | Controlled Component                | Uncontrolled Component             |
    | -------------------- | ----------------------------------- | ---------------------------------- |
    | Data source          | React state                         | DOM (`ref`)                        |
    | Value updated by     | `onChange` handler                  | User input (DOM)                   |
    | Validation           | Easy to validate within React       | Requires manual DOM access         |
    | Performance          | May re-render more often            | Fewer re-renders                   |
    | Use case             | Complex, dynamic, validated forms   | Simple, non-reactive forms         |
    | Example hooks        | `useState`, `useEffect`             | `useRef`                           |

    **Controlled Component** — React is the single source of truth for form data:
    ```jsx
    import { useState } from "react";

    function ControlledInput() {
      const [name, setName] = useState("");

      const handleSubmit = (e) => {
        e.preventDefault();
        alert(`Submitted name: ${name}`);
      };

      return (
        <form onSubmit={handleSubmit}>
          <input type="text" value={name} onChange={(e) => setName(e.target.value)} />
          <button type="submit">Submit</button>
        </form>
      );
    }
    ```

    **Uncontrolled Component** — DOM manages the data instead of React:
    ```jsx
    import { useRef } from "react";

    function UncontrolledInput() {
      const nameRef = useRef();

      const handleSubmit = (e) => {
        e.preventDefault();
        alert(`Submitted name: ${nameRef.current.value}`);
      };

      return (
        <form onSubmit={handleSubmit}>
          <input type="text" ref={nameRef} />
          <button type="submit">Submit</button>
        </form>
      );
    }
    ```

20. Event Delegation vs Event Handling

    - **Event Handling (Normal DOM Way):** Attaches event listeners directly to individual DOM elements. Simple, but inefficient for many elements.
    - **Event Delegation:** Attaches a single listener to a common ancestor and lets events bubble up.

    ```jsx
    {/* Delegation — one listener on <ul> handles all <li> clicks */}
    <ul onClick={handleItemClick}>
      <li>Item 1</li>
      <li>Item 2</li>
      <li>Item 3</li>
    </ul>
    ```

    | Aspect         | Event Handling                        | Event Delegation                          |
    | -------------- | ------------------------------------- | ----------------------------------------- |
    | Listeners      | One per element                       | One on common ancestor                    |
    | Memory         | Higher (many listeners)               | Lower (single listener)                   |
    | Dynamic nodes  | Must re-attach for new elements       | ✅ Works automatically                    |
    | Downside       | Memory-intensive at scale             | `event.target` needs extra checks         |

    **React's internal approach:** React attaches a single event listener at the root container rather than on each element — it uses event delegation by default.

---

### Next.js

21. What is the difference between client and server components in Next.js?
    - **Client:** Runs in the browser, can use state/effects.
    - **Server:** Rendered on the server, better performance, can fetch data directly.

22. Explain SSR, SSG, and ISR in Next.js.
    - **SSR:** Rendered on each request.
    - **SSG:** Rendered at build time.
    - **ISR:** Rebuilds pages after a set interval.

---

### React 19

23. New Features in React 19
    - **Actions** — Server + client mutations
    - **`use()` Hook**
    - **`useOptimistic` Hook**

---

## 🟣 Node.js

1. What is the Node.js Runtime?
   - Node.js is single-threaded in the sense that JavaScript execution happens on one thread, but it is multi-threaded under the hood because Libuv manages a thread pool for heavy I/O. This design makes it perfect for I/O-intensive apps (streaming, APIs) but a poor choice for CPU-intensive tasks (image processing, heavy encryption) because those would block the main thread.

   <img width="1434" height="718" alt="image" src="https://github.com/user-attachments/assets/cc9fe34c-3d53-47e7-b8d2-5a2b7c8073e3" />

2. What is REPL in Node?
   - An interactive shell that cycles through four steps:
     - **Read:** Reads the user's input, parses it into a JavaScript data structure, and stores it in memory.
     - **Eval:** Takes the data structure and evaluates the code.
     - **Print:** Prints the result of the evaluation to the console.
     - **Loop:** Loops the entire process until the user terminates the session.
