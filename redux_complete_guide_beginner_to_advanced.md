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
# 🎯 Redux Top 30 Objective Questions (MCQs)

---

## ✅ 1. Redux ka main purpose kya hai?

A. UI design karna
B. State manage karna
C. API call karna
D. Routing

**Answer:** B
**Explanation:** Redux ka primary role global state ko manage karna hai taaki data consistent aur predictable rahe.

---

## ✅ 2. Redux me data kaha store hota hai?

A. Component
B. Local storage
C. Store
D. Reducer

**Answer:** C
**Explanation:** Store Redux ka central container hota hai jahan poora application state rakha jata hai.

---

## ✅ 3. Redux ka "single source of truth" kya hai?

A. Action
B. Reducer
C. Store
D. Dispatch

**Answer:** C
**Explanation:** Store hi ek jagah hoti hai jahan se pura app state access karta hai.

---

## ✅ 4. Action kya hota hai?

A. Function
B. Object
C. Array
D. Class

**Answer:** B
**Explanation:** Action ek plain object hota hai jo batata hai kya event hua.

---

## ✅ 5. Action me kaunsa field mandatory hota hai?

A. payload
B. type
C. data
D. value

**Answer:** B
**Explanation:** `type` field action ko uniquely identify karta hai.

---

## ✅ 6. Reducer kya return karta hai?

A. Old state
B. New state
C. Action
D. Component

**Answer:** B
**Explanation:** Reducer hamesha updated (new) state return karta hai.

---

## ✅ 7. Reducer ka type kya hota hai?

A. Object
B. Function
C. Class
D. Array

**Answer:** B
**Explanation:** Reducer ek pure function hota hai.

---

## ✅ 8. Dispatch ka use kya hai?

A. State read karna
B. Action bhejna
C. UI render karna
D. API call

**Answer:** B
**Explanation:** Dispatch function action ko store tak bhejta hai.

---

## ✅ 9. Redux flow kya hai?

A. Reducer → Action → Store
B. Component → Action → Reducer → Store
C. Store → Reducer → Component
D. Action → Store → Reducer

**Answer:** B
**Explanation:** Component action dispatch karta hai, reducer process karta hai, store update hota hai.

---

## ✅ 10. Redux me state immutable hoti hai?

A. Yes
B. No

**Answer:** A
**Explanation:** State directly change nahi hoti, naya state create hota hai.

---

## ✅ 11. Redux Toolkit kya hai?

A. Library
B. Framework
C. Official toolset
D. API

**Answer:** C
**Explanation:** Redux Toolkit official recommended package hai jo Redux ko simplify karta hai.

---

## ✅ 12. configureStore kis package se aata hai?

A. redux
B. react-redux
C. @reduxjs/toolkit
D. axios

**Answer:** C
**Explanation:** Modern Redux setup ke liye ye function Redux Toolkit me hota hai.

---

## ✅ 13. Slice kya hota hai?

A. Component
B. Reducer + Actions
C. API
D. Hook

**Answer:** B
**Explanation:** Slice me reducer aur uske actions ek jagah define hote hain.

---

## ✅ 14. createSlice ka use kya hai?

A. API call
B. Store banana
C. Reducer + Action banana
D. UI banana

**Answer:** C
**Explanation:** Ye boilerplate kam karta hai aur actions + reducer ek sath banata hai.

---

## ✅ 15. useSelector ka use kya hai?

A. Data bhejna
B. Data read karna
C. API call
D. Dispatch karna

**Answer:** B
**Explanation:** Store se data lene ke liye use hota hai.

---

## ✅ 16. useDispatch ka use kya hai?

A. Data read karna
B. State delete karna
C. Action bhejna
D. UI update

**Answer:** C
**Explanation:** Store ko update karne ke liye action dispatch karta hai.

---

## ✅ 17. Provider ka use kya hai?

A. API call
B. Store ko app me provide karna
C. Reducer banana
D. Hook banana

**Answer:** B
**Explanation:** React app ko Redux store se connect karta hai.

---

## ✅ 18. Redux me async kaise handle hota hai?

A. useState
B. createAsyncThunk
C. useEffect
D. map

**Answer:** B
**Explanation:** Async operations ke liye Redux Toolkit me ye helper use hota hai.

---

## ✅ 19. createAsyncThunk kya return karta hai?

A. Object
B. Promise lifecycle actions
C. Array
D. Function only

**Answer:** B
**Explanation:** Ye pending, fulfilled, rejected actions generate karta hai.

---

## ✅ 20. Redux me kaun state ko modify karta hai?

A. Component
B. Reducer
C. Action
D. Store

**Answer:** B
**Explanation:** Sirf reducer hi state update logic define karta hai.

---

## ✅ 21. Redux DevTools ka use kya hai?

A. UI design
B. Debugging
C. Routing
D. API

**Answer:** B
**Explanation:** State changes track aur debug karne ke liye.

---

## ✅ 22. Redux me multiple reducers kaise combine karte hain?

A. combineReducers
B. mergeReducers
C. joinReducers
D. attachReducers

**Answer:** A
**Explanation:** Multiple reducers ko ek root reducer me combine karta hai.

---

## ✅ 23. Redux me middleware ka use kya hai?

A. UI styling
B. Async logic handle karna
C. State store karna
D. Routing

**Answer:** B
**Explanation:** Middleware side effects aur async logic handle karta hai.

---

## ✅ 24. Redux Thunk kya hai?

A. Hook
B. Middleware
C. Reducer
D. Store

**Answer:** B
**Explanation:** Async actions likhne ke liye popular middleware.

---

## ✅ 25. Redux me state directly mutate kar sakte hain?

A. Yes
B. No (except Toolkit internally)

**Answer:** B
**Explanation:** Plain Redux me mutation allowed nahi hai; Toolkit internally handle karta hai.

---

## ✅ 26. Redux kis pattern pe based hai?

A. MVC
B. Flux
C. Observer
D. Singleton

**Answer:** B
**Explanation:** Redux Flux architecture follow karta hai.

---

## ✅ 27. React-Redux kya provide karta hai?

A. Hooks
B. UI components
C. Routing
D. API calls

**Answer:** A
**Explanation:** useSelector aur useDispatch jaise hooks provide karta hai.

---

## ✅ 28. useSelector kab re-render karta hai?

A. Jab component mount ho
B. Jab state change ho
C. Jab API call ho
D. Kabhi nahi

**Answer:** B
**Explanation:** Jab selected state change hoti hai tab component re-render hota hai.

---

## ✅ 29. Redux me best practice kya hai?

A. Large reducers
B. Direct mutation
C. Small slices
D. No structure

**Answer:** C
**Explanation:** Chhote aur modular slices maintainable hote hain.

---

## ✅ 30. Redux small apps me use karna chahiye?

A. Yes
B. No (usually overkill)

**Answer:** B
**Explanation:** Small apps me unnecessary complexity badhata hai.

---

## 🎯 Next Steps

- Redux DevTools use karo
- Middleware samjho (Thunk)
- Advanced patterns seekho

---

🔥 Happy Coding Bhai!

