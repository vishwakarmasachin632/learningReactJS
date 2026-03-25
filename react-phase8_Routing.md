# 🚀 PHASE 8: Routing (🔥 MUST for Projects)

Bhai 🔥 ab tu React ka real app level pe aa gaya hai  
👉 Routing (React Router) = Multi-page app banane ka core 🔥

---

## 📚 Aaj hum cover karenge:

- React Router kya hai  
- Setup  
- BrowserRouter  
- Routes & Route  
- useNavigate  
- useParams  
- Real mini project  

---

## 🔹 1. React Router kya hai?

👉 React SPA hota hai (single page)  
👉 But hume multiple pages ka feel chahiye  

👉 Ye kaam karta hai:  
👉 React Router  

💡 Example:

```
/ → Home
/about → About
/contact → Contact
```

---

## 🔹 2. Install React Router

```bash
npm install react-router-dom
```

---

## 🔹 3. Basic Setup 🔥

### ✅ main.jsx

```js
import React from "react";
import ReactDOM from "react-dom/client";
import App from "./App";
import { BrowserRouter } from "react-router-dom";

ReactDOM.createRoot(document.getElementById("root")).render(
  <BrowserRouter>
    <App />
  </BrowserRouter>
);
```

---

## 🔹 4. Routes & Route

### ✅ App.jsx

```js
import { Routes, Route } from "react-router-dom";

function Home() {
  return <h1>Home Page 🏠</h1>;
}

function About() {
  return <h1>About Page ℹ️</h1>;
}

function Contact() {
  return <h1>Contact Page 📞</h1>;
}

function App() {
  return (
    <Routes>
      <Route path="/" element={<Home />} />
      <Route path="/about" element={<About />} />
      <Route path="/contact" element={<Contact />} />
    </Routes>
  );
}

export default App;
```

---

## 🔹 5. Navigation (Link)

👉 Page reload avoid karne ke liye `<Link>` use hota hai  

### ✅ Example:

```js
import { Link } from "react-router-dom";

function Navbar() {
  return (
    <>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>
      <Link to="/contact">Contact</Link>
    </>
  );
}
```

---

## 🔹 6. useNavigate (🔥 Programmatic Navigation)

👉 Button click pe redirect  

### ✅ Example:

```js
import { useNavigate } from "react-router-dom";

function Home() {
  const navigate = useNavigate();

  return (
    <button onClick={() => navigate("/about")}>
      Go to About
    </button>
  );
}
```

---

## 🔹 7. useParams (🔥 Dynamic Routing)

👉 URL se data lena  

### ✅ Route:

```js
<Route path="/user/:id" element={<User />} />
```

### ✅ Component:

```js
import { useParams } from "react-router-dom";

function User() {
  const { id } = useParams();

  return <h1>User ID: {id}</h1>;
}
```

💡 Example:

👉 /user/101 → show 101  

---

## 🔥 8. Real Mini Project (🔥 Must Try)

```js
import { BrowserRouter, Routes, Route, Link } from "react-router-dom";

function Home() {
  return <h1>Home</h1>;
}

function About() {
  return <h1>About</h1>;
}

function App() {
  return (
    <BrowserRouter>
      <Link to="/">Home</Link>
      <Link to="/about">About</Link>

      <Routes>
        <Route path="/" element={<Home />} />
        <Route path="/about" element={<About />} />
      </Routes>
    </BrowserRouter>
  );
}
```

---

## 🎯 Real Use Cases

👉 Dashboard navigation  
👉 E-commerce pages  
👉 User profile pages  
👉 Admin panel  

---

## ⚠️ Common Mistakes

- ❌ `<a>` tag use karna (page reload ho jayega)  
- ❌ BrowserRouter wrap bhool jana  
- ❌ wrong path  

---

## 📌 Summary

✔ React Router → navigation  
✔ Routes/Route → pages define  
✔ Link → navigation without reload  
✔ useNavigate → redirect  
✔ useParams → dynamic data  

---

## ⚡ Practice Task (🔥 MUST)

👉 1. 3 pages banao:  
- Home  
- About  
- Contact  

👉 2. Navbar banao  

👉 3. Dynamic route:  
- /user/1, /user/2  

👉 4. Button click → navigate karo  

---

## 🚀 NEXT PHASE (🔥 ADVANCED)

Agla part:

👉 State Management (Context API 🔥)  
👉 Redux (basic idea)  
👉 API Handling (fetch + axios)  

---

💬 Bol bhai: next kare? (State Management + API 🔥)
