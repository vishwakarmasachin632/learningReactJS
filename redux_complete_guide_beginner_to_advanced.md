# 🚀 Redux Complete Guide (React Developer Roadmap)

## 📌 1. Redux Kya Hai?
Redux ek **state management library** hai jo large applications me data ko manage karne ke liye use hoti hai.

### 🤔 Problem Without Redux
- Props drilling (parent → child → child → child)
- Data management messy ho jata hai
- Multiple components me same data sync karna difficult

### ✅ Redux Solution
- Global Store (single source of truth)
- Predictable state updates
- Easy debugging

---

## 📌 2. Kab Redux Use Karna Chahiye?

### ❌ Redux mat use karo jab:
- Small app ho
- Simple state ho (useState/useContext enough ho)

### ✅ Redux use karo jab:
- Multiple components me same data share ho
- Complex state logic ho
- Authentication, cart system, dashboard ho

---

## 📌 3. Real Life Example

### 🛒 E-commerce App
- Cart data har component me chahiye
- Navbar me count
- Cart page me items

👉 Solution: Redux store me cart store karo

---

## 📌 4. Redux Core Concepts

### 1️⃣ Store
👉 Pure application ka data yahan hota hai

### 2️⃣ Action
👉 Object jo batata hai "kya hua"

```js
{ type: "ADD_TO_CART", payload: item }
```

### 3️⃣ Reducer
👉 Function jo state update karta hai

```js
function cartReducer(state = [], action) {
  switch (action.type) {
    case "ADD_TO_CART":
      return [...state, action.payload];
    default:
      return state;
  }
}
```

### 4️⃣ Dispatch
👉 Action ko trigger karta hai

```js
dispatch({ type: "ADD_TO_CART", payload: product });
```

---

## 📌 5. Redux Flow

Component → Dispatch → Action → Reducer → Store Update → UI Re-render

---

## 📌 6. Redux Toolkit (Recommended Way)

Redux Toolkit modern aur easy way hai Redux use karne ka.

### Install

```bash
npm install @reduxjs/toolkit react-redux
```

---

## 📌 7. Store Setup

```js
import { configureStore } from '@reduxjs/toolkit'
import cartReducer from './cartSlice'

export const store = configureStore({
  reducer: {
    cart: cartReducer
  }
})
```

---

## 📌 8. Slice (Important Concept)

Slice = Reducer + Actions together

```js
import { createSlice } from '@reduxjs/toolkit'

const cartSlice = createSlice({
  name: 'cart',
  initialState: [],
  reducers: {
    addItem: (state, action) => {
      state.push(action.payload)
    },
    removeItem: (state, action) => {
      return state.filter(item => item.id !== action.payload)
    }
  }
})

export const { addItem, removeItem } = cartSlice.actions
export default cartSlice.reducer
```

---

## 📌 9. React Me Use Karna

### Provider Setup

```js
import { Provider } from 'react-redux'
import { store } from './store'

<Provider store={store}>
  <App />
</Provider>
```

---

### useDispatch & useSelector

```js
import { useDispatch, useSelector } from 'react-redux'
import { addItem } from './cartSlice'

function Product() {
  const dispatch = useDispatch()
  const cart = useSelector(state => state.cart)

  return (
    <>
      <button onClick={() => dispatch(addItem({ id: 1, name: 'Phone' }))}>
        Add to Cart
      </button>
      <p>Total Items: {cart.length}</p>
    </>
  )
}
```

---
# 🧠 useDispatch & useSelector (Redux Hooks Explained)

---

## 🧠 1. `useDispatch` — “Action bhejne ke liye”

👉 Iska use hota hai **Redux store ko update karne ke liye**

### 📌 Simple language:

> “Bhai store me change karna hai → dispatch use karo”

---

### ✅ Example:

```js
import { useDispatch } from "react-redux";
import { addItem } from "./cartSlice";

function Product() {
  const dispatch = useDispatch();

  return (
    <button onClick={() => dispatch(addItem({ id: 1, name: "Phone" }))}>
      Add to Cart
    </button>
  );
}
```

### 🔥 Kya ho raha hai?

* Button click hua
* `dispatch` action bhej raha hai
* reducer state update karega

---

## 🧠 2. `useSelector` — “Data lene ke liye”

👉 Iska use hota hai **Redux store se data read karne ke liye**

### 📌 Simple language:

> “Store me kya data hai → useSelector se uthao”

---

### ✅ Example:

```js
import { useSelector } from "react-redux";

function Navbar() {
  const cart = useSelector((state) => state.cart);

  return <h1>Items: {cart.length}</h1>;
}
```

### 🔥 Kya ho raha hai?

* Store se `cart` data liya
* UI me show kiya
* Jab state change hogi → auto re-render

---

## ⚡ Dono ka relation (Flow)

