# 🔐 Block Cipher Modes of Operation — Cyber Journal

> ⚡ _Core Idea:_ Block ciphers encrypt fixed-size blocks. Modes of operation define **how multiple blocks are securely processed**.

---

## 🌆 1. Electronic Codebook (ECB)

### 🧠 Intuition

- Simplest mode — encrypt each block **independently**
- Same plaintext → same ciphertext (⚠️ big weakness)

---

### ⚙️ Process

```text
Encryption:
P1 ──► Encrypt(K) ──► C1
P2 ──► Encrypt(K) ──► C2
...
PN ──► Encrypt(K) ──► CN

Decryption:
C1 ──► Decrypt(K) ──► P1
...
```

---

### ⚠️ Weakness (Critical)

- Patterns are preserved
- Identical blocks produce identical ciphertext

> 🚨 This leaks structure (e.g., encrypted images still recognizable)

---

### 🖼️ Example Insight

- Encrypting an image → outline still visible
- No randomness involved

---

### 🧾 Mini Recap

- ✔ Simple
- ✔ Fast
- ❌ Not secure (pattern leakage)

---

## 🌌 2. Cipher Block Chaining (CBC)

### 🧠 Intuition

- Each block depends on the **previous ciphertext**
- Introduces randomness using **IV (Initialization Vector)**

---

### ⚙️ Process

```text
Encryption:
C1 = Encrypt(K, P1 ⊕ IV)
C2 = Encrypt(K, P2 ⊕ C1)
...
CN = Encrypt(K, PN ⊕ C(N-1))

Decryption:
P1 = Decrypt(K, C1) ⊕ IV
P2 = Decrypt(K, C2) ⊕ C1
...
```

---

### ✨ Key Features

- 🔗 Chaining removes patterns
- 🎲 IV adds randomness
- ⛓️ Sequential dependency (not parallel-friendly)

---

### ⚠️ Notes

- IV must be **unique and unpredictable**
- Error in one block affects **current + next block**

---

### 🧾 Mini Recap

- ✔ Secure vs ECB
- ✔ Hides patterns
- ❌ Slower (sequential)

---

## 🌊 3. Output Feedback (OFB)

### 🧠 Intuition

- Turns block cipher into a **stream cipher**
- Generates keystream independent of plaintext

---

### ⚙️ Process

```text
Keystream Generation:
O1 = Encrypt(K, Nonce)
O2 = Encrypt(K, O1)
...

Encryption:
C1 = P1 ⊕ O1
C2 = P2 ⊕ O2

Decryption:
P1 = C1 ⊕ O1
P2 = C2 ⊕ O2
```

---

### ✨ Key Features

- 🔁 No error propagation
- ⚡ Same process for encryption/decryption
- 🎯 Pre-computable keystream

---

### ⚠️ Warning

- Never reuse **Nonce + Key**
  → leads to catastrophic security failure

---

### 🧾 Mini Recap

- ✔ No chaining errors
- ✔ Stream-like behavior
- ❌ Sensitive to nonce reuse

---

## 🔄 4. Cipher Feedback (CFB)

### 🧠 Intuition

- Like OFB, but uses **ciphertext feedback**
- Works on smaller units (bits/bytes)

---

### ⚙️ Process

```text
Encryption:
C1 = P1 ⊕ Encrypt(K, IV)
C2 = P2 ⊕ Encrypt(K, C1)
...

Decryption:
P1 = C1 ⊕ Encrypt(K, IV)
P2 = C2 ⊕ Encrypt(K, C1)
```

---

### ✨ Key Features

- 🔁 Self-synchronizing
- 📦 Works in smaller segments (s bits)
- 🔄 Uses ciphertext as feedback

---

### ⚠️ Notes

- Error affects **current + limited future blocks**
- Slightly slower than OFB

---

### 🧾 Mini Recap

- ✔ Flexible (bit-level)
- ✔ Self-healing
- ❌ More complex

---

## 🚀 5. Counter (CTR) Mode

### 🧠 Intuition

- Converts block cipher into **parallel stream cipher**
- Uses incrementing counters

---

### ⚙️ Process

```text
Keystream:
O1 = Encrypt(K, Counter1)
O2 = Encrypt(K, Counter2)

Encryption:
C1 = P1 ⊕ O1
C2 = P2 ⊕ O2

Decryption:
P1 = C1 ⊕ O1
```

---

### ✨ Key Features

- ⚡ Fully parallelizable
- 🚀 High performance
- 🔄 Same operation for encrypt/decrypt

---

### ⚠️ Critical Warning

> 🚨 Ciphertext can be modified (no integrity protection)

- Must combine with authentication (e.g., MAC)

---

### 🧾 Mini Recap

- ✔ Fastest mode
- ✔ Parallel
- ❌ No built-in integrity

---

# 🌃 Final Comparison Table

| Mode | Pattern Leak | Parallel   | Error Propagation | Speed      | Security     |
| ---- | ------------ | ---------- | ----------------- | ---------- | ------------ |
| ECB  | ❌ Yes       | ✔ Yes     | ❌ None           | ⚡ Fast    | 🚨 Weak      |
| CBC  | ✔ No        | ❌ No      | ⚠️ Medium         | 🐢 Slower  | 🔐 Good      |
| OFB  | ✔ No        | ⚠️ Partial | ❌ None           | ⚡ Fast    | 🔐 Good      |
| CFB  | ✔ No        | ❌ No      | ⚠️ Limited        | ⚖️ Medium  | 🔐 Good      |
| CTR  | ✔ No        | ✔ Yes     | ❌ None           | 🚀 Fastest | ⚠️ Needs MAC |

---

# 🌌 Summary

> 💡 Choosing the right mode = balancing **security, performance, and use case**

- ECB → ❌ Never use (except learning)
- CBC → 🧱 Classic secure choice
- OFB / CFB → 🌊 Stream-like flexibility
- CTR → 🚀 Modern high-performance standard (with authentication!)
