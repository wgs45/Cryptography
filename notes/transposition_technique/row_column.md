# 🔀 Transposition Technique

---

## 🏛️ Row-Column Transposition

A more sophisticated **transposition cipher** that rearranges characters based on a grid structure! 🧩

### 📐 How It Works

1️⃣ **Create a Rectangle/Grid**

- Choose a key (which determines column order).
- Arrange plaintext **row by row** into a grid.

2️⃣ **Rearrange the Columns**

- Read the text **column by column** (in a defined order).

3️⃣ **Ciphertext Formation**

- The final encrypted message is formed by reading characters in this new column order! 🔒

---

### ✏️ Example

Let's encrypt **HELLO WORLD** using a 4-column layout:

#### 🔹 Step 1: Arrange in a Grid (Row by Row)

| H   | E   | L   | L   |
| --- | --- | --- | --- |
| O   |     | W   | O   |
| R   | L   | D   |     |

#### 🔹 Step 2: Read Column by Column

Ciphertext might be: **HOR LLEWD OLO** (depending on column order).

---

### 🎭 Why Use Row-Column Transposition?

- ✔️ **More Secure** than simple columnar transposition.
- ✔️ **Adds Complexity** to ciphertext structure.
- ✔️ **Easy to Implement** but harder to break without knowing the key!

---

🔑 **Fun Fact:** This method was historically used in wartime encryption to securely transmit messages! 🕵️‍♂️

---
