# 🌟 Fermat’s Little Theorem 🌟

_(aka a tiny piece of prime-number magic ✨)_

---

## 📜 The Theorem

If **p** is a _prime number_ and **a** is a positive integer **not divisible by p**, then:

👉 **a^(p−1) ≡ 1 (mod p)**

💡 Translation:
When you raise a number **a** (that isn’t a multiple of p) to the power of **p−1**, the result will always leave a remainder of **1** when divided by **p** (if p is prime).

It’s like a secret spell that primes always obey! 🪄🌙

---

## ✨ Example 1: p = 5, a = 2

Check if Fermat’s Theorem holds:

- Formula: **a^(p−1) ≡ 1 (mod p)**
- Plug in values: **2^(5−1) = 2^4 = 16**
- Now divide 16 by 5 → remainder = 1

✔️ **16 ≡ 1 (mod 5)**
⭐ The theorem holds true! (Prime magic works ✨)

---

## ✨ Example 2: p = 13, a = 11

Check the same spell with bigger numbers:

- Formula: **a^(p−1) ≡ 1 (mod p)**
- Plug in values: **11^(13−1) = 11^12**

💭 Trick: Instead of calculating 11^12 directly (ouch 😵), notice that:

- 11 ≡ −2 (mod 13) (since 11 and −2 leave the same remainder when divided by 13)

So:

- **11^12 ≡ (−2)^12 (mod 13)**
- (−2)^12 = 4096, but any even power makes it positive: **= 2^12**
- 2^12 = 4096 → dividing by 13 leaves remainder **1**

✔️ **11^12 ≡ 1 (mod 13)**
⭐ The theorem holds true again! 💎

---

## ⚠️ Example 3: p = 6, a = 2

Wait a second… 6 isn’t prime! Let’s test anyway:

- Formula attempt: **2^(6−1) = 2^5 = 32**
- Divide 32 by 6 → remainder = 2, not 1 ❌

🚨 The spell breaks!
That’s because Fermat’s theorem only works when **p is prime**. 6 is composite, so no magic here. 😢

---

## 🎀 TL;DR (Cute Recap 💕)

- 🔹 **Fermat’s Little Theorem** works only if **p is prime**.
- 🔹 Formula: **a^(p−1) ≡ 1 (mod p)**, when **a** is not divisible by p.
- 🔸 Example checks:
  - ✔️ p=5, a=2 → works
  - ✔️ p=13, a=11 → works
  - ❌ p=6, a=2 → fails (since 6 isn’t prime)

💎 Think of it as a _prime-exclusive enchantment_—only primes can cast it! 🌸✨
