# 🚀 PHASE 1: BASICS (Foundation Strong Kar)

Aaj hum ye cover karenge:
- What is React
- SPA
- Virtual DOM
- Vite Setup
- Folder Structure
- JSX
- Components

---

## 🔹 1. What is React?

👉 React ek JavaScript library hai UI banane ke liye.  
👉 **Created by:** Meta

### 🤔 Kyu use karte hai?
- Fast UI updates
- Reusable components
- Large apps easily manage kar sakte

### 💡 Real-life example:
> Instagram / Facebook ka UI → React se bana hota hai

---

## 🔹 2. SPA (Single Page Application)

👉 SPA = ek hi page reload bina change hota hai

❌ **Traditional Website:**
- Har click pe page reload

✅ **React SPA:**
- Page reload nahi hota
- Sirf content change hota hai

### 💡 Example:
> Login → Dashboard (without reload)

👉 Isse performance fast hoti hai ⚡

---

## 🔹 3. Virtual DOM

👉 React directly browser DOM ko update nahi karta  
👉 Pehle ek Virtual copy (Virtual DOM) banata hai

### 🔄 Flow:
1. State change hota hai
2. Virtual DOM update hota hai
3. React compare karta hai **(Diffing)**
4. Sirf changed part update hota hai

### 🤔 Kyu important?
👉 Fast rendering  
👉 Performance optimized

---

## 🔹 4. Setup React using Vite 🔥

**Step 1:** Create project
```bash
npm create vite@latest my-app
```

**Step 2:**
```bash
cd my-app
npm install
npm run dev
```

👉 Browser me open:
```
http://localhost:5173
```

---

## 🔹 5. Folder Structure (Simple samajh)

```
my-app/
 ├── public/
 ├── src/
 │   ├── assets/
 │   ├── App.jsx
 │   ├── main.jsx
 │   └── components/
 ├── package.json
```

**Important files:**
- `main.jsx` → entry point
- `App.jsx` → main component

---

## 🔹 6. JSX (JavaScript XML)

👉 JSX = JavaScript + HTML

```jsx
const element = <h1>Hello Bhai 👋</h1>;
```

### Rules:

❌ `class` → nahi &nbsp;&nbsp; ✅ `className` use karo

```jsx
<div className="box">Hello</div>
```

### Dynamic JSX

```jsx
const name = "Sachin";

return <h1>Hello {name}</h1>;
```

👉 `{}` ke andar JS likhte hai

---
# JSX vs TSX

In React development:

- **JSX** = JavaScript + HTML-like syntax
- **TSX** = TypeScript + JSX

They are file formats used mainly in React applications.

---

## Main Difference

| JSX | TSX |
|---|---|
| Uses JavaScript | Uses TypeScript |
| No type safety | Strong type safety |
| Easier for beginners | Better for large apps |
| Errors found at runtime | Errors found during development(compile time) |

---

## JSX Example

```jsx
function User(props) {
  return <h1>{props.name}</h1>;
}
```
### TSX Example

```tsx
type UserProps = {
  name: string;
};

function User({ name }: UserProps) {
  return <h1>{name}</h1>;
}
```
---

## 🔹 7. Components (🔥 Core Concept)

👉 React ka heart = Components  
👉 UI ko small parts me tod dete hai

### ✅ Functional Component (Most Important)

```jsx
function Header() {
  return <h1>Welcome Bhai 🔥</h1>;
}

export default Header;
```

**Use:**
```jsx
import Header from "./Header";

function App() {
  return <Header />;
}
```

---

### 🧠 Class Component (Basic idea only)

```jsx
import React, { Component } from "react";

class Header extends Component {
  render() {
    return <h1>Hello Class Component</h1>;
  }
}
```

👉 Aajkal mostly **functional components + hooks** use hote hai

---
# 🔹 1. Pehle kya tha? (Class Components)

Earlier in React, we used class components:

```jsx
class MyComponent extends React.Component {
  render() {
    return <h1>Hello</h1>;
  }
}
```

👉 Problem kya thi?

* `this` keyword ka confusion 😵
* Boilerplate code zyada
* State manage karna complex
* Lifecycle methods (`componentDidMount` etc.) yaad rakhne padte the

---

# 🔹 2. Ab kya use ho raha hai? (Functional Components)

Now we use functional components + Hooks

```jsx
function MyComponent() {
  return <h1>Hello</h1>;
}
```

