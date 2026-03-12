# 🧬 Parity Bit — Error Detection in Digital Systems

---

## 🌌 1. Why Do We Need Parity Bits?

Digital systems constantly transmit and store binary data.
However, during this process, **bit errors** can occur due to physical and environmental factors.

### ⚡ Common Causes of Bit Errors

- 🔌 **Electrical noise** — interference in circuits
- 📉 **Signal attenuation** — weakening signals over distance
- 💾 **Memory faults** — storage hardware failures
- 📡 **Transmission interference** — network disturbances

### 🧪 Example

| Role        | Binary Data |
| ----------- | ----------- |
| 📤 Sender   | `10110010`  |
| 📥 Receiver | `10100010`  |

> ⚠️ Without redundancy, the receiver **cannot detect** that the data was corrupted.

---

### 💡 Core Idea

Parity introduces a **redundant bit** that allows simple error detection.

- ➕ Add **one extra bit** to the data
- 🔍 Used to **verify integrity**
- 🧠 This extra bit is called the **Parity Bit**

---

### 🧠 Mini Recap

- Data can become corrupted during transmission.
- A **parity bit** is a lightweight method to **detect errors**.
- It **adds redundancy**, enabling consistency checks.

---

# ⚖️ 2. Even Parity vs Odd Parity

Parity systems enforce a rule about the **total number of `1`s** in a bit sequence.

Two common types exist:

| Parity Type        | Rule                                  |
| ------------------ | ------------------------------------- |
| ⚖️ **Even Parity** | Total number of `1`s must be **even** |
| 🔁 **Odd Parity**  | Total number of `1`s must be **odd**  |

---

## ⚖️ Even Parity

### 📊 Example

Data:

```
1011001
```

Count the `1`s:

```
1 0 1 1 0 0 1
```

Number of `1`s = **4 (even)**

Therefore the parity bit must be:

```
0
```

### 📦 Result

```
10110010
```

### 🔢 XOR Verification

```text
1 ⊕ 0 ⊕ 1 ⊕ 1 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 0 = 0
```

> ✔ Result `0` means **even parity satisfied**

---

## 🔁 Odd Parity

### 📊 Example

Data:

```
1011001
```

Number of `1`s = **4 (even)**

To make it **odd**, parity bit must be:

```
1
```

### 📦 Result

```
10110011
```

### 🔢 XOR Verification

```text
1 ⊕ 0 ⊕ 1 ⊕ 1 ⊕ 0 ⊕ 0 ⊕ 1 ⊕ 1 = 1
```

> ✔ Result `1` confirms **odd parity**

---

### 🧠 Mini Recap

- **Even parity:** total `1`s must be even
- **Odd parity:** total `1`s must be odd
- Parity is often verified using **XOR operations**

---

# 📡 3. Parity Checking Process (Receiver Side)

When data arrives, the receiver performs a **parity validation**.

### 🔍 Verification Steps

1️⃣ **Count the number of `1`s** in the received data
2️⃣ **Check parity rule**

- ⚖️ Even parity → total must be **even**
- 🔁 Odd parity → total must be **odd**

3️⃣ **Determine result**

| Result            | Meaning              |
| ----------------- | -------------------- |
| ✔ Rule satisfied | Data assumed correct |
| ❌ Rule violated  | Error detected       |

---

### 🧠 Concept Insight

Parity enforces a **global consistency constraint** on the bit sequence.

> 🧩 If the constraint fails → corruption occurred.

---

### 🧠 Mini Recap

- Receiver verifies parity rule
- Violation indicates **data corruption**
- It is a **simple but effective error detection method**

---

# 🚨 4. Error Detection Capability & Limitations

Parity checking has strengths **and** limitations.

---

## 🟢 What Parity CAN Detect

Parity can detect:

- 🔹 **Any odd number of bit errors**
- 🔹 **All single-bit errors**

### 🧪 Example: Single Bit Flip

Original

```
10110010
```

Error

```
10110000
```

The number of `1`s changes → parity rule **fails**.

> ✔ Error detected.

---

## 🔴 What Parity CANNOT Detect

Parity fails when **even numbers of bits flip**.

### 🧪 Example: Two Bit Errors

Original

```
10110010
```

Corrupted

```
10010000
```

Two bits flipped.

- Total `1`s remains **even**
- Parity check **passes**

> ⚠️ Error **goes undetected**

---

### ⚠️ Another Limitation

Parity bits **cannot correct errors**.

They only:

- 🔍 Detect possible corruption
- ❌ Cannot identify which bit is wrong

---

### 🧠 Mini Recap

| Capability                | Result |
| ------------------------- | ------ |
| Detect single-bit errors  | ✔ Yes |
| Detect odd-number errors  | ✔ Yes |
| Detect even-number errors | ❌ No  |
| Correct errors            | ❌ No  |

---

# 🔐 5. Role of Parity Bits in DES Key Schedule

In the **DES encryption algorithm**, parity bits appear in the **64-bit key**.

However, they **do not participate in encryption**.

---

## 🧠 Key Processing Step

DES applies a transformation called:

> **Permuted Choice 1 (PC-1)**

This step:

- ❌ **Removes the 8 parity bits**
- 🔑 Converts **64-bit key → 56-bit effective key**

---

### 📊 DES Key Structure

```
1   2   3   4   5   6   7   8
9  10  11  12  13  14  15  16
17 18  19  20  21  22  23  24
25 26  27  28  29  30  31  32
33 34  35  36  37  38  39  40
41 42  43  44  45  46  47  48
49 50  51  52  53  54  55  56
57 58  59  60  61  62  63  64
```

### 📍 Important

The **rightmost bit of each byte** is a **parity bit**.

```
[7 data bits][1 parity bit]
```

Total:

- 🔢 **56 data bits**
- ⚖️ **8 parity bits**

---

### 🧠 Why Keep Parity Bits?

They are used for:

- 🔍 **Key integrity verification**
- 🛠 Detecting key corruption before encryption

But they **do NOT participate in**:

- Feistel rounds
- Subkey generation
- Encryption or decryption

---

### 🧠 Mini Recap

| Property                 | Role    |
| ------------------------ | ------- |
| Total key length         | 64 bits |
| Effective key            | 56 bits |
| Parity bits              | 8 bits  |
| Used in encryption       | ❌ No   |
| Used for error detection | ✔ Yes  |

---

# 🌃 Final Neon Recap

### ⚡ Parity Bit Essentials

- ➕ **Adds one redundant bit** for integrity checking
- ⚖️ Two types: **Even parity** and **Odd parity**
- 🔍 Detects **odd-number bit errors**
- 🚫 Cannot detect **even-number errors**
- ❌ Cannot **correct errors**
- 🔐 In **DES**, parity bits are **discarded before key scheduling**

---

> 🧠 **Memory Anchor**

```
Parity Bit = Simple Error Detector
Odd Errors ✔
Even Errors ✖
Correction ✖
```
