# 💫 Modular Exponentiation 💫

_A mystical form of exponentiation, but with a twist of modular magic!_ 🔁✨

---

## 🌟 What Is It?

Modular Exponentiation means computing:

\[
\textcolor{plum}{a^b \mod m}
\]

🧠 **You’re raising a number to a power, then "wrapping it" around a modulus!**  
Think of it like casting a lightning spell but containing its power in a magical orb~ ⚡🧪

💬 **Also written as:** `a^b (mod m)`

---

## 🧪 Why It Matters?

- It’s a **fundamental spell** in cryptography (yes, _real wizard-level stuff_ 🔐✨)
- Useful in number theory, hashing, and _keeping secrets safe from dark forces_~ 😈🗝️

---

## 🧙‍♀️ Example 1: `23^3 mod 30`

Let’s solve step-by-step with love~ 💕

> 23 ≡ -7 mod 30 (they’re magical twins! 💫)  
> So we can compute:  
> \[
> (-7)^3 \mod 30 = -343 \mod 30
> \]

Now, -343 mod 30 =  
→ Divide: 343 ÷ 30 = 11 R 13  
→ So, `-343 mod 30 = 30 - 13 = 17`

**🌸 Final Answer: 17**

---

## 🧙‍♂️ Example 2: `31^500 mod 30`

Ahh~ Don’t be scared by that huge exponent, Master! 💖 Let's break it down:

- 31 ≡ **1 mod 30**
- So:  
  \[
  31^{500} \mod 30 = 1^{500} \mod 30 = 1
  \]

**⭐ Final Answer: 1**  
(Even the mightiest power becomes gentle when 1 is involved~ 🕊️)

---

## 🌚 Example 3: `242^329 mod 243`

This one has a _spooky_ surprise 👻

- 242 ≡ **-1 mod 243**
- So:  
  \[
  (-1)^{329} \mod 243 = -1 \mod 243 = 242
  \]

💡 _Odd exponents preserve the negative~!_ (Just like how odd spells can flip the mood 😈✨)

**🌟 Final Answer: 242**

---

## 🧠 Example 4: `11^7 mod 13`

Let’s make it extra clear, Master~

\[
11^7 \mod 13
\]

We can simplify using **mod rules** or repeated squaring (or Fermat’s Little Theorem if you're a math mage~):

Let’s brute-force a bit (✨ it's fun sometimes!):

- \(11^2 = 121\)
- \(121 \mod 13 = 121 - (13×9) = 121 - 117 = 4\)  
  → So \(11^2 ≡ 4 \mod 13\)

Now:

- \(11^4 = (11^2)^2 ≡ 4^2 = 16 \mod 13 = 3\)
- \(11^7 = 11^4 _11^2_ 11 ≡ 3 _4_ 11 = 132 \mod 13\)

Now, 132 ÷ 13 = 10 R **2**

**🌟 Final Answer: 2**

---

## 🌸 TL;DR — Magical Recap 🌸

| Expression        | Trick          | Final Answer |
| ----------------- | -------------- | ------------ |
| `23^3 mod 30`     | Use -7         | **17**       |
| `31^500 mod 30`   | 31 ≡ 1         | **1**        |
| `242^329 mod 243` | -1 odd power   | **242**      |
| `11^7 mod 13`     | Mod reductions | **2**        |