Aur state bhi manage kar sakte ho:

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

---

# 🔥 3. Why Functional Components are Preferred?

## ✅ 1. Simple & Clean

* No `this`
* Less code
* Easy to read

---

## ✅ 2. Hooks ne game change kar diya

Hooks (like `useState`, `useEffect`) ne class components ki need almost khatam kar di

👉 Example:

* `componentDidMount` ❌
* `useEffect` ✅

---

## ✅ 3. Better Reusability

Custom hooks bana sakte ho:

```js
function useFetchData() {
  // reusable logic
}
```

👉 Ye class me mushkil tha

---

## ✅ 4. Performance (thoda better)

* Functional components lightweight hote hain
* Aur modern optimizations (like memoization) easily apply hote hain

---

## ✅ 5. Industry Standard

Aaj ke time me:

* New projects → Functional components only
* Companies expect Hooks knowledge

---

## ✅ 6. Easier Testing & Debugging

* Functions predictable hote hain
* Debug karna easy hota hai

---

# 🔴 4. Kya Class Components useless ho gaye?

👉 Nahi, but rarely used

Use cases:

* Old legacy projects
* Error boundaries (ab hooks se bhi aa gaya hai)

---

# 🧠 Final Simple Line

👉 Functional components use hote hain because:

> **"They are simpler, cleaner, and powerful due to Hooks."**

---

### 🔥 Important Concept: Component Reusability

```jsx
function Card() {
  return <h2>Product Card</h2>;
}

function App() {
  return (
    <>
      <Card />
      <Card />
      <Card />
    </>
  );
}
```

👉 Same component multiple baar use kar sakte ho

---
# 🔄 React Component Lifecycle

## What is Component Lifecycle?

Component lifecycle means the different stages a React component goes through from creation to removal.

In simple words:

> Component lifecycle is the journey of a component from mounting on the screen, updating, and finally unmounting.

---

# Main Phases of Component Lifecycle

React component lifecycle has mainly 3 phases:

```text
1. Mounting
2. Updating
3. Unmounting
```

---

# 1. Mounting Phase

## What is Mounting?

Mounting means the component is created and shown on the screen for the first time.

Simple words:

> When a component appears on the UI for the first time, it is called mounting.

---

## Example

```jsx
function App() {
  return <h1>Hello React</h1>;
}
```

When this component is displayed in the browser for the first time, it is mounted.

---

## Functional Component Mounting Example

```jsx
import { useEffect } from "react";

function Welcome() {
  useEffect(() => {
    console.log("Component mounted");
  }, []);

  return <h1>Welcome to React</h1>;
}

export default Welcome;
```

### Explanation

```jsx
useEffect(() => {
  console.log("Component mounted");
}, []);
```

Here, empty dependency array `[]` means this code runs only once when the component mounts.

---

# 2. Updating Phase

## What is Updating?

Updating means the component re-renders when its state or props change.

Simple words:

> When data changes and React updates the UI again, it is called updating.

---

## Updating happens when:

- State changes
- Props change
- Parent component re-renders

---

## Functional Component Updating Example

```jsx
import { useEffect, useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Component updated because count changed");
  }, [count]);

  return (
    <div>
      <h1>Count: {count}</h1>
      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </div>
  );
}

export default Counter;
```

### Explanation

```jsx
useEffect(() => {
  console.log("Component updated because count changed");
}, [count]);
```

This code runs whenever `count` changes.

---

# 3. Unmounting Phase

## What is Unmounting?

Unmounting means the component is removed from the screen.

Simple words:

> When a component is removed from the UI, it is called unmounting.

---

## Functional Component Unmounting Example

```jsx
import { useEffect } from "react";

function Timer() {
  useEffect(() => {
    const timer = setInterval(() => {
      console.log("Timer running");
    }, 1000);

    return () => {
      clearInterval(timer);
      console.log("Component unmounted");
    };
  }, []);

  return <h1>Timer Component</h1>;
}

export default Timer;
```

### Explanation

```jsx
return () => {
  clearInterval(timer);
  console.log("Component unmounted");
};
```

This return function is called a cleanup function.

It runs when the component is removed from the screen.

---

# Lifecycle in Functional Components

In functional components, lifecycle is handled using the `useEffect` hook.

| Lifecycle Phase | Functional Component |
|---|---|
| Mounting | `useEffect(() => {}, [])` |
| Updating | `useEffect(() => {}, [dependency])` |
| Unmounting | Cleanup function inside `useEffect` |

