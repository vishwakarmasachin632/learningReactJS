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

> 💬 **Ready hai next level ke liye? (Props + useState 🔥)**  
> Next part me real project type example ke sath samjhaunga 💯
