# 🌟 **EULER’S THEOREM**

---

## 💠 **Definition — The Charm of Relatively Prime Numbers**

When two positive integers **a** and **n** share no common factors except 1 (✨ _they’re called relatively prime_),
a wondrous relation holds true:

> **a^φ(n) ≡ 1 (mod n)**

🧙‍♀️ In human words:
If you raise _a_ to the power of _φ(n)_ (Euler’s Totient Function of _n_),
you’ll always end up with a remainder of **1** when divided by _n_! 💫

---

## 📘 **What’s φ(n)?**

φ(n) (pronounced _phi of n_) counts **how many numbers below n** are _relatively prime_ to n.
Think of it as counting the “friendly” numbers that don’t share any divisors with _n_! 💕

Example:
n = 10 → numbers less than 10 are [1, 2, 3, 4, 5, 6, 7, 8, 9]
Relatively prime ones are [1, 3, 7, 9] → that’s **4 numbers**
⭐ So φ(10) = 4

---

## ✨ **Example 1: Proof for a = 3 and n = 10**

### 🎯 Given

- a = 3
- n = 10
- φ(10) = 4

Now apply Euler’s spell~ 🪄

**a^φ(n) ≡ 1 (mod n)**
→ 3^4 ≡ 1 (mod 10)

**Calculation:**
3⁴ = 81
81 ÷ 10 → remainder = 1

🌸 Result: **81 ≡ 1 (mod 10)**

✅ **The theorem holds true!**
✨ The numbers dance in perfect harmony~

---

## ⚙️ **Example 2: Proof for a = 2 and n = 10**

### 🎯 Given

- a = 2
- n = 10
- φ(10) = 4

Now apply again:
**a^φ(n) ≡ 1 (mod n)**
→ 2⁴ ≡ 1 (mod 10)

**Calculation:**
2⁴ = 16
16 ÷ 10 → remainder = 6

🚫 **Result:** 16 ≡ 6 (mod 10)

❌ **The theorem does NOT hold true!**

Because 2 and 10 are **not relatively prime**
(They share a common factor: 2!)

💡 _Lesson learned:_
Euler’s Theorem only works when **a and n are coprime**—their only shared friend is 1~ 💞

---

## 🌿 **TL;DR — Quick Recap**

|       Symbol       | Meaning                                     |          Example          |
| :----------------: | :------------------------------------------ | :-----------------------: |
|         a          | Base number                                 |             3             |
|         n          | Modulus                                     |            10             |
|        φ(n)        | Numbers less than n that are coprime with n |             4             |
| a^φ(n) ≡ 1 (mod n) | The core of Euler’s magic                   | ✔️ Works if gcd(a, n) = 1 |

---

## 🧠 **Memory Tip!**

✨ _If gcd(a, n) = 1 → the spell holds true!_
💥 Otherwise → the charm fails and chaos ensues!

💬 Think of Euler’s theorem like a magical contract between two numbers—
It only activates when both respect the rule of independence~ 🌙💞
