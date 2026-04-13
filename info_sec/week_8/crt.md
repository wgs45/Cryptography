# 🌌 Chinese Remainder Theorem (CRT)

---

## 🧭 Ancient Intuition

> 📜 From **孫子算經 (Sunzi Suanjing)**:

- 🧩 A number leaves:
  - remainder **2 mod 3**
  - remainder **3 mod 5**
  - remainder **2 mod 7**

- ❓ What is the number?

👉 Answer: **23**

---

## 🌠 General Form

> Solve:

```text
x ≡ a1 (mod m1)
x ≡ a2 (mod m2)
...
x ≡ an (mod mn)
```

### ⚠️ شرط (Condition)

- ✅ All moduli must be **pairwise coprime**
  - gcd(mi, mj) = 1 for i ≠ j

---

## ⚙️ Construction Formula

Let:

```text
M = m1 × m2 × ... × mn
Mi = M / mi
ti = inverse of Mi mod mi
```

---

### ✨ Final Solution

x \equiv \sum\_{i=1}^{n} a_i t_i M_i \ (\mathrm{mod}\ M)

---

## 🧩 Example Walkthrough

Solve:

```text
x ≡ 2 (mod 3)
x ≡ 3 (mod 5)
x ≡ 2 (mod 7)
```

### 🔢 Step-by-step

- M = 3 × 5 × 7 = 105
- M₁ = 35, M₂ = 21, M₃ = 15

Find inverses:

- t₁ = 35⁻¹ mod 3 = 2
- t₂ = 21⁻¹ mod 5 = 1
- t₃ = 15⁻¹ mod 7 = 1

Compute:

```text
x = (2×2×35) + (3×1×21) + (2×1×15)
  = 140 + 63 + 30
  = 233 mod 105 = 23
```

---

## 🔁 Mini Recap

- 🧩 Break problem into smaller moduli
- ⚡ Solve independently
- 🔗 Reconstruct with CRT
- 🚀 Efficient and elegant

---

# 🚀 CRT in RSA Optimization

## 🌠 Core Idea

> Instead of computing:

```text
S = m^d mod N
```

Split into **two smaller computations**:

---

## ⚙️ Optimization Steps

- Compute:

```text
dp = d mod (p - 1)
dq = d mod (q - 1)
```

- Then:

```text
Sp = m^dp mod p
Sq = m^dq mod q
```

- 🔗 Recombine using CRT

---

## ⚡ Why Faster?

- 🧠 Operations done modulo **p and q** (smaller numbers)
- ⏱️ Modular exponentiation complexity reduces significantly

> 🚀 Result: **Up to 4× speed improvement**

---

## 🔁 Mini Recap

- ✂️ Split computation
- ⚡ Work on smaller numbers
- 🔗 Recombine with CRT
- 🚀 Massive speed gain

---

# ✍️ ElGamal Digital Signature

## 🌠 Intuition

> 🔐 Based on **discrete logarithm problem**

---

## ⚙️ Key Generation

```text
Choose prime q
Choose primitive root α

Private key: XA
Public key: YA = α^XA mod q
```

---

## ✨ Signature Generation

```text
1. Choose random K (gcd(K, q-1) = 1)
2. S1 = α^K mod q
3. S2 = K⁻¹(M - XA·S1) mod (q-1)
```

- 📦 Signature = (S1, S2)

---

## 🔍 Verification

```text
V1 = α^M mod q
V2 = YA^S1 × S1^S2 mod q
```

- ✅ If V1 = V2 → valid
- ❌ Else → invalid

---

## 🔁 Mini Recap

- 🔐 Uses discrete log hardness
- 🎲 Random K is critical
- ⚠️ Reusing K breaks security

---

# ⚠️ ElGamal Critical Warning

> 🚨 Never reuse K!

- If K reused:
  - 😱 Private key can be recovered

- 💥 Same vulnerability as DSA/ECDSA

---

# 🧬 Schnorr Digital Signature

## 🌠 Intuition

> ✨ Simpler, more efficient signature scheme

---

## ⚙️ Key Generation

```text
Choose primes p, q (q | p-1)
Choose α

Private key: s
Public key: v = α^(-s) mod p
```

---

## ✨ Signing

```text
1. Choose random r
2. x = α^r mod p
3. e = H(M || x)
4. y = (r + s·e) mod q
```

- 📦 Signature = (e, y)

---

## 🔍 Verification

```text
x' = α^y × v^e mod p
Check: e == H(M || x')
```

---

## 🧠 Why It Works

- Because:

```text
α^y × v^e = α^(r+se) × α^(-se) = α^r
```

✔️ Matches original x

---

## 🔁 Mini Recap

- ✨ Compact & efficient
- 🔐 Strong security proof
- 🚀 Widely used in modern crypto

---

# ⚔️ Signature Schemes Comparison

| Feature           | 🔐 RSA    | ✍️ ElGamal   | 🧬 Schnorr   |
| ----------------- | --------- | ------------ | ------------ |
| Hard Problem      | Factoring | Discrete Log | Discrete Log |
| Signature Size    | Medium    | Large        | Small        |
| Efficiency        | Medium    | Slower       | Fast         |
| Security Proof    | Weak      | Moderate     | Strong       |
| Randomness Needed | ❌        | ⚠️ Yes (K)   | ⚠️ Yes (r)   |

---

# 🌌 Final Synthesis

> 🧠 Three pillars of modern crypto elegance:

- 🧩 **CRT** → reconstruct & optimize
- 🔐 **RSA** → factorization-based security
- ✍️ **ElGamal / Schnorr** → discrete log signatures

💡 Real-world systems:

- Combine **math + randomness + hashing**
- Prioritize **efficiency + security proofs**
