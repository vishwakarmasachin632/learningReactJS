# 🚀 PHASE 2: Props & State (CORE)

Aaj hum cover karenge:
- Props
- State (useState)
- Props vs State
- Event Handling

---

## 🔹 1. Props (Data Passing)

👉 Props = Parent → Child data bhejne ka tareeka

### ✅ Example:

**👨‍👦 Parent Component (App.jsx)**
```jsx
function App() {
  return <User name="Sachin" age={22} />;
}
```

**👶 Child Component (User.jsx)**
```jsx
function User(props) {
  return (
    <h1>
      Name: {props.name}, Age: {props.age}
    </h1>
  );
}

export default User;
```

**💡 Output:**
```
Name: Sachin, Age: 22
```

---

### 🔥 Modern Way (Destructuring)

```jsx
function User({ name, age }) {
  return <h1>{name} - {age}</h1>;
}
```

### 🤔 Kyu use karte hai?
- Dynamic UI
- Reusable components
- Data pass karne ke liye

---

## 🔹 2. State (useState Hook) 🔥🔥

👉 State = Component ke andar ka data (jo change hota hai)  
👉 Hook use karte hai: `useState`

### ✅ Example: Counter App

```jsx
import { useState } from "react";

function Counter() {
  const [count, setCount] = useState(0);

  return (
    <>
      <h1>Count: {count}</h1>

      <button onClick={() => setCount(count + 1)}>
        Increase
      </button>
    </>
  );
}
```

### 🔄 Kaise kaam karta hai?

```jsx
const [count, setCount] = useState(0);
```

| Part | Kya hai |
|------|---------|
| `count` | current value |
| `setCount` | update function |
| `0` | initial value |

### 💡 Real Use Case:
- Like button 👍
- Cart items 🛒
- Form input

---

## 🔹 3. Props vs State (🔥 Interview Question)

| Feature | Props | State |
|---------|-------|-------|
| Data source | Parent | Component khud |
| Mutable? | ❌ No | ✅ Yes |
| Purpose | Data pass | Data manage |

### 🧠 Simple samajh:
> 👉 **Props** = input &nbsp;&nbsp; 👉 **State** = memory

---

## 🔹 4. Event Handling 🔥

👉 React me events handle karte hai like:
- `onClick`
- `onChange`
- `onSubmit`

### ✅ Example: Button Click

```jsx
function ClickExample() {
  const handleClick = () => {
    alert("Button clicked 🔥");
  };

  return <button onClick={handleClick}>Click Me</button>;
}
```

### ✅ Input Handling

```jsx
import { useState } from "react";

function InputExample() {
  const [name, setName] = useState("");

  return (
    <>
      <input
        type="text"
        onChange={(e) => setName(e.target.value)}
      />

      <h2>Hello {name}</h2>
    </>
  );
}
```

🔥 **Important:**  
👉 `e.target.value` = input ka current value

---

## 🔹 5. Combine Everything (Mini App 🔥)

```jsx
import { useState } from "react";

function App() {
  const [name, setName] = useState("");

  return (
    <>
      <h1>Welcome {name}</h1>

      <input
        type="text"
        placeholder="Enter name"
        onChange={(e) => setName(e.target.value)}
      />

      <button onClick={() => setName("")}>
        Clear
      </button>
    </>
  );
}

export default App;
```

### 🎯 Real-Life Understanding
> 👉 User input → State me store  
> 👉 UI automatically update → React magic ✨

---

## 📌 Summary (Aaj kya seekha)

| # | Topic |
|---|-------|
| ✔ | Props (data pass karna) |
| ✔ | useState (state manage karna) |
| ✔ | Props vs State |
| ✔ | Event handling |

---

## ⚡ Practice Task (Important)

**👉 1.** Counter App bana (Increase + Decrease)

**👉 2.** Input field bana:
- Name enter karo
- Live display ho

**👉 3.** Ek component bana:
```jsx
<User name="Aman" />
<User name="Rahul" />
```

---

## 🚀 NEXT PHASE (🔥 MOST IMPORTANT)

Agla part me:

👉 Conditional Rendering 🔥🔥  
👉 if/else  
👉 ternary  
👉 &&  
👉 switch case

---

> 💬 **Ready hai next level ke liye?**  
> Next part me aur bhi powerful concepts aane wale hai 💯
