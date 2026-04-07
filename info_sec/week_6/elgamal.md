# 🛡️ ElGamal Cryptosystem — Journal

---

## 🔹 1. Overview — Public Key Cryptography

> 💡 **Intuition:** Based on **Discrete Logarithms**, related to Diffie-Hellman, allows **encryption & decryption** with public/private keys.

- Announced by **ElGamal, 1984**
- Works on **blocks**, size depends on a prime `q`
- Public key scheme → sender can encrypt without sharing private key

---

## 🏗️ 2. How Public Key Works — Analogy

```txt
Alice = Bob's lock + treasure box
Bob   = Bob's key + treasure box

```

> 🔑 Only Bob’s key (private key) can open the box; the lock (public key) is safe to share.

---

## 🌐 3. Elements of ElGamal Cryptosystem

### 🔹 Global Public Parameters

- `q` = prime number
- `α < q` = primitive root of q

### 👤 Alice — Key Generation

1. Pick private `X_A < q-1` 🔒
2. Compute public:

```txt
Y_A = α^X_A mod q

```

- **Public key:** Pu = {q, α, Y_A}
- **Private key:** X_A

---

### 📨 Bob — Encryption

1. Message `M < q`
2. Pick **random r < q** 🔒
3. Compute shared key:

```txt
K = Y_A^r mod q

```

1. Compute ciphertext components:

```txt
C1 = α^r mod q
C2 = K * M mod q

```

1. Send ciphertext:

```txt
Ciphertext = (C1 || C2)

```

---

### 🔓 Alice — Decryption

1. Receive `(C1, C2)`
2. Compute shared key:

```txt
K = C1^X_A mod q

```

1. Recover plaintext:

```txt
M = C2 * K^(-1) mod q

```

> ✅ Works because:

```txt
K = (Y_A)^r mod q = (α^X_A)^r mod q = α^(r*X_A) mod q = C1^X_A mod q

```

---

## ⚠️ 4. Risk — Reusing r

> 💡 Each block **must use a unique r**, otherwise the system becomes vulnerable.

- Suppose two messages M1, M2 encrypted with same r:

```txt
C1,1 = α^r mod q,  C2,1 = K*M1 mod q
C1,2 = α^r mod q,  C2,2 = K*M2 mod q

```

- Then:

```txt
M2 = (C2,1)^(-1) * C2,2 * M1 mod q

```

- 🔓 If M1 is known, **M2 can be easily derived** → security breach

---

## 🧠 5. Mini Recap

- ElGamal is **asymmetric**, uses **public/private keys**
- Encryption involves **random r**, ensuring unpredictability
- Security relies on **Discrete Logarithm Problem**
- ⚠️ Reusing r = catastrophic, unique r for each block required
