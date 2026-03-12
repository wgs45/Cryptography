# 🔐 Advanced Encryption Standard (AES)

---

# 🌌 1. What is AES?

The **Advanced Encryption Standard (AES)** is a modern symmetric encryption algorithm standardized by the **National Institute of Standards and Technology (NIST)** in **2001**.

It replaced the older **Data Encryption Standard** because DES became vulnerable to brute-force attacks.

---

## 🧠 Core Properties

| Property      | Description                            |
| ------------- | -------------------------------------- |
| 🔑 Type       | Symmetric key cryptosystem             |
| 📦 Block Size | **128 bits (16 bytes)**                |
| 🔁 Structure  | Substitution–Permutation Network       |
| ⚙️ Rounds     | Depends on key length                  |
| 🧮 Operations | Byte substitution, permutation, mixing |

---

## 🔑 AES Variants

AES supports three key lengths.

| Version | Key Length | Rounds    |
| ------- | ---------- | --------- |
| AES-128 | 128 bits   | 10 rounds |
| AES-192 | 192 bits   | 12 rounds |
| AES-256 | 256 bits   | 14 rounds |

The **key schedule** generates:

```
N + 1 round keys
```

Example:

| Cipher  | Round Keys |
| ------- | ---------- |
| AES-128 | 11         |
| AES-192 | 13         |
| AES-256 | 15         |

---

### 🧠 Mini Recap

- AES is the **modern encryption standard**
- Uses **128-bit blocks**
- Uses **multiple rounds depending on key size**

---

# 🧩 2. AES Data Structure — The State Matrix

AES organizes data into a **4 × 4 matrix** called the **State**.

```
| B0  B4  B8  B12 |
| B1  B5  B9  B13 |
| B2  B6  B10 B14 |
| B3  B7  B11 B15 |
```

Each element is:

```
1 byte (8 bits)
```

Total:

```
16 bytes = 128 bits
```

---

### 💡 Why a Matrix?

Using a matrix allows AES to:

- 🔄 **Rearrange bytes**
- 🔀 **Diffuse information**
- 🔗 **Mix bits across columns**

This strengthens cryptographic security.

---

### 🧠 Mini Recap

- AES processes data as a **4×4 byte matrix**
- This matrix is called the **State**
- All transformations operate on the State

---

# ⚙️ 3. AES Round Transformations

Each AES round applies **four transformations**.

| Step | Operation   | Purpose                 |
| ---- | ----------- | ----------------------- |
| 1    | SubBytes    | Non-linear substitution |
| 2    | ShiftRows   | Byte permutation        |
| 3    | MixColumns  | Diffusion               |
| 4    | AddRoundKey | Key mixing              |

⚠️ **Final round omits MixColumns**.

---

## AES Round Structure

```
Initial Round
    ↓
AddRoundKey

Rounds 1 → N-1
    ↓
SubBytes
ShiftRows
MixColumns
AddRoundKey

Final Round
    ↓
SubBytes
ShiftRows
AddRoundKey
```

---

### 🔁 Decryption Operations

Each transformation has an **inverse**.

| Encryption  | Decryption     |
| ----------- | -------------- |
| SubBytes    | InvSubBytes    |
| ShiftRows   | InvShiftRows   |
| MixColumns  | InvMixColumns  |
| AddRoundKey | same operation |

---

### 🧠 Mini Recap

AES encryption rounds apply **four transformations** to the State.

The **last round skips MixColumns**.

---

# 🧬 4. SubBytes Transformation

SubBytes performs **non-linear substitution** using an **S-Box**.

---

## 🧠 What is an S-Box?

AES uses a **16 × 16 lookup table** called the **Substitution Box (S-Box)**.

Properties:

- Contains **all 256 possible byte values**
- Each input byte maps to **exactly one output byte**

Example lookup:

```
SubBytes(2E) → 31
```

Decryption uses:

```
InvSubBytes(31) → 2E
```

---

## Example State Transformation

Before SubBytes

```
EA 04 65 85
87 F2 4D 97
83 45 5D 96
EC 6E 4C 90
```

After SubBytes

```
5C 33 98 B0
4A C3 46 E7
F0 2D AD C5
8C D8 95 A6
```

---

### 🎯 Purpose

SubBytes introduces:

- 🔀 **Non-linearity**
- 🛡 **Resistance to linear and differential cryptanalysis**

---

### 🧠 Mini Recap

SubBytes:

- Replaces every byte using the **S-Box**
- Provides **confusion** in encryption

---

# 🔄 5. ShiftRows Transformation

ShiftRows performs **row-wise permutation**.

---

## Rotation Rules

