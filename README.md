# FullStack Interview Preparation

A collection of common **HTML, CSS, JavaScript, and React** interview questions with answers.  
This repo is collaborative — feel free to contribute more questions 🚀

---

## 📑 Table of Contents
- [HTML](#html)
- [CSS](#css)
- [JavaScript](#javascript)
- [React](#react)

---

## 🟠 HTML

1. What is the difference between block, inline, and inline-block elements?  
   - Block: Takes full width (`<div>`, `<p>`, `<h1>`).  
   - Inline: Takes only needed space (`<span>`, `<a>`).  
   - Inline-block: Behaves like inline but supports width/height.  

1. What are semantic HTML tags? Why are they important?  
   - Tags that describe meaning, not just presentation (`<header>`, `<article>`, `<footer>`).  
   - Improves accessibility & SEO.  

1. Difference between `id` and `class` in HTML?  
   - `id`: Unique identifier (used once per page).  
   - `class`: Can be reused for multiple elements.  

1. What is **datalist** in html?
   - The <datalist> element in HTML is used to provide a list of predefined suggestions for an <input> field.
   - It gives users the convenience of auto-complete options, while still allowing free text entry.
   - **Example**
     ```
     <input list="browsers" name="browser" placeholder="Choose or type...">

      <datalist id="browsers">
        <option value="Google Chrome">
        <option value="Mozilla Firefox">
        <option value="Microsoft Edge">
        <option value="Safari">
        <option value="Opera">
      </datalist>

     ```

1. What is HTML5?
   - **Semantic tags:**
   - EX: header, footer, article, section
   - **Multimedia:**
   - EX: video, audio
   - **APIs:**
   - EX: Geolocation, Local Storage, Canvas

## 🔵 CSS

1. Difference between relative, absolute, fixed, and sticky positioning?  
   - Relative: Positioned relative to itself.  
   - Absolute: Positioned relative to nearest positioned ancestor.  
   - Fixed: Always stays at the same place (relative to viewport).  
   - Sticky: Switches between relative & fixed depending on scroll.  

1. What is the difference between inline, internal, and external CSS?  
   - Inline: Inside the element (`style=""`).  
   - Internal: Inside `<style>` tag.  
   - External: In a separate `.css` file.  

1. Explain the difference between `em`, `rem`, `%`, and `px` in CSS.  
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

1. What is hoisting in JavaScript?  
   - JavaScript moves variable & function declarations to the top of scope before execution.  

1. Difference between `==` and `===`?  
   - `==`: Compares values after type conversion (loose equality).  
   - `===`: Compares both value & type (strict equality).  

1. Explain closures in JavaScript.  
   - A closure is when a function remembers its lexical scope even if executed outside of it.  

1. hasOwnProperty vs Object.hasOwn.  
   -  | Feature                          | `obj.hasOwnProperty(key)` | `Object.hasOwn(obj, key)` |
      | -------------------------------- | ------------------------- | ------------------------- |
      | Type                             | Instance method           | Static method             |
      | Safe?                            | ❌ Can break             | ✅ Always safe            |
      | Prototype override risk          | YES                       | NO                        |
      | Works with `Object.create(null)` | ❌ No                    | ✅ Yes                    |
      | Recommended today                | No                        | Yes (ES2022+)             |

1. Explain Microtask vs Macrotask.  
   - Macrotask  → “small, high-priority tasks” like promises. EX: setTimeout, setInterval, setImmediate
   - Microtask  → “big tasks” like timers, events, I/O EX: Promise
   
   - Microtasks always run before the next macrotask
   <img width="1049" height="590" alt="image" src="https://github.com/user-attachments/assets/422ed303-58a9-4bae-9b44-4ddac4529cdb" />

1. map vs forEach.  

| Feature      | map()              | forEach()    |
| ------------ | -----------------  | ------------ |
| Return value | New array          | undefined    |
| Purpose      | Transform data     | Side effects |
| Chainable    | Yes                | No           |
| React usage  | ✅ Yes (JSX lists) | ❌ No       |

---

1. JavaScript 2022 (ES2022) New Features
   - .at() Method (Array & String)
   ```
   const arr = [10, 20, 30, 40];

   console.log(arr.at(1));   // 20
   console.log(arr.at(-1));  // 40
   ```
   - **Object.hasOwn()** Safer way to check object properties
   - Object.hasOwn() better than obj.hasOwnProperty()
   ```
   const obj = { name: "John" };

   console.log(Object.hasOwn(obj, "name")); // true
   ```
   - Error Cause (error.cause)
   ```
   try {
     JSON.parse("invalid");
   } catch (err) {
     throw new Error("Parsing failed", { cause: err });
   }
   ```

## 🟢 React

1. What is the difference between functional and class components?  
   - Class: Uses `this`, lifecycle methods.  
   - Functional: Uses hooks (`useState`, `useEffect`), simpler syntax.  

1. What is the difference between `useMemo`, `useCallback`, and `React.memo`?  
   - `useMemo`: Memoizes a **calculated value**.  
   - `useCallback`: Memoizes a **function** reference.  
   - `React.memo`: Memoizes a **whole component** to avoid re-renders.

1. What is the difference between `useMemo`, `useCallback`, and `React.memo`?  
   <img width="1268" height="475" alt="image" src="https://github.com/user-attachments/assets/b78c9190-2d18-4b5d-be26-7881d1e09a5f" />
   **useCallback Example**

      ```import React, { useState, useCallback } from "react";
      
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
   **useMemo Exmaple**

      ```import React, { useState, useMemo } from "react";

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

1. What is the difference between client and server components in Next.js?  
   - Client: Run in browser, can use state/effects.  
   - Server: Rendered on server, better performance, can fetch data directly.  

1. Explain SSR, SSG, and ISR in Next.js.  
   - SSR: Rendered on request.  
   - SSG: Rendered at build time.  
   - ISR: Rebuilds pages after interval.
  
1. What are functional components in React?
   - Functional components are JavaScript functions that accept arguments (called props) and return React elements that describe what should appear on the screen.

1. What is an implicit return in functional components?
   - If a component only contains a single return statement, you can skip the return keyword and curly braces by using parentheses:
   - ```javascript
         // Functional component with implicit return
         const MyComponent = () => (
           <h1>Hello, world!</h1>
         );
         export default MyComponent;

1. Why must a React component return a single root element?
   - React requires one root element because the virtual DOM needs a single entry point to represent the component tree.
     
1. Why is JSX not valid JavaScript?
   - Browsers cannot directly interpret JSX. It must be transpiled (commonly by Babel) into JavaScript that React can execute.
  
1. React Elements vs. HTML Elements?
   - | Feature        | React Element                 | HTML Element                      |
     | -------------- | ----------------------------- | --------------------------------- |
     | What it is     | JS object (virtual DOM node)  | Actual DOM node in browser        |
     | Mutability     | Immutable                     | Mutable                           |
     | Created by     | JSX / `React.createElement()` | HTML / `document.createElement()` |
     | Where it lives | In memory (virtual DOM)       | In browser DOM tree               |
     | Purpose        | Describe UI structure         | Display UI structure              |
     
1. What are props in React?
   - Read-only data passed from parent to child to configure components.

1. What is the difference between props and state?
   - Props: Immutable, passed from parent.
   - State: Mutable, managed within the component.

1. Can a child component modify props directly?
   - ❌ No. Props are read-only; children use callback functions to update parent data.

1. What is the children prop used for?
   - To render nested JSX elements inside a component.

1. What is the purpose of defaultProps?
   - To define default values when a prop isn’t passed.
     
1. React Component Lifecycle (Class & Function)
   - What is the Component Lifecycle?
      Every React component goes through a lifecycle of three main phases:

      - Mounting – Component is created and inserted into the DOM.
      - Updating – Component re-renders when props or state change.
      - Unmounting – Component is removed from the DOM.

     These phases allow developers to run code at specific moments, such as fetching data, optimizing performance, or cleaning up resources.
   - Class Component Lifecycle
     Class components use built-in lifecycle methods that get called automatically by React at different phases.
     ```
      | Phase          | Method                              |   Purpose                                | When It Runs                        |
      | -------------- | ----------------------------------- | ---------------------------------------- | ----------------------------------- |
      | Mounting       | `constructor()`                     | Initialize state and bind methods.       | Before component appears on screen. |
      |                | `static getDerivedStateFromProps()` | Sync state from props (rarely used).     | Before every render.                |
      |                | `render()`                          | Return JSX (UI).                         | During render.                      |
      |                | `componentDidMount()`               | Run side effects (fetch, subscriptions). | After first render.                 |
      | Updating       | `shouldComponentUpdate()`           | Optimize by skipping re-renders.         | Before re-render.                   |
      |                | `getSnapshotBeforeUpdate()`         | Capture DOM info before update.          | Before DOM changes.                 |
      |                | `componentDidUpdate()`              | Run side effects after updates.          | After DOM is updated.               |
      | Unmounting     | `componentWillUnmount()`            | Cleanup (timers, listeners, etc).        | Before component is removed.        |

     ```
   - **Example**
     ```
           class MyComponent extends React.Component {
        constructor(props) {
          super(props);
          this.state = { data: null };
        }
      
        componentDidMount() {
          console.log("Mounted");
        }
      
        shouldComponentUpdate(nextProps, nextState) {
          return nextState.data !== this.state.data;
        }
      
        componentDidUpdate() {
          console.log("Updated");
        }
      
        componentWillUnmount() {
          console.log("Unmounted");
        }
      
        render() {
          return <div>{this.state.data}</div>;
        }
      }

     ```

   - Functional Component Lifecycle (with Hooks)
     Functional components don’t have lifecycle methods, but React Hooks provide equivalent behavior — mainly through useEffect() and useLayoutEffect().
     ```
      | **Lifecycle Stage**  | **Class Method**             | **Functional Equivalent (Hooks)**                   |
      | -------------------- | ---------------------------- | --------------------------------------------------- |
      | Mounting             | `componentDidMount()`        | `useEffect(() => { ... }, [])`                      |
      | Updating             | `componentDidUpdate()`       | `useEffect(() => { ... }, [dependencies])`          |
      | Unmounting           | `componentWillUnmount()`     | Cleanup function inside `useEffect()`               |
      | State initialization | `constructor()`              | `useState()`                                        |
      | Derived state        | `getDerivedStateFromProps()` | Logic inside `useEffect()` reacting to prop changes |
     ```
   - **Example:**
     ```
     import React, { useState, useEffect } from "react";

      function MyComponent() {
        const [data, setData] = useState(null);
      
        // componentDidMount + componentDidUpdate
        useEffect(() => {
          console.log("Mounted or Updated");
          setData("Hello React!");
      
          // componentWillUnmount
          return () => {
            console.log("Cleanup before unmount");
          };
        }, []); // empty array = run once (on mount)
      
        return <div>{data}</div>;
      }
     ```
   - **Lifecycle Flow Summary**
     - Class Components
       Mounting → Updating → Unmounting constructor → getDerivedStateFromProps → render → componentDidMount → shouldComponentUpdate → render → getSnapshotBeforeUpdate → componentDidUpdate → componentWillUnmount
     - Functional Components
       Mounting → Updating → Unmounting
       
1. What is the purpose of defaultProps?
    - | Feature         | React Element                         | HTML Element                             |
      | --------------- | ------------------------------------- | ---------------------------------------- |
      | **Type**        | JS Object                             | DOM Node                                 |
      | **Exists in**   | Virtual DOM                           | Real DOM                                 |
      | **Created by**  | `React.createElement()` or JSX        | Browser or `document.createElement()`    |
      | **Mutable?**    | ❌ No — immutable                     | ✅ Yes — mutable                        |
      | **Performance** | Efficient (batch updates via diffing) | Slower when directly modified repeatedly |
      | **Purpose**     | Describe what UI should look like     | Rendered UI on screen                    |

   - **Visualization**
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


1. In React useState is mutable or immutable?
   - useState is immutable in react. React will always expect to create new state not to modify the existing state. If the existing state is modified react might not re-render.
   - A functional update is when you pass a function to the state setter, rather than a new value directly.
   - **The wrong approach (direct mutation)**
 
   ```
   
   import { useState } from 'react';
   
   function ItemList() {
     const [items, setItems] = useState(['apple', 'banana']);
   
     const addItem = () => {
       // 🔴 Wrong: Directly mutating the state array
       items.push('cherry');
       setItems(items);
     };
   
     return (
       <div>
         <button onClick={addItem}>Add Cherry</button>
         <ul>
           {items.map((item, index) => (
             <li key={index}>{item}</li>
           ))}
         </ul>
       </div>
     );
   }
   
   ```
   - **The correct approach (immutability)**
   ```
   import { useState } from 'react';
   
   function ItemList() {
     const [items, setItems] = useState(['apple', 'banana']);
   
     const addItem = () => {
       // ✅ Correct: Creating a new array with the new item
       setItems([...items, 'cherry']);
     };
   
     return (
       <div>
         <button onClick={addItem}>Add Cherry</button>
         <ul>
           {items.map((item, index) => (
             <li key={index}>{item}</li>
           ))}
         </ul>
       </div>
     );
   }
   
   ```
   
1. Event Delegation vs Event Handling — React default method for events

   - **Event Handling (Normal DOM Way)**
     - Event handling means attaching event listeners directly to DOM elements.
     - **Example**
       ```html
       <button onclick="handleClick()">Click Me</button>
       ```
     - **Behaviour**
       - Each element that listens to an event has its own separate listener.
       - For many elements, the browser stores many handlers — this can consume memory and slightly slow performance if there are thousands of nodes.
     - **Pros:**
       - Simple and direct.
       - Works exactly as per browser default event system.
     - **Cons:**
       - Inefficient if many elements need the same event.
       - Harder to manage dynamically added elements.
       - Slightly inconsistent across browsers historically.

   - **Event Delegation**
     - Event Delegation is a pattern where instead of adding many listeners, you add a single listener to a common ancestor and let events bubble up the DOM.
     - **Example**
       ```jsx
       <ul onClick={handleItemClick}>
         <li>Item 1</li>
         <li>Item 2</li>
         <li>Item 3</li>
       </ul>
       ```
     - **Behavior:**
       - The single listener on the `<ul>` handles clicks from any `<li>` inside it.
       - Uses the event bubbling mechanism (event travels from target → ancestors).
     - **Pros:**
       - Much more memory-efficient.
       - Can handle future elements added dynamically.
       - Centralized event control.
     - **Cons:**
       - `event.target` changes based on where the user clicked (may need extra checks).
       - Doesn’t work well if event propagation is stopped early.

   - **Internal Use of Event in React**
     - React attaches a few global event listeners (at the root or document level) instead of attaching one to every element.
     - React does not attach a click listener to the actual `<button>` DOM node.
     - Instead, React attaches a single event listener for all clicks at the top-level container.


1. Controlled vs. Uncontrolled Components.
   - **Controlled Components**
     - In a controlled component, form data is handled by the React component state.
     - The value of the input element is controlled via React’s state (`useState` or `this.state`).
     - Every change in the input field triggers an event handler that updates the state.
     - **Example**
       ```jsx
       import { useState } from "react";

       function ControlledInput() {
         const [name, setName] = useState("");

         const handleChange = (e) => {
           setName(e.target.value);
         };

         const handleSubmit = (e) => {
           e.preventDefault();
           alert(`Submitted name: ${name}`);
         };

         return (
           <form onSubmit={handleSubmit}>
             <input type="text" value={name} onChange={handleChange} />
             <button type="submit">Submit</button>
           </form>
         );
       }

       export default ControlledInput;
       ```
     - **Key Points**
       - React is the single source of truth for form data.
       - Easier to validate and manipulate input values.
       - Slightly more code but better control.

   - **Uncontrolled Components**
     - In an uncontrolled component, form data is handled by the DOM itself.
     - You access the value using `ref` instead of React state.
     - **Example**
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

       export default UncontrolledInput;
       ```
     - **Key Points**
       - DOM manages the data instead of React.
       - Simpler for quick or legacy forms.
       - Harder to validate or sync with other UI states.

   - **Comparison Table**

     | Feature                         | Controlled Component                          | Uncontrolled Component                     |
     |----------------------------------|-----------------------------------------------|--------------------------------------------|
     | Data source                      | React state                                   | DOM (`ref`)                                |
     | Value updated by                 | `onChange` handler                            | User input (DOM)                           |
     | Validation                       | Easy to validate within React                 | Requires manual DOM access                 |
     | Performance                      | May re-render more often                      | Fewer re-renders                           |
     | Use case                         | Complex, dynamic, validated forms             | Simple, non-reactive forms                 |
     | Example hooks                    | `useState`, `useEffect`                       | `useRef`                                   |


1. Tree Shaking?

     - Tree shaking = removing unused code from your bundle
     - Used by bundlers like Webpack, Rollup, and Vite.
    ```
      // math.js
      export const add = (a, b) => a + b;
      export const sub = (a, b) => a - b;
      
      // app.js
      import { add } from "./math";
      
      add(2, 3);
    ```
   
1. Why do we need to build React?
- JSX is actually converted to JavaScript even in development, but the difference is that in development it's not optimized, while in production it is fully optimized for performance.
     - **React code cannot run directly in browser efficiently.**
     - JSX needs compilation → converted by Babel
     - Optimize code → minification, tree shaking
     - Bundle multiple files → using Webpack
     - Support modern JS in old browsers
 
      | Feature        | 🧪 Development Mode             | 🚀 Production Build                          |
      | -------------- | ------------------------------- | -------------------------------------------- |
      | JSX Conversion | Converted instantly (in memory) | Converted during build                       |
      | Performance    | Not optimized                   | Highly optimized                             |
      | Minification   | ❌ No                           | ✅ Yes                                        |
      | Tree Shaking   | ❌ No                           | ✅ Yes (removes unused code)                  |
      | Bundling       | Minimal / on-demand              | Fully bundled & code-split                   |
      | Debugging      | ✅ Warnings, error overlays      | ❌ No debugging info                          |
      | Source Maps    | ✅ Enabled                       | ⚠️ Optional / often disabled                 |
      | Refresh        | ✅ Fast Refresh (HMR)            | ❌ No HMR                                     |
      | Build Output   | Stored in memory                  | Physical optimized files (dist/build folder) |
      | Focus          | Developer Experience              | Performance & Optimization                   |


 1. Lazy Loading?

     - **Load components only when needed**
     - Improves performance by reducing initial bundle.

 1. New Features in React 19
     - **Actions (Server + Client mutations)**
     - **use() Hook**
     - **useOptimistic Hook**
       
## 🟠 Node.JS


1. What is the Node.JS Runtime?
   - Node.js is single-threaded in the sense that the JavaScript execution happens on one thread, but it is multi-threaded under the hood because Libuv manages a thread pool for heavy I/O. This design makes it perfect for I/O-intensive apps (streaming, APIs) but a poor choice for CPU-intensive tasks (image processing, heavy encryption) because those would block the main thread.
  
     <img width="1434" height="718" alt="image" src="https://github.com/user-attachments/assets/cc9fe34c-3d53-47e7-b8d2-5a2b7c8073e3" />
     
1. What is REPL in Node?
   - The REPL functions in a continuous cycle, which is fundamental to how interactive shells work:

      Read: Reads the user's input, parses it into a JavaScript data structure, and stores it in memory.
      
      Eval: Takes the data structure and evaluates the code.
      
      Print: Prints the result of the evaluation to the console.
      
      Loop: Loops the entire process until the user terminates the session.


