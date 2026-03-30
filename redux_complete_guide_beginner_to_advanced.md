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

- Redux kya hai?
- Action vs Reducer?
- Redux Toolkit kya hai?
- useSelector vs useDispatch?

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

