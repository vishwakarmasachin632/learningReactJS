# 🚀 PHASE 7: Lifecycle + Styling

Aaj hum cover karenge:

- Lifecycle (simple way)
- useEffect se lifecycle samajhna
- Styling methods (CSS, Inline, Modules, Styled Components)

---

## 🔹 1. Lifecycle kya hota hai?

👉 Component ka life cycle (janam → update → khatam 😄)

### 🔄 3 Phases:

#### 1️⃣ Mounting
👉 Component first time render hota hai

#### 2️⃣ Updating
👉 State / props change hone par re-render

#### 3️⃣ Unmounting
👉 Component remove ho jata hai

---

## 🔥 useEffect se Lifecycle samajh

### ✅ Mounting (run once)
```js
import { useEffect } from "react";

useEffect(() => {
  console.log("Component mounted 🚀");
}, []);
```

### ✅ Updating
```js
useEffect(() => {
  console.log("Updated 🔄");
}, [count]);
```

### ✅ Unmounting (cleanup)
```js
useEffect(() => {
  return () => {
    console.log("Component removed ❌");
  };
}, []);
```

---

## 💡 Real Example (Timer)

```js
import { useEffect, useState } from "react";

function Timer() {
  const [count, setCount] = useState(0);

  useEffect(() => {
    const interval = setInterval(() => {
      setCount(prev => prev + 1);
    }, 1000);

    return () => clearInterval(interval); // cleanup
  }, []);

  return <h1>{count}</h1>;
}
```

---

## 🔹 2. Styling in React 🎨

👉 UI banane ke liye styling must hai

---

### 🔸 Method 1: Normal CSS

#### ✅ CSS file
```css
/* styles.css */
.box {
  background: black;
  color: white;
  padding: 10px;
}
```

#### ✅ Use
```js
import "./styles.css";

<div className="box">Hello</div>
```

---

### 🔸 Method 2: Inline Styling

```js
<div style={{ color: "red", fontSize: "20px" }}>
  Hello
</div>
```

⚠️ Rules:
- camelCase use karo (fontSize)
- object format me likho

---

### 🔸 Method 3: CSS Modules (🔥 Scoped CSS)

👉 Class clash problem solve karta hai

#### ✅ File:
```css
styles.module.css

.box {
  color: blue;
}
```

#### ✅ Use:
```js
import styles from "./styles.module.css";

<div className={styles.box}>Hello</div>
```

---

### 🔸 Method 4: Styled Components (🔥 Advanced)

👉 CSS inside JS

#### Install:
```bash
npm install styled-components
```

#### ✅ Example:
```js
import styled from "styled-components";

const Button = styled.button`
  background: black;
  color: white;
  padding: 10px;
`;

function App() {
  return <Button>Click Me</Button>;
}
```

---

## 🎯 Kab kya use kare?

| Method  | Use Case              |
|--------|----------------------|
| CSS    | Simple projects      |
| Inline | Quick styles         |
| Modules| Medium projects      |
| Styled | Large scalable apps  |

---

## 🔥 Real Mini UI Example

```js
function App() {
  return (
    <div className="card">
      <h2>Product</h2>
      <button>Buy Now</button>
    </div>
  );
}
```

---

## 💡 Real-Life Understanding

👉 Lifecycle = component ka life  
👉 Styling = UI ka look  

---

## ⚠️ Common Mistakes

- ❌ cleanup bhool jana (memory leak)
- ❌ inline styling overuse
- ❌ global CSS conflicts

---

## 📌 Summary

✔ Lifecycle → mounting/updating/unmounting  
✔ useEffect → lifecycle control  
✔ CSS methods → multiple ways  

---

## ⚡ Practice Task (🔥 MUST)

👉 1. Timer app banao  
👉 2. CSS module use karke card design karo  
👉 3. Styled button bana  

---

## 🚀 NEXT PHASE (🔥 PROJECT LEVEL)

Agla part:

👉 React Router (🔥 must for apps)  
👉 Navigation  
👉 Dynamic routes  
👉 useNavigate / useParams  
