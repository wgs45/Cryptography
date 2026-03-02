# 🧱 Data Encryption Standard (DES)

> 🌌 _Vintage Cyber Shield (1977)_ — A symmetric block cipher built on the Feistel network, once the backbone of global cryptography.

---

## 📜 Historical Snapshot

- 🏛 Adopted by **NIST** in 1977
- 🔐 Symmetric-key algorithm
- 🔑 Effective key length: **56 bits**
- 📦 Block size: **64 bits**
- 🧬 Structure: **Feistel Network**

> ⚠️ Today DES is considered insecure due to small key size (brute-force feasible).

---

# 🧠 1️⃣ Big Picture Architecture

## 🔷 High-Level Encryption Flow

```text
64-bit Plaintext
        ↓
Initial Permutation (IP)
        ↓
16 Feistel Rounds
        ↓
32-bit Swap
        ↓
Inverse Initial Permutation (IP⁻¹)
        ↓
64-bit Ciphertext
```

---

### 🧩 Feistel Round Logic

Each round transforms:

```text
Li = Ri-1
Ri = Li-1 ⊕ F(Ri-1, Ki)
```

Where:

- 🔑 Ki = 48-bit round key
- ⚙️ F = nonlinear mixing function

> 💡 Feistel property: Encryption and decryption use the same structure (reverse key order).

---

### ⚡ Mini Recap

- 64-bit input
- 16 rounds
- Same algorithm for encryption/decryption
- Only key order changes

---

# 🔄 2️⃣ Initial & Final Permutations

## 🧭 Initial Permutation (IP)

- Rearranges 64-bit input
- No cryptographic strength
- Historical hardware optimization

Example structure:

```text
58 50 42 34 26 18 10 2
60 52 44 36 28 20 12 4
...
```

---

## 🔁 Inverse Initial Permutation (IP⁻¹)

- Reverses IP
- Produces final ciphertext

> 🧠 IP and IP⁻¹ cancel each other structurally.

---

### 📌 Summary

| Stage | Purpose            |
| ----- | ------------------ |
| IP    | Bit rearrangement  |
| IP⁻¹  | Undo rearrangement |

Pure permutation — no confusion or diffusion added.

---

# 🔥 3️⃣ Inside One DES Round

## 🧬 Round Structure Overview

```text
Ri-1 (32 bits)
      ↓
Expansion (E) → 48 bits
      ↓
XOR with Ki (48 bits)
      ↓
S-Boxes → 32 bits
      ↓
Permutation (P)
      ↓
Output (32 bits)
```

---

## 🔍 Step-by-Step Breakdown

### 1️⃣ Expansion (E Table)

- Expands 32 → 48 bits
- Duplicates boundary bits
- Creates overlap

```text
32 1 2 3 4 5
4 5 6 7 8 9
...
```

🎯 Purpose:

- Enable mixing with 48-bit round key
- Increase diffusion potential

---

### 2️⃣ XOR with Round Key

```text
Expanded R ⊕ Ki
```

🔑 Injects key material into the round.

---

### 3️⃣ S-Box Substitution (Nonlinear Core)

- 8 S-boxes
- Each: 6 bits → 4 bits
- Total: 48 → 32 bits

Example:

```text
Input: 1 0101 0
Row = first & last bits → 10 (binary) = 2
Column = middle 4 bits → 0101 = 5
Output = S1[2][5] = 6 → 0110
```

> 🎭 S-boxes provide **confusion** (nonlinearity).

---

### 4️⃣ Permutation (P Table)

- Rearranges 32 bits after S-boxes
- Enhances diffusion

```text
16 7 20 21 29 12 ...
```

🎯 Spreads S-box output across next round.

---

### ⚡ Round Recap

| Step  | Function              |
| ----- | --------------------- |
| E     | Expand bits           |
| XOR   | Add key               |
| S-box | Nonlinear compression |
| P     | Diffusion permutation |

> 🔥 This structure repeats 16 times.

---

# 🔑 4️⃣ Key Schedule (Round Key Generation)

## 🧩 Key Preparation

### Step 1️⃣ Permuted Choice 1 (PC-1)

- Input: 64-bit key
- Removes 8 parity bits
- Output: 56 bits

```text
64 bits → PC-1 → 56 bits
```

Split into:

- Ci (28 bits)
- Di (28 bits)

---

### Step 2️⃣ Left Circular Shifts

Each round shifts Ci and Di:

| Round | Bits Rotated |
| ----- | ------------ |
| 1     | 1            |
| 2     | 1            |
| 3–8   | 2            |
| 9     | 1            |
| 10–15 | 2            |
| 16    | 1            |

> 🔄 Creates evolving key material per round.

---

### Step 3️⃣ Permuted Choice 2 (PC-2)

- Compresses 56 → 48 bits
- Selects specific bits

```text
Ci + Di → PC-2 → Ki (48 bits)
```

🎯 Produces round key Ki.

---

### 🔁 Key Schedule Flow

```text
64-bit Key
    ↓
PC-1 → 56 bits
    ↓
Split → C0 | D0
    ↓
Left Shifts (per round)
    ↓
PC-2
    ↓
Round Key Ki (48 bits)
```

---

### 🧠 Key Schedule Summary

- 16 round keys
- Each 48 bits
- Derived from shifting + permuting

---

# 🌌 5️⃣ Why DES Is Weak Today

> 🚨 Main vulnerability: 56-bit key

- Brute-force feasible with modern hardware
- Broken publicly in 1998 (EFF DES Cracker)

💡 Successor:

- Triple DES (3DES)
- Advanced Encryption Standard (AES)

---

# ⚡ Complete DES Mental Model

### 🔷 Structural Layers

1. 🧭 IP (Permutation)
2. 🔁 16 Feistel Rounds
   - Expansion
   - XOR
   - S-box
   - Permutation

3. 🔄 Swap halves
4. 🔁 IP⁻¹

---

# 🧩 Final Neon Recap

- 📦 64-bit block cipher
- 🔑 56-bit effective key
- 🔁 16 Feistel rounds
- 🎭 S-boxes provide confusion
- 🔀 Permutations provide diffusion
- ⚠️ Now cryptographically obsolete

---

> 🌃 DES is like a retro neon firewall — architecturally elegant, historically powerful, but no match for modern quantum-speed adversaries.
