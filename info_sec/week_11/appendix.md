# 🌌 Cryptographic Hash Functions

---

## 💠 Hash Function Foundations

---

### 🔹 Intuition (Why)

Hash functions act like **digital fingerprints**—they compress any data into a fixed-size identity.

---

### 🧪 Formal Logic (How)

**Core Properties:**

- 📏 Variable input → fixed output
- ⚡ Fast to compute
- 🔐 Pre-image resistance → cannot reverse
- 🎭 Collision resistance → unlikely same hash

---

### 🏁 Recap

- Hash = integrity + compression
- Foundation for authentication systems

---

## 💠 Integrity Problem in Untrusted Networks 📡

---

### 🔹 Intuition (Why)

Sending `M + hash(M)` seems safe… until an attacker modifies both.

---

### 🧪 Formal Logic (How)

**Normal Flow:**

```text
Bob → Request M
Server → M || H(M)
```

**Attack Scenario:**

```text
Hacker intercepts:
M → M'
H(M) → H(M')

Bob receives valid-looking forged data
```

---

### 🛠️ Applied Example (Metal)

```text
M' || H(M')  # Attacker recomputes hash after modification
```

**System Impact:** Plain hashes provide integrity, but NOT authenticity.

---

### 🏁 Recap

- Hash alone ❌ insufficient
- Anyone can recompute hash

---

## 💠 Keyed Hash (MAC) 🔑

---

### 🔹 Intuition (Why)

We need **proof of origin**, not just data integrity.

---

### 🧪 Formal Logic (How)

- Introduce secret key **K**
- Compute:

```text
MAC(M) = H(K || M)
```

---

### 🛠️ Applied Example (Metal)

**Secure Flow:**

```text
Server → M || H(K || M)
```

**Attack Attempt:**

```text
Attacker tries:
M' || H(? || M')  # Cannot compute without K
```

**System Impact:** Only parties with K can generate valid authentication codes.

---

### ⚡ Comparison Table

| Method           | Integrity | Authentication | Attack Resistance |
| ---------------- | --------- | -------------- | ----------------- |
| Hash Only        | ✅        | ❌             | Weak              |
| MAC (Keyed Hash) | ✅        | ✅             | Strong            |

---

### 🏁 Recap

- MAC = hash + secret key
- Prevents forgery in insecure channels

---

## 💠 One-Time Password (OTP) 🔄

---

### 🔹 Intuition (Why)

Static passwords are reusable → vulnerable to replay attacks.

---

### 🧪 Formal Logic (How)

**Hash Chain Generation:**

```text
h1 = H(root)
h2 = H(h1)
h3 = H(h2)
...
hn = H(hn-1)
```

- Each `hi` = one-time password
- Derived from shared secret **root**

---

### 🛠️ Applied Example (Metal)

**Authentication Sequence:**

```text
Login 1 → send hn
Login 2 → send hn-1
...
Final → send root
```

**Verification:**

```text
Server checks:
H(hn-1) == hn
```

**System Impact:** Enables secure authentication even over insecure channels.

---

### 🔐 Security Insight

- Knowing `hi` does NOT reveal `hi-1`
- Forward secure due to hash one-way property

---

### 🏁 Recap

- OTP = evolving passwords
- Prevents replay attacks

---

## 💠 System-Level Perspective 🌐

---

### ⚡ Design Evolution

| Technique | Problem Solved             | Limitation               |
| --------- | -------------------------- | ------------------------ |
| Hash      | Data integrity             | No authentication        |
| MAC       | Integrity + authentication | Requires shared key      |
| OTP       | Replay protection          | Requires synchronization |

---

### 🏁 Final Takeaway

> Hash functions evolve from
> **Integrity → Authentication → Temporal Security** ✨
