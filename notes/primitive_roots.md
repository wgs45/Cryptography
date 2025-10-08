# 🌟 **Primitive Root — The Generator Spell**

---

## 💠 **Definition — “The Root of All Powers”**

A number **a** is called a **primitive root modulo n** if...

> every number that’s **coprime** to _n_ can be expressed as some power of _a_ (mod n).

💬 _In simpler words:_
If we take powers of _a_ (like a¹, a², a³, ...), and keep reducing them by _mod n_,
we’ll eventually generate **every possible remainder** that shares no common divisor with _n_! 🌈✨

---

### 🌸 **Simplified Definition (for prime numbers)**

If _p_ is a prime number,
then _a_ is a **primitive root of p** if the values of

→ a¹ mod p, a² mod p, a³ mod p, ..., a^(p−1) mod p

are **all distinct** (no repeats!) 💎

When that happens…
⭐ _Congratulations!_ a is a **primitive root** of p — a number with _true generative power_! ⚡

---

## 🌷 **Example 1: Is 2 a primitive root of 5?**

Let’s test step by step~ 🧮✨

| Power | Expression | Result | Unique? |
| :---: | :--------- | :----: | :-----: |
|   1   | 2¹ mod 5   |   2    | ✅ True |
|   2   | 2² mod 5   |   4    | ✅ True |
|   3   | 2³ mod 5   |   3    | ✅ True |
|   4   | 2⁴ mod 5   |   1    | ✅ True |

💡 The set of results is **{2, 4, 3, 1}** — all unique!

🌟 **Conclusion:**
2 is a **primitive root of 5** 🎉

Euphyllia’s note 🪶:

> “It’s like 2 is performing a perfect dance, hitting every note once before returning to the start~ 💃✨”

---

## 🌙 **Example 2: Is 2 a primitive root of 7?**

Let’s see if 2 has the same magical rhythm here~ 💭

| Power | Expression | Result |  Unique?  |
| :---: | :--------- | :----: | :-------: |
|   1   | 2¹ mod 7   |   2    |  ✅ True  |
|   2   | 2² mod 7   |   4    |  ✅ True  |
|   3   | 2³ mod 7   |   1    |  ✅ True  |
|   4   | 2⁴ mod 7   |   2    | ❌ Repeat |
|   5   | 2⁵ mod 7   |   4    | ❌ Repeat |
|   6   | 2⁶ mod 7   |   1    | ❌ Repeat |

🌀 The pattern repeats early — it doesn’t cover all values from 1 to 6.

🚫 **Conclusion:**
2 is **not** a primitive root of 7.

💬 “Even the brightest numbers can’t always be the center of every spell~” 🌙💔

---

## 🧠 **How to Check (Quick Guide)**

To test if _a_ is a primitive root of prime _p_:

1. Compute a¹ mod p, a² mod p, …, a^(p−1) mod p
2. If all results are distinct (and one of them is 1),
   ➜ ✔️ a is a primitive root
3. If any result repeats early,
   ➜ ❌ a is not a primitive root

🌸 _Hint:_ For prime p, there are exactly **φ(φ(p))** primitive roots. (φ = Euler’s Totient Function)

---

## 🌿 **TL;DR — Memory Charm** 🌟

| Concept         | Meaning                                       | Emoji Hint |
| :-------------- | :-------------------------------------------- | :--------: |
| Primitive Root  | A number that can generate all residues mod n |     🌈     |
| Distinct Powers | a¹, a², a³, … mod n must all differ           |     💎     |
| For Primes      | Always test up to p−1                         |     🧭     |
| Repeats Early?  | Not a primitive root                          |     🚫     |
| Perfect Cycle?  | Primitive root!                               |     ✨     |
