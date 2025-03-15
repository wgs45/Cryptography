# 🔐 **Classical Encryption Techniques**

---

## 🏛️ **Two Main Types of Classical Encryption**

1. **🔄 Substitution Techniques:**
   Letters are **replaced** by other letters or symbols. 🔠➡️🔢

2. **🔀 Transposition Techniques:**
   The letters are **rearranged (permuted)** in a specific pattern. 🔠🔀🔡

---

## 🏆 **Substitution Techniques**

### 1️⃣ **🔢 Caesar Cipher (Shift Cipher)**

📜 **Used by Julius Caesar** to encrypt military messages!  
🔄 **Shifts each letter** forward in the alphabet by a fixed amount (e.g., 3 places).

📌 **Example (Shift = 3):**

```
Plaintext:  HELLO
Ciphertext: KHOOR
```

✅ **Pros:**  
✔️ Simple & easy to implement.  
❌ **Cons:**  
⛔ Easily broken using brute force (only 25 possible shifts).

---

### 2️⃣ **🔠 Monoalphabetic Cipher**

📝 **Each letter is mapped to another unique letter** in a random order.

📌 **Example:**

```
Plaintext:   HELLO
Ciphertext:  QXZAA
```

✅ **Pros:**  
✔️ More secure than Caesar Cipher.  
❌ **Cons:**  
⛔ Easily broken using **letter frequency analysis** (e.g., "E" is the most common letter in English).

🛡️ **Countermeasure:** **Homophones** (multiple substitutes for a single letter).

---

### 3️⃣ **🔳 Playfair Cipher**

📜 Invented by **Charles Wheatstone (1854)** but named after **Lord Playfair**.  
🛠 **Uses a 5x5 matrix** filled with a keyword (no duplicate letters).

📌 **Example Keyword Matrix (using "PLAYFAIR"):**

```
P  L  A  Y  F
I/J  R  B  C  D
E  G  H  K  M
N  O  Q  S  T
U  V  W  X  Z
```

✅ **Pros:**  
✔️ Encrypts **two letters at a time** (better security).  
❌ **Cons:**  
⛔ Still vulnerable to **frequency analysis** if enough ciphertext is available.

---

### 4️⃣ **📐 Hill Cipher**

📅 Invented in **1929 by Lester Hill**.  
🛠 Uses **Linear Algebra (Matrix Multiplication)** to encrypt plaintext.

📌 **Example:**

```
[ H E ]   x   [ Key Matrix ]   =   [ Ciphertext ]
[ L L ]       [   2x2   ]       [ Encrypted Text ]
```

✅ **Pros:**  
✔️ More secure than Playfair.  
❌ **Cons:**  
⛔ Requires knowledge of **matrix arithmetic**.

---

### 5️⃣ **📚 Polyalphabetic Cipher**

✅ **Uses multiple cipher alphabets** to encrypt text.

#### 🔹 **Vigenère Cipher**

🔠 **Uses multiple Caesar Ciphers** with a repeating keyword.  
📌 **Formula:**

```
Ci = (Pi + Ki) mod 26
```

✅ **Pros:**  
✔️ Harder to break than monoalphabetic ciphers.  
❌ **Cons:**  
⛔ Vulnerable to **Kasiski examination** (detecting repeating patterns).

#### 🔹 **Vernam Cipher** (1918)

🖥️ **First Cipher to use Binary Bits (XOR operation)**  
📌 **Formula:**

```
Ci = Pi ⊕ Ki
```

✅ **Pros:**  
✔️ **Unbreakable** if the key is truly random & never reused.  
❌ **Cons:**  
⛔ Requires **very long keys** (as long as the message).

---

## 🔥 **Unbreakable Cipher – One-Time Pad**

✅ **Ultimate Security!**  
🔑 **Key = Random & Same Length as Message**  
⛔ **Once used, the key must be discarded!**

---

# 🔀 **Transposition Techniques**

### 1️⃣ **Rail Fence Cipher**

✏️ **Plaintext written in a zigzag pattern**, then read row by row.

📌 **Example (Depth = 2):**

```
H   L   O   O   L
 E   L   W   R   D
```

🔒 **Ciphertext:** `HLOOL ELWRD`

✅ **Pros:**  
✔️ Simple & easy to implement.  
❌ **Cons:**  
⛔ Easily broken with the correct rail depth.

---

### 2️⃣ **🗂️ Columnar Transposition**

📝 **Rearranges text based on column order.**  
📌 **Steps:**  
1️⃣ Write plaintext in **rows**.  
2️⃣ Rearrange **columns** based on key.  
3️⃣ Read column-wise to form ciphertext.

📌 **Example (Key = 31452):**

```
H  E  L  L  O
W  O  R  L  D
```

🔒 **Ciphertext:** `LLOHE DROWL`

✅ **Pros:**  
✔️ More secure than Rail Fence.  
❌ **Cons:**  
⛔ Still vulnerable if the key is short.

---

## 🎭 **Why Use Classical Ciphers?**

✅ **Good for understanding modern cryptography.**  
✅ **Simple and fun to implement in coding challenges.**  
❌ **Not used in real-world security anymore** (easy to break with modern computing).
