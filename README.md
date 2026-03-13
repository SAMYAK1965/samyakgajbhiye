# Hi 👋 I'm Samyak Gajbhiye
![Profile Views](https://komarev.com/ghpvc/?username=samyakgajbhiye&color=blue)

🎓 Final Year Electronics & Telecommunication Engineering Student  
💻 Full-Stack Developer  

# Tech Stack
![React](https://img.shields.io/badge/React-black?logo=react)
![Vue.js](https://img.shields.io/badge/Vue.js-green?logo=vue.js)
![HTML](https://img.shields.io/badge/HTML-orange?logo=html5)
![CSS](https://img.shields.io/badge/CSS-blue?logo=css3)
![JavaScript](https://img.shields.io/badge/JavaScript-yellow?logo=javascript)

![Python](https://img.shields.io/badge/Python-blue?logo=python)
![Flask](https://img.shields.io/badge/Flask-black?logo=flask)
![REST API](https://img.shields.io/badge/REST-API-lightgrey)


![MySQL](https://img.shields.io/badge/MySQL-blue?logo=mysql)
![SQLite](https://img.shields.io/badge/SQLite-lightgrey?logo=sqlite)


![Git](https://img.shields.io/badge/Git-orange?logo=git)
![GitHub](https://img.shields.io/badge/GitHub-black?logo=github)
![Postman](https://img.shields.io/badge/Postman-orange?logo=postman)

---

## 📌 Projects

### 🔐 Secure File Encryption & Decryption System
- Built a secure file encryption system using **Python, Vue.js, and SQLite**
- Implemented encryption and decryption for secure file storage
- Designed a frontend interface for file upload and management

### ⚙️ Scalable Backend API System
- Developed REST APIs using **Python**
- Integrated database operations and secure data handling
- Tested APIs using **Postman**

---

## ⚡ Code Performance & Optimization

Efficient code is at the core of scalable software. Below are optimizations I apply across my tech stack.

---

### 🐍 Python — Common Inefficiencies & Fixes

**1. Use list comprehensions instead of manual loops**

```python
# ❌ Slow — appending inside a loop
squares = []
for n in range(10_000):
    squares.append(n * n)

# ✅ Fast — list comprehension (2–3× faster)
squares = [n * n for n in range(10_000)]
```

**2. Use `set` for O(1) lookups instead of `list` O(n)**

```python
# ❌ Slow — linear search in a list
valid_ids = [1, 2, 3, 4, 5]          # O(n) per lookup
if user_id in valid_ids:
    grant_access()

# ✅ Fast — constant-time lookup in a set
valid_ids = {1, 2, 3, 4, 5}          # O(1) per lookup
if user_id in valid_ids:
    grant_access()
```

**3. Cache expensive function results with `lru_cache`**

```python
from functools import lru_cache

# ❌ Slow — recomputes Fibonacci for every call
def fib(n):
    if n < 2:
        return n
    return fib(n - 1) + fib(n - 2)   # exponential time O(2^n)

# ✅ Fast — memoised, O(n) total with cache
@lru_cache(maxsize=None)
def fib(n):
    if n < 2:
        return n
    return fib(n - 1) + fib(n - 2)
```

**4. Use generators for large datasets to save memory**

```python
# ❌ Memory-heavy — loads all records into a list at once
def read_all_records(file_path):
    with open(file_path) as f:
        return f.readlines()           # entire file in RAM

# ✅ Memory-efficient — yields one line at a time
def read_records(file_path):
    with open(file_path) as f:
        for line in f:
            yield line.strip()
```

---

### 🌐 JavaScript / React — Performance Patterns

**1. Use `Array.prototype` methods instead of manual loops**

```js
// ❌ Verbose and harder to optimize
const result = [];
for (let i = 0; i < items.length; i++) {
    if (items[i].active) {
        result.push(items[i].value * 2);
    }
}

// ✅ Declarative and JIT-friendly (optimized)
const result = items
    .filter(item => item.active)
    .map(item => item.value * 2);
```

**2. Avoid O(n²) nested-loop lookups — use a `Map` for O(n) total**

```js
// ❌ O(n²) — nested loops
const merged = users.map(user => {
    const profile = profiles.find(p => p.id === user.id); // O(n) per user
    return { ...user, ...profile };
});

// ✅ O(n) — pre-index profiles into a Map
const profileMap = new Map(profiles.map(p => [p.id, p]));
const merged = users.map(user => ({ ...user, ...profileMap.get(user.id) }));
```

**3. Memoize expensive React computations with `useMemo`**

```jsx
import { useMemo } from 'react';

// ❌ Recomputes on every render
function Dashboard({ transactions }) {
    const total = transactions.reduce((sum, t) => sum + t.amount, 0);
    return <p>Total: {total}</p>;
}

// ✅ Recomputes only when transactions change
function Dashboard({ transactions }) {
    const total = useMemo(
        () => transactions.reduce((sum, t) => sum + t.amount, 0),
        [transactions]
    );
    return <p>Total: {total}</p>;
}
```

---

### 🗄️ SQL — Query Optimizations

**1. Add indexes on frequently filtered / joined columns**

```sql
-- ❌ Full table scan on every query
SELECT * FROM orders WHERE customer_id = 42;

-- ✅ Create an index once — subsequent queries use the index (O(log n))
CREATE INDEX idx_orders_customer ON orders(customer_id);
SELECT * FROM orders WHERE customer_id = 42;
```

**2. Avoid the N+1 query problem with a JOIN**

```python
# ❌ N+1 — 1 query for users + N queries for their orders
users = db.query("SELECT * FROM users")
for user in users:
    orders = db.query("SELECT * FROM orders WHERE user_id = ?", user["id"])

# ✅ Single query with JOIN — one round-trip to the database
rows = db.query("""
    SELECT u.id, u.name, o.id AS order_id, o.total
    FROM users u
    LEFT JOIN orders o ON o.user_id = u.id
""")
```

---

## 📊 GitHub Stats

![Samyak's GitHub stats](https://github-readme-stats.vercel.app/api?username=samyakgajbhiye&show_icons=true&theme=default)

![Top Languages](https://github-readme-stats.vercel.app/api/top-langs/?username=samyakgajbhiye&layout=compact)

---

## 📫 Connect With Me

LinkedIn:  
https://www.linkedin.com/in/samyak-gajbhiye-02b153187/

Email:  
Samyakgajbhiye1965@gmail.com
