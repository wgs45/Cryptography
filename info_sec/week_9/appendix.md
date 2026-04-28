# 🌌 Cyber-Scholar Dashboard: Public-Key Authentication 🔐

---

## 💠 Intuition: Why Public-Key Authentication?

Symmetric systems rely on **shared secrets** → hard to distribute securely.
Public-key systems solve this by splitting power:

- 🔓 Public Key → anyone can use
- 🔒 Private Key → only the owner controls

> [!IMPORTANT]
> Authentication now depends on **ownership of a private key**, not secrecy of a shared password.

---

## 🧪 Public-Key Notation

### 🛠️ Core Operations

- `E(PK_Alice, M)` → encrypt message for Alice
- `S(SK_Alice, M)` → Alice signs message

### ⚡ Key Insight

- Encryption ≠ Signing (different purposes)

| Operation  | Key Used | Goal            |
| ---------- | -------- | --------------- |
| Encryption | Receiver | Confidentiality |
| Signing    | Sender   | Authentication  |

> [!NOTE]
> In practice, systems often use **separate key pairs** for encryption and signing to avoid cross-protocol risks.

---

## 🧪 Public-Key Authentication Protocol

### 🔄 Workflow (Simplified)

1. Bob → Alice: "Hi, I am Bob"
2. Alice → Bob: `E(PK_Bob, RA)`
3. Bob → Alice: `S(SK_Bob, RA)`

### ✅ Why It Works

- Only Bob can **decrypt RA**
- Only Bob can **sign RA correctly**

> [!IMPORTANT]
> Combines **confidentiality (encryption)** + **authenticity (signature)**.

---

## ⚠️ Subtle Weakness

- Only Bob is authenticated
- Alice remains **unauthenticated**

> [!NOTE]
> This is **one-way authentication**.

---

## 💠 Session Key Establishment (Hybrid Crypto)

Instead of using public-key crypto for everything (slow ⚡), we:

1. Authenticate
2. Establish a **shared symmetric key KAB**

---

## 🧪 Authentication + Session Key Protocol

### 🔄 Workflow

1. Bob → Alice: `Bob || RB`
2. Alice → Bob: `E(PK_Bob, RB || KAB)`
3. Bob → Alice: `E(PK_Alice, RB + 1 || KAB)`

### ✅ Achievements

- Bob is authenticated
- Shared key `KAB` established

### ⚠️ Limitation

- No proof that **Alice is legitimate**

> [!IMPORTANT]
> Still missing **mutual trust**.

---

## 💠 Mutual Authentication + Key Exchange

Now both parties **sign + encrypt** messages.

---

## 🧪 Protocol Variant A (Sign → Encrypt)

### 🔄 Workflow

1. Bob → Alice: `Bob || RB`
2. Alice → Bob: `E(PK_Bob, S(SK_Alice, RB || KAB))`
3. Bob → Alice: `E(PK_Alice, S(SK_Bob, RB + 1 || KAB))`

### ✅ Strength

- Signature ensures identity
- Encryption ensures confidentiality

---

## 🧪 Protocol Variant B (Encrypt → Sign)

### 🔄 Workflow

1. Bob → Alice: `Bob || RB`
2. Alice → Bob: `S(SK_Alice, E(PK_Bob, RB || KAB))`
3. Bob → Alice: `S(SK_Bob, E(PK_Alice, RB + 1 || KAB))`

### ⚖️ Comparison

| Approach       | Order             | Security Focus           |
| -------------- | ----------------- | ------------------------ |
| Sign → Encrypt | Hidden signature  | Privacy + authenticity   |
| Encrypt → Sign | Visible signature | Integrity + transparency |

> [!NOTE]
> Choice depends on whether you want **signature visibility**.

---

## ⚡ Improved Protocol (Key Confirmation)

### 🔄 Workflow

1. Bob → Alice: `Bob || RB`
2. Alice → Bob: `E(PK_Bob, S(SK_Alice, RB || KAB))`
3. Bob → Alice: `E(KAB, RB + 1)`

### ✅ Final Upgrade

- Confirms both parties **actually possess KAB**

> [!IMPORTANT]
> Prevents half-completed key exchanges (critical in real systems).

---

## 💠 System Design Insight

Public-key authentication is often combined with:

- 🔐 Symmetric encryption (fast data transfer)
- 🔏 Digital signatures (identity proof)
- 🔄 Nonces (freshness)

This hybrid approach powers protocols like:

- TLS (web security)
- SSH (secure login)

---

## 🏁 Recap: Protocol Evolution

| Stage                     | Feature Added          | Remaining Issue     |
| ------------------------- | ---------------------- | ------------------- |
| Public-Key Authentication | Identity via signature | One-way only        |
| + Session Key             | Efficient encryption   | No mutual auth      |
| Mutual Authentication     | Two-way trust          | No key confirmation |
| Improved Version          | Key confirmation       | ✅ Robust           |
