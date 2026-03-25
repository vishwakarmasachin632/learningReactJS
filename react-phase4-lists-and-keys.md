# 🚀 PHASE 4: Lists & Keys

Aaj hum cover karenge:
- map() function
- list rendering
- keys kya hote hai
- real examples

---

## 🔹 1. List Rendering kya hota hai?

👉 Multiple items ko UI me show karna

### 💡 Example:
- Users list
- Products
- Tasks

---

## 🔹 2. map() Function (🔥 MOST IMPORTANT)

👉 Array ko loop karke UI generate karta hai

### ✅ Basic Example:

```jsx
function App() {
  const users = ["Sachin", "Rahul", "Aman"];

  return (
    <div>
      {users.map((user) => (
        <h2>{user}</h2>
      ))}
    </div>
  );
}
```

### 💡 Output:
```
Sachin
Rahul
Aman
```

---

## 🔹 3. Keys kya hote hai? (🔥 Interview Question)

👉 Har list item ko unique identify karne ke liye use hota hai

**❌ Without key (Warning aayega)**
```jsx
{users.map((user) => (
  <h2>{user}</h2>
))}
```

**✅ With key**
```jsx
{users.map((user, index) => (
  <h2 key={index}>{user}</h2>
))}
```

### 🔥 Best Practice:
👉 Index avoid karo (agar possible ho) — unique `id` use karo

```jsx
const users = [
  { id: 1, name: "Sachin" },
  { id: 2, name: "Rahul" }
];

{users.map((user) => (
  <h2 key={user.id}>{user.name}</h2>
))}
```

---

## 🔹 4. Real Object Example 🔥

```jsx
function App() {
  const products = [
    { id: 1, name: "Laptop", price: 50000 },
    { id: 2, name: "Phone", price: 20000 }
  ];

  return (
    <div>
      {products.map((p) => (
        <div key={p.id}>
          <h2>{p.name}</h2>
          <p>Price: ₹{p.price}</p>
        </div>
      ))}
    </div>
  );
}
```

---

## 🔹 5. Conditional Rendering inside map 🔥

```jsx
const users = [
  { id: 1, name: "Sachin", isAdmin: true },
  { id: 2, name: "Rahul", isAdmin: false }
];

{users.map((user) => (
  <div key={user.id}>
    <h2>{user.name}</h2>
    {user.isAdmin && <p>Admin 🔐</p>}
  </div>
))}
```

---

## 🔹 6. Dynamic List (State + map) 🔥

```jsx
import { useState } from "react";

function App() {
  const [tasks, setTasks] = useState(["Task 1", "Task 2"]);

  return (
    <div>
      {tasks.map((task, index) => (
        <h3 key={index}>{task}</h3>
      ))}
    </div>
  );
}
```

---

## 🔹 7. Add Item in List (🔥 Real Use)

```jsx
import { useState } from "react";

function App() {
  const [tasks, setTasks] = useState([]);
  const [input, setInput] = useState("");

  const addTask = () => {
    setTasks([...tasks, input]);
    setInput("");
  };

  return (
    <>
      <input
        value={input}
        onChange={(e) => setInput(e.target.value)}
      />

      <button onClick={addTask}>Add</button>

      {tasks.map((task, index) => (
        <h3 key={index}>{task}</h3>
      ))}
    </>
  );
}
```

---

## 🔥 Real Understanding

| Concept | Matlab |
|---------|--------|
| `map` | loop — array se UI banao |
| `key` | identity — React ko help karta hai |
| `state + map` | dynamic UI — real-time update |

---

## ⚠️ Common Mistakes

| ❌ Mistake | ✅ Fix |
|-----------|--------|
| `key` bhool jana | Har list item pe `key` lagao |
| `index` use karna jab `id` available ho | Unique `id` use karo |
| Directly array mutate karna | `setTasks([...tasks, newItem])` use karo |

---

## 📌 Summary (Aaj kya seekha)

| # | Topic |
|---|-------|
| ✔ | map() → list render |
| ✔ | key → unique identity |
| ✔ | dynamic UI → state + map |

---

## ⚡ Practice Task (🔥 MUST)

**👉 1.** User List banao:
```js
[
  { id: 1, name: "Sachin" },
  { id: 2, name: "Aman" }
]
```

**👉 2.** Task App:
- Input field
- Add button
- List display

**👉 3.** Show only Admin users (conditional rendering + map combine karo)

---

## 🚀 NEXT PHASE

Agla part 🔥:

👉 Forms Handling  
👉 Controlled Components  
👉 Multiple Inputs  
👉 Validation

---

> 💬 **Ready hai next level ke liye?**  
> Forms me real-world input handling sikhenge 💯
