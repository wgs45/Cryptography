# 🌌 Combination of Encryption & Signing

---

# 🧬 Core Concepts

## 🌠 Security Properties

- 🔐 **Encryption → Confidentiality**
  - Protects message from being read

- ✍️ **Digital Signature → Integrity + Non-repudiation**
  - Ensures message is unchanged
  - Proves sender identity

---

## 🧩 Notation System

| Symbol        | Meaning                    |
| ------------- | -------------------------- |
| 🔓 PKA / PKB  | Public keys (Alice / Bob)  |
| 🔒 SKA / SKB  | Private keys (Alice / Bob) |
| 📩 M          | Message                    |
| ✍️ S(SK, M)   | Signature                  |
| 🔍 V(PK, Sig) | Verification               |
| 🔐 E(PK, M)   | Encryption                 |
| 🔓 D(SK, C)   | Decryption                 |

---

## 🎯 Goal

> Combine both to achieve:

- 🔐 Confidentiality
- ✍️ Integrity
- 🧾 Non-repudiation

---

# ⚙️ Method 1: Encrypt-then-Sign

## 🔄 Flow

```text id="8dz6c7"
C1 = E(PKB, M1)
Sig1 = S(SKA, C1)

Send → C1 || Sig1
```

---

## 🔍 Receiver (Bob)

```text id="k0cv4n"
1. Verify: V(PKA, Sig1) == C1 ?
2. Decrypt: M1 = D(SKB, C1)
```

---

## 🧠 Key Idea

> ✍️ Signature is applied to **ciphertext**

---

## ⚡ Properties

- ✅ Integrity of encrypted data
- ✅ Sender authentication
- ⚠️ Signature visible to attacker (on ciphertext)

---

## 🔁 Mini Recap

- 🔐 Encrypt first
- ✍️ Sign encrypted result
- 🧠 Signature protects ciphertext

---

# ⚙️ Method 2: Sign-then-Encrypt

## 🔄 Flow

```text id="w6f45y"
Sig1 = S(SKA, M1)
C1 = E(PKB, M1)

Send → C1 || Sig1
```

---

## 🔍 Receiver (Bob)

```text id="49q1rl"
1. Decrypt: M1 = D(SKB, C1)
2. Verify: V(PKA, Sig1) == M1 ?
```

---

## 🧠 Key Idea

> ✍️ Signature is applied to **plaintext**

---

## ⚠️ Security Concern

- ❌ Signature may be exposed after decryption
- ❌ Can be misused in certain attacks

---

## 🔁 Mini Recap

- ✍️ Sign message
- 🔐 Encrypt message
- ⚠️ Slightly weaker structure

---

# ⚔️ Comparison

| Feature             | 🔐 Encrypt-then-Sign | ✍️ Sign-then-Encrypt |
| ------------------- | -------------------- | -------------------- |
| Signature protects  | Ciphertext           | Plaintext            |
| Verification timing | Before decryption    | After decryption     |
| Security            | ✅ Stronger          | ⚠️ Risky             |
| Preferred           | ⭐ Yes               | ❌ Less preferred    |

---

# 💥 Critical Attack Scenario

## 🎭 Attack Story (Trudy’s Trick)

```text id="r6dljx"
1. Trudy intercepts:
   C1 = E(PKB, M1)

2. Later asks Bob:
   "Please sign this message (C1)"

3. Bob signs:
   S = S(SKB, C1)

4. Trudy now has:
   Valid signature on C1
```

---

## 😱 Result

- 💥 Attacker gets a **valid signature** from Bob
- ❌ Bob unknowingly signs attacker-controlled data

---

## 🧠 Root Cause

> 🚨 No binding between:

- Public key
- Owner identity

---

## 🔁 Mini Recap

- 🎭 Trick user into signing arbitrary data
- 💥 Leads to signature misuse
- ⚠️ Identity not verified

---

# 🧩 Fundamental Problem

## ⚠️ Public Key Trust Issue

> 🔓 A public key alone does NOT prove identity

- ❌ Anyone can claim:
  - “This is Bob’s public key”

- 😱 Leads to **Man-in-the-Middle attacks**

---

## 🧠 Visual Intuition

- 📦 Lock (public key) without owner identity
- 🕵️ Attacker replaces lock
- 🔓 Victim encrypts to attacker instead

---

# 🪪 Digital Certificates

## 🌠 Solution

> Bind identity ↔ public key

---

## 📜 Definition

- 🧾 A **digital certificate** is:
  - A **signed statement**
  - Linking:
    - 👤 Identity (e.g., Bob)
    - 🔓 Public key

---

## ⚙️ How It Works

- 🏢 Trusted authority (CA) signs certificate
- 🔍 Others verify using CA’s public key

---

## 🔁 Mini Recap

- 🧾 Certificate = identity + public key
- 🛡️ Prevents impersonation
- 🌐 Foundation of HTTPS, TLS

---

# 🌌 Final Synthesis

> 💫 Secure communication requires **three layers**:

- 🔐 Encryption → secrecy
- ✍️ Signature → authenticity
- 🪪 Certificate → identity trust