---
---

## 📌 Summary (Aaj kya seekha)

| # | Topic |
|---|-------|
| ✔ | React kya hai |
| ✔ | SPA ka concept |
| ✔ | Virtual DOM |
| ✔ | Vite setup |
| ✔ | JSX basics |
| ✔ | Components |

---

## 🚀 NEXT PART (Bohot Important)

Agla part me hum cover karenge:

👉 Props  
👉 useState (🔥 most important)  
👉 Event Handling  
👉 Props vs State

---

## ⚡ Tera Task (Practice)

**1.** Ek simple component bana:
```jsx
function Welcome() {
  return <h1>Hello React 🚀</h1>;
}
```

**2.** App me use kar

**3.** Ek aur component bana:
```jsx
function Footer() {
  return <p>Footer Section</p>;
}
```
---
# Default Export vs Named Export

## Difference Table

| Point | Default Export | Named Export |
|---|---|---|
| Number of exports | Only one default export per file | Multiple named exports per file |
| Import syntax | Without `{}` | With `{}` |
| Import name | Can use any name | Must use exact exported name |
| Best for | Main component of a file | Multiple components/functions |
| Example export | `export default Header` | `export { Header }` |
| Example import | `import Header from "./Header"` | `import { Header } from "./Header"` |

---

## One-line Answer

> Default export allows one main export per file and can be imported with any name, while named export allows multiple exports and must be imported with the exact name using curly braces.
---
# 🚀 React Phase 1: Important Interview Questions and Answers

## Topics Covered

- What is React
- SPA
- Virtual DOM
- Vite Setup
- Folder Structure
- JSX
- JSX vs TSX
- Components
- Functional Components vs Class Components
- Component Reusability

---

# 🔹 1. What is React?

## Q1. What is React?

### Answer

React is a **JavaScript library** used to build user interfaces.

In simple words:

> React is used to build the frontend UI of web applications.

React mainly follows a component-based approach.

### Example

```jsx
function App() {
  return <h1>Hello React</h1>;
}

export default App;
```

### Interview Answer

> React is a JavaScript library used for building fast, interactive, and reusable user interfaces. It is mainly used for frontend development and follows a component-based architecture.

---

## Q2. Is React a library or a framework?

### Answer

React is a **JavaScript library**, not a full framework.

A library means:

> React mainly focuses on building the UI/view layer of an application.

Frameworks like Angular provide a complete structure, but React mainly handles the user interface.

### Interview Answer

> React is a JavaScript library, not a framework. It mainly focuses on building the view layer or UI part of an application.

---

## Q3. Who created React?

### Answer

React was created by **Facebook**, now known as **Meta**.

It is used in popular applications like Facebook and Instagram.

### Interview Answer

> React was created by Facebook, now Meta. It is widely used for building fast and interactive user interfaces.

---

## Q4. What is the main purpose of React?

### Answer

The main purpose of React is to build:

- Fast user interfaces
- Reusable UI components
- Interactive web applications
- Maintainable frontend code

React divides the UI into small reusable parts called components.

### Example

```jsx
function Header() {
  return <h1>This is Header</h1>;
}

function Footer() {
  return <p>This is Footer</p>;
}
```

### Interview Answer

> The main purpose of React is to build fast, reusable, and interactive user interfaces using components.

---

## Q5. Why do we use React?

### Answer

We use React because it makes frontend development easier and more efficient.

| Reason | Explanation |
|---|---|
| Fast UI updates | React updates only the required part of the UI |
| Reusable components | Same component can be used multiple times |
| Easy maintenance | Code is divided into small components |
| Large app support | Big applications can be managed easily |
| Strong community | React has a large ecosystem and community |

### Interview Answer

> We use React because it helps us build fast, reusable, and maintainable user interfaces. It uses components and Virtual DOM to improve performance and code organization.

---

# 🔹 2. SPA - Single Page Application

## Q6. What is SPA?

### Answer

SPA stands for **Single Page Application**.

In a SPA, the application loads a single HTML page, and after that, only the required content changes dynamically.

In simple words:

> In SPA, the full page does not reload on every click. Only the content changes.

### Example

```text
Login → Dashboard
```

This navigation can happen without a full page reload.

### Interview Answer

> SPA stands for Single Page Application. It loads a single web page and updates content dynamically without refreshing the entire page.

