# 🌟 Euler Totient Function (φ) 🌟

_A magical number theory charm that filters true number-friends!_ ✨🔮

---

## 📖 Definition

- **Symbol:** φ(n)
- **Meaning:** The number of positive integers less than **n** that are **relatively prime** to **n**.
- **Relatively prime:** two numbers share no common factor except 1.

---

## ✨ Example 1: φ(5)

Here **n = 5** (prime ✨).
Numbers less than 5 → 1, 2, 3, 4

| Number | gcd(x, 5) | Relatively Prime? |
| ------ | --------- | ----------------- |
| 1      | 1         | ✔️                |
| 2      | 1         | ✔️                |
| 3      | 1         | ✔️                |
| 4      | 1         | ✔️                |

🌟 **Answer:** φ(5) = 4

---

## ✨ Example 2: φ(8)

Here **n = 8** (not prime ❌).
Numbers less than 8 → 1, 2, 3, 4, 5, 6, 7

| Number | gcd(x, 8) | Relatively Prime? |
| ------ | --------- | ----------------- |
| 1      | 1         | ✔️                |
| 2      | 2         | ❌                |
| 3      | 1         | ✔️                |
| 4      | 4         | ❌                |
| 5      | 1         | ✔️                |
| 6      | 2         | ❌                |
| 7      | 1         | ✔️                |

🌟 **Answer:** φ(8) = 4

---

## 🧮 Formula Scroll ✨

Depending on **n**, use one of these:

🔹 If **n is prime**:
φ(n) = n − 1

🔹 If **n = p × q** (p, q are primes):
φ(n) = (p − 1)(q − 1)

🔹 If **n = p1^a × p2^b × … × pk^c** (prime factorization):
φ(n) = n × (1 − 1/p1) × (1 − 1/p2) × … × (1 − 1/pk)

---

## ✨ Example 3: φ(5) (Prime Case)

n = 5 (prime)
φ(5) = 5 − 1 = 4

✔️ Matches our earlier example!

---

## ✨ Example 4: φ(35) (Two Primes Case)

n = 35 = 5 × 7
φ(35) = (5 − 1)(7 − 1)
φ(35) = 4 × 6 = 24

🌟 **Answer:** φ(35) = 24

---

## ✨ Example 5: φ(7000) (Many Prime Factors)

n = 7000
Prime factorization → 2^3 × 5^3 × 7

Distinct primes: 2, 5, 7

φ(7000) = 7000 × (1 − 1/2) × (1 − 1/5) × (1 − 1/7)
φ(7000) = 7000 × (1/2) × (4/5) × (6/7)
φ(7000) = 2400

🌟 **Answer:** φ(7000) = 2400

---

## 💎 TL;DR Magical Recap

- φ(n) = numbers less than n that are **coprime with n**.
- Prime n → φ(n) = n − 1
- Two primes → φ(n) = (p − 1)(q − 1)
- General → Multiply n by (1 − 1/p) for each distinct prime factor p.

🌸 _Imagine φ(n) as a filter spell—keeping only numbers that truly “vibe” with n!_ 💕
