# 🌌 RSA Cryptosystem — Cryptography Journal

---

# 🧬 Foundations of RSA

## 🌠 Intuition

> 🔐 RSA uses **two keys**:

- 🔓 Public key → for encryption / verification
- 🔒 Private key → for decryption / signing

💡 Built on a **one-way trapdoor function**:

- Easy → multiply primes
- Hard → factor back

---

## 🧩 Key Generation Flow

### ⚙️ Step-by-Step

```text
1. Choose two large primes: p, q
2. Compute modulus: N = p × q
3. Compute φ(N) = (p - 1)(q - 1)
4. Choose e such that gcd(e, φ(N)) = 1
5. Compute d such that:
   e × d ≡ 1 mod φ(N)
```

---

## 🔑 Key Structure

- 🔓 Public Key → **(N, e)**
- 🔒 Private Key → **d**

---

## 🔁 Mini Recap

- 🔢 Uses prime multiplication
- 🔑 Public & private key pair
- ⚡ Security relies on **factorization hardness**

---

# 🧠 Security of RSA

## ⚡ Core Assumption

> 🚨 Factoring large integers is **computationally infeasible**

- Easy:
  - 🧮 Compute: `N = p × q`

- Hard:
  - ❌ Recover: `p, q from N`

---

## 🧩 Why Factoring Breaks RSA

- If attacker finds **p, q**:
  - 🧮 Can compute φ(N)
  - 🔓 Can derive **d** from **e**

---

## 🚀 Future Threat

> ⚠️ Quantum computing changes everything

- 🧠 **Shor’s Algorithm**:
  - Can factor integers efficiently
  - 💥 Breaks RSA if powerful enough

---

## 🔁 Mini Recap

- 🔐 Security = factoring difficulty
- ⚠️ Quantum computers threaten RSA

---

# 🔄 RSA Encryption & Decryption

## 📊 Core Equations

### ✨ Encryption

```text
C = M^e mod N
```

### 🔓 Decryption

```text
M = C^d mod N
```

---

## 🧠 Why It Works

> Based on number theory (Euler / Fermat)

a^{p-1} \equiv 1 \ (\text{mod } p)

- 🔁 Because:
  - `e × d ≡ 1 mod φ(N)`

- ✨ Ensures:
  - `(M^e)^d ≡ M mod N`

---

## 🔁 Mini Recap

- 🔐 Encrypt with public key
- 🔓 Decrypt with private key
- 🧠 Works due to modular arithmetic

---

# ⚠️ Small e Vulnerability

## 🚨 Problem Scenario

- Choose small exponent: `e = 3`

### 📉 Weak Encryption

```text
C = M^3 mod N
```

---

## 🧠 Attack Insight (Cube Attack)

- If:
  - 📦 M³ < N (no modular wrap)

- Then:
  - 😱 Attacker computes cube root directly!

```text
M = ∛C
```

---

## ❓ What About e = 2?

- Even worse:

```text
M = √C
```

---

## 🛡️ Defense

- ✔️ Use **padding schemes** (e.g., OAEP)
- ✔️ Avoid predictable plaintext

---

## 🔁 Mini Recap

- ⚠️ Small e → dangerous
- 💥 Leads to root-based attacks
- 🛡️ Use padding to secure

---

# ✍️ RSA Digital Signature

## 🌠 Intuition

> 🔒 Sign with private key → 🔍 verify with public key

---

## ✨ Signing

```text
S = H(M)^d mod N
```

---

## 🔍 Verification

```text
H(M) = S^e mod N
```

---

## 🧠 Why Hash Function?

> ⚡ Never sign raw messages

- 📦 Fixed-size output
- 🛡️ Prevents manipulation
- 🚀 Improves efficiency

---

## 🔁 Mini Recap

- ✍️ Private key signs
- 🔍 Public key verifies
- 🧠 Hash ensures integrity

---

# 💥 Multiplication Attack (Signature Forgery)

## ⚠️ Attack Idea

Given:

```text
S1 = M1^d mod N
S2 = M2^d mod N
```

Attacker computes:

```text
S = S1 × S2 = (M1 × M2)^d mod N
```

---

## 😱 Result

- ✔️ Valid signature for:

```text
M = M1 × M2
```

- ❌ Without knowing private key!

---

## 🧠 Root Cause

> RSA is **multiplicative**

```text
(M1 × M2)^d = M1^d × M2^d
```

---

## 🛡️ Countermeasure

> Use **hash function before signing**

```text
S = H(M)^d mod N
```

- ❌ Now attacker cannot combine hashes meaningfully

---

## 🔁 Mini Recap

- 💥 RSA is multiplicative → exploitable
- 🛡️ Hashing prevents forgery

---

# ⚔️ Final Synthesis

> 🌌 RSA is elegant but fragile without proper safeguards

- 🔐 Strength:
  - Based on hard math (factorization)

- ⚠️ Weakness:
  - Poor parameter choices → vulnerable

- 🧠 Reality:
  - Always combined with:
    - Padding (OAEP)
    - Hashing (SHA family)
