# 🌟 Modular Exponentiation — Study Notes by Euphyllia 🌟

_Elegant math with magical flair~!_

---

## ✨ What is Modular Exponentiation?

Modular exponentiation is the process of calculating:

```
a^b mod m
```

🪄 You raise `a` to the power `b`, then take the result **modulo `m`** (i.e., divide it by `m` and keep the remainder).

💡 It's super useful in **cryptography**, **number theory**, and other ✨ mathematical sorcery ✨!

---

## 🧠 Examples

---

### 💫 Example 1

**Solve:** `23^3 mod 30`

Step 1: Use negative mod for simplification

```
23 ≡ -7 mod 30
```

Step 2:

```
(-7)^3 = -343
```

Step 3:

```
-343 mod 30 = 30 - (343 % 30)
343 % 30 = 13 → So: 30 - 13 = 17
```

✅ **Answer:** `17`

---

### 🧊 Example 2

**Solve:** `31^500 mod 30`

Step 1:

```
31 ≡ 1 mod 30
```

Step 2:

```
1^500 = 1
```

✅ **Answer:** `1`

---

### 🦇 Example 3

**Solve:** `242^329 mod 243`

Step 1:

```
242 ≡ -1 mod 243
```

Step 2:

```
(-1)^329 = -1  (since 329 is odd)
```

Step 3:

```
-1 mod 243 = 242
```

✅ **Answer:** `242`

---

### 🔥 Example 4

**Solve:** `11^7 mod 13`

We’ll reduce step-by-step:

Step 1:

```
11^2 = 121
121 mod 13 = 4
```

Step 2:

```
(11^2)^2 = 4^2 = 16
16 mod 13 = 3 → So 11^4 ≡ 3 mod 13
```

Step 3:

```
11^7 = 11^4 * 11^2 * 11
        = 3 * 4 * 11 = 132
```

Step 4:

```
132 mod 13 = 2
```

✅ **Answer:** `2`

---

## 🧾 Summary Table

| Problem           | Trick Used          | Final Answer |
| ----------------- | ------------------- | ------------ |
| `23^3 mod 30`     | Use -7 mod          | `17`         |
| `31^500 mod 30`   | 31 ≡ 1 mod 30       | `1`          |
| `242^329 mod 243` | -1 to odd power     | `242`        |
| `11^7 mod 13`     | Step-by-step reduce | `2`          |