---

## Q7. What is the difference between a traditional website and a SPA?

### Answer

| Traditional Website | Single Page Application |
|---|---|
| Full page reloads on every click | Page does not reload fully |
| Server sends a new HTML page | Same page updates dynamically |
| Can feel slower | Provides faster user experience |
| More server requests | Fewer full-page reloads |
| Example: Old websites | Example: Gmail, Facebook, React apps |

### Interview Answer

> In a traditional website, every navigation reloads the full page. In a SPA, only the required content changes dynamically without reloading the complete page.

---

## Q8. Why is SPA fast?

### Answer

SPA is fast because:

1. It does not reload the full page.
2. Only the required content updates.
3. JavaScript updates the UI in the browser.
4. User experience becomes smoother.

### Interview Answer

> SPA is fast because it does not reload the entire page. It updates only the required part of the UI dynamically using JavaScript.

---

# 🔹 3. Virtual DOM

## Q9. What is Virtual DOM?

### Answer

Virtual DOM is a lightweight copy of the real browser DOM.

React does not directly update the real DOM first.  
It first updates the Virtual DOM.

In simple words:

> Virtual DOM is a temporary copy of the real DOM that React uses to compare changes.

### Interview Answer

> Virtual DOM is a lightweight copy of the real DOM. React uses it to compare UI changes and update only the required part of the real DOM.

---

## Q10. Why does React not directly update the real DOM?

### Answer

Updating the real DOM directly can be slow.

So React follows this process:

1. First, it updates the Virtual DOM.
2. Then, it compares the old Virtual DOM and new Virtual DOM.
3. Finally, it updates only the changed part in the real DOM.

This process improves performance.

### Interview Answer

> React does not directly update the real DOM because direct DOM manipulation can be slow. React uses Virtual DOM to find changes efficiently and update only the necessary part of the real DOM.

---

## Q11. Explain the Virtual DOM flow.

### Answer

```text
State changes
        ↓
Virtual DOM updates
        ↓
React compares old Virtual DOM and new Virtual DOM
        ↓
Diffing happens
        ↓
Only the changed part updates in the Real DOM
```

### Interview Answer

> When state changes, React creates a new Virtual DOM, compares it with the old Virtual DOM using diffing, and updates only the changed part in the real DOM.

---

## Q12. What is diffing in React?

### Answer

Diffing is the process where React compares the old Virtual DOM with the new Virtual DOM.

In simple words:

> Diffing means finding the difference between the old UI and the new UI.

### Interview Answer

> Diffing is the process where React compares the old Virtual DOM with the new Virtual DOM and finds the minimum changes required to update the real DOM.

---

## Q13. How does Virtual DOM improve performance?

### Answer

Virtual DOM improves performance because React does not update the complete page.

React updates only the part of the UI where the change happened.

### Example

```jsx
const [count, setCount] = useState(0);
```

If `count` changes, React updates only the UI related to `count`.

### Interview Answer

> Virtual DOM improves performance by reducing direct real DOM manipulation. React compares changes in the Virtual DOM and updates only the changed part in the real DOM.

---

# 🔹 4. Vite Setup

## Q14. What is Vite?

### Answer

Vite is a modern frontend build tool used to create and run frontend projects quickly.

In simple words:

> Vite helps us create and run React applications faster.

### Interview Answer

> Vite is a modern frontend build tool that provides a fast development server and quick project setup for React applications.

---

## Q15. How do you create a React app using Vite?

### Answer

Step 1: Create project

```bash
npm create vite@latest my-app
```

Step 2: Go inside the project folder

```bash
cd my-app
```

Step 3: Install dependencies

```bash
npm install
```

Step 4: Run the app

```bash
npm run dev
```

Open in browser:

```text
http://localhost:5173
```

### Interview Answer

> To create a React app using Vite, we use `npm create vite@latest my-app`, then install dependencies using `npm install`, and run the project using `npm run dev`.

---

## Q16. What is the use of `npm create vite@latest my-app`?

### Answer

This command creates a new Vite project.

```bash
npm create vite@latest my-app
```

Here, `my-app` is the project name.

### Interview Answer

> `npm create vite@latest my-app` is used to create a new Vite project with the given project name.

---

## Q17. What does `npm install` do?

### Answer

`npm install` installs all required project dependencies.

These dependencies are installed inside the `node_modules` folder.

### Example

```bash
npm install
```

