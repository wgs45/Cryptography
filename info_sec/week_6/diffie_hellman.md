# 🌐 Diffie-Hellman Key Exchange — Journal

---

## 🔑 1. Overview — Secure Shared Secrets

> 💡 **Intuition:** Two parties can create a shared secret **without ever sending it directly**.

- Security relies on the **Discrete Logarithm Problem**
- Enables **symmetric keys** to be established over insecure channels

---

## 🧮 2. Core Concept — Discrete Logarithm

### 🔹 Formula

```txt
y = g^x mod p

```

- 🔑 **Given:** y, g, p
- ❌ **Unknown:** x is extremely hard to compute
- ⚡ Difficulty comes from **modular arithmetic wrap-around**

### 🔹 Why Hard?

- Many exponents produce **same modulo results**
- Example:

```txt
14 ≡ 2 (mod 12) ➔ Could be 14, 26, 38, …

```

- Predicting x from y is **computationally infeasible**

---

## 🏗️ 3. Primitive Roots

> 🌱 A primitive root `α` of prime `p` generates all integers 1..p-1 modulo p.

- Sequence:

```txt
α^1 mod p, α^2 mod p, α^3 mod p, …, α^(p-1) mod p

```

- Ensures **full coverage** of modulo space → good for key generation

---

## 🔄 4. Diffie-Hellman Protocol — Step by Step

### 🌍 Global Public Elements

- `q` = prime number
- `α` < q, primitive root of q

### 👤 User A (Alice)

1. Pick private `X_A < q` 🔒
2. Compute public:

```txt
Y_A = α^X_A mod q

```

### 👤 User B (Bob)

1. Pick private `X_B < q` 🔒
2. Compute public:

```txt
Y_B = α^X_B mod q

```

### 🔄 Shared Key Computation

- Alice computes:

```txt
K = (Y_B)^X_A mod q = α^(X_B*X_A) mod q

```

- Bob computes:

```txt
K = (Y_A)^X_B mod q = α^(X_A*X_B) mod q

```

> ✅ Result: Both have the **same shared secret** K

---

## ⚠️ 5. Man-in-the-Middle Attack (MITM)

> 🕵️‍♂️ If an attacker (Darth) intercepts exchanges:

- Darth picks private `X_D`
- Computes public `Y_D = α^X_D mod q`
- Intercepts messages: Alice → Bob and Bob → Alice

### 🔹 Effect

- Alice encrypts using `K_2 = Y_D^X_A mod q`
- Bob encrypts using `K_1 = Y_D^X_B mod q`
- Darth knows **both K_1 and K_2** → can read all messages

### ⚡ Key Insight

- **DH is vulnerable without authentication**
- Must combine with **digital signatures or certificates** for safety

---

## 🧠 6. Mini Recap

- Diffie-Hellman allows **secure key generation over public channels**
- Security is based on **Discrete Logarithm Problem**
- Primitive roots ensure **full modular coverage**
- Always beware **MITM attacks**
