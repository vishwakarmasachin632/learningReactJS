# 🚀 PHASE 3: Conditional Rendering (🔥 MUST MASTER)

Aaj hum cover karenge:
- if/else
- ternary operator
- logical AND (&&)
- switch case (🔥 special concept)
- real use cases

---

## 🔹 1. Conditional Rendering kya hota hai?

👉 UI ko condition ke basis par change karna

### 💡 Real Example:
- Login hai → Dashboard dikhao
- Login nahi → Login page dikhao

---

## 🔹 2. if/else (Outside JSX)

👉 JSX ke andar direct `if` use nahi hota ❌  
👉 JSX ke bahar use hota hai ✅

### ✅ Example:

```jsx
function App() {
  const isLoggedIn = true;

  if (isLoggedIn) {
    return <h1>Welcome User 🔥</h1>;
  } else {
    return <h1>Please Login</h1>;
  }
}
```

### 🤔 Kab use kare?
- Jab complex logic ho
- Multiple lines return karni ho

---

## 🔹 3. Ternary Operator (🔥 Most Used)

👉 JSX ke andar use hota hai

### ✅ Example:

```jsx
function App() {
  const isLoggedIn = false;

  return (
    <div>
      {isLoggedIn ? <h1>Dashboard</h1> : <h1>Login Page</h1>}
    </div>
  );
}
```

### 💡 Real Use:
- Login / Logout
- Dark mode toggle
- Button text change

---

## 🔹 4. Logical AND (&&)

👉 Jab sirf ek condition true ho tab show karna ho

### ✅ Example:

```jsx
function App() {
  const isAdmin = true;

  return (
    <div>
      <h1>Welcome</h1>
      {isAdmin && <h2>Admin Panel 🔐</h2>}
    </div>
  );
}
```

### 🤔 Kab use kare?
👉 Optional UI show karna ho, jaise:
- Admin panel
- Notifications
- Badge

---

## 🔹 5. Switch Case Rendering (🔥 IMPORTANT)

👉 Direct JSX me switch nahi use hota  
👉 Function ke through use karte hai

### ✅ Example:

```jsx
function App() {
  const role = "admin";

  const renderUI = () => {
    switch (role) {
      case "admin":
        return <h1>Admin Dashboard 🔥</h1>;

      case "user":
        return <h1>User Dashboard</h1>;

      default:
        return <h1>Guest</h1>;
    }
  };

  return <div>{renderUI()}</div>;
}
```

### 🔥 Real Use Cases:
- Role-based UI
- Status-based UI
- Multi-condition logic

---

## 🔹 6. Multiple Conditions (Real Example)

```jsx
function App() {
  const status = "loading";

  return (
    <div>
      {status === "loading" && <h2>Loading...</h2>}
      {status === "success" && <h2>Data Loaded ✅</h2>}
      {status === "error" && <h2>Error ❌</h2>}
    </div>
  );
}
```

---

## 🔥 Pro Tip (Interview Level)

👉 Nested ternary avoid karo ❌  
👉 Code unreadable ho jata hai

**❌ Bad:**
```jsx
isLoggedIn ? isAdmin ? <Admin /> : <User /> : <Login />
```

**✅ Better:**
```jsx
if (!isLoggedIn) return <Login />;
if (isAdmin) return <Admin />;
return <User />;
```

---

## 🎯 Real Mini Project (🔥 Must Practice)

### ✅ Login Toggle UI

```jsx
import { useState } from "react";

function App() {
  const [isLoggedIn, setIsLoggedIn] = useState(false);

  return (
    <>
      <button onClick={() => setIsLoggedIn(!isLoggedIn)}>
        Toggle Login
      </button>

      {isLoggedIn ? (
        <h1>Welcome Back 🔥</h1>
      ) : (
        <h1>Please Login</h1>
      )}
    </>
  );
}
```

---

## 📌 Summary (Aaj kya seekha)

| # | Method | Kab use kare |
|---|--------|--------------|
| ✔ | if/else | Complex logic |
| ✔ | ternary | Most used, JSX ke andar |
| ✔ | && | Single condition show/hide |
| ✔ | switch | Multiple cases / roles |

---

## ⚡ Practice Task

**👉 1.** Role UI banao:
- `admin` → Admin Panel
- `user` → User Panel
- `guest` → Guest

**👉 2.** Loading UI:
- `loading` → "Loading..."
- `success` → "Data Loaded"

**👉 3.** Button toggle:
- Show / Hide text

---

## 🚀 NEXT PHASE

Agla part 🔥:

👉 Lists & Keys (map function)  
👉 Dynamic UI rendering  
👉 Real data show karna

---

> 💬 **Ready hai next level ke liye?**  
> Lists & Keys ke saath real dynamic UI banayenge 💯