```
useDispatch → Action bhejta hai → Store update hota hai
useSelector → Updated data read karta hai → UI update hoti hai
```

---

## 🛒 Real-Life Example (E-commerce)

### 👇 Situation:

* Product page → item add karega
* Navbar → cart count dikhayega

### 🔁 Flow:

1. Product page → `useDispatch` → item add
2. Store update
3. Navbar → `useSelector` → updated count show

---

## 🧩 Ek hi component me dono use

```js
import { useDispatch, useSelector } from "react-redux";
import { addItem } from "./cartSlice";

function App() {
  const dispatch = useDispatch();
  const cart = useSelector((state) => state.cart);

  return (
    <>
      <button onClick={() => dispatch(addItem({ id: 1 }))}>
        Add
      </button>
      <p>Total: {cart.length}</p>
    </>
  );
}
```

---

## ❌ Common Mistakes

❌ `useSelector(state => state)` → pura store mat uthao
✅ `useSelector(state => state.cart)` → specific lo

❌ Dispatch directly call mat karo render me
✅ Event handler me use karo

---

## 🎯 Short Summary

| Hook          | Use                        |
| ------------- | -------------------------- |
| `useDispatch` | Store update karne ke liye |
| `useSelector` | Store se data lene ke liye |


---
## 📌 10. Async Operations (API Calls)

```js
import { createAsyncThunk, createSlice } from '@reduxjs/toolkit'

export const fetchProducts = createAsyncThunk(
  'products/fetch',
  async () => {
    const res = await fetch('https://api.example.com/products')
    return res.json()
  }
)

const productSlice = createSlice({
  name: 'products',
  initialState: { data: [], loading: false },
  extraReducers: (builder) => {
    builder
      .addCase(fetchProducts.pending, (state) => {
        state.loading = true
      })
      .addCase(fetchProducts.fulfilled, (state, action) => {
        state.loading = false
        state.data = action.payload
      })
  }
})
```

---

## 📌 11. Folder Structure

```
src/
 ├── app/
 │    └── store.js
 ├── features/
 │    ├── cart/
 │    │     └── cartSlice.js
 │    ├── product/
 │          └── productSlice.js
```

---

## 📌 12. Best Practices

✅ Redux Toolkit use karo
✅ Slice small rakho
✅ Logic reducers me rakho
❌ Direct state mutate mat karo (except Toolkit)

---

## 📌 13. Redux vs Context API

| Feature | Redux | Context |
|--------|------|--------|
| Large apps | ✅ | ❌ |
| Performance | ✅ | ❌ |
| Setup | Complex | Easy |

---
## 📌 14. Interview Questions

### ❓ Redux kya hai?

Redux ek **state management library** hai jo React applications me global state ko manage karne ke liye use hoti hai.
Iska main purpose hai data ko predictable aur centralized banana (single source of truth).

---

### ❓ Action vs Reducer?

#### 🔹 Action:

* Ek **object** hota hai jo batata hai *kya hua*
* Isme `type` aur optional `payload` hota hai

```js
{ type: "ADD_TO_CART", payload: item }
```

#### 🔹 Reducer:

* Ek **function** hota hai jo decide karta hai state kaise update hogi
* Current state + action → new state return karta hai

```js
function cartReducer(state = [], action) {
  switch (action.type) {
    case "ADD_TO_CART":
      return [...state, action.payload];
    default:
      return state;
  }
}
```

---

### ❓ Redux Toolkit kya hai?

Redux Toolkit ek **official recommended way** hai Redux use karne ka.

#### ✅ Benefits:

* Boilerplate code kam karta hai
* Easy setup (`configureStore`)
* Slice concept (actions + reducer together)
* Built-in support for async (createAsyncThunk)

---

### ❓ useSelector vs useDispatch?

| Hook          | Use                                                    |
| ------------- | ------------------------------------------------------ |
| `useSelector` | Store se data read karne ke liye                       |
| `useDispatch` | Store ko update karne ke liye (actions bhejne ke liye) |

#### 🔹 Example:

```js
const dispatch = useDispatch();
const cart = useSelector((state) => state.cart);

dispatch(addItem({ id: 1 }));
```

---

### 🎯 Short Trick (Interview Me Bolne Ke Liye)

* Redux = Global State Manager
* Action = What happened
* Reducer = How state changes
* useSelector = Get data
* useDispatch = Update data

---


---

## 📌 15. Summary

Redux ek powerful tool hai jo complex applications me state management ko easy banata hai.

👉 Agar app bada hai → Redux use karo
👉 Agar small hai → useState/useContext enough

---

## 🎯 Next Steps

- Redux DevTools use karo
- Middleware samjho (Thunk)
- Advanced patterns seekho

---

🔥 Happy Coding Bhai!

