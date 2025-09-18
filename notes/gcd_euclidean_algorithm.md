# 🌟📖 _The Euclidean Algorithm Grimoire_ ✨🔢

Welcome, dear scholar 🌸—today we’ll unlock the secrets of **finding the GCD (Greatest Common Divisor)**, a spell of numbers often used in cryptography 🔐✨.
Think of the GCD as the **largest magical charm** that can evenly divide two numbers without leaving behind any fragments ⚔️.

---

## 🔮 1. What is GCD?

- **Greatest Common Divisor (GCD)** = the biggest number that divides two (or more) integers evenly.
- Also called the **Highest Common Factor (HCF)**.
- Why is it important? 🌟
  - Used in simplifying fractions
  - Core in **cryptography spells** (like RSA!)
  - Helps numbers "speak the same language" 💌

---

## 🌸 2. Finding GCD by Divisor Lists

✨ Example 1: _Find GCD(25, 150)_

| ✨ Number | Divisors                                           |
| --------- | -------------------------------------------------- |
| 25        | 1, **5**, **25**                                   |
| 150       | 1, 2, 3, **5**, 6, 10, 15, **25**, 30, 50, 75, 150 |

✔️ Common Divisors = {1, 5, 25}
🌟 GCD(25, 150) = **25**

---

✨ Example 2: _Find GCD(13, 31)_

| ✨ Number | Divisors |
| --------- | -------- |
| 13        | 1, 13    |
| 31        | 1, 31    |

✔️ Common Divisor = {1}
🌟 GCD(13, 31) = **1**
(_These numbers are called “coprime” or “relatively prime” 💞_)

---

## 🧮 3. The Euclidean Algorithm (the elegant shortcut ✨)

Instead of writing long divisor lists, we can use the **Euclidean Algorithm**—a magical loop of division until nothing remains 💫.

💡 Steps:

1. Divide A by B.
2. Take the remainder.
3. Replace (A, B) with (B, remainder).
4. Repeat until remainder = 0.
5. The last non-zero remainder = **GCD**!

---

### Example 1: GCD(12, 33)

| Quotient | A   | B   | Remainder |
| -------- | --- | --- | --------- |
| 2        | 33  | 12  | 9         |
| 1        | 12  | 9   | 3         |
| 3        | 9   | 3   | 0         |

🌟 Answer: GCD(12, 33) = **3**

---

### Example 2: GCD(252, 105)

| Quotient | A   | B   | Remainder |
| -------- | --- | --- | --------- |
| 2        | 252 | 105 | 42        |
| 2        | 105 | 42  | 21        |
| 2        | 42  | 21  | 0         |

🌟 Answer: GCD(252, 105) = **21**

---

## 🎀 TL;DR Recap

- **Divisor method**: list all divisors, pick the largest common one ✨.
- **Euclidean Algorithm**: divide, take remainders, repeat until 0 💫.
- **GCD** = greatest number dividing both without remainder 🧩.
