# 🌌 Information Security Study Journal

_A Neon-Lit Cybersecurity Dashboard for Long-Term Mastery_

---

## 🧱 Pillars of Information Security

### 🔐 CIA Triad (Defensive View)

| Principle              | Meaning                            | Goal                 |
| ---------------------- | ---------------------------------- | -------------------- |
| 🧿 **Confidentiality** | Prevent unauthorized access        | Keep secrets safe    |
| 🧬 **Integrity**       | Prevent unauthorized modification  | Keep data correct    |
| ⚡ **Availability**    | Ensure systems/data are accessible | Keep systems running |

> 💡 **Reality Check:** It’s impossible to maximize all three equally. Trade-offs always exist.

⚠️ Example:
Cloud systems prioritize **Availability**, sometimes at the cost of strict isolation.

---

### 🧨 DAD Model (Attacker View)

| Threat                      | Targets                |
| --------------------------- | ---------------------- |
| 📤 **Disclosure**           | Breaks Confidentiality |
| ✏️ **Alteration**           | Breaks Integrity       |
| 💥 **Destruction / Denial** | Breaks Availability    |

> 🎯 Think of **CIA** as protection goals, and **DAD** as attack outcomes.

---

### 🛰 Mini Recap

- CIA = What we protect
- DAD = What attackers attempt
- Security = Managing trade-offs wisely

---

# 🧾 Authenticity & Nonrepudiation

## 🪪 Authenticity

### Intuition

Can we trust the source?

### Definition

- Data genuinely originates from its claimed source.
- Data has not changed in transit or storage.

📦 Example:
If a message claims to be from Bob, authenticity ensures:

- It _is_ from Bob.
- It wasn’t modified along the way.

---

## 🧷 Nonrepudiation

### Intuition

No denial allowed.

### Definition

- The subject who performed an action cannot deny it later.
- Essential for accountability.

📝 Example:
Digital signatures provide nonrepudiation.

---

### 🌠 Mini Recap

- Authenticity = Verify origin
- Nonrepudiation = Prevent denial
- Both support accountability systems

---

# 🛡 AAA Services Framework

## 🔑 The Five Elements

| Element               | Purpose                        | Example             |
| --------------------- | ------------------------------ | ------------------- |
| 🪪 **Identification** | Claim identity                 | Enter username      |
| 🔐 **Authentication** | Prove identity                 | Password, OTP       |
| 🚪 **Authorization**  | Grant permissions              | Access control list |
| 📊 **Auditing**       | Record activities              | System logs         |
| 🧮 **Accounting**     | Review logs for responsibility | Compliance checks   |

---

## 🔁 Flow Logic

```
User → Identification → Authentication → Authorization → Auditing → Accounting
```

### 🔍 Breakdown

#### 🪪 Identification

- User claims identity.
- Example: typing a username.

#### 🔐 Authentication

- Provide proof.
- Example: password + OTP.
- 🔑 Foundation for authorization and logging.

#### 🚪 Authorization

- Defines allowed actions.
- Grant / Deny resource access.

#### 📊 Auditing

- Logs events and activities.
- System logs, event logs, surveillance.

#### 🧮 Accounting

- Reviews logs.
- Holds users accountable.

---

### 🌌 Mini Recap

- Authentication is the **gatekeeper**.
- Auditing records actions.
- Accounting enforces responsibility.

---

# 💾 Data States & Countermeasures

## 📦 Data at Rest

Stored on disk or backup.

**Protection Methods:**

- 🔐 Encryption
- 🧬 Cryptographic hash
- 🎟 Tokenization

---

## 📡 Data in Transit

Moving across networks.

**Protection Methods:**

- 🌍 HTTPS
- 📁 FTPS
- 🖥 SSH

---

## ⚙️ Data in Use

Being processed in memory.

**Protection Method:**

- 🧮 Homomorphic encryption

  > Allows computation on encrypted data.

---

### 🤔 Can the Cloud Be Fully Trusted?

> ⚠️ Cloud providers ensure availability and scale, but ultimate trust depends on:

- Encryption strategy
- Key management
- Provider transparency

---

### 🌠 Mini Recap

| State   | Risk           | Protection         |
| ------- | -------------- | ------------------ |
| Rest    | Theft          | Encryption         |
| Transit | Interception   | TLS/HTTPS          |
| Use     | Memory attacks | Secure computation |

---

# 🧠 Encoding vs Encryption vs Hashing

## 📦 Encoding

```
apple → [encoded] → treasure box → apple
```

- Reversible.
- No secret key.
- Used for formatting (e.g., Base64).

---

## 🔐 Encryption

```
apple → 🔒 encrypted → locked box → apple
```

- Requires key.
- Reversible only with correct key.
- Protects confidentiality.