### Interview Answer

> `npm install` installs all dependencies mentioned in the `package.json` file.

---

## Q18. What does `npm run dev` do?

### Answer

`npm run dev` starts the development server.

After running this command, the React app runs in the browser.

Default Vite URL:

```text
http://localhost:5173
```

### Interview Answer

> `npm run dev` starts the Vite development server and runs the React application locally.

---

# 🔹 5. React Folder Structure

## Q19. What is the basic folder structure of a React project?

### Answer

```text
my-app/
 ├── public/
 ├── src/
 │   ├── assets/
 │   ├── App.jsx
 │   ├── main.jsx
 │   └── components/
 ├── package.json
```

### Interview Answer

> A basic React project contains folders like `public`, `src`, `assets`, and files like `main.jsx`, `App.jsx`, and `package.json`.

---

## Q20. What is the role of `main.jsx`?

### Answer

`main.jsx` is the entry point of a React application.

It renders the main `App` component inside the root element of the HTML page.

### Example

```jsx
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App.jsx";

ReactDOM.createRoot(document.getElementById("root")).render(
  <App />
);
```

### Interview Answer

> `main.jsx` is the entry point of a React application. It renders the root component, usually `App`, into the browser DOM.

---

## Q21. What is the role of `App.jsx`?

### Answer

`App.jsx` is the main component of a React application.

Usually, other components are imported and used inside `App.jsx`.

### Example

```jsx
function App() {
  return (
    <div>
      <h1>Welcome to React</h1>
    </div>
  );
}

export default App;
```

### Interview Answer

> `App.jsx` is the main component of a React application where the main UI structure is defined and other components are used.

---

## Q22. Why do we create a `components` folder?

### Answer

We create a `components` folder to store reusable UI components.

### Example

```text
components/
 ├── Header.jsx
 ├── Footer.jsx
 └── Card.jsx
```

### Benefits

- Code remains organized
- Components become reusable
- Maintenance becomes easier

### Interview Answer

> The `components` folder is used to store reusable UI components and keep the project structure clean and organized.

---

## Q23. What is the use of the `assets` folder?

### Answer

The `assets` folder is used to store static files such as:

- Images
- Icons
- CSS files
- Fonts
- Logos

### Example

```text
assets/
 ├── logo.png
 ├── banner.jpg
 └── style.css
```

### Interview Answer

> The `assets` folder is used to store static resources like images, icons, logos, fonts, and stylesheets.

---

# 🔹 6. JSX

## Q24. What is JSX?

### Answer

JSX stands for **JavaScript XML**.

JSX allows us to write HTML-like syntax inside JavaScript.

### Example

```jsx
const element = <h1>Hello React</h1>;
```

In simple words:

> JSX = JavaScript + HTML-like syntax

### Interview Answer

> JSX is a syntax extension for JavaScript that allows us to write HTML-like code inside JavaScript. It is commonly used in React to describe UI.

---

## Q25. Why do we use `className` instead of `class` in JSX?

### Answer

In JavaScript, `class` is a reserved keyword.

So, in JSX, we use `className` to apply CSS classes.

Wrong:

```jsx
<div class="box">Hello</div>
```

Correct:

```jsx
<div className="box">Hello</div>
```

### Interview Answer

> In JSX, we use `className` instead of `class` because `class` is a reserved keyword in JavaScript.

---

## Q26. How do you display dynamic values in JSX?

### Answer

We use curly braces `{}` to display dynamic values in JSX.

### Example

```jsx
const name = "Sachin";

function App() {
  return <h1>Hello {name}</h1>;
}
```

Output:

```text
Hello Sachin
```

### Interview Answer

> In JSX, dynamic values are displayed using curly braces `{}`.

---

## Q27. What is the use of `{}` in JSX?

### Answer

In JSX, `{}` is used to write JavaScript expressions.

### Example

```jsx
const age = 22;

return <p>Age is {age}</p>;
```

We can also write expressions:

```jsx
return <p>Total: {10 + 20}</p>;
```

### Interview Answer

> Curly braces `{}` in JSX are used to embed JavaScript expressions inside HTML-like JSX code.

---

# 🔹 7. JSX vs TSX

## Q28. What is the difference between JSX and TSX?

### Answer

| JSX | TSX |
|---|---|
| Used with JavaScript | Used with TypeScript |
| No strong type safety | Provides strong type safety |
| Easier for beginners | Better for large applications |
| Errors are mostly found at runtime | Errors can be found during development/compile time |

