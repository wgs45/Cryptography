# 🔐 Authenticated Encryption for Low-Cost Devices

> ⚡ _Core Idea:_ Provide **confidentiality + integrity + authenticity** in resource-constrained environments (IoT, WSN).

---

## 🌍 Background: Low-Cost Embedded Devices

### 🧠 Context

- 📡 Widely used in:
  - Wireless Sensor Networks (WSN)
  - Internet of Things (IoT)
  - Smart meters (AMI)

---

### ⚠️ Security Challenges

- Wireless communication is vulnerable:
  - 👁️ Eavesdropping (data leaks)
  - ✍️ Message forgery (tampering)
  - 🎭 Impersonation (fake devices)

---

### 🎯 Requirement

> 🔐 Secure communication must ensure:

- 🔒 Confidentiality (hide data)
- 🧾 Integrity (no modification)
- 🪪 Authenticity (verify sender)

---

### 🧾 Mini Recap

- Devices = **low power, low memory**
- Threats = **high**
- Solution = **lightweight authenticated encryption**

---

## 🛰️ TinySec (WSN Security Architecture)

### 🧠 Intuition

- Combines:
  - 🔐 Encryption (confidentiality)
  - 🧾 MAC (integrity + authenticity)

---

### ⚙️ Process

```text id="7mrx6c"
Step 1: Encrypt plaintext → Ciphertext
Step 2: Compute MAC over ciphertext
```

---

### ✨ Advantages

- ✔ Full security (CIA triad)
- ✔ Resistant to known-plaintext attacks
- 🎲 Uses IV randomness

---

### ⚠️ Disadvantages

- ❌ High computational cost
- 🔁 Two-pass process:
  - Pass 1 → Encryption
  - Pass 2 → MAC

- 🔄 Requires inverse operations (decryption complexity)

---

### 🧾 Mini Recap

- ✔ Secure
- ❌ Heavy for low-cost devices

---

## 🧩 Ciphertext Stealing (CTS)

### 🧠 Intuition

- Prevents **ciphertext expansion** when last block is short

---

### ⚙️ Problem

- AES block size = 128 bits
- If last block < 128 bits → padding increases size

---

### 💡 Solution

- “Steal” bits from previous block
- Avoid sending padded data

---

### ⚠️ Limitation

> 🚨 Expansion still unavoidable if:

- Message length < one block

---

### 🧾 Mini Recap

- ✔ Saves bandwidth
- ✔ Efficient for small payloads
- ❌ Not perfect for very short data

---

## 🚀 Counter Mode with CBC-MAC (CCM)

### 🧠 Intuition

- Combines:
  - 🔄 CTR mode → encryption
  - 🧾 CBC-MAC → authentication

---

### ⚙️ Structure

```text id="8rq1fh"
Encryption:
CTR mode → generates ciphertext

Authentication:
CBC-MAC → computes MAC over data
```

---

### ✨ Advantages

- ⚡ Precomputable keystream
- 🧠 No inverse function needed (code efficient)
- 📦 No ciphertext expansion
- 📡 Used in Wi-Fi security (IEEE 802.11i)

---

### ⚠️ Disadvantages

- ❌ Still computationally heavy
- 🔁 Two-pass system (like TinySec)

---

### 🧾 Mini Recap

- ✔ Industry standard
- ✔ Efficient structure
- ❌ Not ideal for ultra-low-power devices

---

## 🌿 Variant CCM (Energy-Efficient)

### 🧠 Intuition

- Simplifies MAC:
  - Instead of CBC-MAC → uses XOR

---

### ⚙️ Process

```text id="5nfb42"
MAC = C1 ⊕ C2 ⊕ ... ⊕ Cn
```

---

### ⚠️ Critical Weakness (Cryptoanalysis)

- XOR is linear → predictable relationships

```text id="ydkvj6"
C1 ⊕ C2 = C1' ⊕ C2'
```

> 🚨 Attackers can manipulate ciphertext while preserving MAC

---

### 🧾 Mini Recap

- ✔ Energy efficient
- ❌ Insecure (weak MAC)

---

## ⚡ SCMA (Simultaneous Combined Mode Algorithm)

### 🧠 Intuition

- Combines encryption + authentication in **one pass**
- Uses:
  - 🔁 Tweak values (Twk)
  - ➕ Modular arithmetic

---

### ⚙️ Concept

```text id="7eq0ns"
Encryption + MAC computed simultaneously
Using:
- AES operations
- Modular addition (mod 2^n)
```

---

### ⚠️ Weakness (Cryptoanalysis)

```text id="lkc62x"
C1 + C2 mod 2^n = same pattern after modification
```

> 🚨 Predictable structure → vulnerable to manipulation

---

### 🧾 Mini Recap

- ✔ One-pass efficiency
- ❌ Weak against certain attacks

---

# 🌃 Final Comparison

| Scheme      | Passes | Efficiency     | Security   | Suitability   |
| ----------- | ------ | -------------- | ---------- | ------------- |
| TinySec     | 2      | ❌ Low         | ✔ High    | ⚠️ Limited    |
| CCM         | 2      | ⚖️ Medium      | ✔ High    | ✔ Standard   |
| Variant CCM | 1      | ✔ High        | ❌ Weak    | ❌ Unsafe     |
| SCMA        | 1      | ✔ High        | ❌ Weak    | ❌ Risky      |
| CTS         | —      | ✔ Saves space | ⚠️ Neutral | ✔ Supportive |

---

# 🌌 Master Summary

> 💡 The real challenge:
> balancing **security vs energy vs performance**

- 🔐 Strong security → usually **more computation**
- ⚡ Low energy → often **weaker protection**
- 🧠 Best real-world choice:
  - **CCM (or modern AEAD like GCM/ChaCha20-Poly1305)**