---

## 🧃 One-Way Hash

```
apple → hash function → apple juice → ❌ no reverse
```

- Irreversible.
- Fixed-length output.
- Used for passwords & integrity checks.

---

### 🌌 Mini Recap

| Concept    | Reversible? | Uses Key? | Purpose           |
| ---------- | ----------- | --------- | ----------------- |
| Encoding   | ✅          | ❌        | Format conversion |
| Encryption | ✅          | ✅        | Confidentiality   |
| Hash       | ❌          | ❌        | Integrity         |

---

# 🔐 Basics of Cryptography

---

## 🔁 Symmetric Key Cryptography

### 🔄 Flow

```
Plaintext → Encrypt (Secret Key) → Ciphertext
Ciphertext → Decrypt (Same Key) → Plaintext
```

### Key Characteristics

- Same secret key for encryption & decryption.
- Fast and efficient.
- Key distribution is challenging.

---

## 🔑 Asymmetric Key Cryptography

### 🧍 Alice & 🧑 Bob Scenario

1️⃣ Bob publishes **public key**
2️⃣ Alice encrypts message using Bob’s public key
3️⃣ Alice sends ciphertext
4️⃣ Bob decrypts using **private key**

```
Public Key → Encrypt
Private Key → Decrypt
```

### Key Characteristics

- Two different keys.
- Solves key distribution issue.
- Slower than symmetric encryption.

---

### 🌌 Mini Recap

| Type       | Keys Used        | Speed  | Use Case                 |
| ---------- | ---------------- | ------ | ------------------------ |
| Symmetric  | 1 secret key     | Fast   | Bulk encryption          |
| Asymmetric | Public + Private | Slower | Key exchange, signatures |

---

# 🧮 Cryptographic Hash Functions

## 🧠 Core Properties

- Input: Arbitrary length
- Output: Fixed length
- One-way function
- Collision probability: Very low

---

### 🔄 Concept Model

```
Plaintext → Hash Function → Digest
```

- Plaintext₁ ≠ Plaintext₂
- Digest₁ ≠ Digest₂ (ideally)

⚠️ Collision: Two inputs produce same hash (rare but possible).

---

### 🌠 Mini Recap

- Hashing ensures integrity.
- Cannot reverse to original data.
- Critical for password storage.

---

# 🧠 Kerckhoffs’ Principle

> 🔎 A cryptosystem must remain secure even if everything except the key is public knowledge.

### 🔑 Core Idea

Security must rely **only on key secrecy**, not algorithm secrecy.

⚠️ Never trust:

- Custom, unapproved cryptographic algorithms.

### 📜 Approved Standards

Security functions approved by:

- NIST SP 800-140C (CMVP program)

---

### 🌌 Mini Recap

- Algorithm = Public
- Key = Secret
- Security = Key strength

---

# 🌐 Wireless Sensor Networks (WSNs)

## 📡 What is WSN?

- Large number of **resource-constrained sensor nodes**
- Few powerful **base stations**
- Collect environmental data

Examples:

- 🌡 Temperature
- 💧 Humidity
- 🧬 Biological data

---

## 🔥 Applications

- Fire surveillance
- Movement detection

---

## ⚠️ Security Issues in WSN

### 🧨 Node Capture Attack

- Physical capture of sensor node.
- Firmware analysis.
- Possible buffer overflow exploitation.
- Sensitive data leakage if no hardware protection.

---

### 🐛 Malicious Code Injection

- Worm attack
- Fake data delivery
- Distributed manipulation

---

### 🌌 Mini Recap

WSNs are:

- Resource-limited
- Physically exposed
- High-risk environments

Security must consider hardware + software defenses.

---

# 🛰 Remote Attestation for Integrity Validation

## 🎯 Purpose

Allows a verifier to remotely confirm that a device’s program memory has not been altered.

---

## 🔁 Challenge-Response Model

```
Verifier → Challenge → Prover
Prover → Compute Checksum → Verifier
Verifier → Validate Integrity
```

### Protection Against

- Replay attacks

---

## 🔐 Integrity Methods

- Hash-based checksum
- HMAC (Keyed-Hash Message Authentication Code)

---

### 🌌 Mini Recap

Remote Attestation:

- Validates firmware integrity.
- Uses challenge-response.
- Protects distributed systems like WSNs.

---

# 🌠 Final Dashboard Recap

## 🧱 Core Models

- CIA vs DAD
- AAA Framework

## 🔐 Cryptographic Foundations

- Encoding ≠ Encryption ≠ Hash
- Symmetric vs Asymmetric
- Kerckhoffs’ Principle

## 🌐 Advanced Topics

- WSN Security
- Remote Attestation
- Data State Protection