| Row   | Shift           |
| ----- | --------------- |
| Row 0 | no shift        |
| Row 1 | left shift by 1 |
| Row 2 | left shift by 2 |
| Row 3 | left shift by 3 |

---

### Example

Before:

```
X0  X1  X2  X3
X4  X5  X6  X7
X8  X9  X10 X11
X12 X13 X14 X15
```

After:

```
X0  X1  X2  X3
X5  X6  X7  X4
X10 X11 X8  X9
X15 X12 X13 X14
```

---

### 🎯 Purpose

ShiftRows spreads bytes across columns.

This helps:

- 📡 **Propagate errors**
- 🔗 **Increase diffusion**

---

### 🧠 Mini Recap

ShiftRows:

- Rotates rows
- Breaks column alignment
- Improves diffusion

---

# 🧪 6. MixColumns Transformation

MixColumns transforms **each column independently**.

The transformation is defined by **matrix multiplication** in:

```
GF(2⁸)
```

---

## Encryption Matrix

```
|02 03 01 01|
|01 02 03 01|
|01 01 02 03|
|03 01 01 02|
```

This matrix multiplies each column of the State.

---

## Decryption Matrix

```
|0E 0B 0D 09|
|09 0E 0B 0D|
|0D 09 0E 0B|
|0B 0D 09 0E|
```

---

### Example Result

Column input:

```
87
6E
46
A6
```

Computation:

```
(02 × 87) ⊕ (03 × 6E) ⊕ 46 ⊕ A6
```

Result:

```
47
```

---

### 🎯 Purpose

MixColumns provides:

- 🔀 **Strong diffusion**
- 📡 **Byte interdependence**

A single byte change affects **entire columns**.

---

### 🧠 Mini Recap

MixColumns:

- Uses **finite field arithmetic**
- Mixes bytes within each column

---

# 🔑 7. AddRoundKey Transformation

AddRoundKey combines the **State** with the **Round Key**.

Operation:

```
State ⊕ RoundKey
```

This is a **bitwise XOR operation**.

---

### Example

```
State
47 40 A3 4C
AC 19 28 57
EB 59 8B 1B
37 D4 70 9F
```

```
Round Key
77 FA D1 5C
40 2E A1 C3
94 E4 3A 42
66 DC 29 00
```

Result:

```
F2 38 13 42
ED A5 A6 BC
F3 21 41 6A
1E 84 E7 D6
```

---

### 🎯 Purpose

AddRoundKey ensures encryption depends on the **secret key**.

Without the correct key:

```
Decryption is impossible
```

---

### 🧠 Mini Recap

AddRoundKey:

- XOR State with Round Key
- Introduces key dependency

---

# 🧠 8. AES Key Expansion (Key Schedule)

AES generates round keys from the **original key**.

Each key is split into **4-byte words**.

---

## Core Formula

```
W4 = SubWord(RotWord(W3)) ⊕ Rcon[i]
```

---

## Key Schedule Components

### 🔄 RotWord

Rotates a word left by 1 byte.

```
[a0 a1 a2 a3] → [a1 a2 a3 a0]
```

---

### 🔁 SubWord

Applies the **S-Box substitution** to each byte.

---

### ⚡ Round Constant (Rcon)

XOR with predefined constants.

| i   | Rcon |
| --- | ---- |
| 1   | 01   |
| 2   | 02   |
| 3   | 04   |
| 4   | 08   |
| 5   | 10   |
| 6   | 20   |
| 7   | 40   |
| 8   | 80   |
| 9   | 1B   |
| 10  | 36   |

---

## Key Expansion Structure

```
W0 W1 W2 W3
   ↓
W4 W5 W6 W7
   ↓
...
   ↓
W44 W45 W46 W47
```

AES-128 generates **44 words**.

---

### 🧠 Mini Recap

Key Expansion:

- Generates round keys
- Uses **RotWord**
- Uses **SubWord**
- Uses **Rcon constants**

---

# 🌃 Final Neon Summary

### AES Core Pipeline

```
Plaintext
   ↓
AddRoundKey
   ↓
(SubBytes → ShiftRows → MixColumns → AddRoundKey) × N
   ↓
(SubBytes → ShiftRows → AddRoundKey)
   ↓
Ciphertext
```

---

### ⚡ AES Security Strength

| Feature           | Benefit                |
| ----------------- | ---------------------- |
| Large key sizes   | brute-force resistant  |
| Non-linear S-box  | strong confusion       |
| Byte permutations | diffusion              |
| Finite field math | cryptographic strength |

---

# 🌠 Memory Anchor

```
SubBytes → Confusion
ShiftRows → Permutation
MixColumns → Diffusion
AddRoundKey → Secret Key Mixing
```
