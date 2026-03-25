# 🚀 PHASE 6: Hooks (🔥 Core of React)

Aaj hum cover karenge:
- useEffect (🔥 most important)
- useRef
- useContext
- Custom Hooks

---

## 🔹 1. useEffect (🔥🔥 MOST IMPORTANT)

👉 Side effects handle karne ke liye use hota hai

### 🤔 Side Effect kya hota hai?
👉 Jo UI render ke alawa hota hai:
- API call
- Timer
- DOM update
- Event listeners

### ✅ Basic Syntax:

```jsx
useEffect(() => {
  // code here
}, []);
```

---

### 🔥 Example 1: Run only once (Mounting)

```jsx
import { useEffect } from "react";

function App() {
  useEffect(() => {
    console.log("Component Loaded 🚀");
  }, []);

  return <h1>Hello</h1>;
}
```

👉 `[]` = sirf ek baar run hota hai

---

### 🔥 Example 2: Run on state change

```jsx
import { useState, useEffect } from "react";

function App() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    console.log("Count changed:", count);
  }, [count]);

  return (
    <>
      <h1>{count}</h1>
      <button onClick={() => setCount(count + 1)}>+</button>
    </>
  );
}
```

---

### 🔥 Example 3: API Call

```jsx
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    fetch("https://jsonplaceholder.typicode.com/users")
      .then(res => res.json())
      .then(data => setUsers(data));
  }, []);

  return (
    <>
      {users.map(user => (
        <h3 key={user.id}>{user.name}</h3>
      ))}
    </>
  );
}
```

---

### ⚠️ Dependency Array — Samajh Le (Important!)

| Dependency Array | Kab run hoga |
|-----------------|--------------|
| `[]` | Sirf ek baar (on mount) |
| `[state]` | Jab bhi woh state change ho |
| No array | Har render pe 😵 (avoid karo) |

---

## 🔹 2. useRef (🔥 Underrated but Powerful)

👉 Value store karta hai **WITHOUT re-render**

### ✅ Example:

```jsx
import { useRef } from "react";

function App() {
  const inputRef = useRef();

  const focusInput = () => {
    inputRef.current.focus();
  };

  return (
    <>
      <input ref={inputRef} />
      <button onClick={focusInput}>Focus</button>
    </>
  );
}
```

### 💡 Use Cases:
- Input focus
- DOM access
- Previous value store

---

## 🔹 3. useContext (🔥 Prop Drilling ka Solution)

👉 Global data share karne ke liye

### 🤔 Problem (Prop Drilling):
> Parent → Child → Child → Child (props pass karte rehna 😵)

### ✅ Solution:

```jsx
import { createContext, useContext } from "react";

const UserContext = createContext();

function App() {
  return (
    <UserContext.Provider value="Sachin">
      <Child />
    </UserContext.Provider>
  );
}

function Child() {
  const user = useContext(UserContext);
  return <h1>Hello {user}</h1>;
}
```

### 💡 Use Cases:
- User data
- Theme (dark/light)
- Auth system

---

## 🔹 4. Custom Hooks (🔥 Advanced but Easy)

👉 Apna khud ka hook banana

### ✅ Hook banana:

```jsx
import { useState } from "react";

function useCounter() {
  const [count, setCount] = useState(0);

  const increase = () => setCount(count + 1);

  return { count, increase };
}
```

### ✅ Hook use karna:

```jsx
function App() {
  const { count, increase } = useCounter();

  return (
    <>
      <h1>{count}</h1>
      <button onClick={increase}>+</button>
    </>
  );
}
```

### 🔥 Kyu use kare?
- Code reuse
- Clean code
- Logic separate karna

---

## 🎯 Real Understanding — Hooks Cheatsheet

| Hook | Kaam |
|------|------|
| `useState` | Data store karna |
| `useEffect` | Side effects handle karna |
| `useRef` | DOM/value store (no re-render) |
| `useContext` | Global data share karna |
| Custom Hook | Reusable logic banana |

---

## ⚠️ Common Mistakes

| ❌ Mistake | ✅ Fix |
|-----------|--------|
| `useEffect` infinite loop | Dependency array sahi rakho |
| Dependency array galat | Sirf required states daalo |
| State inside loop | Hooks sirf top-level pe likhte hai |

---

## 📌 Summary (Aaj kya seekha)

| # | Topic |
|---|-------|
| ✔ | useEffect → side effects |
| ✔ | useRef → no re-render storage |
| ✔ | useContext → global state |
| ✔ | Custom Hook → reusable logic |

---

## ⚡ Practice Task (🔥 MUST)

**👉 1.** API fetch karo — users list show karo  
**👉 2.** Button click pe input focus karo (`useRef`)  
**👉 3.** Theme context banao (dark / light)  
**👉 4.** Custom counter hook banao — `useCounter`

---

## 🚀 NEXT PHASE

Agla part 🔥:

👉 Lifecycle (simple way)  
👉 Styling in React  
👉 CSS Modules  
👉 Styled Components

---

> 💬 **Ready hai next level ke liye?**  
> Real app styling aur lifecycle ke saath React aur powerful banega 🔥💯
