# 🚀 PHASE 9: State Management + API Handling

Aaj hum cover karenge:

- Context API (🔥 important)
- Redux (basic idea)
- API calls (fetch + axios)
- Loading & Error handling

---

## 🔹 1. Context API (🔥 Global State)

👉 Jab data ko multiple components me share karna ho  

🤔 Problem:

👉 Props drilling 😵  

App → Child → Child → Child  

✅ Solution: Context API  

### Step 1: Create Context

```js
import { createContext } from "react";

export const UserContext = createContext();
```

### Step 2: Provider

```js
import { UserContext } from "./UserContext";

function App() {
  return (
    <UserContext.Provider value="Sachin">
      <Child />
    </UserContext.Provider>
  );
}
```

### Step 3: Consume

```js
import { useContext } from "react";
import { UserContext } from "./UserContext";

function Child() {
  const user = useContext(UserContext);

  return <h1>Hello {user}</h1>;
}
```

🔥 Use Cases:

👉 Auth (login user)  
👉 Theme (dark/light)  
👉 Language  

---

## 🔹 2. Redux (Basic Idea 🧠)

👉 Jab app bada ho jata hai  

### 🧠 Concept:

- Store → data  
- Action → kya karna hai  
- Reducer → kaise change hoga  

### Flow:

Component → Dispatch → Reducer → Store → UI update  

💡 Example (conceptual):

```js
dispatch({ type: "INCREMENT" });
```

👉 Redux powerful hai but  
👉 Small projects → Context API enough ✅  

---

## 🔹 3. API Handling (🔥 Real World)

👉 Backend se data lana  

---

### 🔸 Method 1: fetch()

```js
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

### 🔸 Method 2: axios (🔥 Better)

👉 Install:

```bash
npm install axios
```

```js
import axios from "axios";
import { useEffect, useState } from "react";

function App() {
  const [users, setUsers] = useState([]);

  useEffect(() => {
    axios
      .get("https://jsonplaceholder.typicode.com/users")
      .then(res => setUsers(res.data));
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

## 🔥 fetch vs axios

| Feature   | fetch | axios |
|----------|------|-------|
| Built-in | ✅   | ❌    |
| JSON auto| ❌   | ✅    |
| Easy syntax | ❌ | ✅   |

---

## 🔹 4. Loading & Error Handling 🔥

```js
import { useEffect, useState } from "react";
import axios from "axios";

function App() {
  const [users, setUsers] = useState([]);
  const [loading, setLoading] = useState(true);
  const [error, setError] = useState("");

  useEffect(() => {
    axios.get("https://jsonplaceholder.typicode.com/users")
      .then(res => {
        setUsers(res.data);
        setLoading(false);
      })
      .catch(() => {
        setError("Something went wrong ❌");
        setLoading(false);
      });
  }, []);

  if (loading) return <h2>Loading... ⏳</h2>;
  if (error) return <h2>{error}</h2>;

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

## 🎯 Real Understanding

👉 Context = global state  
👉 Redux = large app state  
👉 API = backend data  
👉 Loading/Error = UX improve  

---

## ⚠️ Common Mistakes

- ❌ API inside render  
- ❌ loading handle na karna  
- ❌ error ignore karna  

---

## 📌 Summary

✔ Context API → global data  
✔ Redux → large apps  
✔ fetch/axios → API calls  
✔ loading/error → better UX  

---

## ⚡ Practice Task (🔥 MUST)

👉 1. API fetch karo (users)  
👉 2. Loading & error show karo  
👉 3. Context me user store karo  
👉 4. Multiple components me use karo  

---

## 🚀 FINAL PHASE (🔥 LAST STEP)

Agla part:

👉 Performance Optimization  
👉 React.memo  
👉 useMemo  
👉 useCallback  

---

💬 Bol bhai: last phase kare? (Performance 🔥)