### Interview Answer

> JSX is used with JavaScript, while TSX is used with TypeScript. TSX provides type safety, which makes it better for large applications.

---

## Q29. Why is TSX better for large applications?

### Answer

TSX is better for large applications because TypeScript provides type safety.

### Example

```tsx
type UserProps = {
  name: string;
};

function User({ name }: UserProps) {
  return <h1>{name}</h1>;
}
```

If we pass a value other than a string to `name`, TypeScript can show an error during development.

### Interview Answer

> TSX is better for large applications because it provides type safety, reduces runtime errors, and makes the code easier to maintain.

---

# 🔹 8. Components

## Q30. What is a React component?

### Answer

A component is a reusable block of UI in React.

In simple words:

> A component is a small part of the UI that can be reused in multiple places.

### Example

```jsx
function Header() {
  return <h1>Welcome</h1>;
}

export default Header;
```

### Interview Answer

> A React component is a reusable piece of UI. React applications are built by combining multiple components.

---

## Q31. Why are components called the heart of React?

### Answer

React applications are built using components.

### Example

```text
App
 ├── Header
 ├── Sidebar
 ├── ProductCard
 └── Footer
```

That is why components are considered the core concept of React.

### Interview Answer

> Components are called the heart of React because the entire UI is divided into small reusable components.

---

## Q32. What is a functional component?

### Answer

A functional component is a simple JavaScript function that returns JSX.

### Example

```jsx
function Welcome() {
  return <h1>Hello React</h1>;
}

export default Welcome;
```

### Interview Answer

> A functional component is a JavaScript function that returns JSX. Modern React mainly uses functional components with hooks.

---

## Q33. How do you import and use a component?

### Answer

Create `Header.jsx`:

```jsx
function Header() {
  return <h1>Welcome</h1>;
}

export default Header;
```

Use it inside `App.jsx`:

```jsx
import Header from "./Header";

function App() {
  return <Header />;
}

export default App;
```

### Interview Answer

> We import a component using the `import` statement and use it like an HTML tag inside JSX.

---

## Q34. Why should component names start with a capital letter?

### Answer

In React, component names should start with a capital letter.

Correct:

```jsx
function Header() {
  return <h1>Hello</h1>;
}
```

Reason:

> React treats lowercase tags as HTML elements and uppercase tags as custom components.

### Interview Answer

> Component names should start with a capital letter because React identifies uppercase tags as custom components and lowercase tags as normal HTML elements.

---

# 🔹 9. Functional Component vs Class Component

## Q35. What is a class component?

### Answer

A class component is the older way of creating components in React.

### Example

```jsx
import React, { Component } from "react";

class Header extends Component {
  render() {
    return <h1>Hello Class Component</h1>;
  }
}

export default Header;
```

### Interview Answer

> A class component is a React component created using a JavaScript class. It uses the `render()` method to return JSX.

---

## Q36. What is the difference between functional and class components?

### Answer

| Functional Component | Class Component |
|---|---|
| It is a JavaScript function | It is a JavaScript class |
| Less code | More boilerplate code |
| No `this` keyword | Uses `this` keyword |
| Uses hooks | Uses lifecycle methods |
| Preferred in modern React | Mostly found in legacy projects |

### Interview Answer

> Functional components are simple JavaScript functions that return JSX, while class components are JavaScript classes that use the `render()` method. Modern React prefers functional components because they are simpler and support hooks.

---

## Q37. Why are functional components preferred today?

### Answer

Functional components are preferred because:

1. They are simple and clean.
2. There is no `this` keyword confusion.
3. They support hooks.
4. They require less boilerplate code.
5. They are easier to test and debug.
6. They are the industry standard.

### Interview Answer

> Functional components are preferred because they are simpler, cleaner, and powerful due to hooks like `useState` and `useEffect`.

---

## Q38. What were the problems with class components?

### Answer

Problems with class components:

- Confusion with the `this` keyword
- More boilerplate code
- Complex state management
- Lifecycle methods were harder to remember
- Code readability was lower

### Interview Answer

> Class components had issues like `this` keyword confusion, more boilerplate code, complex lifecycle methods, and lower readability.

---

# 🔹 10. Hooks Basics

## Q39. What are Hooks?

### Answer

Hooks are special functions in React that allow functional components to use state and lifecycle features.

