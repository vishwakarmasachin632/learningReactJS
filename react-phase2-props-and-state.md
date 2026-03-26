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

---
# React Event Handling & Input Types Guide

---

## 🔥 1. onClick → When & Why we use it

```jsx
<button onClick={handleClick}>Click Me</button>
```

### ✅ Use when:

* User clicks a button
* Trigger action immediately

### 💡 Real use cases:

* Submit button (simple cases)
* Delete item
* Open modal
* Like button ❤️

👉 Your code:

```js
const handleClick = () => {
  alert("Button clicked 🔥");
};
```

✔ Runs only when clicked

---

## 🔥 2. onSubmit → When & Why we use it

```jsx
<form onSubmit={handleSubmit}>
```

### ✅ Use when:

* You are working with forms
* You want to submit data (login, signup, etc.)

---

### ❗ Why `e.preventDefault()`?

```js
const handleSubmit = (e) => {
  e.preventDefault();
};
```

### 🧠 Default Behavior:

When a form submits:

* Page reloads
* Data may be lost

### ❌ Without it:

👉 Page refresh → React state reset

### ✅ With it:

👉 Prevent refresh → React handles everything smoothly

---

### 🔥 Real Example:

```js
const handleSubmit = (e) => {
  e.preventDefault();
  alert("Form handled by React 🚀");
};
```

---

## 🔥 3. onChange → When & Why we use it

```jsx
<input onChange={(e) => setName(e.target.value)} />
```

### ✅ Use when:

* User types in input field
* You want live data

---

### ❗ What is `e.target.value`?

### 🧠 Breakdown:

* `e` → event object
* `e.target` → the element (input field)
* `e.target.value` → what user typed

---

### 🔍 Example:

If user types:

```
Sachin
```

👉 Then:

```js
e.target.value === "Sachin"
```

---

## 🔥 4. What is `e` (event object)?

```js
const handleSubmit = (e) => {}
```

👉 `e` = event object

### It contains:

* what triggered the event
* which element triggered it
* extra info (key press, value, etc.)

💡 Think like this:
👉 `e` = full information about the event

---

## 🧠 Easy Analogy

| Concept            | Real Life Example                |
| ------------------ | -------------------------------- |
| onClick            | Pressing a button                |
| onSubmit           | Submitting a form                |
| onChange           | Typing in a textbox              |
| e                  | Event details (who, what, where) |
| e.target.value     | What user typed                  |
| e.preventDefault() | Stop page refresh                |

---

## 🔥 Flow Understanding (VERY IMPORTANT)

### 👉 Input typing:

User types → onChange → e.target.value → setState → UI updates

### 👉 Form submit:

User clicks submit → onSubmit → preventDefault → custom logic

---

## 🚀 Final Summary

* onClick → simple button action

* onSubmit → form submission

* onChange → input tracking

* e → event object

* e.target.value → input value

* e.preventDefault() → stop page reload

---

# 🔥 Why we use `type`?

Good question 👍 — “why we use type?” depends on where you are using it. In your code, it’s mainly in:

```jsx
<input type="text" />
<button type="submit">Submit</button>
```

---

## 🔥 1. type in `<input>`

```jsx
<input type="text" />
```

### ✅ Why we use it:

`type` tells the browser what kind of input this is

---

### 🧠 Different input types

| Type     | Purpose            |
| -------- | ------------------ |
| text     | Normal text input  |
| password | Hidden text (••••) |
| email    | Email validation   |
| number   | Only numbers       |
| file     | Upload files       |
| checkbox | Select options     |

---

### 💡 Example:

```jsx
<input type="password" />
```

👉 User types → text is hidden

---

## 🔥 2. type in `<button>`

```jsx
<button type="submit">Submit</button>
```

### ✅ Why we use it:

It defines button behavior

---

### 🧠 Button types

| Type   | Behavior      |
| ------ | ------------- |
| submit | Submits form  |
| button | Normal button |
| reset  | Resets form   |

---

### ❗ Important (VERY COMMON MISTAKE)

👉 Default button type inside `<form>` is:

```jsx
type="submit"
```

So this:

```jsx
<button>Click</button>
```

⚠️ Will automatically submit the form!

---

### ✅ Best Practice

Always define type:

```jsx
<button type="button">Click</button>
<button type="submit">Submit</button>
```

---

## 🔥 Real Flow Example

```jsx
<form onSubmit={handleSubmit}>
  <input type="text" />
  <button type="submit">Submit</button>
</form>
```

### Flow:

1. Click button
2. type="submit" triggers form
3. onSubmit runs
4. e.preventDefault() stops reload

---

## 🧠 Final Summary

* type = defines behavior
* In `<input>` → defines data type
* In `<button>` → defines action

---

---
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