### Example

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return <button onClick={() => setCount(count + 1)}>{count}</button>;
}
```

### Interview Answer

> Hooks are special functions in React that allow functional components to use features like state and side effects.

---

## Q40. What is `useState`?

### Answer

`useState` is a React Hook used to manage state in functional components.

### Example

```jsx
const [count, setCount] = useState(0);
```

| Part | Meaning |
|---|---|
| `count` | Current state value |
| `setCount` | Function used to update the state |
| `0` | Initial value |

### Interview Answer

> `useState` is a React Hook that allows us to add and manage state inside functional components.

---

## Q41. What is `useEffect`?

### Answer

`useEffect` is a React Hook used to handle side effects.

Examples of side effects:

- API call
- Timer
- Console log
- DOM update
- Data fetching

### Example

```jsx
useEffect(() => {
  console.log("Component mounted");
}, []);
```

### Interview Answer

> `useEffect` is a React Hook used to perform side effects in functional components, such as API calls, timers, and data fetching.

---

# 🔹 11. Component Reusability

## Q42. What is component reusability?

### Answer

Component reusability means using the same component in multiple places.

### Example

```jsx
function Card() {
  return <h2>Product Card</h2>;
}

function App() {
  return (
    <>
      <Card />
      <Card />
      <Card />
    </>
  );
}
```

Here, the same `Card` component is used three times.

### Interview Answer

> Component reusability means creating a component once and using it multiple times in different parts of the application.

---

## Q43. What are the benefits of reusable components?

### Answer

| Benefit | Explanation |
|---|---|
| Less code duplication | We do not need to write the same code again and again |
| Easy maintenance | Updating one component updates it everywhere |
| Clean code | Code remains organized |
| Faster development | We can build UI quickly by reusing components |

### Interview Answer

> Reusable components reduce code duplication, improve maintainability, keep the code clean, and make development faster.

---

# 🔹 12. Practical Interview Questions

## Q44. Create a simple Welcome component.

### Answer

```jsx
function Welcome() {
  return <h1>Hello React 🚀</h1>;
}

export default Welcome;
```

---

## Q45. Create a Footer component.

### Answer

```jsx
function Footer() {
  return <p>Footer Section</p>;
}

export default Footer;
```

---

## Q46. Use Welcome and Footer inside App.

### Answer

```jsx
import Welcome from "./Welcome";
import Footer from "./Footer";

function App() {
  return (
    <>
      <Welcome />
      <Footer />
    </>
  );
}

export default App;
```

---

# ✅ Most Important Interview Questions

## Q1. What is React?

React is a JavaScript library used for building user interfaces.

---

## Q2. What is SPA?

SPA stands for Single Page Application. It updates content dynamically without reloading the full page.

---

## Q3. What is Virtual DOM?

Virtual DOM is a lightweight copy of the real DOM. React uses it to compare changes and update only the changed part of the real DOM.

---

## Q4. What is JSX?

JSX stands for JavaScript XML. It allows us to write HTML-like syntax inside JavaScript.

---

## Q5. What are components?

Components are reusable UI blocks in React.

---

## Q6. Why are functional components preferred?

Functional components are preferred because they are simple, clean, and powerful due to hooks.

---

## Q7. What is `useState`?

`useState` is a React Hook used to manage state in functional components.

---

## Q8. What is the role of `main.jsx`?

`main.jsx` is the entry point of a React application. It renders the `App` component into the DOM.

---

## Q9. What is the role of `App.jsx`?

`App.jsx` is the main component of a React application where other components are usually used.

---

## Q10. Why is React fast?

React is fast because it uses Virtual DOM and updates only the changed part of the real DOM.

---

# Best Interview Flow Answer

```text
React is a JavaScript library used for building fast and interactive user interfaces.

React applications are component-based, which means the UI is divided into small reusable parts.

React supports SPA, which means the page does not reload completely and only the required content changes.

React uses Virtual DOM to improve performance. When state changes, React updates the Virtual DOM, compares it with the previous version using diffing, and updates only the changed part in the real DOM.

JSX allows us to write HTML-like syntax inside JavaScript. In JSX, we use className instead of class and use curly braces to write JavaScript expressions.

Modern React mainly uses functional components because they are simple, clean, and support hooks like useState and useEffect.
```
---

> 💬 **Ready hai next level ke liye? (Props + useState 🔥)**  
> Next part me real project type example ke sath samjhaunga 💯
